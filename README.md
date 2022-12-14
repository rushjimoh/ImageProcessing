# Image Processing
## Project Overview
The project titled, "Enhancing Optical Character Recognition (OCR) Capabilities for Historical Documents", aims to understand the processes which degrade historical page scans and increase OCR error rates

In return, this will make the text from historical articles easier to index and catalog for future research

## SPIN Project [link spin page](http://spin.ncsa.illinois.edu/)
The reason why I am exploring this topic is to understand the differences between scanned pages and born digital documents for astrophysical literature. In other words, we to ask ourselves, "what makes an image look old?"

An [example](https://vtechworks.lib.vt.edu/handle/10919/100113) from previous work that highlights the task we are doing, shows the different transformations that can be conducted on an image using code to make a new image look old.

<img src="https://github.com/rushjimoh/ImageProcessing/blob/main/Screen%20Shot%202022-07-26%20at%206.58.14%20PM.png?raw=true" height="600">
Figure 1. Kahu, S. Y., Ingram, W. A., Fox, E. A., & Wu, J. (2021). ScanBank: A benchmark dataset for figure extraction from scanned electronic theses and dissertations. 2021 ACM/IEEE Joint Conference on Digital Libraries (JCDL). https://doi.org/10.1109/jcdl52503.2021.00030 

<img src="https://github.com/rushjimoh/ImageProcessing/blob/main/Screen%20Shot%202022-08-31%20at%2012.45.09%20PM.png?raw=true" height="600">
Figure 2. Kahu, S. Y., Ingram, W. A., Fox, E. A., & Wu, J. (2021). ScanBank: A benchmark dataset for figure extraction from scanned electronic theses and dissertations. 2021 ACM/IEEE Joint Conference on Digital Libraries (JCDL). https://doi.org/10.1109/jcdl52503.2021.00030


![image](https://user-images.githubusercontent.com/107584957/187746292-17411feb-9c4b-41f3-bc5e-a0030bc699e5.png)


## My work
We are starting to explore the scanned pages with image processing methods in Python and the examples below shows the beginning process into the world of image processing that can lead to more findings:
```
import cv2 as cv
image_pic = "gdrive/MyDrive/Figure Layout and Classification Independent Study/data/ScannedPages/1895ApJ_____1__212F_p1.jpeg"
img = cv.imread(image_pic)
plt.imshow(img)

blur = cv.blur(img,(25,25))

fig, ax = plt.subplots(1,2, figsize=(20,30))
ax[0].imshow(img)
ax[0].set_title("Original")

ax[1].imshow(blur)
ax[1].set_title("Blur")

plt.show()
```

![example blur image](https://github.com/rushjimoh/ImageProcessing/raw/main/blur.png)

The image above shows one of the methods that'll allow us to add blur to an image. Blur is being applied because this can occur during the scanning process of historical documents, especially since this was so long ago.

Another example is shown below of contrast being taken away from an image to mimic the way old, scanned images are viewed.

```
bright_pic ="gdrive/MyDrive/Figure Layout and Classification Independent Study/data/ScannedPages/1960ApJ___131__282B_p1.jpeg"
bright = cv.imread(bright_pic)
plt.imshow(bright)

cdf_m = np.ma.masked_equal(cdf,0)
cdf_m = (cdf_m - cdf_m.min())*255/(cdf_m.max()-cdf_m.min()) #this is an equation to calc. the histogram equalization equation
cdf = np.ma.filled(cdf_m,0).astype('uint8')

img = cv.imread(bright_pic,0)
equ = cv.equalizeHist(img)
res = np.hstack((img,equ)) #stacking images side-by-side
plt.imshow(res)
plt.imshow(res,cmap='gray')
```
![example saturation](https://github.com/rushjimoh/ImageProcessing/blob/main/satur.png?raw=true)


This [New.ipynb](https://github.com/rushjimoh/ImageProcessing/blob/main/New.ipynb) file shows how to identify a region of interest, and remove that from an image. The final result shows the original image, the image/region that was extracted, and the finished product. 

This is just the beginning of a still developing project, I will continue to further my knowledge and include more methods as time progresses.

The [Kahu et al. 2019](https://arxiv.org/abs/2106.15320) is the previous research on this topic, with the [reference code](https://github.com/SampannaKahu/ScanBank).
