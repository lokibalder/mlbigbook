<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>
本篇内容介绍样本不均衡问题如何处理

0. 样本不均衡问题的定义
比如分类问题中，某一些类别的占比特别少。而数据往往符合长尾现象，不平衡的情况是很自然会出现的。
0.1 样本不均衡带来的问题
损失函数侧重在样本更多的类比上，也需模型的指标很好，但是这个模型在识别样本偏少的类别上可能效果很差。

1. 模型层面
1.1 加权loss
核心思想：
传统的交叉熵公式：TODO
$$
CE = 
\begin{cases}
-log(p),\,\,if y = 1\\
-log(1-p),\,\,if y = 0\\
\end{cases}
$$
可以为类别加上不同的权重，这里引入了超参a，比如一共有100条正样本和10000条负样本，可以将a设置为100/10100，这样正样本的loss会乘以一个高一些的权重，负样本的loss会乘以一个低一些的权重。

1.2 Focal Loss
考虑了样本的难易程度可以影响loss，在样本不均衡的场景下，有很多负样本是非常容易区分的样本。

1.3 GHM Loss
对于离群点，从置信度的角度去调整loss

2.从数据层面解决

