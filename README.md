# 🌐 ClassCentral Hindi Scraper

A powerful Python tool that scrapes the ClassCentral website and translates all content to Hindi, creating a fully functional Hindi version of the platform.

## 📋 Overview

This project automatically:
- **Scrapes** ClassCentral's website content
- **Translates** all text content to Hindi using Google Translate
- **Downloads** all assets (CSS, JS, images) locally
- **Creates** a deployable static website


## 🔧 How The Scraping and Website Creation Works

### 1. **Web Scraping Process**

The scraper employs a sophisticated multi-phase approach with intelligent resource management:

#### Phase 1: Link Discovery & Analysis
- **Homepage Crawling**: Fetches and analyzes `https://www.classcentral.com/`
- **HTML Parsing**: Uses BeautifulSoup4 for robust HTML parsing
- **Link Extraction**: Discovers all internal navigation links and course pages
- **Queue Management**: Creates a prioritized list of pages to process
- **Duplicate Prevention**: Ensures each page is processed only once

#### Phase 2: Content Processing Pipeline
For each discovered page, the scraper executes this comprehensive workflow:

1. **Content Fetching**
   - Sends HTTP requests with proper User-Agent headers
   - Implements timeout handling and retry logic
   - Validates response status and content type

2. **Asset Discovery & Download**
   - Identifies all CSS, JavaScript, and image dependencies
   - Downloads external resources with intelligent filename generation
   - Updates HTML references to point to local asset paths

3. **Content Translation**
   - Translates visible text elements to Hindi using Google Translate API
   - Preserves HTML structure, formatting, and semantic meaning
   - Implements rate limiting to avoid API restrictions

4. **Link Processing**
   - Converts internal navigation links to relative paths
   - Ensures complete offline functionality
   - Maintains site navigation structure and user experience

5. **File Generation**
   - Creates clean, optimized HTML files with UTF-8 encoding
   - Organizes assets in structured, maintainable directories
   - Generates comprehensive navigation index

### 2. **Asset Management**

The scraper intelligently handles all website assets with advanced optimization techniques:

#### CSS Files
- **Comprehensive Download**: Fetches all external stylesheets and CSS imports
- **Smart Organization**: Stores in `assets/css/` with clean, descriptive filenames
- **Path Resolution**: Updates all HTML `<link>` references to local paths
- **Dependency Handling**: Manages CSS imports and cascading stylesheets
- **Minification Ready**: Preserves original formatting for potential optimization

#### JavaScript Files
- **Complete Script Collection**: Downloads all external JavaScript files and modules
- **Organized Storage**: Stores in `assets/js/` with logical filename structure
- **Analytics Removal**: Disables tracking scripts and analytics for Hindi site
- **Error Prevention**: Implements graceful fallback for failed script downloads
- **Performance Optimization**: Maintains script loading order and dependencies

#### Images
- **Comprehensive Coverage**: Downloads all images including lazy-loaded and responsive variants
- **Quality Enhancement**: Optimizes image URLs for maximum resolution and quality
- **Format Support**: Handles PNG, JPG, GIF, SVG, WebP, and other modern formats
- **CDN Optimization**: Intelligently processes Imgix and other CDN URLs
- **Lazy Loading Preservation**: Maintains original lazy loading functionality

### 3. **Translation Process**

Uses Google Translate API to convert content:

#### Text Elements Translated
- Headers (h1, h2, h3, h4, h5, h6)
- Paragraphs (p)
- Links (a)
- Lists (li)
- Buttons and labels
- Table content (td, th)
- Span and div text

#### Translation Features
- **Rate Limiting**: 0.5-second delays between translations
- **Error Handling**: Keeps original text if translation fails
- **Quality Control**: Only translates meaningful text (>3 characters)
- **Context Preservation**: Maintains HTML structure

### 4. **Link Processing**

Converts all internal links to work offline:

```python
# Before: https://www.classcentral.com/course/machine-learning
# After: machine-learning.html
```

### 5. **File Organization**

Creates a clean directory structure:

```
classcentral_hindi/
├── index.html                 # Homepage
├── navigation.html            # Site navigation
├── course-page.html          # Course pages
├── assets/
│   ├── css/                  # Stylesheets
│   ├── js/                   # JavaScript files
│   └── images/               # Images
├── checkpoint.json           # Progress tracking
└── progress.json            # Page status
```

## 📊 Progress Tracking

The scraper includes robust progress management:

### Checkpoint System
- Saves progress every 5 pages
- Allows resuming from interruptions
- Stores visited URLs and current state

### Progress Monitoring
- Real-time progress bars
- Estimated completion time
- Success/failure tracking per page

### Memory Management
- Garbage collection every 3 pages
- Variable cleanup after processing
- Optimized for large-scale scraping

## 🛠️ Configuration

### Environment Variables
```bash
# Optional: Custom output directory
OUTPUT_DIR=custom_output

# Optional: Custom base URL
BASE_URL=https://custom-classcentral.com
```

### Scraping Limits
```python
# In classcentral_scraper.py
max_pages = 100  # Adjust based on your needs
```

## 📈 Performance Features

### Optimization Techniques
- **Parallel Processing**: Async translation operations
- **Asset Caching**: Avoids re-downloading existing files
- **Memory Management**: Regular cleanup to prevent memory leaks
- **Rate Limiting**: Prevents API blocks and server overload

### Estimated Performance
- **Pages per hour**: ~144 pages (25 seconds per page average)
- **Asset download**: 3-8 seconds per page
- **Translation**: 10-20 seconds per page
- **Total time**: Varies based on content complexity

## 🚀 Deployment

The generated `classcentral_hindi/` folder is ready for deployment to:

### Free Hosting Options
- **Netlify**: Drag & drop deployment
- **Vercel**: Git integration with auto-deploy
- **GitHub Pages**: Free static hosting
- **Firebase Hosting**: Google's hosting solution

### Deployment Commands
```bash
# Netlify (recommended)
# Just drag classcentral_hindi/ folder to Netlify dashboard

# Vercel
cd classcentral_hindi
vercel