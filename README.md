# Undergraduate-Research

The goal of my undergraduate research project was to devise a method to cluster hand-written words of historical documents to speed up the process of transcription. The assumption was that in a text there aren't many unique words, thus the clustering would reduce the work load.

## Proposed Method

As my files were scan of documents without any structure (images), it was required to develop some techniques to extract the words from the images. Only then it was possible to do a feature extraction to perform the clustering. The next subsections explains these two stages.

### Image Processing

The image processing workflow was:

1. Obtain the images from the [National Library](http://bndigital.bn.br/). A sample can be seen [here](https://github.com/lucasschmidtc/Undergraduate-Research/blob/master/imageProcessing/0-letter.jpg).
2. [Segment the ink from the rest of the image](https://github.com/lucasschmidtc/Undergraduate-Research/blob/master/imageProcessing/2-inkSegmentation.png) by applying the [Otsu Method](https://en.wikipedia.org/wiki/Otsu%27s_method).
3. [Detection/Bound Boxing of the words](https://github.com/lucasschmidtc/Undergraduate-Research/blob/master/imageProcessing/3-boundBoxing.png).

### Feature Extraction and Clustering

From the step of words (rectangles of images) outputted by the previous process, the feature extraction and clustering workflow was:

1. [From each word extract 3 time series](https://github.com/lucasschmidtc/Undergraduate-Research/blob/master/featureClustering/timeSeries.png): one to the bottom and upper silhouette of the word, and a final one that counts the amount of transition from black to white ink (per column of pixels). The use of time series is justified by the observation that one writtes from left to right, thus the pixels have a weak time relation.
2. From the time series of each word compute its dissimilarity to every other word by using the [Dynamic Time Warping](https://en.wikipedia.org/wiki/Dynamic_time_warping) technique.
3. Apply a Hierarchical clustering algorithm to obtain the dendogram. The [poster](https://github.com/lucasschmidtc/Undergraduate-Research/blob/master/poster-wordContour-siicusp-PT_BR.pdf) contains an image that illustrates this whole process.

## Results

This project was my course final paper ([monograph](https://github.com/lucasschmidtc/Undergraduate-Research/blob/master/monograph-wordContour-PT_BR.pdf) in Portuguese) and was presented as a poster at the 20th SIICUSP Symposium.
