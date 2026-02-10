# cryptocurrency_trading_algorithm
這個在 IBM Skills Network 上的專案是一個經典的金融科技 (FinTech) 入門實作，教導如何利用 Python 的數據科學生態系來自動化投資決策。

## 專案核心主題 (Core Topics)
- 加密貨幣市場資料獲取與處理
- 量化交易基礎 (Quantitative Trading)：理解演算法交易與手動交易的差異。
- 數據獲取與清理：從金融 API 提取加密貨幣的歷史價格。使用 yfinance 從 Yahoo Finance 拉取歷史價格資料（BTC-USD 等）
- 時間序列分析 (Time Series Analysis)：處理隨時間變化的價格數據（如 Adjusted Close）（開高低收、成交量）
- 回溯測試 (Backtesting)與績效評估（報酬率、勝率、風險指標）：利用歷史數據驗證交易策略的盈虧表現。
- 技術指標實作：本專案涵蓋了如何定義「買入/賣出」邏輯。
- 資料視覺化（價格走勢圖、買賣訊號標記）

## 支援的 HTTP 方法與主要功能
此專案為**純 Python 腳本 / Jupyter Notebook**，**沒有自建後端 API**，也不直接使用 HTTP 方法進行交易。
GET：主要依賴yfinance 函式庫向 Yahoo Finance API 發送 GET 請求（對應的虛擬HTTP操作），以獲取特定期間（如 2020 年）的 BTC-USD JSON 或 CSV 數據。
- **GET**：yfinance.download() 內部發送 GET 請求，獲取歷史 OHLCV 資料（Open, High, Low, Close, Volume）
- **無 POST/PUT/DELETE**：專案不涉及真實下單或修改資料庫，所有交易邏輯皆在本地記憶體/DataFrame 中模擬完成
- **主要功能重點**：資料下載 → 清洗與計算指標 → 產生買賣訊號 → 模擬交易 → 計算累積報酬與視覺化

## 主要功能：
- download()：獲取歷史市場數據。
- 策略執行：根據預設條件（如價格突破或均線）產生交易訊號。
- 績效評估：計算投資報酬率 (Return on Investment)。

## Workflow (操作流程)
- 安裝與匯入套件
- 資料獲取，使用 yfinance 下載比特幣(BTC-USD)歷史匯率。
- 資料探索，使用 pandas 查看資料結構（開盤、收盤、成交量、head()、價格走勢圖）。
- 視覺化，利用 matplotlib 繪製收盤價折線圖、買賣訊號與累積報酬圖。 
- 實作策略，編寫邏輯判斷何時購買或賣出。
- 回測模擬，假設初始資金（如 $10,000），模擬在過去一年的交易結果與績效計算。
- 結果分析，對比Buy and Hold與演算法交易的收益。

## API 路由總覽
**外部 API：yfinance 介接的是 Yahoo Finance 的公共 API 路由。**
內部路由：此專案為腳本式開發，不包含 Web 路由，但可擴充為 FastAPI 路由來提供交易建議。

## 環境需求
- Python 3.7+：核心執行環境。
- Jupyter Notebook / Cloud IDE：用於逐步執行與呈現圖表。

## 複製專案 (Cloning)
在 IBM Skills Network 的實驗室環境中，你可以透過以下方式開始：
```git clone https://github.com/ibm-developer-skills-network/create-cryptocurrency-trading-algorithm-python.git```

```cd create-cryptocurrency-trading-algorithm```

## Installation (安裝依賴庫)
```pip install yfinance pandas numpy matplotlib```
1. 然後匯入套件：
```import yfinance as yf```
#### yfinance：數據源工具。
```import pandas as pd```
#### pandas：數據處理核心，負責 DataFrame 操作。
```import numpy as np```
#### numpy：負責底層數值計算。
```from matplotlib import pyplot as plt```
#### matplotlib / pyplot：生成靜態價格圖表與交易點標記。
```from matplotlib.dates import DateFormatter```
#### DateFormatter：優化 X 軸時間標籤的顯示格式。
2. 啟動開發伺服器
3. 本專案為腳本，無須啟動 Web 伺服器，直接執行 .py 或 .ipynb 檔案即可。
   

## Structure (專案結構與工具)
- Create_a_Cryptocurrency_Trading_Algorithm_in_Python.ipynb   # 主 Notebook
- README.md                          # 本說明文件
#### 資料由 yfinance 即時下載）

## 應用方向
- 個人投資助手：自動追蹤感興趣的貨幣並發送通知
- 市場研究工具：分析不同加密貨幣間的相關性
- 自動化報表生成：定期產出市場走勢分析圖
- 股票/外匯/商品期貨的類似回測分析

## MVP 方向 
- 即時交易機器人 (Live Trading Bot)：串接交易所 API（如 Binance 或 Coinbase）真實交易。
- 多幣種移動平均策略優化工具（加入參數掃描、走走測試 Walk-Forward，擴展至股票、外匯，實現多元化投資組合管理。）
- 加密貨幣投資儀表板(Streamlit / Dash 前端 + 即時資料更新）
- 情緒分析儀 (Sentiment Trader)：加入 NLP 技術，整合 Twitter API，根據社群媒體情緒決定買賣。
- 風險調整後報酬分析器（加入 Sharpe Ratio、最大回撤等指標）：讓使用者輸入不同參數並即時看到回測結果的 Web 應用。 
- AI 預測模型：升級為機器學習模型（如 LSTM、Random Forest）來預測未來價格。

## Tool 
- Python
- pandas, numpy #數據處理
- matplotlib, pyplot #視覺化
- DateFormatter #時間軸顯示
- yfinance #金融數據

## Key Takeaways
- 使用 yfinance 快速獲取加密貨幣市場資料的能力
- 理解 OHLCV 資料結構與基本時間序列分析
- 設計與實作簡單規則型交易策略（Rule-based Trading）
- 進行策略回測並視覺化績效（買賣點、累積報酬曲線）
- 認識程式化交易的核心流程：資料 → 策略 → 回測 → 優化
- 為機器學習交易、強化學習、即時交易打下基礎
