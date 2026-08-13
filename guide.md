# AgriGuard AI

## AI-Powered Crop Disease Prediction and Management System

**Project Type:** Mini Project / Software Engineering Project
**Domain:** Artificial Intelligence, Machine Learning, Agriculture, Full-Stack Web Development
**Reference:** Smart India Hackathon-inspired problem statement — AI-Driven Crop Disease Prediction and Management System
**Frontend & Full-Stack Framework:** Next.js
**Database:** MongoDB
**Machine Learning:** Python, PyTorch/TensorFlow
**ML API:** FastAPI

---

# 1. Project Overview

Agriculture is heavily affected by plant diseases. If a disease is detected late, it can spread rapidly across crops and cause significant reductions in crop yield and financial losses.

Farmers often depend on visual inspection or expert consultation to identify diseases. This can be slow, expensive, and unavailable in remote areas.

**AgriGuard AI** is a web/mobile-friendly intelligent crop health platform that allows a farmer to upload or capture an image of a crop leaf. The system uses a machine-learning model to analyze the image and predict the most likely disease.

The system then provides:

* Disease name
* Prediction confidence
* Disease severity
* Symptoms
* Recommended management actions
* Prevention methods
* Weather-based disease risk
* Diagnosis history
* Crop health analytics
* Notifications and alerts

The goal is not simply to build an image classifier.

The goal is to build a complete **crop disease prediction and management platform**.

---

# 2. Problem Statement

Farmers may face difficulty identifying crop diseases at an early stage because:

1. Disease symptoms can look similar across different diseases.
2. Agricultural experts may not always be immediately available.
3. Manual diagnosis takes time.
4. Disease progression can be rapid.
5. Weather conditions can increase disease risk.
6. Farmers may not maintain historical records of crop health.
7. Existing disease-detection demonstrations often only identify a disease without providing useful management information.

Therefore, there is a need for an intelligent system that can:

> Detect potential crop diseases from images and provide actionable information to help farmers manage crop health.

---

# 3. Proposed Solution

AgriGuard AI provides an integrated crop-health platform.

The basic workflow is:

```text
Farmer
   ↓
Login / Register
   ↓
Register Farm
   ↓
Select Crop
   ↓
Capture / Upload Leaf Image
   ↓
Image Validation
   ↓
AI Disease Prediction
   ↓
Disease + Confidence
   ↓
Severity Assessment
   ↓
Management Recommendations
   ↓
Weather Analysis
   ↓
Disease Risk
   ↓
Notification / Alert
   ↓
Diagnosis History
```

---

# 4. Main Objectives

## 4.1 Primary Objectives

The system should:

* Detect crop diseases from leaf images.
* Provide a prediction confidence score.
* Identify whether the plant appears healthy or diseased.
* Provide disease information.
* Provide management recommendations.
* Maintain diagnosis history.
* Provide crop health analytics.
* Integrate weather information.
* Estimate disease risk based on environmental conditions.

## 4.2 Secondary Objectives

The system should eventually support:

* Multiple crops.
* Multiple diseases.
* Multilingual interfaces.
* Mobile-friendly usage.
* Regional disease analysis.
* Notifications.
* Offline/edge inference as a future enhancement.

---

# 5. Scope

The first version should NOT attempt to identify every disease affecting every crop.

That would be unrealistic for a mini project.

## Initial Scope

Support approximately 2–3 crops.

Example:

### Tomato

* Healthy
* Early Blight
* Late Blight
* Leaf Mold
* Septoria Leaf Spot

### Potato

* Healthy
* Early Blight
* Late Blight

### Pepper

* Healthy
* Bacterial Spot

The exact supported diseases should depend on the dataset used for training.

---

# 6. Target Users

## 6.1 Farmer

The farmer can:

* Register.
* Create farms.
* Add crops.
* Scan leaves.
* View predictions.
* View recommendations.
* Check crop health.
* View previous diagnoses.
* Receive alerts.

## 6.2 Administrator

The administrator can:

* Manage users.
* View disease statistics.
* View system activity.
* Manage disease information.
* Monitor reported diagnoses.
* View regional trends.
* Manage recommendation data.

## 6.3 Agricultural Expert — Future

An optional expert role can be added later.

Experts can:

