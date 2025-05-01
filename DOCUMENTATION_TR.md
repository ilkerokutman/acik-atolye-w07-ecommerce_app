# E-Ticaret Uygulaması - Teknik Dokümantasyon

## E-Ticaret Uygulaması Dokümantasyonu

Bu belge, E-Ticaret Uygulamasının mimarisini, bileşenlerini ve işlevselliğini ana hatlarıyla açıklar.

## Mimari Genel Bakış

### Katman Yapısı

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

### Domain-Spesifik Akış Örneği (Ürün)

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  product_screen │     │    product_     │     │    product_     │
│   (UI Katmanı)  │◄───►│   controller    │◄───►│   repository    │
└─────────────────┘     │(Kontrolcü Katmanı)    │(Repo Katmanı)   │
                        └─────────────────┘     └────────┬────────┘
                                                         │
                                                         ▼
                                               ┌─────────────────┐
                                               │   api_provider  │
                                               │  (Veri Katmanı) │
                                               └─────────────────┘
```

## Proje Yapısı

```
lib/
├── main.dart                  # Uygulama giriş noktası
├── app/                       # Uygulama katmanı
│   ├── routes/                # Uygulama navigasyonu
│   │   └── app_pages.dart
│   ├── domain/                # Domain-spesifik özellikler
│   │   ├── home/              # Ana sayfa domain'i
│   │   │   ├── controllers/    # Ana sayfa kontrolcüleri
│   │   │   │   └── home_controller.dart
│   │   │   ├── screens/        # Ana sayfa ekranları
│   │   │   │   └── home_screen.dart
│   │   │   └── widgets/        # Ana sayfaya özgü widget'lar
│   │   │       └── featured_products_widget.dart
│   │   ├── category/          # Kategori domain'i
│   │   │   ├── controllers/    # Kategori kontrolcüleri
│   │   │   │   └── category_controller.dart
│   │   │   ├── models/         # Kategori modelleri
│   │   │   │   └── category.dart
│   │   │   ├── repositories/   # Kategori repository'leri
│   │   │   │   └── category_repository.dart
│   │   │   ├── screens/        # Kategori ekranları
│   │   │   │   └── category_screen.dart
│   │   │   └── widgets/        # Kategoriye özgü widget'lar
│   │   │       └── category_chip_widget.dart
│   │   ├── product/           # Ürün domain'i
│   │   │   ├── controllers/    # Ürün kontrolcüleri
│   │   │   │   └── product_controller.dart
│   │   │   ├── models/         # Ürün modelleri
│   │   │   │   ├── product.dart
│   │   │   │   └── comment.dart
│   │   │   ├── repositories/   # Ürün repository'leri
│   │   │   │   └── product_repository.dart
│   │   │   ├── screens/        # Ürün ekranları
│   │   │   │   ├── product_screen.dart
│   │   │   │   ├── product_reviews_screen.dart
│   │   │   │   └── product_gallery_screen.dart
│   │   │   └── widgets/        # Ürüne özgü widget'lar
│   │   │       ├── product_card_widget.dart
│   │   │       ├── product_carousel_widget.dart
│   │   │       └── comment_card_widget.dart
│   │   ├── basket/            # Sepet domain'i
│   │   │   ├── controllers/    # Sepet kontrolcüleri
│   │   │   │   └── basket_controller.dart
│   │   │   ├── models/         # Sepet modelleri
│   │   │   │   └── basket_item.dart
│   │   │   ├── screens/        # Sepet ekranları
│   │   │   │   └── basket_screen.dart
│   │   │   └── widgets/        # Sepete özgü widget'lar
│   │   │       └── basket_item_card_widget.dart
│   │   ├── profile/           # Profil domain'i
│   │   │   ├── controllers/    # Profil kontrolcüleri
│   │   │   │   ├── profile_controller.dart
│   │   │   │   ├── address_controller.dart
│   │   │   │   ├── payment_method_controller.dart
│   │   │   │   ├── order_controller.dart
│   │   │   │   └── settings_controller.dart
│   │   │   ├── models/         # Profil modelleri
│   │   │   │   ├── user.dart
│   │   │   │   ├── address.dart
│   │   │   │   ├── payment_method.dart
│   │   │   │   ├── order.dart
│   │   │   │   └── settings.dart
│   │   │   ├── repositories/   # Profil repository'leri
│   │   │   │   └── user_repository.dart
│   │   │   ├── screens/        # Profil ekranları
│   │   │   │   ├── profile_screen.dart
│   │   │   │   ├── edit_profile_screen.dart
│   │   │   │   ├── addresses_screen.dart
│   │   │   │   ├── payment_methods_screen.dart
│   │   │   │   ├── my_orders_screen.dart
│   │   │   │   └── settings_screen.dart
│   │   │   └── widgets/        # Profile özgü widget'lar
│   │   │       ├── profile_header_widget.dart
│   │   │       ├── address_card_widget.dart
│   │   │       ├── payment_method_card_widget.dart
│   │   │       ├── order_card_widget.dart
│   │   │       └── settings_tile_widget.dart
│   │   ├── content/           # İçerik domain'i
│   │   │   ├── screens/        # İçerik ekranları
│   │   │   │   ├── about_screen.dart
│   │   │   │   ├── faq_screen.dart
│   │   │   │   ├── contact_screen.dart
│   │   │   │   ├── help_screen.dart
│   │   │   │   └── privacy_screen.dart
│   │   │   └── widgets/        # İçeriğe özgü widget'lar
│   │   └── shared/            # Domain'ler arası paylaşılan bileşenler
│   │       ├── bindings/       # GetX bağımlılık enjeksiyonu için bağlamalar
│   │       │   └── app_bindings.dart  # Tüm kontrolcüler için tek bağlama sınıfı
│   │       ├── models/         # Paylaşılan modeller
│   │       │   └── base_model.dart
│   │       ├── providers/      # Paylaşılan API/mock veri sağlayıcıları
│   │       │   └── api_provider.dart
│   │       └── widgets/        # Paylaşılan yeniden kullanılabilir UI bileşenleri
│   │           ├── app_bar_widget.dart
│   │           ├── loading_indicator_widget.dart
│   │           ├── error_message_widget.dart
│   │           ├── empty_state_widget.dart
│   │           └── price_tag_widget.dart
│   └── core/                  # Çekirdek işlevsellik
│       ├── constants/          # Uygulama sabitleri
│       │   ├── ui_strings.dart   # Metin sabitleri
│       │   ├── ui_assets.dart    # Varlık yolu sabitleri
│       │   ├── keys.dart         # Anahtar sabitleri
│       │   └── ui_dimens.dart    # Boyut sabitleri
│       ├── utils/              # Yardımcı fonksiyonlar
│       │   ├── dialog_utils.dart # Dialog yardımcıları
│       │   ├── common_utils.dart # Genel yardımcılar
│       │   ├── currency_utils.dart # Para birimi yardımcıları
│       │   └── image_utils.dart  # Resim yardımcıları
│       ├── extensions/         # Uzantı metodları
│       │   ├── string_extensions.dart
│       │   └── context_extensions.dart
│       ├── theme/              # Uygulama teması
│       │   ├── app_theme.dart    # Tema konfigürasyonu
│       │   ├── app_colors.dart   # Renk paleti
│       │   └── app_text_styles.dart # Metin stilleri
│       └── localization/       # Uluslararasılaştırma
│           ├── app_localizations.dart
│           └── app_translations.dart
└── assets/                    # Statik varlıklar
    ├── images/
    └── mock/                  # Sahte JSON verileri
        ├── products.json
        ├── categories.json
        └── profile.json
