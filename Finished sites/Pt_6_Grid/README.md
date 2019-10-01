# Analyzing the layouts

We first set up the page in Adobe Xd.

Here is the link [https://xd.adobe.com/spec/f255d364-6d5e-4aaf-7703-6f8d0a398281-8464/grid/]

## Markup -The HTML for the homepage

1) I start to set up my HTML page.

   - Set up the correct html page with DOCTYPE html
   - Links to css and fonts
   - Title

2) I then set up all my elements (with classes) on the page in the body section.

## CSS - The first lines of CSS I should always write

3) I always start my css file with these settings:

The border box includes all the padding and margin when i set a width or height to an element, if i dont do this i need to calculate the width and height with padding an margin!

" * {box-sizing: border-box;} "

In the body I put all these styles I want to use everywhere.

    body {
        margin: 0;
        font-family: 'Montserrat', sans-serif;
        font-size: 1rem;        /* 1rem = 16 px (default) */
        color: #404040;      /* the color of for the paragraphs*/
        line-height: 1.6;       /* Its easier to read */
    }

    img {
        max-width: 100%;
        display: block;
    }

Its also good to state the exact font-weight.

    h1, h2, strong {
        font-weight: 700;
    }

### I start with the Typography

4) Set up the typography for the other classes and set the typography heading in the css file so everything is ordered nicely.

## Setting up the grid for small screens

### Hero area

5) Next i set up the grid for small screens

Because grid lets us have much flatter markup than we previously had, I often find myself using a solution like this to 
create a "container" on my page, without having on in my markup.

The basic setup is to give your grid grid-template-columns: 

    .hero { grid-template-columns: minmax(1em, 1fr) minmax(0px, 500px) minmax(1em, 1fr); }

The minmax(1em, 1fr) on the left and the right gives us the spacing around our page, and then we can do whatever we want in 
the middle, whether it's one big column like we setup in this video, or breaking that up into multiple columns like we'll do later on for big screens.

### info section

Breaking the display: grid and the grid-template-columns off to it's own class makes it very easy to reuse the class 
wherever we need it instead of having to declare the same thing over and over again.

We put it in a .main-grid class

    /* ==================
    general layout
===================== */

    .main-grid {
        display: grid;
        grid-template-columns: minmax(1em, 1fr) minmax(0px, 500px) minmax(1em, 1fr);
    }

We also add the .main-grid class to the markup in the HTML file.

## Setting up the footer

I put this in the general layout since the footer will be everywhere.


## Setting up the grid, and hero, for larger screens

Remember, we want to use the same grid throughout our entire site to stay consistent. 
We've already seen that the layout is effectively a 3-column grid, with some items spanning more than one column.


## Navigation - using flexbox and not grid

### Setting up our navigation for small screens with positioning

There are a number of position values that we can assign to an element.

    - position: static - the default
    - position: relative - allows us to use the top, bottom, left, and right properties. It will be positioned relative to it's natural place on the page.
    - position: fixed - it is removed from the flow of the document and placed in a fixed position within the viewport. This means it will scroll with the page, alway staying in view.
    - position: absolute - it is removed from the flow of the document, but does no flow with the page.
    - position: sticky - a new property that works much like fixed, but it will scroll with the page until it reaches a certain point, where it will then "stick".
  
Further reading on positioning
This MDN article [https://developer.mozilla.org/en-US/docs/Web/CSS/position] goes into detail on the subject

## Making the close button

When using "button"s, when they are used outside of forms and we're using JavaScript to make them work, 
it's important to give them an aria-label attribute. Think of it like the alt for the button where we describe what the button is there to do.

## Creating the "open" state and adding JavaScript to close our navigation

JavaScript is a totally different beast from CSS. It's the next stage if you haven't got there yet, but if it seem confusing in this one, 
please don't worry about it. We're here for CSS for now, this will just give you a little taste of some of the possiblities that JS opens up.

## Adding the open button to our navigation

Very similar to our close button, but with a few different styles on it.

note: if you see a "hi" popup a couple of times, I'd run a test script when I ran into a problem with the JS 
(I forgot to change the "open-nav" class). I didn't include it in the recording, and it's not in the script file if you look, 
but it seems like Scrimba keeps running it when the page reloads anyway :)

## 18 - Styling the navigation for large screens

Navigations sure do take a lot to set up properly!

note: I also mispoke in this video. I mentioned that intial sets it back to the original value that was on that property. 
It's a little more complicated than that. For example, if you set display: initial on any element, it will set it to inline, 
even if it's a block element by default. It doesn't look at the element, but simply goes to that properties default value, 
regardless of what element it is on.

## Fixing up the navigation and hero area

In this video I first use positioning to get the navigation to overlap the hero area. That results in us needing more padding, 
which results in the background-image almost being perfectly placed. So, a little tweaking after that and we're good to go onto the next page!

## Styling the about page

Fixing the layout and typography of the About page. Overall everything is pretty straight forward on this page, 
but I do use a nice trick with the :first-child pseudo-class to fix a spacing issue with the titles.

## Exploring box-shadows to get the effect on our images

Box shadows are fun to play with.

The box-shadow property accepts 6 values, though a few of them are optional.

The 5 main values
These must be in this order:

    1 horizontal offset (positive to the right, negative to the left)
    2 vertical offset (positive moves down, negative moves up)
    3 blur
    4 spread
    5 color
The blur and spread are optional.

<strong>inset shadows</strong>
You can also use the inset keyword to move the shadow to the inside of a box. 
This must be the first value given: 

    - box-shadow: inset 10px 10px 20px 0px rgba(0,0,0,.35);

A common setting for a nice subtle box shadow:

    .shadow {
        box-shadow: 0px 0px 25px rgba(0,0,0, .3);
    }

## Using pseudo-elements to add the yellow lines

Pseudo-elements are similar to pseudo-classes, in that they don't live in the markup.

A pseudo-element, however, gets added to the DOM (the HTML that the browser renders, versus what we write). 
They are inserted inside the selector we chose, but either right before or after the content of that element.

To get a pseudo-element to render takes a bit more work than selecting it though. 
We also have to declare the content: '' even if there is no content inside it, or it will never render. 
We also then either have to declare a display or a position.

In this video we scratch the surface of how they work. If you'd like a deeper dive, 
I have pa three-part series on YouTube [https://www.youtube.com/playlist?list=PL4-IK0AVhVjPBX_HelwDlNsTiyr2YGSBw] that explores them much more.

## Styling the contact form for larger screens

A new little grid feature makes an appearance: grid-auto-flow: dense. Using this is useful if you have empty cells because of 
how the content is flowing, and you want to make sure everything is tightly packed in and filling in those empty cells.
