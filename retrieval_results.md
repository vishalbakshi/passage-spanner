This file contains the definition of expected results for a sample of retrieved passages using answerai-colbert-small-v1.


## Chapter 1 Question 20

Answer components and related contexts:

```
"answer_component": "The validation set is the portion of the dataset that is not used for training the model, but for evaluating the model during training"

"context": [
  "To avoid this, our first step was to split our dataset into two sets: the *training set* (which our model sees in   training) and the *validation set*, also known as the *development set* (which is used only for evaluation). This lets us test that the model learns lessons from the training data that generalize to new data, the validation data."
]
```
```
"answer_component": [
  "This ensures that the model performance is not due to \u201ccheating\u201d or memorization of the dataset, but rather because it learns the appropriate features to use for prediction",
  "overfitting"
 ]

"context": [
  "One way to understand this situation is that, in a sense, we don't want our model to get good results by \"cheating.\" If it makes an accurate prediction for a data item, that should be because it has learned characteristics of that kind of item, and not because the model has been shaped by *actually having seen that particular item*.",

  "Even when your model has not fully memorized all your data, earlier on in training it may have memorized certain parts of it. As a result, the longer you train for, the better your accuracy will get on the training set; the validation set accuracy will also improve for a while, but eventually it will start getting worse as the model starts to memorize the training set, rather than finding generalizable underlying patterns in the data. When this happens, we say that the model is *overfitting*."
]
```

```
"answer_component": "However, it is possible that we overfit the validation data as well."

"context": [
  "The problem is that even though the ordinary training process is only looking at predictions on the training data when it learns values for the weight parameters, the same is not true of us. We, as modelers, are evaluating the model by looking at predictions on the validation data when we decide to explore new hyperparameter values! So subsequent versions of the model are, indirectly, shaped by us having seen the validation data. Just as the automatic training process is in danger of overfitting the training data, we are in danger of overfitting the validation data through human trial and error and exploration."
]
```
```
"answer_component": "This is because the human modeler is also part of the training process, adjusting hyperparameters (see question 32 for definition) and training procedures according to the validation performance."

"context": [
  "In fact, not necessarily. The situation is more subtle. This is because in realistic scenarios we rarely build a model just by training its weight parameters once. Instead, we are likely to explore many versions of a model through various modeling choices regarding network architecture, learning rates, data augmentation strategies, and other factors we will discuss in upcoming chapters. Many of these choices can be described as choices of *hyperparameters*. The word reflects that they are parameters about parameters, since they are the higher-level choices that govern the meaning of the weight parameters."
]
```
```
"answer_component": "Therefore, another unseen portion of the dataset, the test set, is used for final evaluation of the model."

"context": [
  "The solution to this conundrum is to introduce another level of even more highly reserved data, the *test set*. Just as we hold back the validation data from the training process, we must hold back the test set data even from ourselves. It cannot be used to improve the model; it can only be used to evaluate the model at the very end of our efforts. In effect, we define a hierarchy of cuts of our data, based on how fully we want to hide it from training and modeling processes: training data is fully exposed, the validation data is less exposed, and test data is totally hidden. This hierarchy parallels the different kinds of modeling and evaluation processes themselves\u2014the automatic training process with back propagation, the more manual process of trying different hyper-parameters between training sessions, and the assessment of our final result."
]
```
```
"answer_component": "This splitting of the dataset is necessary to ensure that the model generalizes to unseen data."
"context": [
  "Having two levels of \"reserved data\"\u2014a validation set and a test set, with one level representing data that you are virtually hiding from yourself\u2014may seem a bit extreme. But the reason it is often necessary is because models tend to gravitate toward the simplest way to do good predictions (memorization), and we as fallible humans tend to gravitate toward fooling ourselves about how well our models are performing. The discipline of the test set helps us keep ourselves intellectually honest. That doesn't mean we *always* need a separate test set\u2014if you have very little data, you may need to just have a validation set\u2014but generally it's best to use one if at all possible."
]
```
