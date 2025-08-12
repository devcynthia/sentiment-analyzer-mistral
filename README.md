# 😊 Sentiment Analyzer (Mistral)

**Created by**: Cynthia  
**Created on**: 2025-08-12  
**Purpose**: Learning project - AI sentiment analysis using Mistral model via Ollama

A simple AI application that uses the **Mistral model** via Ollama to classify the sentiment of text as Positive, Negative, or Neutral. Features a **FastAPI** backend and **Streamlit** frontend with an intuitive user interface.

## ✨ Features

### Backend (FastAPI)
- ✅ Clean sentiment analysis with standardized responses
- ✅ Input validation and sanitization (3-5,000 characters)
- ✅ Comprehensive error handling with meaningful messages
- ✅ Model fallback system for availability issues
- ✅ Health check endpoints with model discovery
- ✅ Request timeout handling and rate limiting
- ✅ OpenAPI documentation (auto-generated)

### Frontend (Streamlit)
- ✅ Modern, intuitive UI with real-time status monitoring
- ✅ Visual sentiment display with colors and emojis
- ✅ Example text samples for quick testing
- ✅ Character/word counting with validation
- ✅ Model selection (when multiple models available)
- ✅ Analysis confidence levels and detailed results
- ✅ Copy-to-clipboard functionality
- ✅ Built-in troubleshooting guide

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- [Ollama](https://ollama.com) installed and running

### 1. Clone and Setup
```bash
git clone https://github.com/devcynthia/school-of-ai-projects.git
cd school-of-ai-projects/sentiment-analyzer-mistral

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\\Scripts\\activate

# Install dependencies
pip install -r requirements.txt
```

### 2. Setup Ollama and Mistral Model
```bash
# Start Ollama service (if not already running)
ollama serve

# Download Mistral model
ollama pull mistral:7b-instruct
```

### 3. Start the Application

**Terminal 1 - Backend:**
```bash
cd backend
python main.py
# Server will run on http://localhost:8000
```

**Terminal 2 - Frontend:**
```bash
cd frontend  
streamlit run app.py
# UI will open in browser at http://localhost:8501
```

### 4. Using the Application
1. Open http://localhost:8501 in your browser
2. Check that the system status shows "✅ Backend service is running"
3. Enter text to analyze (3-5,000 characters)
4. Click "🔍 Analyze Sentiment"
5. Review the sentiment classification with confidence level

## 📁 Project Structure

```
sentiment-analyzer-mistral/
│
├── backend/
│   └── main.py              # FastAPI server with sentiment analysis
├── frontend/  
│   └── app.py               # Streamlit UI application
├── venv/                    # Virtual environment
├── requirements.txt         # Python dependencies
└── README.md               # This file
```

## 🎯 Sentiment Classifications

The system classifies text into three categories:

- **😊 Positive**: Happy, good, excellent, wonderful, amazing
- **😞 Negative**: Sad, bad, terrible, awful, horrible  
- **😐 Neutral**: Mixed, okay, average, unsure

## 🔧 Configuration

### Backend Configuration
Edit `backend/main.py` to modify:
- `OLLAMA_BASE_URL`: Ollama service URL (default: http://localhost:11434)
- `DEFAULT_MODEL`: Default model name (default: mistral:7b-instruct)
- Text length limits, request timeouts, model parameters

### Model Selection
The application automatically detects available models and provides fallback options:
- If specified model unavailable → uses first available model
- If no models available → shows helpful error message
- Supports any Ollama-compatible model

## 🛠️ API Documentation

### Backend Endpoints

**GET /** - Basic health check  
**GET /health** - Detailed system status including available models  
**POST /analyze/** - Main sentiment analysis endpoint

#### Analyze Endpoint
```bash
curl -X POST "http://localhost:8000/analyze/" \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -d "text=I love this product!&model=mistral:7b-instruct"
```

**Response:**
```json
{
  "sentiment": "Positive",
  "confidence": "high",
  "model_used": "mistral:7b-instruct",
  "input_text": "I love this product!",
  "input_length": 19,
  "raw_response": "Positive",
  "timestamp": "2025-08-12T10:30:00.123456",
  "status": "success"
}
```

## 🔍 Troubleshooting

### Common Issues

**❌ Backend service not available**
```bash
cd backend && python main.py
```

**❌ Ollama service not running**
```bash
ollama serve
```

**❌ No models available**
```bash
# Download Mistral model
ollama pull mistral:7b-instruct
# OR for smaller/faster model
ollama pull mistral
```

**❌ Model response timeout**
- Try shorter text input
- Check system resources (RAM/CPU)
- Restart Ollama service

**❌ Connection errors**
- Verify ports 8000 and 8501 are available
- Check firewall settings
- Ensure all services started in correct order

### Performance Tips
- **For speed**: Use shorter text inputs (< 500 characters)
- **For accuracy**: Use longer, more detailed text
- **Memory usage**: Monitor RAM with larger models
- **Response time**: Expect 5-15 seconds for analysis

## ⚠️ Important Notes

- **Privacy**: All processing happens locally on your machine
- **Resource usage**: Mistral models require 4GB+ RAM
- **Internet**: Only required for initial setup and model downloads
- **Security**: No data is sent to external services

## 🛡️ Security Features

- Input validation and sanitization
- Request rate limiting and timeout handling
- No external API calls during operation
- Local-only processing for data privacy
- Comprehensive error handling without exposing system details

## 📊 Performance Metrics

Typical performance on modern hardware:
- **Model loading**: 10-30 seconds initial startup
- **Analysis time**: 5-15 seconds per request
- **Memory usage**: ~4-6GB RAM for mistral:7b-instruct
- **Accuracy**: High for clear positive/negative sentiment, good for neutral

## 🤝 Contributing

This is a learning/demonstration project. Feel free to:
- Experiment with different models (llama2, gemma2, etc.)
- Modify the UI/UX design
- Add new features (batch processing, sentiment confidence scores)
- Optimize performance and accuracy

## 🎓 Learning Objectives

This project demonstrates:
- FastAPI backend development with AI integration
- Streamlit frontend with modern UI components
- Local AI model deployment using Ollama
- RESTful API design and error handling
- Real-time web application architecture
- Input validation and security best practices

---

*Created as a technical assessment/learning project. All code includes proper error handling, logging, and security considerations.*