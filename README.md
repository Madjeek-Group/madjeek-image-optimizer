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

Or inline it directly inside a <script> tag.

💻 Console Commands
The script exposes a global object MadjeekImageOptimizer for debugging purposes. Open the browser console (F12) to use it:

View status of all images:

javascript
MadjeekImageOptimizer.debug();
Analyze a specific image:

javascript
const img = document.querySelector('img');
MadjeekImageOptimizer.analyze(img);
Force re-optimization of all images:

javascript
MadjeekImageOptimizer.optimize();
📄 License
This project is licensed under the MIT License.

Copyright (c) 2024 Madjeek

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
