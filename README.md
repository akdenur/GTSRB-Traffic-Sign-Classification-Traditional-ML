# GTSRB Trafik Levhası Sınıflandırma — Geleneksel Makine Öğrenmesi

**Alman Trafik Levhası Tanıma Veri Kümesi (GTSRB)** üzerinde geleneksel görüntü işleme ve makine öğrenmesi yaklaşımlarının karşılaştırmalı analizi. Bu çalışma, el ile tasarlanmış (handcrafted) öznitelik çıkarımı, boyut indirgeme ve klasik sınıflandırıcılar kullanarak **%98,72 test doğruluğu** elde eden güçlü bir referans noktası (baseline) sunmaktadır.

## Proje Özeti

Trafik levhası tanıma, otonom sürüş ve gelişmiş sürücü destek sistemleri (ADAS) için kritik bir problemdir. Bu çalışmada ham trafik levhası görüntüleri sistematik bir geleneksel makine öğrenmesi hattından geçirilerek, derin öğrenme mimarilerine geçmeden önce manuel öznitelik mühendisliğinin başarım sınırları incelenmiştir.

### Veri Kümesi
- **Kaynak:** German Traffic Sign Recognition Benchmark (GTSRB)
- **Sınıf Sayısı:** 43 trafik levhası kategorisi (hız sınırları, yasaklama, tehlike uyarı ve mecburi yön işaretleri)
- **Toplam Görüntü:** 39.209 etiketli görüntü

## Yöntem

1. **Görüntü Ön İşleme (OpenCV):**
   - Farklı çözünürlük ve en-boy oranlarına sahip görüntülerin standartlaştırılması.
   - Renk uzayı dönüşümleri ve Canny kenar tespiti.
2. **Hibrit Öznitelik Çıkarımı:**
   - **HOG (Yönlendirilmiş Gradyan Histogramları):** Kenar yönelimlerini ve şekil yapısını yakalar.
   - **LBP (Yerel İkili Örüntüler):** Yerel doku (texture) özniteliklerini çıkarır.
   - **Canny Kenar Öznitelikleri:** Yapısal sınırları belirginleştirir.
3. **Boyut İndirgeme:**
   - **PCA (Temel Bileşen Analizi):** Yüksek boyutlu öznitelik vektörlerini maksimum varyansı koruyarak sıkıştırır, eğitim süresini optimize eder ve aşırı öğrenmeyi (overfitting) azaltır.
4. **Sınıflandırma Modelleri:**
   - **Rastgele Orman (Random Forest)**
   - **Destek Vektör Makineleri (SVM)**

## Temel Bulgular

- **En İyi Model:** Hibrit öznitelikler (HOG + LBP + Canny) ve PCA ile eğitilen **SVM** modeli **%98,72 test doğruluğu** elde etmiştir.
- **Performans Sınırları:** Manuel öznitelik mühendisliği, özellikle görsel olarak birbirine çok benzeyen hız sınırı levhalarında (örneğin Sınıf 5) ve aşırı ışık, bulanıklık veya düşük kontrast bozulmalarında doğal bir performans tavanına ulaşmaktadır.
- **Sonraki Aşama:** Bu çalışmada elde edilen sonuçlar, devam niteliğindeki [Derin Öğrenme (Özel CNN ve MobileNetV2)](https://github.com/akdenur/GTSRB-Traffic-Sign-Classification-Deep-Learning) çalışması için temel kıyaslama noktası olarak kullanılmıştır.

## Kullanılan Teknolojiler

- **Dil:** Python
- **Ortam:** Google Colab
- **Kütüphaneler:** Scikit-learn, OpenCV, NumPy, Pandas, Matplotlib, Seaborn

## Depo Yapısı

```text
├── GTSRB_Traditional_ML_Pipeline.ipynb   # Uçtan uca eğitim ve değerlendirme notebook'u
├── GTSRB_Traditional_ML_Report.pdf       # IEEE formatında detaylı akademik proje raporu
└── README.md                             # Proje dokümantasyonu
