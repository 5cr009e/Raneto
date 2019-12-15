[Hinton的理论](https://zhuanlan.zhihu.com/p/29435406)

- sigmoid会饱和，造成梯度消失。于是有了ReLU。
- ReLU负半轴是死区，造成梯度变0。于是有了LeakyReLU，PReLU。
- 强调梯度和权值分布的稳定性，由此有了ELU，以及较新的SELU。
- 太深了，梯度传不下去，于是有了highway。
- 干脆连highway的参数都不要，直接变残差，于是有了ResNet。
- 强行稳定参数的均值和方差，于是有了BatchNorm。
- 在梯度流中增加噪声，于是有了 Dropout。
- RNN梯度不稳定，于是加几个通路和门控，于是有了LSTM。
- LSTM简化一下，有了GRU。
- GAN的JS散度有问题，会导致梯度消失或无效，于是有了WGAN。
- WGAN对梯度的clip有问题，于是有了WGAN-GP。

### [Meta Learning 17](https://zhuanlan.zhihu.com/p/32270990?group_id=930928567332741120)

[Meta Learning](https://zhuanlan.zhihu.com/p/28639662)

[一篇文献汇总](https://github.com/songrotek/Meta-Learning-Papers)

思路：

- 基于Memory
- 基于预测梯度
- 基于Attention
- 借鉴LSTM
- 面向RL
- 训练好base model
- WaveNet
- 预测loss