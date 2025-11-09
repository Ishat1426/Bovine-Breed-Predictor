# 🐄 Cattle Breed Predictor

An AI-powered cattle breed identification system using computer vision and machine learning. This application predicts cattle breeds from images using a trained EfficientNet model and provides visual explanations through Grad-CAM heatmaps.

## ✨ Features

- **Multi-Breed Classification**: Identifies 5 cattle breeds (Gir, Holstein-Friesian, Murrah, Jersey, Nili Ravi)
- **Visual Explanations**: Grad-CAM heatmaps show which image regions influenced predictions
- **Multi-Modal Analysis**: Combines image analysis with cattle traits (milk, weight, lactation, disease scores)
- **Crossbreed Detection**: Flags potential crossbreeds when confidence is low
- **Silhouette Overlays**: Visual breed comparison with silhouette templates
- **Feedback System**: Collects user feedback to improve model performance
- **REST API**: Easy integration with web applications

## 🐮 Supported Breeds

| Breed | Code | Characteristics |
|-------|------|----------------|
| Gir | `Gir` | Indigenous Indian breed, heat-resistant |
| Holstein-Friesian | `H_F` | High milk production, black and white |
| Murrah | `Murrah` | Buffalo breed, excellent for dairy |
| Jersey | `Jersey` | Small size, high butterfat content |
| Nili Ravi | `nili_ravi` | Buffalo breed, good milk yield |

## 🚀 Installation

### Prerequisites
- Python 3.8+
- CUDA-compatible GPU (optional, for faster inference)
- 4GB+ RAM

### Setup
```bash
# Clone the repository
git clone <repository-url>
cd Breed-Predictor

# Install dependencies
pip install -r requirements.txt

# Download or train the model (see Training section)
# Ensure best_model.pth is in the project root
```

### Dependencies
- **Flask**: Web framework for API
- **PyTorch**: Deep learning framework
- **torchvision**: Computer vision utilities
- **OpenCV**: Image processing
- **Pillow**: Image handling
- **NumPy**: Numerical computations
- **Flask-CORS**: Cross-origin resource sharing

## ⚡ Quick Start

### 1. Start the Server
```bash
python app.py
```
The server will start at `http://localhost:5000`

### 2. Test with API
```bash
curl -X POST \
  -F "image=@path/to/cattle_image.jpg" \
  -F "milk=15.0" \
  -F "weight=450" \
  -F "lact=10" \
  -F "disease=2" \
  http://localhost:5000/predict
```

## 📖 API Documentation

### POST `/predict`
Predicts cattle breed from uploaded image and traits.

**Request:**
- **Form Data:**
  - `image`: Image file (JPG/PNG)
  - `milk`: Milk production (liters/day, optional)
  - `weight`: Weight in kg (optional)
  - `lact`: Lactation period (optional)
  - `disease`: Disease resistance score (optional)

**Response:**
```json
{
  "top3": [
    ["Jersey", 0.85],
    ["Gir", 0.12],
    ["H_F", 0.03]
  ],
  "final_pred": "Jersey",
  "cnn_conf": 0.85,
  "crossbreed_flag": false,
  "heatmap_url": "/static/results/image_20231109_heat.jpg",
  "silhouette_url": "/static/results/image_20231109_sil_overlay.jpg"
}
```

### POST `/feedback`
Submit user feedback for model improvement.

**Request:**
```json
{
  "image": "filename.jpg",
  "predicted_final": "Jersey",
  "action": "correct|incorrect",
  "scores": {"user_rating": 5}
}
```

## 🧠 Model Architecture

- **Base Model**: EfficientNet-B0
- **Input Size**: 224×224 pixels
- **Classes**: 5 cattle breeds
- **Training**: Transfer learning with data augmentation
- **Inference**: CPU/GPU/MPS support

### Model Performance
- **Validation Accuracy**: ~92%
- **Model Size**: 16MB
- **Inference Time**: ~200ms (CPU), ~50ms (GPU)

## 🔧 Training Your Own Model

### Data Preparation
```bash
# Organize your dataset:
dataset/
├── train/
│   ├── Gir/
│   ├── H_F/
│   ├── Murrah/
│   ├── Jersey/
│   └── nili_ravi/
├── val/
└── test/
```

### Training Pipeline
```bash
# 1. Remove duplicates
python src/data_processing/dedup.py

# 2. Split train/validation
python src/data_processing/split_train_val.py

# 3. Apply data augmentation
python src/data_processing/augmentation.py

# 4. Train the model
python src/training/train_cnn_final.py

# 5. Evaluate performance
python src/evaluation/evaluate_test.py
python src/evaluation/evaluate_test_with_mistakes.py
```

## 📊 Evaluation and Testing

### Basic Evaluation
```bash
python src/evaluation/evaluate_test.py
```

### Detailed Error Analysis
```bash
python src/evaluation/evaluate_test_with_mistakes.py
```

### Generate Visualizations
```bash
python src/utils/demo-fusion_gradcam.py
python src/utils/make_silhouettes.py
```

## 🌐 Web Interface

The application includes a modern, professional web interface:

- **Home**: Upload images and get predictions with visual explanations
- **Breed Database**: Browse supported cattle breeds and their characteristics
- **Documentation**: Complete API reference and usage examples
- **Support**: Help center with FAQ and system status

Access the web interface at `http://localhost:5000` after starting the server.

## 📁 Project Structure

```
Breed-Predictor/
├── app.py                      # Main Flask application
├── requirements.txt            # Python dependencies
├── README.md                  # This file
├── best_model.pth             # Trained model weights
├── breed_traits.csv           # Breed characteristics
├── templates/                 # HTML templates
├── static/                    # CSS and result images
└── src/                       # Organized source modules
    ├── data_processing/       # Data preparation
    ├── training/             # Model training
    ├── evaluation/           # Performance testing
    └── utils/                # Helper functions
```

See [PROJECT_STRUCTURE.md](PROJECT_STRUCTURE.md) for detailed module descriptions.

## 🔍 Features in Detail

### Grad-CAM Visualization
- Shows which parts of the image the model focuses on
- Helps understand model decision-making
- Useful for debugging and validation

### Crossbreed Detection
- Identifies potential hybrid animals
- Based on confidence thresholds and prediction uncertainty
- Flags low-confidence or ambiguous predictions

### Multi-Modal Analysis
- Combines visual features with numerical traits
- Supports milk production, weight, lactation, and health scores
- Improves prediction accuracy for edge cases

## 🚨 Important Notes

- Ensure your model file `best_model.pth` is in the project root
- The model expects images to be properly formatted (RGB, decent resolution)
- GPU support is automatically detected (CUDA/MPS)
- All prediction results are logged for analysis

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes following the project structure
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Support

For issues, questions, or contributions:
- Check the [Documentation](http://localhost:5000/documentation) page
- Visit the [Support Center](http://localhost:5000/support)
- Review the project structure in [PROJECT_STRUCTURE.md](PROJECT_STRUCTURE.md)

---
