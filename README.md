# MuffinBrandsCDN
Documentation for api

# API Documentation for RadioCast File Upload Service

## Base URL
```
http://musicfiles.radiocast.net
```

## Endpoints

### 1. Upload a File
**Endpoint:**
```
POST /upload
```
**Description:**
Uploads a file to the server.

**Request:**
- Content-Type: `multipart/form-data`
- Form Field: `file` (the file to be uploaded)

**Response:**
- **200 OK**: Returns a JSON object with the file URL.
- **400 Bad Request**: Returns an error if no file is uploaded or the file type is not allowed.

**Example Request using cURL:**
```sh
curl -X POST -F "file=@path/to/your/file.png" http://musicfiles.radiocast.net/upload
```

**Example Successful Response:**
```json
{
  "url": "http://musicfiles.radiocast.net/abcd1234"
}
```

**Example Error Response:**
```json
{
  "error": "No file part"
}
```

---

### 2. Retrieve a File
**Endpoint:**
```
GET /<filename>
```
**Description:**
Retrieves a file by its unique name (without extension).

**Path Parameters:**
- `filename` (string): The unique identifier of the uploaded file (without extension).

**Response:**
- **200 OK**: Returns the file if found.
- **404 Not Found**: If the file does not exist.

**Example Request:**
```
GET http://musicfiles.radiocast.net/abcd1234
```

**Example Error Response:**
```json
{
  "error": "File not found"
}
```

---

## Notes
- Supported file types include images, videos, audio, documents, archives, and scripts.
- Files are stored under `mediaforradiocast` with images saved in `mediaforradiocast/pictures`.
- Uploaded file history is stored in user cookies for tracking past uploads.
- Files can be accessed directly using their unique identifier without specifying an extension.

