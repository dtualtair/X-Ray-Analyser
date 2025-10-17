# X-Ray Analyser

**X-Ray Analyser** is a web-based application that leverages deep learning for automated analysis and captioning of X-ray images. It provides a user-friendly interface for uploading medical X-rays, processing them through an AI model, and generating diagnostic descriptions and highlight annotations to assist radiologists and healthcare professionals.

---

## 🎯 Project Overview

Modern radiology workflows face increasing demand and potential for diagnostic delays. X-Ray Analyser aims to streamline this process by:  
- Automatically detecting anomalies in X-ray images using a CNN-based model.  
- Generating detailed textual reports via an integrated NLP module.  
- Highlighting critical regions with bounding boxes for rapid triage.  
- Prioritizing urgent cases based on severity scoring.

This end-to-end solution accelerates diagnosis, reduces human error, and supports clinical decision-making.

---

## ✨ Key Features

- **Image Upload & Preview**: Intuitive drag-and-drop or file selector for X-ray images (PNG, JPG, DICOM).  
- **Deep Learning Analysis**: CNN-based detection of fractures, infections, and other anomalies.  
- **Report Generation**: NLP-driven summarization of findings with medical terminology.  
- **Bounding Box Annotations**: Visual markers on detected regions of interest.  
- **Severity Scoring & Prioritization**: Assigns urgency levels to facilitate case triage.  
- **Downloadable Reports**: Export PDF reports containing images, annotations, and text summaries.  
- **REST API**: Programmatic access to upload images and retrieve analysis results.  

---

## 🏗️ Architecture & Technologies

| Component                | Technology               |
|--------------------------|--------------------------|
| **Backend**              | Python, Flask, FastAPI   |
| **Frontend**             | React, Next.js, TypeScript |
| **Deep Learning**        | PyTorch, TensorFlow      |
| **Model Storage**        | ONNX for cross-platform  |
| **Database**             | PostgreSQL, MongoDB      |
| **Containerization**     | Docker, Docker Compose   |
| **Deployment**           | AWS ECS / Kubernetes     |


### Workflow Diagram

```
User Upload → Frontend UI → Backend API → Image Preprocessing → DL Model Inference → NLP Module → Result Assembly → Frontend Display & Report Export
```

---

## 🚀 Getting Started

### Prerequisites

- Node.js 16.x or higher  
- Python 3.8 or higher  
- Docker & Docker Compose  
- Git

### Installation

1. **Clone the repository**  
```bash
git clone https://github.com/dtualtair/X-Ray-Analyser.git
cd X-Ray-Analyser
```

2. **Backend Setup**  
```bash
cd backend
python -m venv venv
source venv/bin/activate    # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

3. **Frontend Setup**  
```bash
cd ../frontend
npm install
```

4. **Environment Variables**  
Create `.env` files in both `backend` and `frontend` with the following variables:  
```env
# Backend (.env)
MODEL_PATH=path/to/model.onnx
DATABASE_URL=postgresql://user:pass@localhost:5432/xray
SECRET_KEY=your_secret_key

# Frontend (.env.local)
NEXT_PUBLIC_API_URL=http://localhost:8000/api
```

5. **Run with Docker Compose**  
```bash
docker-compose up --build
```
This will launch:
- Backend API on `http://localhost:8000`
- Frontend UI on `http://localhost:3000`
- Database services

---

## 💡 Usage Examples

### Upload & Analyse via UI  
1. Navigate to `http://localhost:3000`  
2. Drag and drop an X-ray image or click to select  
3. Click **Analyse**  
4. View bounding boxes and generated report  
5. Download PDF summary

### API Endpoints

- `POST /api/analyse` – Upload X-ray image (`multipart/form-data`).  
  - **Request**: Form field `file` with image  
  - **Response**: JSON with `annotations`, `report`, `severity_score`

- `GET /api/models` – List available AI models  
- `POST /api/models/select` – Switch active model (`model_name`)

---

## 🧠 Model & Training

- **Backbone**: ResNet50 / EfficientNet for feature extraction  
- **Detection Head**: Faster R-CNN for bounding box proposals  
- **Report Generator**: Transformer-based encoder-decoder architecture  
- **Training Data**: Public chest X-ray datasets (e.g., MIMIC-CXR) and custom labeled sets  
- **Evaluation Metrics**: mAP for detection, BLEU/ROUGE for report quality

---

## 🔧 Configuration

All settings can be adjusted in `config.yaml` (backend) and `next.config.js` (frontend). Key parameters include:

- **MODEL_CONFIG**: Path and inference parameters  
- **DB_CONFIG**: Host, port, credentials  
- **API_CONFIG**: Rate limits, timeout settings

---
**Made with ❤️ by DTU Altair**