```

## Proje Genel Bakış
Bu belge, 7. Hafta E-Ticaret Uygulaması Flutter projesi için teknik detayları sağlar. Uygulama, gelişmiş GetX durum yönetimini, bağımlılık enjeksiyonunu ve sahte bir API'den alınan sahte verilerle dinamik UI güncellemelerini gösterir.

## Mimari

### Durum Yönetimi
Uygulama, durum yönetimi için GetX kullanacaktır. GetX, minimal boilerplate kod ile uygulama durumunu yönetmek için basit ve güçlü bir yol sağlar.

Anahtar bileşenler:
- **Kontrolcüler**: Belirli özellikler için durumu yönetir (ürünler, kategoriler, sepet, profil)
- **Reaktif Değişkenler**: Durum değiştiğinde UI'ı otomatik olarak günceller
- **Bağımlılık Enjeksiyonu**: Tek bir AppBindings sınıfı ile kontrolcü yaşam döngülerini yönetir

### Veri Modelleri

#### Ürün Modeli
```dart
class Product {
  final int id;
  final String title;
  final String description;
  final double price;
  final double salePrice;
  final bool onSale;
  final List<String> images;
  final int categoryId;
  final List<Comment> comments;
  
  // fromJson ve toJson metodları
}
```

#### Kategori Modeli
```dart
class Category {
  final int id;
  final String name;
  final String icon;
  
