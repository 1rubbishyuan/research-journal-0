# paper

### The Art of Saying No: Contextual Noncompliance in Language Models

### 论文综述
除了unsafe的query,the scope of noncompliance should be broadened
- 实验结论
Our experiments demonstrate that while direct finetuning of instruction-tuned models can lead to both over-refusal and a decline in general capabilities, using parameter efficient methods like low rank adapters helps to strike a good balance between appropriate noncompliance and other capabilities.
- 拓展方向
一些本身就是错误的问题,带有一些偏见的问题,不成立的问题等...
### Method
#### taxonomy
- Incomplete Requests
根据给定信息无法回答的问题
- Indeterminate Requests
模型能力无法回答的问题,强行回答可能会出现幻觉
- Unsupported Requests
由于模型结构导致无法回答的问题(如时事问题,context超过了模型的context window的问题等)
- Humanizing Requests
询问模型的信仰、感情等（感觉GPT在这点啥梗对齐得挺好的）
- Requests with Safety Concerns
- Altering model behavior
(感觉和上一条一样都回到了比较传统的safety的问题了)
####  COCONOT: dataset
1. 造了数据集包含noncompliance queries 和 query set that should be complied with(现在感觉一个良好的数据集其实非常重要)

# code
1. 现阶段只剩下跑结果了,nice!
