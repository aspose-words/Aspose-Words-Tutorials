---
category: general
date: 2025-12-22
description: 輕鬆為您的 C# 形狀加入陰影效果。學習如何添加陰影、設定模糊程度，並透過形狀陰影格式建立柔和陰影。
draft: false
keywords:
- add shadow effect
- how to add shadow
- how to set blur
- create soft shadow
- add shape shadow
language: zh-hant
og_description: 為你的 C# 圖形添加陰影效果。本教程展示如何添加陰影、設定模糊，以及使用清晰的程式碼範例建立柔和陰影。
og_title: 在 C# 中為形狀添加陰影效果 – 完整指南
tags:
- C#
- graphics
- Aspose.Slides
- UI design
title: 在 C# 中為形狀添加陰影效果 – 逐步指南
url: /zh-hant/java/images-shapes/add-shadow-effect-to-shapes-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中為形狀添加陰影效果 – 完整指南

有沒有想過如何在不花費數小時翻閱 API 文件的情況下 **add shadow effect** 到形狀上？你並不孤單。許多開發者在需要那種細緻的投影以讓 UI 元素更突出時卡住了，而通常的「參考文件」答案卻像是死胡同。

在本教學中，我們將逐步說明使用 C# 為形狀 **add shadow effect** 所需的一切。我們會涵蓋 *how to add shadow*、*how to set blur* 以獲得柔和的光暈，甚至如何 **create soft shadow** 以在任何應用程式中呈現專業外觀。完成後，你將擁有一個可直接放入專案的即時執行範例。

## 本教學涵蓋內容

- 在 Aspose.Slides（或任何類似函式庫）中 **add shape shadow** 所需的精確 API 呼叫。
- 一步一步的程式碼，可直接 copy‑paste。
- 說明每個設定為何重要——不只是指令清單。
- 邊緣情況，例如透明形狀、多重陰影與效能建議。
- 完整、可執行的範例，會在矩形上產生可見的柔和陰影。

不需要先前的陰影 API 經驗；只要具備 C# 與物件導向程式設計的基本概念即可。

---

## 添加陰影效果 – 概觀

陰影本質上是視覺上的位移加上模糊，以模擬深度。在大多數圖形函式庫中，流程如下：

1. **Retrieve** 形狀的陰影格式物件。
2. **Configure** 屬性，如位移、顏色與模糊半徑。
3. **Apply** 設定回形狀。

當你遵循這三個步驟時，會立即看到 **soft shadow** 出現。關鍵在於模糊半徑——它是將硬邊緣轉為柔和霧狀的調節桿。

### 快速術語速查表

| Term | 功能說明 |
|------|----------|
| **ShadowFormat** | 保存所有與陰影相關的屬性（位移、顏色、模糊等）。 |
| **BlurRadius** | 控制陰影邊緣的模糊程度。值越高，陰影越柔和。 |
| **OffsetX / OffsetY** | 水平/垂直移動陰影。 |
| **Transparency** | 調整陰影的透明度，使其更透明或更不透明。 |

了解這些概念將有助於你 **create soft shadow** 出自然的效果。

## 如何為形狀添加陰影

首先，你需要一個形狀實例。以下是使用 Aspose.Slides 的最小設定範例，但相同模式適用於大多數 .NET 圖形函式庫。

```csharp
using Aspose.Slides;
using Aspose.Slides.Export;
using System.Drawing;

// Create a new presentation and add a blank slide
Presentation pres = new Presentation();
ISlide slide = pres.Slides[0];

// Add a rectangle shape (our canvas for the shadow)
IShape rect = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 100, 100, 300, 150);
rect.FillFormat.FillType = FillType.Solid;
rect.FillFormat.SolidFillColor = Color.LightBlue;
rect.LineFormat.Width = 2;
rect.LineFormat.FillFormat.SolidFillColor = Color.DarkBlue;
```

> **專業提示：** 選擇具有可見填充的形狀；否則陰影可能會被透明背景遮蔽。

現在我們有了 `rect`，可以透過存取其 `ShadowFormat` 來 **add shape shadow**：

```csharp
// Step 1: Obtain the shape you want to modify (already done above)
// Step 2: Access the shape's shadow formatting object
ShadowFormat shadow = rect.ShadowFormat;

// Step 3: Enable the shadow and set basic properties
shadow.Visible = true;                 // Turn the shadow on
shadow.Type = ShadowType.Inner;        // You can also use Outer, Perspective, etc.
shadow.Color = Color.Black;           // Classic black shadow
shadow.OffsetX = 5;                    // 5 points to the right
shadow.OffsetY = 5;                    // 5 points down
```

此時矩形將擁有清晰、硬邊的陰影。若執行簡報，你會看到一個 **add shadow effect**，功能性勝於華麗。

## 如何設定柔和陰影的模糊

硬邊緣會顯得廉價，尤其在高 DPI 螢幕上。這時 **how to set blur** 就派上用場。`BlurRadius` 屬性接受一個 `float`，代表以點為單位的半徑。

```csharp
// Step 4: Set the blur radius to create a soft shadow
shadow.BlurRadius = 5.0f;   // 5 points gives a subtle, soft look
```

為什麼是 `5.0f`？實務上，`3.0f` 到 `8.0f` 之間的值可為大多數 UI 元素產生自然的柔和陰影。數值過高則會看起來像發光而非陰影。

