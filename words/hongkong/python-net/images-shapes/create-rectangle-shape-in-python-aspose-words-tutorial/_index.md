---
category: general
date: 2026-06-21
description: 使用 Aspose.Words 在 Python 中建立矩形形狀。學習如何為形狀添加陰影、設定形狀填充顏色，並在幾分鐘內將文件儲存為 PDF。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: zh-hant
og_description: 使用 Aspose.Words 在 Python 中建立矩形形狀。本指南示範如何為形狀添加陰影、設定形狀填充顏色，並將文件另存為 PDF。
og_title: 在 Python 中建立矩形形狀 – Aspose.Words 教學
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: 在 Python 中建立矩形形狀 – Aspose.Words 教學
url: /zh-hant/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Python 中建立矩形形狀 – Aspose.Words 教程

有沒有想過在使用 Python 編寫程式時，**如何在 Word 文件中建立矩形形狀**？你並不是唯一有此疑問的人。許多開發者在需要快速的視覺元素（例如帶有淡淡陰影的彩色方框）並將整個文件匯出為 PDF 時，常常卡關。  

本指南將逐步說明一個完整且可執行的範例，示範**建立矩形形狀**、**設定形狀填色**、**為形狀加入陰影**，最後**將文件儲存為 PDF**。不會有模糊的說明，只有您今天就能直接複製貼上並執行的具體程式碼。

## 您需要的環境

- Python 3.8 或更新版本（我們使用的語法在任何較新的版本皆可運作）。
- 有效的 Aspose.Words for Python 授權或免費試用版（此函式庫純粹使用 Python，無需 COM 互操作）。
- 您熟悉的文字編輯器或 IDE — VS Code 表現優秀，其他皆可使用。

就這樣。沒有繁重的框架，也沒有額外的作業系統層級相依性。讓我們開始吧。

## 第一步：安裝 Aspose.Words for Python

首先，若尚未安裝，請從 PyPI 取得套件：

```bash
pip install aspose-words
```

此步驟的重要性：Aspose.Words 提供我們將依賴的 `Document` 與 `DocumentBuilder` 類別。若未安裝此函式庫，之後的呼叫（例如 `insert_shape`）將不存在，腳本會在繪製任何線條前就崩潰。

> **專業提示：** 保持虛擬環境整潔。於安裝前執行 `python -m venv .venv && source .venv/bin/activate`，讓函式庫與系統套件隔離。

## 第二步：建立新文件與 DocumentBuilder

現在我們真的要**建立矩形形狀**——但首先需要一個空白畫布。

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

`Document` 物件代表整個檔案，而 `DocumentBuilder` 是一個便利的輔助工具，知道游標所在位置並能在該處插入元素。可將 builder 想像成在頁面上書寫的筆。

## 第三步：插入矩形形狀

這裡是主要動作發生的地方。我們將**建立矩形形狀**，設定固定的寬度與高度，然後將其定位於頁面上。

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

為什麼選擇矩形？它是最簡單的形狀，同時能展示填色與陰影。若之後需要圓形或星形，只需將 `ShapeType.RECTANGLE` 替換為其他列舉值即可。

## 第四步：設定形狀填色

單純的白色方框不夠吸引人，讓我們**設定形狀填色**為柔和的顏色——淡藍色在報告中表現不錯。

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

您可以使用任何預先定義的 `aw.Color` 成員（`red`、`green`、`dark_gray` 等），或傳入 RGB 元組（`aw.Color.from_argb(255, 30, 144, 255)`）。填色是使用者在任何陰影或邊框套用前看到的顏色。

## 第五步：為形狀加入陰影

現在來做視覺上的修飾：**為形狀加入陰影**。陰影提供深度，使矩形在頁面上更突出。

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**如何加入陰影**？上面的程式碼正是如此，但讓我們拆解每個屬性的意義：

- `visible` – 開關效果的開啟/關閉。
- `color` – 定義色調；深灰色模擬自然光線。
- `blur` – 數值越高產生更柔和的邊緣。
- `offset_x` / `offset_y` – 將陰影從形狀移開；調整此值可模擬不同光源角度。
- `transparency` – 0 為實心，1 為完全透明；0.2 產生細膩的效果。
- `type` – `OUTER` 在形狀外投射陰影，`INNER` 則在內部投射。

若需要更誇張的投影陰影，可將 `blur` 提升至 10‑15，並將 `offset_x`/`offset_y` 調整至 6‑8。