* Review difficult cases.
* Verify AI predictions.
* Add recommendations.
* Provide feedback.

---

# 7. High-Level Architecture

```text
                         ┌─────────────────────┐
                         │      Farmer         │
                         │  Web / Mobile UI    │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │      Next.js        │
                         │                     │
                         │ App Router          │
                         │ React UI            │
                         │ API Routes          │
                         │ Authentication      │
                         │ Business Logic      │
                         └──────────┬──────────┘
                                    │
                  ┌─────────────────┼─────────────────┐
                  │                 │                 │
                  ▼                 ▼                 ▼
             MongoDB          Weather API      ML Service
                                                      │
                                                      ▼
                                              Python / FastAPI
                                                      │
                                                      ▼
                                             ML Model
                                                      │
                                                      ▼
                                           Disease Prediction
```

---

# 8. Technology Stack

## Frontend

* Next.js
* React
* TypeScript
* Tailwind CSS
* shadcn/ui
* Recharts or another charting library

## Backend

Next.js itself will handle the application backend:

* Route Handlers
* Server Actions where appropriate
* Authentication
* Authorization
* Business logic
* Database operations

## Database

MongoDB.

## Machine Learning

Python.

Possible libraries:

* PyTorch or TensorFlow
* torchvision
* OpenCV
* NumPy
* Pillow
* scikit-learn

## ML API

FastAPI.

## Storage

For the prototype:

* Local storage during development

For deployment:

* Cloudinary, S3-compatible storage, or another object-storage service.

Images should generally NOT be stored directly inside MongoDB.

MongoDB should store the image URL and metadata.

## External APIs

Potentially:

* Weather API
* Geolocation API
* Notification service

---

# 9. Why Next.js Instead of Express + React?

The project does not need:

```text
React
   ↓
Express
   ↓
MongoDB
```

if Next.js is already being used.

Instead:

```text
Next.js
├── UI
├── Server Components
├── Route Handlers
├── Server Actions
├── Authentication
└── MongoDB
```

This reduces unnecessary infrastructure.

However, the ML model should remain separate:

```text
Next.js
   ↓
FastAPI
   ↓
ML Model
```

Python is the better environment for model training and inference.

---

# 10. Complete Application Modules

The system should contain the following modules:

```text
1. Authentication
2. User Management
3. Farm Management
4. Crop Management
5. Image Upload
6. AI Disease Prediction
7. Disease Information
8. Disease Management
9. Weather Analysis
10. Disease Risk Prediction
11. Diagnosis History
12. Crop Health Analytics
13. Notifications
14. Admin Dashboard
```

---

# 11. Authentication Module

Users should be able to:

* Register.
* Login.
* Logout.
* Reset password.
* Manage profile.

Example registration:

```text
Name
Email
Password
Location
Preferred Language
```

After registration:

```text
User
  ↓
Dashboard
  ↓
Create Farm
```

---

# 12. Farm Management

A farmer can create one or more farms.

Example:

```text
Farm Name: Omer Farm
Location: Hyderabad
Area: 2.5 acres
```

The farmer can then add crops.

Example:

```text
Farm
 ├── Tomato
 ├── Potato
 └── Pepper
```

---

# 13. Crop Management

Each crop should contain information such as:

```text
Crop
├── Crop name
├── Variety
├── Planting date
├── Farm
├── Area
└── Current health status
```

Example:

```text
Crop: Tomato

Farm: Omer Farm
Area: 1 acre
Planting Date: 2026-07-20

Current Health:
82%
```

---

# 14. Image Scanning Module

The primary user action is:

```text
[ Scan Crop ]
```

The user can:

```text
Take Photo
     OR
Upload Image
```

The frontend should validate:

* File type
* File size
* Image dimensions

Supported formats:

```text
JPG
JPEG
PNG
WEBP
```

---

# 15. Image Processing Pipeline

The image goes through:

```text
Image Upload
     ↓
Validation
     ↓
Resize
     ↓
Normalization
     ↓
ML Model
```

The ML model should receive a standardized image.

For example:

```text
224 × 224 pixels
```

depending on the model architecture.

---

# 16. Machine Learning Pipeline

The ML system is responsible for disease classification.

