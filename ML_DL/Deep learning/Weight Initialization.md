## Why initializing weights with zeros is a problem:
1. Symmetry problem: With all zero weights, every neuron in the network computes the same output, so they are essentially redundant copies. This leaves no room for different units to specialize and learn different features.
2. Getting stuck during training: With zeros, the gradients on each weight will be the same during backpropagation. This means the weights will update identically, so no differentiation emerges between units. The network remains homogeneous.
3. Vanishing/exploding gradients: All-zero initialization can make gradients either vanish to zero or explode to very large values during backprop. This prevents effective learning.
4. Lack of output variation: Neural networks with all zero weights produce zero or constant outputs. This provides no useful information for the loss function to improve upon.

## Initializing all the weights to the same non-zero value is still problematic for a few reasons:

1. Symmetry: With identical weights, all the neurons are effectively the same. This prevents differentiation between units, limiting their ability to specialize for distinct features.
2. Signals disappear or explode: Equal weights can lead to inputs either fading out or accumulating uncontrollably as they propagate through the layers. This makes optimization difficult.
3. Slow convergence: Identical gradients from symmetric weights means the optimization algorithm must slowly break symmetry. Learning is much slower compared to proper random initialization.
4. Vanishing/exploding gradients: Depending on the non-zero value chosen, gradients can still vanish or explode, inhibiting training.
5. Stuck in local optima: The symmetric initialization provides a flat energy landscape without clear gradients, making it easy to get trapped in poor local minima.

![[Screenshot 2023-07-17 144516.png]]

## Solutions:

Xavier initialization:

- Scales weights based on number of inputs and outputs to keep variance consistent across layers.
- Formula: W = np.random.randn(fan_in, fan_out) / np.sqrt(fan_in)
- Helps signals propagate through network smoothly.

He initialization:

- Refinement of Xavier approach for ReLU networks.
- Formula: W = np.random.randn(fan_in, fan_out) / np.sqrt(fan_in/2)
- Accounts for ReLU only using half the inputs.

LeCun initialization:

- Original technique proposed in early 1990s.
- Formula: W = np.random.randn(fan_in, fan_out) / np.sqrt(fan_in)
- Very similar to Xavier init. Helps stabilize gradient flow.

Key points:

- All use random Gaussian weights to break symmetry
- Scale inputs or variance to control signal stability
- Enable efficient convergence and avoid vanishing/exploding gradients
- Crucial for training modern deep neural networks

So in summary, properly randomized and controlled initialization schemes are essential for enabling effective optimization.