# ecommerce

# 🛍️ Vue Product Display (Task 5 - project-based virtual intern)

This is a simple Vue.js project that fetches product data from [Fake Store API](https://fakestoreapi.com/) and displays it based on category: **Men's Clothing**, **Women's Clothing**, or **Unavailable Product**.

Each category section has different styles including layout colors, button themes, and product name styling. When a product is unavailable, a custom layout is shown with a background image and centered overlay text.

---

## 🚀 Features

- Fetch product by index (`1–20`) from FakeStore API
- Display product details dynamically
- Switch to next product with a button
- Category-specific styling:
  - Men's clothing (blue)
  - Women's clothing (pink)
  - Unavailable product (gray/white with overlay)
- Loader animation while fetching
- Responsive layout with clean UI

---

## 🧱 Tech Stack

- **Vue 3**
- **JavaScript (ES6)**
- **HTML & CSS (Vanilla)**
- **FakeStore API**

---

## 📦 How to Run Locally

1. **Clone the repo**

```bash
git clone https://github.com/salsabilatts/task5.git
cd task5

## 🚀 Deployment with Docker & CI/CD

This project uses Docker to containerize the Vue.js app.

**Build the Docker image:**

```bash
docker build -t vue-product-app .

Run the container:
docker run -d -p 8080:80 --name vue-product-container vue-product-app

The app will be available at http://localhost:8080.

⚙️ CI/CD with GitHub Actions
This project includes a GitHub Actions workflow for CI/CD that:

Builds the Docker image.
Pushes it to Docker Hub.
Every push to the main branch will trigger the build and deployment to Docker Hub.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```
✨ Author
Salsabila A. 
