# 1
#### (a)
We have $n$ users. $\pi = \pi_1$ is the proportion of $n$ users that uses FireFox. $Y_1$ is a sample number of $n$ users that uses FireFox.

$$E[Y_1] = \pi n$$

We want:
$$E[\hat\pi_1] = \pi$$
$$E\left[\frac{Y_1}{n}\right] = \pi$$
$$\hat\pi_1 = \frac{Y_1}{n}$$
$$c_1 = \frac{1}{n}$$

#### (b)
We are given:
$$E[Y_2] = 2\pi n$$

Then:
$$E[c_2Y_2] = \pi$$
$$c_2 * 2\pi n = \pi$$
$$c_2 = \frac{1}{2n}$$

#### (c)
TODO: Write multinomial on your notesheet
$$MSE[\hat \pi_1] = Var[\hat \pi_1]$$
$$MSE[\hat \pi_1] = Var\left[\frac{Y_1}{n}\right]$$
$$MSE[\hat \pi_1] = \frac{1}{n^2}Var[Y_1]$$
$$MSE[\hat \pi_1] = \frac{1}{n^2}n\pi(1-\pi)$$
$$MSE[\hat \pi_1] = \frac{1}{n}\pi(1-\pi)$$

Similarly:
$$MSE[\hat \pi_2] = Var[\hat \pi_2]$$
$$MSE[\hat \pi_2] = Var\left[\frac{Y_2}{2n}\right]$$
$$MSE[\hat \pi_2] = \frac{1}{4n^2}Var[Y_2]$$
$$MSE[\hat \pi_2] = \frac{1}{4n^2}n(2\pi)(1-2\pi)$$
$$MSE[\hat \pi_2] = \frac{1}{2n}\pi(1-2\pi)$$

$\hat \pi_2$ is a better estimator since MSE is lower.

#### (d) i.
$$E[\hat \pi_3] = E[E[\hat \pi_2 | Y_3 + Y_4]]$$

Tower property:
$$E[\hat \pi_3] = E[\hat \pi_2]$$

Since $\hat \pi_2$ is unbiased, then $\hat \pi_3$ is also unbiased.

#### (d) ii.
TODO: Do I need to compute an exact number or stating the theorem is good enough?

Yes, $\hat \pi_3$ is a better estimator than $\hat \pi_2$ by the Rao-Blackwell theorem.

# 2
#### (a)
$$E[X_1] = E[X_2] = \lambda$$
$$E[\hat \theta_1] = \frac{2}{3}\lambda + \frac{1}{3}\lambda$$
$$E[\hat \theta_1] = \lambda$$

$\hat \theta_1$ is unbiased.

#### (b)
$$MSE[\hat\theta_1] = Var[\hat\theta_1] + Bias[\hat\theta_1]^2$$
$$MSE[\hat\theta_1] = Var[\hat\theta_1]$$
$$MSE[\hat\theta_1] = Var\left[\frac{2}{3}X_1 + \frac{1}{3}X_2\right]$$
$$MSE[\hat\theta_1] = \frac{4}{9}Var[X_1] + \frac{1}{9}Var[X_2]$$
$$MSE[\hat\theta_1] = \frac{5}{9}\lambda$$

#### (c)
We have:
$$P(X_1 = k) = \frac{\lambda^ke^{-\lambda}}{k!}$$
$$P(X_2 = m) = \frac{\lambda^me^{-\lambda}}{m!}$$

We want to solve for:
$$P(X_1 = k | T = t)$$

Note: Since $T = X_1 + X_2$, $X_1 = k$, and $T = t$, we know:
$$X_2 = t - k$$

Using Bayes:
$$P(X_1 = k | T = t) = \frac{P(X_1 = k, X_2 = t - k)}{P(T)}$$

Joint PMF ($X_1, X_2$ are iid):
$$P(X_1 = k, X_2 = m) = P(X_1 = k)P(X_2 = m)$$
$$P(X_1 = k, X_2 = m) = \frac{\lambda^ke^{-\lambda}}{k!}\frac{\lambda^me^{-\lambda}}{m!}$$
$$P(X_1 = k, X_2 = m) = \frac{\lambda^{k+m}e^{-2\lambda}}{k!m!}$$

