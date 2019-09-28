# Taking flexbox to the next level

## Video 1: flex-direction, flex-wrap, and flex-flow

### flex-direction

We've already seen flex-direction but there is more to it!

- row - the parent is a row, the direct children become columns
- row-reverese - same as a row, but the order of the columns is reversed
- column - the parent is a column, the direct children become rows
- column-reverse - same as column, but the order of the rows is reversed
- 
### flex-wrap

By default, flex-wrap is set to nowrap. This means that if the children can't fit inside the parent at their natural size, they'll be squeezed down until they reach their minimum possible size. If they all still can't fit, they'll overflow out the side of the parent.

We can change this behavior by declaring flex-wrap: wrap. When we do this, the direct children will keep their sizing, and instead wrap down if there isn't enough room.

## 
