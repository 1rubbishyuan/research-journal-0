# paper
## DebUnc: Mitigating Hallucinations in Large Language Model Agent Communication with Uncertainty Estimations(multi-agent debate)

### 论文创新
在debate中显示地加入confidence.

### 评估uncertainty的方法
- token probality-based uncertainty metrics
类似于ppl
- llm-generated uncertainty metrics
通过fine-tune让模型具备自己输出uncertainty的能力,在一些情况下由于probality-based
- sampling-based uncertainty metrics
多次output,从其分布中采样,并根据分布来决定置信度

# code
1. 是否应该想办法排除掉仅仅由于没有完成解析而造成的错误