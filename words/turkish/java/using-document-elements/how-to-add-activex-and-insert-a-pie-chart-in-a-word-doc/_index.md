---
category: general
date: 2026-08-17
description: Aspose.Words kullanarak bir Word belgesine ActiveX denetimleri ekleme
  ve bir pasta grafiği ekleme. Bir dilimi patlatıp birkaç adımda DOCX olarak kaydetme.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: tr
lastmod: 2026-08-17
og_description: ActiveX denetimlerini ekleme, pasta grafiği ekleme, dilimi patlatma
  ve Aspose.Words ile DOCX olarak kaydetme – adım adım tam rehber.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: ActiveX ekleme ve Word belgesine pasta grafiği ekleme
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: ActiveX ekleme ve bir Word belgesine pasta grafiği ekleme
url: /tr/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word belgesine ActiveX ekleme ve pasta grafiği ekleme

Word belgesine **ActiveX ekleme** denetimlerini eklemeniz ve bir grafiği gömmek istiyorsanız, bu öğretici size eksiksiz, çalıştırılabilir bir çözüm gösterir. Aspose.Words kullanarak bir ActiveX CommandButton yerleştirebilir, bir pasta grafiği oluşturabilir, vurgulamak için bir dilimi patlatabilir ve sonunda sadece birkaç C# satırıyla **DOCX olarak kaydedebilirsiniz**.

Aşağıdaki bölümlerde gerekli tüm importları, tam kod listesini ve her adımın neden önemli olduğuna dair açıklamaları göreceksiniz. Sonunda, programatik olarak oluşturduğunuz herhangi bir .docx dosyasına etkileşimli denetimler ve görsel veriler ekleyebileceksiniz.

## Önkoşullar

Başlamadan önce şunların kurulu olduğundan emin olun:

* .NET 6.0 veya daha yeni (kod .NET Framework 4.7+ ile de çalışır)
* Aspose.Words for .NET paketi (NuGet üzerinden temin edilebilir)
* Visual Studio 2022 veya VS Code gibi bir geliştirme ortamı
* C# ve Word nesne modeli hakkında temel bilgi

Ek üçüncü‑taraf grafik kütüphanelerine ihtiyaç yok—Aspose.Words yerleşik grafik oluşturma sağlar.

## Aspose.Words ile ActiveX denetimleri ekleme

ActiveX denetimleri, bir Word dosyasına doğrudan etkileşimli UI öğeleri gömmenizi sağlar. Bu rehberde daha sonra VBA koduna bağlanabilecek bir **CommandButton** ekleyeceğiz.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Neden bu çalışır:**  
`InsertForms2OleControl` Word UI'nin bir ActiveX denetimi olarak tanıdığı bir OLE kapsayıcısı oluşturur. Denetim tipini `CommandButton` olarak ayarlayıp bir başlık vermek, kullanıcı dosyayı Word’de açtığında standart bir düğme gibi davranmasını sağlar.

## Pasta grafiği ekleme ve bir dilimi patlatma

Grafikler, belge içinde veri görselleştirmek için kullanışlıdır. Aşağıdaki adımlar **grafik ekleme** ve özellikle ilk dilimi patlatılmış bir **pasta grafiği** oluşturmayı gösterir.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Neden dilimi patlatıyorsunuz:**  
`SetExplode(0, true)` çağrısı, Aspose.Words’e ilk veri noktasını kaydırmasını söyler ve izleyicinin gözünü o segmente çeker. Bu, sunumlarda ana değeri vurgulamak için yaygın bir tekniktir.

## DOCX olarak kaydetme

ActiveX düğmesi ve grafiği ekledikten sonra belgeyi diske kaydedin. Bu adım, standart yöntemi kullanarak **DOCX olarak kaydetme** işlemini gösterir.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

`Output.docx` dosyası artık etkileşimli bir düğme, patlatılmış bir dilime sahip bir pasta grafiği içerir ve ek eklentilere ihtiyaç duymadan Microsoft Word’de açılabilir.

## Tam çalıştırılabilir örnek

Her şeyi bir araya getirerek, bir konsol uygulamasına kopyalayıp hemen çalıştırabileceğiniz bağımsız bir program aşağıdadır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Beklenen sonuç:**  
`Output.docx` dosyasını Word’de açtığınızda *Click Me* etiketiyle bir düğme ve ilk dilimi (Ocak) diğerlerinden ayrılmış bir pasta grafiği görürsünüz. Düğme VBA olay işleme için hazırdır ve grafik Word’ün yerleşik grafik araçlarıyla düzenlenebilir.

## Yaygın sorular ve uç durumlar

* **Başka ActiveX türleri ekleyebilir miyim?**  
  Evet. `Forms2OleControlType.CommandButton` ifadesini `Forms2OleControlType` enum’undan herhangi bir değerle (ör. `CheckBox`, `OptionButton`) değiştirin. Aynı ekleme deseni geçerlidir.

* **Farklı bir grafik türüne ihtiyacım olursa?**  
  `InsertChart` çağrısında `ChartType.Bar`, `ChartType.Line` vb. kullanın. **grafik ekleme** adımı aynı kalır; sadece enum değeri değişir.

* **Patlatılmış dilimin boyutunu nasıl kontrol ederim?**  
  Aspose.Words şu anda ikili bir patlatma bayrağı (true/false) destekler. Daha ince kontrol (ör. kaydırma mesafesi) için kaydetmeden sonra temel OOXML’i düzenlemeniz gerekir.

* **Belge eski Word sürümleriyle uyumlu mu?**  
  DOCX olarak kaydetmek, Word 2007 ve sonrası ile uyumluluğu sağlar. Word 2003 için `SaveFormat.Doc` kullanılabilir, ancak bu formatta ActiveX desteği sınırlıdır.

* **`System.Drawing` referansına ihtiyacım var mı?**  
  Hayır. Tüm çizim nesneleri Aspose.Words tarafından sağlanır; tek gerekli NuGet paketi `Aspose.Words`’tür.

## Sonuç

Artık **ActiveX ekleme**, **pasta grafiği ekleme**, **pasta dilimini patlatma** ve **DOCX olarak kaydetme** konularını Aspose.Words for .NET ile nasıl yapacağınızı biliyorsunuz. Tam örnek, belge oluşturma aşamasından son kaydetmeye kadar her adımı kapsar ve her API çağrısının mantığını açıklar.

Sonraki adımlarda şunları keşfedebilirsiniz:

* CommandButton tıklamasına yanıt veren VBA makroları ekleme (**grafik ekleme** ve veri güncellemelerini otomatikleştirme)
* Kurumsal kimliğe uygun renkler ve veri etiketleriyle grafiğin görünümünü özelleştirme
* **ComboBox** veya **ListBox** gibi ek ActiveX denetimleri ekleyerek daha zengin formlar oluşturma

Kodu deneyin, örnek verileri değiştirin ve çözümü kendi belge‑oluşturma hatlarınızla bütünleştirin. İyi kodlamalar!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalarla tam çalışan kod örnekleri içerir ve API özelliklerini daha iyi kavramanıza yardımcı olur.

- [Aspose.Words for .NET Kullanarak Word'e Sütun Grafiği Ekleme](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET Kullanarak Word'e Basit Sütun Grafiği Ekleme](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Aspose.Words for .NET Kullanarak Word'e Balon Grafiği Ekleme](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}