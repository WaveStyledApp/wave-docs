---
layout: default
nav_exclude: true
---
# Graph Discussion

Notes about work done on Sep 19 and some responses to questions that will help outline the recommenders continued dev.

## Weight Adjustments

In terms of adjusting weights, I currently am thinking of it like this:
- Edges have same initial weight when they are first generated
- Calibration/Choosing:
       - Liking an outfit will increase the weight of all edges involved in the outfit, it will also(to a significantly lesser amount) increase the weight of all edges that are connected to the nodes in the outfit(giving the item an overall higher rating to all other pieces). Same process for disliking. 


## Too many Edges - Maybe only using edges from an item to other clothing types

if it was just edges from an item to other  would you then not only be learning about a particular items compatibility with another group of clothing (like a white hoodie pairs well with any jacket type). I dont think that would be useful enough information to learn properly about a users preferences. There aren't any edges from a shoe to another shoe and 2 items must have at least 1 occasion and 1 weather in common for an edge to be generated. The edge generation is damn near instantaneous and we are using a pretty minimalist ADT. 

Keeping track of how a single items relationship with particular clothing types could be helpful, especially in template generation.


## Max path, ensuring we are not getting same outfits

Instead of always taking the highest weight in a max path, it should probably be randomly selected from a range of the weights(like the top x items from the seleceted initial clothing type) 

## Where I am stuck

Say you start with a shoe and then choose a tee with a high weight between them. Then the third item should be chosen with respect to the shoes edges and the tee's edges. Cannot get my head around this part yet. 

# Other Work Done

## Reconfiguring generateTemplates

Had to change it a bit more from the old version we used in Alpha. It can definitely be refactored further and adjusted more, but good for now. It returns the indices that have been chosen instead of bit array.

## Item selection

Going to loop through the type we need to select. Randomly select which piece to start with. Another function will choose the item from the pool of the same type and based on the weight. 

None of this is set in stone. Still exploring. 