```text
Input Image
     ↓
Preprocessing
     ↓
Feature Extraction
     ↓
Classification Model
     ↓
Probability Scores
     ↓
Top Prediction
```

Example internal model output:

```json
{
  "healthy": 0.02,
  "early_blight": 0.94,
  "late_blight": 0.03,
  "leaf_mold": 0.01
}
```

The system selects:

```text
early_blight
```

because it has the highest probability.

---

# 17. Model Architecture

For the first version, use transfer learning.

Possible models:

* MobileNetV3
* EfficientNet
* ResNet

For a mini project, MobileNet or EfficientNet is preferable because the model is smaller and easier to deploy.

Example:

```text
Plant Image
     ↓
MobileNet / EfficientNet
     ↓
Feature Extraction
     ↓
Classification Layer
     ↓
Disease Classes
```

Do NOT train an enormous model from scratch unless there is a specific reason.

---

# 18. Dataset

A suitable public plant-disease dataset can be used for initial development.

PlantVillage is one commonly used dataset for plant disease research.

The dataset should be divided into:

```text
Training
Validation
Testing
```

Example:

```text
70% Training
15% Validation
15% Testing
```

The exact split can be changed based on experimentation.

---

# 19. Model Output

The ML service should return structured data.

Example:

```json
{
  "crop": "Tomato",
  "disease": "Early Blight",
  "confidence": 0.942,
  "status": "diseased"
}
```

The Next.js backend then enriches this result with information from MongoDB.

---

# 20. Important: Confidence Is Not Certainty

The UI must NOT say:

> "The plant definitely has Early Blight."

Instead:

> "The model predicts Early Blight with 94.2% confidence."

This distinction is important.

The system is an AI-assisted decision-support tool, not a replacement for a qualified agricultural expert.

---

# 21. Prediction Result Page

After scanning, the user should see a clear result.

Example:

```text
┌─────────────────────────────────────────┐
│              Crop Analysis              │
├─────────────────────────────────────────┤
│                                         │
│          [ Uploaded Image ]             │
│                                         │
│  Crop                                    │
│  Tomato                                  │
│                                         │
│  Detected Condition                      │
│  Early Blight                            │
│                                         │
│  AI Confidence                           │
│  94.2%                                   │
│                                         │
│  Status                                  │
│  Diseased                                │
│                                         │
│  Severity                                │
│  Medium                                  │
│                                         │
│  [ View Management Advice ]              │
└─────────────────────────────────────────┘
```

---

# 22. Disease Severity

The initial ML model does not necessarily need to directly predict severity.

Instead, severity can initially be determined using a rule-based system.

Example:

```text
Confidence
+
Visible affected area
+
Disease information
=
Severity estimate
```

Example:

```text
Affected leaf area < 10%
→ Low

10–30%
→ Medium

30–60%
→ High

>60%
→ Critical
```

This is a prototype rule.

It should not be presented as scientifically validated unless you actually validate it with agricultural expertise/data.

---

# 23. Disease Information

Every supported disease should have a record in MongoDB.

Example:

```text
Disease:
Early Blight

Crop:
Tomato

Description:
Fungal disease affecting tomato foliage.

Symptoms:
- Brown spots
- Yellowing leaves
- Concentric rings

Risk Factors:
- High humidity
- Wet foliage
- Poor air circulation
```

---

# 24. Management Recommendations

The result page should contain:

```text
Management Recommendations

Immediate Actions
────────────────────────
• Remove heavily infected leaves.
• Improve airflow around plants.
• Avoid unnecessary leaf wetness.

Prevention
────────────────────────
• Maintain adequate plant spacing.
• Practice field sanitation.
• Monitor nearby plants.

Monitoring
────────────────────────
Inspect the crop again within 24–48 hours.
```

For a student project, store these recommendations in MongoDB.

Do not let an LLM freely generate agricultural treatment instructions and present them as authoritative.

---

# 25. Weather Integration

The system can retrieve weather information based on the farm's location.

Example:

```text
Temperature: 27°C
Humidity: 86%
Rainfall: 18mm
Wind: 7 km/h
```

The system can then calculate a disease-risk score.

Example:

```text
Temperature     → Suitable
Humidity        → High
Rainfall        → High
Leaf Wetness    → High

Overall Risk
████████████████░░ 82%

HIGH
```

