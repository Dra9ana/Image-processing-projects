# Image Processing Projects Overview
# Project 2
## Exercise 1: Image Filtering Exercise

### Overview
The primary objective is to enhance image quality by suppressing unwanted frequency components while preserving important details. Exercise includes finding appropriate filter to apply to solve this problem.

#### Libraries Used
- `numpy`: For numerical operations.
- `matplotlib`: For plotting images and results.
- `skimage`: For image processing.
- `ipywidgets`: For interactive plotting.

### Procedure
1. **Reading the Image**
   - The input image is read and converted to a floating-point format using `skimage`.

2. **Fourier Transform**
   - The Fourier transform of the image is computed to analyze its frequency components.

3. **Applying Filters**
   - A Gaussian low-pass filter is applied to suppress high-frequency noise.
   - Notch filters are utilized to specifically target and reject unwanted frequency components.

4. **Filter Parameter Testing**
   - Various standard deviations are tested for the Gaussian filter to find an optimal balance between noise reduction and detail preservation.

5. **Results Visualization**
   - Results for different filter configurations are visualized, showcasing the effectiveness of the filtering process.

### Results
The exercise resulted in several filtered images, each demonstrating the impact of different standard deviations and filter types. Key findings include:
- **Standard Deviation Testing**: The standard deviation of 65 was found to provide the best results, balancing noise reduction and edge preservation.
- **Comparison of Filter Types**: The Gaussian notch filter effectively removed sinusoidal components while preserving image details compared to ideal and Butterworth notch filters.

### Conclusion
This exercise successfully demonstrates the application of low-pass and notch filtering techniques in image processing, highlighting the importance of filter selection and parameter tuning for optimal image enhancement.

---

## Exercise 2: Image Restoration Exercise

### Overview
This project focuses on restoring degraded images using advanced filtering techniques, specifically Wiener filtering and band-pass sharpening. The primary goal is to enhance the visual quality of images affected by blurring and noise, making them more legible and suitable for further analysis.

### Objectives
- Implement Gaussian low-pass filtering to estimate the degradation function of images.
- Apply Wiener filtering to restore images while minimizing the mean square error.
- Enhance the restored images using band-pass sharpening and contrast adjustment techniques.
- Evaluate the effectiveness of different filtering methods in preserving image quality.

### Methodology

#### 1. Gaussian Low-Pass Filtering
- Developed a Gaussian mask to model the degradation of the image.
- The standard deviations for the x and y axes were estimated based on the characteristics of the image spectrum.

#### 2. Wiener Filtering
- Implemented a Wiener filter to minimize the mean square error during the restoration process.
- Utilized the estimated degradation function to adjust the image in the frequency domain.
- Ensured the restored image was clipped to maintain pixel value ranges.

#### 3. Band-Pass Sharpening and Contrast Enhancement
- Applied a band-pass filter to enhance specific frequencies in the image.
- Implemented a gamma transformation to improve the contrast of the restored image, making text and details more prominent.

### Results
The final output images demonstrated significant improvements in clarity and legibility, particularly for textual content. The implemented methods effectively reduced noise and enhanced essential features of the images while also addressing artifacts introduced during restoration.

### Conclusion
The project successfully demonstrated the application of various image restoration techniques. The results indicate that a combination of Wiener filtering and band-pass sharpening can significantly enhance degraded images, making them suitable for further analysis.

### Technologies Used
- Python
- NumPy
- SciPy
- Matplotlib
- Scikit-image

---

## Exercise 3: Adaptive Median Filter Implementation

### Overview
This exercise focuses on implementing an adaptive median filter for image processing, which aims to effectively remove impulsive noise while preserving the details of an image.
The adaptive median filter dynamically adjusts the size of the filtering window based on the characteristics of the image surrounding each pixel.

### Objectives
- Develop an adaptive median filter that balances noise reduction and detail preservation.
- Implement a data structure (heap) to efficiently compute the median, minimum, and maximum values in real-time.
- Apply the filter to an image to evaluate its performance and effectiveness in reducing noise.

### Methodology
The adaptive median filter operates by:

1. **Dynamic Window Sizing**: For each pixel, the smallest window size is determined that effectively removes noise without overly compromising image details. If the median value is an extreme (minimum or maximum), the window size increases until a suitable median is found or the maximum allowed size is reached.

2. **Heap Data Structure**: A combination of two heaps is utilized:
   - A max heap to store the lower half of the data.
   - A min heap to store the upper half of the data.
   This approach allows for efficient calculation of the median as new pixels are added to the heaps.

