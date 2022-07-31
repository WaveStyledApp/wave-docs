# Sitdown Summary - July 31st 2022 - Matt

Notes about work down on July 31st 2022. Base code fot the image scraper. 

## Image Scraper
- Making it as a class so that it can be easily used by other systems. 

- Main planned methods:
    - search() for given # of images of a term, it will collect all the links and 
    - download() will download the links and store them in a folder named after the search term.
    - process() will simlpy store base information about each image into either a SQL table or csv file. Info will include dimension, size of file, and a hash to ensure no duplicates exists
    - curate() will act like displayFit functions from earlier in project, and will make it an easy process for us to get rid of images that do not fit what we are looking for, and to tag each image with color. 
    - will be some helper functions as well.
- Currently working on search(). URL's needed to be properly parse because they are getting loaded as "http%F%F.." instead of proper slashes. 
    - urllib has a functin that should fix it

## Model Ideas
- Just putting message I sent to Sanjay here today about a different perspective for the model.
    - So I had a thought, I’m not sure if it would even change how we are approaching our model. It might just be a different perspective to think about.  But we have been looking trying to determine whether a user will like the outfits we generate. A recommendation model. What if we thought about it more like: we are trying to predict what the user is going to wear next, something, more along the lines of something sequential. I have no clue whether that would look differently than what we have already been thinking about. Just a different possibility for us to consider. 