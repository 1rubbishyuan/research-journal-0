# paper

## RULE: Reliable Multimodal RAG for Factuality in Medical Vision Language Models

### RAG(Retrieval Augmented Generation)应用存在的两个问题
1. 检索程度的问题,即检索不能太少也不能太多
2. 模型回答正确时,对检索信息的依赖可能会导致其将答案改错

### 论文创新点
#### RULE
一种对冲上面提到的两个问题的策略
1. Context Retrieval for Reference
检索是基于相似度进行的,具体的方案为对image encoder和text encoder进行fine tune 来让二者在相关的信息上解码出更相似的vector，而对于基于图像的检索则基本等同于这个过程,将与当前图像相似度的Top-K的文本信息作为检索信息
2. Factuality Risk Control Through Calibrated Retrieved Context Selection
一种纯数学的方法,不过其中一个奇怪的点是要计算FR就必须先让模型把问题跑一遍才能计算并在之后决定新的k值,这个很怪很怪
3. Knowledge Balanced Preference tuning
把由于过度依赖检索信息而导致错误的情况作为dispreferred,把基于ground truth的作为preferred然后做DPO来完成

### 任务场景
医学诊断(是一个多模态的任务场景)

## STARK : Social Long-Term Multi-Modal Conversation with Persona Commonsense Knowledge

### 论文创新点
提出了一种收集 a large-scale
long-term multi-modal conversation dataset
that covers a wide range of social personas in a multi-modality format, time intervals, and images.的framework 叫做MCU

即创建了一个具有个人偏好的多模态数据集,感觉可能还挺有用的。

### MCU的pipline(8 steps)
1. Generating social persona attribute based on the collection of demographics


# code
1. 使用transformer的模型时,除了vllm+多线程还可以考虑利用batch来进行加速(但我怎么感觉我那个reward写的不太对)

# twitter
1. context window的大小对于模型的性能有着较为重要的作用
2. 70B甚至更大的模型fine tune以后不见得能够取得更好的效果