---

# 26. Disease Risk Engine

The risk engine can initially be rule-based.

Example:

```text
Temperature suitable?
Humidity high?
Rainfall high?
Previous disease detected?

        ↓

Risk Score
```

Example:

```text
Humidity:       +30
Rainfall:       +25
Temperature:    +20
Previous cases: +15
                ----
Total:           90
```

Then:

```text
0–25   → LOW
26–50  → MODERATE
51–75  → HIGH
76–100 → VERY HIGH
```

These values are project rules and should be described as a prototype risk model, not as an agricultural scientific standard.

---

# 27. Weather-Based Alert

Example:

```text
⚠️ HIGH DISEASE RISK

Tomato — Early Blight

Your farm currently has conditions
that may increase disease risk.

Humidity: 89%
Temperature: 23°C
Rainfall: High

Recommended Action:

Inspect tomato leaves within the
next 24 hours.

[ View Details ]
```

---

# 28. Diagnosis History

Every scan should be stored.

Example:

```text
Date          Crop       Disease          Confidence
-----------------------------------------------------
Aug 13        Tomato     Early Blight     94%
Aug 10        Tomato     Healthy          97%
Aug 06        Potato     Late Blight      89%
Aug 01        Tomato     Leaf Mold        91%
```

The farmer can open any previous diagnosis.

---

# 29. Crop Health Score

The dashboard can calculate a simplified crop-health score.

Example:

```text
Crop Health

Tomato
████████████████░░░░ 82%

Potato
██████████████░░░░░░ 71%

Pepper
██████████████████░░ 90%
```

The score can use:

```text
Recent diagnosis
Disease severity
Disease frequency
Recent risk
```

Again, this should be clearly documented as a **system-generated indicator**, not a scientifically validated crop-health measurement.

---

# 30. Dashboard

The main dashboard should contain:

```text
Welcome, Farmer

┌────────────┐ ┌────────────┐
│ Farms      │ │ Crops      │
│ 3          │ │ 7          │
└────────────┘ └────────────┘

┌────────────┐ ┌────────────┐
│ Scans      │ │ Diseases   │
│ 47         │ │ 8          │
└────────────┘ └────────────┘


Crop Health
────────────────────────

Tomato       ████████████████░ 82%
Potato       █████████████░░░░ 71%
Pepper       █████████████████ 90%


Recent Diagnoses
────────────────────────

Tomato    Early Blight    94%
Potato    Late Blight     89%
Tomato    Healthy         97%


Disease Risk
────────────────────────

⚠️ Tomato
High Risk

[ Scan Crop ]
```

---

# 31. Admin Dashboard

The administrator dashboard can show:

```text
Total Users
Total Farms
Total Scans
Total Diseases Detected
Most Common Disease
Most Affected Crop
```

Example:

```text
SYSTEM OVERVIEW

Users                    1,284
Registered Farms           742
Total Scans              8,932
Diseases Detected        3,217

Most Detected Disease:
Tomato Early Blight

Most Affected Crop:
Tomato
```

---

# 32. Regional Disease Heatmap

This is an advanced feature.

If location data is collected with user consent and appropriate privacy controls:

```text
        Disease Distribution

              🔴
         🟠   🔴   🟠
       🟢  🟠   🔴
          🟢
      🟢       🟠
```

The admin could see:

```text
Region: Hyderabad

Tomato Early Blight
Cases: 37

Previous Week: 18

Trend: +105%
```

This could eventually help identify regional disease outbreaks.

---

# 33. MongoDB Data Model

## User

```text
User
├── _id
├── name
├── email
├── passwordHash
├── role
├── location
├── language
├── createdAt
└── updatedAt
```

## Farm

```text
Farm
├── _id
├── userId
├── name
├── location
├── latitude
├── longitude
├── area
├── unit
├── createdAt
└── updatedAt
```

## Crop

```text
Crop
├── _id
├── farmId
├── cropType
├── variety
├── plantingDate
├── area
├── healthScore
├── createdAt
└── updatedAt
```

## Diagnosis

```text
Diagnosis
├── _id
├── userId
├── farmId
├── cropId
├── imageUrl
├── crop
├── disease
├── confidence
├── severity
├── status
├── weatherSnapshot
├── recommendations
├── createdAt
└── updatedAt
```

