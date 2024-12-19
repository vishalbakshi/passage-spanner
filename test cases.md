## Test Cases

A running list of test cases that I used to check my code. Skip to:

- [Passages that partially overlap](#passages-that-partially-overlap)
- [Passages that are completely contained within other passages](#passages-that-are-completely-contained-within-other-passages)
- [Multiple passages that could form chains of overlaps](#multiple-passages-that-could-form-chains-of-overlaps)
- Passages that appear multiple times in the document
- Empty or whitespace-only passages
- Passages with special characters or formatting
- Non-existent passages
- Passages in different orders

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

Expected final passages:

```
"brown fox jumps over the lazy dog.\nA clever"
"fox jumps over the lazy dog.\nA clever"
"over the lazy dog."
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

### Multiple passages that could form chains of overlaps

```
"""Once upon a time, a magical crystal glowed brightly.
Its light danced across the ancient cavern walls.
Deep within, secrets waited to be discovered."""
```

Passages:

|passage|start|end|
|:-:|:-:|:-:|
|`"magical crystal"`|20|34|
|`"crystal glowed"`|28|41|
|`"glowed brightly"`|36|50|
|`"brightly.\nIts light"`|43|61|
|`"light danced"`|57|68|
|`"Deep within"`|103|113|
|`"to be discovered"`|131|146|

Spans:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"magical crystal"`|`"crystal glowed"`|-6|`True`|
|`"magical crystal"`|`"glowed brightly"`|2|`True`|
|`"magical crystal"`|`"brightly.\nIts light"`|9|`True`|
|`"magical crystal"`|`"light danced"`|23|`False`|
|`"magical crystal"`|`"Deep within"`|69|`False`|
|`"magical crystal"`|`"to be discovered"`|97|`False`|
|`"crystal glowed"`|`"glowed brightly"`|-5|`True`|
|`"crystal glowed"`|`"brightly.\nIts light"`|2|`True`|
|`"crystal glowed"`|`"light danced"`|16|`True`|
|`"crystal glowed"`|`"Deep within"`|62|`False`|
|`"crystal glowed"`|`"to be discovered"`|90|`False`|
|`"glowed brightly"`|`"brightly.\nIts light"`|-7|`True`|
|`"glowed brightly"`|`"light danced"`|7|`True`|
|`"glowed brightly"`|`"Deep within"`|53|`False`|
|`"glowed brightly"`|`"to be discovered"`|81|`False`|
|`"brightly.\nIts light"`|`"light danced"`|-4|`True`|
|`"brightly.\nIts light"`|`"Deep within"`|42|`False`|
|`"brightly.\nIts light"`|`"to be discovered"`|70|`False`|
|`"light danced"`|`"Deep within"`|35|`False`|
|`"light danced"`|`"to be discovered"`|63|`False`|
|`"Deep within"`|`"to be discovered"`|18|`True`|

Filtering out all spans that have a distance of more than 20 characters and grouping by first passage:

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"magical crystal"`|`"crystal glowed"`|-6|`True`|
|`"magical crystal"`|`"glowed brightly"`|2|`True`|
|`"magical crystal"`|`"brightly.\nIts light"`|9|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"crystal glowed"`|`"glowed brightly"`|-5|`True`|
|`"crystal glowed"`|`"brightly.\nIts light"`|2|`True`|
|`"crystal glowed"`|`"light danced"`|16|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"glowed brightly"`|`"brightly.\nIts light"`|-7|`True`|
|`"glowed brightly"`|`"light danced"`|7|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"brightly.\nIts light"`|`"light danced"`|-4|`True`|

|start|end|distance|<= `max_dist`|
|:-:|:-:|:-:|:-:|
|`"Deep within"`|`"to be discovered"`|18|`True`|

The final passages should be:

```
"magical crystal glowed brightly.\nIts light"
"crystal glowed brightly.\nIts light danced"
"glowed brightly.\nIts light danced"
"brightly.\nIts light danced"
"Deep within, secrets waited to be discovered"
```
