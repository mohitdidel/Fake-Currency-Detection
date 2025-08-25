🏦 Fake Currency Detection (₹500 / ₹2000 Notes)

📌 Project Overview
I am developing a fake currency detection system using Python and OpenCV.  
The goal is to automatically verify Indian currency notes (₹500 and ₹2000) by analyzing their security features such as bleed lines and the serial number panel.  
This system aims to help banks, shops, and individuals quickly identify counterfeit notes without specialized hardware.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

🎯 Objectives
- Detect counterfeit Indian currency notes (₹500 / ₹2000).  
- Automate **feature extraction & verification** using computer vision.  
- Provide a **fast and reliable rule-based detection system**.  
- Enable practical use cases where expensive machines are not available.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

📂 Dataset Description
- The dataset contains images of **both genuine and fake notes** of ₹500 and ₹2000.  
- Each note is captured under:
  - Different lighting conditions (indoor, daylight).  
  - Multiple angles and backgrounds.  
- Dataset includes **balanced samples** for real and fake.  
- Filenames encode denomination & label (e.g., `500_real_01.jpg`, `2000_fake_03.jpg`).  
- Additional **template ROIs** for features (bleed lines, number panels) are stored for comparisons.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

⚙️ Procedure & Workflow
1️⃣ Preprocessing
- Resize all input images to 1167×519.  
- Apply Gaussian blur to reduce noise.  
- Convert to grayscale where required.

2️⃣ Feature Extraction
Feature 8: Left Bleed Lines 
- Crop left strip → threshold → count vertical transitions.  
- Accept if average transitions ≈ 5 (range 4.7–5.6).  

Feature 9: Right Bleed Lines  
- Similar process on right strip.  
- Accept if transitions ≈ 5 (range 4.7–5.6).  

Feature 10: Serial Number Panel 
- Crop number panel → threshold → contour detection.  
- Count bounding boxes of digits.  
- Accept if **≥ 9 characters detected**.  

3️⃣ Decision Logic
- If **≥ 2 out of 3 features** pass → ✅ REAL Note.  
- Otherwise → ❌ FAKE Note.  

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

📊 Results
- Output:** `"REAL CURRENCY NOTE"` or `"FAKE CURRENCY NOTE"`.  
- Validation done on both denominations (₹500 & ₹2000).  
- Performance evaluated with accuracy, precision, and recall.  

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

🚀 How to Run in Google Colab
1. Upload the project notebook or script.  
2. Upload a test note image.  
3. Run all cells → System will output REAL / FAKE.  

python
✅ RESULT: REAL CURRENCY NOTE
❌ RESULT: FAKE CURRENCY NOTE
