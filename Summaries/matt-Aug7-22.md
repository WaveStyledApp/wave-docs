---
layout: default
nav_exclude: true
---
# Object Detection and Dataset research + MNIST is a bust

Notes about work done on August 7th 2022. Researching some basic object recognition and possible datasets.

## MNIST is a bust
- Whole image is being considered, model doesnt know what it is looking for just picks up on patterns across whole image. When there are various backgrounds within an image it will not work
- Good brush up on ML and using photos

## Object Detection/Recognition
- This is the way to go.  Use something pretrained like YOLO model and have a good dataset. 

## Dataset research

- I've been looking into DeepFashion and V2, along with smoe of the other large scale datasets. They also do not account for a great diversity of types of clothing. Most are not meant for something we are trying to do. 
    - They are good. But the big problem is that the ones we could use are non-commerical purposes. 
    - I'm starting to think that curating our own dataset and possibly releasing it might be a good way to get our names out there. It could take a little while to have one we are happy with the size of, but it could be very useful. Also more clothing types.
- I've optimized the search engine so that results from the scraper tend to fit better with search term. Very similary quality to google images

# Random Thought About Recommender System

Just thinking about a possible route of recommending without relying on a ML model. 
Every item in a wardrobe has a compatability level with every other.
Each item is a node with an edge to every other item, the weight of that edge is compatability.
To generate outfits we compute Highest paths of compatability. Calibration identifies some initial relationships and as the recommender is used further the weights change as well. Other graphs could be used to track compatability of  combinations of clothing and combinations of colors.
# Next steps
- Looking into larger scale image curation with the scraper.
    - Threading
    - Throwing it on server
    - Error handling
    - Refine process() and make it independent so donwloads can be happending and process is happening
    - Curate list of search terms
        - I'm thinking for each clothing type we do something like
       
        `tshirt`
        
        `walmart tshirt`

        `[insert other brands] tshirt`
        
    - Curate say 1K "tshirt" images and try object detection
    - Once an okay sized dataset, see how good model is at classification with unseen scraped data


