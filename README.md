
# Document Scanner
![image](https://github.com/user-attachments/assets/a9397f9c-ec35-43de-9e81-108e52c4f377)


## Overview
The **Document Scanner** project uses OpenCV to scan and crop documents from an image. This tool is designed to automatically detect the largest rectangular object in an image, assume it as a document, and then transform and crop the image to provide a clean, top-down view of the document.

## Features
- **Preprocessing**: Converts the image to grayscale, applies Gaussian blur, and detects edges using the Canny edge detector.
- **Contour Detection**: Identifies the largest rectangular contour, which is assumed to be the document.
- **Perspective Transformation**: Warps the detected document to a top-down view.
- **Cropping**: Crops the warped image to remove any unnecessary borders.

## Prerequisites
Before running the project, ensure you have the following:
- **OpenCV**: Installed and configured in your development environment.
- **Image File**: A sample image of a document to test the scanner.

## Setup

1. **Clone the Repository**:
    ```bash
    git clone <repository-url>
    cd Document-Scanner
    ```

2. **Prepare the Resources**:
   - Place your document images in the `Resources` directory.

3. **Build the Project**:
   - Compile the code using your preferred C++ compiler, making sure to link the OpenCV libraries.

## Usage

1. **Run the Project**:
   - Execute the compiled program to start the document scanning process.
   - The program will automatically detect, warp, and crop the document from the image.

2. **View Results**:
   - The original image, warped document, and cropped output will be displayed in separate windows.

## Code Explanation

The main parts of the project code include:

- **Image Preprocessing**:
  ```cpp
  Mat preProcessing(Mat img) {
      cvtColor(img, imgGray, COLOR_BGR2GRAY);
      GaussianBlur(imgGray, imgBlur, Size(3, 3), 3, 0);
      Canny(imgBlur, imgCanny, 25, 75);
      Mat kernel = getStructuringElement(MORPH_RECT, Size(3, 3));
      dilate(imgCanny, imgDil, kernel);
      return imgDil;
  }
  ```

- **Finding Contours**:
  ```cpp
  vector<Point> getContours(Mat image) {
      // Finding the largest rectangle
  }
  ```

- **Reordering Points**:
  ```cpp
  vector<Point> reorder(vector<Point> points) {
      // Reordering points to map correctly for warping
  }
  ```

- **Warping the Image**:
  ```cpp
  Mat getWarp(Mat img, vector<Point> points, float w, float h) {
      // Applying perspective transformation
  }
  ```

## Customization
- **Image Path**: Modify the `path` variable in `main()` to test different images.
- **Crop Value**: Adjust the `cropVal` parameter in `main()` to fine-tune the cropping borders.

## Contributing
Feel free to fork the project and submit pull requests if you have any improvements or bug fixes.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements
- **OpenCV**: For providing the powerful library that made this project possible.
- **Image Processing Techniques**: For the methods used in detecting and transforming documents.