Find $P(T = t)$:
$$P(T = t) = P(X_1 + X_2 = t)$$

TODO: write convolutions on the cheat sheet
TODO: write Poisson sum property on the cheat sheet

Note:
$$X_1 + X_2 \sim Poisson(2\lambda)$$

Then:
$$P(T = t) = \frac{(2\lambda)^t e^{-2\lambda}}{t!}$$

Solve for answer:
$$P(X_1 | T) = \frac{\lambda^{t}e^{-2\lambda}}{k!(t-k)!} * \frac{t!}{(2\lambda)^t e^{-2\lambda}}$$
$$P(X_1 | T) = \frac{t!}{k!(t-k)!} * \frac{\lambda^{t}e^{-2\lambda}}{(2\lambda)^t e^{-2\lambda}}$$
$$P(X_1 | T) = \frac{t!}{k!(t-k)!} * \frac{1}{2^t}$$
$$P(X_1 = k | T = t) = \binom{t}{k} \left(\frac{1}{2}\right)^k \left(\frac{1}{2}\right)^{t - k}$$

Similarly:
$$P(X_2 = k | T = t) = \binom{t}{k} \left(\frac{1}{2}\right)^k \left(\frac{1}{2}\right)^{t - k}$$

Then:
$$X_i|T \sim Binomial\left(T, \frac{1}{2}\right)$$

#### (d)
$$\hat\theta_2 = E[\hat\theta_1|T]$$
$$\hat\theta_2 = \frac{2}{3}E[X_1|T] + \frac{1}{3}E[X_2|T]$$

Using the distribution from (c):
$$E[X_i|T] = \frac{T}{2}$$

Then:
$$\hat\theta_2 = \frac{T}{2}$$

#### (e)
From Rao-Blackwells Theorem:
$$Bias[\hat \theta_2] = 0$$

Then:
$$MSE[\hat \theta_2] = Var[\hat\theta_2]$$
$$MSE[\hat \theta_2] = Var\left[\frac{T}{2}\right]$$
$$MSE[\hat \theta_2] = \frac{1}{4}Var\left[T\right]$$
$$MSE[\hat \theta_2] = \frac{1}{4}*2\lambda$$
$$MSE[\hat \theta_2] = \frac{1}{2}\lambda$$

Since:
$$\hat \theta_2 = g(T)$$

$\hat \theta_2$ is the best estimator by the Lehmann-Scheffé Theorem.

TODO: put the theorem on the cheat sheet.

# 3
#### (a)
$$f_\theta(X_1...X_n) = v(t, \theta)w(X_1...X_n)$$
$$\left(\prod_{i=1}^n X_i\right)^{-\theta} = v(t, \theta)w(X_1...X_n)$$
$$exp\left(ln\left(\left(\prod_{i=1}^n X_i\right)^{-\theta}\right)\right) = v(t, \theta)w(X_1...X_n)$$
$$exp\left(-\theta\ ln\left(\prod_{i=1}^n X_i\right)\right) = v(t, \theta)w(X_1...X_n)$$
$$exp\left(-\theta \sum_{i=1}^n ln\ X_i\right) = v(t, \theta)w(X_1...X_n)$$

Note that:
$$T = \sum_{i=1}^n ln\ X_i$$

Then:
$$v(t, \theta) = exp(-\theta T)$$
$$w(X_1...X_n) = 1$$

# 4
TODO: Add factorization theorem to cheat sheet

