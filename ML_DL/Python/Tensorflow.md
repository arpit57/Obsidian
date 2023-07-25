## Syntaxes(simple ANN)

**Sequential model with list of layers**: This is probably the most widely used syntax for simple models where each layer has exactly one input tensor and one output tensor, and the layers form a linear stack. It's concise and easy to understand, which makes it a great choice for beginners and for simple use cases.

```python
model = tf.keras.models.Sequential([
  tf.keras.layers.Dense(100, activation='relu'),
  tf.keras.layers.Dense(50, activation='relu'),
  tf.keras.layers.Dense(10, activation='relu'),
  tf.keras.layers.Dense(3, activation='softmax')
])
```



**Sequential model with `add` method**: This approach is often used when the model architecture needs to be defined in a more dynamic or flexible way, such as in a loop or conditional statement. It's just as easy to understand as the list of layers approach, but it offers a bit more flexibility.

```python
model = tf.keras.models.Sequential()
model.add(tf.keras.layers.Dense(100, activation='relu'))
model.add(tf.keras.layers.Dense(50, activation='relu'))
model.add(tf.keras.layers.Dense(10, activation='relu'))
model.add(tf.keras.layers.Dense(3, activation='softmax'))
```

**Functional API**: This approach is used when you need to build models that have multiple inputs, multiple outputs, shared layers, or non-linear topology (e.g., residual connections, multi-branch models). It offers a lot of flexibility, but it can be a bit harder to understand for beginners.

```python
input_layer = tf.keras.Input(shape=(input_dim,))
dense1 = tf.keras.layers.Dense(100, activation='relu')(input_layer)
dense2 = tf.keras.layers.Dense(50, activation='relu')(dense1)
dense3 = tf.keras.layers.Dense(10, activation='relu')(dense2)
output_layer = tf.keras.layers.Dense(3, activation='softmax')(dense3)

model = tf.keras.Model(inputs=input_layer, outputs=output_layer)
```

**Model subclassing**: This is the most flexible approach, and it's often used when you need to define custom layers, custom training loops, or models with complex, dynamic architectures. It gives you full control over the forward pass of the model, but it's also the most complex approach and can be harder to debug.

```python
class MyModel(tf.keras.Model):
    def __init__(self):
        super(MyModel, self).__init__()
        self.dense1 = tf.keras.layers.Dense(100, activation='relu')
        self.dense2 = tf.keras.layers.Dense(50, activation='relu')
        self.dense3 = tf.keras.layers.Dense(10, activation='relu')
        self.dense4 = tf.keras.layers.Dense(3, activation='softmax')

    def call(self, inputs):
        x = self.dense1(inputs)
        x = self.dense2(x)
        x = self.dense3(x)
        return self.dense4(x)

model = MyModel()
```

## Compile and Fit

**compile method:**

Before training a model, you need to configure the learning process, which is done via the `compile` method. It receives three arguments:

- **An optimizer**: This could be the string identifier of an existing optimizer (such as `rmsprop` or `adagrad`), or an instance of the `Optimizer` class. Examples: `Adam`, `SGD`, etc.
    
- **A loss function**: This is the objective that the model will try to minimize. It can be the string identifier of an existing loss function (such as `categorical_crossentropy` or `mse`), or it can be a custom objective function.
    
- **A list of metrics**: For any classification problem, you will want to set this to `metrics=['accuracy']`. A metric could be the string identifier of an existing metric or a custom metric function.
    

Here's an example of how to compile a model:

```python
`model.compile(optimizer='adam', loss='categorical_crossentropy',               metrics=['accuracy'])`
```

**fit method:**

Keras models are trained on Numpy arrays of input data and labels using the `fit` method. It trains the model for a fixed number of epochs (iterations on a dataset).

The `fit` method has two required arguments:

- **input data (features)**: training data that the model will learn from.
    
- **labels (targets)**: labels associated with the training data.
    

There are also several optional arguments. Two commonly used ones are:

- **epochs**: an integer, the number of times the model will cycle through the entire training dataset.
    
- **batch_size**: number of samples per gradient update. If unspecified, it will default to 32.
    

Here's an example of how to fit a model:

```python
`history = model.fit(X_train, y_train, epochs=10, batch_size=32)`
```

The `fit` method returns a `History` object. Its `History.history` attribute is a record of training loss values and metrics values at successive epochs, as well as validation loss values and validation metrics values (if applicable).

In summary, `compile` sets up the learning process, and `fit` actually trains the model. After these two steps, the model will have learned to associate the input data with the corresponding labels, and it can be used to make predictions on new data.

## Is it valid to not mention input layer

In Keras, you do not need to explicitly define an input layer when creating a Sequential model. The model automatically infers the input shape based on the input data it receives when you first train or use the model.

However, it's often a good idea to explicitly state the input shape, especially if you plan to use the model's architecture separately from its weights. It also helps to avoid any potential errors when you add layers to the model or try to use it with input data that has a different shape than expected.

You can do this by adding an `Input` layer at the beginning of your model or by specifying the `input_shape` or `input_dim` argument in the first layer of your model. Here's how you could modify your model to explicitly specify an input shape:
```python
model = tf.keras.models.Sequential([
  tf.keras.layers.Input(shape=(input_dim,)),
  tf.keras.layers.Dense(100, activation='relu'),
  tf.keras.layers.Dense(50, activation='relu'),
  tf.keras.layers.Dense(10, activation='relu'),
  tf.keras.layers.Dense(3, activation='softmax')
])
```

where `input_dim` is the number of features in your input data.

Or with `input_dim` directly in the `Dense` layer:

```python
model = tf.keras.models.Sequential([
  tf.keras.layers.Dense(100, activation='relu', input_dim=input_dim),
  tf.keras.layers.Dense(50, activation='relu'),
  tf.keras.layers.Dense(10, activation='relu'),
  tf.keras.layers.Dense(3, activation='softmax')
])
```
In this case, `input_dim` would be replaced with the number of input features in your dataset.

## Keras and TF

Think of TensorFlow as the engine of a car. It's a powerful, efficient machine that can handle a lot of heavy lifting. It's flexible and can be tweaked and tuned in many ways. However, to use it, you need to understand how an engine works, and handling it directly can be complicated and require a lot of technical knowledge.

Now, think of Keras as the car's dashboard and steering wheel. It's the user-friendly interface that you, the driver, interact with. It's designed to be simple and intuitive, hiding the complex machinery under the hood. You don't need to know exactly how the engine works to drive the car - you just need to know how to use the steering wheel, pedals, and other controls.

In this analogy, TensorFlow provides the underlying engine for computation, while Keras provides the user-friendly interface for building and training machine learning models. Keras is actually a part of TensorFlow as of TensorFlow version 2.0 - it's the official high-level API for TensorFlow. That means you can use the simplicity and ease of use of Keras, while also having access to the power and flexibility of TensorFlow if you need it.

In other words, Keras is the easy-to-use "wrapper" around the powerful but more complex TensorFlow. Keras simplifies the process of building and training models, while TensorFlow provides the underlying tools and capabilities for advanced machine learning tasks.