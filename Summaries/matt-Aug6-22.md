---
layout: default
nav_exclude: true
---
# MNIST fashion dataset exploration

Notes about work done on August 5th/6th 2022. Exploring the MNIST dataset and building an implementation of it.

## Scraper Notes
- At this point the scraper is useful to curating clothing to test on the model and judge how useful a model trained with MNIST.

## MNIST dataset
- MINST dataset has labels:
    
    `class_names = ['T-shirt/top', 'Trouser', 'Pullover', 'Dress', 'Coat',
               'Sandal', 'Shirt', 'Sneaker', 'Bag', 'Ankle boot']`
    
- TensorFlow has a good guide of building the model and training it with the MNIST fashion dataset
    - https://github.com/tensorflow/docs/blob/master/site/en/tutorials/keras/classification.ipynb
- Followed this implementation of training the model, then built a function to process scraped images from the web to see if the images carried over
    - Processing scraped images:
        - Training data is all 28x28 so scaled images down
        - Greyscaled images. Could also try playing with no grayscale
        - Training data has a primarily black background while a lot of the scraped images had white background so I inverted the images greyscale.
-  Results: 
    - From only a few tests the model yielded quite accurate results. Sometimes a tee-shirt was labeled as a tee, but this might be the best way to implement the type of clothing detection

## Next Steps
- Test the model thoroghly on more scraped images(maybe even on my own wardrobe)
- Start considering how we will detect colors
    - https://github.com/codebrainz/color-names/blob/master/output/colors.csv
    - https://data-flair.training/blogs/project-in-python-colour-detection/



