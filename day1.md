# paper

## step controlled DPO (感觉重点在于如何造数据)

### 论文工作

1. 提出了SCDPO架构
2. 证明了该方法在数学推理上的有效性，使用了GSM8K和MATH数据集
3. 此外还使用了APE210K数据集，也是一个数学问题数据集

### pipline

#### step-contolled data generation

- $D_{naive}$ : 就是让模型生成preferred-dispreferred solution pairs,是离线数据
- $D_{SC}$ : 带有逐步错误注释的数据集,也就是希望数据在一个可控的步数上产生错误。 实现的方案为把正确的前k步和prompt一起作为输入，然后设置temperature为一个较高的值且该值逐步递增，然后生成数据直到出现错误。

#### step-aware DPO training

把两个数据集混合起来进行DPO的训练，从而在抽象意义上做到step-level的DPO训练

### Experiments

### 模型使用

Mistral-7B 作为Baseline的对比实验
InternLM2-20B作为increase的基础模型

## Efficient World Models with Context-Aware Tokenization

稍微有点晦涩

### 学术名词

delta-token: 理解为记录前后状态变化的token

### 论文工作

提出一种新的RL agent，具有更好的可拓展性

# code

## 修改ssh代理

在本机的~/.ssh/config中添加下列内容可以实现"DNS"最后一行可以用于服务器到本机的流量端口映射

```js
Host aistation-1
     HostName 10.31.118.166
     User root
     Port 32585
     RemoteForward 10808 localhost:7890
```

## 环境配置

- proxychains 端口映射
- -i 换源
- 网络问题需要重新login一下ssh