## Disease

```text
Disease
├── _id
├── name
├── crop
├── description
├── symptoms
├── riskFactors
├── prevention
├── management
└── createdAt
```

---

# 34. Recommended Next.js Project Structure

```text
agriguard-ai/
│
├── app/
│   ├── (auth)/
│   │   ├── login/
│   │   └── register/
│   │
│   ├── dashboard/
│   │
│   ├── farms/
│   │
│   ├── crops/
│   │
│   ├── scan/
│   │
│   ├── diagnosis/
│   │
│   ├── history/
│   │
│   ├── admin/
│   │
│   └── api/
│       ├── auth/
│       ├── farms/
│       ├── crops/
│       ├── diagnosis/
│       ├── diseases/
│       └── weather/
│
├── components/
│   ├── dashboard/
│   ├── farms/
│   ├── crops/
│   ├── diagnosis/
│   ├── charts/
│   └── ui/
│
├── lib/
│   ├── mongodb.ts
│   ├── auth.ts
│   ├── ml.ts
│   ├── weather.ts
│   └── validations.ts
│
├── models/
│   ├── User.ts
│   ├── Farm.ts
│   ├── Crop.ts
│   ├── Diagnosis.ts
│   └── Disease.ts
│
├── services/
│   ├── diagnosis.service.ts
│   ├── weather.service.ts
│   └── ml.service.ts
│
├── types/
│
└── public/
```

---

# 35. ML Service Structure

Separate Python service:

```text
ml-service/
│
├── app/
│   ├── main.py
│   ├── model.py
│   ├── preprocessing.py
│   ├── predictor.py
│   └── schemas.py
│
├── models/
│   └── plant_disease_model.pt
│
├── training/
│   ├── train.py
│   ├── evaluate.py
│   └── preprocessing.py
│
├── requirements.txt
└── Dockerfile
```

---

# 36. Prediction API

The Python service could expose:

```text
POST /predict
```

Request:

```text
multipart/form-data

image = leaf.jpg
crop = tomato
```

Response:

```json
{
  "crop": "Tomato",
  "disease": "Early Blight",
  "confidence": 0.942,
  "status": "diseased"
}
```

---

# 37. Next.js Prediction Flow

The browser should NOT directly communicate with the ML server.

Use:

```text
Browser
   ↓
Next.js
   ↓
FastAPI
   ↓
ML Model
```

Why?

Because your Next.js server can:

* authenticate the user
* validate the request
* control access
* store the image
* call the ML service
* validate the ML response
* store the diagnosis
* return a clean response

This gives you a much cleaner architecture.

---

# 38. Complete Scan Flow

When the farmer clicks:

```text
[ Scan Crop ]
```

the following happens:

```text
1. User selects image
        ↓
2. Next.js validates image
        ↓
3. Image uploaded to storage
        ↓
4. Next.js sends image to FastAPI
        ↓
5. FastAPI preprocesses image
        ↓
6. ML model predicts disease
        ↓
7. FastAPI returns prediction
        ↓
8. Next.js validates result
        ↓
9. Next.js retrieves disease information
        ↓
10. Weather data is retrieved
        ↓
11. Risk engine calculates risk
        ↓
12. Diagnosis stored in MongoDB
        ↓
13. Result returned to frontend
        ↓
14. Result displayed to farmer
```

---

# 39. Final API Response

The frontend should receive something like:

```json
{
  "diagnosisId": "66abc123",
  "crop": {
    "name": "Tomato"
  },
  "prediction": {
    "disease": "Early Blight",
    "confidence": 94.2,
    "status": "diseased"
  },
  "severity": {
    "level": "MEDIUM",
    "score": 62
  },
  "diseaseInfo": {
    "description": "A fungal disease affecting tomato foliage.",
    "symptoms": [
      "Brown circular spots",
      "Yellowing leaves",
      "Concentric rings"
    ]
  },
  "management": {
    "immediateActions": [
      "Remove heavily infected leaves",
      "Improve plant airflow"
    ],
    "prevention": [
      "Avoid excessive leaf wetness",
      "Maintain adequate spacing"
    ]
  },
  "weather": {
    "temperature": 27,
    "humidity": 86,
    "rainfall": 18
  },
  "risk": {
    "score": 82,
    "level": "HIGH"
  }
}
```

