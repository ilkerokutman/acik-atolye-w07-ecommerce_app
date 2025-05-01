# E-Commerce App - Technical Documentation

## E-Commerce App Documentation

This document outlines the architecture, components, and functionality of the E-Commerce App.

## Architecture Overview

### Layer Structure

The application follows a domain-oriented architecture with clear separation of concerns:

```
┌─────────────────────────────────────────────────────────────────┐
│                           UI Layer                               │
│                                                                 │
│  ┌─────────────┐   ┌─────────────┐   ┌─────────────┐            │
│  │   Screens   │   │   Widgets   │   │ UI Components│            │
│  └─────────────┘   └─────────────┘   └─────────────┘            │
└───────────────────────────┬─────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│                      Controller Layer                           │
│                                                                 │
│  ┌─────────────┐   ┌─────────────┐   ┌─────────────┐            │
│  │  GetX State │   │ UI Logic    │   │ Navigation  │            │
│  │ Management   │   │             │   │             │            │
│  └─────────────┘   └─────────────┘   └─────────────┘            │
└───────────────────────────┬─────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│                      Repository Layer                           │
│                                                                 │
│  ┌─────────────┐   ┌─────────────┐   ┌─────────────┐            │
│  │ Data Access │   │ Model       │   │ Business    │            │
│  │ Logic       │   │ Conversion  │   │ Logic       │            │
│  └─────────────┘   └─────────────┘   └─────────────┘            │
└───────────────────────────┬─────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│                        Data Layer                               │
│                                                                 │
│  ┌─────────────┐   ┌─────────────┐   ┌─────────────┐            │
│  │ API Provider│   │ Local       │   │ Models      │            │
│  │             │   │ Storage     │   │             │            │
│  └─────────────┘   └─────────────┘   └─────────────┘            │
└─────────────────────────────────────────────────────────────────┘
```

### Domain-Specific Flow Example (Product)

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  product_screen │     │    product_     │     │    product_     │
│    (UI Layer)   │◄───►│   controller    │◄───►│   repository    │
└─────────────────┘     │ (Control Layer) │     │  (Repo Layer)   │
                        └─────────────────┘     └────────┬────────┘
                                                         │
                                                         ▼
                                               ┌─────────────────┐
                                               │   api_provider  │
                                               │   (Data Layer)  │
                                               └─────────────────┘
