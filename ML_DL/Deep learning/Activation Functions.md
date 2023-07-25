# Introduction

An **activation function** is a **function** that is added to an **artificial neural network** in order to help the network learn **complex patterns in the data**. When comparing with a neuron-based model that is in our brains, the **activation function** is at the end deciding what is to be fired to the next neuron.

> In [**artificial neural networks**](https://en.wikipedia.org/wiki/Artificial_neural_network), the **activation function** of a node defines the output of that node given an input or set of inputs. A standard [**integrated circuit**](https://en.wikipedia.org/wiki/Integrated_circuit) can be seen as a [**digital network**](https://en.wikipedia.org/wiki/Digital_electronics) of activation functions that can be “ON” (1) or “OFF” (0), depending on input. — **Wikipedia**

So, summing it up, **activation functions are mathematical equations that determine the output of a neural network.**

![](https://miro.medium.com/max/835/1*kyNdmhtc5oo4Q0-wtk7NTQ.png)

Before jumping in-depth about the different types of activation functions, let’s take a quick look into how an artificial neuron works -

![](https://miro.medium.com/max/875/1*k9pQ6T6claVVn39ZMcqlKg.png)

A mathematical visualization of the processes described above can be shown as-

![](https://miro.medium.com/max/875/1*0wDAsK-gy8NMxMyimPjw_g.png)



# 1. Sigmoid Activation Function -

![](https://miro.medium.com/max/875/1*-NCZJnLMt-sX-zCJ4DRPYQ.png)

The **Sigmoid Function** looks like an **S-shaped** curve.

Formula : **f(z) = 1/(1+ e^-z)**

Why and when do we use the Sigmoid Activation Function?

1.  The output of a sigmoid function **ranges between 0 and 1**. Since, output values bound between 0 and 1, it **normalizes** the output of each neuron.
2.  Specially used for models where we have to **predict the probability** as an output. Since the probability of anything exists only between the range of **0 and 1,** sigmoid is the **perfect** choice.
3.  **Smooth gradient**, preventing “jumps” in output values.
4.  The function is **differentiable**.That means, we can find the slope of the sigmoid curve at any two points.
5.  **Clear predictions**, i.e very close to 1 or 0.

What are some **disadvantages** of the Sigmoid activation function?

1.  Prone to gradient vanishing (when the **sigmoid** function value is either too high or too low, the derivative becomes very small i.e. << 1. This causes **vanishing gradients** and poor learning for deep networks.)
2.  The function output is **not centered on 0,** which will reduce the efficiency of weight update.
3.  The sigmoid function performs exponential operations, which is slower for computers.

# 2. Tanh or Hyperbolic Tangent Activation Function -

![](https://miro.medium.com/max/554/1*WeuJzmlt3iNVWsUsvf24Eg.png)

The tanh activation function is also **sort of sigmoidal (S-shaped).**

![](https://miro.medium.com/max/805/1*SBcMLQ2rP77M9uuXYtX0hA.png)

Formula of tanh activation function

**Tanh is a hyperbolic tangent function**. The curves of tanh function and sigmoid function are relatively similar. But it has some advantage over the sigmoid function. Let's look at what it is.

Why is tanh **better compared** to sigmoid activation function?

![](https://miro.medium.com/max/875/1*p5Vbj8YE3l4JdgKOy6YqVg.jpeg)

1.  First of all, when the input is large or small, the output is **almost smooth and the gradient is small**, which is not conducive to weight update. The difference is the output interval. The output interval of tanh is 1, and the whole function is **0-centric, which is better than sigmoid.**
2.  The **major advantage** is that the **negative inputs** will be mapped strongly **negative** and the **zero inputs** will be mapped **near zero** in the tanh graph.

> N**ote:** In general **binary classification problems**, the tanh function is used for the **hidden layer** and the sigmoid function is used for the **output layer**. However, these are **not static**, and the specific activation function to be used must be analyzed according to the specific problem, or it depends on debugging.

# 3. ReLU (Rectified Linear Unit) Activation Function-

![](https://miro.medium.com/max/750/1*jOU3PnNiB0YIH1Y_t-iXng.png)

The ReLU is half rectified (from the bottom). f(z) is zero when z is less than zero and f(z) is equal to z when z is above or equal to zero.

![](https://miro.medium.com/max/636/1*Eav-4gyK6dKvV4MGf-Gq6w.png)

**Range:** [ 0 to infinity)

The **ReLU (Rectified Linear Unit)** function is an activation function that is currently **more popular** compared to other activation functions in deep learning.

Compared with the sigmoid function and the tanh function, it has the following **advantages**:

1.  When the input is positive, there is **no gradient saturation problem.**
2.  The calculation speed is much **faster**. The ReLU function has only a linear relationship. Whether it is forward or backward, it is much faster than sigmoid and tanh. (Sigmoid and tanh need to calculate the exponent, which will be slower.)

Of course, there are **disadvantages:**

1) **Dead ReLU problem**- When the input is negative, ReLU is completely **inactive**, which means that once a negative number is entered, **ReLU will die**. In this way, in the forward propagation process, it is not a problem. Some areas are sensitive and some are insensitive. But in the **back propagation** process, if you enter a negative number, the **gradient will be completely zero,** which has the **same** problem as the sigmoid function and tanh function.

2) We find that the output of the ReLU function is either 0 or a positive number, which means that the ReLU function is **not a 0-centric function.**

# 4. Leaky ReLU Activation Function-

An activation function **specifically designed to compensate** for the dying ReLU problem.

![](https://miro.medium.com/max/875/1*ZGazDurOnSW8sBsSNVEVHA.jpeg)

ReLU vs Leaky ReLU

Why Leaky ReLU is **better** than ReLU?

![](https://miro.medium.com/max/875/1*EDdrPlFPyxNPF377lrDzMw.png)

1.  The leaky ReLU **adjusts the problem of zero gradients** for negative value, by giving a very **small linear component of x** to negative inputs**(0.01x)**.
2.  The leak helps to increase the range of the ReLU function. Usually, the value of **a** is **0.01** or so.
3.  Range of the Leaky ReLU is **(-infinity to infinity).**

> **Note :** In theory, Leaky ReLU has all the advantages of ReLU, plus there will be no problems with Dead ReLU, but in actual operation, it has not been fully proved that Leaky ReLU is always better than ReLU.

# 5. ELU (Exponential Linear Units) function-

![](https://miro.medium.com/max/368/1*T1kXV0Jys4-yMTIiWg88Xg.png)

ELU vs Leaky ReLU vs ReLU

**ELU** is also **proposed to solve the problems** of ReLU. In contrast to ReLUs, ELUs have **negative values** which pushes the **mean of the activations** closer to **zero.** Mean activations that are closer to zero **enable faster learning** as they bring the **gradient closer to the natural gradient.**

![](https://miro.medium.com/max/811/1*SPRharcieVjGvA2yWqENPA.png)

Obviously, **ELU has all the advantages of ReLU**, and:

-   **No Dead ReLU** issues,the mean of the output is close to 0, **zero-centered**.
-   In **contrast** to ReLUs, ELUs have negative values which allows them to push mean unit activations closer to zero like **batch normalization** but with **lower computational complexity**. Mean shifts toward zero speed up learning by bringing the normal gradient closer to the unit natural gradient because of a **reduced bias shift effect.**
-   ELUs **saturate to a negative value** with smaller inputs and thereby decrease the forward propagated variation and information.

One **small problem** is that it is slightly more **computationally intensive.** Similar to Leaky ReLU, although theoretically better than ReLU, there is currently no good evidence in practice that ELU is always better than ReLU.

# 6. PRelu (Parametric ReLU)-

![](https://miro.medium.com/max/840/1*BmVRlcbyW-ri03BRm9HV6g.png)

**PReLU** is also an **improved** version of **ReLU.**

![](https://miro.medium.com/max/720/1*8zNvM6g04IikhkT0JMzn6w.png)

We look at the formula of PReLU. The parameter **α** is generally a number between 0 and 1, and it is generally relatively small, such as a few zeros.

-   if **aᵢ=0**, f becomes ReLU
-   if **aᵢ>0**, f becomes leaky ReLU
-   if **aᵢ is a learnable parameter**, f becomes PReLU

Coming to the **advantages** of PReLU-

1.  In the negative region, PReLU has a **small slope**, which can also **avoid** the problem of **ReLU death**.
2.  Compared to ELU, PReLU is a **linear operation** in the negative region. Although the slope is small, it **does not tend to 0**, which is a certain advantage.

# 7. Softmax

![](https://miro.medium.com/max/480/1*AHitfux7ddZiiGiC6jrlLA.jpeg)

**Softmax** is used as the **activation function** for multi-class classification problems where class membership is required on more than two class labels. For an arbitrary real vector of length K, Softmax can **compress it into a real vector of length K** with a value in the **range (0, 1)**, and the sum of the elements in the vector is 1.

![](https://miro.medium.com/max/875/1*t2FbP10uDFZrufDCYELWFA.jpeg)

> Softmax is different from the normal max function: the max function only outputs the largest value, and Softmax ensures that smaller values have a smaller probability and will not be discarded directly. It is a **“max”** that is **“soft”**; it can be thought to be a **probabilistic or “_softer_” version of the argmax function.**

The denominator of the Softmax function combines all factors of the original output value, which means that the different probabilities obtained by the Softmax function are related to each other.

The **major drawback** in the softmax activation function is that it is -

1.  Non-differentiable at zero and ReLU is unbounded.

2. The gradients for negative input are zero, which means for activations in that region, the weights are not updated during backpropagation. This can create dead neurons that never get activated.

# 8. Swish (A Self-Gated) Function

![](https://miro.medium.com/max/875/1*avgXN89BZtU8Amfh7fex7w.png)

The formula is: **y = x * sigmoid (x)**

Swish’s design was inspired by the use of sigmoid functions for gating in LSTMs and highway networks. We use the same value for gating to simplify the gating mechanism, which is called **self-gating**.

> The **advantage of self-gating** is that it only requires a **simple scalar input,** while normal gating requires multiple scalar inputs. This feature enables self-gated activation functions such as Swish to easily **replace activation functions that take a single scalar as input (such as ReLU)** without changing the hidden capacity or number of parameters.

**Note:** Swish activation function can only be implemented when your **neural network is ≥ 40 layers.**

The **major advantages** of the Swish activation function are as follows:

1.**Unboundedness** is helpful to prevent the gradient from gradually approaching 0 during slow training, causing saturation.

(At the same time, being bounded has advantages, because bounded active functions can have strong regularization, and larger negative inputs will be resolved.)

2. Derivative **always > 0.**

3. **Smoothness** also plays an important role in **optimization and generalization.**

# 9. Maxout

![](https://miro.medium.com/max/750/1*Ae28NCJH6ZYooc64jIPYQw.jpeg)

A **Maxout** layer is simply a layer where the activation function **is the max of the inputs.** As stated in the **paper**, even an MLP with **2 maxout units** can **approximate any function.**

A single Maxout unit can be interpreted as making a **piecewise linear approximation (PWL)** to a **real-valued function** where the line segment between any two points on the graph of the function lies above or on the graph (**convex function**).

![](https://miro.medium.com/max/875/1*erIcz2XPYd8r4L86icbA9Q.png)

Maxout can also be implemented for a **d-dimensional vector(V).**

![](https://miro.medium.com/max/875/1*t8cNgQcRBYPtezzl0T1WVw.jpeg)

Consider, two convex functions **h1(x) and h2(x)**, approximated by two Maxout units. By the above preposition, the function **g(x) is a continuous PWL function.**

![](https://miro.medium.com/max/565/1*rKsfpy6_xsBBxiuE_b6ZRA.png)

Hence, it is found that a **Maxout layer consisting of two Maxout units can approximate any continuous function arbitrarily well.**

![](https://miro.medium.com/max/875/1*ILlj6PNNLiX96ggk6WNEeA.png)

# 10. Softplus-

![](https://miro.medium.com/max/875/1*enmbqoxIDqtM6kODX7Sngg.png)

**Softplus function**: f(x) = **ln(1+exp x)**

The **derivative** of softplus is -

f ′(x)=exp(x) / ( 1+exp⁡ x )

= **1/ (1 +exp(−x ))**

,which is also called the **logistic/sigmoid function.**

The softplus function is similar to the ReLU function, but it is **relatively smooth.** It is unilateral suppression like ReLU.

It has a wide acceptance range **(0, + inf)**.