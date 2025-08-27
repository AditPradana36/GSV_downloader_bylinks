# 🗺️ Google Street View Downloader by Links  

This repository provides a **Google Street View (GSV) image downloader** that works from a list of Google Maps links stored in an Excel file.  
It is designed as a **continuation of my previous project**: [GSV Panorama Downloader by Coordinates](https://github.com/AditPradana36/GSV_panorama_downloader).  

While the earlier repo focused on downloading panoramas by **latitude/longitude coordinate points**,  
this new implementation allows downloading **directly from Google Maps links** — making it easier for users who already have Street View URLs instead of coordinates.  

---

## 🔄 Relation to the Previous Repository  

- **Previous repo** → [GSV Panorama Downloader by Coordinates](https://github.com/AditPradana36/GSV_panorama_downloader)  
  - Input: latitude & longitude values  
  - Output: panorama images + metadata  

- **This repo** → GSV Downloader by Links  
  - Input: Excel file with copied **Google Maps Street View URLs**  
  - Output: heading-based slices, stitched panoramas, and full metadata  

📌 In short: **Same goal, different input style.**  
This repo complements the earlier tool by making the workflow more accessible for users who collect links rather than coordinates.  

---

## ✨ Key Features  

- 📂 **Batch download from Excel** – process multiple Google Maps links at once.  
- 📌 **Heading slices** – capture each link from multiple heading ranges (0°–360°).  
- 🌐 **Panorama stitch** – combine slices into one wide panorama.  
- 📝 **Metadata export** – includes pano ID, capture date, heading range, status, and timestamp.  
- ⚡ **Multiple modes** – choose between `headings`, `panorama`, or `both`.  

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

### 2. 📂 Prepare Your Excel File (Links Input)  

Create an **Excel file** (`.xlsx`) with at least these two columns:  

| id | link |  
|----|------|  
| 1  | https://www.google.com/maps/@-6.175392,106.827153,3a,75y,90t/... |  
| 2  | https://www.google.com/maps/@-6.200000,106.816666,3a,75y,90t/... |  

- `id` → unique identifier (number, code, or label).  
- `link` → Street View URL copied from Google Maps.  
- Example filename: `trylink.xlsx`  

Upload the file into Colab (default path: `/content/trylink.xlsx`).  

---

### 3. ⚙️ Configure Parameters  

Inside the notebook:  

```python
api_key = "YOUR_API_KEY"
xlsx_path = "/content/trylink.xlsx"
output_folder = "/content"
download_mode = "panorama"   # options: "headings", "panorama", or "both"
heading_ranges = [(0,90), (90,180), (180,270), (270,360)]
image_size = "640x640"
fov = 90
pitch = 0
metadata_output = "/content/metadata_from_links.csv"
