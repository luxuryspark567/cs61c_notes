# Neural Net

At a basic level, a neural networks tries to approximate a (non-linear) function that maps your input into a desired output. A basic neuron consists of a weighted linear combination of the input, followed by a non-linearity -- for example, a threshold. Consider the following neuron, which implements the logical `AND` operation:

[![](https://cs61c.org/fa24/projects/proj2/part-b/neuron.png)](https://cs61c.org/fa24/projects/proj2/part-b/neuron.png)

It is easy to see that for A=0, B=0, the linear combination 0\*0.6 + 0\*0.6 = 0, which is less than the threshold of 1 and will result in a 0 output. With an input A=0, B=1 or A=1, B=0 the linear combination will results in 1\*0.6 + 0\*0.6 = 0.6, which is less than 1 and result in a 0 output. Similarly, A=1, B=1 will result in 1\*0.6+1\*0.6=1.2, which is greater than the threshold and will result in a 1 output! What is interesting is that the simple neuron operation can also be described as an inner product between the vector \[A,B]^T and the weights vector \[0.6,0.6]^T followed by as thresholding, non-linear operation.

More complex functions can not be described by a simple neuron alone. We can extend the system into a network of neurons, in order to approximate the complex functions. For example, the following 2 layer network approximates the logical function `XOR`:

[![](https://cs61c.org/fa24/projects/proj2/part-b/XOR.png)](https://cs61c.org/fa24/projects/proj2/part-b/XOR.png)

The above is a 2 layer network. The network takes 2 inputs, computes 2 intermediate values, and finally computes a single final output.

It can be written as matrix multiplications with matrices `m_0` and `m_1` with thresholding operations in between as shown below:

[![](https://cs61c.org/fa24/projects/proj2/part-b/mtx.png)](https://cs61c.org/fa24/projects/proj2/part-b/mtx.png)

Convince yourself that this implements an `XOR` for the appropriate inputs!

You are probably wondering how the weights of the network were determined? This is beyond the scope of this project, and we would encourage you to take advanced classes in numerical linear algebra, signal processing, machine learning and optimization. We will only say that the weights can be trained by giving the network pairs of correct inputs and outputs and changing the weights such that the error between the outputs of the network and the correct outputs is minimized. Learning the weights is called: "Training". Using the weights on inputs is called "Inference". We will only perform inference, and you will be given weights that were pre-trained by your dedicated TA's.

In this project we will implement a similar, but slightly more complex network which is able to classify handwritten digits. As inputs, we will use the [MNIST](http://yann.lecun.com/exdb/mnist/) data set, which is a dataset of 60,000 28x28 images containing handwritten digits ranging from 0-9. We will treat these images as "flattened" input vectors of size 784 (`= 28 * 28`). In a similar way to the example before, we will perform matrix multiplications with pre-trained weight matrices `m_0` and `m_1`. Instead of thresholding we will use two different non-linearities: The `ReLU` and `ArgMax` functions. Details will be provided in descriptions of the individual tasks.

[![](https://cs61c.org/fa24/projects/proj2/part-b/MNIST.png)](https://cs61c.org/fa24/projects/proj2/part-b/MNIST.png)
