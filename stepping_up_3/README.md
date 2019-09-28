In this module:

    Line-height
    Text-transform
    Letter-spacing

    Viewport units
    background images
    gradients
    Transitions
    Blending modes

    Form
    Input
    Button
    Styling them all up!

CONTROLLING OUR BACKGROUND IMAGES

REMEMBER: If it has text on top it is a background image and not just an image!

We've seen background-image, and how it creates repeating patterns that tile when the image is smaller than the space it fits.

We can do a lot to control our background images though!

background-position
    Numerical values
        A single value will move it that much on both the x and y axis
        If you include 2 values, the first will be on the x-axis, the second on the y-axis
    Keywords
        We can also assign keywords, such as: 
            top left, bottom center, center right, etc. 
        This can be useful to control the 
        position of the image when using background-size: cover.

background-size
    Numerical values
    When giving it numerical values, we can control the exact size of our image.

Keywords
    - auto      is the default, nothing will change
    - contain   ensures that the entire image is visible. It might seem strange, but it can be used for something like a 
                logo that's set as a background image, along with no-repeat
    - cover     will ensure that the image covers the entire space without repeating, but it will result in the image 
                being cropped

background-repeat
    We can prevent our image from repeating, either at all, or having it only repeat along a single axis.

Values
    repeat      - the default
    no-repeat   - the image will not repeat at all
    repeat-x    - it will only repeat on the x-axis
    repeat-y    - it will only repeat on the y-axis


EXAMPLE:

.background-mage {
    padding:  100px;
    background-image: url(images/email-pattern.png);
    background-position: center;
    background-size: cover;
}

####
Step 1 in creating the BBQ_spalsh_page

BBQ splash markup:


<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="/stepping_up_3/BBQ_spalsh_page/css/styles.css">

    <title>BBQ Splash</title>
</head>

<body>
        <div class="intro">
            <h1></h1>
            <p></p>
            <p class="top-text"></p>
        </div>
        
        <div class="main-content">
            <h2></h2>
            <p></p>
            <p></p>
            <!--TODO form will go here -->
            <p class="fine-print"></p>
        </div>
    </body>
</html>

###
Step 2 - Set the typography in the css file!

Always start the css file with:

* {
    box-sizing: border-box;
}

body {
    margin: 0;
}

I always recommend starting to write CSS with the typography first. If you start with the layout (as people love to do), 
and then you start changing fonts and font-sizes, everything shifts around. That means going back into the layout and making more changes.

Also, because of how I set up the markup in this video, we get the opportunity to see combinators.

The + combinator
    This combinator will add a style if a selector is an adjacent sibling. So in this example, we see:
        h1 + p. 
    That means those styles will only apply to paragraphs that are directly after an h1.

        h1 + p {
            color: #F18119;
            font-weight: 900;
            font-size: 1.3125rem;
        }

The ~ combinator
    This is the general sibling combinator. It will grab any selector that is a sibling to the first. 
    So if we write:
        h1 ~ p 
    it will select all paragraphs that are siblings to the h1.

        h1 ~ p {
            color: #F18119;
            font-weight: 900;
            font-size: 1.3125rem;
        }   

More information on combinators
    MDN article looking at them all
    A YouTube video of mine where I explore them
###

Step 3 - Adding the background image

It's always a good idea to also add a background-color, even though when you have a background-image you can't see it.

