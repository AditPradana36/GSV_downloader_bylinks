# 🗺️ Google Street View Downloader by Links  

This repository provides a **Google Street View Downloader** that works from a list of Google Maps links stored in an Excel file.  
Instead of downloading manually, you can **batch-download hundreds of Street View images** by simply pasting your links into a spreadsheet.  

---

## ✨ Key Features  
- 📂 **Batch download from Excel** – download Street View images for **multiple locations at once**.  
- 📌 **Heading slices** – capture each location from multiple heading ranges (0°–360°).  
- 🌐 **Panorama stitch** – merge multiple headings into one wide panorama.  
- 📝 **Metadata export** – save important info (pano ID, capture year/month, status, timestamp).  
- ⚡ **Flexible modes** – choose between `headings`, `panorama`, or `both`.  

---

## ⚙️ Setup & Usage  

### 1. 🔑 Get Your API Key  
1. Go to the [Google Cloud Console](https://console.cloud.google.com/).  
2. Create a project and enable:  
   - **Street View Static API**  
   - **Street View Image API**  
3. Generate an API Key and ensure **billing is enabled**.  
4. Paste the API Key into the notebook (`api_key` parameter).  

---

### 2. 📂 Prepare Your Excel File (Multiple Links)  
Create an **Excel file** (`.xlsx`) with at least these two columns:  

| id | link |  
|----|------|  
| 1  | https://www.google.com/maps/@-6.175392,106.827153,3a,75y,90t/... |  
| 2  | https://www.google.com/maps/@-6.200000,106.816666,3a,75y,90t/... |  
| 3  | https://www.google.com/maps/... |  

- Each row represents **one Street View location**.  
- `id` = unique identifier for the link (numbers, codes, or labels).  
- `link` = copied from Google Maps (right-click → *Copy link*).  

📌 Example filename: `trylink.xlsx`  
Upload it to Colab (default path: `/content/trylink.xlsx`).  

---

### 3. ⚙️ Configure Parameters  
Inside the notebook, set:  

```python
api_key = "YOUR_API_KEY"
xlsx_path = "/content/trylink.xlsx"
output_folder = "/content"
download_mode = "panorama"   # "headings", "panorama", or "both"
heading_ranges = [(0,90), (90,180), (180,270), (270,360)]
image_size = "640x640"
fov = 90
pitch = 0
metadata_output = "/content/metadata_from_links.csv"
