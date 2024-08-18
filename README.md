# CLTV Tahminleme Projesi

Bu proje, bir e-ticaret veri seti kullanarak müşterilerin gelecekteki satın alma davranışlarını tahmin etmeyi amaçlamaktadır. Proje, müşteri yaşam boyu değerini (CLTV) tahmin etmek için **Beta-Geometric/NBD (BG-NBD)** ve **Gamma-Gamma** modellerini kullanmaktadır. Bu sayede, hangi müşterilerin gelecekte en fazla satın almayı yapacağını belirlemek mümkün olmaktadır.

## İçindekiler

1. [Giriş](#giriş)
2. [Veri Seti](#veri-seti)
3. [Veri Ön İşleme](#veri-ön-işleme)
4. [Modelleme](#modelleme)
5. [Sonuçlar](#sonuçlar)
6. [Kullanım](#kullanım)
7. [Lisans](#lisans)

## Giriş

Bu proje, müşteri davranışlarını anlamak ve gelecekteki satın alma davranışlarını tahmin etmek amacıyla BG-NBD ve Gamma-Gamma modellerini kullanır. Proje, Python programlama dili ve `lifetimes` kütüphanesi kullanılarak geliştirilmiştir.

## Veri Seti

Veri seti, e-ticaret işlemlerine dair bilgileri içeren bir Excel dosyasından alınmıştır. Aşağıdaki değişkenleri içerir:
- `Invoice`: Fatura numarası
- `StockCode`: Ürün kodu
- `Description`: Ürün açıklaması
- `Quantity`: Ürün miktarı
- `InvoiceDate`: Fatura tarihi
- `Price`: Ürün fiyatı
- `Customer ID`: Müşteri numarası
- `Country`: Ülke

## Veri Ön İşleme

Veri ön işleme adımları şunları içerir:
1. Eksik değerlerin temizlenmesi
2. İade işlemlerinin çıkarılması
3. Aykırı değerlerin baskılanması
4. Yeni değişkenlerin oluşturulması (`TotalPrice`)
5. Analiz için gerekli değişkenlerin hesaplanması (`recency`, `T`, `frequency`, `monetary`)

## Modelleme

Modelleme süreci şu adımları içerir:
1. **BG-NBD Modeli**: Müşteri satın alma sıklığını ve recency (son satın alma tarihi) ile analiz süresini (T) dikkate alarak müşterinin gelecekteki satın alma sıklığını tahmin eder.
2. **Gamma-Gamma Modeli**: Müşterilerin satın alma başına ortalama harcamalarını tahmin eder.


## Sonuçlar

Aşağıdaki tablo en iyi 10 müşteri için, modelleme sonuçlarına göre her müşteri için tahmin edilen 1 aylık satın alma sıklığını (expected_purc_1_month) ve diğer metrikleri göstermektedir:

| Customer ID | Recency   | T        | Frequency | Monetary | Expected Purchases (1 Month) | Expected Purchases (Rounded) | Expected Average Profit | CLV       | Segment |
|-------------|-----------|----------|-----------|----------|------------------------------|------------------------------|-------------------------|-----------|---------|
| 1970        | 16446.0000 | 29.1429  | 29.4286   | 2        | 0.3933                       | 0                            | 84236.2500              | 92301.0619| A       |
| 1122        | 14646.0000 | 50.4286  | 50.7143   | 73       | 4.8119                       | 5                            | 3838.4386               | 3847.6982| A       |
| 2761        | 18102.0000 | 52.2857  | 52.5714   | 60       | 3.8636                       | 4                            | 4327.6217               | 4340.3219| A       |
| 2458        | 17450.0000 | 51.2857  | 52.5714   | 46       | 2.9815                       | 3                            | 4229.3650               | 4245.5707| A       |
| 843         | 14096.0000 | 13.8571  | 14.5714   | 17       | 2.8955                       | 3                            | 3833.2229               | 3873.2473| A       |
| 36          | 12415.0000 | 44.7143  | 48.2857   | 21       | 1.5139                       | 2                            | 5948.3110               | 5998.3918| A       |
| 1257        | 14911.0000 | 53.1429  | 53.4286   | 201      | 12.4722                      | 12                           | 715.5476                | 716.1886 | A       |
| 874         | 14156.0000 | 51.5714  | 53.1429   | 55       | 3.5005                       | 4                            | 2134.1751               | 2141.0438| A       |
| 1754        | 16000.0000 | 0.0000   | 0.4286    | 3        | 1.6639                       | 2                            | 4131.2333               | 4388.0165| A       |
| 2487        | 17511.0000 | 52.8571  | 53.4286   | 31       | 2.0298                       | 2                            | 2937.4961               | 2954.2658| A       |
