# 🔧 Troubleshooting Guide

This guide covers common issues and their solutions when setting up the Google Drive Image Gallery.

## 🚨 Common Issues

### 1. Images Not Loading

#### Problem: Blank cards or placeholder images
```
Symptoms:
- Cards appear but no images inside
- Gray placeholder rectangles
- Console errors about failed image loading
```

#### Solutions:

**A. Check Folder Permissions**
```
✅ Steps to fix:
1. Open your Google Drive folder
2. Right-click → Share
3. Ensure it's set to "Anyone with the link can view"
4. If not, change it and click Done
5. Wait 2-3 minutes and refresh your gallery
```

**B. Verify Folder ID**
```
✅ How to get correct Folder ID:
1. Open your folder in Google Drive
2. Look at the URL: https://drive.google.com/drive/folders/1HnGs939Un5no5VSP1eDP7mWIlyKZyWHK
3. Copy everything after "folders/": 1HnGs939Un5no5VSP1eDP7mWIlyKZyWHK
4. Make sure this matches your code
```

**C. Test Folder Accessibility**
```
✅ Test URL (replace with your values):
https://www.googleapis.com/drive/v3/files?q='YOUR_FOLDER_ID'+in+parents&key=YOUR_API_KEY

If this shows JSON data with your files, the setup is correct.
If it shows an error, check the error message below.
```

---

### 2. API Key Issues

#### Problem: "API Error: Requests from referer blocked"
```
Error message:
"API Error: Requests from referer http://localhost:8000/ are blocked."
```

#### Solution:
```
✅ Remove API Key Restrictions:
1. Go to Google Cloud Console
2. Navigate to: APIs & Services → Credentials
3. Click on your API key
4. Under "Application restrictions": Select "None"
5. Click Save
6. Wait 2-3 minutes for changes to take effect
```

#### Problem: "403 Forbidden" or "Invalid API Key"
```
Error message:
"HTTP error! status: 403"
```

#### Solutions:

**A. Check API Key**
```
✅ Verify your API key:
1. Make sure you copied the entire key (no spaces)
2. API keys are usually 39 characters long
3. Should start with "AIza"
```

**B. Enable Google Drive API**
```
✅ Ensure API is enabled:
1. Google Cloud Console → APIs & Services → Library
2. Search: "Google Drive API"
3. Click it and ensure it shows "API enabled"
4. If not, click "Enable"
```

**C. Check Project Selection**
```
✅ Make sure you're using the right project:
1. Top of Google Cloud Console shows current project
2. Click dropdown to switch if needed
3. API key must be from the same project where Drive API is enabled
```

---

### 3. CORS Policy Errors

#### Problem: "blocked by CORS policy"
```
Error message:
"Access to fetch at 'https://www.googleapis.com/drive/v3/files...' 
from origin 'null' has been blocked by CORS policy"
```

#### Solution:
```
✅ Use a web server instead of opening file directly:

Option 1 - Python (if installed):
cd /path/to/your/project
python -m http.server 8000
Open: http://localhost:8000

Option 2 - Node.js (if installed):
npx serve .
Follow the URL shown

Option 3 - VS Code:
Install "Live Server" extension
Right-click index.html → "Open with Live Server"
```

---

### 4. No Images Found

#### Problem: "No images found" message
```
Symptoms:
- Gallery loads but shows "No images found"
- API call succeeds but no images
```

#### Solutions:

**A. Check Image Formats**
```
✅ Supported formats:
- JPG/JPEG ✅
- PNG ✅  
- GIF ✅
- WebP ✅

❌ Not supported:
- Raw files (CR2, NEF, ARW)
- Documents (PDF, DOC)
- Videos (MP4, AVI)
```

**B. Check Folder Structure**
```
✅ Correct structure:
Your Folder/
├── image1.jpg
├── image2.png
└── image3.jpeg

❌ Won't work:
Your Folder/
└── Subfolder/
    ├── image1.jpg
    └── image2.png

Images must be directly in the folder, not in subfolders.
```

