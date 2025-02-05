# 1
#### Step 1
$$E[X] = \int_0^\infty x \lambda e^{-\lambda x}\ dx$$

$$E[X] = \lambda \int_0^\infty xe^{-\lambda x}\ dx$$

$$E[X] = \frac{1}{\lambda} = \bar X$$

$$\hat \lambda_{MOM} = \frac{1}{\bar X}$$

This result will match the result from MLE.

#### Step 2
$$L(\lambda) = \prod_{i = 1}^n \lambda e^{-\lambda x_i}$$

$$l(\lambda) = n\ log\ \lambda - \lambda \sum_{i = 1}^n x_i$$
$$\frac{\delta l(\lambda)}{\delta \lambda} = \frac{n}{\lambda} - \sum_{i = 1}^n x_i = 0$$

$$\frac{n}{\lambda} = \sum_{i = 1}^n x_i$$

$$\hat \lambda_{MLE} = \frac{n}{\sum_{i = 1}^n x_i}$$

$$\hat \lambda_{MLE} = \frac{1}{\bar X}$$

This result matches the MOM.

# 2
#### a - obtain MOM estimator
$$E[X] = \int_0^\infty \frac{x^2}{\theta^2} exp\left(-\frac{x^2}{2\theta^2}\right)\ dx$$

$$E[X] = \frac{\sqrt\pi \theta}{\sqrt 2} = \bar X$$

$$\hat \theta_{MOM} = \frac{\sqrt 2}{\sqrt \pi} \bar X$$

#### a - compute bias and MSE
$$Bias[\hat \theta_{MOM}] = E[\hat \theta_{MOM}] - \theta$$

$$Bias[\hat \theta_{MOM}] = \frac{\sqrt 2}{\sqrt \pi} E[\bar X] - \theta$$

$$Bias[\hat \theta_{MOM}] = \frac{\sqrt 2}{\sqrt \pi} \frac{\sqrt\pi \theta}{\sqrt 2} - \theta$$

$$Bias[\hat \theta_{MOM}] = 0$$

$$MSE[\hat \theta_{MOM}] = Var[\hat \theta_{MOM}] + Bias[\hat \theta_{MOM}]$$

$$MSE[\hat \theta_{MOM}] = Var[\hat \theta_{MOM}] + 0$$

$$MSE[\hat \theta_{MOM}] = \frac{2}{\pi} Var[\bar X]$$

$$MSE[\hat \theta_{MOM}] = \frac{2}{\pi} \frac{Var[X]}{n}$$

$$E[X^2] = \int_0^\infty \frac{x^3}{\theta^2} exp\left(-\frac{x^2}{2\theta^2}\right)\ dx$$

$$E[X^2] = 2\theta^2$$

$$Var[X] = E[X^2] - (E[X])^2 = 2\theta^2 - \frac{\pi}{2}\theta^2$$

$$Var[X] = \left(2 - \frac{\pi}{2}\right) \theta^2$$

$$MSE[\hat \theta_{MOM}] = \frac{2\theta^2(2 - \frac{2}{\pi})}{n\pi}$$

#### b - obtain MLE
$$L(\theta) = \prod_{i = 1}^n \frac{x_i}{\theta^2} exp\left(-\frac{x_i^2}{2\theta^2}\right)$$

$$l(\theta) = \sum_{i=1}^n log(x_i) - 2n\ log\ \theta - \sum_{i = 1}^n \frac{x_i^2}{2\theta^2}$$

$$\frac{\delta l(\theta)}{\delta \theta} = - \frac{2n}{\theta} + \sum_{i = 1}^n \frac{x_i^2}{\theta^3} = 0$$

$$\sum_{i = 1}^n \frac{x_i^2}{\theta^3} = \frac{2n}{\theta}$$

$$\sum_{i = 1}^n x_i^2 = 2n\theta^2$$

$$\theta^2 = \frac{1}{2n} \sum_{i = 1}^n x_i^2$$

$$\hat\theta_{MLE} = \sqrt{\frac{1}{2n} \sum_{i = 1}^n x_i^2}$$

This result differs from our MOM.