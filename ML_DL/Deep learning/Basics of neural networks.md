# What is a Neural Network?

How do we define a Neural Network? It is essentially a naive implementation of how our brains might work. It’s not a very accurate representation but it tries to replicate some of the methods our brain uses to learn from it’s mistakes. Let’s look at how our brains work from a simplified perspective and then compare it with a Neural Network.

The brain is essentially a bunch of neurons connected to each other in a huge interconnected network. There are a lot of neurons and even more connections. These neurons pass a small amount of electrical charge to each other as a way to transmit information. Another important feature of these neural connections is that the connection between two neurons can be vary between **strong** and **weak.** A strong connection allows more charge to flow between them and a weak one allows lesser. A neuron pathway which frequently transmits charge will eventually become a **strong pathway.**

Now as the brain takes input from any external source, let’s say for example we touch a hot pan. The nerves from our hand transmits info to certain neurons in our brain. Now there is a pathway from these neurons to the neurons which control our hand. And in these cases our brain has **learnt** that the best option is to move our hand from the pan ASAP. Hence this certain **pathway** between the neurons taking input from the hand and the neurons controlling the hand will be **strong.**

Neural pathways become **stronger** upon frequent usage, and our brain essentially tries to use pathways which have proven to give us better results over time. So essentially as we humans live our lives and decide whether our actions are good or bad, we are training our brain to make sure we don’t repeat our previous mistakes or keep doing things which we think resulted in a good outcome. This is a highly simplified explanation and doesn’t fully portray what’s going on, but hopefully it helps you understand the basic concept.

# Functionality of a Neural Network

Now let’s understand how a Neural Network is represented. A neural network consists of many **Nodes** (Neurons) in many **layers.** Each layer can have _any number_ of nodes and a neural network can have _any number_ of layers. Let’s have a closer look at a couple of layers.

![](https://miro.medium.com/max/544/1*pCM9ttrYaeM8CAi0DyxwLA.png)

Layers in a Neural Network

Now as you can see, there are many interconnections between both the layers. These interconnections exist between **each node** in the first layer with **each and every node** in the second layer. These are also called the **weights** between two layers.

Now let’s see how exactly these weights function.

![](https://miro.medium.com/max/875/1*SaQMHTLi4C7MIA4IzjAXJw.png)

Here we take the example of what’s going on with a **single node** in the network. Here we are considering all the values from the **previous layer** connecting to **one node in the next layer**.

> Y is the **final value** of the node.
> 
> W represents the **weights** between the nodes in the previous layer and the output node.
> 
> X represents the **values of the nodes** of the previous layer.
> 
> B represents **bias**, which is an additional value present for each neuron. Bias is essentially a weight without an input term. It’s useful for having an **extra bit of adjustability** which is not dependant on previous layer.
> 
> H is the **intermediate node value**. This is not the final value of the node.
> 
> f( ) is called an **Activation Function** and it is something we can choose. We will go through it’s importance later.

So finally, the output value of this node will be **f(0.57)**

Now let’s look at the calculations between two complete layers:

![](https://miro.medium.com/max/875/1*dbf_lVYurfSxvABaQhakxg.png)

The weights in this case have been color coded for easier understanding. We can represent the entire calculation as a matrix multiplication. If we represent the weights corresponding to each input node as vectors and arrange them horizontally, we can form a matrix, this is called the **weight matrix.** Now we can multiply the weight matrix with the input vector and then add the bias vector to get the intermediate node values.

![](https://miro.medium.com/max/875/1*OCyfb1kJNZbZx1Ozi5RSAQ.png)

We can summarize the entire calculation as **Y = f(W*X + B)**. Here, Y is the output vector, X is the input vector, W represents the weight matrix between the two layers and B is the bias vector.

We can determine the size of the weight matrix by looking at the number of input nodes and output nodes. An M*N weight matrix means that it is between two layers with the **first layer** having **N nodes** and the **second layer** having **M nodes**.

![](https://miro.medium.com/max/875/1*-Eeve28pEqkXioOPOv4G7Q.png)

Now let’s look at a complete neural network.

![](https://miro.medium.com/max/875/1*tIwGoSbyUZEHNp93pRqROw.png)

This is a small neural network of four layers. The input layer is where we feed our **external stimulus**, or basically the **data** from which our neural network has to **learn from**. The output layer is where we are supposed to get the target value, this represents what exactly our neural network is trying to **_predict_ or _learn_**_._ All layers in between are called **hidden layers.** When we feed the inputs into the first layer, the values of the nodes will be calculated layer by layer using the matrix multiplications and activation functions till we get the final values at the output layer. That is how we get an **output** from a neural network.

So essentially a neural network is, simply put, a series of matrix multiplications and activation functions. When we input a vector containing the input data, the data is multiplied with the sequence of weight matrices and subjected to activation functions till it reaches the output layer, which contains the **predictions** of the neural network corresponding to that particular input.

# Role of Activation Function

Even though our neural network has a very complex configuration of weights, it will not be able to solve a problem without the activation function. The reason for this lies in the concept of **Non Linearity.**

Let’s revise what linearity and non linearity means.

![](https://miro.medium.com/max/875/1*fOcXmFmniOTJVyI5I3bTTg.png)

linear relationship example

The above equation represents a **linear relationship** between Y and X1,X2. Regardless of what values W1 and W2 have, at the end of the day the change of value of X1 and X2 will result in a **linear** change in Y. Now if we look at real world data we realize this is actually not desirable because data often has **non linear** relationships between the input and output variables.

![](https://miro.medium.com/max/740/1*lRfLiNorqmOlb-38Y6wv_A.png)

linear relationship vs non-linear relationship

The above diagram represents a typical dataset which shows a non-linear relationship between X and Y. If we try to fit a linear relationship on the data, we will end up with the **red line,** which is not a very accurate representation of the data. However if our relationship can be **non linear**, we are able to get the green line, which is much better.

Now let’s compare the neural network equation **with and without the activation function.**

![](https://miro.medium.com/max/770/1*MZiEmpCYJyJG4ctl5ypm3w.png)

We can observe that in this equation, there exists a **linear relationship** between the input and the output. However in the case of the equation **with activation function**, we can say that the relationship between input and output can be non linear, IF the activation function is **itself non linear**. Hence all we have to do is keep some non linear function as the activation function for each neuron and our neural network is now **capable** of fitting on non linear data.

Let’s look at a couple of popular activation functions:

![](https://miro.medium.com/max/766/1*fKQ8aWPSDSDoK7MUBgR1XA.png)

**ReLU:** ReLU stands for Rectified Linear Unit. It essentially becomes an identity function (y = x) when x ≥ 0 and becomes 0 when x < 0. This is a very widely used activation function because its a nonlinear function and it is very simple.

**Sigmoid:** Sigmoid is essentially a function bounded between 0 and 1. It will become 0 for values which are very negative and 1 for values which are very positive. Hence this function _squishes_ values which are very high or very low to values between 0 and 1. This is useful in neural networks sometimes to ensure values aren’t extremely high or low. This function is usually used at the last layer when we need values which are binary (0 or 1).