  // fromJson ve toJson metodları
}
```

#### Yorum Modeli
```dart
class Comment {
  final int id;
  final String username;
  final String text;
  final double rating;
  final DateTime date;
  
  // fromJson ve toJson metodları
}
```

#### Sepet Öğesi Modeli
```dart
class BasketItem {
  final Product product;
  int quantity;
  
  double get totalPrice => product.onSale 
    ? product.salePrice * quantity 
    : product.price * quantity;
}
```

#### Kullanıcı Modeli
```dart
class User {
  final int id;
  final String name;
  final String email;
  final String phone;
  final String profileImage;
  
  // fromJson ve toJson metodları
}
```

#### Adres Modeli
```dart
class Address {
  final int id;
  final String title;
  final String fullName;
  final String addressLine1;
  final String addressLine2;
  final String city;
  final String state;
  final String postalCode;
  final String country;
  final bool isDefault;
  
  // fromJson ve toJson metodları
}
```

#### Ödeme Yöntemi Modeli
```dart
class PaymentMethod {
  final int id;
  final String type; // 'credit_card', 'paypal', etc.
  final String cardNumber; // Masked for security
  final String cardHolderName;
  final String expiryDate;
  final bool isDefault;
  
  // fromJson ve toJson metodları
}
```

#### Sipariş Modeli
```dart
class Order {
  final int id;
  final DateTime date;
  final String status;
  final List<BasketItem> items;
  final double totalAmount;
  final Address shippingAddress;
  final PaymentMethod paymentMethod;
  
  // fromJson ve toJson metodları
}
```

#### Ayarlar Modeli
```dart
class Settings {
  final bool darkMode;
  final bool notificationsEnabled;
  final String language;
  final String currency;
  
  // fromJson ve toJson metodları
}
```

### API Sağlayıcı

```dart
class ApiProvider {
  Future<List<Product>> getProducts() async {
    // Sahte veriden ürünleri getir ve ayrıştır
  }
  
  Future<List<Category>> getCategories() async {
    // Sahte veriden kategorileri getir ve ayrıştır
  }
  
  Future<Product> getProductDetails(int id) async {
    // Sahte veriden ürün detaylarını getir ve ayrıştır
  }
  
  Future<User> getUserProfile() async {
    // Sahte veriden kullanıcı profilini getir ve ayrıştır
  }
  
  Future<List<Address>> getUserAddresses() async {
    // Sahte veriden kullanıcı adreslerini getir ve ayrıştır
  }
  
