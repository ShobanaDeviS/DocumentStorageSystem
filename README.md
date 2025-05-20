# 📄 Secure Document Storage System

This project is a secure document storage system built using **ASP.NET Core**, **JWT Authentication**, and **Entity Framework Core** with file versioning and BLOB storage in **SQL Server**.

---

## 🧩 Features

- 🔐 User registration and login with JWT-based authentication
- 📁 Document upload (with version control)
- 📥 File download (latest or specific version using `?revision=X`)
- 🔒 Each user can access only their own files
- 💾 Files stored in SQL Server as BLOBs
- 🔬 Swagger UI for API testing
- 🧪 xUnit-ready for unit testing
- 🌐 Basic frontend in HTML + JavaScript (optional)

---

## 🛠 Tech Stack

- Backend: ASP.NET Core Web API (.NET 9)
- Auth: JWT (JSON Web Tokens)
- Database: SQL Server with EF Core
- Frontend: HTML + JS (inside `wwwroot`)
- Testing: xUnit (optional)
- Docs: Swagger (OpenAPI)

---

## 🚀 Getting Started

### 1. Clone and Restore Packages

```bash
git clone <repo-url>
cd DocumentStorageSystem
dotnet restore
```

### 2. Update Configuration

Edit `appsettings.json`:

```json
"ConnectionStrings": {
  "DefaultConnection": "Server=localhost;Database=DocStorageDb;Trusted_Connection=True;TrustServerCertificate=True;"
},
"Jwt": {
  "Key": "MyUltraSecureSecretKey_2025_XYZ",
  "Issuer": "DocumentStorageSystem",
  "Audience": "DocumentStorageSystem"
}
```

---

### 3. Create Database

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

---

### 4. Run the Application

```bash
dotnet run
```

Visit:
- API docs: `https://localhost:<port>/swagger`
- Frontend: `https://localhost:<port>/wwwroot/index.html`

---

## 📦 API Endpoints

### 🔐 Auth
| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/auth/register` | POST | Register user `{ username, password }` |
| `/api/auth/login` | POST | Login user `{ username, password }` |

### 📁 Document
| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/documents/upload` | POST | Upload document (multipart/form-data) |
| `/api/documents/{fileName}` | GET | Download latest or specific version |

Use query param: `?revision=0` for older versions

---

## 🔑 Using Swagger with JWT

1. Call `/api/auth/login` and copy the returned token
2. Click 🔐 `Authorize` in Swagger
3. Paste: `Bearer <your_token_here>`

---

## 🧠 AI Tools Used

- ChatGPT (for code generation and documentation)
- BlackBox

---

## 📹 Demo (Optional)

Link to demo video showing:
- Register/Login
- Uploading and downloading files
- Swagger usage

---

