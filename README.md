# E-Commerce App

A comprehensive Flutter e-commerce application demonstrating domain-oriented architecture with GetX state management.

## Project Overview

This e-commerce app showcases advanced Flutter development practices including:

- **Domain-Oriented Architecture**: Organized by feature domains rather than technical layers
- **GetX State Management**: Reactive state management with dependency injection
- **Mock API Integration**: Simulated backend with JSON data
- **Comprehensive UI**: Multiple screens covering the full e-commerce experience

## Features

### Home
- Featured products carousel
- Category navigation
- Product recommendations

### Product
- Detailed product information
- Image galleries
- User reviews and ratings
- Related products

### Category
- Category browsing
- Filtered product views
- Sorting and filtering options

### Basket
- Add/remove products
- Quantity adjustment
- Price calculations
- Checkout flow

### Profile
- User information management
- Address management
- Payment method management
- Order history
- Application settings

### Content
- About page
- FAQ
- Contact information
- Help center
- Privacy policy

## Architecture

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

Each domain contains its own:
- Models
- Repository
- Controller
- Screens
- Widgets

## Project Structure

```
lib/
├── main.dart                  # App entry point
├── app/                       # Application layer
│   ├── routes/                # App navigation
│   │   └── app_pages.dart
│   ├── domain/                # Domain-specific features
│   │   ├── home/              # Home domain
│   │   ├── category/          # Category domain
│   │   ├── product/           # Product domain
│   │   ├── basket/            # Basket domain
│   │   ├── profile/           # Profile domain
│   │   ├── content/           # Content domain
│   │   └── shared/            # Shared components
│   └── core/                  # Core functionality
│       ├── constants/         # App constants
│       ├── utils/             # Utility functions
│       ├── extensions/        # Extension methods
│       ├── theme/             # App theming
│       └── localization/      # Internationalization
└── assets/                    # Static assets
    ├── images/
    └── mock/                  # Mock JSON data
```

## Getting Started

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/ilkerokutman/acik-atolye-w07-ecommerce_app.git
   ```

2. **Navigate to the Project Directory**:
   ```bash
   cd acik-atolye-w07-ecommerce_app
   ```

3. **Create Platform-Specific Code**:
   ```bash
   flutter create .
   ```
   This will generate platform-specific code using the latest Flutter SDK.
   
   Alternatively, you can customize the package name and project name:
   ```bash
   flutter create --org=com.mycompany --project-name=my_ecommerce_app .
   ```
   This allows you to set your own organization identifier and project name.

4. **Install Dependencies**:
   ```bash
   flutter pub get
   ```

5. **Run the App**:
   ```bash
   flutter run
   ```

## Development Process

The development process is organized into phases as outlined in the [TASKS.md](TASKS.md) file:

1. **Documentation & Analysis**: Understanding the project requirements
2. **Project Setup**: Setting up the Flutter environment
3. **UI Design Mockups**: Creating mockups for all screens
4. **Core Implementation**: Implementing core utilities and constants
5. **Shared Components**: Implementing shared models, providers, and widgets
6. **Domain Implementation**: Implementing each domain (product, category, etc.)
7. **Integration & Testing**: Connecting all domains and testing
8. **Finalization**: Optimizing and preparing for production

## Documentation

For detailed technical documentation, refer to [DOCUMENTATION.md](DOCUMENTATION.md).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
