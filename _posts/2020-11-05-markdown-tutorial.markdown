---
layout: post
title:  "Markdown Tutorial"
date:   2020-11-06 12:54:04 -0700
categories: markdown tutorial
---
In this post, I will be writing a tutorial on how to create a Markdown from scratch and all that a beginner needs to know about it.

Markdown is a lightweight Markup language with easy to use plain text formatting syntax that was created by John Gruber and Aaron Swartz in 2004.
It is used for styling different forms of writing like formatting README files, writing messages in online discussions platform, writing content for the web and to create rich text.

## Basic Markdown Syntaxes
Syntaxes are set of rules for grammar and spelling that defines the combination of symbols considered to be correctly structured in a particular programming language.

##### Headings
Headings in Markdown are any line which is prefixed with the hashtag (#) symbol. The number of hashtags represents the heading level. A total of 6 levels can be made with 6 hashtags but in most writings, only 3 is commonly used. Headings are useful in subdividing reports in the right order, organizing and making reports look aesthetically pleasing. The syntax in block quotes are showing what the text looks like in Markdown.

```
# Heading 1
## Heading 2  
### Heading 3
```
# Heading 1
## Heading 2  
### Heading 3

##### Texts
When writing text in Markdown, you can place emphasis on a word by wrapping it in asterisks (*) or underscores (_). They can range from 1 to 3 symbols based on the extent of the emphasis. The syntax in block quotes are showing what the text looks like in Markdown.
```
*Item 1*  
**Item 2**  
__Item 3__
```
*Item 1*  
**Item 2**  
__Item 3__

When adding a link to a text, the text will we wrapped with the links in square brackets [] followed by the URL to be linked in brackets (). The syntax in block quote is showing what the text looks like in Markdown.
```
[Atom](https://atom.io/)
```
[Atom](https://atom.io/)

When writing quotes, the text should start with the greater than sign (>) that converts the text to a block text. The syntax in block quote is showing what the text looks like in Markdown.
```
> On the journey to becoming you must persevere.
```
> On the journey to becoming you must persevere.

##### Images
Images are written in similar format as when attaching a link to a text. The only difference is that the line starts with the exclamation mark (!). The syntax in block quote is showing what the text looks like in Markdown.
```
![octocat](https://github-atom-io-herokuapp-com.freetls.fastly.net/assets/index-octonaut-8ece2623b8966578e2414c89b7b7190cb56339d1f8b7d260adf62110ce9f39c4.svg)
```
![octocat](https://github-atom-io-herokuapp-com.freetls.fastly.net/assets/index-octonaut-8ece2623b8966578e2414c89b7b7190cb56339d1f8b7d260adf62110ce9f39c4.svg)

##### Lists
Lists are written with the following symbols (*, - or +) or numbers at the beginning of the line. For more formatting, the line can also be indented to create nested lists. The lists can be in ordered or unordered forms. The syntax in block quotes are showing what the text looks like in Markdown.
```
Ordered
1. Item 1
2. Item 2
3. Item 3
   1. Item 3a
   2. Item 3b

Unordered
* Item 1
* Item 2
  * Item 2a
  * Item 2b
```
Ordered
1. Item 1
2. Item 2
3. Item 3
   1. Item 3a
   2. Item 3b

Unordered
* Item 1
* Item 2
  * Item 2a
  * Item 2b

##### Horizontal lines
Horizontal lines (---) are used to denote visual separation between different sections of a text. The syntax in block quote is showing what the text looks like in Markdown.
```
---
```
---
##### Code snippets
Code snippets are visible to readers of an article by using the back-tick symbol around a code in a sentence. For example;

```
```r
#read in the csv
all_covid_data <- read.csv("path/to/my/file.csv")```
```
```r
#read in the csv
all_covid_data <- read.csv("path/to/my/file.csv")
```
##### Inline code
Inline codes are written by using the back tick and/or less and greater than symbol. The syntax in block quote is showing what the text looks like in Markdown.
```
For an inline code you can use
`<this>` in the text line.
```
For an inline code you can use
`<this>` in the text line.

## Implementations of Markdown
Implementations of Markdown are available for a lot of programming languages and applications and also multiple platforms support this Markup language.  
In as much as Markdown is a minimal Markup language that is read and edited with the text editors, there are specially designed editors that are beneficial in previewing the files and these are available for all major platforms. Examples are;
1. **Atom**: A desktop application built with HTML, JavaScript, CSS, and Node.js integration. It also serves as an Integrated Development Environment (IDE).
2. **Doxygen**: A source code documentation generator which supports Markdown with extra features.
3. **R Studios**: An Integrated Development Environment (IDE) for R language.
4. **Sublime Text**: A sophisticated text editor for code, markup and prose.
5. **GitHub Flavored Markdown (GFM)**: uses its own version of the Markdown syntax that provides an additional set of useful features, many of which make it easier to work with content on GitHub.com. It is useful for rendering README files in GitHub.
6. **Discount**: A C implementation.
7. **PHP Markdown**: A library package that includes the PHP Markdown parser and its sibling PHP Markdown Extra with additional features.
8. **Markdig**: A .NET library that follows the CommonMark specifications and includes a collection of extensions and the ability for the user to create their own.
9. **MarkAPL**: A converter written in Dyalog APL language.
10. **Showdown and Smartdown**: Markdown renderers in JavaScript.
11. **Hackmd.io**: An online Markdown editor that supports Markdown with extra features.
12. **Gomarkdown**: Markdown parser and HTML renderer in Go.

## Reasons you should use Markdown.
1. It is suitable for everything. From writing online blog posts, to creating README files for projects and more. Markdown is an easy way to provide structure and style to any document with ease.
2. It is platform independent because it is a plaintext file. Markdown can be created on any device running Operating System because it doesn't need a proprietary software like Microsoft word.
3. It is portable. Files containing markdown can be viewed using virtually any application
4. It is everywhere. Multiple websites and applications support the use of Markdown. Examples are GitHub, Reddit, R Studios etc