---

# 40. Frontend Result

The UI should transform the API response into:

```text
┌─────────────────────────────────────────────┐
│              AI CROP ANALYSIS               │
├─────────────────────────────────────────────┤
│                                             │
│  [ LEAF IMAGE ]                             │
│                                             │
│  TOMATO                                     │
│                                             │
│  ⚠ EARLY BLIGHT                            │
│                                             │
│  AI Confidence                              │
│  ███████████████████░ 94.2%                 │
│                                             │
│  Severity                                   │
│  ● MEDIUM                                   │
│                                             │
│  ─────────────────────────────────────────  │
│                                             │
│  DISEASE INFORMATION                        │
│                                             │
│  Brown spots and yellowing may appear       │
│  on affected leaves.                        │
│                                             │
│  ─────────────────────────────────────────  │
│                                             │
│  MANAGEMENT                                 │
│                                             │
│  ✓ Remove affected leaves                   │
│  ✓ Improve airflow                          │
│  ✓ Avoid excessive leaf moisture            │
│                                             │
│  ─────────────────────────────────────────  │
│                                             │
│  CURRENT DISEASE RISK                       │
│                                             │
│  ████████████████░░ 82%                     │
│                                             │
│  HIGH                                       │
│                                             │
│  Humidity: 86%                              │
│  Temperature: 27°C                          │
│                                             │
│  ⚠ Inspect your crop within 24 hours.      │
│                                             │
│  [ View History ]    [ Scan Another ]       │
└─────────────────────────────────────────────┘
```

---

# 41. Healthy Plant Output

The system must also properly handle healthy plants.

Example:

```text
┌───────────────────────────────────────┐
│          CROP ANALYSIS                │
├───────────────────────────────────────┤
│                                       │
│  TOMATO                               │
│                                       │
│  ✓ HEALTHY                            │
│                                       │
│  AI Confidence: 97.1%                 │
│                                       │
│  No visible disease detected.         │
│                                       │
│  Recommendations:                     │
│                                       │
│  ✓ Continue regular monitoring        │
│  ✓ Maintain proper irrigation         │
│  ✓ Monitor weather conditions         │
│                                       │
│  [ Save Result ]                      │
└───────────────────────────────────────┘
```

---

# 42. Low-Confidence Output

This is extremely important.

Suppose:

```text
Healthy: 31%
Early Blight: 36%
Late Blight: 33%
```

The system should NOT confidently claim:

> Early Blight detected.

Instead:

```text
⚠ LOW CONFIDENCE

The AI could not confidently identify
a disease from this image.

Confidence: 36%

Please:
• Capture a clearer image.
• Ensure the leaf is visible.
• Avoid blurry or dark images.

For important decisions, consult
an agricultural expert.
```

This makes the system more responsible and technically credible.

---

# 43. Image Quality Validation

Before calling the ML model, check:

```text
Is image readable?
Is image too dark?
Is image blurry?
Is leaf visible?
Is image supported?
```

If the image quality is poor:

```text
Image Quality Too Low

Please capture another image.

Tips:
✓ Use natural lighting
✓ Keep the leaf in focus
✓ Fill most of the frame
✓ Avoid multiple overlapping leaves
```

This can significantly improve real-world usability.

---

# 44. Notifications

The system can send notifications for:

```text
Disease detected
        ↓
High severity
        ↓
High weather risk
        ↓
Regional outbreak
```

Example:

```text
⚠️ Crop Health Alert

High disease risk detected for
your tomato crop.

Risk: 82%

Open AgriGuard AI to view details.
```

---

# 45. Security Requirements

Because this is a full-stack application, implement:

* Password hashing.
* Authentication.
* Authorization.
* Input validation.
* File-type validation.
* File-size limits.
* Rate limiting.
* Secure HTTP headers.
* Environment variables.
* MongoDB access restrictions.
* Server-side authorization checks.

Never expose:

```text
MONGODB_URI
JWT_SECRET
ML_SERVICE_SECRET
WEATHER_API_KEY
```

to the browser.

---

# 46. Privacy

Farm/location data can be sensitive.

