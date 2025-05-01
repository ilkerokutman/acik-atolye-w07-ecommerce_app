# E-Ticaret Uygulaması - Uygulama Görevleri

Bu belge, DOCUMENTATION_TR.md'de tanımlanan mimariye göre E-Ticaret Uygulamasını uygulamak için adım adım görevleri ana hatlarıyla belirtir.

> **ÖNEMLİ**: Her bileşen (sınıf, model, kontrolcü vb.) için önce şunları içeren ayrıntılı bir plan belgesi oluşturmalısınız:
> - Sınıf adı ve amacı
> - Tüm özellikler/değişkenler, türleri ve amaçları ile
> - Tüm metodlar, parametreleri, dönüş türleri ve açıklamaları ile
> - Diğer bileşenlere olan bağımlılıklar
> - Örnek kullanım örnekleri
>
> Planınız tamamlanıp incelendikten sonra uygulamaya başlamalısınız.

## Aşama 1: Dokümantasyon ve Analiz

- [ ] Proje dokümantasyonunu okuyun ve anlayın (DOCUMENTATION_TR.md)
- [ ] Domain odaklı mimariyi ve katman yapısını inceleyin
- [ ] Bileşenler arasındaki veri akışını analiz edin
- [ ] Her domain'in ve paylaşılan bileşenin rolünü anlayın
- [ ] Sahte veri yapısını ve formatını inceleyin
- [ ] Bileşenler (sınıflar, modeller, kontrolcüler vb.) için bir planlama belgesi şablonu oluşturun

## Aşama 2: Proje Kurulumu

