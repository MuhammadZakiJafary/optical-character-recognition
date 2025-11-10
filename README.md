🧠 Optical Character Recognition (OCR) Using Python and Tesseract
This project demonstrates an Optical Character Recognition (OCR) system developed in Python using OpenCV, Tesseract, and Pillow, implemented inside Google Colab. The project extracts and converts printed or handwritten text from images into editable digital text.
The main objective of this project is to showcase how artificial intelligence and computer vision can be used to enable machines to read and interpret text from visual input.

🚀 Features
Extracts text from printed or handwritten images.
Works directly in Google Colab — no local setup required.
Supports multiple image formats (.png, .jpg, .jpeg).
Includes preprocessing (grayscale, thresholding) to enhance accuracy.
Saves extracted text to a .txt file for download.

🧩 Technologies Used
Python 🐍
OpenCV (for image preprocessing)
Tesseract OCR (for text recognition)
Pillow (for image handling)
Google Colab (for running the project online)

⚙️ Installation
Step 1: Install Dependencies
Run these commands in Google Colab:
!pip install pytesseract opencv-python pillow
!apt install tesseract-ocr -y

🧾 Usage
Step 1: Import Libraries
import cv2
import pytesseract
from PIL import Image
from google.colab import files

Step 2: Upload an Image
uploaded = files.upload()
for filename in uploaded.keys():
    image_path = filename

Step 3: Read and Display the Image
image = cv2.imread(image_path)
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
Image.fromarray(image_rgb)

Step 4: Extract Text
text = pytesseract.image_to_string(image_rgb)
print(text)

Step 5: (Optional) Preprocessing for Better Accuracy
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
_, thresh = cv2.threshold(gray, 150, 255, cv2.THRESH_BINARY)
text_cleaned = pytesseract.image_to_string(thresh)
print(text_cleaned)

Step 6: Save Extracted Text
with open("extracted_text.txt", "w", encoding="utf-8") as f:
    f.write(text_cleaned)
files.download("extracted_text.txt")

🎯 Example Output
Upload an image containing text.
The notebook extracts readable text.
Output text is displayed in the console and can be downloaded as a .txt file.

🛠️ Future Improvements
Add batch OCR (process multiple images at once).
Integrate translation for extracted text.
Add handwriting recognition using deep learning models.

Create a web interface using Flask or Streamlit.