The application should:

* Collect only required information.
* Clearly communicate location usage.
* Avoid exposing individual farmer locations publicly.
* Aggregate location data for regional analytics.
* Restrict admin access.

---

# 47. Non-Functional Requirements

## Performance

Prediction results should ideally return within a few seconds under normal conditions.

## Scalability

The application should allow:

```text
10 users
     ↓
100 users
     ↓
1,000 users
```

without redesigning the entire architecture.

## Reliability

If the ML service is unavailable:

```text
ML Service Unavailable

We couldn't analyze your image right now.

Please try again later.
```

The application must not crash.

---

# 48. Error Handling

Possible errors:

### Invalid image

```text
Please upload a valid crop image.
```

### ML unavailable

```text
AI analysis is temporarily unavailable.
```

### Weather unavailable

```text
Weather information is temporarily unavailable.
```

The diagnosis should still be usable even if weather data fails.

---

# 49. MVP Definition

For the first submission, build only:

```text
✓ Registration/Login
✓ Dashboard
✓ Farm creation
✓ Crop creation
✓ Image upload
✓ ML prediction
✓ Confidence score
✓ Disease information
✓ Management recommendations
✓ Diagnosis history
✓ MongoDB persistence
```

This is enough for a strong working project.

---

# 50. Advanced Version

After MVP:

```text
✓ Weather integration
✓ Disease risk prediction
✓ Notifications
✓ Crop health score
✓ Admin dashboard
✓ Regional disease analytics
✓ Heatmaps
✓ Multilingual UI
✓ Voice assistant
✓ Mobile application
✓ Offline inference
```

---

# 51. Recommended Development Phases

## Phase 1 — Planning

* Finalize supported crops.
* Finalize disease classes.
* Select dataset.
* Design UI.
* Design MongoDB schemas.
* Design architecture.

## Phase 2 — Next.js Foundation

Build:

* Authentication.
* Dashboard.
* MongoDB connection.
* User model.
* Farm model.
* Crop model.

## Phase 3 — ML

Build:

* Dataset preprocessing.
* Model training.
* Evaluation.
* Model export.
* FastAPI prediction service.

## Phase 4 — Integration

Connect:

```text
Next.js → FastAPI → ML Model
```

Then save results to MongoDB.

## Phase 5 — Management

Add:

* Disease information.
* Recommendations.
* Severity.
* History.

## Phase 6 — Weather

Add:

* Weather API.
* Risk calculation.
* Risk dashboard.

## Phase 7 — Admin

Add:

* User statistics.
* Disease statistics.
* Analytics.

## Phase 8 — Deployment

Deploy:

```text
Next.js → Vercel
MongoDB → MongoDB Atlas
FastAPI → Cloud service
Model → ML service
```

---

# 52. Final User Journey

The final demonstration should look like this:

```text
                    START
                      │
                      ▼
                 Login/Register
                      │
                      ▼
                 Farmer Dashboard
                      │
                      ▼
                   My Farm
                      │
                      ▼
                  Select Crop
                      │
                      ▼
                 Scan Crop 📷
                      │
                      ▼
                Upload Leaf Image
                      │
                      ▼
               Image Validation
                      │
                      ▼
                 AI Analysis
                      │
                      ▼
             Disease Prediction
                      │
              ┌───────┴───────┐
              │               │
          Healthy          Diseased
              │               │
              │               ▼
              │        Severity Analysis
              │               │
              │               ▼
              │        Management Advice
              │               │
              └───────┬───────┘
                      │
                      ▼
                Weather Analysis
                      │
                      ▼
                 Disease Risk
                      │
                      ▼
                Save Diagnosis
                      │
                      ▼
                Show Dashboard
                      │
                      ▼
                  END
```

---

# 53. Example Complete Demonstration

A good final viva/demo could go like this:

### Step 1

Login as farmer.

### Step 2

Create:

```text
Farm: Omer Farm
Location: Hyderabad
Area: 2.5 acres
```

### Step 3

Add:

```text
Crop: Tomato
```

### Step 4

Click:

```text
Scan Crop
```

### Step 5

Upload leaf image.

### Step 6

AI returns:

```text
Tomato Early Blight
Confidence: 94.2%
```

### Step 7

System displays:

