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


