# Identifikasi Pergerakan dan Peramalan Saham TLKM Menggunakan ARIMA

## Deskripsi
Proyek ini menganalisis pergerakan harga saham Telkom Indonesia (TLKM) dan melakukan peramalan harga penutupan menggunakan metode ARIMA. Dataset diambil dari Yahoo Finance mulai 1 Januari 2020 hingga 26 Juli 2024.

## Data
Data yang digunakan mencakup harga pembukaan, tertinggi, terendah, penutupan, volume, dan adjusted close saham TLKM. Data diperoleh melalui library `yfinance`.

## Tahapan Analisis

### 1. Cek Stasioneritas
- Uji **ADF** dilakukan untuk memeriksa apakah data stasioner.
- Hasil: p-value = 0.34 → data tidak stasioner.
- Lakukan **differencing** 1 kali → data menjadi stasioner (p-value < 0.05).

### 2. Analisis Autokorelasi
- Plot **ACF** dan **PACF** sebelum dan sesudah differencing.
- Digunakan untuk menentukan ordo ARIMA secara manual.

### 3. Penentuan Model ARIMA
- **Manual:** ARIMA(1,1,1)
- **Otomatis:** Menggunakan `pmdarima.auto_arima` → ARIMA(5,1,0)
- Model dibandingkan berdasarkan AIC untuk memilih yang terbaik.

### 4. Fitting Model
- Fitting model ARIMA menggunakan `statsmodels.tsa.arima.model.ARIMA`.
- Model 1: ARIMA(1,1,1)
- Model 2: ARIMA(5,1,0)

### 5. Forecasting
- Data dibagi menjadi training (80%) dan testing (20%).
- Prediksi dilakukan pada data testing menggunakan model ARIMA(1,1,1).
- Hasil prediksi dibandingkan dengan data aktual.
- Visualisasi hasil menggunakan matplotlib.

## Hasil
- Model ARIMA(1,1,1) menangkap tren jangka pendek dengan baik.
- Model auto_arima memilih ARIMA(5,1,0) berdasarkan AIC, memberikan model lebih kompleks.
- Plot aktual vs prediksi menunjukkan pergerakan harga saham TLKM.

## Library yang Digunakan
- `yfinance` → untuk download data saham.
- `pandas` → manipulasi data.
- `matplotlib` → visualisasi.
- `statsmodels` → fitting model ARIMA.
- `pmdarima` → auto_arima.