```

## Project Overview
This document provides technical details for the Week 7 E-Commerce App Flutter project. The application demonstrates advanced GetX state management, dependency injection, and dynamic UI updates using mock data from a mock API.

## Architecture

### State Management
The application will use GetX for state management. GetX provides a simple and powerful way to manage application state with minimal boilerplate code.

Key components:
- **Controllers**: Manage state for specific features (products, categories, basket, profile)
- **Reactive Variables**: Update UI automatically when state changes
- **Dependency Injection**: Manage controller lifecycles with a single AppBindings class

### Project Structure
```
lib/
├── main.dart                  # App entry point
├── app/                       # Application layer
│   ├── routes/                # App navigation
│   │   └── app_pages.dart
│   ├── domain/                # Domain-specific features
│   │   ├── home/              # Home domain
│   │   │   ├── controllers/    # Home controllers
│   │   │   │   └── home_controller.dart
│   │   │   ├── screens/        # Home screens
│   │   │   │   └── home_screen.dart
│   │   │   └── widgets/        # Home-specific widgets
│   │   │       └── featured_products_widget.dart
│   │   ├── category/          # Category domain
│   │   │   ├── controllers/    # Category controllers
│   │   │   │   └── category_controller.dart
│   │   │   ├── models/         # Category models
│   │   │   │   └── category.dart
│   │   │   ├── repositories/   # Category repositories
│   │   │   │   └── category_repository.dart
│   │   │   ├── screens/        # Category screens
│   │   │   │   └── category_screen.dart
│   │   │   └── widgets/        # Category-specific widgets
│   │   │       └── category_chip_widget.dart
│   │   ├── product/           # Product domain
│   │   │   ├── controllers/    # Product controllers
│   │   │   │   └── product_controller.dart
│   │   │   ├── models/         # Product models
│   │   │   │   ├── product.dart
│   │   │   │   └── comment.dart
│   │   │   ├── repositories/   # Product repositories
│   │   │   │   └── product_repository.dart
│   │   │   ├── screens/        # Product screens
│   │   │   │   ├── product_screen.dart
│   │   │   │   ├── product_reviews_screen.dart
│   │   │   │   └── product_gallery_screen.dart
│   │   │   └── widgets/        # Product-specific widgets
│   │   │       ├── product_card_widget.dart
│   │   │       ├── product_carousel_widget.dart
│   │   │       └── comment_card_widget.dart
│   │   ├── basket/            # Basket domain
│   │   │   ├── controllers/    # Basket controllers
│   │   │   │   └── basket_controller.dart
│   │   │   ├── models/         # Basket models
│   │   │   │   └── basket_item.dart
│   │   │   ├── screens/        # Basket screens
│   │   │   │   └── basket_screen.dart
│   │   │   └── widgets/        # Basket-specific widgets
│   │   │       └── basket_item_card_widget.dart
│   │   ├── profile/           # Profile domain
│   │   │   ├── controllers/    # Profile controllers
│   │   │   │   ├── profile_controller.dart
│   │   │   │   ├── address_controller.dart
│   │   │   │   ├── payment_method_controller.dart
│   │   │   │   ├── order_controller.dart
│   │   │   │   └── settings_controller.dart
│   │   │   ├── models/         # Profile models
│   │   │   │   ├── user.dart
│   │   │   │   ├── address.dart
│   │   │   │   ├── payment_method.dart
│   │   │   │   ├── order.dart
│   │   │   │   └── settings.dart
│   │   │   ├── repositories/   # Profile repositories
│   │   │   │   └── user_repository.dart
│   │   │   ├── screens/        # Profile screens
│   │   │   │   ├── profile_screen.dart
│   │   │   │   ├── edit_profile_screen.dart
│   │   │   │   ├── addresses_screen.dart
│   │   │   │   ├── payment_methods_screen.dart
│   │   │   │   ├── my_orders_screen.dart
│   │   │   │   └── settings_screen.dart
│   │   │   └── widgets/        # Profile-specific widgets
│   │   │       ├── profile_header_widget.dart
│   │   │       ├── address_card_widget.dart
│   │   │       ├── payment_method_card_widget.dart
│   │   │       ├── order_card_widget.dart
│   │   │       └── settings_tile_widget.dart
│   │   ├── content/           # Content domain
│   │   │   ├── screens/        # Content screens
│   │   │   │   ├── about_screen.dart
│   │   │   │   ├── faq_screen.dart
│   │   │   │   ├── contact_screen.dart
│   │   │   │   ├── help_screen.dart
│   │   │   │   └── privacy_screen.dart
│   │   │   └── widgets/        # Content-specific widgets
│   │   └── shared/            # Shared components across domains
│   │       ├── bindings/       # GetX bindings for dependency injection
│   │       │   └── app_bindings.dart  # Single binding class for all controllers
│   │       ├── models/         # Shared models
│   │       │   └── base_model.dart
│   │       ├── providers/      # Shared API/mock data providers
│   │       │   └── api_provider.dart
│   │       └── widgets/        # Shared reusable UI components
│   │           ├── app_bar_widget.dart
│   │           ├── loading_indicator_widget.dart
│   │           ├── error_message_widget.dart
│   │           ├── empty_state_widget.dart
│   │           └── price_tag_widget.dart
│   └── core/                  # Core functionality
│       ├── constants/          # App constants
│       │   ├── ui_strings.dart   # Text constants
│       │   ├── ui_assets.dart    # Asset path constants
│       │   ├── keys.dart         # Key constants
│       │   └── ui_dimens.dart    # Dimension constants
│       ├── utils/              # Utility functions
│       │   ├── dialog_utils.dart # Dialog utilities
│       │   ├── common_utils.dart # Common utilities
│       │   ├── currency_utils.dart # Currency utilities
│       │   └── image_utils.dart  # Image utilities
│       ├── extensions/         # Extension methods
│       │   ├── string_extensions.dart
│       │   └── context_extensions.dart
│       ├── theme/              # App theming
│       │   ├── app_theme.dart    # Theme configuration
│       │   ├── app_colors.dart   # Color palette
│       │   └── app_text_styles.dart # Text styles
│       └── localization/       # Internationalization
│           ├── app_localizations.dart
│           └── app_translations.dart
└── assets/                    # Static assets
    ├── images/
    └── mock/                  # Mock JSON data
        ├── products.json
        ├── categories.json
        └── profile.json
