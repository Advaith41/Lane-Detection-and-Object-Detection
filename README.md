# Lane-Detection-and-Object-Detection

## Project Overview
This project introduces an advanced Visual Driving Assistant (VDA) designed to enhance road safety by integrating lane detection and vehicle recognition. The system utilizes state-of-the-art algorithms for real-time lane marking and vehicle tracking. By combining traditional computer vision techniques with deep learning models like YOLOv8, the VDA delivers crucial feedback to drivers, ensuring a safer driving experience.

The system incorporates **YOLOv8**, a powerful object detection model, to identify and track vehicles in the driver’s vicinity. Simultaneously, lane detection is achieved using image processing methods like **Canny Edge Detection**, **Hough Transform**, and masking, enabling the system to detect road boundaries. Alerts are triggered when vehicles are identified as being too close, ensuring optimal safety.

Real-time video visualization of lane detection and object recognition is provided, demonstrating the practical application of the system and its potential as an effective driving assistant.

## Algorithm in Action
Here’s a sample of the system in action:

![Output Lane GIF](https://github.com/Advaith41/Lane-Detection-and-Object-Recognition/blob/main/Lane%20Detection%20and%20Object%20Recognition/impl_vid/challenge/output_lane.gif)


## I. Introduction
With the rapid increase in road traffic, ensuring driving safety has become a priority. In this context, **Visual Driving Assistants (VDAs)** are being developed to help drivers navigate the road more safely by analyzing their surroundings and providing crucial driving feedback.

This project introduces a VDA that combines **lane detection** and **vehicle recognition**. It leverages the YOLOv8 model for detecting vehicles and traditional image processing techniques (Canny edge detection, Hough transform) to map lane boundaries. By integrating these methods, the system offers drivers real-time alerts, helping them stay aware of road conditions and avoid potential collisions.

## II. Related Work

### A. Canny Edge Detection
Canny edge detection plays a critical role in identifying lane boundaries in images. The process involves several stages:
1. **Noise Reduction**: A Gaussian filter is used to smooth the image.
2. **Gradient Calculation**: The gradient magnitude and direction are computed to identify edge intensity.
3. **Non-Maximum Suppression**: Thin edges are retained while suppressing weaker edges.
4. **Double Thresholding**: Differentiates strong, weak, and non-edges to focus on the most relevant lines.

### B. Hough Transform
The **Hough Transform** detects straight lines within an image after edge detection. This algorithm converts the image into a parameter space, identifying lines by accumulating votes. After detection, the lines are classified into left and right lanes, aiding in accurate lane representation on the road.

### C. YOLOv8n
**YOLOv8n** (You Only Look Once v8) is a deep learning-based model designed for real-time object detection. It offers high accuracy and speed, making it ideal for vehicle detection in driving scenarios. The model tracks vehicles in the driver’s field of view and helps calculate their proximity, enabling the system to issue alerts if any vehicle is deemed to be too close.

## III. System Architecture

### Lane Detection Pipeline
1. **Preprocessing**: Convert the input image to grayscale and apply a Gaussian blur for noise reduction.
2. **Edge Detection**: Use Canny edge detection to identify potential lane boundaries.
3. **Line Detection**: Apply Hough Transform to detect and classify the left and right lane lines based on their orientation and position.
4. **Lane Visualization**: Draw the detected lanes (left and right) on the original image for visual feedback.

### Object Detection Pipeline
1. **Vehicle Detection**: Use YOLOv8n to detect vehicles in the camera's field of view.
2. **Proximity Analysis**: Calculate the relative distance of detected vehicles to assess their risk.
3. **Alerting**: Trigger alerts if a vehicle is detected too close to the driver's vehicle.

### Integration of Lane Detection & Object Recognition
The results from lane detection and vehicle recognition are merged and displayed in real-time, providing a complete picture of the road environment to the driver.

## IV. Experiments and Evaluation

### A. Datasets & Testing
The system was tested using three video datasets from the **Udacity database**:
1. **solidWhiteRight.mp4**
2. **solidYellowLeft.mp4**
3. **challenge.mp4**

Each dataset posed unique challenges, including varying lane types, road conditions, and lighting.

### B. Performance and Errors

#### Lane Detection Errors:
- **Incorrect Slope**: Happens when the left or right lane is incorrectly identified due to variations in road curvature or angles.
- **Cross-Poly**: Occurs when points from opposite lanes are mistakenly connected, especially on winding roads.
- **Slope Not Detected**: The system fails to detect the lane when there are too few data points or irregular patterns.

#### Object Recognition Errors:
- **False Positive Detection**: Non-vehicle objects may be detected as vehicles.
- **False Proximity Alert**: The system might incorrectly classify a distant vehicle as being too close, based on its relative position in the image.

#### Performance Metrics:
- **Lane Detection Error (LDE)**:
    - SolidWhiteRight.mp4: ~0.95%
    - SolidYellowLeft.mp4: ~2.32%
    - Challenge.mp4: ~43.98%
  
- **Vehicle Recognition Error Rate**: ~13% across all videos.

## V. Conclusion
The **Visual Driving Assistant (VDA)** effectively integrates deep learning and traditional computer vision methods to provide real-time lane detection and vehicle recognition. While the system performs well in controlled scenarios, it faces challenges in more complex environments, such as roads with sharp curves or varying lighting conditions.

To further enhance the system’s accuracy and robustness, future work could explore advanced deep learning-based approaches, such as **semantic segmentation**, for more accurate lane detection in diverse driving conditions.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

