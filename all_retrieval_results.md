This file contains the definition of expected results for a sample of retrieved passages using answerai-colbert-small-v1. The passages are identified by their rank (starting at 1) in the top-10 retrieved passages for that question. Note that the "document" in each case is the chapter notebook converted into a string. All passages are used in this example. 

## Table of Contents

- [Chapter 1 Question 20](#chapter-1-question-20)
- [Chapter 2 Question 22](#chapter-2-question-22)
- [Chapter 4 Question 20](#chapter-4-question-20)
- [Chapter 10 Question 6](#chapter-10-question-6)
- [Chapter 13 Question 17](#chapter-13-question-17)


## Chapter 1 Question 20 
([top](#table-of-contents))


|Passage Rank|Start|End|
|:-:|:-:|:-:|
|10|61090|63395|
|6|63181|65325|
|9|83166|85396|
|8|85102|86662|
|4|97959|100302|
|3|100094|102557|
|1|102340|104684|
|2|104561|106725|
|7|106476|108423|
|5|108299|110645|

I'm listing only those Spans that are at most a distance of `max_dist` (2000 characters) apart, for brevity:

|Start Passage|End Passage|Distance|
|:-:|:-:|:-:|
|10|6|-214|
|9|8|-294|
|4|3|-208|
|3|1|-217|
|1|2|-123|
|1|7|1792|
|2|7|-249|
|2|5|1574|
|7|5|-124|

Keeping the longest span for each starting passage gives us our final 7 spans:

|Start Passage|End Passage|Distance|
|:-:|:-:|:-:|
|10|6|-214|
|9|8|-294|
|4|3|-208|
|3|1|-217|
|1|7|1792|
|2|5|1574|
|7|5|-124|

Looking at the first and last few characters for each span:

|Start Passage|End Passage|Sample Text|
|:-:|:-:|:-:|
|10|6|`'That is always our goal w...et starts getting worse).'`|
|9|8|`'*Machine learning* is a d...is called *segmentation*.'`|
|4|3|`"(We'll even take you step...s in your validation set."`|
|3|1|`'Splitting off our validat...simple model can achieve.'`|
|1|7|`'The test and validation s...pear in the training set.'`|
|2|5|`"(It's also a good idea fo...h order you read them in."`|
|7|5|`'<img src="images/timeseri...h order you read them in.'`|

## Chapter 2 Question 22 
([top](#table-of-contents))

|Passage Rank|Start|End|
|:-:|:-:|:-:|
|9|1895|4355|
|10|14818|17173|
|7|35863|37365|
|8|39457|40921|
|2|54412|56386|
|1|56136|58222|
|4|58005|60287|
|5|60062|62488|
|3|62239|64539|
|6|66421|68761|

Identifying passages at or below 2000 characters apart, keeping the longest span for each starting passage:

|Start Passage|End Passage|Distance|
|:-:|:-:|:-:|
|2|4|1619
|1|5|1840
|4|3|1952
|5|3|-249
|3|6|1882

The first and last few characters for each span:

|Start Passage|End Passage|Sample Text|
|:-:|:-:|:-:|
|2|4|`"So what's left is a web a,,,downsides too, of course."`
|1|5|`'If you do need this funct...nally find is easy to do.'`
|4|3|`'6. Click Launch.\n<img alt...s can result in disaster!'`
|5|3|`'The hardware that you wil...s can result in disaster!'`
|3|6|`"It's still not easy but i...should be very concerned."`

## Chapter 4 Question 20 
([top](#table-of-contents))

|Passage Rank|Start|End|
|:-:|:-:|:-:|
|8|38802|41020
|6|49370|51048
|3|60664|62661
|1|62499|64378
|9|64219|66008
|4|65932|67812
|2|67535|69795
|5|83123|85040
|10|84919|87167
|7|86843|89207

|Start Passage|End Passage|Distance|
|:-:|:-:|:-:|
|3|9|1558
|1|4|1554
|9|2|1527
|4|2|-277
|5|7|1803
|10|7|-324

|Start Passage|End Passage|Sample Text|
|:-:|:-:|:-:|
|3|9|`"Let's check our accuracy....loss function is better."`
|1|4|`'The problem is that a sma...why did we define a loss?'`
|9|2|`'It is also a vector (i.e....ance on that single item.'`
|4|2|`'In PyTorch, we always ass...ance on that single item.'`
|5|7|`'This is known as the *uni...l contained in *tensors*.'`
|10|7|`'A function that can solve...l contained in *tensors*.'`

## Chapter 10 Question 6 
([top](#table-of-contents))

|Passage Rank|Start|End|
|:-:|:-:|:-:|
|9|1888|4199
|7|4092|6258
|5|6061|8341
|8|19172|21234
|1|24952|27045
|10|30794|32681
|6|32454|34241
|4|34038|35778
|3|37587|39404
|2|43353|44284

|Start Passage|End Passage|Distance|
|:-:|:-:|:-:|
|9|5|1862
|7|5|-197
|10|4|1357
|6|4|-203
|4|3|1809

|Start Passage|End Passage|Sample Text|
|:-:|:-:|:-:|
|9|5|`'The Wikipedia English is ...s from many, many pieces?'`
|7|5|`'Using this approach, we h...s from many, many pieces?'`
|10|4|`"Since `fine_tune` doesn't...g the first 10 documents."`
|6|4|`'We can now use it to fine...g the first 10 documents.'`
|4|3|`'A classifier, however, pr...nce just three years ago.'`
