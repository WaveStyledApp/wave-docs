# Scraper Development Notes

Notes about work done on August 4th 2022. Adding functionality for manual curation before we look into automating it

## Scraper work

The process function will open each downloaded image from the folder. Waits for a 0 or 1, 0's will delete the image from folder, ones will store metadata. Left click on the image will save the rgb so we can easily set colors.


## Thoughts on object detection

What if you had a model and you told it "I will give you 8 different objects, then gave it a bunch and let it figure out which are which based on the fact that there should be 8 different groupings" 

## Next Steps

Finish up process function, start looking into object detection.