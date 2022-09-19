# Graph Exporation

Notes about work completed on Sep 18. Built a basic Graph ADT

## Random Notes

Change "Typical" to "General" in weather. I dont like the sound of typical. 

## Graph ADT Layout

Just did a basic 3 class Graph Structure. Node is a class, edge is a class, graph itself is a graph. 

- Graph

Represnts an entire wardrobe. List of nodes and list of edges.

- Node

Represents a clothing item in wardrobe, identified by its PK(pieceid), a node also stores relevant info about the piece(color,type,oc/we's)

- Edge

Represents the compatibility between different pieces of the wardrobe. Stores the start and end node as well as the weight

## Graph Basic Capabilities

- Add edge and add node functions

Creates new object and adds it to list with required info

- getNode

returns node queried by the pieceid

- edgeExists

Return T/F based on whether there is already an edge between 2 nodes

## Generating Edges

A clothing item should have an edge to every other clothing item unless they are of the same type and they should have at least 1 compatible weather and occasion. 

GenerateEdges runs in O(V^2) with an O(E) for every inside the nested loop, double loops through the vectors to create the edges.

## Loading Wardrobe

Loaded CSV into the graph with pandas and iterrows(). The entire process of loading and creating edges happens very quickly.

## Next steps 

- Simulate random edge generation

This was easy. For now keeping ratings between 0 and 1 in steps of hundreths(0.01-1.00)

- Start thinking about the algorithm


Where does it start generating from? Do we randomly select a first piece that has a high enough piece? Or do we start with strictly one type, like shoes first(only item common across all types). Could possibly implement both of these.


Before considering what the first piece is, we need to consider how many pieces we want based on our given weather. We are going to need some sort of templates that represent clothing types for the weather. 


## Templates

Cold, Hot, Rainy, Snowy, Typical/General/Better Word

Cold - Shoes, Pants, Shirt(?), Overtop, Hat(?) 

Hot - Shoes, Shorts, Tee, Hat(?)

Rainy - Shoes, Pants, Shorts(?), Shirt(?), Jacket(?), Overtop(?), Hat(?)

Snowy - Shoes, Pants, Overtop, Shirt(?), Jacket, Hat(?)

General - Shoes, Pants(?), Shorts(?), Shirt(?), Overtop(?), Hat(?)

First thing I notice here is that all weather types will always have shoes, might have a hat and will/might have a shirt 

- Possible 30% chance across the board to add hat to a template. 
- An interesting way to expand this would be to add the ability for the generation to occur based on what the user tends to like (Shirts more than overtops on a general day) or wears hats more often than 30% of the time. 

Cold:

	Pants
	Overtop (75%)
	Overtop + Shirt (25%)
	Shoes
	Hat(30%)


Hot:

	Shorts
	Shoes
	Tee
	Hat(30%)

Rainy:

	Shoes
	Shorts/Pants(depending on hot or cold, will figure this out) 
	Shirt/Overtop Weather dependent too
	Hat(30%)
	Jacket(50%) or maybe weather dependent


Snowy:

	Shoes
	Pants
	Overtop
	Jacket
	Hat(30%)


General:

	Shoes
	Shirt/Overtop (25/75)
	Pants/Shorts (50/50)
	Hat(30)


Might make use of the old generation algo for this, and alter it as needed.
