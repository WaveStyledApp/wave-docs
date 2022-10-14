---
layout: default
nav_exclude: true
---
# Sitdown Summary - July 31st 2022 - Sanjay

Notes on ideas and exploration done on technologies we are considering.

## Server Hosting

- Main goal for this iteration of development is to put the backend on a deployable server that ensures safe and secure connections from multiple users

- Deviate from using LAN-based networks -- should be able to access the app on cellular data or any stable WiFi anywhere

- Side Quest
  
  - **EC2** : played around with it locally (I know you also did Matt)
    
    - was able to ssh into my instance using the form 
      
      - ``ssh i <path to private key> ec2-uer@<public DNS ipv4 name>``
    
    - from there, installed github using ``sudo yum install git``
    
    - and I was able to clone the repo and run wave-server
      
      - Socket issues came up, and we can fix those shortly by changing the IP address
  
  - Going to be taking a mini AWS course to acquaint myself with the technologies so I'm better fit at diagnosing plan of actions and possible issues, *but* this is solid progress as it is clearly possible to run our server on the AWS bucket while using version control on the terminal

- Want to look into other technologies than AWS
  
  - Cloud based web application hosting services 
  
  - Some that I found...
    
    - [Digital Ocean](https://www.digitalocean.com/go/developer-brand?utm_campaign=amer_brand_kw_en_cpc&utm_adgroup=digitalocean_exact_exact&_keyword=digitalocean&_device=c&_adposition=&utm_content=conversion&utm_medium=cpc&utm_source=google&gclid=Cj0KCQjw0JiXBhCFARIsAOSAKqDOtD2IPt7m54owFZ3ZD3TO-NHSHMvBXT6iaR4gwJMNdgJ8vk8L0B4aAnt1EALw_wcB)
      
      - costs money to enter, but a free account gives solid credit
      
      - similar to AWS after some research but could suffice our needs with maybe better UI and such

- Ultimately, we just want a place that infinitely runs our backend (while supporting Git updates) and allows machines from anywhere to access the server and DB from anywehere

## Model

- Images are the new means with which we will be traning and processing our clothing data

- Images naturally implies Conv2D layers in a convolutional neural network

- Will use the images from scraping algorithm from Matt, and we can preprocess them using openCV libraries and numPy to vectorize them, transform them to widen our input data size and scope. We want to rotate and flip images so the model understands location and key features of items its idenfying

- Questions to think about
  
  - are we training on clothing item recognition? (for the add form) or arw we training on outfit implication like user favorability or whether an item can be used in the future
  
  - for the add form, definitely will need a clothing recognition model to expedite the process (like a resume filler form)
    
    - key points: efficiency. we want the model to be faster than a human filling out the add form
      
      - faster than 10-15 seconds
    
    - Tensorflow Hub 
      
      - [Fashion MNIST database](https://github.com/zalandoresearch/fashion-mnist) 
        
        - most commonly used in recognition task and traning for ML models
      
      - [TensorFlow Hub-clothing model](https://tfhub.dev/google/experts/bit/r50x1/in21k/clothing/1)
        
        - a Model I found that uses a subset of the ImageNet dataset for clothing items
      
      - [TensorFlow Hub](https://tfhub.dev/s?module-type=image-feature-vector)
        
        - feature vector models -> could be useful since we want to take an image and extract feature vectors from it to directly use in the add form
  
  ## Next Steps
  
  Look into more AWS stuff with Matt, and also try these models out and see if any of them provide a good fit for us. Maybe using a prebuilt model that clearly works on a task can help us transfer it over to our task. 
  
   *but first, we need to discuss what exactly we are trying to do with the model and such, which can give clarity on what we want the inputs and outputs to do*
  
  
