---
layout: post
title: "beginning markdown"
date: 2016-04-09 08:46:36
description: ""
category: markdown
tags: [markdown]
---

# Beginning Markdown 
I started my hexo blog last year, and recently I get down to adding content frequently. So, I begin with learning besic markdown. The following tips are from http://www.markdowntutorial.com/. 
## 1. Italics and Bold 
To make a phrase italic in Markdown, you can surround words with an underscore ( _ ).Similarly, to make phrases bold in Markdown, you can surround words with two asterisks ( ** ).

for example:

italic:  
`_this_` ==> _this_

bold:  
`**this**` ==> **this**

italic and bold:  
`**_this_**` ==> **_this_**


## 2. headers 

# Header one
## Header two
### Header three 
#### Header four
##### Header five
###### Header six

You can't really make a header bold, but you can italicize certain words.for example:

`##Header _two_`
## Header _two_ 

## 3. Links 

### 3.1. inline link 

To create an **inline link**, you wrap the link text in brackets ( [ ] ), and then you wrap the link in parenthesis ( ( ) ).

`####The Latest News from [the BBC](www.bbc.com/news)` is shown as below:
#### The Latest News from [the BBC](www.bbc.com/news) 

### 3.2. reference link 

The other link type is called a **reference link**. As the name implies, the link is actually a reference to another place in the document.

```
Do you want to [see something fun][a fun place]?
Well, do I have [the website for you][another fun place]!
[a fun place]: www.zombo.com
[another fun place]: www.stumbleupon.com
```
is shown as below:

Do you want to [see something fun][a fun place]?

Well, do I have [the website for you][another fun place]!

[a fun place]: www.zombo.com
[another fun place]: www.stumbleupon.com

## 4. Images 

### 4.1. inline image 

Images also have two styles, just like links. To create an inline image, you'll use the same syntax as an inline link.

`![A representation of Octdrey Catburn](http://octodex.github.com/images/octdrey-catburn.jpg)` is shown as below:
![A representation of Octdrey Catburn](http://octodex.github.com/images/octdrey-catburn.jpg)

### 4.2. refenence image 

For a reference image, you'll follow the same pattern as a reference link. You'll precede the Markdown with an exclamation point, then provide two brackets for the alt text, and then two more for the image tag. At the bottom of your Markdown page, you'll define an image for the tag.

```
![The first father][First Father]

![The second first father][Second Father]

[First Father]: http://octodex.github.com/images/founding-father.jpg
[Second Father]: http://octodex.github.com/images/foundingfather_v2.png
```
is shown as below:

![The first father][First Father]

![The second first father][Second Father]

[First Father]: http://octodex.github.com/images/founding-father.jpg
[Second Father]: http://octodex.github.com/images/foundingfather_v2.png

## 5. Blockquotes 

A blockquote is a sentence or paragraph that's been specially formatted to draw attention to the reader. To create a block quote, all you have to do is preface a line with the "greater than" caret (>). For example:

```
> "Her eyes had called him and his soul had leaped at the call. To live, to err, to fall, to triumph, to recreate life out of life!"
```

> "Her eyes had called him and his soul had leaped at the call. To live, to err, to fall, to triumph, to recreate life out of life!"

You can also place a caret character on each line of the quote. This is particularly useful if your quote spans multiple paragraphs. For example:

```
> —Of whom are you speaking? Stephen asked at length.
>
> Cranly did not answer.
```


> —Of whom are you speaking? Stephen asked at length.
>
> Cranly did not answer.

## 6. Lists 

### 6.1. unordered list 

To create an unordered list, you'll want to preface each item in the list with an asterisk ( * ). Each list item also gets its own line. For example, a grocery list in Markdown might look like this:

```
* Milk
* Eggs
* Salmon
* Butter
```

* Milk
* Eggs
* Salmon
* Butter

### 6.2. ordered list 

An ordered list is prefaced with numbers, instead of asterisks. Take a look at this recipe:
```
1. Crack three eggs over a bowl
2. Pour a gallon of milk into the bowl
3. Rub the salmon vigorously with butter
4. Drop the salmon into the egg-milk bowl
```

1. Crack three eggs over a bowl
2. Pour a gallon of milk into the bowl
3. Rub the salmon vigorously with butter
4. Drop the salmon into the egg-milk bowl

### 6.3. more depth 

To make a list with more depth, or, to nest one list within another, all you have to do is to remember to indent each asterisk one space more than the preceding item. For example:

```
* Tintin
 * A reporter
 * Has poofy orange hair
 * Friends with the world's most awesome dog
* Haddock
 * A sea captain
 * Has a fantastic beard
 * Loves whiskey
   * Possibly also scotch?
```

* Tintin
 * A reporter
 * Has poofy orange hair
 * Friends with the world's most awesome dog
* Haddock
 * A sea captain
 * Has a fantastic beard
 * Loves whiskey
   * Possibly also scotch?


### 6.4. a paragraph example

```
1. Crack three eggs over a bowl.

 Now, you're going to want to crack the eggs in such a way that you don't make a mess.

 If you _do_ make a mess, use a towel to clean it up!

2. Pour a gallon of milk into the bowl.

 Basically, take the same guidance as above: don't be messy, but if you are, clean it up!

3. Rub the salmon vigorously with butter.

   By "vigorous," we mean a strictly vertical motion. Julia Child once quipped:
   > Up and down and all around, that's how butter on salmon goes.
4. Drop the salmon into the egg-milk bowl.

   Here are some techniques on salmon-dropping:

   * Make sure no trout or children are present
   * Use both hands
   * Always have a towel nearby in case of messes
```

1. Crack three eggs over a bowl.

 Now, you're going to want to crack the eggs in such a way that you don't make a mess.

 If you _do_ make a mess, use a towel to clean it up!

2. Pour a gallon of milk into the bowl.

 Basically, take the same guidance as above: don't be messy, but if you are, clean it up!

3. Rub the salmon vigorously with butter.

   By "vigorous," we mean a strictly vertical motion. Julia Child once quipped:
   > Up and down and all around, that's how butter on salmon goes.
4. Drop the salmon into the egg-milk bowl.

   Here are some techniques on salmon-dropping:

   * Make sure no trout or children are present
   * Use both hands
   * Always have a towel nearby in case of messes

## 7. Paragraphs 

### 7.1. hard break 

```
Do I contradict myself?

Very well then I contradict myself,

(I am large, I contain multitudes.)
```

is shown as below:

Do I contradict myself?

Very well then I contradict myself,

(I am large, I contain multitudes.)

### 7.2. soft break 

```
Do I contradict myself?··
Very well then I contradict myself,··
(I am large, I contain multitudes.)
```

is shown as below(**a dot represents a space**):

Do I contradict myself?  
Very well then I contradict myself,  
(I am large, I contain multitudes.)
