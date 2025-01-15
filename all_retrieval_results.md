This file contains the definition of expected results for a sample of retrieved passages using answerai-colbert-small-v1. The passages are identified by their rank (starting at 1) in the top-10 retrieved passages for that question. Note that the "document" in each case is the chapter notebook converted into a string. All passages are used in this example. 

## Table of Contents

- [Chapter 1 Question 20](#chapter-1-question-20)
- [Chapter 2 Question 22](#chapter-2-question-22)
- [Chapter 4 Question 20](#chapter-4-question-20)
- [Chapter 10 Question 6](#chapter-10-question-6)
- [Chapter 13 Question 17](#chapter-13-question-17)


## Chapter 1 Question 20 
([top](#table-of-contents))


|Passage Rank|start_pos|end_pos|
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

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|10|6|61090|65325
|9|8|83166|86662
|4|3|97959|102557
|3|1|100094|104684
|1|2|102340|106725
|1|7|102340|108423
|2|7|104561|108423
|2|5|104561|110645
|7|5|106476|110645

grouping by ending passage end position and keeping the span with the smallest start.start_pos:

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|10|6|61090|65325
|9|8|83166|86662
|4|3|97959|102557
|3|1|100094|104684
|1|2|102340|106725
|1|7|102340|108423
|7|5|106476|110645

grouping by start.start_pos and keeping the span with the largest end.end_pos:

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|10|6|61090|65325
|9|8|83166|86662
|4|3|97959|102557
|3|1|100094|104684
|1|7|102340|108423
|2|5|104561|110645


Sorting by rank (all passages are included in spans):

|Start Passage|End Passage|Sample Text|
|:-:|:-:|:-:|
|3|1|`'Splitting off our validat...simple model can achieve.'`|
|1|7|`'The test and validation s...pear in the training set.'`|
|2|5|`"(It's also a good idea fo...h order you read them in."`|
|4|3|`"(We'll even take you step...s in your validation set."`|
|10|6|`'That is always our goal w...et starts getting worse).'`|
|9|8|`'*Machine learning* is a d...is called *segmentation*.'`|

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

Valid spans, grouping by start.start_pos and keeping the span with the largest end.end_pos, then grouping by end.end_pos and keeping the span with the smallest start.start_pos:

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|2|4|56386|60287
|1|5|56136|62488
|4|3|58005|64539
|3|6|62239|68761

Sorting by rank, and including passages not contained in any of the four spans:

|Start Passage|End Passage|Ranks contained|Sample Text|
|:-:|:-:|:-:|:-:|
|1|5|1,4,5|`'If you do need this funct...nally find is easy to do.'`
|2|4|1,2,4|`"So what's left is a web a,,,downsides too, of course."`
|4|3|3,4,5|`'6. Click Launch.\n<img alt...s can result in disaster!'`
|3|6|3,6|`"It's still not easy but i...should be very concerned."`
|7|7|7|`"fastai includes many pred...es they end up as unreali"`
|8|8|8|`"This is a specific exampl...rain our bear classifier."`
|9|9|9|`"Both of these can be prob...ence to the final result."`
|10|10|10|`"Deep learning does greatl...f the items in that set)."`

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

Final spans:

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|3|9|60664|66008
|1|4|62499|67812
|9|2|64219|69795
|5|7|83123|89207

Final texts:

|Start Passage|End Passage|Ranks contained|Sample Text|
|:-:|:-:|:-:|:-:|
|3|9|1,3,9|`"Let's check our accuracy....loss function is better."`
|1|4|1,4,9|`'The problem is that a sma...why did we define a loss?'`
|9|2|2,4,9|`'It is also a vector (i.e....ance on that single item.'`
|5|7|5,7,10|`'This is known as the *uni...l contained in *tensors*.'`
|6|6|6|`"We want to distinguish cl...hrough our 7 step process."`
|8|8|8|`"This is where that decisi...s will change its result."`


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

Final spans:

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|9|5|1862
|10|4|1357
|4|3|1809

Final texts:

|Start Passage|End Passage|Ranks contained|Sample Text|
|:-:|:-:|:-:|:-:|
|1|1|1|`"What is important is that...be passed to `TextBlock`."`
|2|2|2|`"Many people assume or hop...r your specific problems."`
|4|3|3,4|`'A classifier, however, pr...nce just three years ago.'`
|10|4|4,6,10|`"Since `fine_tune` doesn't...g the first 10 documents."`
|9|5|5,7,9|`'The Wikipedia English is ...s from many, many pieces?'`
|8|8|8|`"That means we'll need our...he previous one left off."`

## Chapter 13 Question 17
([top](#table-of-contents))

|Passage Rank|Start|End|
|:-:|:-:|:-:|
|9|11835|13854
|5|13697|15391
|3|18723|20684
|8|20516|22328
|4|22104|23974
|2|23818|25854
|1|25685|26910
|6|34168|36104
|10|35809|37721
|7|49708|52032

Final spans:

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|9|5|11835|15391
|3|4|18723|23974
|8|2|20516|25854
|4|1|22104|26910
|6|10|34168|37721

Final texts:

|Start Passage|End Passage|Ranks contained|Sample Text|
|:-:|:-:|:-:|:-:|
|4|1|1,2,4|`'### Understanding Convolu...or images.\n### A Note Abo'`
|8|2|2,4,8|`'_Features_ is never used ...since we have two layers.'`
|3|4|3,4,8|`"That's because a linear l...d less as it gets deeper."`
|9|5|5,9|`'We can see we get the sam...oing to show it here too!'`
|6|10|6,10|`"We did do that in the `ge...well! Let's find out why."`
|7|7|7|`"However, this can cause p...ochs and see how it goes."`
