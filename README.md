# Week 7 - E-Commerce App

This is the starter project for the **Week 7 E-Commerce App** in the Flutter course.  
The app demonstrates advanced GetX state management, dependency injection, and dynamic UI updates. It uses mock data from a mock API.

---

## Features

### **Screens**

1. **Home Screen**:
   - Carousel displaying random products.
   - Horizontal category chips for product filtering.
   - Product grid showing other products.

2. **Category Screen**:
   - Displays products filtered by the selected category.

3. **Product Screen**:
   - Shows detailed information about the selected product:
     - Product title and description.
     - Product code.
     - Multiple product images (opens in a pager view).
     - Price tags: `actual` and `onSale`.
     - User comments displayed below product details.

4. **Basket Screen**:
   - Displays a list of items currently added to the basket.
   - Shows the total price of items.
   - Includes a "Clear" button to empty the basket.
   - Features a "Buy Now" button (no action yet).

---

## Concepts Covered

- **GetX State Management**:
  - Reactive controllers to manage app state, including basket contents.
- **Dependency Injection**:
  - Inject and manage controllers using `Bindings`.
- **API Integration**:
  - Fetch and parse mock data from a mock API.
- **Dynamic UI**:
  - Use reactive variables to update the UI seamlessly.
- **Advanced Widgets**:
  - Carousel, horizontal chips, and grid layouts.

---

## Project Structure

- **Main Code**: Located in `lib/main.dart`.
- **Screens**:
  - `home_screen.dart`: Displays the home page with carousel, categories, and product grid.
  - `category_screen.dart`: Filters and displays products by category.
  - `product_screen.dart`: Shows product details and user comments.
  - `basket_screen.dart`: Manages and displays items in the basket.
- **Controllers**:
  - Separate controllers for managing product, category, and basket state.
- **Data**:
  - Mock JSON data fetched from a mock API.
  - Data models for parsing and displaying product and category information.

---

## Development Steps

This repository contains multiple commits, each representing a milestone in the app's development.  
You can roll back to any state to follow along with the class:

1. **Initial Template**: Empty Flutter app with GetX setup.
2. **Home Screen**: Add carousel, category chips, and product grid.
3. **Category Screen**: Filter and display products by category.
4. **Product Screen**: Display detailed product information with a pager for images.
5. **Basket Screen**: Manage and display basket items with total price.
6. **Final App**: Completed E-Commerce App with mock API integration and full functionality.

Use the following command to check out a specific commit:
```bash
git checkout <commit-hash>
```

---

## Getting Started

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/ilkerokutman/acik-atolye-w07-ecommerce_app.git
   ```
2. **Navigate to the Project Directory**:
   ```bash
   cd w07-ecommerce-app
   ```
3. **Run the App**:
   - Ensure you have Flutter installed.
   - Start the app using:
     ```bash
     flutter run
     ```

---

## Contribution

Please refer to the [CONTRIBUTION.md](CONTRIBUTION.md) file for guidelines on contributing to this repository.

---

## License

This project is licensed under the [MIT License](LICENSE).
