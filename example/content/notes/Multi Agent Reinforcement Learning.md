### Multi Agent Reinforcement Learning

#### Chap 1 Supervised Learning



##### 1.1 Least Squares Estimation

Example:Linear Regression

Problem:

$$y(n)=\phi^T\theta$$

where $\phi^T=[x(n),1]$ and $\theta^T=[a,b]$

minimize cost function $V=\sum_{n=1}^N{(y(n)-\phi^T(n)\hat\theta})^2$

Find minimum:

> $\frac{\partial V}{\partial \hat\theta}=\sum2(y(n)-\phi^T\hat\theta)(-\phi(n))$
>
> doesn't change the result
>
> A good method is reformulate the cost function as:
>
> $V=-\frac{1}{2}\sum_{n=1}^N{(y(n)-\phi^T(n)\hat\theta})^2$

$$ \frac{\partial V}{\partial \hat\theta}=\sum_{n=1}^{N}(y(n)-\phi^T(n)\hat\theta)\phi(n)=\sum_{n=1}^N\phi(n)y(n)-\phi(n)\phi^T(n)\hat\theta=0$$

LS solution:

$$\hat\theta=[\sum_{n=1}^{N}\phi(n)\phi^T(n)]^{-1}[\sum^{N}_{n=1}\phi(n)y(n)]$$

where the inverse $\sum_{n=1}^{N}\phi(n)\phi^T(n)]^{-1}$ exists. otherwise the system is not identifiable.





Prediction error

$$\frac{\partial V}{\partial \hat\theta}=0=\sum_{n=1}^{N}(y(n)-\phi^T(n)\hat\theta)\phi(n)$$

$$\epsilon(n)=(y(n)-\phi^T(n)\hat\theta)$$

Typically add a ==(white) noise== term

$$y(n)=\phi^T(n)\theta+v(n)$$

assume we want to learn the dynamics of a second-order linear system or a IIR filter,given by $y(n)=-a_1y(n-1)-a_2y(n-2)+b_1u(n-1)+b_2u(n-2)+v(n)$

$$\phi^T(n)=[y(n-1),y(n-2),u(n-1),u(n-2)]$$

In general, k-th order autoregressive exogenous(ARX) model sturcture could be written as $y(n)=-a_1y(n-1)-a_2y(n-2)-…-a_my(n-k)+b_1u(n-1)+b_2u(n-2)+…+b_{n-k}u(n-k)+v(n)$

$$\Phi=[\phi(1),…\phi(n)]$$

$$\hat\Theta=(\Phi \Phi^T)^{-1}\Phi Y$$



##### 1.2 ==Recursive== Least Squares

==Real time== version LS algorithm

Considering the long-short time memory network

So the cost function with forgetting factor is:

$$V=\sum_{n=1}^N\lambda^{N-t}(y(n)-\phi^T(n)\hat\theta)^2$$

The solution could be drived with pratial derivative:

$$\hat\theta=[\sum_{n=1}^{N}\lambda^{N-t}\phi(n)\phi^T(n)]^{-1}[\sum_{n=1}^{N}\lambda^(N-t)\phi(n)y(n)]$$

> Considering Wavelet transform or short time Fourier transform, the importace of data various during differnet time scale. A feasible way to solve this is using a window function.
>
> In real time application, RLS has better adaption to data differs from time.

RLS:

$$\hat\theta(n+1)=\hat\theta(n)+L(n+1)(y(n+1)-\phi^T(n+1)\hat\theta(n))$$

$$L(n+1)=\frac{P(n)\phi(n+1)}{\lambda+\phi^T(n+1P(n)\phi(n+1))}$$

$$P(n+1)=\frac{1}{\lambda}(P(n)-\frac{P(n)\phi(n+1)\phi^T(n+1)P(n)}{\lambda+\phi^T(n+1)P(n)\phi(n+1)})$$



##### 1.3 Least Mean Squares

