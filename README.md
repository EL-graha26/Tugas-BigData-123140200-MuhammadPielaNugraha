# Eksplorasi Mandiri Mahadata (IF25-40402): Replikasi Parsial Peramalan Beban dengan Apache Spark

**Artikel acuan:** Ali, H. A. E.-S., Alham, M. H., & Ibrahim, D. K. (2024). *Big data resolving using Apache Spark for load forecasting and demand response in smart grid: A case study of Low Carbon London Project.* Journal of Big Data. https://doi.org/10.1186/s40537-024-00909-6

**Tingkat replikasi:** parsial + perluasan (subset data, mode lokal Spark, ditambah uji pengaruh jumlah *partition*).

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


