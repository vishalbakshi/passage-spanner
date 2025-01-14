## Test Cases

A running list of test cases that I used to check my code. Skip to:
- [Passages that partially overlap](#passages-that-partially-overlap)
- [Multiple passages that could form chains of overlaps](#multiple-passages-that-could-form-chains-of-overlaps)
- [Repeated passages](#repeated-passages)
- [Empty passage](#empty-passage)
- [Whitespace character passages](#whitespace-character-passages)
- [Passages with special characters or formatting](#passages-with-special-characters-or-formatting)
- [Passages that are completely contained within other passages](#passages-that-are-completely-contained-within-other-passages)
- [Non-existent passages](#non-existent-passages)
- [Passages in different orders](#passages-in-different-orders)

`max_dist` = 20.

### Passages that partially overlap
[top](#test-cases)

```
document = """The quick brown fox jumps over the lazy dog.
A clever fox leaps across the sleeping hound.
The nimble creature bounds through the garden."""

passages = [
    "brown fox jumps over",
    "fox jumps over the lazy",
    "over the lazy dog.\nA clever",  
    "the lazy dog",
    "sleeping hound.\nThe nimble"    
]
```
Here are the starting and ending positions of each passage in the `document` (manually counted):

|rank|passage|start_pos|end_pos|
|:-:|:-:|:-:|:-:|
|1|`"brown fox jumps over"`|10|29
|2|`"fox jumps over the lazy"`|16|38
|3|`"over the lazy dog.\nA clever"`|26|52
|4|`"the lazy dog"`|31|42
|5|`"sleeping hound.\nThe nimble"`|75|100

Looking now at all 10 spans manually:

|start rank|end rank|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|1|2|-13|`True`|
|1|3|-3|`True`|
|1|4|2|`True`|
|1|5|46|`False`|
|2|3|-12|`True`|
|2|4|-7|`True`|
|2|5|37|`False`|
|3|4|-21|`True`|
|3|5|23|`False`|
|4|5|33|`False`|

Filtering out all spans that have a distance of more than 20 characters:

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|2|10|38
|1|3|10|52
|1|4|10|42
|2|3|16|52
|2|4|16|42
|3|4|26|42

grouping by ending passage end position:

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|2|10|38

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|4|10|42
|2|4|16|42
|3|4|26|42

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|3|10|52
|2|3|16|52

keeping the span with the smallest start.start_pos:

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|2|10|38

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|4|10|42

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|3|10|52

grouping by start.start_pos:

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|2|10|38
|1|4|10|42
|1|3|10|52

keeping the span with the largest end.end_pos:

|start rank|end rank|start.start_pos|end.end_pos|`highest_rank`|Included passages|
|:-:|:-:|:-:|:-:|:-:|:-:|
|1|3|10|52|1|1,2,3,4

```
document = """The quick brown fox jumps over the lazy dog.
A clever fox leaps across the sleeping hound.
The nimble creature bounds through the garden."""

passages = [
    1 "brown fox jumps over",
    2 "fox jumps over the lazy",
    3 "over the lazy dog.\nA clever",  
    4 "the lazy dog",
    5 "sleeping hound.\nThe nimble"    
]
```

Since the final span has a highest rank of 1, it should be the first text in the list, following by the unused passage of rank 5:

```
"brown fox jumps over the lazy dog.\nA clever"
"sleeping hound.\nThe nimble"
```

### Multiple passages that could form chains of overlaps
[top](#test-cases)

```
"""Once upon a time, a magical crystal glowed brightly.
Its light danced across the ancient cavern walls.
Deep within, secrets waited to be discovered."""
```

Passages:

|rank|passage|start_pos|end_pos|
|:-:|:-:|:-:|:-:|
|1|`"magical crystal"`|20|34|
|2|`"crystal glowed"`|28|41|
|3|`"glowed brightly"`|36|50|
|4|`"brightly.\nIts light"`|43|61|
|5|`"light danced"`|57|68|
|6|`"Deep within"`|103|113|
|7|`"to be discovered"`|131|146|

Spans:

|start rank|end rank|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|1|2|-6|`True`|
|1|3|2|`True`|
|1|4|9|`True`|
|1|5|23|`False`|
|1|6|69|`False`|
|1|7|97|`False`|
|2|3|-5|`True`|
|2|4|2|`True`|
|2|5|16|`True`|
|2|6|62|`False`|
|2|7|90|`False`|
|3|4|-7|`True`|
|3|5|7|`True`|
|3|6|53|`False`|
|3|7|81|`False`|
|4|5|-4|`True`|
|4|6|42|`False`|
|4|7|70|`False`|
|5|6|35|`False`|
|5|7|63|`False`|
|6|7|18|`True`|

Filtering out all spans that have a distance of more than `max_dist` (20 chars):

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|2|20|41
|1|3|20|50
|1|4|20|61
|2|3|28|50
|2|4|28|61
|2|5|28|68
|3|4|36|61
|3|5|36|68
|4|5|43|68
|6|7|103|146

grouping by ending passage end position and keeping the span with the smallest start.start_pos:

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|2|20|41

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|3|20|50

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|4|20|61

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|2|5|28|68

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|6|7|103|146

grouping by start.start_pos and keeping the span with the largest end.end_pos:

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|1|4|20|61

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|2|5|28|68

|start rank|end rank|start.start_pos|end.end_pos|
|:-:|:-:|:-:|:-:|
|6|7|103|146

The final texts should be as followed (no unused passages):

```
"magical crystal glowed brightly.\nIts light"
"crystal glowed brightly.\nIts light danced"
"Deep within, secrets waited to be discovered"
```

### Repeated passages
[top](#test-cases)

Building out this test made me realize that I needed to find all occurences of a passage in a document (`document.find` only returns the first occurence) so I used `regex.finditer`.

```
"""The quick brown fox jumps over the lazy dog.
The quick brown fox runs through the field.
A lazy dog sleeps in the sun."""
```

Passages:

|passage|start|end|
|:-:|:-:|:-:|
|`"quick brown fox"`|4|18|
|`"lazy dog"`|35|42|
|`"quick brown fox"`|49|63|
|`"lazy dog"`|91|98|

Spans:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"quick brown fox"`|`"lazy dog"`|17|`True`|
|`"quick brown fox"`|`"quick brown fox"`|31|`False`|
|`"quick brown fox"`|`"lazy dog"`|73|`False`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"lazy dog"`|`"quick brown fox"`|7|`True`|
|`"lazy dog"`|`"lazy dog"`|49|`False`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"quick brown fox"`|`"lazy dog"`|28|`False`|

Filtering out all spans that have a distance of more than 20 characters:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"quick brown fox"`|`"lazy dog"`|17|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"lazy dog"`|`"quick brown fox"`|7|`True`|

The final passages should be:

```
"quick brown fox jumps over the lazy dog"
"lazy dog.\nThe quick brown fox"
```

### Empty passage
[top](#test-cases)

After running this case, I updated the `end_pos` calculation to account for `0`-length strings. 

```
document = "doc"
passages = [""]
```

Passages:

|passage|start|end|
|:-:|:-:|:-:|
|`''`|0|0|
|`''`|1|1|
|`''`|2|2|
|`''`|3|3|

Spans:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`''`|`''`|1|`True`|
|`''`|`''`|2|`True`|
|`''`|`''`|3|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`''`|`''`|1|`True`|
|`''`|`''`|2|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`''`|`''`|1|`True`|

Longest span for each starting passage:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`''`|`''`|3|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`''`|`''`|2|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`''`|`''`|1|`True`|

Resulting passages:

```
"doc"
"oc"
"c"
```

## Whitespace character passages
[top](#test-cases)

```
document = "This is a\nsample\tdocument with some content."
passages = [" ", "   ", "\n", "\t"]
```

Passages:

|passage|start|end|
|:-:|:-:|:-:|
|`' '`|4|4|
|`' '`|7|7|
|`'\n'`|9|9|
|`'\t'`|16|16|
|`' '`|25|25|
|`' '`|30|30|
|`' '`|35|35|

Spans:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`' '`|`' '`|3|`True`|
|`' '`|`'\n'`|5|`True`|
|`' '`|`'\t'`|12|`True`|
|`' '`|`' '`|21|`False`|
|`' '`|`' '`|26|`False`|
|`' '`|`' '`|31|`False`|


|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`' '`|`'\n'`|2|`True`|
|`' '`|`'\t'`|9|`True`|
|`' '`|`' '`|18|`True`|
|`' '`|`' '`|23|`False`|
|`' '`|`' '`|28|`False`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`'\n'`|`'\t'`|7|`True`|
|`'\n'`|`' '`|16|`True`|
|`'\n'`|`' '`|21|`False`|
|`'\n'`|`' '`|26|`False`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`'\t'`|`' '`|9|`True`|
|`'\t'`|`' '`|14|`True`|
|`'\t'`|`' '`|19|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`' '`|`' '`|5|`True`|
|`' '`|`' '`|10|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`' '`|`' '`|5|`True`|

Longest span for each starting passage:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`' '`|`'\t'`|12|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`' '`|`' '`|18|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`'\n'`|`' '`|16|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`'\t'`|`' '`|19|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`' '`|`' '`|10|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`' '`|`' '`|5|`True`|

Resulting passages:

```
" is a\nsample\t"
" a\nsample\tdocument "
"\nsample\tdocument "
"\tdocument with some "
" with some "
" some "
```

### Passages with special characters or formatting
[top](#test-cases)

```
document = """Special *formatting* and (punctuation) test!
Some text with @#$% special chars.
More text with <html> tags and line-breaks
    plus some indentation."""
passages = [
    "*formatting*",
    "@#$%",
    "<html>",
    "    plus"
]
```

Passages:

|passage|start|end|
|:-:|:-:|:-:|
|`"*formatting*"`|8|19|
|`"@#$%"`|60|63|
|`"<html>"`|95|100|
|`"    plus"`|123|130|

Spans:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"*formatting*"`|`"@#$%"`|41|`False`|
|`"*formatting*"`|`"<html>"`|76|`False`|
|`"*formatting*"`|`"    plus"`|104|`False`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"@#$%"`|`"<html>"`|32|`False`|
|`"@#$%"`|`"    plus"`|60|`False`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"<html>"`|`"    plus"`|23|`False`|

All spans are greater than `max_dist` so there is no text extracted from the document.

### Passages that are completely contained within other passages
[top](#test-cases)

```
"""The majestic unicorn galloped through the enchanted forest.
Its rainbow mane sparkled in the golden sunlight.
Ancient magic flowed through the mystical creature."""
```

Passages:

|passage|start|end|
|:-:|:-:|:-:|
|`'majestic unicorn galloped through the enchanted'`|4|50
|`'unicorn galloped'`|13|28
|`'galloped through'`|21|36
|`'the enchanted forest.\nIts rainbow'`|38|70
|`'rainbow mane'`|64|75
|`'Ancient magic'`|110|122

Spans:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`'majestic unicorn galloped through the enchanted'`|`'unicorn galloped'`|-37|`True`|
|`'majestic unicorn galloped through the enchanted'`|`'galloped through'`|-29|`True`|
|`'majestic unicorn galloped through the enchanted'`|`'the enchanted forest.\nIts rainbow'`|-12|`True`|
|`'majestic unicorn galloped through the enchanted'`|`'rainbow mane'`|14|`True`|
|`'majestic unicorn galloped through the enchanted'`|`'Ancient magic'`|60|`False`|
|`'unicorn galloped'`|`'galloped through'`|-7|`True`|
|`'unicorn galloped'`|`'the enchanted forest.\nIts rainbow'`|10|`True`|
|`'unicorn galloped'`|`'rainbow mane'`|36|`False`|
|`'unicorn galloped'`|`'Ancient magic'`|82|`False`|
|`'galloped through'`|`'the enchanted forest.\nIts rainbow'`|2|`True`|
|`'galloped through'`|`'rainbow mane'`|28|`False`|
|`'galloped through'`|`'Ancient magic'`|74|`False`|
|`'the enchanted forest.\nIts rainbow'`|`'rainbow mane'`|-6|`True`|
|`'the enchanted forest.\nIts rainbow'`|`'Ancient magic'`|40|`False`|
|`'rainbow mane'`|`'Ancient magic'`|35|`False`|

Filtering out all spans that have a distance of more than 20 characters and grouping by first passage:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`'majestic unicorn galloped through the enchanted'`|`'unicorn galloped'`|-37|`True`|
|`'majestic unicorn galloped through the enchanted'`|`'galloped through'`|-29|`True`|
|`'majestic unicorn galloped through the enchanted'`|`'the enchanted forest.\nIts rainbow'`|-12|`True`|
|`'majestic unicorn galloped through the enchanted'`|`'rainbow mane'`|14|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`'unicorn galloped'`|`'galloped through'`|-7|`True`|
|`'unicorn galloped'`|`'the enchanted forest.\nIts rainbow'`|10|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`'galloped through'`|`'the enchanted forest.\nIts rainbow'`|2|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`'the enchanted forest.\nIts rainbow'`|`'rainbow mane'`|-6|`True`|

The final passages should be:

```
"majestic unicorn galloped through the enchanted forest.\nIts rainbow mane"
"unicorn galloped through the enchanted forest.\nIts rainbow"
"galloped through the enchanted forest.\nIts rainbow"
"the enchanted forest.\nIts rainbow mane"
```

### Non-existent passages
[top](#test-cases)

```
document = """The sky is blue.
The grass is green.
The sun is yellow.
The rose is red.
The cloud is white."""

passages = [
    "The sky is blue.",
    "The grass is green.",
    "This passage is not in the document.",
    "The sun is yellow.",
    "The rose is red.",
    "The cloud is white.",
    "This passage is also not in the document."
]
```

Passages:

|passage|start|end|
|:-:|:-:|:-:|
|`"The sky is blue."`|0|15|
|`"The grass is green."`|17|35|
|`"This passage is not in the document."`|-1||
|`"The sun is yellow."`|37|54|
|`"The rose is red."`|56|71|
|`"The cloud is white."`|73|91|
|`"This passage is also not in the document."`|-1||


Spans:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"The sky is blue."`|`"The grass is green."`|2|`True`
|`"The sky is blue."`|`"The sun is yellow."`|22|`False`
|`"The sky is blue."`|`"The rose is red."`|41|`False`
|`"The sky is blue."`|`"The cloud is white."`|58|`False`

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"The grass is green."`|`"The sun is yellow."`|2|`True`|
|`"The grass is green."`|`"The rose is red."`|21|`False`|
|`"The grass is green."`|`"The cloud is white."`|38|`False`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"The sun is yellow."`|`"The rose is red."`|2|`True`|
|`"The sun is yellow."`|`"The cloud is white."`|19|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"The rose is red."`|`"The cloud is white."`|2|`True`|

Largest Spans for each starting Passage that are under `max_dist`:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"The sky is blue."`|`"The grass is green."`|2|`True`

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"The grass is green."`|`"The sun is yellow."`|2|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"The sun is yellow."`|`"The cloud is white."`|19|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"The rose is red."`|`"The cloud is white."`|2|`True`|

Final result:

```
"The sky is blue.\nThe grass is green."
"The grass is green.\nThe sun is yellow."
"The sun is yellow.\nThe rose is red.\nThe cloud is white."
"The rose is red.\nThe cloud is white."
```

### Passages in different orders
[top](#test-cases)

```python
document = "The quick brown fox jumps over the lazy dog. The dog sleeps while the fox hunts."
passages = ["fox", "dog", "quick", "sleeps"]
```
Passages:

|passage|start|end|
|:-:|:-:|:-:|
|`"quick"`|4|8|
|`"fox"`|16|18|
|`"dog"`|40|42|
|`"dog"`|49|51|
|`"sleeps"`|53|58|
|`"fox"`|70|72|

Spans:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"quick"`|`"fox"`|8|`True`|
|`"quick"`|`"dog"`|32|`False`|
|`"quick"`|`"dog"`|41|`False`|
|`"quick"`|`"sleeps"`|45|`False`|
|`"quick"`|`"fox"`|62|`False`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"fox"`|`"dog"`|22|`False`|
|`"fox"`|`"dog"`|31|`False`|
|`"fox"`|`"sleeps"`|35|`False`|
|`"fox"`|`"fox"`|52|`False`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"dog"`|`"dog"`|7|`True`|
|`"dog"`|`"sleeps"`|11|`True`|
|`"dog"`|`"fox"`|28|`False`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"dog"`|`"sleeps"`|2|`True`|
|`"dog"`|`"fox"`|19|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"sleeps"`|`"fox"`|12|`True`|

Largest Spans for each starting Passage that are under `max_dist`:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"quick"`|`"fox"`|8|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"dog"`|`"sleeps"`|11|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"dog"`|`"fox"`|19|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"sleeps"`|`"fox"`|12|`True`|

Final result:

```
"quick brown fox"
"dog. The dog sleeps"
"dog sleeps while the fox"
"sleeps while the fox"
```
