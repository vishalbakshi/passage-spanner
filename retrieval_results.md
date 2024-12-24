This file contains the definition of expected results for a sample of retrieved passages using answerai-colbert-small-v1. The passages are identified by their rank (starting at 1) in the top-10 retrieved passages for that question. Note that the "document" in each case is the chapter notebook converted into a string. 


## Chapter 1 Question 20

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

`[Passage 1]`"The problem is that a small change in weights from `x_old` to `x_new` isn't likely to cause any prediction to change, so `(y_new - y_old)` will almost always be 0. In other words, the gradient is 0 almost everywhere.\nA very small change in the value of a weight will often not actually change the accuracy at all. This means it is not useful to use accuracy as a loss function\u2014if we do, most of the time our gradients will actually be 0, and the model will not be able to learn from that number.\n\n> S: In mathematical terms, accuracy is a function that is constant almost everywhere (except at the threshold, 0.5), so its derivative is nil almost everywhere (and infinity at the threshold). This then gives gradients that are 0 or infinite, which are useless for updating the model.\n\nInstead, we need a loss function which, when our weights result in slightly better predictions, gives us a slightly better loss. So what does a \"slightly better prediction\" look like, exactly? Well, in this case, it means that if the correct answer is a 3 the score is a little higher, or if the correct answer is a 7 the score is a little lower.\n\nLet's write such a function now. What form does it take?\n\nThe loss function receives not the images themselves, but the predictions from the model. Let's make one argument, `prds`, of values between 0 and 1, where each value is the prediction that an image is a 3. It is a vector (i.e., a rank-1 tensor), indexed over the images.\n\nThe purpose of the loss function is to measure the difference between predicted values and the true values \u2014 that is, the targets (aka labels). Let's make another argument, `trgts`, with values of 0 or 1 which tells whether an image actually is a 3 or not. It is also a vector (i.e., another rank-1 tensor), indexed over the images.\n\nSo, for instance, suppose we had three images which we knew were a 3, a 7, and a 3."

---

**Answer component**: 

"Slightly better predictions mean if the model is more confident about the correct prediction"

**Contexts**

"You can see that this function returns a lower number when predictions are more accurate, when accurate predictions are more confident (higher absolute values), and when inaccurate predictions are less confident"

**Relevant passage(s)**

`[Passage 9]`"It is also a vector (i.e., another rank-1 tensor), indexed over the images.\n\nSo, for instance, suppose we had three images which we knew were a 3, a 7, and a 3. And suppose our model predicted with high confidence (`0.9`) that the first was a 3, with slight confidence (`0.4`) that the second was a 7, and with fair confidence (`0.2`), but incorrectly, that the last was a 7. This would mean our loss function would receive these values as its inputs:\ntrgts  = tensor([1,0,1])\nprds   = tensor([0.9, 0.4, 0.2])\nHere's a first try at a loss function that measures the distance between `predictions` and `targets`:\ndef mnist_loss(predictions, targets):\n    return torch.where(targets==1, 1-predictions, predictions).mean()\nWe're using a new function, `torch.where(a,b,c)`. This is the same as running the list comprehension `[b[i] if a[i] else c[i] for i in range(len(a))]`, except it works on tensors, at C/CUDA speed. In plain English, this function will measure how distant each prediction is from 1 if it should be 1, and how distant it is from 0 if it should be 0, and then it will take the mean of all those distances.\n\n> note: Read the Docs: It's important to learn about PyTorch functions like this, because looping over tensors in Python performs at Python speed, not C/CUDA speed! Try running `help(torch.where)` now to read the docs for this function, or, better still, look it up on the PyTorch documentation site.\nLet's try it on our `prds` and `trgts`:\ntorch.where(trgts==1, 1-prds, prds)\nYou can see that this function returns a lower number when predictions are more accurate, when accurate predictions are more confident (higher absolute values), and when inaccurate predictions are less confident. In PyTorch, we always assume that a lower value of a loss function is better."