---

### 5. Slow Loading

#### Problem: Gallery takes long time to load

#### Solutions:

**A. Too Many Images**
```
✅ Optimize for large collections:
1. Reduce itemsPerPage in code:
   let itemsPerPage = 6; // Instead of 12

2. Or organize into multiple folders
```

**B. Large Image Files**
```
✅ Optimize your images:
1. Recommended size: Under 2MB per image
2. Dimensions: Max 1920x1080 for web display
3. Use online compressors if needed
```

---

### 6. JavaScript Errors

#### Problem: Console shows JavaScript errors

#### Common Error Messages:

**A. "Cannot read property of undefined"**
```
✅ Solution:
1. Make sure all HTML elements exist
2. Check for typos in element IDs
3. Ensure JavaScript runs after page loads
```

**B. "Unexpected token"**
```
✅ Solution:
1. Check for missing commas, brackets, or semicolons
2. Ensure API key and folder ID are in quotes
3. Validate JSON responses in browser dev tools
```

---

### 7. Mobile Issues

#### Problem: Gallery doesn't work on mobile

#### Solutions:

**A. Responsive Issues**
```
✅ Check viewport meta tag is present:
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**B. Touch Events**
```
✅ Ensure touch events work:
- Images should be clickable on mobile
- Pagination buttons should respond to touch
- Modal should close on touch outside
```

---

## 🔍 Debugging Steps

### Step 1: Check Browser Console
```
1. Press F12 (Windows/Linux) or Cmd+Option+I (Mac)
2. Click Console tab
3. Refresh the page
4. Look for error messages (red text)
5. Share screenshots of errors when asking for help
```

### Step 2: Test API Manually
```
1. Open this URL in browser (replace with your values):
   https://www.googleapis.com/drive/v3/files?q='YOUR_FOLDER_ID'+in+parents&key=YOUR_API_KEY

2. Expected result: JSON data with file list
3. If error: Note the exact error message
```

### Step 3: Verify Network Requests
```
1. Browser DevTools → Network tab
2. Refresh page
3. Look for requests to googleapis.com
4. Check status codes (200 = good, 403/404 = problem)
```

---

## 📞 Getting More Help

### Before Asking for Help

Please provide:

1. **Error Messages**: Screenshots of browser console
2. **Your Setup**: 
   - Operating system
   - Browser and version
   - How you're running the gallery (local server, file://, etc.)
3. **What You've Tried**: List the solutions you've already attempted
4. **Configuration**: 
   - Are your folder and API key working in the manual test URL?
   - Is your folder actually public?

### Where to Get Help

1. **GitHub Issues**: Open an issue on the repository
2. **Stack Overflow**: Tag with `google-drive-api` and `javascript`
3. **Google's Documentation**: [Drive API Troubleshooting](https://developers.google.com/drive/api/guides/handle-errors)

---

## ✅ Success Checklist

If your gallery is working correctly, you should see:

- [ ] Images loading and displaying properly
- [ ] Pagination controls working
- [ ] Modal popup on image click
- [ ] Responsive design on mobile
- [ ] No errors in browser console
- [ ] Fast loading (under 5 seconds for first page)

## 🎯 Performance Tips

### Optimize for Better Performance

1. **Limit Images per Page**
   ```javascript
   let itemsPerPage = 8; // Faster loading
   ```

2. **Compress Images**
   - Use tools like TinyPNG or ImageOptim
   - Target: Under 500KB per image

3. **Use CDN**
   - Google Drive acts as a CDN
   - Images are served from Google's fast servers

4. **Preload Critical Resources**
   ```html
   <link rel="preload" href="path-to-critical-css" as="style">
   ```

---

*If none of these solutions help, please open an issue on GitHub with detailed information about your problem and what you've tried.*
