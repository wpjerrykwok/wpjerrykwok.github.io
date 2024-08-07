---
title: Markdown .md syntax
tags: [Markdown, Study Notes]
style: border
color: danger
description: my markdown reference card
asset_path: /assets/images/blog/2024-07-27/
---
To help myself to quick access to some common markdown syntax.

![Two cute claymation monsters on a gradient background working together - Image created with Microsoft Designer]({{ page.asset_path }}my_image.jpeg)

## Headings

```md
# Headline Level 1
```

# Headline Level 1

```md
## Headline Level 2
```

## Headline Level 2

```md
### Headline Level 3
```

### Headline Level 3

```md
#### Headline Level 4
```

#### Headline Level 4

```md
##### Headline Level 5
```

##### Headline Level 5

```md
###### Headline Level 6
```

###### Headline Level 6

```md
Also Headline Level 1
=
```

Also Headline Level 1
=

```md
Also Headline Level 2
-
```

Also Headline Level 2
-

---

## Paragraphs

```md
This is the first line. 
This is normal text staying with the first line.

This is the second line going to next line with extra blank line.
```

This is the first line. 
This is normal text staying with the first line.

This is the second line going to next line with extra blank line.

---

## Line Breaks

```md
This is first line.   
This is second line by 3 extra spaces tailing the first line.
```

This is first line.   
This is second line by 3 extra spaces tailing the first line.

---

## Emphasis

```md
**BOLD by adding two asterisks before and after**
```

**BOLD by adding two asterisks before and after**

```md
__BOLD by adding two underscores before and after__
```

__BOLD by adding two underscores before and after__

```md
*italic by adding one asterisk before and after*
```

*italic by adding one asterisk before and after*

```md
_italic by adding one underscore before and after_
```

_italic by adding one underscore before and after_

```md
***BOLD and italic by using three asterisks or underscore before and after***
```

***BOLD and italic by using three asterisks or underscore before and after***

```md
> Blockquotes
>
> multiple lines
> > Nested Blockquotes
```

> Blockquotes
>
> multiple lines
> > Nested Blockquotes

---

## Lists

```md
1. First Item in ordered list
2. Numbering does not matter
   1. Indented
   1. Numbering does not matter
1. Here we go again

- First item in unordered list
- Second
  * Indented
- We can use -, *, +
```

1. First Item in ordered list
2. Numbering does not matter
   1. Indented
   1. Numbering does not matter
1. Here we go again

- First item in unordered list
- Second
  * Indented
- We can use -, *, +

---

## Code

```md
`enclosed with backtick`
```

`enclosed with backtick`

````md
```html
<html>
  <head>
    Tab to make code block
  </head>
</html>
```

```py
<code block>
```
````

```html
<html>
  <head>
    Tab to make code block
  </head>
</html>
```

```py
<code block>
```

---

## Rulers

```md
3 asterisks
***
```

3 asterisks
***

```md
3 dashes
---
```

3 dashes
---

```md
3 underscores
___
```

3 underscores
___

---

## Links

```md
link text in brackets and URL in parentheses
[Jerry's LinkedIn](https://www.linkedin.com/in/wpjerrykwok/)
```

link text in brackets and URL in parentheses
[Jerry's LinkedIn](https://www.linkedin.com/in/wpjerrykwok/)

```md
put in <> for a quick add   
<https://www.linkedin.com/in/wpjerrykwok/>
```

put in <> for a quick add
<https://www.linkedin.com/in/wpjerrykwok/>

```md
bracket followed by bracket for reference style link [Jerry's LinkedIn][1]

[1]: https://www.linkedin.com/in/wpjerrykwok/
```

bracket followed by bracket for reference style link [Jerry's LinkedIn][1]

[1]: https://www.linkedin.com/in/wpjerrykwok/

---

## Images

```md
! followed by brackets and then path in parentheses
![Sailing Team]({{ page.asset_path }}team.jpeg)
```

! followed by brackets and then path in parentheses
![Sailing Team]({{ page.asset_path }}team.jpeg)

```md
To control image size
<img src="{{ page.asset_path }}team.jpeg" width="100" height="100">
```

<img src="{{ page.asset_path }}team.jpeg" width="100" height="100">

---

## Footnotes

```md
This is a footnote[^1]. Another footnote[^2].

[^1]: My reference
[^2]: Another footnote
```

This is a footnote[^1]. Another footnote[^2].

[^1]: My reference
[^2]: Another footnote

---

## Table

```md
left |center|right
:-----|:-----:|----:
One|Two|$1.00
```

left |center|right
:-----|:-----:|----:
One|Two|$1.00

---

## Task List

```md
- [x] dash with brackets
- [ ] First
   - [x] indented One
- [ ] Second
```

- [x] dash with brackets
- [ ] First
   - [x] indented One
- [ ] Second

---

## Collapsed Details

```md
<details>
<summary>collapsed</summary>
This is the copy for the collapsed text.
</details>
```

<details>
<summary>collapsed</summary>
This is the copy for the collapsed text.
</details>

---

## Emoji

```md
emojis :joy: :tada:
```

emojis :joy: :tada:

---

## Alert Syntax

```md
> :memo: **Note:**
> Let's take a note.

> :bulb: **Tip:**
> Pocket a tip.

> :warning: **Warning:**
> This is a Warning.
```

> :memo: **Note:**
> Let's take a note.

> :bulb: **Tip:**
> Pocket a tip.

> :warning: **Warning:**
> This is a Warning.

_Reference:_

[Markdown Guide](https://www.markdownguide.org/)
