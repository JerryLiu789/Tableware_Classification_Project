# 餐具物件偵測 (YOLO 11)

## 專案簡介
本專案使用 **YOLO 11** 進行 **餐具物件偵測**，目標是 **精準偵測各種餐具 (碗、盤子、筷子、湯匙、叉子、杯子、刀子)**，並提升模型的 mAP (Mean Average Precision)。
透過 **資料增強 (Data Augmentation)** 及 **Soft-NMS** 等技術，優化模型的整體偵測準確率。

---

## 資料來源
本專案使用 **網路爬蟲** 取得大量餐具圖片，以手動標註整體數據 10% 左右的標籤，完成後使用 yolo11 預測剩餘 90% 的標籤，之後再以人工方式檢查標籤正確性與調整以完成整份數據的標籤任務。  
數據集經過 **數據清理、平衡類別**，最終整理出 **6000 - 7000 張圖片** 作為訓練數據。

 **標註類別：**
- 🥣 `Bowl`
- 🍽️ `Plate`
- 🥢 `Chopsticks`
- 🥄 `Spoon`
- 🍴 `Fork`
- 🍷 `Cup`
- 🔪 `Knife`

---

##  目標
1. **訓練 YOLO 11 來精準偵測餐具**
2. **以提升整體 mAP 為首要要優化指標，確保高準確率與高召回率**
3. **使用 Soft-NMS 以及數據增強等方式來優化偵測結果**
4. **測試 YOLO 在圖片與影片上的表現**

---

##  技術與工具
### 主要技術
- **物件偵測**：YOLO 11 (Ultralytics)
- **資料增強**：
  -  水平翻轉 (`fliplr`)
  -  垂直翻轉 (`flipud`)
  -  隨機旋轉 (`degrees`)
  -  縮放 (`scale`)
  -  亮度變化 (`hsv_v`)
  -  Mosaic Augmentation
- **後處理**：Soft-NMS (Soft Non-Maximum Suppression)

---

##  結果
在完全不進行任何優化手段前，整體 mAP 便來到 0.86， precision 0.79， Recall 0.82，
在進行所有優化，包含使用當前精準度最高的模型(yolo11x)、提升 Epoch 、使用數據增強技術、使用 Soft-NMS 來減少不同類別框重疊的情況等，都沒有對整體模型性能有較顯著的進步，
推測模型已經有效收斂，若要有效提升模型效能，必需從資料集著手，進行更嚴謹的資料篩選與排除不夠精確的標籤，此工程較為浩大，對於練習性質的專案，學習效果幫助不大，便以此作為最終總結。

---

##  成果展示
![偵測結果](finished_test_images/1.jpg)
![偵測結果](finished_test_images/2.jpg)
![偵測結果](finished_test_images/3.jpg)
![偵測結果](finished_test_images/4.jpg)
![偵測結果](finished_test_images/5.jpg)
![偵測結果](finished_test_images/6.jpg)
![偵測結果](finished_test_images/7.jpg)
![偵測結果](finished_test_images/8.jpg)



