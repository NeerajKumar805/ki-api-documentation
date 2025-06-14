# Kamsid Industries APIs Documention.

## User APIs

### 1. Sign Up

**POST** `/api/users/signup`
**Request**

```json
{
  "username": "neeraj",
  "password": "pass123",
  "mobileNo": "9988776653",
  "email": "neeraj@example.com"
}
```

**Success (201 Created)**

```json
{
  "success": true,
  "message": "Sign up successfully",
  "data": {
    "userId": "neeraj20250615091200",
    "username": "neeraj",
    "isActive": true,
    "isAdmin": false,
    "mobileNo": "9988776653",
    "email": "neeraj@example.com"
  }
}
```

**Error (400 Bad Request)**

```json
{
  "success": false,
  "message": "Mobile number already exists",
  "data": null
}
```

### 2. Login

**POST** `/api/users/login`
**Request**

```json
{
  "loginKey": "neeraj",  // or email or mobileNo
  "password": "pass123"
}
```

**Success (200 OK)**

```json
{
  "success": true,
  "message": "Login successful",
  "data": {
    "userId": "neeraj20250615091200",
    "username": "neeraj",
    "isActive": true,
    "isAdmin": false
  }
}
```

**Error (400 Bad Request)**

```json
{
  "success": false,
  "message": "Invalid credentials",
  "data": null
}
```

### 3. Get All Users

**GET** `/api/users`
**Success (200 OK)**

```json
{
  "success": true,
  "message": "Fetched all users",
  "data": [
    {
      "userId": "neeraj20250615091200",
      "username": "neeraj",
      "isActive": true,
      "isAdmin": false,
      "mobileNo": "9988776653",
      "email": "neeraj@example.com"
    }
  ]
}
```

### 4. Get User by ID

**GET** `/api/users/{userId}`
**Success (200 OK)**

```json
{
  "success": true,
  "message": "User found",
  "data": {
    "userId": "neeraj20250615091200",
    "username": "neeraj",
    "isActive": true,
    "isAdmin": false,
    "mobileNo": "9988776653",
    "email": "neeraj@example.com"
  }
}
```

**Error (404 Not Found)**

```json
{
  "success": false,
  "message": "User not found",
  "data": null
}
```

### 5. Update User (Full)

**PUT** `/api/users/{userId}`
**Request**

```json
{
  "username": "neeraj_upd",
  "password": "newpass123",
  "mobileNo": "9988776653",
  "email": "neeraj_upd@example.com",
  "isActive": false,
  "isAdmin": true
}
```

**Success (200 OK)**

```json
{
  "success": true,
  "message": "User updated successfully",
  "data": {
    "userId": "neeraj20250615091200",
    "username": "neeraj_upd",
    "isActive": false,
    "isAdmin": true,
    "mobileNo": "9988776653",
    "email": "neeraj_upd@example.com"
  }
}
```

**Error (400 Bad Request)**

```json
{
  "success": false,
  "message": "Email already exists",
  "data": null
}
```

### 6. Update User (Partial)

**PATCH** `/api/users/{userId}`
**Request**

```json
{
  "email": "partial@example.com"
}
```

**Success (200 OK)**

```json
{
  "success": true,
  "message": "User patched successfully",
  "data": {
    "userId": "neeraj20250615091200",
    "username": "neeraj",
    "isActive": true,
    "isAdmin": false,
    "mobileNo": "9988776653",
    "email": "partial@example.com"
  }
}
```

### 7. Delete User

**DELETE** `/api/users/{userId}`
**Success (200 OK)**

```json
{
  "success": true,
  "message": "User deleted successfully",
  "data": "neeraj20250615091200"
}
```

---

## Address APIs

### 1. Create Address

**POST** `/api/addresses`
**Request**

```json
{
  "area": "Sector 62",
  "city": "Noida",
  "state": "UP",
  "pin": "201301",
  "user": { "userId": "neeraj20250615091200" }
}
```

**Success (201 Created)**

```json
{
  "success": true,
  "message": "Address added successfully",
  "data": {
    "addressId": 1,
    "area": "Sector 62",
    "city": "Noida",
    "state": "UP",
    "pin": "201301",
    "user": { "userId": "neeraj20250615091200" }
  }
}
```

**Error (404 Not Found)**

```json
{
  "success": false,
  "message": "User not found",
  "data": null
}
```

