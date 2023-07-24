REFERENCE: markdown-it demo




What the project does (intro)
How to run the project (installation and documentation)
Why it's noteworthy (interesting things)
Who maintains the project (contributing, references, licences)


HEADINGS (# + space + title)
# H1 
## H2
### H3
#### H4
##### H5
###### H6



LINES

___  (continues line)
---    (discontinues line) 
*** (line with points)



TYPOGRAPHIC REPLACEMENTS

	(c) ©
 (C)   ©
	(r) ®
	(R) ®
 (tm)  ™
(TM)  ™
(p) 
(P)
+- 

Test..          Test…
Test…         Test…
Test….        Test…
Test?....      Test?..
Test!......    Test!..

!!!!!!            !!!
????            ??
,,                  ,
-- ---            __ ___


EMPHASIS

** This text is in bold **
__This text is in bold__
*This text is in italic*
_This text is in italic_
~~This text is strikethrough~~


BLOCKQUOTES

>  Text with one part of block
>>  Text with two part of block
> > >  Text with three part of block


LISTS

- Unordered

+ Create a list starting with `+`, `-` or `*`
   + The spaces indicate the space in block
      - Details
   * Other thing


- Ordered

	1. One thing
	2. Two things
	3. Three things

(* You can use sequential numbers or use the same number)

23.Other thing
	1. Asfasdfasfd 


CODE

- Idented code
	
	// Some code
	Line 1 of code
	Line 2 of code
	Line 3 of code

- Block code "fences"

```
Code
```

- Sintax highlighting (indicating the language)

```js
Var foo = function(bar) {
	return bar ++;
}

Console.log(foo(5));
```


TABLES


|Team|Complete name|
|---------|----------------|
|RM    | Real Madrid Club de Fúbol|
|V|Valencia Club de Fútbol|
|ATH|Athletic de Bilbao|

(* If you want to text align is from right you should put ----: as the line )



LINKS

[Link text](Url)

(* If you put a url, this text is autoconvert to link)



IMAGES

![Alternative text of image](url)

(* Same that links, if you put a url of image)


EMOJIS

- Classic markup: :wink:   :crush:  :cry:
- Shortcuts (emoticons): :-)   :-(   ;)   8-)


SUBSCRIPT AND SUPERSCRIPT

19^th^
H~2~O


FORMAT TEXT

++ Inserted text++
==Marked text==

Footnote 1 link[^first]
Footnote 2 link[^second]


SECTIONS 

Term 1
  ~ Definition 1

Term 2
  ~ Definition 2a
  ~ Definition 2b



ABBREVATIONS

This is HTML abbreviation example.
*[HTML]: Hyper Text Markup Language


CUSTOM CONTAINERS (IN YELLOW)

::: warning
*here be dragons*
:::