  Future<List<PaymentMethod>> getUserPaymentMethods() async {
    // Sahte veriden kullanıcı ödeme yöntemlerini getir ve ayrıştır
  }
}
```

## Bağımlılık Enjeksiyonu

Uygulama, tüm kontrolcüleri enjekte etmek için tek bir bağlama sınıfı kullanacaktır. Tüm kontrolcüler, uygulama yaşam döngüsü boyunca bellekte kalmalarını sağlamak için `permanent: true` ile kaydedilecektir:

```dart
class AppBindings extends Bindings {
  @override
  Future<void> dependencies() async {
    // Önce sağlayıcıları kaydet
    await Get.putAsync(() async => ApiProvider(), permanent: true);
    
    // Repository'leri kaydet
    await Get.putAsync(() async => ProductRepository(apiProvider: Get.find()), permanent: true);
    await Get.putAsync(() async => CategoryRepository(apiProvider: Get.find()), permanent: true);
    await Get.putAsync(() async => UserRepository(apiProvider: Get.find()), permanent: true);
    
    // Kontrolcüleri bellekte tutmak için permanent: true ile kaydet
    await Get.putAsync(() async => ProductController(productRepository: Get.find()), permanent: true);
    await Get.putAsync(() async => CategoryController(categoryRepository: Get.find()), permanent: true);
    await Get.putAsync(() async => BasketController(), permanent: true);
    await Get.putAsync(() async => ProfileController(userRepository: Get.find()), permanent: true);
    await Get.putAsync(() async => AddressController(userRepository: Get.find()), permanent: true);
    await Get.putAsync(() async => PaymentMethodController(userRepository: Get.find()), permanent: true);
    await Get.putAsync(() async => OrderController(userRepository: Get.find()), permanent: true);
    await Get.putAsync(() async => SettingsController(), permanent: true);
  }
}
```

## Ekranlar

### Ana Sayfa Ekranı
- Öne çıkan ürünler için carousel
- Kategori yatay chip'leri
- Ürün grid'i

### Kategori Ekranı
- Seçilen kategoriye göre filtrelenmiş ürünleri gösterir
- Sıralama ve filtreleme seçenekleri

### Ürün Ekranı
- Ürün detayları, açıklama, fiyat
- Ürün resimleri için carousel
- Kullanıcı yorumları ve puanlamaları
- Sepete ekle butonu

### Ürün Yorumları Ekranı
- Tüm kullanıcı yorumlarını gösterir
- Ortalama puanı gösterir

### Ürün Galerisi Ekranı
- Ürün resimlerini tam ekran görüntüler
- Resimler arasında kaydırma

### Sepet Ekranı
- Sepetteki öğeleri listeler
- Her öğe için miktar ayarı
- Toplam fiyat hesaplaması
- Ödeme işlemine geçiş butonu

### Profil Ekranı
- Kullanıcı bilgilerini gösterir
- Profil düzenleme, adresler, ödeme yöntemleri, siparişler ve ayarlara bağlantılar

### Profil Düzenleme Ekranı
- Görüntülenen ad ve profil fotoğrafını düzenlemeye izin verir

### Adresler Ekranı
- Kullanıcı adreslerini ekleme/düzenleme/kaldırma yetenekleriyle listeler

### Ödeme Yöntemleri Ekranı
- Ödeme yöntemlerini ekleme/düzenleme/kaldırma yetenekleriyle listeler

### Siparişlerim Ekranı
- Kullanıcı siparişlerini detayları ve durumlarıyla listeler

### Ayarlar Ekranı
- Bildirim tercihlerini ve tema ayarlarını (karanlık/açık) değiştirmeye izin verir

### İçerik Ekranları
- Hakkında, SSS, İletişim, Yardım ve Gizlilik ekranları

## Navigasyon

Uygulama, GetX rota yönetimini kullanacaktır:

```dart
class AppPages {
  static final routes = [
    // Ana rotalar
    GetPage(name: '/', page: () => HomeScreen()),
    GetPage(name: '/category/:id', page: () => CategoryScreen()),
    GetPage(name: '/product/:id', page: () => ProductScreen()),
    GetPage(name: '/product/:id/reviews', page: () => ProductReviewsScreen()),
    GetPage(name: '/product/:id/gallery', page: () => ProductGalleryScreen()),
    GetPage(name: '/basket', page: () => BasketScreen()),
    
    // Profil rotaları
    GetPage(name: '/profile', page: () => ProfileScreen()),
    GetPage(name: '/profile/edit', page: () => EditProfileScreen()),
    GetPage(name: '/profile/addresses', page: () => AddressesScreen()),
    GetPage(name: '/profile/payment-methods', page: () => PaymentMethodsScreen()),
    GetPage(name: '/profile/orders', page: () => MyOrdersScreen()),
    GetPage(name: '/profile/settings', page: () => SettingsScreen()),
    
    // İçerik rotaları
    GetPage(name: '/about', page: () => AboutScreen()),
    GetPage(name: '/faq', page: () => FaqScreen()),
    GetPage(name: '/contact', page: () => ContactScreen()),
    GetPage(name: '/help', page: () => HelpScreen()),
    GetPage(name: '/privacy', page: () => PrivacyScreen()),
  ];
}
```

## UI Bileşenleri

### Paylaşılan Widget'lar
- **AppBarWidget**: Tüm ekranlar için tutarlı bir app bar sağlar
- **LoadingIndicatorWidget**: Veri yüklenirken gösterilir
- **ErrorMessageWidget**: Hata mesajlarını gösterir
- **EmptyStateWidget**: Veri olmadığında gösterilir
- **PriceTagWidget**: Fiyat ve indirimli fiyat bilgilerini gösterir

### Ürün Widget'ları
- **ProductCardWidget**: Grid'de ürünleri göstermek için
- **ProductCarouselWidget**: Ürün resimlerini göstermek için
- **CommentCardWidget**: Kullanıcı yorumlarını göstermek için

### Kategori Widget'ları
- **CategoryChipWidget**: Yatay kaydırılabilir kategori listesi için

### Sepet Widget'ları
- **BasketItemCardWidget**: Sepetteki öğeleri göstermek için

### Profil Widget'ları
- **ProfileHeaderWidget**: Kullanıcı bilgilerini göstermek için
- **AddressCardWidget**: Kullanıcı adreslerini göstermek için
- **PaymentMethodCardWidget**: Ödeme yöntemlerini göstermek için
- **OrderCardWidget**: Sipariş bilgilerini göstermek için
- **SettingsTileWidget**: Ayar seçeneklerini göstermek için

## Tema

Uygulama, tutarlı bir görünüm ve his için bir tema kullanacaktır:

```dart
class AppTheme {
  static ThemeData lightTheme = ThemeData(
    primaryColor: AppColors.primary,
    colorScheme: ColorScheme.light(
      primary: AppColors.primary,
      secondary: AppColors.accent,
    ),
    textTheme: AppTextStyles.textTheme,
    // Diğer tema özellikleri
  );
  