It creates a fallback, just in case something happens (like in this, where the recording doesn't load in the image 
for about 20 seconds, and we can't read the text until it updates!)
###

Step 4 - Changing the order of apperance

Remember, to change the order of something, it first has to be a flex item.

If you try to apply the order property to something which isn't a direct child of a flex container, then it will have no effect.

Step 1:     display: flex; & flex-direction: column;

    .intro {
        background-image: url(images/dark-ribs.jpg);
        background-color: #404040;
        padding: 0 .25em 1em;
        display: flex;
        flex-direction: column;
    }

Step 2:     order: -1

    .top-text {
        font-size: 0.625rem;
        color: #F18119;
        font-weight: 900;
        text-transform: uppercase;
        order: -1;
    }
###

Step 5 - Styling the main content apperance

Step 6 - Adding the media query

When adding in a media query, you might be given an exact size to use by the designer or design team, but if not, 
try not to base it off popular break points or specific devices. Add in a media query when the layout dictates 
that you need one (usually it revolves around paragraph's line-length getting too long).

Focus on when your design needs a breakpoint.. not the mobilesizes!

Find the size that looks good when making the screen bigger..
###

step 7 - Set things up for larger screens

A look at fixing our background-image, as well as creating a 2-column layout at larger screen sizes.
###

VIEWPORT UNITS 

Viewport units are interesting, but sometimes take a little getting used to.

    vh - viewport height        height: 75vh;
    vw - viewport width         width: 50vw; (or 50%)
    vmin - either the viewport height or width, whichever is smaller    height: 25vmin;
    vmax - either the viewport height or width, whichever is bigger     height: 25vmax;

header {
    background: lightblue;
    padding: 1em;
    height: 25vmax;
}

###

Step 8 - adding viewports units

It's easy to add, but we do run into a small issue with it as well.

When setting viewport units, especially for a height, I strongly suggest setting it as a min-height. It'll help avoid problems when the content is taller than the viewport.

Fixing viewports with border-box

As we've seen with the box model, CSS calculates the size of an element based on it's content + padding + border + margin.
When we set a width, we are setting that width on the content of the element, and then all the other properties get added to create the total size.

We can change that behavior by declaring box-sizing: border-box;
(star selector * - affects everything on the page)

* {
    box-sizing: border-box;
}

border-box includes: content + padding + border + margin!!

This will change how the size of an element is calculated, now including both padding and border, inside the width (or height) that we set.
We often declare this on the * selector, which will select every element on the page. By doing this, it makes it much easier to work.
###

USING FLEXBOX TO VERTICALLY CENTER THE MAIN CONTENT 

Remember, when we use flexbox, 
    justify-content is on the main axis, 
and 
    align-items works on the cross axis. 

When we use flex-direction: column, the main axis switches, meaning that justify-content starts to work vertically instead of horizontally!
###

FIXING THE INTRO SECTION ON BOTH SMALL AND LARGE SCREEENS 

Another good use case for justify-content!

.intro {
    background-image: url(/stepping_up_3/BBQ_spalsh_page/img/ribs.jpg);
    background-size: cover;
    background-color: #404040;
    background-position: center;
    padding: 0 .5em 2em;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    min-height: 50vh;
}

###

DEALING WITH VERY LARGE SCREENS SOLUTION #1 

When using compound selectors, we know that something like

    .intro p    

is a decendant selector. It will select all paragraphs that are a decendant of

    .intro.

Sometimes we only want to select items that are the direct child of something though, and not *all the decendants. 
We can do this by using the > combinator.

By using it like this

    .intro > p 

it will only select paragraphs if they are a direct child of .intro, but not if they are nested inside of something else. 
This can be very useful from time to time!

    .intro > *,
    .main-content > * {
        max-width: 400px;
        margin-left: auto;
        margin-right: auto;
    }

###

DEALING WITH VERY LARGE SCREENS SOLUTION #2

1)  add a container class to the intro and main-content sections
2)  add a container-intro class to deal with the spacing and everything we had before.
3)  move the: 
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        min-height: 50vh;
    from the .intro class to the .container-intro class
4)  add 
            .container-intro {
            /* 100% is matching the height of the parent (.intro height 100vh) */
            height: 100%;
        }
    to the media query.

###

FORMS

First, we must create our form using the <form> element. When we hit the submit button on a form, 
it will submit anything that is inside that single <form> element.

We use <input>s for many different things, using the type="" attribute to declare the type of input that the element is.

Some examples include:

        text
        email
        password
        file
        date
        color
Learn more about forms
If you'd like to learn more about forms, the MDN 
[https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms] 
has a lot of documentation on them and is always a good place to start.

Take a look at the two form files unser forms for more info on setting forms up and styling them!
###

GRADIANTS

Interestingly, gradients in CSS are set as a background-image.

Instead of giving the background-image a url(), we instead give it a value of either:

    linear-gradient() a gradient that goes in a specific direction
    radial-gradient() a circular shaped gradient, starting in the middle and expanding out

We can simply give a gradent a list of colors: 
    
    linear-gradient(red, yellow, orange, blue);

And if we want, we can give it a direction, either through keywords or degrees:

    linear-gradient(to bottom right, red, yellow, orange, blue);
    linear-gradient(45deg, red, yellow, orange, blue);
###
BLENDING IMAGES, COLORS AND GRADIENTS WITH BACKGROUND-BELND-model

background-blend-mode is a super fun CSS property that we can use to blend a background-image with a background-color, 
or even two background-images!

If you want to use more than one image, or an image with a gradient, they all have to be put on a single background-image 
property, and comma separated.

Here is a great article if you're interested in learning more about blending modes in general.

[https://www.slrlounge.com/workshop/the-ultimate-visual-guide-to-understanding-blend-modes/]
