## Introduction

Wiki defininition: In mathematics, gradient descent (also often called steepest descent) is a [first-order](https://en.wikipedia.org/wiki/Category:First_order_methods "Category:First order methods") [iterative](https://en.wikipedia.org/wiki/Iterative_algorithm "Iterative algorithm") [optimization](https://en.wikipedia.org/wiki/Mathematical_optimization "Mathematical optimization") [algorithm](https://en.wikipedia.org/wiki/Algorithm "Algorithm") for finding a [local minimum](https://en.wikipedia.org/wiki/Local_minimum "Local minimum") of a [differentiable function](https://en.wikipedia.org/wiki/Differentiable_function "Differentiable function"). The idea is to take repeated steps in the opposite direction of the [gradient](https://en.wikipedia.org/wiki/Gradient "Gradient") (or approximate gradient) of the function at the current point, because this is the direction of steepest descent. Conversely, stepping in the direction of the gradient will lead to a [local maximum](https://en.wikipedia.org/wiki/Local_maximum "Local maximum") of that function; the procedure is then known as gradient ascent.

Other definition: Gradient descent is an optimization algorithm that is used to minimize a cost function in machine learning and deep learning.

## Intuition

Gradient descent uses the gradient of the cost function to determine the direction in which the parameters should be updated to minimize the cost. The gradient is a vector that points in the direction of the steepest increase of the cost function. So, to minimize the cost function, the parameters are updated in the opposite direction of the gradient.

Each iteration, the parameters are updated by a small step called the learning rate. The learning rate determines the size of the step that the parameters are updated. A small learning rate will make the optimization converge slowly, but it will be less likely to overshoot the optimal solution. A large learning rate will make the optimization converge faster, but it will be more likely to overshoot the optimal solution.

The mathematical formula for gradient descent for a cost function J(θ) with respect to parameters θ is:

*θ = θ - α * ∇J(θ)*

Where:

-   θ is the vector of parameters of the model
-   α is the learning rate, a small positive value that determines the step size of the update
-   ∇J(θ) is the gradient of the cost function J(θ) with respect to the parameters θ.

It's worth noting that if the cost function is a convex function, meaning it has only one global minimum, the algorithm will converge to the optimal solution. But if the cost function has multiple local minima, it's possible that the algorithm will converge to a local minimum instead of the global minimum.
![[Pasted image 20230127010753.png]]

## Function requirements

Gradient descent algorithm does not work for all functions. There are two specific requirements. A function has to be:

#### Differentiable
First, what does it mean it has to be **differentiable**? If a function is differentiable it has a derivative for each point in its domain — not all functions meet these criteria. First, let’s see some examples of functions meeting this criterion:
![[Pasted image 20230127143722.png]]
Typical non-differentiable functions have a step a cusp or a discontinuity:
![[Pasted image 20230127143748.png]]

#### Convex
For a univariate function, this means that the line segment connecting two function’s points lays on or above its curve (it does not cross it). If it does it means that it has a local minimum which is not a global one.
![[Pasted image 20230127143955.png]]
![[Pasted image 20230127144042.png]]

## Gradient

Before jumping into code one more thing has to be explained — what is a gradient. Intuitively it is a slope of a curve at a given point in a specified direction.

In the case of **a univariate function**, it is simply the **first derivative at a selected point**. In the case of **a multivariate function**, it is a **vector of derivatives** in each main direction (along variable axes). Because we are interested only in a slope along one axis and we don’t care about others these derivatives are called **partial derivatives**.

A gradient for an n-dimensional function f(x) at a given point p is defined as follows:

![](https://miro.medium.com/max/184/1*duhfS4ufOrjtXJw_rHg_6Q.gif)

The upside-down triangle is a so-called _nabla_ symbol and you read it “del”. To better understand how to calculate it let’s do a hand calculation for an exemplary 2-dimensional function below.

![](https://miro.medium.com/max/171/1*z-6cHPM1q_HtB4HrAXZ-FQ.gif)

![](https://miro.medium.com/max/875/1*fWc_cUNDEn4LpS6aissyXA.jpeg)

3D plot; Image by author

Let’s assume we are interested in a gradient at point p(10,10):

![](https://miro.medium.com/max/289/1*HJAz03MhHAFI-l3AeLrSYg.gif)

so consequently:

![](https://miro.medium.com/max/165/1*MMZM3DhpwFmSr9mkc5fZXg.gif)

![](https://miro.medium.com/max/176/1*4kVChbyOJL49FDICIiGPnQ.gif)

By looking at these values we conclude that the slope is twice steeper along the y axis.

## Algorithm

Gradient Descent Algorithm iteratively calculates the next point using gradient at the current position, scales it (by a learning rate) and subtracts obtained value from the current position (makes a step). It subtracts the value because we want to minimise the function (to maximise it would be adding). This process can be written as:

![](https://miro.medium.com/max/206/1*GixQ9i6cQSvlfoe_XZdcog.gif)

There’s an important parameter **η** which scales the gradient and thus controls the step size. In machine learning, it is called **learning rate** and have a strong influence on performance.

-   The smaller learning rate the longer GD converges, or may reach maximum iteration before reaching the optimum point
-   If learning rate is too big the algorithm may not converge to the optimal point (jump around) or even to diverge completely.

In summary, Gradient Descent method’s steps are:

1.  choose a starting point (initialisation)
2.  calculate gradient at this point
3.  make a scaled step in the opposite direction to the gradient (objective: minimise)
4.  repeat points 2 and 3 until one of the criteria is met:

-   maximum number of iterations reached
-   step size is smaller than the tolerance (due to scaling or a small gradient).

#### Data Scaling
Make sure to scale the data if it’s on a very different scales. If we don’t scale the data, the level curves (contours) would be narrower and taller which means it would take longer time to converge

![](https://miro.medium.com/max/875/1*vXpodxSx-nslMSpOELhovg.png)
Gradient descent: normalized versus unnormalized level curves.

Scale the data to have μ = 0 and σ = 1. Below is the formula for scaling each example:
![](https://miro.medium.com/max/716/1*2g6dhidPigWEuAFyNHL8iw.png)

## Examples

#### Quadratic function
Let’s take a simple quadratic function defined as:
![](https://miro.medium.com/max/185/1*759WQyYJhCOmTg9-bUyajw.gif)
Because it is an univariate function a gradient function is:
![](https://miro.medium.com/max/146/1*XdVinZof2X_-kKO0NzLT7g.gif)
Let’s write these functions in Python:
```python
def func1(x):
return x**2-4*x+1
def gradient_func1(x):
return 2*x - 4
```
For this function, by taking a learning rate of 0.1 and starting point at x=9 we can easily calculate each step by hand. Let’s do it for the first 3 steps:

![](https://miro.medium.com/max/370/1*l4ghz3vtdMDgc0XPFHwAZw.gif)

The python function is called by:
```python
history, result = gradient_descent(9, gradient_func1, 0.1, 100)
```

The animation below shows steps taken by the GD algorithm for learning rates of 0.1 and 0.8. As you see, for the smaller learning rate, as the algorithm approaches the minimum the steps are getting gradually smaller. For a bigger learning rate, it is jumping from one side to another before converging.
![](https://miro.medium.com/max/875/1*v5bc1TzeMKpzTAgorjOoHQ.gif)
First 10 steps taken by GD for small and big learning rate

Trajectories, number of iterations and the final converged result (within tolerance) for various learning rates are shown below:
![](https://miro.medium.com/max/875/1*GR914FuA4pVTTXEpVDJ2Ng.png)

#### A function with a saddle point
Now let’s see how the algorithm will cope with a semi-convex function we investigated mathematically before.
![](https://miro.medium.com/max/195/1*o2y5n16SH8C_kuI0OCApJw.gif)
Below results for two learning rates and two different staring points.

![](https://miro.medium.com/max/875/1*dA6jHOoKa-uNo1sJO2XogA.png)
GD trying to escape from a saddle point
Below an animation for a learning rate of 0.4 and a starting point _x=-0.5_.
![](https://miro.medium.com/max/675/1*Z3wjHCFAehYXYG9lOiqiEw.gif)
Animation of GD trying to escape from a saddle point

Now you see that the existence of a saddle point imposes a real challenge for the first-order gradient descent algorithms like GD and obtaining a global minimum is not guaranteed. Second-order algorithms deal with these situations better (e.g. Newton-Raphson method).

Investigation of saddle points and how to escape from them is a subject of ongoing studies and various solutions were proposed. For example, Chi Jin and M. Jordan proposed a Perturbing Gradient Descent algorithm — details you find in [their blog post](https://bair.berkeley.edu/blog/2017/08/31/saddle-efficiency/).

## Variants of GD

#### Batch Gradient Descent
Batch Gradient Descent is when we sum up over all examples on each iteration when performing the updates to the parameters. Therefore, for each update, we have to sum over all examples:
![](https://miro.medium.com/max/818/1*nu5id-pd3BNCl1KktBxP4g.png)

```python
for i in range(num_epochs):  
    grad = compute_gradient(data, params)  
    params = params — learning_rate * grad
```

The main advantages:
-   We can use fixed learning rate during training without worrying about learning rate decay.
-   It has straight trajectory towards the minimum and it is guaranteed to converge in theory to the global minimum if the loss function is convex and to a local minimum if the loss function is not convex.
-   It has unbiased estimate of gradients. The more the examples, the lower the standard error.

The main disadvantages:
-   Even though we can use vectorized implementation, it may still be slow to go over all examples especially when we have large datasets.
-   Each step of learning happens after going over all examples where some examples may be redundant and don’t contribute much to the update.

#### Mini-batch Gradient Descent
Instead of going over all examples, Mini-batch Gradient Descent sums up over lower number of examples based on the batch size. Therefore, learning happens on each mini-batch of _b_ examples:

![](https://miro.medium.com/max/875/1*9AlSFxKa6iyqR7qqlOQSQQ.png)

-   Shuffle the training data set to avoid pre-existing order of examples.
-   Partition the training data set into _b_ mini-batches based on the batch size. If the training set size is not divisible by batch size, the remaining will be its own batch.
```python
for i in range(num_epochs):  
    np.random.shuffle(data)  
    for batch in radom_minibatches(data, batch_size=32):  
        grad = compute_gradient(batch, params)  
        params = params — learning_rate * grad
```

The batch size is something we can tune. It is usually chosen as power of 2 such as 32, 64, 128, 256, 512, etc. The reason behind it is because some hardware such as GPUs achieve better run time with common batch sizes such as power of 2.

The main advantages:
-   Faster than Batch version because it goes through a lot less examples than Batch (all examples).
-   Randomly selecting examples will help avoid redundant examples or examples that are very similar that don’t contribute much to the learning.
-   With batch size < size of training set, it adds noise to the learning process that helps improving generalization error.
-   Even though with more examples the estimate would have lower standard error, the return is less than linear compared to the computational burden we incur.

The main disadvantages:
-   It won’t converge. On each iteration, the learning step may go back and forth due to the noise. Therefore, it wanders around the minimum region but never converges.
-   Due to the noise, the learning steps have more oscillations (see figure 4) and requires adding learning-decay to decrease the learning rate as we become closer to the minimum.

![](https://miro.medium.com/max/875/1*5mHkZw3FpuR2hBNFlRxZ-A.png)
Gradient descent: batch versus mini-batch loss function

With large training datasets, we don’t usually need more than 2–10 passes over all training examples (epochs). Note: with batch size _b = m_ (number of training examples), we get the Batch Gradient Descent.

#### Stochastic Gradient Descent
Instead of going through all examples, Stochastic Gradient Descent (SGD) performs the parameters update on each example (x^i,y^i). Therefore, learning happens on every example:
![](https://miro.medium.com/max/851/1*ecOF_YWCDJE9GFcEzKzlPw.png)
-   Shuffle the training data set to avoid pre-existing order of examples.
-   Partition the training data set into _m_ examples.

```python
for i in range(num_epochs):  
    np.random.shuffle(data)  
    for example in data:  
        grad = compute_gradient(example, params)  
        params = params — learning_rate * grad
```

It shares most of the advantages and the disadvantages with mini-batch version. Below are the ones that are specific to SGD:

-   It adds even more noise to the learning process than mini-batch that helps improving generalization error. However, this would increase the run time.
-   We can’t utilize vectorization over 1 example and becomes very slow. Also, the variance becomes large since we only use 1 example for each learning step.

Below is a graph that shows the gradient descent’s variants and their direction towards the minimum:
![](https://miro.medium.com/max/875/1*PV-fcUsNlD9EgTIc61h-Ig.png)
Gradient descent variants’ trajectory towards minimum
As the figure above shows, SGD direction is very noisy compared to mini-batch.

## Implementation in Python

```python
import numpy as np

def gradient_descent(start, gradient, learn_rate, max_iter, tol=0.01):
  steps =  [start] # history tracking
  x = start

  for _ in range(max_iter):
    diff = learn_rate * gradient(x)
    if np.abs(diff)<tol:
      break    
    x = x - diff
    steps.append(x) # history tracing

  return steps, x
```

This function takes 5 parameters:
1. starting point - in our case, we define it manually but in practice, it is often a random initialisation
2. gradient function - has to be specified before-hand
3. learning rate - scaling factor for step sizes
4. maximum number of iterations
5. tolerance to conditionally stop the algorithm (in this case a default value is 0.01)

![[Pasted image 20230127170530.png]]
## Interview questions

_Q1_:  What is the idea behind the _Gradient Descent_?

_Q2_:   Explain the intuition behind Gradient Descent algorithm

_Q3_:   What is the difference between _Cost Function_ vs _Gradient Descent_?

_Q4_:   What is the difference between _Maximum Likelihood Estimation_ and _Gradient Descent_?

_Q5_:   Can _Gradient Descent_ be applied to _Non-Convex Functions_?

_Q6_:   What are some _types_ of _Gradient Descent_ do you know?

_Q7_:   Compare the _Mini-batch Gradient Descent_, _Stochastic Gradient Descent_, and _Batch Gradient Descent_

_Q8_:   Explain how does the _Gradient descent_ work in _Linear Regression_

_Q9_:   In which case you would use _Gradient Descent method_ or _Ordinary Least Squares_ and why?

_Q10_:   Name some _Evaluation Metrics_ for Regression Model and when you would use one?

_Q11_:   How does the _Adam_ method of Stochastic Gradient Descent work?

_Q12_:   How does _Batch Size_ affect the Convergence of SGD and why?

_Q13_:   When should we use Algorithms like Adam as opposed to SGD?

_Q14_:   Compare _Batch Gradient Descent_ and _Stochastic Gradient Descent_

_Q15_:   When Optimizing a Neural Network, how do you define the Termination Condition for Gradient Descent?

_Q16_:   How do Gradient-Based Algorithms deal with the flat regions with desired points?

Q17_:   What are some necessary Mathematical Properties a Loss Function needs to have in Gradient-Based Optimization?

_Q18_:   What is the difference between _Gradient Descent_ and _Stochastic Gradient Descent_?

_Q19_:   Does Gradient Descent always _converge_ to an _optimum_?

_Q20_:   How is the _Adam Optimization Algorithm_ different when compared to _Stochastic Gradient Descent_?

_Q21_:   Name some advantages of using _Gradient descent_ vs _Ordinary Least Squares_ for Linear Regression

_Q22_:   What is the difference between _Momentum based Gradient Descent_ and _Nesterov's Accelerated Gradient Descent_?

_Q23_:   In what situations would you prefer _Coordinate Descent_ over _Gradient Descent_?

_Q24_:   What is the _Mirror Descent_?

_Q25_:   Explain in detail how _Momentum-based Gradient Descent_ and _Nesterov's Accelerated Gradient Descent_ work

_Q26_:   Explain _Mathematically_, how Stochastic Gradient Descent saves time compared to Standard Gradient Descent.

_Q27_:   For both _Convex_, and _Non-Convex_ Problems, does the Gradient in SGD always point to the global extreme value?

_Q28_:   How would you train _Linear Regression_ model using _Gradient Descent_? Implement in Python

*Q29*:   What are some common cases where gradient descent may fail to converge?

## Resources

#### Articles
https://towardsdatascience.com/gradient-descent-algorithm-and-its-variants-10f652806a3
https://towardsdatascience.com/gradient-descent-algorithm-a-deep-dive-cf04e8115f21

#### Videos

<iframe width="560" height="315" src="https://www.youtube.com/embed/ORyfPJypKuU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
<iframe width="560" height="315" src="https://www.youtube.com/embed/Jyo53pAyVAM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
<iframe width="560" height="315" src="https://www.youtube.com/embed/V7KBAa_gh4c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
<iframe width="560" height="315" src="https://www.youtube.com/embed/_scscQ4HVTY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

