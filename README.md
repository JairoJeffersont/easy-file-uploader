# EasyFileUploader

`EasyFileUploader` is a lightweight PHP class to handle file uploads and deletions safely and easily.  
It includes validation for **MIME type**, **file size**, automatic **directory creation**, and provides a simple API for removing files from the server.

---

## 📦 Installation

Install the package via Composer:

```bash
composer require jairojeffsantos/easy-file-uploader
```

---

## 🚀 Usage

### Import the class

```php
use JairoJeffSantos\EasyFileUploader;
```

---

### Uploading a file

```php
$result = EasyFileUploader::uploadFile(
    __DIR__ . '/uploads',        // Destination directory
    $_FILES['myfile'],           // File from form
    ['image/jpeg', 'image/png'], // Allowed MIME types
    5                            // Max size in MB
);

if ($result['status'] === 'success') {
    echo "File uploaded to: " . $result['file_path'];
} else {
    echo "Upload failed: " . $result['status'];
}
```

✅ Example of possible statuses:  
- "success" → file uploaded successfully  
- "format_not_allowed" → file type not permitted  
- "max_file_size_exceeded" → file is too large  
- "directory_creation_failed" → destination folder could not be created  
- "file_already_exists" → a file with the same name already exists  
- "move_failed" → upload failed  

---

### Deleting a file

```php
$result = EasyFileUploader::deleteFile(__DIR__ . '/uploads/file_12345.png');

if ($result['status'] === 'success') {
    echo "File deleted successfully.";
} else {
    echo "Error: " . $result['status'];
}
```

✅ Example of possible statuses:  
- "success" → file deleted successfully  
- "file_not_found" → file does not exist  
- "delete_failed" → unable to remove the file  

---

## ⚙️ Features

- ✅ File type (MIME) validation  
- ✅ File size validation  
- ✅ Automatic creation of destination directories  
- ✅ Unique file name generation (to avoid conflicts)  
- ✅ Easy file deletion  

---

## 📄 License

MIT License. Free to use, modify, and distribute.
