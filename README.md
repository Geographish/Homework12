# Week 13 Homework: ARIA v9.0 — The Cloud Engine

本專案為「遙測與空間資訊之分析與應用」Week 13 Homework，主題為 **ARIA v9.0 — The Cloud Engine**。

本次作業使用 Google Earth Engine（GEE）分析花蓮秀林 / 太魯閣研究區的長期植被與 SAR 時序變化，觀察 2024/04/03 花蓮地震前後，以及後續堰塞湖事件後的地表變化。

---

## Project Overview

主要分析內容：

1. Sentinel-2 NDVI 月平均時序分析
2. 震前 / 震後 / 堰塞湖後 NDVI median composite
3. ΔNDVI 變遷偵測與植被損失面積估算
4. Sentinel-1 VV SAR 時序分析
5. NDVI 與 SAR 交叉比對
6. GeoTIFF 匯出至 Google Drive
7. Integration Summary 與心得撰寫

---

## Study Area

研究區為花蓮縣秀林 / 太魯閣山區。

```python
TAROKO_BBOX = [
    121.34526379253053,
    24.046021742135874,
    121.85149217685861,
    24.35767637905926
]
```

GEE 中使用：

```python
aoi = ee.Geometry.Rectangle(TAROKO_BBOX)
```

---

## Dataset

| Dataset | GEE Collection ID | Usage |
|---|---|---|
| Sentinel-2 Level-2A | `COPERNICUS/S2_SR_HARMONIZED` | NDVI time series and composite |
| Sentinel-1 GRD | `COPERNICUS/S1_GRD` | VV SAR backscatter time series |
| Google Earth Engine | GEE cloud platform | ImageCollection filtering, reducer, export |

---

## File Structure

本專案建議的檔案架構如下：

```text
Week13_ARIA_v9_Taroko/
│
├── README.md
├── Week13_ARIA_v9_Taroko.ipynb
│
└── output/
    ├── task1_ndvi_timeseries.png
    ├── task3_sentinel1_vv_timeseries.png
    └── gee_exports_drive_screenshot.png
```

## Main Notebook

```

Notebook 內容依序包含：

1. Python 與 GEE 環境設定
2. 建立秀林 / 太魯閣 AOI
3. Sentinel-2 ImageCollection 篩選
4. SCL 雲遮罩與 NDVI 計算
5. 2020–2026 月平均 NDVI 時序分析
6. 震前 / 震後 / 堰塞湖後 NDVI composite
7. ΔNDVI 變遷偵測與面積統計
8. Sentinel-1 VV SAR 時序分析
9. ΔVV map 與 NDVI + SAR 交叉比對
10. GeoTIFF 匯出
11. Integration Summary
12. 簡短心得
