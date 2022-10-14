---
layout: default
nav_exclude: true
---
# Recommender Moldel Thoughts

Notes about work done on August 8/9
th 2022. Researching some basic object recognition and possible datasets.

## Recommender model

- Define  3 undirected graphs 
- First graph: each item in a wardrobe represents a node.
    - Each item has an edge to all other items in the wardrobe. 
        - EXCEPT for all items in the same main category. No shoes have an edge to other shoes, or no tank tops to tshirts. 
        - Also EXCEPT for items that have no crossover between weather and occasion. Rainboots should not have an edge to  tank top. 
        - The weight of each edge represents the compatability between each item. Each item has a default weight and calibration/recommendation will constantly update the 
        - To generate an outfit we find combinations of items that have a high score between each other.
- Second graph: Each node represents a color that exists in users wardrobe
    - weight between each node are the compatability of colors
- Third graph: Each node represents a type of clothing that our app supports.
    - weight between nodes are the compatability of clothing types
- The first graph should be the primary basis for generating fits though the others should be accounted for and used to generate new fits with items that may have lower compatability score because they had been recommended many times in a improper color scheme or combination of types. 

## Scraper model
 - https://beckernick.github.io/faster-web-scraping-python/
    - Takes advantage of python features for even faster multithreading
    - Stupid quick downlaods
    - 986 images downloaded in 31 seconds
# Next steps
- Check for duplicate images
    - Probably images hashing
- Evaluate what needs to be done in processing outside of deciding if it is a good piece.

