> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.educba.com](https://www.educba.com/html-style-attribute/?source=leftnav)

> Guide to HTML Style Attribute. Here we discuss the list of all examples of HTML Style Attribute that ......

![](https://www.educba.com/academy/wp-content/uploads/2019/11/html-style-attribute.jpg)

Overview of HTML Style Attribute
--------------------------------

HTML code needs the style attribute for web pages to be rendered in web browsers like Chrome, FireFox, IE for them to be displayed as they are intended to look. [HTML tags](https://www.educba.com/basic-html-tags/) can contain various information, and the style attribute controls the appearance of information in [HTML blocks](https://www.educba.com/html-blocks/) using inline styling.

This article will be learning more about the HTML style attribute, which is nothing more than a set of rules that define how a page will be rendered in the web browser.

### List of HTML Style Attribute

Here’s a list of all the style properties that can be used to influence and control the design of HTML elements, accompanied by a practical example :

#### 1. Background-Color

With this [CSS property](https://www.educba.com/what-is-css/) we can set the background color for any HTML element like <div>, <h1> etc.

**Example**

`<div style=”background-color:blue”>My background is blue</div>`

**Output:**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-1.png)

#### 2. Color

The font color of the text in an HTML element can be controlled by setting its color attribute to the [right color name](https://www.educba.com/color-name-in-html/) or HEX code or RGB code.

**Example**

`<div style=”color:blue”>My font color is blue</div>`

**Output:**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-2.png)

#### 3. Border Color

We can set the border color of any HTML element if we’d like to add a border to it.

**Example**

`<p style=”border: 1px solid red”>My border is red</p>`

**Output:**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-3.png)

As you see in the code above, border property accepts 3 properties in the following order: “Border-width border-style border-color”.

#### 4. Background-Image

We can also set an image as a background by using the background-image property as follows:

**Example:**

`<div style=”background-image: url(‘[https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png](https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png)’);height :365px”>`

**Output:**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-4.png)

#### 5. Background-Repeat

As you see in the above example, when an image is set as background using the background-image property, it by default repeats the image both horizontally as well as vertically. However, some images may need to be repeated either vertically or horizontally, or they may not be needed to be repeated. This behavior can be controlled by setting the desired value against the property of background-repeat, and it can be only used when background-image is being used; else, it won’t add any styling value when used as a standalone property.

The value “repeat-x” is used to allow the image to be repeated only horizontally.

The value “repeat-y” is used to allow the image to be repeated only vertically.

The value “no-repeat” is used to stop any kind of repetition of the background image.

Let us modify the above example to improve the background image.

**Example** 

`<div style=”background-image: url(‘[https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png](https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png)’);height :365px; background-repeat:no-repeat”>`

**Output:**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-5.png)

We can compare the examples above and understand that with a background image, we can add an image as the background and with a background repeat, we can control the repetition of the background image.

#### 6. Background-Position

With this property, we can define the position of the background image.

**Example**

`<div>  
</div>`

**Output:**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-6.png)

#### 7. Margins

CSS provides us with properties to set margins on all four sides of an HTML element, or we could add margins to a particular side of the element.

With margin-top can add a margin to the top of the element, margin-right will add a margin to the right of the element, margin-left will add a margin to the left of the element, and margin-bottom will add a margin to the bottom of the element. Instead of using these 4 properties, we can also use the margin property and set its values as per our requirement.

**Example**

`p {  
margin-top: 25px;  
margin-bottom: 75px;  
margin-right: 50px;  
margin-left: 100px;  
}  
or  
p  
{  
margin: 25px 50px 75px 100px;  
}`

#### 8. Padding

The padding property defines the space between the content of an element and its borders. We can use the “padding” property or individual padding properties like padding-top, padding-bottom, padding-left, padding-right to set the padding for top, bottom, left or right of the content of an element.

`p {  
padding-top: 25px;  
padding -bottom: 75px;  
padding -right: 50px;  
padding -left: 100px;  
}  
or  
p  
{  
padding: 25px 50px 75px 100px;  
}`

#### 9. Height and Width

Height and width are the most basic CSS properties used to define the height and width of any HTML element. They can be either set to a pixel value like 200px or a percentage like 10%, 20%, etc.

#### 10. Text-Align

This property is used to set the horizontal direction in which we’d like to align the text of an element. The value can be set to center, right or left.

`p {  
text-align: center;  
}  
or  
p {  
text-align: left;  
}  
or  
p {  
text-align: right;  
}`

#### 11. Text-Decoration

[Text decoration](https://www.educba.com/text-decoration-css/) property can be used to set decorations like underline, line-through or overline over text in HTML.

**Example:**

`<p style=”text-decoration:underline”>This is underline</p>`

**Output:**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-7.png)

#### 12. Letter-Spacing

As the name suggests, this property is used to define the spacing between letters/characters in a word. It can be assigned a positive or negative pixel value to increase or decrease the spacing between letters.

**Example:**

`<p style=”letter-spacing:-3px”>My words are overlapped</p>`

**Output:**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-8.png)

#### 13. Line-Height

Line height defines the distance between vertical lines. Like letter spacing, line height too can be set to a positive or negative pixel value. Let’s review the example below to understand better:

#### Example:

`<p>This paragraph has a small line-height.<br>This paragraph has a small line-height.<br>  
</p>`

**Output:**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-9.png)

#### 14. Text Direction

Sometimes, if the web page’s content is not in English but some other language like Arabic, which follows a right to the left convention, we would need to change the direction of the text. In such cases, we can reverse text direction.

**Example:**

`<p><bdo dir="ltr">I am right to left</bdo></p>`

**Output:**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-10.png)

#### 15. Text Shadow

This property adds a shadow to the text.

**Example:**

`<p> I’ve got a gray shadow</p>`

**Output:**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-11.png)

#### 16. Font Family

We can define the font class for text in an element. We can define multiple font families separated by a comma as a fallback system to handle scenarios where a preferred font class cannot be loaded.

*   **Font style:** With font-style property, we can add italic or oblique effect to the text.

**Example:**

`<p>This is oblique style.</p>`

**Output:**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-12.png)

*   **Font weight:** This property defines the weight of a font.

**Example:**

`<p style=”font-weight: 900”> This is a bold paragraph</p>`

**Output :**

![](https://www.educba.com/academy/wp-content/uploads/2019/10/html-style-attribute-13.png)

The styling attributes showcased above our building blocks with UI and UX designing. They continue to evolve as new versions of CSS are introduced.

### Recommended Articles

This is a guide to HTML Style Attribute. Here we discuss the list of all the style properties that can be used to influence and control the design of HTML elements with the help of practical examples. You may also have a look at the following articles to learn more –

1.  [HTML Fonts Styles](https://www.educba.com/html-fonts-styles/)
2.  [HTML List Styles](https://www.educba.com/html-list-styles/)
3.  [Basic HTML Tags](https://www.educba.com/basic-html-tags/)
4.  [Advantages of HTML](https://www.educba.com/advantages-of-html/)