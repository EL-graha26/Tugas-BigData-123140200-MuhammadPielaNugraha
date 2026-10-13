# Eksplorasi Mandiri Mahadata (IF25-40402): Replikasi Parsial Peramalan Beban dengan Apache Spark

Replikasi parsial artikel: Ali El-Sayed Ali, H., Alham, M. H., & Ibrahim, D. K. (2024).
*Big data resolving using Apache Spark for load forecasting and demand response in smart grid:
A case study of Low Carbon London Project.* Journal of Big Data, 11, 59.
https://doi.org/10.1186/s40537-024-00909-6

Nama : Muhammad Piela Nugraha

NIM : 123140200

## Cakupan
Replikasi parsial pada subset data (Block 0 dari proyek Low Carbon London), mode lokal Spark:
analitik deskriptif (Spark SQL), regresi polinomial (Plain, Lasso, Ridge, Elastic net) dan
Decision Tree Regression (Spark MLlib), dibandingkan dengan Tabel 6 artikel (kolom *Block #0*).

## Struktur
```
src/pipeline.py              pipeline utama (Spark SQL + MLlib)
src/make_synthetic_data.py   data sintetis untuk uji kode saja (bukan hasil eksperimen)
data/README.md               cara mengunduh dataset
results/                     keluaran (CSV, gambar, environment.txt)
laporan/template_laporan.md  kerangka laporan
```

## Menyiapkan lingkungan
Butuh Java 11/17/21 dan Python 3.9+.
```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

## Menjalankan
1. Unduh data sesuai `data/README.md` ke `data/lcl/`.
2. Jalankan:
```bash
python src/pipeline.py --data-dir data/lcl --blocks 0 --out-dir results
```
Opsi: `--blocks 0,1,2` atau `all`, `--seed`, `--poly-degree`, `--cv-folds`, `--driver-memory`.

Keluaran di `results/`: `model_results.csv` (R2, MAE, MSE, RMSE, waktu fit/test),
`desc_*.csv`, `fig_*.png`, `environment.txt` (versi dan parameter).

## Asumsi dan perbedaan terhadap artikel
- Artikel tidak menyebut cara pembagian data; di sini acak 80/20 dengan seed tetap.
- Fitur suhu memakai `apparentTemperature` (artikel memilihnya karena korelasi tertinggi).
- Polinomial derajat 2 (artikel tidak menyebut derajat), fitur jam di-one-hot.
- Grid tuning dan jumlah fold CV ditentukan sendiri (artikel tidak merinci).
- Klaster artikel: GCP Dataproc 1 master + 3 worker (2 vCPU, 7,5 GB RAM). Di sini: Spark mode lokal.

## Pernyataan penggunaan AI
Kerangka kode dan templat laporan dibantu Claude (Anthropic). Isi bagian ini sesuai
bagian mana yang benar-benar dibantu, dan pastikan kamu memahami seluruh kode.
