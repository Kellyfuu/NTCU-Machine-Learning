# ex1

## 使用資料集
- 資料來源：Kaggle - Credit Card Fraud Detection
- 資料筆數：284,807 筆交易資料
- 詐欺交易僅佔 0.172%（極度不平衡）

---

## 模型一：Random Forest（監督式學習）
### 訓練方式：
- 先將資料標準化（標準化 Amount）
- 使用 `train_test_split` 切 70/30
- 使用 `RandomForestClassifier` 進行分類

### 評估指標
Accuracy: 0.9995318516437859
Precision: 0.9576271186440678
Recall: 0.7635135135135135
F1 Score: 0.849624060150376

### 小結：
Random Forest 能夠準確識別多數正常交易，但對極少數詐欺交易的召回率有待加強，可透過調參或資料重抽樣改善。

---

## 模型二：KMeans（非監督式學習）
### 訓練方式：
- 僅用前 1000 筆正常資料訓練
- 嘗試 k=2~4 的群數，用 Silhouette Score 找最佳 k
- 對齊分群結果與實際標籤後進行評估

### 評估指標
Accuracy: 0.9987242957293166
Precision: 0.782608695652174
Recall: 0.36486486486486486
F1 Score: 0.4976958525345622

### 小結：
KMeans 不需標籤資料即可運作，但分類結果無法達到監督式模型的水準。適合作為初步偵測或前處理工具。

---

## 結論：
- Random Forest 在處理標記資料時效果較佳
- KMeans 雖然精度低，但能在無標籤的狀況下做初步偵測
- 日後可考慮結合兩者（Challenge 2）進行融合學習