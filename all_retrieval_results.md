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

I listing only those Spans that are at most a distance of `max_dist` (2000 characters) apart, for brevity:

|Start Passage|End Passage|Distance|
|:-:|:-:|:-:|
|10|4|34564|
|10|3|36699|
|10|1|38945|
|4|3|-208|
|4|1|2038|
|3|1|-217|
