# Learning CSS

## Tech With Tim - CSS For Non-Web Developers - Tutorial - Part 1

[Link to video](https://www.youtube.com/watch?v=ZzoAu4VPyho)

### Intro

### Environment Setup

Make a directory
- open a new powershell
- cd ..
- mkdir css
- open a new VSCode > File > Open folder... > css

Create the HTML and CSS files
- open a new powershell
- echo > tutorial.html
    - press enter after so that the file stays empty
- echo > styles.css

Download 'Live Server'
- Ctrl-Shift-X (Extensions) > Live Server > Install

Notes: 
- What does Live Server do:
- You don't need to manually refresh (hitting save will automatically update)

Start off a basic HTML document (using VSCode snippets)
- open tutorial.html
- html:5
- save w/ ctrl-s

Run Live Server
- Bottom Right of VSCode > Go Live
    - This will open up your HTML document in google chrome under port 5500

Note: You should drag this chrome tab with your html document to the right so that you can see what you are developing as your work
- leftmost tab: vscode
    - 1 tab for notes
    - 1 tab for html file
    - 1 tab for css file
        - achieve this by dragging the .html file to the right, so that they can be side-by-side

- rightmost tab: google chrome

[Example](./figures/0.png)

Make your first change
- add this code to the file on line 6

    ``` html
    <!-- Old -->
    <title>Document</title>

    <!-- New -->
    <title>Tutorial 1</title>
    ```

Commit to github
- open [github](github.com) > your repositories > new > create repository
    - name: css
    - description: leave blank
    - public
    - do not init with README/.gitignore/license

- create a new repository on the command line

    ``` 
    git init
    git add .
    git commit -m "first commit"
    git branch -M main
    git remote add origin https://github.com/MylesThomas/css.git
    git push -u origin main
    ```

Check that your changes were reflected online 
- https://github.com/MylesThomas/css

### CSS Styles

inline styling: not recommended!

Example: 

``` html
<p style="color: aqua; background-color: blue">hello world</p>
```

Good for testing things out 


Styling tag in HTML

Example: 

``` html
<style>
    p {
        color: blue;
    }
</style>
```

Still not preferred...

Best Method: External Style sheet!

Example of linking the style sheet:

``` html
<title>Tutorial 1</title>
<link rel="stylesheet" href="styles.css" />
```

``` css
p {
    color: blue;
}
```

### CSS Selectors

Selector: Way of targeting specific elements

Methods
1. id: unique id that you will add to an element

    ``` html
    <body>
        <p id="p-tag">hello world</p>
        <p>hello world</p>
        <p>hello world</p>
    </body>
    ```

    ``` css
    #p-tag {
        color: pink;
    }
    ```

    - you are not supposed to have the same id on multiple tags...
    - good if you are not re-using styles

2. 

3. class: 

    ``` html
    <body>
        <p id="p-tag">hello world</p>
        <p class="p-tag">hello world</p>
        <p>hello world</p>
    </body>
    ```

    ``` css
    .p-tag {
        color: pink;
    }
    ```

    - you ARE supposed to repeat these
    - good if you are re-using styles

Note:
- many other ways to select, they are too advanced to even need to learn right now

How to select elements inside of another element:
- let's take a div with 3 p tags inside of it
- the following will select all p tags inside of `section1`:

    ``` html
    <div class="section1">
        <div class="section2">
            <p>hello world from section 2</p>
        </div>
        <p>hello world in div class="section1"</p>
        <p>hello world in div class="section1"</p>
        <p>hello world in div class="section1"</p>
    </div>
    ```

    ``` css
        /* Class for a div, then all p tags inside of that div */
    .section1 p {
        color: green;
        font-size: x-small;
    }

    .section1 .section2 p {
        color: purple;
        font-size: larger;
    }
    ```

- you can continue nesting if you'd like, as I did here with the section 2...

- How to grab all of thep tags inside of divs, inside of section1:

    ``` css
    .section1 div p {
        color: red;
    }
    ```


### Colors and Backgrounds

Color:
- popular: built in strings
- can also do rgb/hex
    - rgba: 4th argument has transparency
        - 0: invisible
        - 1: solid/regular

``` css
section1 div p {
    color: rgba(200, 150, 0, 0.2);  /*0.2: almost invisible*/
    font-size: larger;
}
```

Background Color:
- same thing
- fills up entire width of the object, even past the words

### Block vs. Inline

Default property: Display
- default: set to `block`
    - line break after this object
    - next object in DOM will go on next line

- `inline`: Only takes up enough space equal to the content of the paragraph tag
    - no line break
    - spaced out with default spacing/padding

    ``` css
    p {
        display: inline;
    }
    ```

- `inline-block`: He doesn't use this much... not going to get into it
    - has something to do with setting up the width/height

- `none`: Makes the item invisible
    - will you ever need this...?


### Widths and Heights

First, setup a basic example:

``` html
<div class="one">
    <p>hello world from class="one"</p>
</div>
<div class="two">
    <p>hello world from class="two"</p>
</div>
```

``` css
body {
    background-color: aquamarine;
}

.one {
    background-color: antiquewhite;
}

.two {
    background-color: greenyellow;
}
```

Many ways to set width and height!
- flexbox: does it for you

Questions to ask:
- What is the height and width of our body?

Tips:
- set background colors on everything (helps you see how much space they are taking up)


Body: Illusion is that it takes up the entire screen, but that is not true
- it is still inside of the html tag
    - html also does not take up the entire screen....

Try this out: Set the background color for html and body and you will see how they don't actually take up as much space now

``` css
html {
    background-color: black;
}

body {
    background-color: aquamarine;
}
```

Changing the height of the body
- static: 
    - pixels: 100px

- relative:
    - percentage: 100%
        - only works if you have a parent

- dynamic: height of viewport
    - vertical height: 100vh

- relative to default font size:
    - 1rem
    - 10rem

- relative to nearest parent:
    - 1em

How to get the background color for html tag and body tag  
- if you do not set the height of html to be 100%, the body will be 100% of nothing (it will only have the content you have put on the screen, no actual background color)

``` css
html {
    background-color: black;
    height: 100%;
}

body {
    background-color: aquamarine;
    height: 100%;
}
```

Changing the width of the body
- Default: Takes up 100% of screen width

``` css
html {
    width: 100%;
}

body {
    width: 50%;
}
```

Question: What is the default black margin around the body?
- default: margin at top is 5%

This will ensure that your body takes up more space:

``` css
body {
    margin: 0%;
}
```

Tech with Tim Recommendation: Typically uses %'s



### Box Model

Box Model: Fundamental Aspect of CSS
- what different properties do to change the layout of your DOM

Content
- padding
- border
- margin

Tags = Containers that are holding content!

padding: spaces the content out from the edge of the box

``` css
.one {
    padding: 25px 25px 5px 5px;
}
```

Notes:
- padding vertical is NOT same as padding horizontal

border: starts at the edge of the box
- takes up the padding

``` css
.one {
    border: 5px solid orange;
}
```

margin: separation between the object and other objects
- 

``` css
.one {
    margin: 5px 10px 5px 10px;
}
```

Takeaway Notes:
- margin: outside of box
- padding: space between outside of box and interior content
- 

### Flex Box

Flex Box: Powerful way to design HTML pages
- a lot of people get confused w/ flexbox
- tech with tim: says it is intuitive and good for responsive screen sizes
    - his preference

Starting with Flexbox: Add this to 1 container

``` css
body {
    display: flex;
}
```

Next: 
- default: main axis aligned in 1 row

Putting content in the center:

``` css
body {
    display: flex;
    justify-content: center;
}
```

Other options instead of center:
- flex-start
- flex-end
- space-between
- space-around


Making it vertical instead of horizontal:

``` css
body {
    display: flex;
    justify-content: center;
    flex-direction: column;
}
```

Aligning items
- align-items: similar to justify-content

``` css
body {
    display: flex;
    justify-content: center;
    align-items: center;

    height: 100vh;
    width: 0px;
}
```

Gap: sets a specific gap between the objects you have
- replacement for margin (better than doing it individually)
- remove margins to see that there is a default of no gap

``` css
body {
    display: flex;
    justify-content: center;
    align-items: center;

    gap: 10px;

    height: 100vh;
    width: 0px;
}
```

Example: We want object 1 to take up double the space of objects 2 and 3

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tutorial 1</title>
    <link rel="stylesheet" href="styles.css" />
</head>
<body>
    <div class="one">
        <p>hello world from class="one"</p>
    </div>
    <div class="two">
        <p>hello world from class="two"</p>
    </div>
    <div class="three">
        <p>hello world from class="three"</p>
    </div>
</body>
</html>
```

``` css
.one {
    flex: 2;
}

.two {
    flex: 1;
}

.three {
    flex: 1;
}
```

"I want this object to take up 2 flex spaces"


Few more attributes:

- 

### Positioning and Z-Index

Positioning: Can be confusing
- default: static
- absolute: based on parent
- sticky: 
- 

Absolute: 

``` css
#p {
    position: absolute;
    top: 0px;
    bottom: 10px;
}
```