# Taking flexbox to the next level

## Part 1: flex-direction, flex-wrap, and flex-flow

### Flex-direction

We've already seen flex-direction but there is more to it!

- row - the parent is a row, the direct children become columns
- row-reverese - same as a row, but the order of the columns is reversed
- column - the parent is a column, the direct children become rows
- column-reverse - same as column, but the order of the rows is reversed
- 
### flex-wrap

By default, flex-wrap is set to nowrap. This means that if the children can't fit inside the parent at their natural size, they'll be squeezed down until they reach their minimum possible size. If they all still can't fit, they'll overflow out the side of the parent.

We can change this behavior by declaring flex-wrap: wrap. When we do this, the direct children will keep their sizing, and instead wrap down if there isn't enough room.

## Justify-content and align-items and their relationship to flex-direction

We've already seen all three of these properties, but I think it's important to go back over them as we dive deeper into flexbox, because they are so important to understanding flexbox.

### justify-content
This property deals with how the flex items are distributed along the main axis.

The values
- space-between
- space-around
- space-evenly
- center
- flex-start (default)
- flex-end

### align-items
This deals with how the items are positioned along the cross axis.

The values
- flex-start
- flex-end
- center
- stretch (default)
- baseline
<hr>
## Part 2: justify-content and align-items and their relationship to flex-direction

We've already seen all three of these properties, but I think it's important to go back over them as we dive deeper into flexbox, because they are so important to understanding flexbox.

### justify-content
This property deals with how the flex items are distributed along the <strong>main axis (left to right).</strong>

  The values:
  - space-between
  - space-around
  - space-evenly
  - center
  - flex-start (default)
  - flex-end

### align-items
This deals with how the items are positioned along the <strong>cross axis.</strong>
It only works in two circumstances.

The flex-container has a height: ;

  The values:
  - flex-start
  - flex-end
  - center
  - stretch (default)
  - baseline
<hr>
## Part 3: Exploring align-content

Flexbox gives us the align-content property, but it isn't used nearly as much as our:
<br><strong>align-items or justify-content.</strong>

### align-content - cross axis
align-content works very similarly to justify-content, but on the <strong>cross axis.</strong> <br>The reason we don't see it used as much though, is because it only does anything when we have <strong>multiple rows</strong> of content within the flex container, which isn't the most common situation.

  - align-content
    - works on the cross axis
    - ONLY works when you have multiple rows of content
  - justify-content
    - works on the main axis

<strong>REMEMBER</strong> Most of the times its a combination of <strong>justify-content & align-items</strong> and only on odd occasions that we need to use <strong>align-content!</strong>
<hr>
## Part 4. flex-grow and flex-shrink explained

### flex-grow
The flex-grow property deals with how a flex item grows within the flex container. The default is 0, which means that it will not grow at all. If we change this to 1, that flex item will fill up all available space.

### flex-shrink
The flex-shrink property deals with how a flex item will shrink smaller than it's ideal size (it's width, or if there is no width, it's content). By default, it is set to 1.

### They are ratios
Because all flex items have a default of shrink of 1, they all will shrink at the same rate. If we put a larger number on an individual item, it will shrink at a faster rate (and if we put 0 it will not shrink at all).

The same applies for flex-grow. When we set a grow on one item, it will grow to fill the available space, but if two items have the same flex-grow, they will grow at an equal rate and distribute the space between them.

If one item has a larger grow, it will grow at a faster rate than the others.
<hr>
## Part 5. flex-basis - works on the main axis of the flex container

<strong>flex-basis</strong> is one of those properties that people just don't really understand, so they don't use it. For the most part, that's fine too, but because of how it works, there are certain situations where it's the ideal solution!

### How flex-basis works
Flex basis will default to auto, which will look for the width of the element it has been declared on. If there is no width, it will instead go to the size of the content inside that element.

But it doesn't actually focus on the width, it focuses on the main-axis of the flex container.

So, if an element has flex-basis: 500px, while that element's parent has a flex-direction: row, <strong>left to right</strong> it will set the width of that element to 500px. But, if the parent has a flex-direction: column, <strong>up & down</strong> which changes the main axis, it will now set the height to 500px!

This might seem a little strange (because it is), and you might be wondering where it's useful. We'll see a good use case of this very soon!

- flex-basis: auto; is default and it looks for the width and if there is no width it will default to the item size that is inside the item (container).

min-width and max-height limits the flex-basis and looks in these  min-width and max-height.
<hr>
## Part 6. The flex shorthand property

The flex property combines flex-grow, flex-shrink, and flex-basis into a single shorthand property. If you put three values, it will be in the order of grow, shrink, basis.

So the two following code blocks are equivilant:

    {
        flex-grow: 1;
        flex-shrink: 2;
        flex-basis: 600px;
        }

    {
        flex: 1 2 600px;
        }

If we only put a single value, if it is unitless, it will use it for flex-grow, but it will also set the flex-basis to 0. If it has a unit, it will use it for flex-basis.
<hr>

## Part 7. Aligning individual elements with align-self

When we use align-items on the flex container, it affects all of the flex items inside of it. Sometimes we only want to change how one of the flex items is behaving though, and for that, we have align-self.

It can use all of the same values that align-items does, but only affect the alignment of that single element.
<hr>

## Part 8. Margin auto and flexbox

There are two big differences with how margins work inside a flex container:

-   margins no longer collapse
-   setting auto to the margin top and bottom will center an item vertically instead of simply setting it to 0
 <hr>
