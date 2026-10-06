# AI 辅助编程实录

## 1. 任务与提示词

**要做什么：** 读生词表CSV，按HSK等级筛选，统计词性分布，输出练习题txt文件。

**我写的提示词（四件套）：**
【角色】你是Python教学助手
【任务】写一个脚本，读取一份生词表CSV，按HSK等级筛选，统计词性分布，并输出练习题txt文件。
【要求】仅使用Python标准库，每一行都要加中文注释。
【示例】期望输出格式：用“坚持”造一个句子。（动词）

## 2. AI 初版代码

（这是AI根据上面提示词给出的第一版代码，未经过我修改）

```python
import csv

def load_words(path):
    with open(path) as f:
        return list(csv.DictReader(f))

def filter_by_level(words, level="4"):
    return [w for w in words if w["level"] == level]

def count_by_pos(words):
    d = {}
    for w in words:
        d[w["pos"]] = d.get(w["pos"], 0) + 1
    return d

def gen_exercises(words):
    with open("练习.txt", "w") as f:
        for w in words:
            f.write("用“%s”造一个句子。（%s）\n" % (w["word"], w["pos"]))

words = load_words("data/生词表.csv")
lv4 = filter_by_level(words)
print(count_by_pos(lv4))
gen_exercises(lv4)
## 3. 我的修改点（≥3条）
① 修正CSV字段名：AI默认用了英文键名（如 w["level"]、w["word"]），但我查看了自己的CSV表头，字段名其实是中文的“HSK等级”、“词汇”、“词性”。如果直接运行AI的代码会报 KeyError。我把所有对应的键名改成了与CSV一致的中文名称。
② 解决中文乱码：AI在 open() 函数里没有指定编码。在Windows系统下运行会导致中文乱码。我在所有读写文件的地方都补上了 encoding="utf-8"。
③ 统一文件路径：AI把输入文件写死为 "data/生词表.csv"，把输出文件写死为 "练习.txt"。这会导致脚本换个目录运行就找不到文件。我引入了 os.path.dirname(os.path.abspath(file)) 来动态获取脚本所在目录，确保无论从哪里运行，路径都不会出错。
④ 官方教程收获（作业1）：精读Python官方教程后，我发现了“列表推导式”和“with语句”的简洁写法。我把AI原本冗长的循环筛选改成了 [w for w in words if str(w["HSK等级"]) == str(level)]，把文件打开改成了 with open(...)，不仅代码更短，还能自动关闭文件。

## 4. 最终版vs初版差异说明
AI想多了的地方：AI引入了一些不在需求里的写法，我根据“仅用标准库”的要求，删掉了多余的部分，保留最核心逻辑。
AI漏掉的地方：AI忽略了Windows下中文路径的编码问题，也忽略了相对路径的脆弱性。我补齐了 encoding="utf-8"，并把数据路径改成了动态获取。
我为什么这么改：因为老师的验收标准是“脚本要能从任意目录独立运行，不报错”，我必须保证代码在本地跑通且输出结果正确。
