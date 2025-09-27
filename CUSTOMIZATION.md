# 🔧 Configuration Examples

This file contains example configurations and customizations for your Google Drive Image Gallery.

## Basic Configuration

Replace these values in `index.html`:

```javascript
// 🔧 CONFIGURATION - Replace with your actual values
const folderId = "1HnGs939Un5no5VSP1eDP7mWIlyKZyWHK"; // Your Google Drive folder ID
const apiKey = "AIzaSyBas_1uDUYdaRlJdTvnI2rIxmcwK6L-FOA";     // Your Google Drive API key

// Pagination settings
let itemsPerPage = 12; // Number of images per page
let currentPage = 1;   // Starting page
```

## Customization Examples

### 1. Change Gallery Title and Subtitle

```html
<!-- In the HTML section -->
<header>
  <h1>🖼️ My Photography Portfolio</h1>
  <p class="subtitle">
    Beautiful moments captured through my lens. 
    Browse through my latest photography work.
  </p>
</header>
```

### 2. Modify Pagination Settings

```javascript
// For a 3x3 grid (9 images per page)
let itemsPerPage = 9;

// For a 4x4 grid (16 images per page)  
let itemsPerPage = 16;

// For a 2x3 grid (6 images per page, good for mobile)
let itemsPerPage = 6;
```

### 3. Change Color Scheme

```css
/* Blue and Purple Gradient */
body {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

/* Green and Blue Gradient */
body {
  background: linear-gradient(135deg, #11998e 0%, #38ef7d 100%);
}

/* Orange and Pink Gradient */
body {
  background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%);
}

/* Dark Theme */
body {
  background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
}
```

### 4. Customize Card Appearance

```css
/* Rounded cards */
.image-card {
  border-radius: 25px; /* More rounded corners */
}

/* Square cards */
.image-card {
  border-radius: 5px; /* Less rounded corners */
}

/* Card shadows */
.image-card {
  box-shadow: 0 10px 40px rgba(0,0,0,0.2); /* Stronger shadow */
}

/* Card sizes */
.image-card img {
  height: 200px; /* Shorter cards */
  /* or */
  height: 300px; /* Taller cards */
}
```

### 5. Add Loading Animations

```css
/* Pulse loading effect */
@keyframes pulse {
  0% { opacity: 1; }
  50% { opacity: 0.5; }
  100% { opacity: 1; }
}

.loading {
  animation: pulse 2s ease-in-out infinite;
}

/* Bounce loading effect */
@keyframes bounce {
  0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
  40% { transform: translateY(-10px); }
  60% { transform: translateY(-5px); }
}

.loading::after {
  animation: bounce 1s ease infinite;
}
```

### 6. Responsive Breakpoints

```css
/* Tablet styles */
@media (max-width: 1024px) {
  .gallery {
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 20px;
  }
  
  h1 {
    font-size: 2.2rem;
  }
}

/* Mobile styles */
@media (max-width: 768px) {
  .gallery {
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 15px;
  }
  
  h1 {
    font-size: 1.8rem;
  }
  
  .pagination {
    padding: 8px 15px;
  }
  
  .page-btn {
    width: 35px;
    height: 35px;
    font-size: 12px;
  }
}

/* Small mobile styles */
@media (max-width: 480px) {
  .gallery {
    grid-template-columns: 1fr 1fr; /* 2 columns on small screens */
    gap: 10px;
  }
  
  body {
    padding: 10px;
  }
}
```

### 7. Multiple Gallery Configurations

If you want different galleries for different types of images:

```javascript
// Portfolio Gallery
const portfolioConfig = {
  folderId: "1HnGs939Un5no5VSP1eDP7mWIlyKZyWHK",
  title: "📷 Photography Portfolio",
  itemsPerPage: 9
};

// Product Gallery  
const productConfig = {
  folderId: "2InHt849Vo6qp6WTQ2fEQ8xJmzLaZyXIL",
  title: "🛍️ Product Catalog",
  itemsPerPage: 12
};

// Event Gallery
const eventConfig = {
  folderId: "3JoIu950Xp7rq7XUR3gFR9yKn0MbAzYJM", 
  title: "🎉 Event Photos",
  itemsPerPage: 15
};
```

### 8. Add Search Functionality

```html
<!-- Add search box -->
<div class="search-container">
  <input type="text" id="searchInput" placeholder="Search images..." />
  <button onclick="searchImages()">🔍</button>
</div>
```

```javascript
// Search function
function searchImages() {
  const searchTerm = document.getElementById('searchInput').value.toLowerCase();
  const filteredImages = allImages.filter(image => 
    image.name.toLowerCase().includes(searchTerm)
  );
  
  displayImages(filteredImages);
}
```

### 9. Add Image Categories/Tags

```javascript
// Add category to image display
function displayCurrentPage() {
  // ... existing code ...
  
  const category = getImageCategory(file.name);
  const categoryTag = document.createElement("div");
  categoryTag.className = "category-tag";
  categoryTag.textContent = category;
  
  cardContent.appendChild(categoryTag);
}

function getImageCategory(filename) {
  const name = filename.toLowerCase();
  if (name.includes('portrait')) return '👤 Portrait';
  if (name.includes('landscape')) return '🏞️ Landscape'; 
  if (name.includes('product')) return '📦 Product';
  return '📷 General';
}
```

### 10. Performance Optimizations

```javascript
// Lazy loading for better performance
const imageObserver = new IntersectionObserver((entries, observer) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const img = entry.target;
      img.src = img.dataset.src;
      img.classList.remove('lazy');
      observer.unobserve(img);
    }
  });
});

// Apply to images
document.querySelectorAll('img[data-src]').forEach(img => {
  imageObserver.observe(img);
});
```

## Environment-Specific Configurations

### Development Setup
```javascript
const isDevelopment = window.location.hostname === 'localhost';

if (isDevelopment) {
  console.log('Development mode: Enhanced logging enabled');
  // Add more detailed logging
}
```

### Production Setup
```javascript
const isProduction = window.location.hostname !== 'localhost';

if (isProduction) {
  // Disable console logs
  console.log = function() {};
  // Add analytics
  // Add error reporting
}
```

## Tips for Different Use Cases

### Photography Portfolio
- Use `itemsPerPage = 6` for fewer, larger images
- Implement lightbox/modal for full-screen viewing  
- Add EXIF data display
- Group by date or location

### Product Catalog
- Use `itemsPerPage = 12` for grid layout
- Add product information overlay
- Implement category filtering
- Add "quick view" functionality

### Event Gallery
- Use `itemsPerPage = 20` for more images per page
- Chronological ordering
- Add date stamps
- Implement bulk download

### Art Gallery
- Use `itemsPerPage = 4` for larger image display
- Add artwork descriptions
- Implement zoom functionality
- Add artist information

Remember to test any customizations across different browsers and devices!
