# 🛡️ PhishNet-AI - Malicious URL Detection System

**AI-Powered Real-Time Phishing Detection with 96% Accuracy**

## 🌟 Overview

PhishNet-AI is a comprehensive malicious URL detection system that protects users from phishing, malware, and defacement attacks using a hybrid machine learning approach.

**Key Achievement:** 96% accuracy on 651,191 URLs using LightGBM with 5,017 engineered features.

## 🏆 Achievements

🥇 **Winner:** Project Exhibition 2025-26, Dept of AI & DS, KSSEM  
🥉 **3rd Place:** IEEE National Level Project Exhibition at CMRIT

## ✨ Features

- ✅ Real-time URL scanning with ML-powered detection
- ✅ Chrome Extension with hover detection on any webpage
- ✅ React Frontend for interactive URL analysis
- ✅ FastAPI Backend serving predictions via REST API
- ✅ Hybrid 3-layer detection: Whitelist → Rules → ML Model

## 🔧 Technical Architecture

### Hybrid Detection Pipeline

1. **Layer 1: Whitelist** - Instant approval for known safe domains (Google, Facebook, etc.)
2. **Layer 2: Rules** - Typosquatting detection, suspicious TLD checking
3. **Layer 3: ML Model** - LightGBM with 5,017 features (17 manual + 5,000 TF-IDF)

## 🚀 Installation

### Prerequisites

- Python 3.8+
- Node.js 16+
- Google Chrome
- Homebrew (Mac only)

### 1. Clone Repository

```bash
git clone https://github.com/lavanya5454/phishing_website.git
cd phishing_website/PhishNet-AI
```

### 2. Backend Setup

```bash
cd backend
python3 -m venv .venv
source .venv/bin/activate  # Mac/Linux
# On Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

**Install libomp for LightGBM (Mac only):**

```bash
brew install libomp
```

### 3. Frontend Setup

```bash
cd frontend
npm install
```

### 4. Chrome Extension Setup

1. Open `chrome://extensions/`
2. Enable **Developer mode**
3. Click **Load unpacked**
4. Select the `extension` folder

## 🎯 Usage

### Start Backend Server

```bash
cd backend
source .venv/bin/activate
uvicorn main:app --reload --host 127.0.0.1 --port 8000
```

### Start Frontend

```bash
cd frontend
npm run dev
```

**Frontend runs at:** http://localhost:5173

### Use Chrome Extension

1. Ensure backend is running on port 8000
2. Open any website in Chrome
3. Hover over any link
4. See instant safety tooltip:
   - ✅ Green = Safe
   - ⚠️ Yellow = Suspicious
   - 🚨 Red = Dangerous

## 🔌 API Usage

### Endpoint

```
POST http://127.0.0.1:8000/predict
```

### Request Body

```json
{
  "url": "https://example.com"
}
```

### Response

```json
{
  "is_safe": true,
  "prediction": "benign",
  "confidence": 0.95,
  "detection_method": "whitelist"
}
```

### Example cURL Command

```bash
curl -X POST http://127.0.0.1:8000/predict \
  -H "Content-Type: application/json" \
  -d '{"url":"https://google.com"}'
```

## 📁 Project Structure

```
PhishNet-AI/
│
├── backend/
│   ├── main.py                      # FastAPI server
│   ├── malicious_url_detector.pkl   # Trained model
│   └── requirements.txt             # Python dependencies
│
├── frontend/
│   ├── src/                         # React app source
│   └── package.json                 # NPM dependencies
│
├── extension/
│   ├── manifest.json                # Chrome extension config
│   ├── content.js                   # Hover detection script
│   ├── popup.js                     # Extension popup logic
│   └── background.js                # Background service
│
└── requirements.txt                 # Project dependencies
```

## 📊 Model Performance

- **Accuracy:** 96%
- **Dataset:** 651,191 URLs
- **Model:** LightGBM Classifier
- **Features:** 5,017 (17 manual + 5,000 TF-IDF character n-grams)
- **Classes:** Benign, Phishing, Malware, Defacement

## 🐛 Troubleshooting

### Backend not responding

**Check if backend is running:**

```bash
lsof -i :8000
```

**Start backend:**

```bash
cd backend
uvicorn main:app --reload --host 127.0.0.1 --port 8000
```

### Extension not detecting links

- Reload extension at `chrome://extensions/`
- Check that backend is running on port 8000
- Verify console logs in Chrome DevTools

### Extension doesn't work in WhatsApp Desktop

Use WhatsApp Web in Chrome instead: https://web.whatsapp.com

### LightGBM installation issues (Mac)

```bash
brew install libomp
```

## 🔬 Technology Stack

- **Backend:** FastAPI, LightGBM, scikit-learn, uvicorn
- **Frontend:** React, Vite, Tailwind CSS
- **Extension:** Chrome Manifest V3, JavaScript
- **ML:** Python, NumPy, Pandas, TF-IDF vectorization

## 👥 Author

**Lavanya**

- GitHub: [@lavanya5454](https://github.com/lavanya5454)
- Email: lavanya7055@gmail.com

## 📄 License

MIT License

---