### 2. Get All Addresses

**GET** `/api/addresses`
**Response (200 OK)**

```json
{
  "success": true,
  "message": "Fetched all addresses",
  "data": [
    {
      "addressId": 1,
      "area": "Sector 62",
      "city": "Noida",
      "state": "UP",
      "pin": "201301",
      "user": {
        "userId": "neeraj20250615091200"
      }
    },
    {
      "addressId": 2,
      "area": "MG Road",
      "city": "Bangalore",
      "state": "Karnataka",
      "pin": "560001",
      "user": {
        "userId": "john20250615091530"
      }
    }
  ]
}
```
---

### 3. Get Address by ID

**GET** `/api/addresses/{id}`
**Error (404 Not Found)**

```json
{
  "success": false,
  "message": "Address not found",
  "data": null
}
```

### 4. Update Address (Full)

**PUT** `/api/addresses/{id}`
**Request**

```json
{
  "area": "New Sector",
  "city": "Noida",
  "state": "UP",
  "pin": "201302",
  "user": { "userId": "neeraj20250615091200" }
}
```

**Success** same format as POST.

### 5. Update Address (Partial)

**PATCH** `/api/addresses/{id}`
**Request**

```json
{ "city": "Greater Noida" }
```

### 6. Delete Address

**DELETE** `/api/addresses/{id}`
**Success**

```json
{
  "success": true,
  "message": "Address deleted successfully",
  "data": "1"
}
```

---

## Product APIs

### 1. Create Product

**POST** `/api/products`
**Request**

```json
{
  "title": "iPhone 16",
  "description": "Latest iPhone",
  "price": 999.99,
  "inStock": true,
  "category": "Electronics"
}
```

**Error (400 Bad Request)**

```json
{
  "success": false,
  "message": "Another product with same title and description exists",
  "data": null
}
```

### 2. Get All Products

**GET** `/api/products`

> No request body
> **Success (200 OK)**

```json
{
  "success": true,
  "message": "Fetched all products",
  "data": [
    {
      "productId": 1,
      "title": "iPhone 16",
      "description": "Latest iPhone",
      "price": 999.99,
      "inStock": true,
      "category": "Electronics"
    },
    {
      "productId": 2,
      "title": "Bluetooth Headphones",
      "description": "Noise-cancelling over-ear",
      "price": 199.99,
      "inStock": true,
      "category": "Audio"
    }
  ]
}
```

### 3. Get Product by ID

**GET** `/api/products/{id}`

> No request body
> **Success (200 OK)**

```json
{
  "success": true,
  "message": "Fetched product",
  "data": {
    "productId": 1,
    "title": "iPhone 16",
    "description": "Latest iPhone",
    "price": 999.99,
    "inStock": true,
    "category": "Electronics"
  }
}
```

**Error (404 Not Found)**

```json
{
  "success": false,
  "message": "Product not found",
  "data": null
}
```

### 4. Update Product (Full)

**PUT** `/api/products/{id}`
**Request**

```json
{
  "title": "iPhone 16 Pro",
  "description": "Upgraded iPhone with Pro features",
  "price": 1199.99,
  "inStock": true,
  "category": "Electronics"
}
```

**Success (200 OK)**

```json
{
  "success": true,
  "message": "Product updated successfully",
  "data": {
    "productId": 1,
    "title": "iPhone 16 Pro",
    "description": "Upgraded iPhone with Pro features",
    "price": 1199.99,
    "inStock": true,
    "category": "Electronics"
  }
}
```

**Error (400 Bad Request — duplicate)**

```json
{
  "success": false,
  "message": "Another product with same title and description exists",
  "data": null
}
```

### 5. Update Product (Partial)

**PATCH** `/api/products/{id}`
**Request**

```json
{
  "price": 899.99
}
```

**Success (200 OK)**

```json
{
  "success": true,
  "message": "Product patched successfully",
  "data": {
    "productId": 1,
    "title": "iPhone 16 Pro",
    "description": "Upgraded iPhone with Pro features",
    "price": 899.99,
    "inStock": true,
    "category": "Electronics"
  }
}
```

**Error (404 Not Found)**

```json
{
  "success": false,
  "message": "Product not found",
  "data": null
}
```

### 6. Delete Product

**DELETE** `/api/products/{id}`

