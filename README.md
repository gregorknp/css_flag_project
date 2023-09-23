# css_flag_project
How to create a flag using CSS

This project corresponds to the CSS Flag Project in the Intermediate CSS Section.

Given the following html file:

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Flag Project</title>
  <style>
    /* Write your CSS Code here */
    
  </style>
</head>

<!-- 
  IMPORTANT! Do not change any HTML
Don't add any classes/ids/elements 
Use what you know about combining selectors 
and CSS specificity instead.
Hint 1: The flag is 900px by 600px and the circle is 200px by 200px.
Hint 2: You can use CSS inspection to get the colors from
https://appbrewery.github.io/flag-of-laos/
-->

<body>
  <div class="flag">
    <p>The Flag</p>
    <div>
      <div>
        <p>of Laos</p>
      </div>
    </div>
  </div>
</body>

</html>
```

the goal is to create something like the following:

![](images/goal.png)

In order to do that, we are not allowed to modify any html elements. We can only add internal CSS rules inside the <style> tag. The idea is to combine selectors and play with the position property of the elements. My solution applies styling from top to bottom, starting with the div element tagged as flag and ending with the <p> element which contains the text "of Laos". So, let's get started!.

The div element tagged as flag is the container in which the rest of the elements are located and represents the whole flag. The width and the height are provided in the instructions of the exercise and the background color is taken using the css inspector on the url given. So this is how the element if styled:

```html
<style>
    .flag {
      position: relative;             /* This helps to position the first div tag */
      background-color: #ce1126;    /* Set the background color */
      width: 900px;                   /* width 900 pixels */
      height: 600px                   /* height of 600 pixels */
    }
</style>
```

![](images/div_flag.png)

So far not many changes. Next we will target the <p> element which contains the text "The Flag". This is the first child of the class flag element, so we can use the selectors combination .flag > p (Using this notation .flag is the parent and p is the direct child):

```html
<style>
    .flag {
      position: relative;             /* This helps to position the first div tag */
      background-color: #ce1126;    /* Set the background color */
      width: 900px;                   /* width 900 pixels */
      height: 600px                   /* height of 600 pixels */
    }
    .flag > p {                       /* With this selector combination we target the first <p> element of flag */
      position: relative;             /* Position relative to ancestor flag element */
      color: white;                 /* Text color white */
      text-align: center;             /* We align the text to the center of the flag */
      font-size: 75px;                /* Font size oif 75 pixels */
      margin-top: 0px;                /* needed to adjust the flag to the top of the browser after changing the font size */
    }
</style>
```
Playing with the font-size in the inspector, 75 pixels is what I believe is closer to the desired result. We will see that the text inside the white circle fits perfectly using a font size of 75 pixels as well. Note that I have set the margin-top property to 0. I don't know why but after changing the font-size property, a margin with the same amount of pixels is added both top and down the text:

![](images/flag_p_with_top_margin.png)

After setting the margin-top to 0 we get the following result:

![](images/flag_p_without_top_margin.png)

Next, we will target the center of the flag in blue. This is represented by the first <div> tag inside flag class. The background color has been taken from the URL given in the comments. This element has the same width and half the height of the flag element, that means 900 pixels and 300 pixels respectively.
NOTE: I'll change these fixed numbers and will use values relative to flag witdh and height so if these two change in the future, the size of the element will change accordingly. The position is set to absolute so it is relative to the position of the ancestor (Note that the flag element has the position property set) so to get it centered verticaly we have to push it 150 pixelse from the top. This way we have 150 pixels on the top + 300 pixels as the height of the element + 150 pixels on the bottom = 600 pixels:

```html
  <style>
    .flag {
      position: relative;             /* This helps to position the first div tag */
      background-color: #ce1126;    /* Set the background color */
      width: 900px;                   /* width 900 pixels */
      height: 600px                   /* height of 600 pixels */
    }
    .flag > p {                       /* With this selector combination we target the first <p> element of flag */
      position: relative;             /* Position relative to ancestor flag element */
      color: white;                 /* Text color white */
      text-align: center;             /* We align the text to the center of the flag */
      font-size: 75px;                /* Font size oif 75 pixels */
      margin-top: 0px;                /* needed to adjust the flag to the top of the browser after changing the font size */
    }
    .flag > div {                     /* This represents the center of the flag */
      background-color: #002868;    /* set the background color */
      position: absolute;             /* With absolute, the position of the element is relative to the ancestor regardless its default position */
      height: 300px;                  /* the height is half the height of the flag */
      width: 900px;                   /* the width is the same as the width of the flag */
      top: 150px;                     /* The flag gets centered verticaly, leaving the same above up and below */
    }
</style>
```

![](images/div_flag_div.png)












