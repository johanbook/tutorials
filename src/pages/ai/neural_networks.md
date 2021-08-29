# Artificial neural networks

What if we can model the algorithms to behave in the same pattern as the human
brain? From that very question, the concept of artificial neural networks was
born. Sadly, it was also where the resemblance between the two ended.

A neural network consist of a network of nodes, like the brain, where every
connection can have different strengths, also like the brain. In mathematical
terms, this can for a single node be expressed as
$$y =
\phi\left(\sum_i x_i\right)$$.

## Convolutional neural networks

When it comes to analyzing images, networks known as Convolutional Neural
Networks (CNN) is the best. A convolutional layer consisting of a kernel with
learnable weights. This allows the network to learn local features without
needing an absurd amount of complexity.

One architecture is VGG, named after Visual Geometry Group, that stacks very
many convolutional layers on top of each other.

## Under- and overfitting

The complexity of the architecture one chooses must match the problem, otherwise
one will run into something called under- and overfitting. Underfitting is when
the model is not complex enough to solve the problem and is indicating of poor
performance (e.g. low classification accuracy). On the contrary, overfitting is
when a model is too complex and is capable of learning each data point in the
training data rather than learning to generalize. Overtraining is recognized by
satisfying training metrics but poor validation metrics. There are various tools
to counter overtraining, such as data augmentation.

As mentioned earlier, one of greatest problems of the training process is
overtraining. One approach to mitigate this, is to randomly pick a set of nodes
that are inactive during the training period. New nodes are picked after each
update and during inferring all nodes are active. This approach, known as
dropout, has shown to significantly decrease overtraining. On a side-note, it
was recently patented by Google.

Dropout can also be used during inference to create ensemble machines. The mean
of the predictions is a good estimate for the true prediction and the variance
is a measure of uncertainty. However, fine-tuning the used drop-out rate during
inference becomes rather challenging and directly affects the given measure of
uncertainty.

## Data processing and augmentation

To achieve top-notch performance it is of utter importance that one treats the
data properly.

### BatchNorm

### Data augmentation

## Optimizers

The most common ones are SGD and Adam.

## Learning rate schedulers

The learning rate is likely the one hyperparameter that is the most difficult to
set. By performing a range test one can establish a range of suitable learning
rates. From this one can construct a learning rate scheduler, such as CLR
(Cyclic Learning Rate) or a plateau scheduler.

Warm starting is when one start training a model that is already pre-trained.
This might shorten otherwise long training times. The network does not even need
to be pre-trained on the same type of domain of data.
