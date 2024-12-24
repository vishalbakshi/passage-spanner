This file contains the definition of expected results for a sample of retrieved passages using answerai-colbert-small-v1. The passages are identified by their rank (starting at 1) in the top-10 retrieved passages for that question. Note that the "document" in each case is the chapter notebook converted into a string. 

## Table of Contents

- [Chapter 1 Question 20](#chapter-1-question-20)
- [Chapter 2 Question 22](#chapter-2-question-22)
- [Chapter 4 Question 20](#chapter-4-question-20)
- [Chapter 10 Question 6](#chapter-10-question-6)
- [Chapter 13 Question 17](#chapter-13-question-17)


`max_dist` = 2000.

## Chapter 1 Question 20 
([top](#table-of-contents))

|Passage Rank|Start|End|
|:-:|:-:|:-:|
|10|61090|63395|
|4|97959|100302|
|3|100094|102557|
|1|102340|104684|

|Start Passage|End Passage|Distance|
|:-:|:-:|:-:|
|10|4|34564|
|10|3|36699|
|10|1|38945|
|4|3|-208|
|4|1|2038|
|3|1|-217|

**Answer component**

"The validation set is the portion of the dataset that is not used for training the model, but for evaluating the model during training"

**Contexts**

"To avoid this, our first step was to split our dataset into two sets: the *training set* (which our model sees in   training) and the *validation set*, also known as the *development set* (which is used only for evaluation). This lets us test that the model learns lessons from the training data that generalize to new data, the validation data."

**Relevant passage(s)** (Emphasis mine)

`[Passage 4]` "(We\u2019ll even take you step by step through the process of creating your own image dataset soon.)\n\nfast.ai has spent a lot of time creating cut-down versions of popular datasets that are specially designed to support rapid prototyping and experimentation, and to be easier to learn with. In this book we will often start by using one of the cut-down versions and later scale up to the full-size version (just as we're doing in this chapter!). In fact, this is how the world\u2019s top practitioners do their modeling in practice; they do most of their experimentation and prototyping with subsets of their data, and only use the full dataset when they have a good understanding of what they have to do.\n### End sidebar\nEach of the models we trained showed a training and validation loss. A good validation set is one of the most important pieces of the training process. Let's see why and learn how to create one.\n## Validation Sets and Test Sets\nAs we've discussed, the goal of a model is to make predictions about data. But the model training process is fundamentally dumb. If we trained a model with all our data, and then evaluated the model using that same data, we would not be able to tell how well our model can perform on data it hasn\u2019t seen. Without this very valuable piece of information to guide us in training our model, there is a very good chance it would become good at making predictions about that data but would perform poorly on new data.\n\n<mark>To avoid this, our first step was to split our dataset into two sets: the *training set* (which our model sees in training) and the *validation set*, also known as the *development set* (which is used only for evaluation). This lets us test that the model learns lessons from the training data that generalize to new data, the validation data.</mark>\n\nOne way to understand this situation is that, in a sense, we don't want our model to get good results by \"cheating.\" If it makes an accurate prediction for a data item, that should be because it has learned characteristics of that kind of item, and not because the model has been shaped by *actually having seen that particular item*.\n\nSplitting off our validation data means our model never sees it in training and so is completely untainted by it, and is not cheating in any way. Right?\n\nIn fact, not necessarily. The situation is more subtle."
            
---

**Answer component**

"This ensures that the model performance is not due to \u201ccheating\u201d or memorization of the dataset, but rather because it learns the appropriate features to use for prediction"
  
"overfitting"

**Contexts**

"One way to understand this situation is that, in a sense, we don't want our model to get good results by \"cheating.\" If it makes an accurate prediction for a data item, that should be because it has learned characteristics of that kind of item, and not because the model has been shaped by *actually having seen that particular item*."

"Even when your model has not fully memorized all your data, earlier on in training it may have memorized certain parts of it. As a result, the longer you train for, the better your accuracy will get on the training set; the validation set accuracy will also improve for a while, but eventually it will start getting worse as the model starts to memorize the training set, rather than finding generalizable underlying patterns in the data. When this happens, we say that the model is *overfitting*."

**Relevant passage(s)** (Emphasis mine)

`[Passage 4]`"(We\u2019ll even take you step by step through the process of creating your own image dataset soon.)\n\nfast.ai has spent a lot of time creating cut-down versions of popular datasets that are specially designed to support rapid prototyping and experimentation, and to be easier to learn with. In this book we will often start by using one of the cut-down versions and later scale up to the full-size version (just as we're doing in this chapter!). In fact, this is how the world\u2019s top practitioners do their modeling in practice; they do most of their experimentation and prototyping with subsets of their data, and only use the full dataset when they have a good understanding of what they have to do.\n### End sidebar\nEach of the models we trained showed a training and validation loss. A good validation set is one of the most important pieces of the training process. Let's see why and learn how to create one.\n## Validation Sets and Test Sets\nAs we've discussed, the goal of a model is to make predictions about data. But the model training process is fundamentally dumb. If we trained a model with all our data, and then evaluated the model using that same data, we would not be able to tell how well our model can perform on data it hasn\u2019t seen. Without this very valuable piece of information to guide us in training our model, there is a very good chance it would become good at making predictions about that data but would perform poorly on new data.\n\nTo avoid this, our first step was to split our dataset into two sets: the *training set* (which our model sees in training) and the *validation set*, also known as the *development set* (which is used only for evaluation). This lets us test that the model learns lessons from the training data that generalize to new data, the validation data.\n\n<mark>One way to understand this situation is that, in a sense, we don't want our model to get good results by \"cheating.\" If it makes an accurate prediction for a data item, that should be because it has learned characteristics of that kind of item, and not because the model has been shaped by *actually having seen that particular item*.</mark>\n\nSplitting off our validation data means our model never sees it in training and so is completely untainted by it, and is not cheating in any way. Right?\n\nIn fact, not necessarily. The situation is more subtle."

`[Passage 10]`"That is always our goal when creating a model: for it to be useful on data that the model only sees in the future, after it has been trained.\n\n<mark>Even when your model has not fully memorized all your data, earlier on in training it may have memorized certain parts of it. As a result, the longer you train for, the better your accuracy will get on the training set; the validation set accuracy will also improve for a while, but eventually it will start getting worse as the model starts to memorize the training set, rather than finding generalizable underlying patterns in the data. When this happens, we say that the model is *overfitting*.</mark>\n\n<<img_overfit>> shows what happens when you overfit, using a simplified example where we have just one parameter, and some randomly generated data based on the function `x**2`. As you can see, although the predictions in the overfit model are accurate for data near the observed data points, they are way off when outside of that range.\n<img src=\"images/att_00000.png\" alt=\"Example of overfitting\" caption=\"Example of overfitting\" id=\"img_overfit\" width=\"700\">\n**Overfitting is the single most important and challenging issue** when training for all machine learning practitioners, and all algorithms. As you will see, it is very easy to create a model that does a great job at making predictions on the exact data it has been trained on, but it is much harder to make accurate predictions on data the model has never seen before. And of course, this is the data that will actually matter in practice. For instance, if you create a handwritten digit classifier (as we will very soon!) and use it to recognize numbers written on checks, then you are never going to see any of the numbers that the model was trained on\u2014checks will have slightly different variations of writing to deal with. You will learn many methods to avoid overfitting in this book. However, you should only use those methods after you have confirmed that overfitting is actually occurring (i.e., you have actually observed the validation accuracy getting worse during training). We often see practitioners using over-fitting avoidance techniques even when they have enough data that they didn't need to do so, ending up with a model that may be less accurate than what they could have achieved."
        

---

**Answer component**

"However, it is possible that we overfit the validation data as well."

**Contexts**

"The problem is that even though the ordinary training process is only looking at predictions on the training data when it learns values for the weight parameters, the same is not true of us. We, as modelers, are evaluating the model by looking at predictions on the validation data when we decide to explore new hyperparameter values! So subsequent versions of the model are, indirectly, shaped by us having seen the validation data. Just as the automatic training process is in danger of overfitting the training data, we are in danger of overfitting the validation data through human trial and error and exploration."

**Relevant passage(s)**

`[Passage 3]`"Splitting off our validation data means our model never sees it in training and so is completely untainted by it, and is not cheating in any way. Right?\n\nIn fact, not necessarily. The situation is more subtle. This is because in realistic scenarios we rarely build a model just by training its weight parameters once. Instead, we are likely to explore many versions of a model through various modeling choices regarding network architecture, learning rates, data augmentation strategies, and other factors we will discuss in upcoming chapters. Many of these choices can be described as choices of *hyperparameters*. The word reflects that they are parameters about parameters, since they are the higher-level choices that govern the meaning of the weight parameters.\n<mark>The problem is that even though the ordinary training process is only looking at predictions on the training data when it learns values for the weight parameters, the same is not true of us. We, as modelers, are evaluating the model by looking at predictions on the validation data when we decide to explore new hyperparameter values! So subsequent versions of the model are, indirectly, shaped by us having seen the validation data. Just as the automatic training process is in danger of overfitting the training data, we are in danger of overfitting the validation data through human trial and error and exploration.</mark>\n\nThe solution to this conundrum is to introduce another level of even more highly reserved data, the *test set*. Just as we hold back the validation data from the training process, we must hold back the test set data even from ourselves. It cannot be used to improve the model; it can only be used to evaluate the model at the very end of our efforts. In effect, we define a hierarchy of cuts of our data, based on how fully we want to hide it from training and modeling processes: training data is fully exposed, the validation data is less exposed, and test data is totally hidden. This hierarchy parallels the different kinds of modeling and evaluation processes themselves\u2014the automatic training process with back propagation, the more manual process of trying different hyper-parameters between training sessions, and the assessment of our final result.\n\nThe test and validation sets should have enough data to ensure that you get a good estimate of your accuracy. If you're creating a cat detector, for instance, you generally want at least 30 cats in your validation set."
            

---

**Answer component**

"This is because the human modeler is also part of the training process, adjusting hyperparameters (see question 32 for definition) and training procedures according to the validation performance."

**Contexts**

"In fact, not necessarily. The situation is more subtle. This is because in realistic scenarios we rarely build a model just by training its weight parameters once. Instead, we are likely to explore many versions of a model through various modeling choices regarding network architecture, learning rates, data augmentation strategies, and other factors we will discuss in upcoming chapters. Many of these choices can be described as choices of *hyperparameters*. The word reflects that they are parameters about parameters, since they are the higher-level choices that govern the meaning of the weight parameters."

**Relevant passage(s)**

`[Passage 3]`"Splitting off our validation data means our model never sees it in training and so is completely untainted by it, and is not cheating in any way. Right?\n\n<mark>In fact, not necessarily. The situation is more subtle. This is because in realistic scenarios we rarely build a model just by training its weight parameters once. Instead, we are likely to explore many versions of a model through various modeling choices regarding network architecture, learning rates, data augmentation strategies, and other factors we will discuss in upcoming chapters. Many of these choices can be described as choices of *hyperparameters*. The word reflects that they are parameters about parameters, since they are the higher-level choices that govern the meaning of the weight parameters.</mark>\nThe problem is that even though the ordinary training process is only looking at predictions on the training data when it learns values for the weight parameters, the same is not true of us. We, as modelers, are evaluating the model by looking at predictions on the validation data when we decide to explore new hyperparameter values! So subsequent versions of the model are, indirectly, shaped by us having seen the validation data. Just as the automatic training process is in danger of overfitting the training data, we are in danger of overfitting the validation data through human trial and error and exploration.\n\nThe solution to this conundrum is to introduce another level of even more highly reserved data, the *test set*. Just as we hold back the validation data from the training process, we must hold back the test set data even from ourselves. It cannot be used to improve the model; it can only be used to evaluate the model at the very end of our efforts. In effect, we define a hierarchy of cuts of our data, based on how fully we want to hide it from training and modeling processes: training data is fully exposed, the validation data is less exposed, and test data is totally hidden. This hierarchy parallels the different kinds of modeling and evaluation processes themselves\u2014the automatic training process with back propagation, the more manual process of trying different hyper-parameters between training sessions, and the assessment of our final result.\n\nThe test and validation sets should have enough data to ensure that you get a good estimate of your accuracy. If you're creating a cat detector, for instance, you generally want at least 30 cats in your validation set."

---

**Answer component**
"Therefore, another unseen portion of the dataset, the test set, is used for final evaluation of the model."

**Contexts**
"The solution to this conundrum is to introduce another level of even more highly reserved data, the *test set*. Just as we hold back the validation data from the training process, we must hold back the test set data even from ourselves. It cannot be used to improve the model; it can only be used to evaluate the model at the very end of our efforts. In effect, we define a hierarchy of cuts of our data, based on how fully we want to hide it from training and modeling processes: training data is fully exposed, the validation data is less exposed, and test data is totally hidden. This hierarchy parallels the different kinds of modeling and evaluation processes themselves\u2014the automatic training process with back propagation, the more manual process of trying different hyper-parameters between training sessions, and the assessment of our final result."

**Relevant passage(s)**

`[Passage 3]`"Splitting off our validation data means our model never sees it in training and so is completely untainted by it, and is not cheating in any way. Right?\n\nIn fact, not necessarily. The situation is more subtle. This is because in realistic scenarios we rarely build a model just by training its weight parameters once. Instead, we are likely to explore many versions of a model through various modeling choices regarding network architecture, learning rates, data augmentation strategies, and other factors we will discuss in upcoming chapters. Many of these choices can be described as choices of *hyperparameters*. The word reflects that they are parameters about parameters, since they are the higher-level choices that govern the meaning of the weight parameters.\nThe problem is that even though the ordinary training process is only looking at predictions on the training data when it learns values for the weight parameters, the same is not true of us. We, as modelers, are evaluating the model by looking at predictions on the validation data when we decide to explore new hyperparameter values! So subsequent versions of the model are, indirectly, shaped by us having seen the validation data. Just as the automatic training process is in danger of overfitting the training data, we are in danger of overfitting the validation data through human trial and error and exploration.\n\n<mark>The solution to this conundrum is to introduce another level of even more highly reserved data, the *test set*. Just as we hold back the validation data from the training process, we must hold back the test set data even from ourselves. It cannot be used to improve the model; it can only be used to evaluate the model at the very end of our efforts. In effect, we define a hierarchy of cuts of our data, based on how fully we want to hide it from training and modeling processes: training data is fully exposed, the validation data is less exposed, and test data is totally hidden. This hierarchy parallels the different kinds of modeling and evaluation processes themselves\u2014the automatic training process with back propagation, the more manual process of trying different hyper-parameters between training sessions, and the assessment of our final result.</mark>\n\nThe test and validation sets should have enough data to ensure that you get a good estimate of your accuracy. If you're creating a cat detector, for instance, you generally want at least 30 cats in your validation set."

---

**Answer component**
"This splitting of the dataset is necessary to ensure that the model generalizes to unseen data."

**Contexts**
"Having two levels of \"reserved data\"\u2014a validation set and a test set, with one level representing data that you are virtually hiding from yourself\u2014may seem a bit extreme. But the reason it is often necessary is because models tend to gravitate toward the simplest way to do good predictions (memorization), and we as fallible humans tend to gravitate toward fooling ourselves about how well our models are performing. The discipline of the test set helps us keep ourselves intellectually honest. That doesn't mean we *always* need a separate test set\u2014if you have very little data, you may need to just have a validation set\u2014but generally it's best to use one if at all possible."

**Relevant passage(s)**

`[Passage 1]`"The test and validation sets should have enough data to ensure that you get a good estimate of your accuracy. If you're creating a cat detector, for instance, you generally want at least 30 cats in your validation set. That means that if you have a dataset with thousands of items, using the default 20% validation set size may be more than you need. On the other hand, if you have lots of data, using some of it for validation probably doesn't have any downsides.\n\n<mark>Having two levels of \"reserved data\"\u2014a validation set and a test set, with one level representing data that you are virtually hiding from yourself\u2014may seem a bit extreme. But the reason it is often necessary is because models tend to gravitate toward the simplest way to do good predictions (memorization), and we as fallible humans tend to gravitate toward fooling ourselves about how well our models are performing. The discipline of the test set helps us keep ourselves intellectually honest. That doesn't mean we *always* need a separate test set\u2014if you have very little data, you may need to just have a validation set\u2014but generally it's best to use one if at all possible.</mark>\n\nThis same discipline can be critical if you intend to hire a third party to perform modeling work on your behalf. A third party might not understand your requirements accurately, or their incentives might even encourage them to misunderstand them. A good test set can greatly mitigate these risks and let you evaluate whether their work solves your actual problem.\n\nTo put it bluntly, if you're a senior decision maker in your organization (or you're advising senior decision makers), the most important takeaway is this: if you ensure that you really understand what test and validation sets are and why they're important, then you'll avoid the single biggest source of failures we've seen when organizations decide to use AI. For instance, if you're considering bringing in an external vendor or service, make sure that you hold out some test data that the vendor *never gets to see*. Then *you* check their model on your test data, using a metric that *you* choose based on what actually matters to you in practice, and *you* decide what level of performance is adequate. (It's also a good idea for you to try out some simple baseline yourself, so you know what a really simple model can achieve."

## Chapter 2 Question 22 
([top](#table-of-contents))

|Passage Rank|Start|End|
|:-:|:-:|:-:|
|2|54412|56386|
|1|56136|58222|
|3|62239|64539|

|Start Passage|End Passage|Distance|
|:-:|:-:|:-:|
|2|1|-250|
|2|3|5853|
|1|3|4017|

**Answer component**: 

"GPUs are best for doing identical work in parallel"

**Contexts**

"As we've seen, GPUs are only useful when they do lots of identical work in parallel"

**Relevant passage(s)**

`[Passage 2]`"So what's left is a web application! To view your notebook as a Voil\u00e0 web application, replace the word \"notebooks\" in your browser's URL with: \"voila/render\". You will see the same content as your notebook, but without any of the code cells.\n\nOf course, you don't need to use Voil\u00e0 or ipywidgets. Your model is just a function you can call (`pred,pred_idx,probs = learn.predict(img)`), so you can use it with any framework, hosted on any platform. And you can take something you've prototyped in ipywidgets and Voil\u00e0 and later convert it into a regular web application. We're showing you this approach in the book because we think it's a great way for data scientists and other folks that aren't web development experts to create applications from their models.\n\nWe have our app, now let's deploy it!\n### Deploying your app\nAs you now know, you need a GPU to train nearly any useful deep learning model. So, do you need a GPU to use that model in production? No! You almost certainly *do not need a GPU to serve your model in production*. There are a few reasons for this:\n\n- <mark>As we've seen, GPUs are only useful when they do lots of identical work in parallel</mark>. If you're doing (say) image classification, then you'll normally be classifying just one user's image at a time, and there isn't normally enough work to do in a single image to keep a GPU busy for long enough for it to be very efficient. So, a CPU will often be more cost-effective.\n- An alternative could be to wait for a few users to submit their images, and then batch them up and process them all at once on a GPU. But then you're asking your users to wait, rather than getting answers straight away! And you need a high-volume site for this to be workable. If you do need this functionality, you can use a tool such as Microsoft's [ONNX Runtime](https://github.com/microsoft/onnxruntime), or [AWS Sagemaker](https://aws.amazon.com/sagemaker/)\n- The complexities of dealing with GPU inference are significant."

---

**Answer component**: 

"If you will be analyzing single pieces of data at a time (like a single image or single sentence), then CPUs may be more cost effective instead"

**Contexts**

"If you're doing (say) image classification, then you'll normally be classifying just one user's image at a time, and there isn't normally enough work to do in a single image to keep a GPU busy for long enough for it to be very efficient. So, a CPU will often be more cost-effective."

**Relevant passage(s)**

`[Passage 2]`"So what's left is a web application! To view your notebook as a Voil\u00e0 web application, replace the word \"notebooks\" in your browser's URL with: \"voila/render\". You will see the same content as your notebook, but without any of the code cells.\n\nOf course, you don't need to use Voil\u00e0 or ipywidgets. Your model is just a function you can call (`pred,pred_idx,probs = learn.predict(img)`), so you can use it with any framework, hosted on any platform. And you can take something you've prototyped in ipywidgets and Voil\u00e0 and later convert it into a regular web application. We're showing you this approach in the book because we think it's a great way for data scientists and other folks that aren't web development experts to create applications from their models.\n\nWe have our app, now let's deploy it!\n### Deploying your app\nAs you now know, you need a GPU to train nearly any useful deep learning model. So, do you need a GPU to use that model in production? No! You almost certainly *do not need a GPU to serve your model in production*. There are a few reasons for this:\n\n- As we've seen, GPUs are only useful when they do lots of identical work in parallel. <mark>If you're doing (say) image classification, then you'll normally be classifying just one user's image at a time, and there isn't normally enough work to do in a single image to keep a GPU busy for long enough for it to be very efficient. So, a CPU will often be more cost-effective.</mark>\n- An alternative could be to wait for a few users to submit their images, and then batch them up and process them all at once on a GPU. But then you're asking your users to wait, rather than getting answers straight away! And you need a high-volume site for this to be workable. If you do need this functionality, you can use a tool such as Microsoft's [ONNX Runtime](https://github.com/microsoft/onnxruntime), or [AWS Sagemaker](https://aws.amazon.com/sagemaker/)\n- The complexities of dealing with GPU inference are significant."

---

**Answer component**: 

"especially with more market competition for CPU servers versus GPU servers" 

**Contexts**

"There's a lot more market competition in CPU than GPU servers, as a result of which there are much cheaper options available for CPU servers"

**Relevant passage(s)**

`[Passage 1]`"If you do need this functionality, you can use a tool such as Microsoft's [ONNX Runtime](https://github.com/microsoft/onnxruntime), or [AWS Sagemaker](https://aws.amazon.com/sagemaker/)\n- The complexities of dealing with GPU inference are significant. In particular, the GPU's memory will need careful manual management, and you'll need a careful queueing system to ensure you only process one batch at a time.\n- <mark>There's a lot more market competition in CPU than GPU servers, as a result of which there are much cheaper options available for CPU servers</mark>.\n\nBecause of the complexity of GPU serving, many systems have sprung up to try to automate this. However, managing and running these systems is also complex, and generally requires compiling your model into a different form that's specialized for that system. It's typically preferable to avoid dealing with this complexity until/unless your app gets popular enough that it makes clear financial sense for you to do so.\nFor at least the initial prototype of your application, and for any hobby projects that you want to show off, you can easily host them for free. The best place and the best way to do this will vary over time, so check the [book's website](https://book.fast.ai/) for the most up-to-date recommendations. As we're writing this book in early 2020 the simplest (and free!) approach is to use [Binder](https://mybinder.org/). To publish your web app on Binder, you follow these steps:\n\n1. Add your notebook to a [GitHub repository](http://github.com/).\n2. Paste the URL of that repo into Binder's URL, as shown in <<deploy-binder>>.\n3. Change the File dropdown to instead select URL.\n4. In the \"URL to open\" field, enter `/voila/render/name.ipynb` (replacing `name` with the name of for your notebook).\n5. Click the clickboard button at the bottom right to copy the URL and paste it somewhere safe. \n6. Click Launch.\n<img alt=\"Deploying to Binder\" width=\"800\" caption=\"Deploying to Binder\" id=\"deploy-binder\" src=\"images/att_00001.png\">\nThe first time you do this, Binder will take around 5 minutes to build your site."


---

**Answer component**: 

"GPUs could be used if you collect user responses into a batch at a time, and perform inference on the batch. This may require the user to wait for model predictions"

**Contexts**

"An alternative could be to wait for a few users to submit their images, and then batch them up and process them all at once on a GPU. But then you're asking your users to wait, rather than getting answers straight away"

**Relevant passage(s)**

`[Passage 2]`"So what's left is a web application! To view your notebook as a Voil\u00e0 web application, replace the word \"notebooks\" in your browser's URL with: \"voila/render\". You will see the same content as your notebook, but without any of the code cells.\n\nOf course, you don't need to use Voil\u00e0 or ipywidgets. Your model is just a function you can call (`pred,pred_idx,probs = learn.predict(img)`), so you can use it with any framework, hosted on any platform. And you can take something you've prototyped in ipywidgets and Voil\u00e0 and later convert it into a regular web application. We're showing you this approach in the book because we think it's a great way for data scientists and other folks that aren't web development experts to create applications from their models.\n\nWe have our app, now let's deploy it!\n### Deploying your app\nAs you now know, you need a GPU to train nearly any useful deep learning model. So, do you need a GPU to use that model in production? No! You almost certainly *do not need a GPU to serve your model in production*. There are a few reasons for this:\n\n- As we've seen, GPUs are only useful when they do lots of identical work in parallel. If you're doing (say) image classification, then you'll normally be classifying just one user's image at a time, and there isn't normally enough work to do in a single image to keep a GPU busy for long enough for it to be very efficient. So, a CPU will often be more cost-effective.\n- <mark>An alternative could be to wait for a few users to submit their images, and then batch them up and process them all at once on a GPU. But then you're asking your users to wait, rather than getting answers straight away</mark>! And you need a high-volume site for this to be workable. If you do need this functionality, you can use a tool such as Microsoft's [ONNX Runtime](https://github.com/microsoft/onnxruntime), or [AWS Sagemaker](https://aws.amazon.com/sagemaker/)\n- The complexities of dealing with GPU inference are significant."

---

**Answer component**: 

"Additionally, there are many other complexities when it comes to GPU inference"

**Contexts**

"The complexities of dealing with GPU inference are significant"

"Because of the complexity of GPU serving, many systems have sprung up to try to automate this. However, managing and running these systems is also complex, and generally requires compiling your model into a different form that's specialized for that system. It's typically preferable to avoid dealing with this complexity until/unless your app gets popular enough that it makes clear financial sense for you to do so."

"Overall, we'd recommend using a simple CPU-based server approach where possible, for as long as you can get away with it. If you're lucky enough to have a very successful application, then you'll be able to justify the investment in more complex deployment approaches at that time"

**Relevant passage(s)**

`[Passage 1]`"If you do need this functionality, you can use a tool such as Microsoft's [ONNX Runtime](https://github.com/microsoft/onnxruntime), or [AWS Sagemaker](https://aws.amazon.com/sagemaker/)\n- <mark>The complexities of dealing with GPU inference are significant</mark>. In particular, the GPU's memory will need careful manual management, and you'll need a careful queueing system to ensure you only process one batch at a time.\n- There's a lot more market competition in CPU than GPU servers, as a result of which there are much cheaper options available for CPU servers.\n\n<mark>Because of the complexity of GPU serving, many systems have sprung up to try to automate this. However, managing and running these systems is also complex, and generally requires compiling your model into a different form that's specialized for that system. It's typically preferable to avoid dealing with this complexity until/unless your app gets popular enough that it makes clear financial sense for you to do so</mark>.\nFor at least the initial prototype of your application, and for any hobby projects that you want to show off, you can easily host them for free. The best place and the best way to do this will vary over time, so check the [book's website](https://book.fast.ai/) for the most up-to-date recommendations. As we're writing this book in early 2020 the simplest (and free!) approach is to use [Binder](https://mybinder.org/). To publish your web app on Binder, you follow these steps:\n\n1. Add your notebook to a [GitHub repository](http://github.com/).\n2. Paste the URL of that repo into Binder's URL, as shown in <<deploy-binder>>.\n3. Change the File dropdown to instead select URL.\n4. In the \"URL to open\" field, enter `/voila/render/name.ipynb` (replacing `name` with the name of for your notebook).\n5. Click the clickboard button at the bottom right to copy the URL and paste it somewhere safe. \n6. Click Launch.\n<img alt=\"Deploying to Binder\" width=\"800\" caption=\"Deploying to Binder\" id=\"deploy-binder\" src=\"images/att_00001.png\">\nThe first time you do this, Binder will take around 5 minutes to build your site."

`[Passage 2]`"So what's left is a web application! To view your notebook as a Voil\u00e0 web application, replace the word \"notebooks\" in your browser's URL with: \"voila/render\". You will see the same content as your notebook, but without any of the code cells.\n\nOf course, you don't need to use Voil\u00e0 or ipywidgets. Your model is just a function you can call (`pred,pred_idx,probs = learn.predict(img)`), so you can use it with any framework, hosted on any platform. And you can take something you've prototyped in ipywidgets and Voil\u00e0 and later convert it into a regular web application. We're showing you this approach in the book because we think it's a great way for data scientists and other folks that aren't web development experts to create applications from their models.\n\nWe have our app, now let's deploy it!\n### Deploying your app\nAs you now know, you need a GPU to train nearly any useful deep learning model. So, do you need a GPU to use that model in production? No! You almost certainly *do not need a GPU to serve your model in production*. There are a few reasons for this:\n\n- As we've seen, GPUs are only useful when they do lots of identical work in parallel. If you're doing (say) image classification, then you'll normally be classifying just one user's image at a time, and there isn't normally enough work to do in a single image to keep a GPU busy for long enough for it to be very efficient. So, a CPU will often be more cost-effective.\n- An alternative could be to wait for a few users to submit their images, and then batch them up and process them all at once on a GPU. But then you're asking your users to wait, rather than getting answers straight away! And you need a high-volume site for this to be workable. If you do need this functionality, you can use a tool such as Microsoft's [ONNX Runtime](https://github.com/microsoft/onnxruntime), or [AWS Sagemaker](https://aws.amazon.com/sagemaker/)\n- <mark>The complexities of dealing with GPU inference are significant</mark>."

`[Passage 3]`"It's still not easy but in our case it's worth it, for a faster user experience and to worry less about servers. What works for you will depend, realistically, on the user experience you're trying to create and what you personally find is easy to do. If you really know how to run servers, do it. If you really know how to build native mobile apps, do that. There are many roads up the hill.\n\n<mark>Overall, we'd recommend using a simple CPU-based server approach where possible, for as long as you can get away with it. If you're lucky enough to have a very successful application, then you'll be able to justify the investment in more complex deployment approaches at that time</mark>.\n\nCongratulations, you have successfully built a deep learning model and deployed it! Now is a good time to take a pause and think about what could go wrong.\n## How to Avoid Disaster\nIn practice, a deep learning model will be just one piece of a much bigger system. As we discussed at the start of this chapter, a data product requires thinking about the entire end-to-end process, from conception to use in production. In this book, we can't hope to cover all the complexity of managing deployed data products, such as managing multiple versions of models, A/B testing, canarying, refreshing the data (should we just grow and grow our datasets all the time, or should we regularly remove some of the old data?), handling data labeling, monitoring all this, detecting model rot, and so forth. In this section we will give an overview of some of the most important issues to consider; for a more detailed discussion of deployment issues we refer to you to the excellent [Building Machine Learning Powered Applications](http://shop.oreilly.com/product/0636920215912.do) by Emmanuel Ameisen (O'Reilly)\n\nOne of the biggest issues to consider is that understanding and testing the behavior of a deep learning model is much more difficult than with most other code you write. With normal software development you can analyze the exact steps that the software is taking, and carefully study which of these steps match the desired behavior that you are trying to create. But with a neural network the behavior emerges from the model's attempt to match the training data, rather than being exactly defined.\n\nThis can result in disaster!"

---

**Answer component**: 

"memory management and queuing of the batches"

**Contexts**

"In particular, the GPU's memory will need careful manual management, and you'll need a careful queueing system to ensure you only process one batch at a time"

**Relevant passage(s)**

`[Passage 1]`"If you do need this functionality, you can use a tool such as Microsoft's [ONNX Runtime](https://github.com/microsoft/onnxruntime), or [AWS Sagemaker](https://aws.amazon.com/sagemaker/)\n- The complexities of dealing with GPU inference are significant. <mark>In particular, the GPU's memory will need careful manual management, and you'll need a careful queueing system to ensure you only process one batch at a time</mark>.\n- There's a lot more market competition in CPU than GPU servers, as a result of which there are much cheaper options available for CPU servers.\n\nBecause of the complexity of GPU serving, many systems have sprung up to try to automate this. However, managing and running these systems is also complex, and generally requires compiling your model into a different form that's specialized for that system. It's typically preferable to avoid dealing with this complexity until/unless your app gets popular enough that it makes clear financial sense for you to do so.\nFor at least the initial prototype of your application, and for any hobby projects that you want to show off, you can easily host them for free. The best place and the best way to do this will vary over time, so check the [book's website](https://book.fast.ai/) for the most up-to-date recommendations. As we're writing this book in early 2020 the simplest (and free!) approach is to use [Binder](https://mybinder.org/). To publish your web app on Binder, you follow these steps:\n\n1. Add your notebook to a [GitHub repository](http://github.com/).\n2. Paste the URL of that repo into Binder's URL, as shown in <<deploy-binder>>.\n3. Change the File dropdown to instead select URL.\n4. In the \"URL to open\" field, enter `/voila/render/name.ipynb` (replacing `name` with the name of for your notebook).\n5. Click the clickboard button at the bottom right to copy the URL and paste it somewhere safe. \n6. Click Launch.\n<img alt=\"Deploying to Binder\" width=\"800\" caption=\"Deploying to Binder\" id=\"deploy-binder\" src=\"images/att_00001.png\">\nThe first time you do this, Binder will take around 5 minutes to build your site."

## Chapter 4 Question 20
([top](#table-of-contents))

|Passage Rank|Start|End|
|:-:|:-:|:-:|
|1|62499|64378|
|9|64219|66008|

|Start Passage|End Passage|Distance|
|:-:|:-:|:-:|
|1|9|-159|

**Answer component**: 

"A loss function needs to change as the weights are being adjusted"

**Contexts**

"we need a loss function which, when our weights result in slightly better predictions, gives us a slightly better loss"

**Relevant passage(s)**

`[Passage 1]`"The problem is that a small change in weights from `x_old` to `x_new` isn't likely to cause any prediction to change, so `(y_new - y_old)` will almost always be 0. In other words, the gradient is 0 almost everywhere.\nA very small change in the value of a weight will often not actually change the accuracy at all. This means it is not useful to use accuracy as a loss function\u2014if we do, most of the time our gradients will actually be 0, and the model will not be able to learn from that number.\n\n> S: In mathematical terms, accuracy is a function that is constant almost everywhere (except at the threshold, 0.5), so its derivative is nil almost everywhere (and infinity at the threshold). This then gives gradients that are 0 or infinite, which are useless for updating the model.\n\nInstead, <mark>we need a loss function which, when our weights result in slightly better predictions, gives us a slightly better loss</mark>. So what does a \"slightly better prediction\" look like, exactly? Well, in this case, it means that if the correct answer is a 3 the score is a little higher, or if the correct answer is a 7 the score is a little lower.\n\nLet's write such a function now. What form does it take?\n\nThe loss function receives not the images themselves, but the predictions from the model. Let's make one argument, `prds`, of values between 0 and 1, where each value is the prediction that an image is a 3. It is a vector (i.e., a rank-1 tensor), indexed over the images.\n\nThe purpose of the loss function is to measure the difference between predicted values and the true values \u2014 that is, the targets (aka labels). Let's make another argument, `trgts`, with values of 0 or 1 which tells whether an image actually is a 3 or not. It is also a vector (i.e., another rank-1 tensor), indexed over the images.\n\nSo, for instance, suppose we had three images which we knew were a 3, a 7, and a 3."
            
---

**Answer component**: 

"Accuracy only changes if the predictions of the model change. So if there are slight changes to the model that, say, improves confidence in a prediction, but does not change the prediction, the accuracy will still not change. Therefore, the gradients will be zero everywhere except when the actual predictions change"

**Contexts**

"But accuracy only changes at all when a prediction changes from a 3 to a 7, or vice versa. The problem is that a small change in weights from `x_old` to `x_new` isn't likely to cause any prediction to change, so `(y_new - y_old)` will almost always be 0. In other words, the gradient is 0 almost everywhere"

"A very small change in the value of a weight will often not actually change the accuracy at all. This means it is not useful to use accuracy as a loss function—if we do, most of the time our gradients will actually be 0"

**Relevant passage(s)**

`[Passage 1]`"The problem is that a small change in weights from `x_old` to `x_new` isn't likely to cause any prediction to change, so `(y_new - y_old)` will almost always be 0. In other words, the gradient is 0 almost everywhere.\n<mark>A very small change in the value of a weight will often not actually change the accuracy at all. This means it is not useful to use accuracy as a loss function\u2014if we do, most of the time our gradients will actually be 0</mark>, and the model will not be able to learn from that number.\n\n> S: In mathematical terms, accuracy is a function that is constant almost everywhere (except at the threshold, 0.5), so its derivative is nil almost everywhere (and infinity at the threshold). This then gives gradients that are 0 or infinite, which are useless for updating the model.\n\nInstead, we need a loss function which, when our weights result in slightly better predictions, gives us a slightly better loss. So what does a \"slightly better prediction\" look like, exactly? Well, in this case, it means that if the correct answer is a 3 the score is a little higher, or if the correct answer is a 7 the score is a little lower.\n\nLet's write such a function now. What form does it take?\n\nThe loss function receives not the images themselves, but the predictions from the model. Let's make one argument, `prds`, of values between 0 and 1, where each value is the prediction that an image is a 3. It is a vector (i.e., a rank-1 tensor), indexed over the images.\n\nThe purpose of the loss function is to measure the difference between predicted values and the true values \u2014 that is, the targets (aka labels). Let's make another argument, `trgts`, with values of 0 or 1 which tells whether an image actually is a 3 or not. It is also a vector (i.e., another rank-1 tensor), indexed over the images.\n\nSo, for instance, suppose we had three images which we knew were a 3, a 7, and a 3."
            
---

**Answer component**: 

"The model therefore cannot learn from the gradients equal to zero, and the model's weights will not update and will not train"

**Contexts**

"this means it is not useful to use accuracy as a loss function—if we do, most of the time our gradients will actually be 0, and the model will not be able to learn from that number"

"In mathematical terms, accuracy is a function that is constant almost everywhere (except at the threshold, 0.5), so its derivative is nil almost everywhere (and infinity at the threshold). This then gives gradients that are 0 or infinite, which are useless for updating the model."

**Relevant passage(s)**

`[Passage 1]`"The problem is that a small change in weights from `x_old` to `x_new` isn't likely to cause any prediction to change, so `(y_new - y_old)` will almost always be 0. In other words, the gradient is 0 almost everywhere.\nA very small change in the value of a weight will often not actually change the accuracy at all. This means it is not useful to use accuracy as a loss function\u2014if we do, most of the time our gradients will actually be 0, and the model will not be able to learn from that number.\n\n> S: <mark>In mathematical terms, accuracy is a function that is constant almost everywhere (except at the threshold, 0.5), so its derivative is nil almost everywhere (and infinity at the threshold). This then gives gradients that are 0 or infinite, which are useless for updating the model</mark>.\n\nInstead, we need a loss function which, when our weights result in slightly better predictions, gives us a slightly better loss. So what does a \"slightly better prediction\" look like, exactly? Well, in this case, it means that if the correct answer is a 3 the score is a little higher, or if the correct answer is a 7 the score is a little lower.\n\nLet's write such a function now. What form does it take?\n\nThe loss function receives not the images themselves, but the predictions from the model. Let's make one argument, `prds`, of values between 0 and 1, where each value is the prediction that an image is a 3. It is a vector (i.e., a rank-1 tensor), indexed over the images.\n\nThe purpose of the loss function is to measure the difference between predicted values and the true values \u2014 that is, the targets (aka labels). Let's make another argument, `trgts`, with values of 0 or 1 which tells whether an image actually is a 3 or not. It is also a vector (i.e., another rank-1 tensor), indexed over the images.\n\nSo, for instance, suppose we had three images which we knew were a 3, a 7, and a 3."

---

**Answer component**: 

"A good loss function gives a slightly better loss when the model gives slightly better predictions"

**Contexts**

"Instead, we need a loss function which, when our weights result in slightly better predictions, gives us a slightly better loss"

**Relevant passage(s)**

`[Passage 1]`"The problem is that a small change in weights from `x_old` to `x_new` isn't likely to cause any prediction to change, so `(y_new - y_old)` will almost always be 0. In other words, the gradient is 0 almost everywhere.\nA very small change in the value of a weight will often not actually change the accuracy at all. This means it is not useful to use accuracy as a loss function\u2014if we do, most of the time our gradients will actually be 0, and the model will not be able to learn from that number.\n\n> S: In mathematical terms, accuracy is a function that is constant almost everywhere (except at the threshold, 0.5), so its derivative is nil almost everywhere (and infinity at the threshold). This then gives gradients that are 0 or infinite, which are useless for updating the model.\n\n<mark>Instead, we need a loss function which, when our weights result in slightly better predictions, gives us a slightly better loss</mark>. So what does a \"slightly better prediction\" look like, exactly? Well, in this case, it means that if the correct answer is a 3 the score is a little higher, or if the correct answer is a 7 the score is a little lower.\n\nLet's write such a function now. What form does it take?\n\nThe loss function receives not the images themselves, but the predictions from the model. Let's make one argument, `prds`, of values between 0 and 1, where each value is the prediction that an image is a 3. It is a vector (i.e., a rank-1 tensor), indexed over the images.\n\nThe purpose of the loss function is to measure the difference between predicted values and the true values \u2014 that is, the targets (aka labels). Let's make another argument, `trgts`, with values of 0 or 1 which tells whether an image actually is a 3 or not. It is also a vector (i.e., another rank-1 tensor), indexed over the images.\n\nSo, for instance, suppose we had three images which we knew were a 3, a 7, and a 3."

---

**Answer component**: 

"Slightly better predictions mean if the model is more confident about the correct prediction"

**Contexts**

"You can see that this function returns a lower number when predictions are more accurate, when accurate predictions are more confident (higher absolute values), and when inaccurate predictions are less confident"

**Relevant passage(s)**

`[Passage 9]`"It is also a vector (i.e., another rank-1 tensor), indexed over the images.\n\nSo, for instance, suppose we had three images which we knew were a 3, a 7, and a 3. And suppose our model predicted with high confidence (`0.9`) that the first was a 3, with slight confidence (`0.4`) that the second was a 7, and with fair confidence (`0.2`), but incorrectly, that the last was a 7. This would mean our loss function would receive these values as its inputs:\ntrgts  = tensor([1,0,1])\nprds   = tensor([0.9, 0.4, 0.2])\nHere's a first try at a loss function that measures the distance between `predictions` and `targets`:\ndef mnist_loss(predictions, targets):\n    return torch.where(targets==1, 1-predictions, predictions).mean()\nWe're using a new function, `torch.where(a,b,c)`. This is the same as running the list comprehension `[b[i] if a[i] else c[i] for i in range(len(a))]`, except it works on tensors, at C/CUDA speed. In plain English, this function will measure how distant each prediction is from 1 if it should be 1, and how distant it is from 0 if it should be 0, and then it will take the mean of all those distances.\n\n> note: Read the Docs: It's important to learn about PyTorch functions like this, because looping over tensors in Python performs at Python speed, not C/CUDA speed! Try running `help(torch.where)` now to read the docs for this function, or, better still, look it up on the PyTorch documentation site.\nLet's try it on our `prds` and `trgts`:\ntorch.where(trgts==1, 1-prds, prds)\n<mark>You can see that this function returns a lower number when predictions are more accurate, when accurate predictions are more confident (higher absolute values), and when inaccurate predictions are less confident</mark>. In PyTorch, we always assume that a lower value of a loss function is better."

## Chapter 10 Question 6
([top](#table-of-contents))

|Passage Rank|Start|End|
|:-:|:-:|:-:|
|9|1888|4199|
|1|24952|27045|
|6|32454|34241|

|Start Passage|End Passage|Distance|
|:-:|:-:|:-:|
|9|1|20753|
|9|6|28255|
|1|6|5409|

**Answer component**: 

"Train a language model on a large corpus of text (already done for ULM-FiT by Sebastian Ruder and Jeremy!)"

**Contexts**

"The language model we used in <<chapter_intro>> to classify IMDb reviews was pretrained on Wikipedia."

**Relevant passage(s)**

None.

---

**Answer component**: 

"Fine-tune the language model on text classification dataset"

**Contexts**

"first we need to fine-tune our language model pretrained on Wikipedia to the corpus of IMDb reviews"

"The Wikipedia English is slightly different from the IMDb English, so instead of jumping directly to the classifier, we could fine-tune our pretrained language model to the IMDb corpus"

**Relevant passage(s)**

`[Passage 1]`"What is important is that we preserve the order of the tokens (so from 1 to 5,000 for the first mini-stream, then from 5,001 to 10,000...), because we want the model to read continuous rows of text (as in the preceding example). An `xxbos` token is added at the start of each during preprocessing, so that the model knows when it reads the stream when a new entry is beginning.\n\nSo to recap, at every epoch we shuffle our collection of documents and concatenate them into a stream of tokens. We then cut that stream into a batch of fixed-size consecutive mini-streams. Our model will then read the mini-streams in order, and thanks to an inner state, it will produce the same activation whatever sequence length we picked.\n\nThis is all done behind the scenes by the fastai library when we create an `LMDataLoader`. We do this by first applying our `Numericalize` object to the tokenized texts:\nnums200 = toks200.map(num)\nand then passing that to `LMDataLoader`:\ndl = LMDataLoader(nums200)\nLet's confirm that this gives the expected results, by grabbing the first batch:\nx,y = first(dl)\nx.shape,y.shape\nand then looking at the first row of the independent variable, which should be the start of the first text:\n' '.join(num.vocab[o] for o in x[0][:20])\nThe dependent variable is the same thing offset by one token:\n' '.join(num.vocab[o] for o in y[0][:20])\nThis concludes all the preprocessing steps we need to apply to our data. We are now ready to train our text classifier.\n## Training a Text Classifier\nAs we saw at the beginning of this chapter, there are two steps to training a state-of-the-art text classifier using transfer learning: <mark>first we need to fine-tune our language model pretrained on Wikipedia to the corpus of IMDb reviews</mark>, and then we can use that model to train a classifier.\n\nAs usual, let's start with assembling our data.\n### Language Model Using DataBlock\nfastai handles tokenization and numericalization automatically when `TextBlock` is passed to `DataBlock`. All of the arguments that can be passed to `Tokenize` and `Numericalize` can also be passed to `TextBlock`."

`[Passage 9]`"<mark>The Wikipedia English is slightly different from the IMDb English, so instead of jumping directly to the classifier, we could fine-tune our pretrained language model to the IMDb corpus</mark> and then use *that* as the base for our classifier.\n\nEven if our language model knows the basics of the language we are using in the task (e.g., our pretrained model is in English), it helps to get used to the style of the corpus we are targeting. It may be more informal language, or more technical, with new words to learn or different ways of composing sentences. In the case of the IMDb dataset, there will be lots of names of movie directors and actors, and often a less formal style of language than that seen in Wikipedia.\n\nWe already saw that with fastai, we can download a pretrained English language model and use it to get state-of-the-art results for NLP classification. (We expect pretrained models in many more languages to be available soon\u2014they might well be available by the time you are reading this book, in fact.) So, why are we learning how to train a language model in detail?\n\nOne reason, of course, is that it is helpful to understand the foundations of the models that you are using. But there is another very practical reason, which is that you get even better results if you fine-tune the (sequence-based) language model prior to fine-tuning the classification model. For instance, for the IMDb sentiment analysis task, the dataset includes 50,000 additional movie reviews that do not have any positive or negative labels attached. Since there are 25,000 labeled reviews in the training set and 25,000 in the validation set, that makes 100,000 movie reviews altogether. We can use all of these reviews to fine-tune the pretrained language model, which was trained only on Wikipedia articles; this will result in a language model that is particularly good at predicting the next word of a movie review.\n\nThis is known as the Universal Language Model Fine-tuning (ULMFit) approach. The [paper](https://arxiv.org/abs/1801.06146) showed that this extra stage of fine-tuning of the language model, prior to transfer learning to a classification task, resulted in significantly better predictions. Using this approach, we have three stages for transfer learning in NLP, as summarized in <<ulmfit_process>>."

---

**Answer component**: 

"Fine-tune the language model as a text classifier instead"

**Contexts**

"and then we can use that model to train a classifier"

"then use *that* as the base for our classifier"

"We're now moving from language model fine-tuning to classifier fine-tuning. To recap, a language model predicts the next word of a document, so it doesn't need any external labels. A classifier, however, predicts some external label—in the case of IMDb, it's the sentiment of a document"

**Relevant passage(s)**

`[Passage 1]`"What is important is that we preserve the order of the tokens (so from 1 to 5,000 for the first mini-stream, then from 5,001 to 10,000...), because we want the model to read continuous rows of text (as in the preceding example). An `xxbos` token is added at the start of each during preprocessing, so that the model knows when it reads the stream when a new entry is beginning.\n\nSo to recap, at every epoch we shuffle our collection of documents and concatenate them into a stream of tokens. We then cut that stream into a batch of fixed-size consecutive mini-streams. Our model will then read the mini-streams in order, and thanks to an inner state, it will produce the same activation whatever sequence length we picked.\n\nThis is all done behind the scenes by the fastai library when we create an `LMDataLoader`. We do this by first applying our `Numericalize` object to the tokenized texts:\nnums200 = toks200.map(num)\nand then passing that to `LMDataLoader`:\ndl = LMDataLoader(nums200)\nLet's confirm that this gives the expected results, by grabbing the first batch:\nx,y = first(dl)\nx.shape,y.shape\nand then looking at the first row of the independent variable, which should be the start of the first text:\n' '.join(num.vocab[o] for o in x[0][:20])\nThe dependent variable is the same thing offset by one token:\n' '.join(num.vocab[o] for o in y[0][:20])\nThis concludes all the preprocessing steps we need to apply to our data. We are now ready to train our text classifier.\n## Training a Text Classifier\nAs we saw at the beginning of this chapter, there are two steps to training a state-of-the-art text classifier using transfer learning: first we need to fine-tune our language model pretrained on Wikipedia to the corpus of IMDb reviews, <mark>and then we can use that model to train a classifier</mark>.\n\nAs usual, let's start with assembling our data.\n### Language Model Using DataBlock\nfastai handles tokenization and numericalization automatically when `TextBlock` is passed to `DataBlock`. All of the arguments that can be passed to `Tokenize` and `Numericalize` can also be passed to `TextBlock`."

`[Passage 6]`"We can now use it to fine-tune a classifier using the IMDb sentiment labels.\n### Text Generation\nBefore we move on to fine-tuning the classifier, let's quickly try something different: using our model to generate random reviews. Since it's trained to guess what the next word of the sentence is, we can use the model to write new reviews:\nTEXT = \"I liked this movie because\"\nN_WORDS = 40\nN_SENTENCES = 2\npreds = [learn.predict(TEXT, N_WORDS, temperature=0.75) \n         for _ in range(N_SENTENCES)]\nprint(\"\\n\".join(preds))\nAs you can see, we add some randomness (we pick a random word based on the probabilities returned by the model) so we don't get exactly the same review twice. Our model doesn't have any programmed knowledge of the structure of a sentence or grammar rules, yet it has clearly learned a lot about English sentences: we can see it capitalizes properly (*I* is just transformed to *i* because our rules require two characters or more to consider a word as capitalized, so it's normal to see it lowercased) and is using consistent tense. The general review makes sense at first glance, and it's only if you read carefully that you can notice something is a bit off. Not bad for a model trained in a couple of hours! \n\nBut our end goal wasn't to train a model to generate reviews, but to classify them... so let's use this model to do just that.\n### Creating the Classifier DataLoaders\n<mark>We're now moving from language model fine-tuning to classifier fine-tuning. To recap, a language model predicts the next word of a document, so it doesn't need any external labels. A classifier, however, predicts some external label\u2014in the case of IMDb, it's the sentiment of a document</mark>.\n\nThis means that the structure of our `DataBlock` for NLP classification will look very familiar."

`[Passage 9]`"The Wikipedia English is slightly different from the IMDb English, so instead of jumping directly to the classifier, we could fine-tune our pretrained language model to the IMDb corpus and <mark>then use *that* as the base for our classifier</mark>.\n\nEven if our language model knows the basics of the language we are using in the task (e.g., our pretrained model is in English), it helps to get used to the style of the corpus we are targeting. It may be more informal language, or more technical, with new words to learn or different ways of composing sentences. In the case of the IMDb dataset, there will be lots of names of movie directors and actors, and often a less formal style of language than that seen in Wikipedia.\n\nWe already saw that with fastai, we can download a pretrained English language model and use it to get state-of-the-art results for NLP classification. (We expect pretrained models in many more languages to be available soon\u2014they might well be available by the time you are reading this book, in fact.) So, why are we learning how to train a language model in detail?\n\nOne reason, of course, is that it is helpful to understand the foundations of the models that you are using. But there is another very practical reason, which is that you get even better results if you fine-tune the (sequence-based) language model prior to fine-tuning the classification model. For instance, for the IMDb sentiment analysis task, the dataset includes 50,000 additional movie reviews that do not have any positive or negative labels attached. Since there are 25,000 labeled reviews in the training set and 25,000 in the validation set, that makes 100,000 movie reviews altogether. We can use all of these reviews to fine-tune the pretrained language model, which was trained only on Wikipedia articles; this will result in a language model that is particularly good at predicting the next word of a movie review.\n\nThis is known as the Universal Language Model Fine-tuning (ULMFit) approach. The [paper](https://arxiv.org/abs/1801.06146) showed that this extra stage of fine-tuning of the language model, prior to transfer learning to a classification task, resulted in significantly better predictions. Using this approach, we have three stages for transfer learning in NLP, as summarized in <<ulmfit_process>>."

## Chapter 13 Question 17
([top](#table-of-contents))

|Passage Rank|Start|End|
|:-:|:-:|:-:|
|2|23818|25854|
|1|25685|26910|

|Start Passage|End Passage|Distance|
|:-:|:-:|:-:|
|2|1|-164|

**Answer component**: 

"After two stride 2 convolutions, the receptive field is 7x7"

**Contexts**

"In this example, we have just two convolutional layers, each of stride 2, so this is now tracing right back to the input image. We can see that a 7×7 area of cells in the input layer is used to calculate the single green cell in the Conv2 layer. This 7×7 area is the *receptive field* in the input of the green activation in Conv2. We can also see that a second filter kernel is needed now, since we have two layers."

**Relevant passage(s)**

`[Passage 2]`"If we left the number of channels the same in each stride-2 layer, the amount of computation being done in the net would get less and less as it gets deeper. But we know that the deeper layers have to compute semantically rich features (such as eyes or fur), so we wouldn't expect that doing *less* computation would make sense.\nAnother way to think of this is based on receptive fields.\n### Receptive Fields\nThe *receptive field* is the area of an image that is involved in the calculation of a layer. On the [book's website](https://book.fast.ai/), you'll find an Excel spreadsheet called *conv-example.xlsx* that shows the calculation of two stride-2 convolutional layers using an MNIST digit. Each layer has a single kernel. <<preced1>> shows what we see if we click on one of the cells in the *conv2* section, which shows the output of the second convolutional layer, and click *trace precedents*.\n<img alt=\"Immediate precedents of conv2 layer\" width=\"308\" caption=\"Immediate precedents of Conv2 layer\" id=\"preced1\" src=\"images/att_00068.png\">\nHere, the cell with the green border is the cell we clicked on, and the blue highlighted cells are its *precedents*\u2014that is, the cells used to calculate its value. These cells are the corresponding 3\u00d73 area of cells from the input layer (on the left), and the cells from the filter (on the right). Let's now click *trace precedents* again, to see what cells are used to calculate these inputs. <<preced2>> shows what happens.\n<img alt=\"Secondary precedents of conv2 layer\" width=\"601\" caption=\"Secondary precedents of Conv2 layer\" id=\"preced2\" src=\"images/att_00069.png\">\n<mark>In this example, we have just two convolutional layers, each of stride 2, so this is now tracing right back to the input image. We can see that a 7\u00d77 area of cells in the input layer is used to calculate the single green cell in the Conv2 layer. This 7\u00d77 area is the *receptive field* in the input of the green activation in Conv2. We can also see that a second filter kernel is needed now, since we have two layers.</mark>"

---

**Answer component**: 

"The size of the receptive field increases the deeper we are in the network"

**Contexts**

"As you see from this example, the deeper we are in the network (specifically, the more stride-2 convs we have before a layer), the larger the receptive field for an activation in that layer"

**Relevant passage(s)**

`[Passage 1]`"This 7\u00d77 area is the *receptive field* in the input of the green activation in Conv2. We can also see that a second filter kernel is needed now, since we have two layers.\n\n<mark>As you see from this example, the deeper we are in the network (specifically, the more stride-2 convs we have before a layer), the larger the receptive field for an activation in that layer</mark>. A large receptive field means that a large amount of the input image is used to calculate each activation in that layer is. We now know that in the deeper layers of the network we have semantically rich features, corresponding to larger receptive fields. Therefore, we'd expect that we'd need more weights for each of our features to handle this increasing complexity. This is another way of saying the same thing we mentioned in the previous section: when we introduce a stride-2 conv in our network, we should also increase the number of channels.\nWhen writing this particular chapter, we had a lot of questions we needed answers for, to be able to explain CNNs to you as best we could. Believe it or not, we found most of the answers on Twitter. We're going to take a quick break to talk to you about that now, before we move on to color images.\n### A Note Abo"
