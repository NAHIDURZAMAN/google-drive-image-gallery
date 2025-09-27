# 🖼️ Google Drive Image Gallery

A beautiful, responsive image gallery that displays images directly from Google Drive using Google Drive API. Perfect for showcasing products, portfolio, or any image collection with elegant pagination and modal viewing.

## 🌟 Features

- ✨ **Beautiful UI**: Modern gradient background with glass-morphism effects
- 📱 **Fully Responsive**: Works perfectly on all devices
- 🔄 **Pagination**: Smart pagination system with page numbers
- 🖼️ **Modal Viewing**: Click to view full-size images
- ⚡ **Fast Loading**: Optimized image loading with fallback URLs
- 🎨 **Modern Design**: Cards with hover effects and smooth animations
- 🌐 **Easy Setup**: Just replace API key and folder ID

## 🚀 Live Demo

Open `index.html` in your browser to see the gallery in action!

## 📋 Prerequisites

Before using this gallery, you need:

1. **Google Cloud Console Account**
2. **Google Drive folder with images**
3. **Google Drive API Key**

## 🛠️ Setup Instructions

### Step 1: Create Google Drive API Key

1. **Go to Google Cloud Console**
   - Visit [Google Cloud Console](https://console.cloud.google.com/)
   - Sign in with your Google account

2. **Create or Select a Project**
   - Click on project dropdown at the top
   - Create new project or select existing one

3. **Enable Google Drive API**
   ```
   Navigate to: APIs & Services > Library
   Search for: "Google Drive API"
   Click: Enable
   ```

4. **Create API Key**
   ```
   Navigate to: APIs & Services > Credentials
   Click: + CREATE CREDENTIALS
   Select: API Key
   Copy the generated API key
   ```

5. **Configure API Key (Optional but Recommended)**
   ```
   Click on your API key to edit
   Application restrictions: None (for testing)
   API restrictions: Restrict to Google Drive API
   ```

### Step 2: Prepare Google Drive Folder

1. **Create a folder in Google Drive**
2. **Upload your images** to this folder
3. **Make folder public:**
   ```
   Right-click folder → Share
   Change access: Anyone with the link can view
   Click: Done
   ```
4. **Get Folder ID:**
   ```
   Copy folder URL: https://drive.google.com/drive/folders/FOLDER_ID_HERE
   Extract the FOLDER_ID_HERE part
   ```

### Step 3: Configure the Gallery

1. **Open `index.html`** in a text editor
2. **Find these lines** (around line 280):
   ```javascript
   const folderId = "YOUR_FOLDER_ID_HERE";
   const apiKey = "YOUR_API_KEY_HERE";
   ```
3. **Replace with your values:**
   ```javascript
   const folderId = "1HnGs939Un5no5VSP1eDP7mWIlyKZyWHK"; // Your actual folder ID
   const apiKey = "AIzaSyBas_1uDUYdaRlJdTvnI2rIxmcwK6L-FOA";     // Your actual API key
   ```

### Step 4: Test Your Gallery

1. **Open `index.html`** in a web browser
2. **Check browser console** (F12) for any errors
3. **If images don't load:**
   - Verify folder is public
   - Check API key is correct
   - Ensure API key has no domain restrictions

## 🔧 Customization

### Change Items Per Page
```javascript
let itemsPerPage = 12; // Change this number (line ~285)
```

### Modify Gallery Title
```html
<h1>🖼️ Your Gallery Title</h1> <!-- Line ~92 -->
```

### Customize Colors
```css
/* Main gradient background */
background: linear-gradient(135deg, #1a2a6c, #2a3a7c, #3a4a8c);

/* Card hover color */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

### Image Card Size
```css
.image-card {
  /* Change card dimensions */
  height: 300px; /* Adjust as needed */
}
```

## 📁 Project Structure

```
📦 Google-Drive-Gallery/
├── 📄 index.html          # Main gallery file
├── 📄 README.md           # This documentation
├── 📄 setup-guide.md      # Detailed setup guide
├── 📄 troubleshooting.md  # Common issues and solutions
└── 📄 LICENSE             # MIT License
```

## 🚨 Troubleshooting

### Images Not Loading?

1. **Check API Key**
   ```javascript
   // Test your API key by opening this URL in browser:
   https://www.googleapis.com/drive/v3/files?q='YOUR_FOLDER_ID'+in+parents&key=YOUR_API_KEY
   ```

2. **Folder Not Public**
   - Make sure folder sharing is set to "Anyone with the link can view"

3. **CORS Issues**
   - Use a local server instead of opening file:// directly
   - Try: `python -m http.server 8000` in terminal

4. **API Key Restrictions**
   ```
   Google Cloud Console → Credentials → Your API Key
   Set "Application restrictions" to "None"
   ```

### Common Error Messages:

| Error | Solution |
|-------|----------|
| `API Error: Requests from referer blocked` | Remove API key domain restrictions |
| `403 Forbidden` | Check folder permissions and API key |
| `404 Not Found` | Verify folder ID is correct |
| `CORS policy` | Use a web server, not file:// |

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Google Drive API for providing the backend
- Modern CSS features for beautiful styling
- Community feedback for improvements

## 📞 Support

If you have any questions or need help:

1. **Check the [Troubleshooting Guide](troubleshooting.md)**
2. **Open an issue** on GitHub
3. **Star the repo** if it helped you! ⭐

---

### 🔗 Useful Links

- [Google Cloud Console](https://console.cloud.google.com/)
- [Google Drive API Documentation](https://developers.google.com/drive/api)
- [Web Fundamentals - Responsive Images](https://developers.google.com/web/fundamentals/design-and-ux/responsive/images)

---

**Made with ❤️ by [Your Name]**

*Feel free to use this code for your projects and share with others!*
