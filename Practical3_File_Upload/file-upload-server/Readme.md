#  Practical 3: File Upload System 

This project demonstrates a full-stack file upload system using **Node.js** and **Express** on the backend with potential integration for a **React/Next.js** frontend. It supports secure file storage, validation, and proper error handling.

---

##  Objective

To build a backend API that can:
- Accept multiple files via HTTP POST requests
-  Validate file types and sizes
-  Save files securely on the server
-  Return metadata for uploaded files
-  Handle errors gracefully
-  Allow CORS-based frontend integration

---

##  Technologies Used

- **Node.js** – JavaScript runtime environment
- **Express.js** – Web framework for backend
- **Multer** – Middleware for handling `multipart/form-data`
- **CORS** – Cross-Origin Resource Sharing
- **Morgan** – HTTP request logger
- **Dotenv** – Manage environment variables

---

## Installation & Setup

### 1. **Clone the repository**
```bash
git clone https://github.com/SangayZin/SS2025_WEB102_02230298/tree/main/Practical3_File_Upload/file-upload-server
cd file-upload-server
```

### 2. **Install dependencies**
```bash
npm install
```

### 3. **Create .env file**
```env
PORT=8000
FRONTEND_URL=http://localhost:3000
```

### 4. **Run the server**
```bash
node server.js
```

The server will run at http://localhost:8000.

---

##  API Endpoint

### POST /api/upload

**Description:**
Upload up to 5 files (max size 10MB per file).

**Request:**
- Content-Type: `multipart/form-data`
- Field name: `files`

**Example using curl:**
```bash
curl -X POST http://localhost:8000/api/upload \
  -F "files=@./sample1.jpg" \
  -F "files=@./sample2.pdf"
```

**Success Response:**
```json
{
  "success": true,
  "message": "Files uploaded successfully",
  "files": [
    {
      "originalName": "sample1.jpg",
      "filename": "files-1717583432235-123456789.jpg",
      "size": 123456,
      "mimetype": "image/jpeg",
      "path": "uploads/files-1717583432235-123456789.jpg"
    },
    ...
  ]
}
```

---

## 🛡️ File Restrictions

-  **Allowed Types:** .jpg, .jpeg, .png, .gif, .pdf, .doc, .docx
-  **Max File Size:** 10 MB
-  **Max File Count:** 5

---

##  Error Handling

| Error | Message |
|-------|---------|
| Missing files | No files uploaded |
| Invalid file type | Invalid file type. Only JPEG, PNG, GIF, PDF, DOC, DOCX files are allowed. |
| File too large | File too large. Maximum size is 10MB. |
| Too many files | Too many files. Maximum is 5 files. |

---

##  CORS Configuration

```js
app.use(cors({
  origin: process.env.FRONTEND_URL,
  methods: ['GET', 'POST'],
  credentials: true
}));
```

Set the correct frontend origin in `.env` under `FRONTEND_URL`.

---

##  Directory Structure

```bash
file-upload-server/
├── uploads/               # Uploaded files saved here
├── server.js              # Main server file
├── .env                   # Environment variables
├── package.json           # Project dependencies
```

---

##  Future Enhancements

-  Upload progress tracking
-  Cloud storage integration (e.g., AWS S3)
-  User authentication for protected uploads
- File preview support in frontend