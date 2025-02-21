# 1
The MGF can be written as:

$$m_X(t) = \sum_{k = 1}^\infty p_k e^{kt}$$

From the given MGF:

$$P(X = 1) = 0.5$$
$$P(X = 2) = 0.25$$
$$P(X = 3) = 0.125$$
$$...$$

From the pattern:

$$P(X = k) = \frac{1}{2^k},\ k \in \mathbb{N}$$

The distribution is:

$$X \sim Geometric(0.5),\ X \in \mathbb{N}$$

\newpage
# 2
From discussion section, the MGF is:
$$m_{X_1}(t) = \left(\frac{p_1}{1 - (1 - p_1) e^t}\right)^l$$
$$m_{X_2}(t) = \left(\frac{p_2}{1 - (1 - p_2) e^t}\right)^l$$

Since $X_1, X_2$ are independent:
$$m_{X_1 + X_2}(t) = (m_{X_1}(t))(m_{X_2}(t))$$
$$m_{X_1 + X_2}(t) = \left(\frac{p_1}{1 - (1 - p_1) e^t}\right)^l\left(\frac{p_2}{1 - (1 - p_2) e^t}\right)^l$$

The MGF of $NB(l, p_1 + p_2)$ is:
$$\left(\frac{p_1 + p_2}{1 - (1 - p_1 - p_2) e^t}\right)^l$$

Since a sum is not equal to a product when raised to a power, we can conclude:
$$X_1 + X_2 \nsim NB(l, p_1 + p_2)$$

\newpage
# 3
#### (a)
Given:
$$m_{X_1}(t) = exp(4(e^t - 1))$$

Let:
$$Y = 2X_1$$

Then the MGF is:
$$M_Y(t) = E[e^{t(2X)}]$$
$$M_Y(t) = E[(e^{2t})^X]$$
$$M_Y(t) = M_X(2t)$$

Plugging in the given MGF:
$$m_{Y_1}(t) = exp(4(e^{2t}-1)) \neq exp(8(e^t-1))$$

Therefore:
$$2X_1 \nsim Poisson(8)$$

#### (b)
Given:
$$M_{X_1}(t) = exp(4(e^t-1))$$
$$M_{X_2}(t) = exp(4(e^t-1))$$

Let:
$$Y = X_1 + X_2$$

Then:
$$M_Y(t) = E[e^{t(X_1 + X_2)}]$$
$$M_Y(t) = E[(e^{t})^{X_1 + X_2}]$$
$$M_Y(t) = E[(e^{t})^{X_1}(e^{t})^{X_2}]$$
$$M_Y(t) = E[(e^{tX_1})(e^{tX_2})]$$

Since $X_1$ and $X_2$ are independent:
$$M_Y(t) = E[e^{tX_1}]E[e^{tX_2}]$$
$$M_Y(t) = M_{X_1}(t)M_{X_2}(t)$$

Plugging in the given MGF:
$$M_Y(t) = exp(4(e^t-1))exp(4(e^t-1))$$
$$M_Y(t) = exp(8(e^t-1))$$

Therefore:
$$X_1 + X_2 \sim Poisson(8)$$

#### (c)
Using the same proof from (b), we can conclude:
$$X_1 + X_3 \sim Poisson(6)$$

\newpage
# 4
#### (a)
$$F_{Y_i}(y) = P(Y_i \leq y)$$
$$F_{Y_i}(y) = P(-log(1 - X_i) \leq y)$$
$$F_{Y_i}(y) = P(log(1 - X_i) > -y)$$
$$F_{Y_i}(y) = P(1 - X_i > e^{-y})$$
$$F_{Y_i}(y) = P(1 - e^{-y} > X_i)$$
$$F_{Y_i}(y) = P(X_i \leq 1 - e^{-y})$$
$$F_{Y_i}(y) = F_{X_i}(1 - e^{-y})$$
$$f_{Y_i}(y) = e^{-y}\ f_{X_i}(1 - e^{-y})$$
$$f_{Y_i}(y) = e^{-y}\theta(1 - (1 - e^{-y}))^{\theta - 1}$$
$$f_{Y_i}(y) = e^{-y}\theta(e^{-y})^{\theta - 1}$$
$$f_{Y_i}(y) = \theta(e^{-y})^{\theta}$$
$$Y_i \sim Exponential(\theta)$$

#### (b)
$$L(\theta) = \prod_{i = 1}^n \theta(1 - X_i)^{\theta - 1}$$
$$l(\theta) = n\ log(\theta) + (\theta - 1) \sum_{i = 1}^n log(1 - X_i)$$
$$\frac{\delta l(\theta)}{\delta \theta} = \frac{n}{\theta} + \sum_{i = 1}^n log(1 - X_i) = 0$$
$$\sum_{i = 1}^n log(1 - X_i) = -\frac{n}{\theta}$$
$$\hat\theta_{MLE} = \frac{-n}{\sum_{i = 1}^n log(1 - X_i)}$$