## 第六步：將文件儲存為 PDF

所有的工作若無法**將文件儲存為 PDF**並分享就毫無意義。Aspose.Words 只需一行程式碼即可完成：

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

為什麼是 PDF？PDF 能在不同平台間保留版面配置，適合報告、發票或任何可列印的文件。`save` 方法會自動偵測檔案副檔名並選擇正確的格式——只要確保路徑以 `.pdf` 結尾即可。

### 預期結果

開啟產生的 `ShapeWithShadow.pdf`，您應該會看到一個淡藍色的矩形，位於首頁上方居中，並帶有向右下方稍微偏移的柔和深灰色陰影。形狀邊緣清晰，陰影細膩，檔案大小通常在 100 KB 以下。

## 加分：調整陰影 – 回答「如何加入陰影」的問題

您可能會想，*「我可以在不移動形狀的情況下改變陰影方向嗎？」* 當然可以。陰影的位置與形狀座標獨立，只需調整 `offset_x` 與 `offset_y`。正值會使陰影向右/下移動，負值則向左/上移動。若要模擬左上方光源，可設定 `offset_x = -3` 與 `offset_y = -3`。

另一個常見問題：*「如果我要在同一個形狀上加上多重陰影怎麼辦？」* Aspose.Words 每個形狀僅支援單一陰影。若需要分層效果，可建立重複的形狀，稍微偏移，並為每個形狀套用不同的陰影。這算是一種小技巧，但可行。

## 完整腳本 – 可直接執行

以下為完整、獨立的腳本。將其複製到名為 `create_rectangle_with_shadow.py` 的檔案中，並以 `python create_rectangle_with_shadow.py` 執行。

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **注意：** 請將 `YOUR_DIRECTORY` 替換為您機器上實際存在的絕對或相對路徑。若資料夾不存在，Python 會拋出 `FileNotFoundError`。

## 常見陷阱與避免方法

| 問題 | 發生原因 | 解決方式 |
|-------|----------------|-----|
| 陰影未顯示 | `shadow.visible` 保持預設 `False` | 確保 `shadow.visible = True` |
| 形狀不可見 | 填色設定為 `aw.Color.transparent` 或 `None` | 使用實心顏色，例如 `aw.Color.light_blue` |
| PDF 為空 | 忘記呼叫 `doc.save` 或使用錯誤的副檔名儲存 | 呼叫 `doc.save("output.pdf")` 並確認路徑正確 |
| 執行時錯誤 `ImportError` | 未安裝 Aspose.Words 或使用錯誤的 Python 環境 | 在啟用的 venv 中執行 `pip install aspose-words` |

## 下一步 – 探索更多形狀與格式設定

既然您已掌握**建立矩形形狀**，接下來可以：

- 將 `ShapeType.RECTANGLE` 替換為 `ShapeType.ELLIPSE` 或 `ShapeType.PENTAGON`，以嘗試其他幾何形狀。
- 使用 `builder.move_to(rectangle.absolute_position)`，然後 `builder.writeln("Hello World")`，在形狀內加入文字。
- 使用 `group = aw.drawing.GroupShape(doc)` 將多個形狀合併為群組，以建立複雜圖表。
- 匯出為其他格式，如 DOCX（`doc.save("output.docx")`）或 HTML（`doc.save("output.html")`），觀察陰影的呈現方式。

上述每個延伸皆基於相同的核心概念：**為形狀加入陰影**、**設定形狀填色**，以及**將文件儲存為 PDF**（或其他格式）。

---

### 圖片預覽 *(可選)*

![在 Python 中建立帶陰影的矩形形狀](https://example.com/rectangle-shadow.png "在 Python 中建立帶陰影的矩形形狀")

*此螢幕截圖顯示最終 PDF 輸出，包含淡藍色矩形與細緻的外部陰影。*

---

## 結論

我們已逐步說明在 Python 中**建立矩形形狀**、套用自訂填色、**為形狀加入陰影**，最後**將文件儲存為 PDF**的所有必要步驟。程式碼可直接執行，說明涵蓋每個屬性的*原因*，並提及常見的邊緣案例與下一步…

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，建立在此處示範的技術之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [在 Java 中建立 Word 文件 – 加入帶陰影的矩形形狀](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Word 中使用 C# 建立矩形形狀 – 步驟指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words 形狀陰影教學 – 在 C# 中為 Word 形狀加入陰影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}