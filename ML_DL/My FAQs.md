
## Does all the nodes of a particular hidden layer have same bias?

Yes, typically all the nodes in a particular hidden layer of an artificial neural network (ANN) share the same bias term.

Specifically:

- Each node in the hidden layer has its own set of weights connecting it to nodes in the previous layer.
- But all the nodes in a single hidden layer share the same bias value.

The bias is added to the weighted sum of inputs going into a node before the activation function is applied.

Sharing the same bias value for all nodes in a layer helps reduce the total number of trainable parameters in the network.

For example, if a hidden layer has 300 nodes, instead of having 300 separate bias terms, there is just 1 bias value shared across all 300 nodes.

So in summary:

- Weights are unique for each node.
- Biases are shared across nodes in the same layer.

Having the same bias for each hidden layer node is standard practice in ANN architectures to limit total parameters and prevent overfitting.

## XOR and XNOR

XOR returns true if exactly one of the inputs is True, False otherwise

Input 1	Input 2	Input 3	Output
True	True	True	False
True	True	False	False
True	False	True	False
False	True	True	False
True	False	False	True
False	True	False	True
False	False	True	True
False	False	False	False



XNOR returns ture if all inputs are same(either all True or all False), False otherwiese

| Input 1 | Input 2 | Input 3 | Output |

| True | True | True | True |
| True | True | False | False |
| True | False | True | False |
| False | True | True | False |
| True | False | False | False |
| False | True | False | False |
| False | False | True | False |
| False | False | False | True |

## Epochs/ batch size/ Iterations

1 epoch is 1 full pass through entire training set
batch size is how many samples out of entire training set are used in 1 iteration before updating weights
number of iterations is entire sample size by batch size
In neural networks, the weights are typically updated after every iteration, not after every epoch.


## Variance/ Standard deviation

Variance is 1/n * sum((x - x_mean)^2)  [1/(n-1) in case of sample data]
standard deviation is the square root of variance.
basically, these are used to define the spread of a distributed data, doesn't necessarily have to be a normal distribution.
suppose that standard deviation is 2.4, this means that approx 68% of the data lies within 2.4 units(1 standard deviation) above and below the mean or 4.8 units around the mean.
95% inside 2 standard deviation around mean and 99.7% around 3 standard deviation around mean.
This is valid for normal distribution, percentage distribution change for other data distributions.
https://tse2.mm.bing.net/th?id=OIP.a4nb3j_Y-VZdJqCzECKNSQHaDt&pid=Api&P=0&h=180

## Eigen Vectors and Eigen Values

Eigenvectors are vectors that do not change direction when a linear transformation is applied to them.

Eigenvalues are scalars that describe the magnification or scaling factor of the eigenvector after the linear transformation.

More specifically:

- If A is a square matrix representing a linear transformation, the eigenvectors of A are vectors v that satisfy:

Av = λv

Where λ is a scalar eigenvalue.

- When you multiply an eigenvector by its matrix A, the eigenvector's direction remains the same. Only its magnitude scales by the eigenvalue.
- Eigenvectors are unit vectors that align with the new coordinate system defined by the linear transformation.
- Eigenvalues indicate how much each eigenvector is scaled by the transformation.

So in summary, the eigenvectors represent transformed basis vectors and the eigenvalues represent their corresponding scaling factors.