> No request body
> **Success (200 OK)**

```json
{
  "success": true,
  "message": "Product deleted successfully",
  "data": null
}
```

**Error (404 Not Found)**

```json
{
  "success": false,
  "message": "Product not found",
  "data": null
}
```
---

## Order APIs

### 1. Place Order

**POST** `/api/orders`
**Request**

```json
{
  "orderStatus": "PLACED",
  "totalAmount": 1999.98,
  "user": { "userId": "neeraj20250615091200" },
  "shippingAddress": { "addressId": 1 },
  "products": [ { "productId": 1 }, { "productId": 2 } ]
}
```

**Error (400 Bad Request)**

```json
{
  "success": false,
  "message": "At least one product is required",
  "data": null
}
```

### 2. Get All Orders

**GET** `/api/orders`

> No request body
> **Success (200 OK)**

```json
{
  "success": true,
  "message": "Fetched all orders",
  "data": [
    {
      "orderId": 1,
      "orderDate": "2025-06-15T10:00:00",
      "orderStatus": "PLACED",
      "totalAmount": 1199.99,
      "user": { "userId": "neeraj20250615091200" },
      "shippingAddress": { "addressId": 1 },
      "products": [
        { "productId": 1, "title": "iPhone 16 Pro", "description": "...", "price": 1199.99, "inStock": true, "category": "Electronics" }
      ]
    }
  ]
}
```

### 3. Get Order by ID

**GET** `/api/orders/{id}`

> No request body
> **Success (200 OK)**

```json
{
  "success": true,
  "message": "Order fetched",
  "data": {
    "orderId": 1,
    "orderDate": "2025-06-15T10:00:00",
    "orderStatus": "PLACED",
    "totalAmount": 1199.99,
    "user": { "userId": "neeraj20250615091200" },
    "shippingAddress": { "addressId": 1 },
    "products": [
      { "productId": 1, "title": "iPhone 16 Pro", "description": "...", "price": 1199.99, "inStock": true, "category": "Electronics" }
    ]
  }
}
```

**Error (404 Not Found)**

```json
{
  "success": false,
  "message": "Order not found",
  "data": null
}
```

### 4. Update Order (Full)

**PUT** `/api/orders/{id}`
**Request**

```json
{
  "orderStatus": "SHIPPED",
  "totalAmount": 1199.99,
  "user": { "userId": "neeraj20250615091200" },
  "shippingAddress": { "addressId": 1 },
  "products": [ { "productId": 1 } ],
  "orderDate": "2025-06-15T12:00:00"
}
```

**Success (200 OK)**

```json
{
  "success": true,
  "message": "Order updated successfully",
  "data": {
    "orderId": 1,
    "orderDate": "2025-06-15T12:00:00",
    "orderStatus": "SHIPPED",
    "totalAmount": 1199.99,
    "user": { "userId": "neeraj20250615091200" },
    "shippingAddress": { "addressId": 1 },
    "products": [
      { "productId": 1, "title": "iPhone 16 Pro", "description": "...", "price": 1199.99, "inStock": true, "category": "Electronics" }
    ]
  }
}
```

**Error (400 Bad Request — no products)**

```json
{
  "success": false,
  "message": "At least one product is required",
  "data": null
}
```

### 5. Update Order (Partial)

**PATCH** `/api/orders/{id}`
**Request**

```json
{
  "orderStatus": "DELIVERED"
}
```

**Success (200 OK)**

```json
{
  "success": true,
  "message": "Order patched successfully",
  "data": {
    "orderId": 1,
    "orderDate": "2025-06-15T12:00:00",
    "orderStatus": "DELIVERED",
    "totalAmount": 1199.99,
    "user": { "userId": "neeraj20250615091200" },
    "shippingAddress": { "addressId": 1 },
    "products": [ /* same as above */ ]
  }
}
```

**Error (404 Not Found)**

```json
{
  "success": false,
  "message": "Order not found",
  "data": null
}
```

### 6. Delete Order

**DELETE** `/api/orders/{id}`

> No request body
> **Success (200 OK)**

```json
{
  "success": true,
  "message": "Order deleted successfully",
  "data": null
}
```

**Error (404 Not Found)**

```json
{
  "success": false,
  "message": "Order not found",
  "data": null
}
```

---

> **Author:** Neeraj Kumar
