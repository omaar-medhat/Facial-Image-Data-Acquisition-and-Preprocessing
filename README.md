# Face Detection Project

## Overview
This project implements a face detection and facial landmark identification system using Python. It leverages the `dlib` library for face detection and landmark prediction, and `OpenCV` for image processing. The script searches for images online, downloads them, detects faces, draws bounding boxes around detected faces, and marks facial landmarks. Additionally, it includes functionality to crop specific regions of an image, such as the face or eyes.

## Features
- **Image Search and Download**: Uses SerpApi to search for frontal face images on Google and downloads them.
- **Face Detection**: Detects faces in images using `dlib`'s frontal face detector.
- **Facial Landmark Detection**: Identifies 68 facial landmarks using `dlib`'s shape predictor.
- **Image Processing**: Converts images to RGB, draws bounding boxes around faces, and marks facial landmarks with circles.
- **Cropping**: Crops specific regions (e.g., face or eyes) from images for focused analysis.
- **Visualization**: Displays images with detected faces and landmarks using `matplotlib`.

## Prerequisites
- Python 3.x
- Required Python libraries:
  - `numpy`
  - `matplotlib`
  - `pandas`
  - `requests`
  - `beautifulsoup4`
  - `google-search-results`
  - `networkx`
  - `opencv-python`
  - `dlib`
- System dependencies:
  - `cmake` (for `dlib` installation)
  - `bunzip2` (for decompressing the shape predictor file)
- A pre-trained model file: `shape_predictor_68_face_landmarks.dat` (downloaded in the script)

## Installation
1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Install Dependencies**:
   Install the required Python packages:
   ```bash
   pip install numpy matplotlib pandas requests beautifulsoup4 google-search-results networkx opencv-python dlib
   ```

3. **Install System Dependencies**:
   On a Linux-based system, install `cmake` and `bunzip2`:
   ```bash
   sudo apt update
   sudo apt install -y cmake
   ```

4. **Download the Shape Predictor**:
   The script automatically downloads the `shape_predictor_68_face_landmarks.dat` file using `wget`. Ensure you have `wget` installed, or manually download the file from [dlib.net](http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2) and decompress it:
   ```bash
   bunzip2 shape_predictor_68_face_landmarks.dat.bz2
   ```

## Usage
1. **Set Up SerpApi Key**:
   - Obtain an API key from [SerpApi](https://serpapi.com/).
   - Replace the `api_key` in the `params` dictionary in the script with your own key:
     ```python
     params = {
         'q': 'frontal face closeup and sharp',
         'hl': 'en',
         'tbm': 'isch',
         'engine': 'google',
         'api_key': 'your-api-key-here',
     }
     ```

2. **Run the Script**:
   Execute the script:
   ```bash
   python face_detection.py
   ```

3. **Input**:
   - The script prompts for the number of images to download:
     ```
     enter number of image:
     ```
   - Enter an integer (e.g., `3`) to specify how many images to process.

4. **Output**:
   - Images are downloaded as `image1.jpg`, `image2.jpg`, etc.
   - Processed images with bounding boxes and landmarks are displayed using `matplotlib`.
   - Cropped images (e.g., `image_after_crop.jpg`, `image_after_crop_eyes.jpg`) are saved to the working directory.
   - The console outputs the number of detected faces in each image.

## Script Workflow
1. **Search and Download**:
   - Queries Google Images for "frontal face closeup and sharp" using SerpApi.
   - Downloads the specified number of images.

2. **Face Detection**:
   - Loads each image using `OpenCV`.
   - Converts images to RGB format.
   - Uses `dlib`'s frontal face detector to identify faces.
   - Draws green bounding boxes around detected faces.

3. **Facial Landmark Detection**:
   - Uses `dlib`'s shape predictor to identify 68 facial landmarks.
   - Marks landmarks with red circles on the images.

4. **Cropping**:
   - Processes a specific image (`stock-photo.jpg`) to crop the face and eye regions.
   - Saves cropped images as `image_after_crop.jpg` and `image_after_crop_eyes.jpg`.

5. **Visualization**:
   - Displays all processed images with bounding boxes and landmarks using `matplotlib`.

## Notes
- The script assumes a Colab environment for some commands (e.g., `!pip`, `!wget`). For local execution, remove the `!` prefix and ensure dependencies are installed.
- The `stock-photo.jpg` image must be present in the working directory for cropping operations.
- Ensure a stable internet connection for image downloads and API calls.
- The SerpApi key provided in the script is for demonstration; replace it with a valid key.

## Limitations
- The script may fail if the SerpApi key is invalid or the quota is exceeded.
- Image downloads depend on the availability of URLs returned by the API.
- The cropping coordinates are hardcoded for `stock-photo.jpg` and may need adjustment for other images.
- The script is designed for frontal face images; performance may vary with profile or low-quality images.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments
- [dlib](http://dlib.net/) for face detection and landmark prediction.
- [OpenCV](https://opencv.org/) for image processing.
- [SerpApi](https://serpapi.com/) for Google Images search functionality.
