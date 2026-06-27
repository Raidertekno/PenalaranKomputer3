# Sistem Case-Based Reasoning (CBR) untuk Analisis Putusan Pengadilan

## Deskripsi Proyek

Proyek ini dibuat untuk memenuhi tugas mata kuliah Penalaran Komputer dengan menerapkan metode **Case-Based Reasoning (CBR)** pada data putusan pengadilan.

Data yang digunakan berasal dari **Direktori Putusan Mahkamah Agung Republik Indonesia**. Sistem bekerja dengan memanfaatkan kasus-kasus lama untuk membantu menemukan kasus yang mirip dan menghasilkan solusi berdasarkan putusan yang pernah ada.

Tahapan yang digunakan mengikuti siklus CBR, yaitu:

1. Membangun Case Base  
2. Case Representation  
3. Case Retrieval  
4. Case Solution Reuse  
5. Model Evaluation  

Domain perkara yang digunakan pada proyek ini:

**Pidana Umum — Pemerasan dan Pengancaman**

---

## Struktur Repository

```text
CBR-Putusan/

data/
│
├── pdf/
├── raw/
├── processed/
│   ├── clean_text/
│   └── cases.csv
│
├── eval/
│   ├── queries.json
│   ├── retrieval_metrics.csv
│   ├── prediction_metrics.csv
│   ├── retrieval_detail.csv
│   └── prediction_detail.csv
│
├── results/
│   └── predictions.csv
│
└── logs/

notebooks/
│
├── 01_case_base.ipynb
├── 02_case_representation.ipynb
├── 03_retrieval.ipynb
├── 04_reuse.ipynb
└── 05_evaluation.ipynb

requirements.txt
README.md
```

---

## Dataset

Sumber data diperoleh dari:

Direktori Putusan Mahkamah Agung Republik Indonesia

Ketentuan data yang digunakan:

- Minimal 30 dokumen putusan
- Format PDF
- Seluruh dokumen dikonversi menjadi teks sebelum diproses

---

## Instalasi

Clone repository:

```bash
git clone https://github.com/USERNAME/NAMA_REPOSITORY.git
```

Masuk ke folder project:

```bash
cd Penalarankomputer3.ipynb
```

Install library yang dibutuhkan:

```bash
pip install -r requirements.txt
```

---

## Library yang Digunakan

Isi file `requirements.txt`:

```txt
pymupdf
pandas
numpy
scikit-learn
matplotlib
nltk
```

Install:

```bash
pip install -r requirements.txt
```

---

## Cara Menjalankan Project

Notebook dijalankan secara berurutan.

### Tahap 1 — Membangun Case Base

Menyiapkan data putusan.

Proses:
- Konversi PDF ke TXT
- Pembersihan teks
- Validasi hasil ekstraksi

Output:

```text
/data/raw/
/data/processed/clean_text/
```

---

### Tahap 2 — Case Representation

Membentuk struktur data kasus.

Proses:
- Ekstraksi metadata
- Ekstraksi ringkasan fakta
- Ekstraksi argumen hukum
- Feature engineering

Output:

```text
/data/processed/cases.csv
```

Kolom utama:

- case_id
- no_perkara
- tanggal
- jenis_perkara
- terdakwa
- pasal
- ringkasan_fakta
- argumen_hukum
- amar_putusan

---

### Tahap 3 — Case Retrieval

Mencari kasus lama yang paling mirip dengan kasus baru.

Metode:
- TF-IDF
- Cosine Similarity

Output:

```text
/data/eval/queries.json
```

---

### Tahap 4 — Case Solution Reuse

Menggunakan hasil retrieval untuk menghasilkan solusi.

Metode:
- Top-K Similar Cases
- Weighted Similarity

Output:

```text
/data/results/predictions.csv
```

---

### Tahap 5 — Evaluasi Model

Mengukur performa retrieval dan prediksi.

Metrik evaluasi:
- Accuracy
- Precision
- Recall
- F1 Score

Output:

```text
/data/eval/retrieval_metrics.csv
/data/eval/prediction_metrics.csv
```

Tambahan:
- Error analysis
- Visualisasi hasil evaluasi

---

## Contoh Pengujian

Contoh query:

```text
pemerasan disertai ancaman
```

Hasil yang dihasilkan:

- Kasus dengan kemiripan tertinggi
- Prediksi solusi berdasarkan putusan sebelumnya

---

## Ringkasan Metode

Retrieval:
- TF-IDF
- Cosine Similarity

Reuse:
- Weighted Similarity

Evaluasi:
- Accuracy
- Precision
- Recall
- F1-score

---

## Penulis
Adriansyah Pratama  202310370311481
M. Raihan Abdi      202310370311474
Tugas Mata Kuliah Penalaran Komputer  
Fakultas Teknik  
Universitas Muhammadiyah Malang
