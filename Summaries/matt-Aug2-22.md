# Further Scraper development and model disccusion

Notes about work done on August 2nd 2022. Base scraping function has been implemented. Thoughts on possible work for Griffin and Arka. 

## Scraper Work
- The scrape functions base implementation is there. I will probably add a few small features later. 
    - One of those will be handling for search terms that have a space "tank tops", because that makes some weird directory things
- Scrape looks through the links and downlaods the given number of inputted images to a directory named after the search term. 

## Arka and Griffin Possible Work:
Possible Avenues of work:

- Researching hosting images
    - Currently when a user adds a image it is added to a SQL table as a long string. We want to make the switch to images being hosted possibly through FireBase as we would be able to relate images to users FireBase tokens(I think)
        - Something that needs researching and experiments
    - Will add more soon
    
## Next steps

- Work on process function which will allow us to easily look and decide if we want to keep an image or not. Tagging with clothing type and color will be done here and metadata collected too. 
- Put scraper docs up
    - info on booting up searx on instance
    - and using the base functions of scraper