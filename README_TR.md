# E-Ticaret Uygulaması

GetX durum yönetimi ile domain odaklı mimariye sahip kapsamlı bir Flutter e-ticaret uygulaması.

## Proje Genel Bakış

Bu e-ticaret uygulaması, aşağıdaki gelişmiş Flutter geliştirme uygulamalarını sergiler:

- **Domain Odaklı Mimari**: Teknik katmanlar yerine özellik alanlarına göre düzenlenmiş
- **GetX Durum Yönetimi**: Bağımlılık enjeksiyonu ile reaktif durum yönetimi
- **Sahte API Entegrasyonu**: JSON verileri ile simüle edilmiş backend
- **Kapsamlı UI**: Tam e-ticaret deneyimini kapsayan çoklu ekranlar

## Özellikler

### Ana Sayfa
- Öne çıkan ürünler için carousel
- Kategori navigasyonu
- Ürün önerileri

### Ürün
- Detaylı ürün bilgisi
- Resim galerileri
- Kullanıcı yorumları ve puanlamaları
- İlgili ürünler

### Kategori
- Kategori gezinme
- Filtrelenmiş ürün görünümleri
- Sıralama ve filtreleme seçenekleri

### Sepet
- Ürün ekleme/çıkarma
- Miktar ayarlama
- Fiyat hesaplamaları
- Ödeme akışı

### Profil
- Kullanıcı bilgileri yönetimi
- Adres yönetimi
- Ödeme yöntemi yönetimi
- Sipariş geçmişi
- Uygulama ayarları

### İçerik
- Hakkında sayfası
- SSS
- İletişim bilgileri
- Yardım merkezi
- Gizlilik politikası

## Mimari

Uygulama, açık bir sorumluluk ayrımı ile domain odaklı bir mimariyi takip eder:

```
┌─────────────────────────────────────────────────────────────────┐
│                         UI Katmanı                              │
│                                                                 │
│  ┌─────────────┐   ┌─────────────┐   ┌─────────────┐            │
│  │  Ekranlar   │   │  Widgetlar  │   │UI Bileşenleri│            │
│  └─────────────┘   └─────────────┘   └─────────────┘            │
└───────────────────────────┬─────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│                    Kontrolcü Katmanı                            │
│                                                                 │
│  ┌─────────────┐   ┌─────────────┐   ┌─────────────┐            │
│  │  GetX Durum │   │ UI Mantığı  │   │ Navigasyon  │            │
│  │   Yönetimi  │   │             │   │             │            │
│  └─────────────┘   └─────────────┘   └─────────────┘            │
└───────────────────────────┬─────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│                     Repository Katmanı                          │
│                                                                 │
│  ┌─────────────┐   ┌─────────────┐   ┌─────────────┐            │
│  │ Veri Erişim │   │ Model       │   │ İş Mantığı  │            │
│  │ Mantığı     │   │ Dönüşümü    │   │             │            │
│  └─────────────┘   └─────────────┘   └─────────────┘            │
└───────────────────────────┬─────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│                       Veri Katmanı                              │
│                                                                 │
│  ┌─────────────┐   ┌─────────────┐   ┌─────────────┐            │
│  │API Sağlayıcı│   │ Yerel       │   │ Modeller    │            │
│  │             │   │ Depolama    │   │             │            │
│  └─────────────┘   └─────────────┘   └─────────────┘            │
└─────────────────────────────────────────────────────────────────┘
```

Her domain şunları içerir:
- Modeller
- Repository
- Kontrolcü
- Ekranlar
- Widgetlar

## Proje Yapısı

```
lib/
├── main.dart                  # Uygulama giriş noktası
├── app/                       # Uygulama katmanı
│   ├── routes/                # Uygulama navigasyonu
│   │   └── app_pages.dart
│   ├── domain/                # Domain-spesifik özellikler
│   │   ├── home/              # Ana sayfa domain'i
│   │   ├── category/          # Kategori domain'i
│   │   ├── product/           # Ürün domain'i
│   │   ├── basket/            # Sepet domain'i
│   │   ├── profile/           # Profil domain'i
│   │   ├── content/           # İçerik domain'i
│   │   └── shared/            # Paylaşılan bileşenler
│   └── core/                  # Çekirdek işlevsellik
│       ├── constants/         # Uygulama sabitleri
│       ├── utils/             # Yardımcı fonksiyonlar
│       ├── extensions/        # Uzantı metodları
│       ├── theme/             # Uygulama teması
│       └── localization/      # Uluslararasılaştırma
└── assets/                    # Statik varlıklar
    ├── images/
    └── mock/                  # Sahte JSON verileri
```

## Başlangıç

1. **Repository'yi Klonlayın**:
   ```bash
   git clone https://github.com/ilkerokutman/acik-atolye-w07-ecommerce_app.git
   ```

2. **Proje Dizinine Gidin**:
   ```bash
   cd acik-atolye-w07-ecommerce_app
   ```

3. **Platform-Spesifik Kod Oluşturun**:
   ```bash
   flutter create .
   ```
   Bu, en son Flutter SDK'sını kullanarak platform-spesifik kod oluşturacaktır.
   
   Alternatif olarak, paket adını ve proje adını özelleştirebilirsiniz:
   ```bash
   flutter create --org=com.sirketim --project-name=e_ticaret_uygulamam .
   ```
   Bu, kendi organizasyon tanımlayıcınızı ve proje adınızı belirlemenize olanak tanır.

4. **Bağımlılıkları Yükleyin**:
   ```bash
   flutter pub get
   ```

5. **Uygulamayı Çalıştırın**:
   ```bash
   flutter run
   ```

## Geliştirme Süreci

Geliştirme süreci, [TASKS_TR.md](TASKS_TR.md) dosyasında belirtilen aşamalara göre düzenlenmiştir:

1. **Dokümantasyon ve Analiz**: Proje gereksinimlerini anlama
2. **Proje Kurulumu**: Flutter ortamını kurma
3. **UI Tasarım Taslakları**: Tüm ekranlar için taslaklar oluşturma
4. **Çekirdek Uygulama**: Çekirdek yardımcı programları ve sabitleri uygulama
5. **Paylaşılan Bileşenler**: Paylaşılan modelleri, sağlayıcıları ve widget'ları uygulama
6. **Domain Uygulaması**: Her domain'i uygulama (ürün, kategori, vb.)
7. **Entegrasyon ve Test**: Tüm domain'leri bağlama ve test etme
8. **Sonlandırma**: Optimize etme ve üretime hazırlama

## Dokümantasyon

Detaylı teknik dokümantasyon için [DOCUMENTATION_TR.md](DOCUMENTATION_TR.md) dosyasına bakın.

## Lisans

Bu proje MIT Lisansı altında lisanslanmıştır - detaylar için [LICENSE](LICENSE) dosyasına bakın.
