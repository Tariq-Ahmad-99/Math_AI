# Math AI

https://github.com/user-attachments/assets/d1def56c-b9e6-4ff0-95f8-d34ed26d2ea8

## Overview
This project combines **real-time hand gesture recognition**, **AI interaction**, and **drawing capabilities** using Python. It allows users to draw on the screen using hand gestures detected via a webcam, clear the canvas with specific gestures, and interact with an AI model to solve math problems based on the drawings.

## Features
1. **Real-time Hand Tracking**:
   - Tracks hand gestures using the `cvzone.HandTrackingModule`.
   - Detects and interprets specific hand gestures:
     - **Index finger up**: Draw on the canvas.
     - **Thumb and pinky up**: Clear the canvas.

2. **AI Integration**:
   - Integrates with **Google Generative AI** to process drawings and provide answers or solutions.

3. **Interactive Streamlit UI**:
   - Displays a real-time video feed with drawing overlays.
   - Allows users to enable or disable the drawing functionality.
   - Shows AI-generated responses.

4. **Customizable Settings**:
   - Easily switch between AI models by updating the API key.
   - Adjustable detection and tracking confidence levels for the hand tracker.

---

## Installation and Setup

### Prerequisites
- Python 3.8 or higher.
- Webcam

### Dependencies
Install the required Python packages using pip:

```bash
pip install cvzone numpy opencv-python-headless pillow streamlit google-generativeai
```

### Steps
1. Clone this repository:
   ```bash
   git clone <repository_url>
   cd <repository_folder>
   ```
2. Add your Google Generative AI API key to the code:
   Replace `api_no` in `genai.configure(api_key=api_no)` with your API key.

3. Run the application:
   ```bash
   streamlit run main.py
   ```

4. Interact with the application via the Streamlit web interface.

---

## How It Works
1. **Hand Detection**:
   - The webcam captures real-time video frames.
   - `cvzone.HandTrackingModule` detects hand landmarks and determines the gestures.

2. **Drawing on the Canvas**:
   - If the index finger is raised, a line is drawn from its position in the current frame to its position in the previous frame.
   - If the thumb and pinky are raised, the canvas is cleared.

3. **AI Interaction**:
   - When all fingers except the thumb are raised, the current drawing is sent to the AI model for interpretation.

4. **Output Display**:
   - The video feed, along with the drawing overlay, is displayed in real-time.
   - AI-generated responses are shown on the Streamlit interface.

---

## Customization
- Modify the detection and tracking confidence levels in the `HandDetector` initialization to fine-tune hand tracking:
  ```python
  detector = HandDetector(staticMode=False, maxHands=1, modelComplexity=1, detectionCon=0.7, minTrackCon=0.5)
  ```

- Replace the AI model as needed by changing the model name in:
  ```python
  model = genai.GenerativeModel("gemini-1.5-flash")
  ```

---

## License
This project is licensed under the MIT License.
