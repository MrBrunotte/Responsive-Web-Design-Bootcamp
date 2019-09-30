# CSS Grid

## Pt 1 - Setting up a basic grid

We can define a grid, on the parent, by declaring: <br> <br> - grid-template-rows <br> and <br> - grid-template-columns.

To set the widths for your columns (or heights for your rows), all we need to do is place as many values as needed, separated by a space:

- grid-template-columns: 100px 500px 100px;

### grid-template shorthand
If we are declaring both rows and columns, we can use the grid-template shorthand. <br> The values here start with the rows, then then we use a / to start declaring columns:

- grid-template: 100px 100px 500px / 300px 300px 100px;

### How to declare the grid

   On the parent element we declare: display: grid; <br>This creates a new grid formatting context. Margins no longer collapse and the <strong>direct children of the element become grid items.</strong>

## Pt 2 - Placing items on the grid

On a grid item (the direct child of a grid container), we can use the following properties to place our item on the grid we have created:

    - grid-column-start
    - grid-column-end
    - grid-row-start
    - grid-row-end

For all of those values, we assign them line numbers, which correspond to the lines in our grid.

### A grid of 3x3

    .grid {
        display: grid;
        grid-template: 50px 50px 50px / 100px 100px 100px;
    }

I can place the .grid-item2 like this:

    .grid-item2 {
        background: rgb(164, 233, 35);
        color: black;
        padding: 1em 2em;
        border: 2px solid grey;
        display: flex;
        align-items: center;
        justify-content: center;
    
        grid-row-start: 2;
        grid-row-end: 4;
        grid-column-start: 2;
        grid-column-end: 4;
    }
###

## grid-row and grid-column shorthands

To help shorten things, we can use the grid-row and grid-column shorthands.

When using the shorthand, the first value is the start, the second value is the end, and they must be separated by a /

- grid-row: 1 / 3

Also, we can use negative numbers for our grid numbers. If you use a negative number, it still start counting from the far side and move backward through your lines.

### Grid shorthand

    .example {
        grid-row: start / end;
        grid-column: start / end;
    }

When you want it to stretch across the whole grid container it is convenient to use negative number:

    grid-column: 1 / -1;
    grid-row: 2 / - 2;

## Part 4 - Spanning columns

When using grid-rows or grid-columns, sometimes it's hard to keep track of the line number that you want something to go to.

One solution is using span. So instead of specifying an end line, we can say from the line you're starting on, span across X columns or X rows.

Example: grid-column: 2 / span 3

We can also omit the starting line number like so: grid-column: span 3 in which case it will start in whatever cell it is naturally in, and span across the next three.

## Part 5 - Some similarities to flexbox

Grid shares a lot in common with flexbox, such as:

    - collapsing margins
    - align-items
    - justify-content
Also, items stretch by defaut.

But unlike flexbox, grid items also stretch horizontally as well as vertically.

Because of how grid works, we also have a new property: justify-items which we can use to justify individual 
items within their cells, as well as justify-self that we can use on individual grid items.

## Part 8 - The grid-gap property

A look at how we can create empty spaces between our grids using

    - grid-row-gap
    - grid-column-gap
    - grid-gap

    grid-column-gap: 2em;
    grid-row-gap: 5em;

    grid-gap: 0 2em;


<strong>Remember: It doesnt add a gap to the outside only inside! </strong>

## Part 10 - The implicit and explicit grid

A look at what happens if we place an item on grid lines that we haven't explicity created 
(hint: the browser will implicity create them for us!)

When we delare <strong>display: grid;</strong> on an element, all the grid items are automatically
placed inside of a row, <strong>even if we haven't created any yet!</strong>

### Explicit rows and columns

    grid-template-rows: 50px 100px 200px;
    grid-template-columns: 200px; 

When we set up grid-template-columns and grid-template-rows, we are <strong>explicitly</strong>
stating how big they musy be.

### Implicit rows and columns

Sometimes, columns and rows are created automatically.
These are <strong>implicit</strong> rows and columns.

But how big are these implicit rows and columns??

They'll default to auto (the width and height of the content).

If we want, we can state how big we want them to by by using:

    - grid-auto-rows
    - grid-auto-columns

## Part 11 - Exploring grid areas

We can name our cells too!

By using grid-template-areas we no longer have to rely on line numbers.

It does take a bit more time to set them up, but often it more than pays off once media queries start factoring in.

    grid-template-areas: "header header header"
                         "sidebar content content";
                    
<strong> There is NO comma between the ""</strong> and it is written like above!

### Assigning a grid item to a grid area

    .main-content {
        grid-area: content;
    }


## Part 12 - grid-areas and media queries

This is where the real payoff of setting up grid-template-columns comes into play!

By adding a . in the css file we mean that is should be ignored.


## Part 13 - minmax()

A new property that is simply amazing.

Because we use it to set the size of our columns and rows, it allows us to set a minimum and maximum size in one place. It's almost like magic.

## Part 14 - The "fr" unit

The fr unit distributes a fraction of the leftover space, causing cells that use this unit to act a lot like a flex item that 
has a grow on it that isn't 0.


## Part 15 - minmax() and the fr unit

Using 1fr as the maximum size inside of minmax() is very useful, but because of how the fr unit is calculated, it isn't accepted as a minimum size!


# Portfolio

## auto-fit and auto-fill

auto-fit and auto-fill both work inside of repeat(), replacing the number of times we want something to be repeatd.

Both of them work best when combined with a minmax(), especially when that max value uses the fr unit.

auto-fit will fit the columns you’ve defined into the available space.
auto-fill will keep adding in new columns, even if they are empty.