```

## Data Models

### Product
```dart
class Product {
  final int id;
  final String title;
  final String description;
  final String code;
  final List<String> images;
  final double price;
  final double? salePrice;
  final int categoryId;
  final List<Comment> comments;
  
  // Constructor and fromJson methods
}
```

### Category
```dart
class Category {
  final int id;
  final String name;
  final String icon;
  
  // Constructor and fromJson methods
}
```

### BasketItem
```dart
class BasketItem {
  final Product product;
  int quantity;
  
  // Constructor and methods to calculate total price
}
```

### Comment
```dart
class Comment {
  final int id;
  final String userName;
  final String text;
  final double rating;
  final DateTime date;
  
  // Constructor and fromJson methods
}
```

### User
```dart
class User {
  final int id;
  final String name;
  final String email;
  final String phone;
  final String avatar;
  final DateTime memberSince;
  
  // Constructor and fromJson methods
}
```

### Address
```dart
class Address {
  final int id;
  final String title;
  final String fullAddress;
  final String postalCode;
  final String city;
  final String district;
  final bool isDefault;
  
  // Constructor and fromJson methods
}
```

### PaymentMethod
```dart
class PaymentMethod {
  final int id;
  final String type;
  final String title;
  final String cardNumber;
  final String cardHolder;
  final String expiryDate;
  final bool isDefault;
  
  // Constructor and fromJson methods
}
```

### Settings
```dart
class Settings {
  bool emailNotifications;
  bool smsNotifications;
  bool pushNotifications;
  bool promotions;
  String themeMode; // 'light', 'dark', or 'system'
  
  // Constructor and methods
}
```

## API Integration

The app will use a mock API to fetch data. The mock data will be stored in JSON files in the assets folder.

### API Provider
```dart
class ApiProvider {
  Future<List<Product>> getProducts() async {
    // Fetch and parse products from mock data
  }
  
  Future<List<Category>> getCategories() async {
    // Fetch and parse categories from mock data
  }
  
  Future<Product> getProductDetails(int id) async {
    // Fetch and parse product details from mock data
  }
  
  Future<User> getUserProfile() async {
    // Fetch and parse user profile from mock data
  }
  
  Future<List<Address>> getUserAddresses() async {
    // Fetch and parse user addresses from mock data
  }
  
