---
title: Data Visualization dengan RStudio
date: 2025-01-20
external_link: https://adiprasetyo045.github.io/uas-data-visualization/
tags:
  - Data Visualization
  - RStudio
  - ggplot2
---

Proyek UAS ini bertujuan untuk membuat visualisasi data berdasarkan dataset yang diberikan, termasuk grafik univariat, bivariat, multivariat, dan interaktif. Visualisasi ini dirancang untuk mengeksplorasi pola, tren, dan wawasan penting dari data menggunakan ggplot2 di RStudio.

## Gambaran Proyek

Proyek ini berfokus pada analisis dataset UAS yang mencakup informasi tentang harapan hidup, pendapatan per kapita, populasi, dan rata-rata jumlah anak dari berbagai negara dan benua selama beberapa tahun. Outputnya adalah grafik yang membantu memahami distribusi data, hubungan antar variabel, dan tren historis.

## Data Preparation

### 1. Mengimpor Dataset
```r
# Memuat dataset
library(readxl)
file_path <- "Data UAS.xlsx"
df <- read_excel(file_path, sheet = "Data") %>%
  mutate(
    Benua = factor(Benua),
    Tahun = as.integer(Tahun)
  )

# Menampilkan beberapa baris pertama
head(df)
```

### 2. Statistik Deskriptif
```r
# Ringkasan statistik deskriptif
df_summary <- summary(df)
print(df_summary)
```

## Visualisasi Data

### 1. Grafik Univariat
#### Histogram: Distribusi Angka Harapan Hidup
```r
library(ggplot2)
ggplot(df, aes(x = Angka_Harapan_Hidup)) +
  geom_histogram(
    bins = 30, 
    fill = "#69b3a2", 
    color = "white", 
    alpha = 0.9
  ) +
  theme_minimal() +
  labs(
    title = "Distribusi Angka Harapan Hidup",
    x = "Angka Harapan Hidup",
    y = "Frekuensi"
  ) +
  theme(
    plot.title = element_text(hjust = 0.5, face = "bold", size = 14),
    axis.text = element_text(size = 10)
  )
```

### 2. Grafik Bivariat
#### Scatter Plot: Pendapatan per Kapita vs Angka Harapan Hidup
```r
library(plotly)
p_scatter <- ggplot(df, aes(
  x = Pendapatan_per_kapita,
  y = Angka_Harapan_Hidup,
  size = Populasi,
  color = Benua,
  text = paste(
    "Negara:", Negara, 
    "<br>Populasi:", scales::comma(Populasi),
    "<br>Pendapatan:", scales::comma(Pendapatan_per_kapita),
    "<br>Harapan Hidup:", round(Angka_Harapan_Hidup, 2)
  )
)) +
  geom_point(alpha = 0.8) +
  scale_x_log10(labels = scales::comma) +
  theme_minimal() +
  labs(
    title = "Pendapatan per Kapita vs Angka Harapan Hidup",
    x = "Pendapatan per Kapita (Log Skala)",
    y = "Angka Harapan Hidup",
    color = "Benua",
    size = "Populasi"
  ) +
  theme(
    plot.title = element_text(hjust = 0.5, face = "bold", size = 14),
    legend.position = "bottom"
  )

# Interaktif
plotly::ggplotly(p_scatter, tooltip = "text")
```

### 3. Grafik Multivariat
#### Heatmap: Rata-rata Jumlah Anak Berdasarkan Benua dan Tahun
```r
library(RColorBrewer)
heatmap_data <- df %>%
  group_by(Benua, Tahun) %>%
  summarize(Rata_Jumlah_Anak = mean(Jumlah_anak, na.rm = TRUE))

p_heatmap <- ggplot(heatmap_data, aes(x = Tahun, y = Benua, fill = Rata_Jumlah_Anak)) +
  geom_tile(color = "white") +
  scale_fill_gradientn(colors = brewer.pal(9, "YlOrRd"), na.value = "grey") +
  theme_minimal() +
  labs(
    title = "Rata-rata Jumlah Anak Berdasarkan Benua dan Tahun",
    x = "Tahun",
    y = "Benua",
    fill = "Rata-rata\nJumlah Anak"
  ) +
  theme(
    plot.title = element_text(hjust = 0.5, face = "bold", size = 14),
    axis.text.x = element_text(angle = 45, hjust = 1)
  )

# Interaktif
plotly::ggplotly(p_heatmap)
```

### 4. Grafik Interaktif
#### Bubble Plot Interaktif: Pendapatan vs Harapan Hidup
```r
p_bubble <- plot_ly(
  data = df,
  x = ~Pendapatan_per_kapita,
  y = ~Angka_Harapan_Hidup,
  size = ~Populasi,
  color = ~Benua,
  text = ~paste(
    "Negara:", Negara, 
    "<br>Populasi:", scales::comma(Populasi),
    "<br>Pendapatan:", scales::comma(Pendapatan_per_kapita),
    "<br>Harapan Hidup:", round(Angka_Harapan_Hidup, 2)
  ),
  type = "scatter",
  mode = "markers",
  marker = list(sizemode = "diameter", opacity = 0.7)
) %>%
  layout(
    title = "Bubble Plot: Pendapatan vs Harapan Hidup",
    xaxis = list(title = "Pendapatan per Kapita (Log Skala)", type = "log"),
    yaxis = list(title = "Angka Harapan Hidup"),
    legend = list(title = list(text = "Benua"))
  )

p_bubble
```

## Kesimpulan

- Histogram menunjukkan distribusi angka harapan hidup yang beragam, dengan puncak di kisaran tertentu.
- Scatter plot mengindikasikan hubungan positif antara pendapatan per kapita dan angka harapan hidup, terutama di negara-negara maju.
- Heatmap mengungkapkan pola rata-rata jumlah anak per benua dari tahun ke tahun.
- Bubble plot interaktif memberikan fleksibilitas eksplorasi data dengan menampilkan informasi tambahan saat kursor diarahkan ke titik tertentu.
