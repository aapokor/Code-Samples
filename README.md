
Code Samples
============
This repository contains samples of code that I have authored. Please direct questions, comments, and concerns to me through [email](mailto:aapokorny27@gmail.com).
 As a young software developer, I often draw on my unique perspective as a pure math and computer science student
to make valuable connections between theory and application. I also enjoy being
versatile and flexible, and continued education and growth is really important
to me. I am motivated by learning new technologies and languages and growing as a programmer
and a developer. 

### Sample 1: [color_correction.py](color_correction.py)

This subpackage is part of a larger software suite, [PlantCV: Computer Vision Tools for Plant Phenotyping](https://github.com/danforthcenter/plantcv). The purpose of
 this subpackage presents a method for standardizing color spaces of images. The method is divided into six functions, each
  a step of the color space standardization process, to be flexibly implemented in a color correction pipeline, and one helper function
  that acts as a pre-build color correction pipeline for more immediate results. I have written documentation for the methods
  found [here](https://plantcv.readthedocs.io/en/latest/transform_correct_color/) and a tutorial for creating your own color correction
  pipelines [here](https://plantcv.readthedocs.io/en/latest/transform_color_correction_tutorial/). Testing I have written for 
  the package can be found within PlantCV's tests.py file found [here](https://github.com/danforthcenter/plantcv/blob/master/tests/tests.py).
  
  For more information regarding the color space standardization method, please refer to our publication: [An automated, high-throughput method for standardizing image color profiles to improve image-based plant phenotyping](https://peerj.com/articles/5727/).
  
  ####Citations
  
  * Berry JC, Fahlgren N, Pokorny AA, Bart RS, Veley KM. 2018. An automated, high-throughput method for standardizing image color profiles to improve image-based plant phenotyping. PeerJ 6:e5727. DOI: 10.7717/peerj.5727.
  
  * Fahlgren N, Feldman M, Gehan MA, Wilson MS, Shyu C, Bryant DW, Hill ST, McEntee CJ, Warnasooriya SN, Kumar I, Ficor T, Turnipseed S, Gilbert KB, Brutnell TP, Carrington JC, Mockler TC, Baxter I. (2015) A versatile phenotyping system and analytics platform reveals diverse temporal responses to water availability in Setaria. Molecular Plant 8: 1520-1535. http://doi.org/10.1016/j.molp.2015.06.005
 
 ### Sample 2: [sample_image_collection.py](sample_image_collection.py)
 
 This python script was designed to collect a random sample of images of the user's designation from the Danforth Center's
Bellewether Phenotyping Facility's image sets. Image sets can be tens or hundreds of thousands of images large, and viewing them 
in a remote file manager such as WinSCP can cause long loading times and software crashes. Often times, the process of collecting 
a sample of images to train a pipeline in PlantCV is a time consuming activity. This script can be run using a simple Bash command
 during an interactive session on the [Danforth's HTCondor computing cluster](https://bioinformatics.readthedocs.io/en/latest/) to collect a random sample of images efficiently,
  and store the sample with the same hierarchy as the population. This includes separate files for each instance of imaging,
   and a snapshot csv file that records the contents of the file.
   
### Sample 3: [the_Ring_of_Power.py](the_Ring_of_Power.py) 

This PlantCV processing pipeline is fondly named "Ring of Power" because it is the "one pipeline to rule them all." It provides image processing,
data extraction, and data loading into an SQLite database. It was designed to process a previously un-processable image set of approximately
200,000 images. Variation in color spaces, plant health, pot type, and carrier settings had made image processing too difficult
to process the images as a complete set. This pipeline processes the image set on the Danforth Center's HTCondor computing cluster in just about 24 hours using a 
DAG workflow.

It begins by using a Naive-Bayes classifier to segment a color corrected image of a plant. This produces a binary mask where black pixels represent background
 and white pixels represent plant. Then, it subtracts an appropriate background mask from the binary mask, breaking up predictable
 noise within the image. Further minor clean up functions are applied to the mask, and the mask is them reapplied to the original
 RGB image for segmentation. Once the image is segmented, data such as "height," "length,", and "Convex hull area" are extracted. 
 Color data is also extracted. This data is then stored into an SQLite database.
  
 For more information on High-Throughput Phenotyping, the Bellwether Phenotyping Facility, color space standardization, and this 
 pipeline, I am happy to provide my speaking slides from the 11th annual Symposium on Biomathematics, Ecology, Education, and Research.  
 
