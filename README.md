# 國立虎尾科技大學碩博士論文 LaTeX 模板（Compact Layout）

本版本由既有 `nfu_thesis_main` 重新整理，**保留原 NFU 模板的主要排版邏輯與範例內容**，並改成類似 `NTOU_Thesis-main` 的扁平化專案結構，讓一般使用者不必在 `chapters/`、`src/`、`figures/`、`tables/`、`images/`、`pdfs/` 等多層目錄之間尋找設定。

> 建議使用 **XeLaTeX** 編譯。Overleaf：Menu → Compiler → XeLaTeX。

## 檔案結構

```text
NFU_Thesis-main/
├── README.md
├── .gitignore
├── nfu-thesis.sty            # 所有版型、封面、摘要、目錄與頁碼設定
├── nfu_thesis_example.tex    # 主文件；論文資料與範例內容集中於此
├── thesis.bib                # 參考文獻資料庫
├── watermark_nfu.jpg         # 虎科大論文浮水印
├── debug.jpg                 # 範例圖片
├── 口試委員審定書.pdf          # 範例/空白審定書，可自行替換
├── bookspine.tex             # 書背，獨立編譯
├── bookspine.pdf             # 書背範例輸出（若已編譯）
└── nfu_thesis_example.pdf    # 主模板範例輸出（若已編譯）
```

## 一般使用者主要修改哪裡？

開啟 `nfu_thesis_example.tex`，修改最上方的 `\NFUSetup{...}`：

- 學院、系所中英文名稱
- 學位名稱
- 論文中英文題目
- 研究生中英文姓名
- 指導教授中英文姓名
- 年、月
- 浮水印檔名
- 口試委員審定書 PDF 檔名

版面細節（封面字級、頁邊界、摘要標頭、目錄樣式等）集中在 `nfu-thesis.sty`。

## 與原 `nfu_thesis_main` 的主要差異

1. `nfuthesis.cls` → 重構成 `nfu-thesis.sty`。
2. `nfuvars.tex` → 合併進 `nfu_thesis_example.tex` 的 `\NFUSetup{...}`。
3. `abstract.tex`、`acknowledgements.tex`、`extended_abstract.tex` → 合併進主文件。
4. `chapters/`、`figures/`、`tables/` 的範例內容 → 合併進主文件。
5. `images/`、`pdfs/` → 常用資產移到根目錄。
6. 原本書名頁寫死的 `Industrial Engineering amd Management` 改成 `fielden` 變數，並修正 `amd` → `and`。
7. 原英文論文大綱中的 `\selecefont` 拼字錯誤修正為 `\selectfont`。
8. 增加 `bookspine.tex`，使結構更接近 NTOU 範本；書背仍為獨立編譯檔。

## Overleaf 使用方式

1. 將整個 ZIP 上傳至 Overleaf。
2. 將 Main document 指定為 `nfu_thesis_example.tex`。
3. Compiler 選擇 `XeLaTeX`。
4. Recompile。
5. 若要換審定書，直接用同名 PDF 覆蓋 `口試委員審定書.pdf`，或修改 `approvalpdf = {...}`。

## 字型

模板優先使用：

- 英文：Times New Roman
- 中文：TW-Kai

若目前環境找不到，模板會嘗試使用可用的替代字型，以避免直接中止編譯。正式提交前仍應依虎科大最新官方規範確認字型。

## 來源與致謝

本整理版以使用者提供的 NFU template 為基礎。原模板 README 記載其歷史來源包括 NTU/NCTU 系列模板，並由 ZiTe 修改為國立虎尾科技大學版本。`nfu-thesis.sty` 中保留原作者的 Chocolate-Ware notice。

本次重構主要針對**檔案結構、集中設定與可維護性**；不宣稱已完成最新虎科大論文規範的逐項驗證。正式發布 GitHub v1.0 前，仍建議依最新版學位論文規範逐項核對。
