# Madjeek Image Optimizer

A lightweight, adaptive, and automatic JavaScript image optimizer designed for webmasters. 

This script dynamically modifies image URLs to load them at the optimal size based on the user's screen resolution. It significantly improves Lighthouse performance scores and loading times without sacrificing image quality on high-resolution screens (4K/Retina).

## 🚀 Features

* **Fully Automatic:** No need to manually write `srcset` or `sizes` attributes in the HTML.
* **Adaptive:** Detects the user's screen size and device pixel ratio.
* **Quality Preservation:** Keeps the original image size on 4K/Retina screens for maximum quality.
* **Performance Boost:** Loads lighter images on mobile and tablet devices.
* **Smart:** Never upscales an image beyond its original dimensions.
* **Dynamic:** Works with images loaded dynamically (AJAX, infinite scroll, etc.) using MutationObserver.

## 📊 How it works

Based on the screen width, the script applies the following logic:

| Screen Type | Screen Width | Target Display Size | Image Quality |
| :--- | :--- | :--- | :--- |
| **Mobile** | ≤ 600px | 480px (or original) | 75% |
| **Tablet** | ≤ 1200px | 800px (or original) | 80% |
| **Desktop** | ≤ 1920px | 1170px (or original) | 85% |
| **4K / Retina**| > 1920px | Original Size | 92% |

*Note: The script requires the image server to understand URL parameters like `?w=...&q=...` (e.g., Imgix, Cloudinary, or a custom PHP resizer).*

## 🛠️ Installation

1. Download or copy the `madjeek-image-optimizer.js` file.
2. Include the script in the `<head>` or at the end of the `<body>` of all web pages containing images:

```html
<script src="/path/to/madjeek-image-optimizer.js"></script>
