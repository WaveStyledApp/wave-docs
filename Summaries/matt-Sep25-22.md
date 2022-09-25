# Continution of Model exploration

Notes about work done on Sep 19 22. Picking up from where I left off on the graph code.

## VIM Command Notes

$ used to skip to end of line
O  in normal mode used to enter a new line

## Finding the second,third... item in a wardrobe

Once we have atleast one piece, we must take them into consideration when choosing the next item. We start by randomly selecting the next type of clothing. Since we are taking an item of a different type than what has already been selected, we are guaranteed to have an edge from all of our selected items to all items in that type.

We can take the average of the selected items weights to the items in the next type and randomly select from the top 10-20% of the avg wegiths. 

## Implementing this

Through naive methods getting the weighted average of items isnt too complicated. My method could be cleaned up by abstracting some more things. But it is a good start. It has yet to actually be tested. Thats what the next step is..
