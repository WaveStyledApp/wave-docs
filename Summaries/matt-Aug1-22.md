# Further Scraper development and model disccusion

Notes about work done on August 1st 2022. Additional work done on the scraper and comments/discussion based on Sanjay's model notes from July 30

## Model Discussion
We are looking to eventually have 2 models
- First the model for analyzing the trends of user and trying to predict what they will wear next/ what they would like to wear. The recommednation element.
    - I imagine only to possible outputs types for this model.
        - Similar to our original mode, a classification in range of (0,1) depending on whether the model believes that our user will like this. But I do not see a way of doing this without relying on the randomness of clothing generation that we initially used.
        - Secondly, an output of particular clothing items from the users wardrobe that the model thinks the user will want to wear. 
            - Similar to what we were thinking about when we initially built the first model, but we couldnt figure out how to build in with the given time. 
            - Inputs??: Images, occasion and weather type, possible adding the rating value back in for clothing items? 
            - Sequential? Predict one item at a time and feed that forward to predict next item?
            - Objective funciton is trying to maximize for how much a user will like an outfit. 
                - Rating value? All items have the same initial rating? Calibration will increase/decrease across the items that we see. Calibration without any inital data about the users preferences??
- Second model is related to the add form. It will be a model that(if high enough acc) should only ever be trained once. When a user adds a new item, it gets uploaded to server and predict() is called on the model. 
    - Input to this model is the image 
    - Output are a clothing type tag and possibly color?
        - Would we possibly need 2 models if we wanted to do color prediction alongside it?
    - Uploading and predicting on a decent AWS server should be damm near instantaneous.

## Scraper Code
- Not as much progress as i hoped today. 
- Search function is completed. It collects a given number of images with a particular search term. 
- Added some comments, will start documenting after a little more progress


## Next Steps
- In terms of the add models development I think a good starting point(while scraper is still in development). Would be to implement:
    - [Fashion MNIST database](https://github.com/zalandoresearch/fashion-mnist) 
    So we at least have an idea about item recognition will help gain experience for doing it with our own dataset. 
- In terms of recommender, we just need to keep discussing and researching. 
- Scrape function will start tomorrow. Possibly with some multithreading for downloading multiple images at once. Fin
- Figure out what Arka and Griffin can look into/work on.