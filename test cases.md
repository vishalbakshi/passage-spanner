## Test Cases

A running list of test cases that I used to check my code.

### Passages that partially overlap

`max_dist` = 20.

```
"""The quick brown fox jumps over the lazy dog.
A clever fox leaps across the sleeping hound.
The nimble creature bounds through the garden."""
```

Here are the starting and ending positions of each passage in the `document` (manually counted):

|passage|start|end|
|:-:|:-:|:-:|
|`"brown fox jumps over"`|10|29
|`"fox jumps over the lazy"`|16|38
|`"over the lazy dog.\nA clever"`|26|52
|`"the lazy dog"`|31|42
|`"sleeping hound.\nThe nimble"`|75|100

From this I can see that my `end_pos` calculation is actually incorrect, they are off by 1. I need to subtract 1:

```python
def end_pos(self): return self.start_pos + self.length - 1
```

Looking now at all 10 spans manually:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"brown fox jumps over"`|`"fox jumps over the lazy"`|-13|`True`|
|`"brown fox jumps over"`|`"over the lazy dog.\nA clever"`|-3|`True`|
|`"brown fox jumps over"`|`"the lazy dog"`|2|`True`|
|`"brown fox jumps over"`|`"sleeping hound.\nThe nimble"`|46|`False`|
|`"fox jumps over the lazy"`|`"over the lazy dog.\nA clever"`|-12|`True`|
|`"fox jumps over the lazy"`|`"the lazy dog"`|-7|`True`|
|`"fox jumps over the lazy"`|`"sleeping hound.\nThe nimble"`|37|`False`|
|`"over the lazy dog.\nA clever"`|`"the lazy dog"`|-21|`True`|
|`"over the lazy dog.\nA clever"`|`"sleeping hound.\nThe nimble"`|23|`False`|
|`"the lazy dog"`|`"sleeping hound.\nThe nimble"`|33|`False`|

They're all off by 1 but that's expected since my end position moved back 1.

I'm now wondering if my `distance` calculation is wrong. Take for example `the lazy`:

```
0 1 2 3 4 5 6 7 8
t h e   l a z y
```

There is 1 character between these two. So in that sense the distance should be 1. If I was writing documentation, this distance would be "the number of characters between the two passages".

However based on my existing calculation:

```python
def distance(self): return self.end.start_pos - self.start.end_pos
```

The start position of the second word is `4` and the end position of the first word is `2`. The distance is then 2. This distance would be "the number of elements from the last character of the first passage to the first character of the last passage". I'm not sure which one is better. This latter one sounds fine.

Moving on, filtering out all spans that have a distance of more than 20 characters:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"brown fox jumps over"`|`"fox jumps over the lazy"`|-13|`True`|
|`"brown fox jumps over"`|`"over the lazy dog.\nA clever"`|-3|`True`|
|`"brown fox jumps over"`|`"the lazy dog"`|2|`True`|
|`"fox jumps over the lazy"`|`"over the lazy dog.\nA clever"`|-12|`True`|
|`"fox jumps over the lazy"`|`"the lazy dog"`|-7|`True`|
|`"over the lazy dog.\nA clever"`|`"the lazy dog"`|-21|`True`|


breaking it out into three groups by first passage:

|start|end|distance|end.end_pos|
|:-:|:-:|:-:|:-:|
|`"brown fox jumps over"`|`"fox jumps over the lazy"`|-13|38
|`"brown fox jumps over"`|`"over the lazy dog.\nA clever"`|-3|52
|`"brown fox jumps over"`|`"the lazy dog"`|2|42

|start|end|distance|end.end_pos|
|:-:|:-:|:-:|:-:|
|`"fox jumps over the lazy"`|`"over the lazy dog.\nA clever"`|-12|52
|`"fox jumps over the lazy"`|`"the lazy dog"`|-7|42

|start|end|distance|
|:-:|:-:|:-:|:-:|
|`"over the lazy dog.\nA clever"`|`"the lazy dog"`|-21|42


Now comes the interesting part! Currently, I am finding the maximum span based on the max end position of the ending passage:

```python
L(max(g, key=lambda s: s.end.end_pos) for g in gs.values())
```

This would result in the following passages:

|start|end|distance|end.end_pos|
|:-:|:-:|:-:|:-:|
|`"brown fox jumps over"`|`"over the lazy dog.\nA clever"`|-3|52

|start|end|distance|end.end_pos|
|:-:|:-:|:-:|:-:|
|`"fox jumps over the lazy"`|`"over the lazy dog.\nA clever"`|-12|52

|start|end|distance|
|:-:|:-:|:-:|
|`"over the lazy dog.\nA clever"`|`"the lazy dog"`|-21|42

I'll update `end_pos` to be:

```python
def end_pos(self): return self.start_pos + self.length - 1
```

### Passages that are completely contained within other passages

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

