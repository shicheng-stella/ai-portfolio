# 提示词迭代实录

## 场景：HSK4阅读理解出题

### 第一轮（R1 零约束）
**提示词：** 给我根据《愚公移山》出5道HSK4阅读题。

**AI输出与问题：**
<img width="1220" height="2905" alt="34ff022427b9e1e3d1d986e7072ae72" src="https://github.com/user-attachments/assets/aea2a381-6404-476b-afdf-4040a99c22eb" />

**修改思路：**
AI没有身份设定，没限制题型，输出太随意。下一轮我要加上“角色”和“格式”约束。

### 第二轮
**提示词：**
<img width="1415" height="631" alt="c2b0265466bd65f3806218a1ac65e66" src="https://github.com/user-attachments/assets/7acf534d-5150-4edb-99ee-ec038d3df0ee" />

**AI输出与问题：**
<img width="1449" height="556" alt="5426acba17a9b861b76ba608c62c04b" src="https://github.com/user-attachments/assets/9b96ac0c-e47e-470d-acad-7813eef4b646" />
<img width="1423" height="601" alt="0b3eb593668eaa92094409300724ec5" src="https://github.com/user-attachments/assets/176ae985-9edd-4906-a9f5-0a53e24e9403" />

### 第三轮（R3 定标准）
**提示词：** 在上一轮的基础上，强制要求“题型配比：2细节+2词义+1主旨”，并提供了“解析引用原文”的示例。
<img width="1385" height="537" alt="2b97447312b598cbb7682bd818a166f" src="https://github.com/user-attachments/assets/b5e7534c-b3c1-4aaf-b331-42da3ace4e53" />

**AI输出：** （把你刚才截的图片粘贴在这里）
<img width="1496" height="540" alt="90cd0da45665509e8850d0d0d8dcde6" src="https://github.com/user-attachments/assets/da52e84c-e460-4aa0-a200-9a0fdee6c1d4" />
<img width="1505" height="537" alt="8c14cf13d461dad3e0e101b7df31303" src="https://github.com/user-attachments/assets/1d4135bb-5aad-470e-8bce-631c40e01ee0" />

**最终总结：** 经过三轮迭代，每加一根支柱（角色、格式、配比、示例），AI就变好一点。这就是把“碰运气”变成“稳定产出”的方法。






