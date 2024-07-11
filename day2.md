# paper
## understanding alignment in mutiModal LLMS(一篇综述+一种构建数据集的方法BDHS)
### 一些结论（观点）
1. preference alignment 可以在一定程度上减少幻觉
2. KL散度防止策略变化太大是为了模型性能考虑的

### 偏好数据在不同算法中的使用
#### RLHF
用来训练reward model,本质的训练方法是一个简单的二分类任务
#### DAP(DIRECT ALIGNMENT FROM PREFERENCE)
就是直接用偏好数据来构造loss,而不是基于打分
一个存在的问题是离线的算法无法做到根据模型在训练过程中的改变来进一步调整偏好，这可能是有偏的。
#### ODAP(online)
一个点在于本篇论文在做DPO实验时，混合了offline和online的方法，其实就是在偏好数据选择时从两个来源随机(这方法真的合理吗?) 

### Data generate
1. 偏好数据构造有ranking和construction两种方法,前者很好理解，后者其实有点像昨天看到的那个数学推理数据集构造的方案。
2. 一个构造disprefer数据的方法是加噪声
3. BDHS(BIAS-DRIVEN HALLUCINATION SAMPLING)
-  ELICITING LLM BIAS VIA ATTENTION MASKING
通过mask掉图片中的有效信息来诱导幻觉
- 可以把输出分为几段，然后在某一段开始生成错误内容，为了保证和prefer有较大差距，可以考虑在比较早的字段开始

### 模型选择
LLaVA 1.6-34B,因为这个模型在一些muitimodal benchmark上表现比较好

### 数据集积累
COCO : 一个图片数据集
UniMM-CHatSFT : 文字prompt加上图片的问题数据集
