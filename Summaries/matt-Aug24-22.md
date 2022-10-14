---
layout: default
nav_exclude: true
---
# Data Processing for object detection and scraper thoughts

Notes about work done on August 8/24
th 2022. Researching some object detection training processing and working on scraper

## Object Detection
- Objects for each image will need to be classified in a box. There are some programs out there for doing it manually: https://github.com/heartexlabs/labelImg
    - Output of labelImg can be formatted for use across popular object detection models
- If we decide to use this there will need to be 2 levels of data processing. Going through each to delete/keep them and then also classifying them.
## Scraper work
- Tested downloading 10k images of tshirt from SearX, run into a problem where SearX does not allow requests to be made from same IP for a while because it aggregates from other engines and one of the engines doesnt like the constant requesting. Might try proxies but easy fix would just be to add a times.sleep. it happens about once evert 10k links collected.
- From 10k links, 8.7K were successfully downloaded in 8 minutes(including link finding ~1.5 mins) and the folder size is 750mb

## Next Steps
- Test proxies with PIA: https://stackoverflow.com/questions/35144685/how-to-vpn-proxy-connect-in-python
- Once I can successfully get about 50k links at once, going to download that many and process ~1K of them. 

