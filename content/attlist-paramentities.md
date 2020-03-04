---
title: "can we have parameter entities in ATTLIST for reuse of attributes specification? #xml #dtd"
date: 2020-03-04T02:02:18+01:00
draft: false
---

----

> *See [**this very post** on wiki1](https://wiki1.mikf.pl/xml/dtd/attlist-paramentities.html).*

----

On Dec 1, 2013, user Sammi De Guzman asked on StackOverflow:\
(https://stackoverflow.com/questions/20308365)

> How do I declare attributes common to multiple elements?
> --------------------------------------------------------
>
> I have multiple elements I want to give these attributes:
>
> <div>
>
>     <!ATTLIST [all these elements]
>         width   CDATA   "0"
>         height  CDATA   "0"
>         margin  CDATA   "0 0 0 0"
>         padding CDATA   "0 0 0 0"
>         rotation CDATA  "0"
>         halign  (left|center|right|full)    "center"
>         valign  (top|middle|bottom|full)    "middle"
>         >
>
> </div>
>
> Is this possible somehow in DTD, or will I have to do it manually?
>
> (Also, while I\'m here, I don\'t think it was such a good idea to
> declare the `margin` and `padding` attributes that way. Does anyone
> know a better way?)

4.5h later, Daniel Haley answered (the answer is now the accepted
answer):

> Each element needs to have its own [attribute
> declaration](http://www.w3.org/TR/xml11/#attdecls) (`ATTLIST`).
> However, you can use a [parameter
> entity](http://www.w3.org/TR/xml11/#dt-PE) to reuse the bulk of it.
>
> <div>
>
>     <!ENTITY % attrs 
>         'width   CDATA   "0"
>          height  CDATA   "0"
>          margin  CDATA   "0 0 0 0"
>          padding CDATA   "0 0 0 0"
>          rotation CDATA  "0"
>          halign  (left|center|right|full)    "center"
>          valign  (top|middle|bottom|full)    "middle"'>
>
>     <!ELEMENT elem1 (#PCDATA)>
>     <!ATTLIST elem1 %attrs;<
>
>     <!ELEMENT elem2 (#PCDATA)>
>     <!ATTLIST elem2 %attrs;>
>
> </div>
>
> Here\'s another example that has a mix of the parameter entity
> references along with attributes that only appear on the individual
> elements.
>
> <div>
>
>     <!ELEMENT elem1 (#PCDATA)>
>     <!ATTLIST elem1 
>         attr1 CDATA #IMPLIED
>         %attrs;              >
>
>     <!ELEMENT elem2 (#PCDATA)>
>     <!ATTLIST elem2 
>         attr2 CDATA #IMPLIED
>         %attrs;              >
>
> </div>

However, making a minimal-example file
[`exampl.xml`](attlist-paramentities--attachments/exampl.xml) out of
these, we get the following results from `xmmlint`, Chromium, and
Firefox:

-   xmllint:
    <div>

        exampl.xml:12: parser error : ATTLIST: no name for Attribute
        <!ATTLIST elem1 %attrs;>
                        ^
        exampl.xml:12: parser error : internal error: xmlParseInternalSubset: error detected in Markup declaration

        <!ATTLIST elem1 %attrs;>
                               ^
        Entity: line 1: 
        width   CDATA   "0"
        ^
        exampl.xml:12: parser error : internal error: xmlParseInternalSubset: error detected in Markup declaration

        <!ATTLIST elem1 %attrs;>
                               ^
        exampl.xml:14: parser error : StartTag: invalid element name
        <!ELEMENT elem2 (#PCDATA)>
         ^
        exampl.xml:14: parser error : Extra content at the end of the document
        <!ELEMENT elem2 (#PCDATA)>
         ^

    </div>

-   Chromium:
    `error on line 12 at column 17: ATTLIST: no name for Attribute`
-   Firefox:
    <div>

        XML Parsing Error: illegal parameter entity reference
        Location: file:///path/exampl.xml
        Line Number 12, Column 17:

    </div>

So, can we really use that? Is that answer correct? What can we use that
method in? I guess not in much.

----

If you have any comments, please just email me.