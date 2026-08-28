# 國立虎尾科技大學學位論文 LaTeX 模板

> **NFU Thesis LaTeX Template**  
> 以 XeLaTeX 編譯，提供國立虎尾科技大學碩博士論文撰寫所需的封面、書名頁、摘要、目錄、圖表目錄、參考文獻、附錄、英文論文大綱與書背等基本排版功能。

> [!IMPORTANT]
> 本專案為**非官方、持續調整中的 LaTeX 模板**。雖已依虎科大論文格式與既有模板進行整理，但**不保證目前版本已逐項符合校方或各系所最新規定**。正式送印、口試或上傳論文前，請務必再與國立虎尾科技大學教務處、圖書館及所屬系所公告之最新規範核對。

---

## 目錄

- [專案來源與設計方向](#專案來源與設計方向)
- [檔案結構](#檔案結構)
- [環境需求](#環境需求)
- [快速開始：Overleaf](#快速開始overleaf)
- [本機編譯](#本機編譯)
- [與原 NFU 模板的主要差異](#與原-nfu-模板的主要差異)
- [已知限制與注意事項](#已知限制與注意事項)
- [常見問題](#常見問題)
- [來源與致謝](#來源與致謝)
- [授權與再散布說明](#授權與再散布說明)

---


## 專案來源與設計方向

本專案並非從零開始建立，而是以既有虎科大 LaTeX 論文模板為主要基礎，再重新整理檔案結構與使用方式。

主要參考來源如下：

1. [ziteh/nfu-thesis](https://github.com/ziteh/nfu-thesis)  
   作為虎科大論文版型、封面、摘要、目錄與相關格式設定的主要參考來源。

2. [chungyuandye/NTOU_Thesis](https://github.com/chungyuandye/NTOU_Thesis)  
   參考其較精簡的專案結構、單一樣式檔、集中式 metadata 設定及獨立書背檔案等設計方式。

本版本的整理目標是：

> **保留原 NFU 模板的主要排版邏輯，同時降低檔案層級與設定複雜度，讓第一次使用 LaTeX 或 Overleaf 的研究生也能較容易修改與維護。**

---

## 檔案結構

目前專案主要檔案如下：

```text
NFU_Thesis-main/
├── README.md
├── nfu-thesis.sty            # 核心樣式：版面、封面、摘要、目錄、頁碼等
├── nfu_thesis_example.tex    # 論文主文件；一般使用者主要修改此檔
├── thesis.bib                # BibTeX 參考文獻資料庫
├── watermark_nfu.jpg         # 虎科大論文浮水印
├── approval.pdf              # 口試委員審定書範例／待替換 PDF
├── debug.jpg                 # 圖片排版範例使用
├── bookspine.tex             # 書背，需獨立編譯
├── bookspine.pdf             # 書背範例輸出
└── nfu_thesis_example.pdf    # 主模板範例輸出
```

> `bookspine.pdf` 與 `nfu_thesis_example.pdf` 為目前版本的範例輸出。修改 `.tex` 或 `.sty` 後，請以重新編譯後的 PDF 為準。

---

## 環境需求

| 項目 | 建議／需求 |
| --- | --- |
| 編譯引擎 | **XeLaTeX** |
| 線上環境 | Overleaf |
| 本機 TeX 發行版 | TeX Live 或 MiKTeX |
| 編輯器 | Overleaf、VS Code + LaTeX Workshop、TeXstudio 等 |
| 參考文獻 | BibTeX |
| 作業系統 | Windows / macOS / Linux |

> 本模板以 XeLaTeX 為主要編譯環境。請勿直接改用 pdfLaTeX，否則 `fontspec`、`xeCJK` 與中文字型設定可能無法正常運作。

---

## 快速開始：Overleaf

### 1. 上傳專案

將整個專案 ZIP 上傳至 Overleaf，或先解壓縮後將所有檔案上傳至同一個專案。

### 2. 指定主文件

在 Overleaf 專案設定中將 Main document 指定為：

```text
nfu_thesis_example.tex
```

### 3. 指定編譯器

將 Compiler 設為：

```text
XeLaTeX
```

### 4. 修改論文資料

開啟 `nfu_thesis_example.tex`，修改最上方的 `\NFUSetup{...}`。

### 5. 重新編譯

按下 **Recompile**。Overleaf 一般可自動處理 BibTeX 與多次編譯所需流程。

---

## 本機編譯

若使用 TeX Live、MiKTeX、VS Code 或其他本機環境，可在專案根目錄執行：

```bash
xelatex nfu_thesis_example.tex
bibtex nfu_thesis_example
xelatex nfu_thesis_example.tex
xelatex nfu_thesis_example.tex
```

多次執行 XeLaTeX 是為了更新：

- 目錄
- 圖目錄
- 表目錄
- 交叉引用
- 頁碼
- 參考文獻引用

若未使用 BibTeX 或參考文獻沒有變更，可視情況省略 `bibtex` 步驟。

### 編譯書背

```bash
xelatex bookspine.tex
```

輸出：

```text
bookspine.pdf
```

---

### 欄位說明

| 欄位 | 說明 |
| --- | --- |
| `mainfont` | 英文主字型 |
| `cjkfont` | 中文主字型 |
| `universityzh` / `universityen` | 學校中英文名稱 |
| `collegezh` / `collegeen` | 學院中英文名稱 |
| `institutezh` / `instituteen` | 系所／學位學程中英文名稱 |
| `fielden` | 英文學位領域名稱 |
| `degreezh` / `degreeen` | 學位名稱，例如碩士 / Master of Science |
| `classzh` / `classen` | 文件類型，例如論文 / Thesis |
| `titlezh` / `titleen` | 論文中英文題目 |
| `studentzh` / `studenten` | 研究生中英文姓名 |
| `advisorzh` / `advisoren` | 指導教授中英文姓名 |
| `yearzh` | 民國年 |
| `yearen` | 西元年 |
| `monthzh` / `monthen` | 中英文月份 |
| `watermark` | 浮水印圖片檔名 |
| `approvalpdf` | 口試委員審定書 PDF 檔名 |

> 不同系所的正式英文名稱、學位名稱與學位領域可能不同，請依系所正式資料填寫，不要直接沿用範例內容。

---

## 與原 NFU 模板的主要差異

相較於 [ziteh/nfu-thesis](https://github.com/ziteh/nfu-thesis)，本版本主要做了下列整理：

1. 將原本較多層的 `chapters/`、`figures/`、`tables/`、`images/`、`pdfs/`、`src/` 等結構，整理為較精簡的根目錄配置。
2. `nfuthesis.cls` 的主要格式邏輯整理為 `nfu-thesis.sty`。
3. 原先分散於 `nfuvars.tex` 等檔案的論文基本資料，集中至 `nfu_thesis_example.tex` 的 `\NFUSetup{...}`。
4. 中文摘要、英文摘要、誌謝與 Extended Abstract 的範例內容集中在主文件，方便初學者直接查看完整論文流程。
5. 新增／整理可獨立編譯的 `bookspine.tex`。
6. 常用圖片、PDF 與 bibliography 放在根目錄，降低 Overleaf 中尋找檔案的成本。
7. 將部分固定寫死的欄位改為可設定變數，例如英文學位領域 `fielden`。
8. 修正原模板中部分已知的拼字或設定問題，並重新整理字型 fallback 與排版程式。

本版本的核心方向不是改寫所有排版邏輯，而是：

> **在維持 NFU 模板既有格式基礎下，提高可讀性、可維護性與 Overleaf 使用便利性。**

---

## 已知限制與注意事項

目前版本仍在持續調整，使用前請留意：

1. **非虎科大官方模板。** 最終格式仍應以國立虎尾科技大學及所屬系所最新規範為準。
2. `bookspine.tex` 目前以工業管理系工業工程與管理碩士班為範例，其他系所需手動調整系所垂直文字。
3. 書背資料尚未與 `\NFUSetup{...}` 完全共用，因此主文件與書背需分別修改。
4. Extended Abstract 的實際內容長度與細部版面，仍應依各系所規範確認。
5. 不同作業系統與 Overleaf 可用字型不同，fallback 字型可能造成細微版面差異。
6. `nfu_thesis_example.pdf` 與 `bookspine.pdf` 只代表該次編譯結果，不一定與目前 `.tex` / `.sty` 最新內容完全一致；更新程式後請重新編譯。
7. 各系所可能另有封面、書背、英文學位名稱、Extended Abstract 或裝訂細節規定，請勿只依本模板判斷。

---

## 來源與致謝

本專案的形成建立在多個既有 LaTeX 論文模板與作者工作的基礎上，特別感謝：

### NFU 模板

- [ziteh/nfu-thesis](https://github.com/ziteh/nfu-thesis)

該模板將早期台大、交大相關 XeLaTeX 論文模板逐步修改為適用於國立虎尾科技大學的版本，是本專案最主要的 NFU 排版來源。

原專案 README 亦記錄其歷史來源，包括 Tz-Huan Huang、Po-hao Huang 等作者與相關模板貢獻。

### 專案結構與使用方式參考

- [chungyuandye/NTOU_Thesis](https://github.com/chungyuandye/NTOU_Thesis)

本專案參考其較精簡的根目錄結構、單一 `.sty` 核心樣式檔、集中 metadata 設定，以及獨立 `bookspine.tex` 的設計概念。

### 虎科大論文規範

正式論文格式請以國立虎尾科技大學教務處公布之資料為準：

- [國立虎尾科技大學教務處－研究生學位考試申請](https://oaa.nfu.edu.tw/zh_tw/teaching/gradexamapplication)

校方規範可能更新，本專案不以 README 中記載的日期取代官方最新公告。

---

## 授權與再散布說明

`nfu-thesis.sty` 保留其上游來源中的 **Chocolate-Ware License** notice：只要保留原始 notice，即可依其原始聲明使用與修改相關內容。

由於本專案包含上游模板的重構內容、範例圖片／PDF 與後續新增程式，若要進一步正式公開發行或指定整個 repository 的統一開源授權，建議再逐項確認各來源檔案之授權與可再散布條件，並於 repository 根目錄另行加入適合的 `LICENSE` 檔案。

---

## 開發狀態

本模板目前仍會持續調整格式細節與跨環境相容性。若發現：

- 與虎科大最新格式規範不一致
- 特定系所格式無法套用
- Overleaf / TeX Live 編譯問題
- 封面、摘要、目錄、圖表或書背排版問題

歡迎透過 GitHub Issue 記錄問題，並附上：

1. 使用環境（Overleaf / Windows / macOS / Linux）
2. 編譯器與 TeX Live 版本
3. 錯誤訊息或截圖
4. 可重現問題的最小範例

這會比只提供最終 PDF 更容易定位問題。

---

**最後提醒：本模板的目的，是讓排版工作更容易，而不是取代學校與系所的正式論文規範。送印與繳交前，請務必完成最後一次人工格式檢核。**