  Future<List<PaymentMethod>> getUserPaymentMethods() async {
    // Fetch and parse user payment methods from mock data
  }
}
```

## Dependency Injection

The app will use a single binding class to inject all controllers. All controllers will be registered with `permanent: true` to ensure they remain in memory throughout the app lifecycle:

```dart
class AppBindings extends Bindings {
  @override
  Future<void> dependencies() async {
    // Register providers first
    await Get.putAsync(() async => ApiProvider(), permanent: true);
    
    // Register repositories
    await Get.putAsync(() async => ProductRepository(apiProvider: Get.find()), permanent: true);
    await Get.putAsync(() async => CategoryRepository(apiProvider: Get.find()), permanent: true);
    await Get.putAsync(() async => UserRepository(apiProvider: Get.find()), permanent: true);
    
    // Register controllers with permanent: true to keep them in memory
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

## Screens

### Home Screen
- Displays a carousel of featured products
- Shows category chips for filtering
- Displays a grid of products

### Category Screen
- Shows products filtered by the selected category
- Allows sorting and further filtering

### Product Screens
- **Product Screen**: Displays detailed product information, images, price, and basic reviews
- **Product Reviews Screen**: Shows full list of user comments and ratings
- **Product Gallery Screen**: Displays all product images in a fullscreen gallery

### Basket Screen
- Lists items added to the basket
- Shows quantity controls for each item
- Displays total price
- Provides options to clear basket or proceed to checkout

### Profile Screens
- **Profile Screen**: Displays user information and navigation to other profile sections
- **Edit Profile Screen**: Allows editing display name and profile photo
- **Addresses Screen**: Lists user addresses with add/edit/remove capabilities
- **Payment Methods Screen**: Lists payment methods with add/edit/remove capabilities
- **My Orders Screen**: Lists user orders with details and status
- **Settings Screen**: Allows changing notification preferences and theme settings (dark/light)

### Content Screens
- **About Screen**: Information about the app and company
- **FAQ Screen**: Frequently asked questions
- **Contact Screen**: Contact information and form
- **Help Screen**: Help and support information
- **Privacy Screen**: Privacy policy and terms of service

## Navigation
The app will use GetX for navigation between screens.

```dart
// Routes definition
class AppPages {
  static final routes = [
    GetPage(name: '/home', page: () => HomeScreen()),
    GetPage(name: '/category/:id', page: () => CategoryScreen()),
    GetPage(name: '/basket', page: () => BasketScreen()),
    
    // Product routes
    GetPage(name: '/product/:id', page: () => ProductScreen()),
    GetPage(name: '/product/:id/reviews', page: () => ProductReviewsScreen()),
    GetPage(name: '/product/:id/gallery', page: () => ProductGalleryScreen()),
    
    // Profile routes
    GetPage(name: '/profile', page: () => ProfileScreen()),
    GetPage(name: '/profile/edit', page: () => EditProfileScreen()),
    GetPage(name: '/profile/addresses', page: () => AddressesScreen()),
    GetPage(name: '/profile/payment-methods', page: () => PaymentMethodsScreen()),
    GetPage(name: '/profile/orders', page: () => MyOrdersScreen()),
    GetPage(name: '/profile/settings', page: () => SettingsScreen()),
    
    // Content routes
    GetPage(name: '/about', page: () => AboutScreen()),
    GetPage(name: '/faq', page: () => FaqScreen()),
    GetPage(name: '/contact', page: () => ContactScreen()),
    GetPage(name: '/help', page: () => HelpScreen()),
    GetPage(name: '/privacy', page: () => PrivacyScreen()),
  ];
}
```

## State Management

### ProductController
Manages product data and operations:
- Fetching all products
- Fetching product details
- Filtering products by category
- Managing featured products for carousel

### CategoryController
Manages category data and operations:
- Fetching all categories
- Managing selected category

### BasketController
Manages basket state:
- Adding items to basket
- Removing items from basket
- Updating item quantities
- Calculating total price
- Clearing basket

### ProfileController
Manages user profile data:
- Fetching user profile
- Updating user display name and photo

### AddressController
Manages user addresses:
- Fetching user addresses
- Adding new addresses
- Editing existing addresses
- Removing addresses
- Setting default address

### PaymentMethodController
Manages user payment methods:
- Fetching payment methods
- Adding new payment methods
- Editing existing payment methods
- Removing payment methods
- Setting default payment method

### SettingsController
Manages app settings:
- Notification preferences
- Theme settings (dark/light)

## UI Components

### Shared Widgets
Widgets that are used across multiple features of the app:

#### AppBarWidget
Custom app bar with consistent styling across the app.

#### LoadingIndicatorWidget
Standardized loading indicator used throughout the app.

#### ErrorMessageWidget
Consistent error message display.

#### EmptyStateWidget
Widget for displaying empty state messages.

#### PriceTagWidget
Widget for displaying prices with consistent formatting.

### Feature-Specific Widgets

#### Home Widgets

##### FeaturedProductsWidget
Widget for displaying featured products on the home screen.

#### Category Widgets

##### CategoryChipWidget
Chip widget for displaying and selecting categories.

#### Basket Widgets

##### BasketItemCardWidget
Card for displaying items in the basket with quantity controls.

#### Product Widgets

##### ProductCardWidget
Reusable card for displaying product information in lists and grids.

##### ProductCarouselWidget
Carousel widget for displaying product images.

##### CommentCardWidget
Card for displaying user comments and ratings.

#### Profile Widgets

##### ProfileHeaderWidget
Header widget for displaying user profile information.

##### AddressCardWidget
Card for displaying address information with edit and delete options.

##### PaymentMethodCardWidget
Card for displaying payment method information with edit and delete options.

##### SettingsTileWidget
Tile widget for displaying and changing settings.

## Testing Strategy

The app should include:
- Unit tests for controllers and repositories
- Widget tests for UI components
- Integration tests for key user flows

## Performance Considerations

- Lazy loading of product images
- Pagination for product lists
- Caching of product and category data
- Efficient state management with GetX

## Accessibility

- Proper contrast ratios for text
- Semantic labels for images
- Support for screen readers
- Appropriate touch target sizes

## Future Enhancements

- User authentication
- Order history
- Wishlist functionality
- Product search
- Payment integration
- Push notifications