3. **Window Expansion**: When an extreme median value is encountered, the window size increases by adding new pixels while reusing previously computed values to minimize computational overhead.
### Results
Upon applying the adaptive median filter, the output image demonstrates a significant reduction in impulsive noise while retaining critical details. The effectiveness of the filter is evident in comparison to the original noisy image.

### Conclusion
The adaptive median filter successfully balances the trade-off between noise removal and detail preservation in images. The use of heaps for real-time median computation enhances the efficiency of the filtering process, making it suitable for practical applications in image processing.
# Project 3
## Exercise 1: Dice Score Extraction

### Project Description
This project involves developing an image processing function to extract and sum the scores displayed on dice images, specifically differentiating between blue and red dots. The function `extract_dice_score` takes an image of dice as input and returns two numbers representing the sum of scores for blue and red dots, respectively. The segmentation and identification of the dots are achieved using color thresholding in the HSV color space and morphological operations.

### Goals
- Implement a function to accurately extract scores from images of dice.
- Utilize image preprocessing techniques, including color segmentation and morphological operations, to improve the accuracy of dot detection.
- Create visualizations to illustrate the image processing steps and results.

### Achievements
- Successfully implemented the `extract_dice_score` function, which effectively calculates the sum of scores from blue and red dots on the dice images.
- Developed a secondary function, `extract_dice_score_bonus`, to return individual scores from each colored dot as a bonus feature.
- Conducted extensive testing using various images of dice to validate the functionality, achieving accurate results across all test cases.
- Created detailed visualizations that demonstrate each step of the image processing pipeline, including color channel histograms and segmentation results.

### Methodology
The project was executed through a series of systematic steps:

1. **Color Space Transformation**: The images were converted from the RGB color space to the HSV (Hue, Saturation, Value) color space. This transformation was crucial because the HSV color space allows for easier segmentation of colors based on their hue, making it effective for distinguishing between blue and red dots.

2. **Color Thresholding**: A color thresholding technique was applied to isolate the blue and red dots. By defining specific ranges for the hue values corresponding to blue and red colors, the algorithm was able to create binary masks highlighting the relevant features in the images.

3. **Morphological Operations**: To improve the detection of dots and eliminate noise, morphological operations were applied. Dilation and erosion techniques helped refine the shape of the detected dots, ensuring that overlapping or closely spaced dots were correctly recognized and counted.

4. **Score Calculation**: The final step involved calculating the scores by counting the number of detected dots in each color category. The function aggregates these counts and returns the total scores for both blue and red dots.

5. **Testing and Validation**: The implemented function was tested on a diverse set of dice images to evaluate its performance and accuracy. Various scenarios, including different backgrounds and lighting conditions, were considered to ensure robustness.

6. **Visualizations**: Throughout the process, visualizations were created to illustrate each step, including histograms of RGB and HSV channels, the results of segmentation, and the final output showing the scores. These visual aids helped to better understand the effectiveness of each processing stage.

### Conclusion
This project showcases the application of image processing techniques in a practical scenario, demonstrating how color segmentation and morphological operations can be utilized to solve real-world problems involving visual data analysis.

## Exercise 2: Image Gradient Calculation Using Sobel Filters

In this task, I focused on implementing image gradient extraction using Sobel filters for both horizontal and vertical gradients. The Sobel filter is a widely used tool in image processing to highlight areas with rapid intensity changes, which are often indicative of edges. This method is fundamental in preparing images for further edge detection and analysis.

### Key Achievements

- **Implemented Sobel Filters**: Developed functions to compute horizontal and vertical gradients using Sobel operators. This helped in identifying the areas of sharp intensity changes within the image.
  
- **Extracted Gradient Magnitude and Angle**: Calculated the gradient magnitude to quantify the strength of the detected edges, and the gradient angle to determine the direction of these edges.
  
- **Prepared Image for Further Analysis**: The output gradients were utilized to refine the image for subsequent edge detection steps, improving the quality of feature extraction in the image processing pipeline.

### Approach

- **Sobel Filter Application**: Applied the Sobel filter to extract both the horizontal and vertical edges in the image.
  
- **Gradient Magnitude and Angle Calculation**: The magnitude was calculated to reflect the strength of edges, while the angle was used to represent their orientation. These values were crucial for understanding the structure of the edges in the image.

### Results

The use of Sobel filters allowed for effective edge detection, setting the foundation for further image analysis tasks, such as edge detection and feature extraction. This method enhanced the clarity of edges and improved the accuracy of identifying areas with significant changes in intensity.

### Application

This approach is applicable to various computer vision tasks, including object detection, facial recognition, and real-time image processing in fields like robotics and autonomous systems.