#### (c)
We can use the transformation from (a):
$$\hat\theta_{MLE} = \frac{n}{\sum_{i = 1}^n Y_i}$$
$$\hat\theta_{MLE} = \frac{n}{\sum_{i = 1}^n Y_i}$$

Let $Y = \sum_{i = 1}^n Y_i$:
$$\hat\theta_{MLE} = \frac{n}{Y}$$

Since $Y$ is the sum of $n$ independent exponential variables:
$$Y \sim Gamma(n, \theta)$$

Now find the CDF:
$$F_{\hat \theta}(x) = P(\hat \theta < x)$$
$$F_{\hat \theta}(x) = P\left(\frac{n}{Y} < x\right)$$
$$F_{\hat \theta}(x) = P\left(\frac{n}{x} < Y\right)$$
$$F_{\hat \theta}(x) = 1 - P\left(Y < \frac{n}{x}\right)$$
$$F_{\hat \theta}(x) = 1 - F_Y\left(\frac{n}{x}\right)$$
$$f_{\hat \theta}(x) = -f_Y\left(\frac{n}{x}\right) * \frac{-n}{x^2}$$
$$f_{\hat \theta}(x) = f_Y\left(\frac{n}{x}\right) * \frac{n}{x^2}$$

Since $Y$ is a Gamma distribution:
$$f_Y(y) = \frac{\theta^n}{(n - 1)!} * y^{n - 1}e^{-\theta y}$$

Plug in the PDF:
$$f_{\hat \theta}(x) = \frac{\theta^n}{(n - 1)!} * \left(\frac{n}{x}\right)^{n - 1}e^{-\theta \frac{n}{x}} * \frac{n}{x^2}$$

#### (d)
Since $Y$ follows a gamma distribution and $\hat \theta = \frac{n}{Y}$:
$$\hat \theta \sim Inv-Gamma(n, n\theta)$$
$$E[\hat \theta] = \frac{n\theta}{n - 1}$$

Bias:
$$Bias(\hat\theta) = E[\hat\theta_{MLE}] - \theta$$
$$Bias(\hat\theta) = \frac{n\theta}{n - 1} - \theta$$

MSE:
$$MSE(\hat\theta) = Var[\hat\theta] + Bias[\hat \theta]^2$$

Since $\hat \theta$ follows an inverse gamma distribution:
$$Var[\hat\theta] = \frac{n^2\theta^2}{(n - 1)^2(n - 2)}$$

Plug into MSE:
$$MSE(\hat\theta) = \frac{n^2\theta^2}{(n - 1)^2(n - 2)} + \left[\frac{n\theta}{n - 1} - \theta\right]^2$$

\newpage
# 5
#### (a)
$$F_{\hat \lambda}(x) = P(\hat \lambda < x)$$
$$F_{\hat \lambda}(x) = 1 - P(\hat \lambda \geq x)$$
$$F_{\hat \lambda}(x) = 1 - P(\{nX_1 \geq x \cap ... \cap n X_n \geq x\})$$

Since $X_1, ..., X_n$ are independent:
$$F_{\hat \lambda}(x) = 1 - P(nX_1 \geq x)...P(nX_n \geq x)$$

Since $X_1, ..., X_n$ follow the same distribution:
$$F_{\hat \lambda}(x) = 1 - [P(nX_1 \geq x)]^n$$
$$F_{\hat \lambda}(x) = 1 - \left[1 - P\left(X_1 < \frac{x}{n}\right)\right]^n$$
$$F_{\hat \lambda}(x) = 1 - \left[1 - F_{X_1}\left(\frac{x}{n}\right)\right]^n$$

Since $X_1$ is an exponential distribution, the CDF is:
$$F_{X_1}(x) = 1 - e^{-\lambda x}$$

Now plug in the CDF:
$$F_{\hat \lambda}(x) = 1 - \left[1 - [1 - e^{-\lambda \frac{x}{n}}]\right]^n$$
$$F_{\hat \lambda}(x) = 1 - \left[e^{-\lambda \frac{x}{n}}\right]^n$$
$$F_{\hat \lambda}(x) = 1 - e^{-\lambda x}$$

From the CDF:
$$\hat \lambda \sim Exponential(\lambda)$$
$$f_{\hat \lambda}(x) = \lambda e^{-\lambda x}$$

#### (b)
Bias:
$$Bias(\hat \lambda) = E[\hat \lambda] - \lambda$$

Since $\hat \lambda \sim Exponential(\lambda)$:
$$E[\hat \lambda] = \frac{1}{\lambda}$$
$$Bias(\hat \lambda) = \frac{1}{\lambda} - \lambda$$

MSE:
$$MSE[\hat \lambda] = Var[\hat \lambda] + Bias[\hat \lambda]^2$$

Since $\hat \lambda \sim Exponential(\lambda)$:
$$Var[\hat \lambda] = \frac{1}{\lambda^2}$$
$$MSE[\hat \lambda] = \frac{1}{\lambda^2} + \left[\frac{1}{\lambda} - \lambda\right]^2$$