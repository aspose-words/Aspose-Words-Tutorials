---
category: general
date: 2026-10-10
description: Paragrafı Fransızcaya çevirin ve Aspose.Words AI kullanarak grafik veri
  etiketini nasıl değiştireceğinizi, grafik veri etiketini nasıl özelleştireceğinizi
  ve düzenlenmiş docx dosyasını nasıl kaydedeceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: tr
lastmod: 2026-10-10
og_description: Paragrafı Fransızcaya çevirin ve grafik veri etiketini nasıl değiştireceğinizi,
  grafik veri etiketini nasıl özelleştireceğinizi ve Aspose.Words AI kullanarak düzenlenmiş
  docx dosyasını nasıl kaydedeceğinizi öğrenin.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Paragrafı Fransızcaya çevir ve Word'de grafik etiketini değiştir
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: Paragrafı Fransızcaya çevir ve Word'de grafik etiketini değiştir
url: /tr/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Paragrafı Fransızcaya Çevirme ve Word'de Grafik Etiketini Değiştirme

Aynı Word belgesi içinde bir paragrafı **Fransızcaya çevirmek** ve aynı zamanda bir grafiği güncellemek istiyorsanız, bu kılavuz tam olarak nasıl yapılacağını gösterir. Aspose.Words AI kullanarak metni otomatik olarak çevirebilir, ardından bir grafiğin veri etiketini değiştirebilir ve son olarak düzenlenmiş `.docx` dosyasını kaydedebilirsiniz—hepsi birkaç basit adımda.

Bu öğretici, kaynak dosyanın yüklenmesinden değişikliklerin kalıcı hale getirilmesine kadar her şeyi kapsar. Sonunda herhangi bir paragrafı çevirebilecek, bir grafik veri etiketini özelleştirebilecek ve dağıtıma hazır yeni bir Word dosyası üretebileceksiniz. Harici betikler gerekmez; tüm iş akışı tek bir C# programında gerçekleşir.

## Önkoşullar

- .NET 6.0 veya daha yenisi (kod ayrıca .NET Framework 4.7+ ile de çalışır)
- Aspose.Words for .NET lisansı (veya ücretsiz bir değerlendirme anahtarı)
- Google AI çevirmeni için internet erişimi (`Translator` sınıfı altında Google’ın API’sini kullanır)
- En az bir paragraf ve bir grafik içeren bir Word belgesi (`input.docx`)

## Adım 1: Projeyi kurun ve ad alanlarını içe aktarın

Create a new console application and add the Aspose.Words NuGet package:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Now include the required namespaces at the top of `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

These imports give you access to document loading, AI translation, and chart editing functionality.

## Adım 2: Kaynak Word belgesini yükleyin

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Loading the file creates an in‑memory representation that you can query and modify without touching the original file on disk.

## Adım 3: İlk paragrafı Fransızcaya çevirin

The first paragraph is often a title or introductory sentence, making it a good candidate for translation. The `Translator` class abstracts the call to Google’s AI model.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**Neden bu çalışır:**  
`paragraph.Runs.Clear()` mevcut tüm metin akışlarını (run) kaldırır, böylece yeni çeviri eski içerikle birleştirilmez. `new Run(document, translatedText)` paragrafın biçimlendirmesini devralan yeni bir run oluşturur.

## Adım 4: İlk grafiği bulun ve veri etiketini özelleştirin

Charts are stored as `Shape` nodes of type `NodeType.Shape`. The first chart can be fetched with `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**Ana adımların açıklaması:**

- `GetChild(NodeType.Shape, 0, true)` derinlik‑ilk arama yapar ve ilk şekli döndürür; bu örnekte bu şekil bir grafiktir.
- `ChartSeries`, veri noktalarının bir koleksiyonunu temsil eder; ilk seri (`Series[0]`) genellikle birincil veri kümesine karşılık gelir.
- `ChartDataLabelPosition.OutsideEnd` etiketi çubuğun sonundan dışarı taşır, okunabilirliği artırır.
- `dataLabel.Text` değerini Fransızca bir dizeye ayarlamak, etiketi çevrilen paragrafla hizalar.

## Adım 5: Çevrilen paragrafı içeren belgeyi kaydedin

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

At this point the document contains the French paragraph but still holds the original chart configuration.

## Adım 6: Güncellenmiş grafikle belgeyi kaydedin

You can reuse the same `Document` instance—no need to reload it—because the chart modifications are already in memory.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Both files are now ready for distribution:

- **`translated.docx`** – Fransızca paragrafı içerir.
- **`chart-updated.docx`** – Fransızca paragrafı *ve* özelleştirilmiş grafik etiketini içerir.

## Tam, çalıştırılabilir örnek

Below is the full program you can copy‑paste into `Program.cs`. It compiles and runs as‑is, assuming you have replaced `YOUR_DIRECTORY` with a real folder path.



## Sonra Ne Öğrenmelisiniz?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Grafik Veri Etiketini Özelleştir](/words/english/net/programming-with-charts/chart-data-label/)
- [Grafikte Veri Etiketi Sayısını Biçimlendir](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Grafik Veri Etiketi](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}