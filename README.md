#Kamsid Industries APIs Documention.

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
**200 OK**

```json
{
  "success": true,
  "message": "Fetched all addresses",
  "data": [ /* list of addresses */ ]
}
```

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

### 3. Get Product by ID

**GET** `/api/products/{id}`

### 4. Update Product (Full)

**PUT** `/api/products/{id}`
**Request** same full product JSON

### 5. Update Product (Partial)

**PATCH** `/api/products/{id}`
**Request**

```json
{ "price": 899.99 }
```

### 6. Delete Product

**DELETE** `/api/products/{id}`

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

### 3. Get Order by ID

**GET** `/api/orders/{id}`

### 4. Update Order (Full)

**PUT** `/api/orders/{id}`
**Request** same full order JSON

### 5. Update Order (Partial)

**PATCH** `/api/orders/{id}`
**Request**

```json
{ "orderStatus": "SHIPPED" }
```

### 6. Delete Order

**DELETE** `/api/orders/{id}`

---

Please review this in-chat documentation. Once you confirm it’s exactly what you want, I’ll regenerate the PDF so it’s complete.
