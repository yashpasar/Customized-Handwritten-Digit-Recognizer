# Customized-Handwritten-Digit-Recognizer
Handwritten Digit Recognition using OpenCV, sklearn and Python

You can apply a simple OCR on your own handrwitten digits using this python script.
I have used OpenCV to pre-process the image and to extract the digits from the picture.
Using SVM as my model, I trained it using my own handwritten images. 

## Dependencies
1. `cv2`
2. `sklearn`
3. `skimage`
4. `numpy`
5. `collections`

## Analysis  
After searching and reading about feature extraction from images for OCR - I stumbled [HOG](https://en.wikipedia.org/wiki/Histogram_of_oriented_gradients) (Histogram of Gradients).  Basically, it tries to capture the shape of structures in the region by capturing information about gradients. Image gradient are simply intensity changes across pixels in an image.  

![pic-explain](https://gilscvblog.files.wordpress.com/2013/08/figure5.jpg "pic")


It works by dividing the image into small (usually 8x8 pixels) cells and blocks of 4x4 cells. Each cell has a fixed number of gradient orientation bins. Each pixel in the cell votes for a gradient orientation bin with a vote proportional to the gradient magnitude at that pixel or simple put, the "histogram" counts how many pixels have an edge with a specific orientation.  More more info please refer [this](https://gilscvblog.wordpress.com/2013/08/18/a-short-introduction-to-descriptors/) blog post

Using just only HOG histogram vectors as features drastically improved the accuracy of the prediction.  Currently, I have used KNN from OpenCV as my model - I tried using SVM from the same module, but its accuracy was not as good as KNN. The best accuracy I have achieved on a sample image of about 100 digits is 80%.  In the future, I might add more features after looking into SIFT, SURF or even try to get a better accuracy using just plain pixels as data

### Note:  
- User image should be a scanned (atleast 300dpi) image.  
- Image can be any format supported by OpenCV.  

## Results

### Sample Image 1
![Result Number 1](https://github.com/yashpasar/Customized-Handwritten-Digit-Recognizer/blob/master/photo_1.jpg)

### Sample Image 2
![Result Number 2](http://hanzratech.in/figures/digit-reco-2.png)

