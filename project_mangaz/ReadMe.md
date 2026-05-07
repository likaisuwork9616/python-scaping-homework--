# 爬蟲作業練習 (Crawler Practice)

本專案是根據老師課堂講義進一步開發的 **Python 爬蟲腳本 (Python Crawler Script)**，自動化下載與整理 MangaZ 平台的漫畫內容。在開發過程中，針對自動化流程與反偵測機制進行了以下優化。

## 主要功能與優化 (Key Features & Optimizations)

### 1. 自動資料夾創建機制 (Automatic Directory Creation)

在程式初始化階段，為了避免因下載路徑不存在而導致存檔失敗，我找 **Gemini** 詢問了如何在沒有資料夾時創建新資料夾的實作方法。

* **技術解決方案：** 引入 `os` 模組，並在存檔前自動檢查路徑。若偵測到無效路徑，程式會利用 `os.makedirs()` 自動創建新的資料夾 (New Folder)。

### 2. 反爬蟲與行為擬人化 (Anti-Scraping & Humanization)

由於 MangaZ 具有偵測機制，若操作過快或規律明顯，會頻繁觸發「著作權保護 (Copyright Protection)」的灰色字全白畫面。為了解決此問題，本程式實作了以下對策：

* **全域隨機延遲 (Randomized Delay)：** 在進入網頁、點擊閱讀、截圖以及翻頁點擊等關鍵節點，皆加入了 `time.sleep(random.uniform(x, y))`。透過隨機數字 (Random Numbers) 的等待時間，模擬人類真實的閱讀節奏，避免被系統判定為機器人。
* **模擬滑鼠軌跡 (Mouse Trajectory Simulation)：** 在點擊翻頁按鈕前，使用 `ActionChains` 模擬滑鼠移動與微幅震動，確保操作行為不具備機械化的特徵。

### 3. 程式結構封裝 (Code Encapsulation)

* **函式化管理 (Functional Management)：** 程式碼採用 `def main():` 進行封裝，將設定、流程控制與使用者輸入 (`input()`) 分離，提高程式碼的可讀性與專業度。

---

**備註：** 本專案僅用於 AI 職訓課程期中報告及學術研究。
