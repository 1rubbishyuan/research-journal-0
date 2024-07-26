# paper
## Llama3.1技术报告

### pre-training
#### pre-training data
1. Web Data
- PII and safety filtering
- text extraction and cleaning : 
从HTML中筛选高质量的数据,发现markdown对于模型的表现是有害的,故使用纯文本内容
- de-duplication
- Heuristic filtering:
We develop heuristics to remove additional low-quality documents, outliers, and documents with excessive repetitions
- model-based quality filtering(fasttext???)
- code and reasoning data
- code and reasoning data 有建立specific的pipline
- multilingual data
2. data mix
使用knwoledge classfication和 scaling laws for data mix的方法来决定最终的data mix,前者没看懂,后者其实就是scaling 实验
3. Annealing Data
逐步缩小预训练的数据集范围，用来模拟退火
#### scaling相关没怎么看
#### training recipe
一些相关细节配置
### post-training



### post-training

# code 
1. docker 创建时的 . 为上下文目录,即本机此时的工作目录,可以在dockerfile中对上下文目录中的内容进行COPY等操作(注,由于只打包了上下文目录中的内容,所以..会报错)