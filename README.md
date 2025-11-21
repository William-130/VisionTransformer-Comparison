# Vision Transformer Comparison: Swin vs ViT

Proyek perbandingan performa dua model Vision Transformer (Swin Transformer dan ViT) pada dataset Indonesian Food Classification dengan 5 kelas.

## 📋 Deskripsi

Tugas eksplorasi ini membandingkan:

- **Swin Transformer**: Hierarchical transformer dengan shifted window attention
- **Vision Transformer (ViT)**: Pure transformer architecture untuk computer vision (ViT-Base/16)

Kedua model menggunakan pre-trained weights dari ImageNet dan di-fine-tune pada dataset Indonesian Food.

## 🗂️ Struktur Project

```
transformer_explore/
├── dataset/                   # Dataset Indonesian Food
│   ├── train.csv              # Label file
│   └── train/                 # Image files
├── src/                       # Source code
│   ├── data_preparation.py    # Data loading dan preprocessing
│   ├── train_swin.py          # Training Swin Transformer
│   ├── train_vit.py           # Training Vision Transformer (ViT)
│   ├── evaluate.py            # Evaluasi model dan metrics
│   └── visualize.py           # Visualisasi hasil
├── models/                    # Saved model weights
├── outputs/                   # Hasil eksperimen
│   ├── figures/              # Visualisasi dan plot
│   └── results/              # Metrics dan logs
├── requirements.txt           # Dependencies
└── README.md                 # Dokumentasi ini
```

## 🚀 Setup dan Instalasi

### 1. Buat Virtual Environment

```powershell
# Buat virtual environment
python -m venv venv

# Aktivasi virtual environment
.\venv\Scripts\Activate.ps1

# Jika ada error execution policy, jalankan:
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### 2. Install Dependencies

```powershell
pip install -r requirements.txt
```

### 3. Verifikasi Dataset

Pastikan struktur dataset sudah benar:

```
dataset/
├── train.csv          # File dengan kolom: filename, label
└── train/            # Folder berisi semua gambar
```

## 📊 Cara Menjalankan

### Step 1: Eksplorasi Data

```powershell
python src/data_preparation.py
```

Output:

- Distribusi kelas
- Sample visualisasi
- Statistik dataset

### Step 2: Training Swin Transformer

```powershell
python src/train_swin.py
```

Model yang digunakan: `swin_tiny_patch4_window7_224` (pre-trained ImageNet)

### Step 3: Training Vision Transformer (ViT)

```powershell
python src/train_vit.py
```

Model yang digunakan: `vit_base_patch16_224` (pre-trained ImageNet)

### Step 4: Evaluasi dan Perbandingan

```powershell
python src/evaluate.py
```

Output:

- Accuracy, Precision, Recall, F1-Score
- Confusion Matrix
- Inference Time
- Parameter Count

### Step 5: Visualisasi Hasil

```powershell
python src/visualize.py
```

Output:

- Learning curves
- Confusion matrices
- Comparison tables
- Sample predictions

## 📈 Metrik Evaluasi

Setiap model dievaluasi berdasarkan:

1. **Jumlah Parameter**

   - Total parameters
   - Trainable parameters
   - Model size (MB)

2. **Performance Metrics**

   - Accuracy
   - Precision (per-class & average)
   - Recall (per-class & average)
   - F1-Score (per-class & average)
   - Confusion Matrix

3. **Inference Time**
   - Average time per image (ms)
   - Throughput (images/second)
   - Total test set time

## ⚙️ Konfigurasi Training

### Hyperparameters

#### Swin Transformer:
- **Input Size**: 224x224
- **Batch Size**: 8
- **Epochs**: 10
- **Optimizer**: AdamW
- **Learning Rate**: 5e-6
- **Weight Decay**: 0.1
- **Scheduler**: CosineAnnealingLR

#### Vision Transformer (ViT):
- **Input Size**: 224x224
- **Batch Size**: 4
- **Epochs**: 10
- **Optimizer**: AdamW
- **Learning Rate**: 5e-5
- **Weight Decay**: 0.1
- **Scheduler**: CosineAnnealingLR

### Data Augmentation

- Random Horizontal Flip
- Random Rotation (±10°)
- Color Jitter
- Normalization (ImageNet stats)

## 💻 Hardware

Spesifikasi yang digunakan:

- GPU: NVIDIA GeForce RTX 3050 Laptop GPU (4GB)
- CPU: Intel Core i5-11400H
- RAM: 16 GB
- OS: Windows 11

## 📝 Hasil

Hasil lengkap tersimpan di folder `outputs/`:

- `outputs/figures/`: Semua visualisasi
- `outputs/results/`: Metrics dalam format CSV dan JSON
- `models/`: Model weights (best & last checkpoint)

## 🔍 Reproducibility

Untuk hasil yang reproducible:

- Random seed: 42 (set di semua script)
- Gunakan dependencies dari `requirements.txt`
- Jalankan dengan configuration yang sama

## � Hasil Eksperimen

### Model Performance Summary:

| Model | Parameters | Size | Accuracy | Precision | Recall | F1-Score | Inference Speed |
|-------|-----------|------|----------|-----------|--------|----------|-----------------|
| **Swin Transformer** | 27.5M | 105 MB | 97.75% | 97.74% | 97.74% | 97.73% | 1,754 img/s |
| **Vision Transformer (ViT)** | 85.8M | 327 MB | **98.65%** | 98.67% | 98.64% | 98.64% | 1,294 img/s |

### Key Findings:

- ✅ **ViT Base** mencapai akurasi tertinggi (98.65%)
- ✅ **Swin Transformer** 3x lebih ringan dan 35% lebih cepat
- ✅ Kedua model sangat baik untuk Indonesian Food Classification (>97% accuracy)
- ✅ Trade-off: ViT menang 0.9% akurasi, Swin unggul di efisiensi

## 📚 Referensi

1. **Vision Transformer (ViT)**: [Dosovitskiy et al., 2021] - An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale
2. **Swin Transformer**: [Liu et al., 2021] - Swin Transformer: Hierarchical Vision Transformer using Shifted Windows
3. **PyTorch Image Models (timm)**: https://github.com/huggingface/pytorch-image-models

## 👨‍🎓 Author

- **Nama**: William Chan
- **NIM**: 122140130
- **Mata Kuliah**: Deep Learning
- **Semester**: Ganjil 2025/2026

## 📄 License

Proyek ini dibuat untuk keperluan tugas akademik.