  static ThemeData darkTheme = ThemeData(
    primaryColor: AppColors.primaryDark,
    colorScheme: ColorScheme.dark(
      primary: AppColors.primaryDark,
      secondary: AppColors.accentDark,
    ),
    textTheme: AppTextStyles.darkTextTheme,
    // Diğer tema özellikleri
  );
}
```

## Uluslararasılaştırma

Uygulama, çoklu dil desteği için GetX uluslararasılaştırma sistemini kullanacaktır:

```dart
class AppTranslations extends Translations {
  @override
  Map<String, Map<String, String>> get keys => {
    'en_US': {
      'app_name': 'E-Commerce App',
      'home': 'Home',
      'categories': 'Categories',
      // Diğer çeviriler
    },
    'tr_TR': {
      'app_name': 'E-Ticaret Uygulaması',
      'home': 'Ana Sayfa',
      'categories': 'Kategoriler',
      // Diğer çeviriler
    },
  };
}
```

## Sonuç

Bu belge, E-Ticaret Uygulamasının teknik mimarisini, bileşenlerini ve işlevselliğini ana hatlarıyla açıklar. Uygulama, domain odaklı bir mimari kullanarak, her domain'in kendi modelleri, repository'leri, kontrolcüleri, ekranları ve widget'ları ile kendi kendine yeterli olduğu bir yapı sağlar. GetX durum yönetimi ve bağımlılık enjeksiyonu, reaktif ve bakımı kolay bir uygulama sağlar.