```text
Severity: Medium
```

### Step 8

System retrieves:

```text
Symptoms
Management
Prevention
```

### Step 9

Weather API returns:

```text
Temperature: 27°C
Humidity: 86%
Rainfall: High
```

### Step 10

Risk engine returns:

```text
Disease Risk: HIGH
Score: 82%
```

### Step 11

System stores the diagnosis.

### Step 12

Dashboard updates:

```text
Total Scans: 1

Diseases Detected: 1

Tomato Health: 72%
```

This is a complete end-to-end demonstration.

---

# 54. What Makes This Different From a Basic ML Project?

A basic student project:

```text
Image
 ↓
CNN
 ↓
Disease
```

AgriGuard AI:

```text
Image
 ↓
Image Quality Validation
 ↓
ML Disease Detection
 ↓
Confidence
 ↓
Severity
 ↓
Disease Knowledge Base
 ↓
Management Recommendations
 ↓
Weather Analysis
 ↓
Risk Prediction
 ↓
Notifications
 ↓
Historical Analytics
 ↓
Farmer Dashboard
 ↓
Regional Analytics
```

The second architecture demonstrates significantly more engineering.

---

# 55. Project Success Criteria

The project should be considered successful if:

1. A registered user can create a farm.
2. A user can register a crop.
3. A user can upload a crop image.
4. The ML service successfully analyzes the image.
5. The system returns a disease prediction.
6. The system displays confidence.
7. Disease information is displayed.
8. Management recommendations are displayed.
9. The diagnosis is saved in MongoDB.
10. The farmer can view previous diagnoses.
11. Weather information can be retrieved.
12. Disease risk can be calculated.
13. The dashboard displays crop health information.
14. Invalid or low-quality images are handled safely.
15. ML service failures do not crash the application.

---

# 56. Important Limitations

AgriGuard AI should explicitly state:

* AI predictions depend on training data.
* Poor image quality can reduce accuracy.
* The system may not recognize diseases outside supported classes.
* Environmental conditions can affect disease symptoms.
* Disease recommendations should be treated as informational.
* The system is not a replacement for professional agricultural diagnosis.
* The risk score is a prototype decision-support metric unless scientifically validated.

Being honest about limitations makes the project more credible.

---

# 57. Future Scope

Future versions could include:

### Multilingual Support

```text
English
Hindi
Telugu
Tamil
Kannada
Marathi
```

### Voice Interface

```text
Farmer:
"My tomato leaves are turning brown."

AI:
"Please upload a clear image of the affected leaf."
```

### Offline AI

Run a lightweight model directly on a mobile device.

### Expert Verification

```text
AI Prediction
      ↓
Low Confidence
      ↓
Agricultural Expert
      ↓
Verified Diagnosis
```

### Regional Disease Prediction

Use anonymized aggregated data to identify disease trends.

### Yield Prediction

Combine:

```text
Crop
Weather
Disease
Soil
Historical Data
```

to estimate potential yield.

### IoT Integration

Future sensors could provide:

```text
Temperature
Humidity
Soil Moisture
pH
Leaf Wetness
```

The system could then combine sensor data with image-based AI.

---

# 58. Final System

The final AgriGuard AI platform should therefore be understood as:

```text
                 AGRIGUARD AI
                      │
        ┌─────────────┼──────────────┐
        │             │              │
        ▼             ▼              ▼
    FARMER APP     AI ENGINE      ADMIN
        │             │              │
        │             ▼              │
        │       Disease Detection    │
        │       Confidence           │
        │       Severity             │
        │             │              │
        └─────────────┼──────────────┘
                      │
              ┌───────┴────────┐
              ▼                ▼
          MongoDB          Weather API
              │                │
              └───────┬────────┘
                      ▼
                Risk Engine
                      │
                      ▼
                 Notifications
                      │
                      ▼
                 Analytics
```

## Core MVP

```text
Next.js
+
TypeScript
+
MongoDB
+
Python
+
FastAPI
+
PyTorch/TensorFlow
+
Plant Disease Dataset
```

## Final Product

**AgriGuard AI — an AI-assisted crop health platform that detects potential crop diseases from leaf images and provides disease management, weather-based risk analysis, historical tracking, and crop-health insights.**
