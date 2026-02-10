# cryptocurrency_trading_algorithm
這個在 IBM Skills Network 上的專案是一個經典的金融科技 (FinTech) 入門實作，教導如何利用 Python 的數據科學生態系來自動化投資決策。

## 專案核心主題 (Core Topics)
量化交易基礎 (Quantitative Trading)：理解演算法交易與手動交易的差異。

數據獲取與清理：從金融 API 提取加密貨幣的歷史價格。

時間序列分析 (Time Series Analysis)：處理隨時間變化的價格數據（如 Adjusted Close）。

回溯測試 (Backtesting)：利用歷史數據驗證交易策略的盈虧表現。

技術指標實作：雖然此專案為簡單策略，但涵蓋了如何定義「買入/賣出」邏輯。

支援的 HTTP 方法與主要功能
雖然程式碼中主要呼叫套件函式，但底層運作涉及：

GET：透過 yfinance 函式庫向 Yahoo Finance API 發送 GET 請求，以獲取特定期間（如 2020 年）的 BTC-USD JSON 或 CSV 數據。

## 主要功能：

download()：獲取歷史市場數據。

策略執行：根據預設條件（如價格突破或均線）產生交易訊號。

績效評估：計算投資報酬率 (Return on Investment)。

## Workflow (操作流程)
資料獲取：使用 yfinance 下載比特幣歷史匯率。

資料探索：使用 pandas 查看資料結構（開盤、收盤、成交量）。

視覺化：利用 matplotlib 繪製收盤價折線圖。

策略定義：編寫邏輯判斷何時購買或賣出。

回測模擬：假設初始資金（如 $10,000），模擬在過去一年的交易結果。

結果分析：對比「持幣不動 (Buy and Hold)」與「演算法交易」的收益。

## API 路由總覽
外部 API：yfinance 介接的是 Yahoo Finance 的公共 API 路由。

內部路由：此專案為腳本式開發，不包含 Web 路由，但可擴充為 FastAPI 路由來提供交易建議。

## 環境需求
Python 3.x：核心執行環境。
Jupyter Notebook / Cloud IDE：用於逐步執行與呈現圖表。

複製專案 (Cloning)
通常在 IBM Skills Network 的實驗室環境中，你可以透過以下方式開始：
```git clone https://github.com/ibm-developer-skills-network/create-cryptocurrency-trading-algorithm-python.git```

Installation (安裝依賴庫)
```pip install yfinance pandas numpy matplotlib```
啟動開發伺服器
本專案為資料科學腳本，無須啟動 Web 伺服器，直接執行 .py 或 .ipynb 檔案即可。

## Structure (專案結構與工具)
yfinance：數據源工具。

pandas：數據處理核心，負責 DataFrame 操作。

numpy：負責底層數值計算。

matplotlib / pyplot：生成靜態價格圖表與交易點標記。

DateFormatter：優化 X 軸時間標籤的顯示格式。

## 應用方向
個人投資助手：自動追蹤感興趣的貨幣並發送通知。

市場研究工具：分析不同加密貨幣間的相關性。

自動化報表生成：定期產出市場走勢分析圖。

## MVP 方向 (未來開發潛力)
即時交易機器人 (Live Trading Bot)：串接交易所 API（如 Binance 或 Coinbase）實施真實交易。

情緒分析儀 (Sentiment Trader)：整合 Twitter API，根據社群媒體情緒決定買賣。

多策略對比平台：一個讓使用者輸入不同參數並即時看到回測結果的 Web 應用。

AI 預測模型：將簡單策略升級為機器學習模型（如 LSTM）來預測未來價格。

## Tool 
語言：Python

數據處理：Pandas, NumPy

視覺化：Matplotlib

金融數據：yfinance

## Key Takeaways
回測不代表未來：歷史表現優異不保證未來獲利。

自動化的威力：演算法能克服人性恐懼與貪婪，嚴格執行紀律。

視覺化的重要性：透過 matplotlib 繪圖能快速發現數據中的異常值或趨勢。