$$f_\mu(X_1...X_n) = \prod_{i=1}^n \left(\frac{1}{\sqrt{6\pi}}exp\left(-\frac{(X_i-\mu)^2}{6}\right)\right)$$
$$f_\mu(X_1...X_n) = \left(\frac{1}{\sqrt{6\pi}}\right)^n\ \prod_{i=1}^n exp\left(-\frac{(X_i-\mu)^2}{6}\right)$$
$$f_\mu(X_1...X_n) = \left(\frac{1}{\sqrt{6\pi}}\right)^n\ exp\left(-\sum_{i=1}^n\frac{(X_i-\mu)^2}{6}\right)$$
$$f_\mu(X_1...X_n) = \left(\frac{1}{\sqrt{6\pi}}\right)^n\ exp\left(-\frac{1}{6}\sum_{i=1}^n(X_i-\mu)^2\right)$$
$$f_\mu(X_1...X_n) = \left(\frac{1}{\sqrt{6\pi}}\right)^n\ exp\left(-\frac{1}{6}\sum_{i=1}^n(X_i^2-2X_i\mu+\mu^2)\right)$$
$$f_\mu(X_1...X_n) = \left(\frac{1}{\sqrt{6\pi}}\right)^n\ exp\left(-\frac{1}{6}\sum_{i=1}^n(X_i^2-2X_i\mu+\mu^2)\right)$$

Using this equation:
$$T(X) = \sum_{i=1}^n X_i$$

Then:
$$f_\mu(X_1...X_n) = \left(\frac{1}{\sqrt{6\pi}}\right)^n\ exp\left(-\frac{1}{6}\sum_{i=1}^nX_i^2+\frac{1}{3}T(X)\mu-\frac{1}{6}n\mu^2\right)$$
$$f_\mu(X_1...X_n) = \left(\frac{1}{\sqrt{6\pi}}\right)^n\ exp\left(-\frac{1}{6}\sum_{i=1}^nX_i^2\right)exp\left(\frac{1}{3}T(X)\mu-\frac{1}{6}n\mu^2\right)$$

$$v(t, \mu) = exp\left(\frac{1}{3}T(X)\mu-\frac{1}{6}n\mu^2\right)$$
$$w(x) = \left(\frac{1}{\sqrt{6\pi}}\right)^n\ exp\left(-\frac{1}{6}\sum_{i=1}^nX_i^2\right)$$

# 5
#### (a)
$$E[\lambda] = \frac{1.5}{3} = 0.5$$

#### (b)
$$Var[\lambda] = \frac{1.5}{3^2} = \frac{1.5}{9} = 0.1667$$

#### (c)
$$p(\lambda | X_1, ..., X_n) = \frac{p(X_1, ..., X_n | \lambda)p(\lambda)}{p(X_1, ..., X_n)}$$
$$f_{\lambda | X_1, ..., X_n}(l; x_1, ..., x_n) = \frac{\left(\prod_{i=1}^n f(x_i; l)\right) g(l)}{\int_0^\infty \left(\prod_{i=1}^n f(x_i; t)\right) g(t)\ dt}$$
$$f_{\lambda | X_1, ..., X_n}(l; x_1, ..., x_n) \propto \left(\prod_{i=1}^n f(x_i; l)\right) g(l)$$
$$f_{\lambda | X_1, ..., X_n}(l; x_1, ..., x_n) \propto \left(\prod_{i=1}^n \frac{\lambda^{x_i}e^{-\lambda}}{x_i!}\right) \frac{3^{1.5}}{\Gamma(1.5)}\lambda^{0.5}e^{-3\lambda}$$
$$f_{\lambda | X_1, ..., X_n}(l; x_1, ..., x_n) \propto \left(\lambda^{\sum x_i}e^{-n\lambda}\right)\lambda^{0.5}e^{-3\lambda}$$
$$f_{\lambda | X_1, ..., X_n}(l; x_1, ..., x_n) \propto \lambda^{\sum x_i + 0.5}e^{-n\lambda-3\lambda}$$
$$f_{\lambda | X_1, ..., X_n}(l; x_1, ..., x_n) \propto \lambda^{(\sum x_i + 1.5) - 1}e^{-(n+3)\lambda}$$
$$f_{\lambda | X_1, ..., X_n}(l; x_1, ..., x_n) \sim Gamma(\alpha^*, \beta^*)$$

Where:
$$\alpha^* = \sum x_i + 1.5$$
$$\beta^* = n+3$$

Then:
$$E[\lambda | X] = \frac{\alpha^*}{\beta^*}$$
$$E[\lambda | X] = \frac{\sum x_i + 1.5}{n + 3}$$

#### (d)
$$Var[\lambda | X] = \frac{\alpha^*}{(\beta^*)^2}$$
$$Var[\lambda | X] = \frac{\sum x_i + 1.5}{(n + 3)^2}$$

