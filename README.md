# Automated Multiplication Quiz Solver

[![Python 3.8+](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An intelligent automation bot that solves multiplication problems in quizzes/games using OCR and precise mouse control. I needed to automate a very repitive multiplication game for a high score that was required timely elsewhere, and hence the need for this automation was born, you can configure it to play any multiplication(or any arithmetic games) you want by changing the coordinates for the question and answer reigons on the screen and there is a debug mode as well to help you see the resulting images of the reigons specified to adjust them as needed.

<!-- ![Demo Visualization](https://via.placeholder.com/800x400.png?text=Automation+Demo+Screenshot+-+Replace+With+Actual+Image) -->

## Features

- 🎯 Accurate OCR processing with Tesseract v5+
- ⚙️ Configurable screen regions for question/answer detection
- 🤖 Human-like mouse movements and click timing
- 🔄 Automatic pop-up detection ("Back to Game" handling)
- 📸 Debug image saving for OCR optimization
- � Robust error recovery and retry mechanisms
- 🧮 Supports integer multiplication problems (e.g., "12*5")
- 📊 Confidence-based answer matching system
- ⏲️ Randomized delays to mimic human behavior

## Requirements

- Python 3.8+
- Tesseract OCR ≥5.0 ([Windows installer](https://github.com/UB-Mannheim/tesseract/wiki))
- Required Python packages:
  ```bash
  pip install pyautogui pytesseract Pillow imagehash
  ```

## Setup & Configuration

1. **Install Tesseract** and note its installation path
2. Clone repository:
   ```bash
   git clone https://github.com/yourusername/multiplication-solver.git
   cd multiplication-solver
   ```
3. Edit script configuration:
   ```python
   # -*- coding: utf-8 -*-
   # --- Configuration --- MUST BE EDITED ---
   tesseract_path = r'C:\Program Files\Tesseract-OCR\tesseract.exe'  # Your Tesseract path
   
   # Adjust these regions using Windows' Snipping Tool coordinates:
   QUESTION_REGION = (880, 260, 300, 100)       # Region containing multiplication problem
   OPTIONS_REGIONS = [                          # Answer option regions
       (900, 370, 200, 50),
       (900, 440, 200, 50),
       (900, 520, 200, 50),
       (900, 600, 200, 50)
   ]
   BACK_TO_GAME_REGION = (900, 700, 200, 50)    # Pop-up button region
   ```

## How It Works

1. **Screen Capture**: Uses PIL.ImageGrab to capture configured regions
2. **Image Preprocessing**:
   - Grayscale conversion
   - Threshold binarization (adjustable)
   - Optional inversion
3. **OCR Processing**:
   - Custom Tesseract config for numbers/symbols
   - Text cleaning and validation
4. **Calculation**:
   - Parses multiplication problems
   - Computes correct answer
5. **Answer Matching**:
   - Numeric comparison with tolerance
   - Fallback strategies
6. **Execution**:
   - Humanized mouse movements
   - Randomized delays
   - Pop-up handling

## Troubleshooting

**Common Issues**:
- Incorrect OCR results:
  - Adjust `PREPROCESSING_THRESHOLD` (180 default)
  - Enable `SAVE_DEBUG_IMAGES = True`
  - Check debug images in `ocr_debug_images/`
- Tesseract not found:
  - Verify `tesseract_path` in configuration
  - Add Tesseract to system PATH

**Performance Tips**:
- Keep target window visible
- Disable animations in target application
- Use consistent window positioning
- Start with large debug thresholds (200+)

## Limitations

- Currently only supports integer multiplication
- Requires static window positioning
- Dependent on screen resolution (1920x1080 recommended)
- May require calibration for different font styles

## Disclaimer

This project is intended for **educational purposes only**. Always respect application terms of service and local laws when implementing automation solutions. Use at your own risk.