- [ ] Flutter geliştirme ortamını kurun
- [ ] Dokümantasyona göre başlangıç proje yapısını oluşturun
- [ ] pubspec.yaml'a gerekli bağımlılıkları ekleyin:
  - [ ] get (GetX durum yönetimi için)
  - [ ] http (API iletişimi için)
  - [ ] cached_network_image (resim önbelleğe alma için)
  - [ ] carousel_slider (ürün carousel'ları için)
- [ ] Sahte veriler ve resimler için asset klasörlerini ayarlayın
- [ ] Uygulama temasını ve yerelleştirmeyi yapılandırın

## Aşama 3: UI Tasarım Taslakları

- [ ] Ana sayfa ekranları için taslaklar oluşturun
  - [ ] Ana sayfa düzenini tasarlayın (kategorileri, öne çıkan ürünleri, navigasyonu gösteren)
  - [ ] Bileşen konumlarını ve etkileşimlerini belirtin
- [ ] Ürün ekranları için taslaklar oluşturun
  - [ ] Ürün listeleme ekranını tasarlayın (ürün kartlarını, filtreleme seçeneklerini gösteren)
  - [ ] Ürün detay ekranını tasarlayın (resimleri, açıklamayı, fiyatı, sepete ekle butonunu gösteren)
  - [ ] Ürün yorumları ekranını tasarlayın (yorumları, puanlamaları gösteren)
  - [ ] Ürün galerisi ekranını tasarlayın (resim carousel'ını gösteren)
  - [ ] Bileşen konumlarını ve etkileşimlerini belirtin
- [ ] Kategori ekranları için taslaklar oluşturun
  - [ ] Kategori ekranını tasarlayın (kategori listesini, filtrelenmiş ürünleri gösteren)
  - [ ] Bileşen konumlarını ve etkileşimlerini belirtin
- [ ] Sepet ekranları için taslaklar oluşturun
  - [ ] Sepet ekranını tasarlayın (öğeleri, miktarları, +/- butonlarını, toplam fiyatı, ödeme butonunu gösteren)
  - [ ] Bileşen konumlarını ve etkileşimlerini belirtin
- [ ] Profil ekranları için taslaklar oluşturun
  - [ ] Profil ekranını tasarlayın (kullanıcı bilgilerini, seçenekler menüsünü gösteren)
  - [ ] Profil düzenleme ekranını tasarlayın (düzenlenebilir alanları gösteren)
  - [ ] Adresler ekranını tasarlayın (adres listesini, ekleme/düzenleme seçeneklerini gösteren)
  - [ ] Ödeme yöntemleri ekranını tasarlayın (ödeme yöntemlerini, ekleme/düzenleme seçeneklerini gösteren)
  - [ ] Siparişlerim ekranını tasarlayın (sipariş geçmişini gösteren)
  - [ ] Ayarlar ekranını tasarlayın (yapılandırılabilir seçenekleri gösteren)
  - [ ] Bileşen konumlarını ve etkileşimlerini belirtin
- [ ] İçerik ekranları için taslaklar oluşturun
  - [ ] Hakkında/SSS/İletişim/Yardım/Gizlilik ekranlarını tasarlayın
  - [ ] Bileşen konumlarını ve etkileşimlerini belirtin

## Aşama 4: Çekirdek Uygulama

- [ ] core/constants'ı planlayın
  - [ ] ui_strings.dart'ı tasarlayın (tüm metin sabitlerini tanımlayın)
  - [ ] ui_assets.dart'ı tasarlayın (tüm varlık yolu sabitlerini tanımlayın)
  - [ ] keys.dart'ı tasarlayın (tüm anahtar sabitlerini tanımlayın)
  - [ ] ui_dimens.dart'ı tasarlayın (tüm boyut sabitlerini tanımlayın)
- [ ] Onaylanan planlara göre core/constants'ı uygulayın
  - [ ] ui_strings.dart
  - [ ] ui_assets.dart
  - [ ] keys.dart
  - [ ] ui_dimens.dart
- [ ] core/utils'i planlayın
  - [ ] dialog_utils.dart'ı tasarlayın (metodlar, parametreler, dönüşler)
  - [ ] common_utils.dart'ı tasarlayın (metodlar, parametreler, dönüşler)
  - [ ] currency_utils.dart'ı tasarlayın (metodlar, parametreler, dönüşler)
  - [ ] image_utils.dart'ı tasarlayın (metodlar, parametreler, dönüşler)
- [ ] Onaylanan planlara göre core/utils'i uygulayın
  - [ ] dialog_utils.dart
  - [ ] common_utils.dart
  - [ ] currency_utils.dart
  - [ ] image_utils.dart
- [ ] core/extensions'ı planlayın
  - [ ] string_extensions.dart'ı tasarlayın (metodlar, parametreler, dönüşler)
  - [ ] context_extensions.dart'ı tasarlayın (metodlar, parametreler, dönüşler)
- [ ] Onaylanan planlara göre core/extensions'ı uygulayın
  - [ ] string_extensions.dart
  - [ ] context_extensions.dart
- [ ] core/theme'i planlayın
  - [ ] app_theme.dart'ı tasarlayın (özellikler, metodlar)
  - [ ] app_colors.dart'ı tasarlayın (renk sabitleri)
  - [ ] app_text_styles.dart'ı tasarlayın (metin stili sabitleri)
- [ ] Onaylanan planlara göre core/theme'i uygulayın
  - [ ] app_theme.dart
  - [ ] app_colors.dart
  - [ ] app_text_styles.dart
- [ ] app_pages.dart'ta navigasyon rotalarını planlayın (tüm rotalar, parametreler)
- [ ] Onaylanan plana göre app_pages.dart'ta navigasyon rotalarını uygulayın
- [ ] Test için bir geliştirici ekranı oluşturun
  - [ ] Tüm uygulama ekranlarına bağlantılar içeren bir developer_screen.dart tasarlayın
  - [ ] Tipografi ve tasarım öğelerini önizlemek için örnek UI bileşenleri ekleyin
  - [ ] Bu ekranı MaterialApp'te ana ekran olarak ayarlayın (main.dart'ta)
  - [ ] Geliştirme tamamlandığında bunun gerçek home_screen ile değiştirilmesi gerektiğini belirten açık bir yorum ekleyin
  - [ ] Ön koşulları atlayarak (örn. giriş) her ekrana doğrudan navigasyonu uygulayın

## Aşama 5: Paylaşılan Bileşenler

- [ ] Paylaşılan modelleri planlayın
  - [ ] base_model.dart'ı tasarlayın (özellikler, metodlar, serileştirme)
- [ ] Onaylanan planlara göre paylaşılan modelleri uygulayın
  - [ ] base_model.dart
- [ ] Paylaşılan sağlayıcıları planlayın
  - [ ] api_provider.dart'ı tasarlayın (metodlar, parametreler, dönüşler, hata işleme)
- [ ] Onaylanan planlara göre paylaşılan sağlayıcıları uygulayın
  - [ ] api_provider.dart (sahte veriler için)
- [ ] Paylaşılan widget'ları planlayın
  - [ ] app_bar_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
  - [ ] loading_indicator_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
  - [ ] error_message_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
  - [ ] empty_state_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
  - [ ] price_tag_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
- [ ] Onaylanan planlara göre paylaşılan widget'ları uygulayın
  - [ ] app_bar_widget.dart
  - [ ] loading_indicator_widget.dart
  - [ ] error_message_widget.dart
  - [ ] empty_state_widget.dart
  - [ ] price_tag_widget.dart
- [ ] app_bindings.dart ile bağımlılık enjeksiyonunu planlayın (tüm bağımlılıklar, başlatma sırası)
- [ ] Onaylanan plana göre app_bindings.dart ile bağımlılık enjeksiyonunu uygulayın

## Aşama 6: Ürün Domain'i

- [ ] Ürün modellerini planlayın
  - [ ] product.dart'ı tasarlayın (özellikler, metodlar, serileştirme)
  - [ ] comment.dart'ı tasarlayın (özellikler, metodlar, serileştirme)
- [ ] Onaylanan planlara göre ürün modellerini uygulayın
  - [ ] product.dart
  - [ ] comment.dart
- [ ] Ürün repository'sini planlayın
  - [ ] product_repository.dart'ı tasarlayın (metodlar, parametreler, dönüşler, hata işleme)
- [ ] Onaylanan plana göre ürün repository'sini uygulayın
  - [ ] product_repository.dart
- [ ] Ürün kontrolcüsünü planlayın
  - [ ] product_controller.dart'ı tasarlayın (durum değişkenleri, metodlar, bağımlılıklar)
- [ ] Onaylanan plana göre ürün kontrolcüsünü uygulayın
  - [ ] product_controller.dart
- [ ] Ürün ekranlarını planlayın (Aşama 3'te oluşturulan UI taslaklarına bakın)
  - [ ] product_screen.dart'ı tasarlayın (bileşen yerleşimi, kontrolcü etkileşimleri, kullanıcı akışları)
  - [ ] product_reviews_screen.dart'ı tasarlayın (bileşen yerleşimi, kontrolcü etkileşimleri, kullanıcı akışları)
  - [ ] product_gallery_screen.dart'ı tasarlayın (bileşen yerleşimi, kontrolcü etkileşimleri, kullanıcı akışları)
- [ ] Onaylanan planlara göre ürün ekranlarını uygulayın
  - [ ] product_screen.dart
  - [ ] product_reviews_screen.dart
  - [ ] product_gallery_screen.dart
- [ ] Ürün widget'larını planlayın
  - [ ] product_card_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
  - [ ] product_carousel_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
  - [ ] comment_card_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
- [ ] Onaylanan planlara göre ürün widget'larını uygulayın
  - [ ] product_card_widget.dart
  - [ ] product_carousel_widget.dart
  - [ ] comment_card_widget.dart

## Aşama 7: Kategori Domain'i

- [ ] Kategori modellerini planlayın
  - [ ] category.dart'ı tasarlayın (özellikler, metodlar, serileştirme)
- [ ] Onaylanan planlara göre kategori modellerini uygulayın
  - [ ] category.dart
- [ ] Kategori repository'sini planlayın
  - [ ] category_repository.dart'ı tasarlayın (metodlar, parametreler, dönüşler, hata işleme)
- [ ] Onaylanan plana göre kategori repository'sini uygulayın
  - [ ] category_repository.dart
- [ ] Kategori kontrolcüsünü planlayın
  - [ ] category_controller.dart'ı tasarlayın (durum değişkenleri, metodlar, bağımlılıklar)
- [ ] Onaylanan plana göre kategori kontrolcüsünü uygulayın
  - [ ] category_controller.dart
- [ ] Kategori ekranlarını planlayın (Aşama 3'te oluşturulan UI taslaklarına bakın)
  - [ ] category_screen.dart'ı tasarlayın (bileşen yerleşimi, kontrolcü etkileşimleri, kullanıcı akışları)
- [ ] Onaylanan planlara göre kategori ekranlarını uygulayın
  - [ ] category_screen.dart
- [ ] Kategori widget'larını planlayın
  - [ ] category_chip_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
- [ ] Onaylanan planlara göre kategori widget'larını uygulayın
  - [ ] category_chip_widget.dart

## Aşama 8: Ana Sayfa Domain'i

- [ ] Ana sayfa kontrolcüsünü planlayın
  - [ ] home_controller.dart'ı tasarlayın (durum değişkenleri, metodlar, bağımlılıklar)
- [ ] Onaylanan plana göre ana sayfa kontrolcüsünü uygulayın
  - [ ] home_controller.dart
- [ ] Ana sayfa ekranlarını planlayın (Aşama 3'te oluşturulan UI taslaklarına bakın)
  - [ ] home_screen.dart'ı tasarlayın (bileşen yerleşimi, kontrolcü etkileşimleri, kullanıcı akışları)
- [ ] Onaylanan planlara göre ana sayfa ekranlarını uygulayın
  - [ ] home_screen.dart
- [ ] Ana sayfa widget'larını planlayın
  - [ ] featured_products_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
- [ ] Onaylanan planlara göre ana sayfa widget'larını uygulayın
  - [ ] featured_products_widget.dart

## Aşama 9: Sepet Domain'i

- [ ] Sepet modellerini planlayın
  - [ ] basket_item.dart'ı tasarlayın (özellikler, metodlar, serileştirme)
- [ ] Onaylanan planlara göre sepet modellerini uygulayın
  - [ ] basket_item.dart
- [ ] Sepet kontrolcüsünü planlayın
  - [ ] basket_controller.dart'ı tasarlayın (durum değişkenleri, metodlar, bağımlılıklar)
- [ ] Onaylanan plana göre sepet kontrolcüsünü uygulayın
  - [ ] basket_controller.dart
- [ ] Sepet ekranlarını planlayın (Aşama 3'te oluşturulan UI taslaklarına bakın)
  - [ ] basket_screen.dart'ı tasarlayın (bileşen yerleşimi, kontrolcü etkileşimleri, kullanıcı akışları, miktar ayarı)
- [ ] Onaylanan planlara göre sepet ekranlarını uygulayın
  - [ ] basket_screen.dart
- [ ] Sepet widget'larını planlayın
  - [ ] basket_item_card_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
- [ ] Onaylanan planlara göre sepet widget'larını uygulayın
  - [ ] basket_item_card_widget.dart

## Aşama 10: Profil Domain'i

- [ ] Profil modellerini planlayın
  - [ ] user.dart'ı tasarlayın (özellikler, metodlar, serileştirme)
  - [ ] address.dart'ı tasarlayın (özellikler, metodlar, serileştirme)
  - [ ] payment_method.dart'ı tasarlayın (özellikler, metodlar, serileştirme)
  - [ ] order.dart'ı tasarlayın (özellikler, metodlar, serileştirme)
  - [ ] settings.dart'ı tasarlayın (özellikler, metodlar, serileştirme)
- [ ] Onaylanan planlara göre profil modellerini uygulayın
  - [ ] user.dart
  - [ ] address.dart
  - [ ] payment_method.dart
  - [ ] order.dart
  - [ ] settings.dart
- [ ] Profil repository'sini planlayın
  - [ ] user_repository.dart'ı tasarlayın (metodlar, parametreler, dönüşler, hata işleme)
- [ ] Onaylanan plana göre profil repository'sini uygulayın
  - [ ] user_repository.dart
- [ ] Profil kontrolcülerini planlayın
  - [ ] profile_controller.dart'ı tasarlayın (durum değişkenleri, metodlar, bağımlılıklar)
  - [ ] address_controller.dart'ı tasarlayın (durum değişkenleri, metodlar, bağımlılıklar)
  - [ ] payment_method_controller.dart'ı tasarlayın (durum değişkenleri, metodlar, bağımlılıklar)
  - [ ] order_controller.dart'ı tasarlayın (durum değişkenleri, metodlar, bağımlılıklar)
  - [ ] settings_controller.dart'ı tasarlayın (durum değişkenleri, metodlar, bağımlılıklar)
- [ ] Onaylanan planlara göre profil kontrolcülerini uygulayın
  - [ ] profile_controller.dart
  - [ ] address_controller.dart
  - [ ] payment_method_controller.dart
  - [ ] order_controller.dart
  - [ ] settings_controller.dart
- [ ] Profil ekranlarını planlayın (Aşama 3'te oluşturulan UI taslaklarına bakın)
  - [ ] profile_screen.dart'ı tasarlayın (bileşen yerleşimi, kontrolcü etkileşimleri, kullanıcı akışları)
  - [ ] edit_profile_screen.dart'ı tasarlayın (bileşen yerleşimi, kontrolcü etkileşimleri, kullanıcı akışları)
  - [ ] addresses_screen.dart'ı tasarlayın (bileşen yerleşimi, kontrolcü etkileşimleri, kullanıcı akışları)
  - [ ] payment_methods_screen.dart'ı tasarlayın (bileşen yerleşimi, kontrolcü etkileşimleri, kullanıcı akışları)
  - [ ] my_orders_screen.dart'ı tasarlayın (bileşen yerleşimi, kontrolcü etkileşimleri, kullanıcı akışları)
  - [ ] settings_screen.dart'ı tasarlayın (bileşen yerleşimi, kontrolcü etkileşimleri, kullanıcı akışları)
- [ ] Onaylanan planlara göre profil ekranlarını uygulayın
  - [ ] profile_screen.dart
  - [ ] edit_profile_screen.dart
  - [ ] addresses_screen.dart
  - [ ] payment_methods_screen.dart
  - [ ] my_orders_screen.dart
  - [ ] settings_screen.dart
- [ ] Profil widget'larını planlayın
  - [ ] profile_header_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
  - [ ] address_card_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
  - [ ] payment_method_card_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
  - [ ] order_card_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
  - [ ] settings_tile_widget.dart'ı tasarlayın (özellikler, metodlar, UI düzeni)
- [ ] Onaylanan planlara göre profil widget'larını uygulayın
  - [ ] profile_header_widget.dart
  - [ ] address_card_widget.dart
  - [ ] payment_method_card_widget.dart
  - [ ] order_card_widget.dart
  - [ ] settings_tile_widget.dart

## Aşama 11: İçerik Domain'i

- [ ] İçerik ekranlarını planlayın (Aşama 3'te oluşturulan UI taslaklarına bakın)
  - [ ] about_screen.dart'ı tasarlayın (bileşen yerleşimi, içerik yapısı, kullanıcı akışları)
  - [ ] faq_screen.dart'ı tasarlayın (bileşen yerleşimi, içerik yapısı, kullanıcı akışları)
  - [ ] contact_screen.dart'ı tasarlayın (bileşen yerleşimi, içerik yapısı, kullanıcı akışları)
  - [ ] help_screen.dart'ı tasarlayın (bileşen yerleşimi, içerik yapısı, kullanıcı akışları)
  - [ ] privacy_screen.dart'ı tasarlayın (bileşen yerleşimi, içerik yapısı, kullanıcı akışları)
- [ ] Onaylanan planlara göre içerik ekranlarını uygulayın
  - [ ] about_screen.dart
  - [ ] faq_screen.dart
  - [ ] contact_screen.dart
  - [ ] help_screen.dart
  - [ ] privacy_screen.dart

## Aşama 12: Entegrasyon ve Test

- [ ] Entegrasyon stratejisini planlayın
  - [ ] Domain'lerin navigasyon aracılığıyla nasıl bağlanacağını belgelendirin
  - [ ] Bileşenler arasındaki veri akışı için test durumlarını tasarlayın
  - [ ] GetX durum yönetimi için beklenen reaktif davranışı tanımlayın
  - [ ] Farklı ekran boyutları için duyarlı tasarım özelliklerini oluşturun
  - [ ] Hata işleme ve yükleme durumu stratejilerini tasarlayın
  - [ ] Test için uçtan uca kullanıcı akışlarını belgelendirin
- [ ] Onaylanan planlara göre entegrasyonu uygulayın
  - [ ] Tüm domain'leri navigasyon aracılığıyla bağlayın
  - [ ] Bileşenler arasındaki veri akışını test edin
  - [ ] GetX ile reaktif durum yönetimini doğrulayın
  - [ ] Farklı ekran boyutlarında UI duyarlılığını test edin
  - [ ] Hata işleme ve yükleme durumlarını uygulayın
  - [ ] Kullanıcı akışlarının uçtan uca testini gerçekleştirin

## Aşama 13: Sonlandırma

- [ ] Sonlandırma adımlarını planlayın
  - [ ] Performans optimizasyon fırsatlarını belirleyin
  - [ ] Uygulama simgesini ve açılış ekranını tasarlayın
  - [ ] Üretim derleme sürecini belgelendirin
  - [ ] Son dokümantasyon gereksinimlerini ana hatlarıyla belirtin
- [ ] Onaylanan planlara göre sonlandırmayı uygulayın
  - [ ] Performansı optimize edin
  - [ ] Uygulama simgesini ve açılış ekranını ekleyin
  - [ ] Üretim derlemesi için hazırlayın
  - [ ] Son dokümantasyonu oluşturun
  - [ ] Tamamlanan projeyi gönderin

## Aşama 14: Dağıtım (İsteğe Bağlı)

- [ ] Dağıtım stratejisini planlayın
  - [ ] Uygulama mağazası gereksinimlerini araştırın (Google Play, App Store)
  - [ ] Sürüm numaralandırma şemasını tanımlayın
  - [ ] Sürüm notları şablonunu planlayın
  - [ ] Gizlilik politikası ve kullanım şartlarını tasarlayın
  - [ ] Otomatik derlemeler için CI/CD pipeline'ını ana hatlarıyla belirtin
- [ ] Android dağıtımı için hazırlayın
  - [ ] İmzalama anahtarlarını yapılandırın
  - [ ] Mağaza listesi varlıklarını oluşturun (ekran görüntüleri, özellik grafiği)
  - [ ] Uygulama açıklamasını ve anahtar kelimeleri yazın
  - [ ] Play Console hesabını ayarlayın
  - [ ] Bir sürüm derlemesi oluşturun
- [ ] iOS dağıtımı için hazırlayın
  - [ ] Sertifikaları ve sağlama profillerini yapılandırın
  - [ ] App Store Connect listesini oluşturun
  - [ ] App Store ekran görüntülerini ve önizlemeyi hazırlayın
  - [ ] Uygulama açıklamasını ve anahtar kelimeleri yazın
  - [ ] Bir sürüm derlemesi oluşturun
- [ ] Analitik ve izlemeyi uygulayın
  - [ ] Çökme raporlamayı ayarlayın
  - [ ] Kullanım analitiğini yapılandırın
  - [ ] Kullanıcı geri bildirim mekanizmasını uygulayın
- [ ] Lansman sonrası aktiviteleri planlayın
  - [ ] Güncelleme yol haritası oluşturun
  - [ ] Kullanıcı destek kanallarını ayarlayın
  - [ ] Pazarlama aktivitelerini planlayın
