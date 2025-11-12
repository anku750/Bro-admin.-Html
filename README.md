
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Brocool Admin Panel</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #00b09b, #96c93d);
      color: #fff;
      text-align: center;
      padding: 40px;
    }
    h1 { margin-bottom: 10px; }
    input, button {
      margin: 5px;
      padding: 10px;
      border-radius: 10px;
      border: none;
      font-size: 14px;
    }
    .product {
      background: rgba(255,255,255,0.15);
      border-radius: 10px;
      padding: 15px;
      margin: 10px auto;
      width: 300px;
    }
    img {
      width: 100%;
      border-radius: 10px;
    }
    button {
      background: white;
      color: #333;
      font-weight: bold;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>🧊 Brocool Admin Panel</h1>
  <p>Add new product below:</p>
  <input type="text" id="productName" placeholder="Product Name">
  <input type="text" id="productPrice" placeholder="Price (₹)">
  <input type="file" id="productImage" accept="image/*">
  <button onclick="addProduct()">Add Product</button>
  
  <h2>All Products</h2>
  <div id="productList"></div>

  <script>
    const productList = document.getElementById("productList");
    let products = JSON.parse(localStorage.getItem("brocoolProducts")) || [];

    function renderProducts() {
      productList.innerHTML = "";
      products.forEach((p, i) => {
        productList.innerHTML += `
          <div class="product">
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Brocool Admin Panel</title>
  <script type="module">
    // Import Firebase
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.14.0/firebase-app.js";
    import { getDatabase, ref, push, onValue, remove } from "https://www.gstatic.com/firebasejs/10.14.0/firebase-database.js";

    const firebaseConfig = {
      apiKey: "AIzaSyAXPNe0d1O68SqhvwS2B0B9OLXz9tq7w_4",
      authDomain: "brocool-3d4cb.firebaseapp.com",
      projectId: "brocool-3d4cb",
      storageBucket: "brocool-3d4cb.firebasestorage.app",
      messagingSenderId: "858556273626",
      appId: "1:858556273626:web:65cfb6d9e99b9688dba6e3",
      measurementId: "G-W80N31YFKQ"
    };

    const app = initializeApp(firebaseConfig);
    const db = getDatabase(app);

    // Add Product Function
    window.addProduct = function() {
      const name = document.getElementById("productName").value;
      const price = document.getElementById("productPrice").value;
      const file = document.getElementById("productImage").files[0];

      if (!name || !price || !file) return alert("Please fill all fields!");

      const reader = new FileReader();
      reader.onload = function(e) {
        const image = e.target.result;
        const productRef = ref(db, "products");
        push(productRef, { name, price, image });
        alert("✅ Product added successfully!");
        document.getElementById("productName").value = "";
        document.getElementById("productPrice").value = "";
        document.getElementById("productImage").value = "";
      };
      reader.readAsDataURL(file);
    };

    // Load Products
    const productList = document.getElementById("productList");
    const productsRef = ref(db, "products");
    onValue(productsRef, (snapshot) => {
      productList.innerHTML = "";
      snapshot.forEach((child) => {
        const data = child.val();
        const key = child.key;
        productList.innerHTML += `
          <div class="product">
            <img src="${data.image}" alt="${data.name}">
            <h3>${data.name}</h3>
            <p>₹${data.price}</p>
            <button onclick="deleteProduct('${key}')">Delete</button>
          </div>`;
      });
    });

    // Delete Product
    window.deleteProduct = function(id) {
      const delRef = ref(db, "products/" + id);
      remove(delRef);
      alert("🗑️ Product deleted!");
    };
  </script>

  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #00b09b, #96c93d);
      color: #fff;
      text-align: center;
      padding: 40px;
    }
    h1 { margin-bottom: 10px; }
    input, button {
      margin: 5px;
      padding: 10px;
      border-radius: 10px;
      border: none;
      font-size: 14px;
    }
    .product {
      background: rgba(255,255,255,0.15);
      border-radius: 10px;
      padding: 15px;
      margin: 10px auto;
      width: 300px;
    }
    img {
      width: 100%;
      border-radius: 10px;
    }
    button {
      background: white;
      color: #333;
      font-weight: bold;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>🧊 Brocool Admin Panel</h1>
  <p>Add new product below:</p>
  <input type="text" id="productName" placeholder="Product Name">
  <input type="text" id="productPrice" placeholder="Price (₹)">
  <input type="file" id="productImage" accept="image/*">
  <button onclick="addProduct()">Add Product</button>

  <h2>All Products</h2>
  <div id="productList"></div>
</body>
</html>
