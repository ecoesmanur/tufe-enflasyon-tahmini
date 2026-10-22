# Türkiye TÜFE Enflasyon Tahmini – Zaman Serisi Analizi

Türkiye'nin aylık enflasyonunu **SARIMA** modeliyle tahmin eden ve modelin başarısını basit karşılaştırma yöntemleriyle ölçen bir ekonometri projesi.

## Veri
- **Kaynak:** TCMB EVDS – Tüketici Fiyat Endeksi (2003=100), Genel
- **Dönem:** Ocak 2004 – Ocak 2026, aylık (265 gözlem)
- **Dosya:** `tufe_2004_2026.csv`

## Yöntem
1. Aylık enflasyon (log fark) ve yıllık enflasyon hesaplama
2. ADF birim kök testi ile durağanlık kontrolü
3. ACF / PACF analizi
4. AIC'ye göre SARIMA(p,0,q)(P,0,0)[12] model seçimi
5. Son 12 ay (Şubat 2025 – Ocak 2026) ile test, RMSE karşılaştırması
6. Şubat – Temmuz 2026 için 6 aylık tahmin ve %95 güven aralığı

## Temel bulgular
- Yıllık enflasyon Ocak 2026'da **%30,6** (Ocak 2025: %42,1; zirve Ekim 2022: %85,5).
- Seçilen model: **SARIMA(1,0,2)(1,0,0)[12]**
- Test dönemi RMSE: SARIMA **1,235** | 12 ay ortalaması 1,248 | son ay 2,874
- Model, "son ay" yöntemine göre belirgin şekilde daha iyi. "12 ay ortalaması" yöntemine göre fark ise küçük: model genel seviyeyi yakalıyor ama ani aylık şokları tahmin etmekte zorlanıyor.

## Sınırlılıklar
- 2021 sonrası yapısal kırılma (ADF testinde aylık enflasyon %5'te durağan çıkmadı)
- Tek değişkenli model: kur, faiz gibi açıklayıcı değişkenler yok
- TÜİK'in 2026'da 2025=100 bazına geçmesi nedeniyle seri Ocak 2026'da bitiyor

## Kullanılan araçlar
Python · pandas · NumPy · statsmodels · Matplotlib · Google Colab

## Çalıştırma
`tufe_enflasyon_tahmini.ipynb` dosyasını açıp **"Open in Colab"** ile ya da Jupyter'de çalıştırabilirsiniz.

---
**Esma Nur Okşul** – Sakarya Üniversitesi, Ekonometri
