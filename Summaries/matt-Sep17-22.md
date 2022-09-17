# LabelImg Software and scraper setup on alternate computer

Notes about the work done on Sept 17 2022. Looking into Label Image Software for curating images. I have decided to put the proxy issues to the side as I do not think it is crucial at the momment.  

## Label Img

https://github.com/heartexlabs/labelImg

lets us create boxes around objects in an image that we want to label

## Scraper debugging

Found that there is usually a significant amount of duplicate links after doing the initial scan. To limit dupes I convert the list of links to a set then back to a list to eradicate duplicate links. This fix seems to have gotten rid of almost all duplicates. Do not think further duplicate checking is required. Still about 15% of links are broken when the downloading begins. 

## Base Processing

Moving the Image processor to its own file, as its quite a separate process. It will just be used to skim through photos and remove the ones that cannot be used as training data. Also added abililty to cleanup file names after we have gone through initial processing.

Tested on 100+ images, took just over a min to do 100 or so.



# Next steps

Use the image labeler to curate some data and the start exploring building the model. Adding some links here for future reference: https://towardsdatascience.com/how-to-label-images-for-object-detection-step-by-step-7ee317f98583