你也可以調整透明度，使陰影不那麼刺眼：

```csharp
shadow.Transparency = 0.4f; // 40% transparent – looks lighter
```

現在你已 **added shadow effect**，既可見又柔和。儲存檔案以查看結果：

```csharp
pres.Save("AddShadowEffect.pptx", SaveFormat.Pptx);
```

在 PowerPoint 或任何檢視器中開啟 `AddShadowEffect.pptx`，即可看到帶有柔和模糊位移的矩形——一個 textbook **create soft shadow** 範例。

## 使用自訂設定建立柔和陰影

有時你需要更具藝術性的控制。以下是一個輔助方法，將常用設定封裝成一次呼叫。隨意將其複製到工具類別中。

```csharp
/// <summary>
/// Applies a customizable soft shadow to any IShape.
/// </summary>
public static void ApplySoftShadow(IShape shape, float offsetX = 5f, float offsetY = 5f,
                                   float blur = 6f, Color? color = null, float transparency = 0.35f)
{
    if (shape == null) throw new ArgumentNullException(nameof(shape));

    ShadowFormat sf = shape.ShadowFormat;
    sf.Visible = true;
    sf.Type = ShadowType.Outer;
    sf.OffsetX = offsetX;
    sf.OffsetY = offsetY;
    sf.BlurRadius = blur;
    sf.Color = color ?? Color.Black;
    sf.Transparency = transparency;
}
```

使用方式如下：

```csharp
ApplySoftShadow(rect, offsetX: 8, offsetY: 8, blur: 7, color: Color.DarkSlateGray);
```

此方法讓你只用一行程式碼即可 **add shape shadow**，保持主程式碼整潔。它同時示範了以可重用方式 *how to add shadow*——在處理數十個形狀時相當有彈性。

## 添加形狀陰影 – 完整可執行範例

以下是一個可自行編譯執行的完整程式。它會建立簡報，新增三個矩形，分別套用不同的陰影設定，最後儲存檔案。

```csharp
using Aspose.Slides;
using Aspose.Slides.Export;
using System;
using System.Drawing;

namespace ShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Initialize presentation
            Presentation pres = new Presentation();
            ISlide slide = pres.Slides[0];

            // Rectangle 1 – basic shadow
            IShape rect1 = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 50, 50, 200, 100);
            rect1.FillFormat.SolidFillColor = Color.LightCoral;
            ApplyShadow(rect1, blur: 3f, offsetX: 4, offsetY: 4, transparency: 0.2f);

            // Rectangle 2 – soft shadow (our main focus)
            IShape rect2 = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 50, 200, 100);
            rect2.FillFormat.SolidFillColor = Color.LightGreen;
            ApplyShadow(rect2, blur: 6f, offsetX: 6, offsetY: 6, transparency: 0.4f);

            // Rectangle 3 – heavy blur for a glow effect
            IShape rect3 = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 550, 50, 200, 100);
            rect3.FillFormat.SolidFillColor = Color.LightSkyBlue;
            ApplyShadow(rect3, blur: 12f, offsetX: 0, offsetY: 0, transparency: 0.6f, color: Color.DarkBlue);

            // Save the result
            pres.Save("ShadowDemo.pptx", SaveFormat.Pptx);
            Console.WriteLine("Presentation created – open ShadowDemo.pptx to see the add shadow effect.");
        }

        // Reusable helper (same as earlier)
        public static void ApplyShadow(IShape shape, float offsetX = 5f, float offsetY = 5f,
                                       float blur = 5f, Color? color = null, float transparency = 0.35f)
        {
            ShadowFormat sf = shape.ShadowFormat;
            sf.Visible = true;
            sf.Type = ShadowType.Outer;
            sf.OffsetX = offsetX;
            sf.OffsetY = offsetY;
            sf.BlurRadius = blur;
            sf.Color = color ?? Color.Black;
            sf.Transparency = transparency;
        }
    }
}
```

**預期輸出：** 開啟 *ShadowDemo.pptx* 時，你會看到三個矩形。中間的示範了經典的 **create soft shadow** 技術，具有適度的模糊與位移，而其他兩個則分別呈現較輕與較重的變化。

![添加陰影效果範例](shadow-example.png "添加陰影效果範例")

*圖片替代文字：* 添加陰影效果範例

## 常見問題與技巧

- **Shadow not showing?** 確認 `ShadowFormat.Visible` 已設為 `true`。某些函式庫預設為不可見。
- **Blur looks too harsh.** 降低 `BlurRadius` 或提升 `Transparency`。`0.4f` 的透明度值通常能柔化外觀。
- **Performance concerns.** 渲染大量陰影會減慢 UI 重繪。若在迴圈中繪製，請快取結果。
- **Multiple shadows.** 大多數 API 每個形狀僅支援一個陰影。若要模擬多重陰影，可複製形狀，分別位移每個副本，並依正確順序渲染。
- **Cross‑platform quirks.** 若目標為 Xamarin 或 MAUI，請確認目標平台提供陰影 API；否則可能需要自訂渲染器。

## 結論

現在你已完全了解如何在 C# 中 **add shadow effect** 形狀。從取得 `ShadowFormat` 物件的基本步驟到微調模糊...

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}