# 6
#### (a)
$$E[\lambda] = \frac{\alpha}{\beta}$$
$$E[\lambda] = \frac{13.5}{27}$$
$$E[\lambda] = 0.5$$

#### (b)
$$Var[\lambda] = \frac{\alpha}{\beta^2}$$
$$Var[\lambda] = \frac{13.5}{27^2}$$
$$Var[\lambda] = \frac{13.5}{27^2}$$
$$Var[\lambda] = 0.0185$$

#### (c)
$$f_{\lambda | X_1,...,X_n}(l; x_1, ..., x_n) \propto \left(\prod_{i=1}^n f(x_i; l)\right) g(l)$$
$$f_{\lambda | X_1,...,X_n}(l; x_1, ..., x_n) \propto \left(\lambda^{\sum x_i} e^{-n\lambda}\right) \lambda^{12.5}e^{-27\lambda}$$
$$f_{\lambda | X_1,...,X_n}(l; x_1, ..., x_n) \propto \lambda^{\sum x_i + 12.5} e^{-(n+27)\lambda}$$
$$f_{\lambda | X_1,...,X_n}(l; x_1, ..., x_n) \propto \lambda^{(\sum x_i + 13.5) - 1} e^{-(n+27)\lambda}$$
$$f_{\lambda | X_1,...,X_n}(l; x_1, ..., x_n) \sim Gamma(\alpha^*, \beta^*)$$

Where:
$$\alpha^* = \sum x_i + 13.5$$
$$\beta^* = n + 27$$

Then:
$$E[\lambda | X] = \frac{\alpha^*}{\beta^*}$$
$$E[\lambda | X] = \frac{\sum x_i + 13.5}{n + 27}$$

#### (d)
$$Var[\lambda | X] = \frac{\alpha^*}{(\beta^*)^2}$$
$$Var[\lambda | X] = \frac{\sum x_i + 13.5}{(n+27)^2}$$

# 7
$$p(\pi | X_1, ..., X_n) \propto p(X_1, ..., X_n | \pi) p(\pi)$$
$$f_{\pi | X_1, ..., X_n}(\pi; x_1, ..., x_n) \propto \left(\prod_{i = 1}^n f(x_i; \pi)\right) g(\pi)$$
$$f_{\pi | X_1, ..., X_n}(\pi; x_1, ..., x_n) \propto \left(\prod_{i = 1}^n f(x_i; \pi)\right) g(\pi)$$

Note:
$$f(x_i; \pi) = (1 - \pi)^{x_i - 1}\pi$$
$$g(\pi) \propto \pi^{2 - 1} (1 - \pi)^{2-1}$$
$$g(\pi) \propto \pi (1 - \pi)$$

Then:
$$f_{\pi | X_1, ..., X_n}(\pi; x_1, ..., x_n) \propto \left(\prod_{i = 1}^n (1-\pi)^{x_i-1}\pi\right) \pi (1 - \pi)$$
$$f_{\pi | X_1, ..., X_n}(\pi; x_1, ..., x_n) \propto (1-\pi)^{\sum x_i-n} \pi^{n+1} (1 - \pi)$$
$$f_{\pi | X_1, ..., X_n}(\pi; x_1, ..., x_n) \propto \pi^{n+1} (1-\pi)^{\sum x_i-n+1}$$
$$f_{\pi | X_1, ..., X_n}(\pi; x_1, ..., x_n) \propto \pi^{(n+2)-1} (1-\pi)^{(\sum x_i-n+2)-1}$$
$$f_{\pi | X_1, ..., X_n}(\pi; x_1, ..., x_n) \sim Beta(\alpha^*, \beta^*)$$

Where:
$$\alpha^* = n+2$$
$$\beta^* = \sum x_i-n+2$$

Then:
$$E[\pi|X] = \frac{\alpha^*}{\alpha^* + \beta^*}$$
$$E[\pi|X] = \frac{n+2}{n+2 + \sum x_i-n+2}$$
$$E[\pi|X] = \frac{n+2}{4 + \sum x_i}$$
