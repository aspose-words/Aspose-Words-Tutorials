---
category: general
date: 2026-09-30
description: C# kullanarak bir Word belgesine ActiveX denetimi ekleyin. ActiveX düğmesi
  eklemeyi, bir komut düğmesi eklemeyi ve tıklanabilir hâle getirmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: tr
lastmod: 2026-09-30
og_description: C# ile bir Word belgesine ActiveX kontrolü ekleyin. Bu kapsamlı rehberi
  izleyerek bir ActiveX düğmesi ekleyin, bir komut düğmesi ekleyin ve tıklanabilir
  hâle getirin.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Word belgelerine bir ActiveX denetimi ekleyin – adım adım C# rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: C# ile Word'e ActiveX kontrolü ekleme
url: /tr/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile Word'de ActiveX kontrol kelimesi ekleme

Microsoft Word dosyasının içine bir **ActiveX kontrol kelimesi** yerleştirmeniz gerekiyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. Tıklanabilir bir düğme ekleyen, belgeyi kaydeden ve en yeni Aspose.Words for .NET ile çalışan tam, çalıştırılabilir bir örnek göreceksiniz.

ActiveX kontrol kelimesi eklemek, etkileşimli formlar, özel iletişim kutuları veya yerel Word kontrolleri gibi davranan basit UI öğeleri oluşturmanıza olanak tanır. Kullanıcı etkileşimi gerektiren bir sözleşme şablonu ya da bir “Çalıştır” düğmesi gereken bir rapor oluşturuyor olun, aşağıdaki adımlar ihtiyacınız olan her şeyi kapsar.

## Prerequisites

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 SDK veya daha yeni bir sürüm (kod .NET Framework 4.8 ile de çalışır)
* Visual Studio 2022 (veya C# destekleyen herhangi bir IDE)
* Aspose.Words for .NET kurulmuş (`dotnet add package Aspose.Words`)
* C# ve Word belge yapısı hakkında temel bir anlayış

> **Pro tip:** `InsertForms2OleControl` yöntemi yalnızca Word'ün form alanları için kullandığı eski “Forms 2.0” kontrolleriyle çalışır. Daha yeni Office sürümlerini hedefleseniz bile kontrol masaüstü istemcisinde doğru şekilde görüntülenir.

## Step 1: Set up the project and import namespaces

Yeni bir konsol projesi oluşturun ve gerekli `using` ifadelerini ekleyin. Bu, derleyicinin `Document`, `DocumentBuilder` ve `OleControlType` sınıflarını bulabilmesini sağlar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

`Aspose.Words` ad alanı Word işleme için yüksek seviyeli API'ler sunarken, `Aspose.Words.Drawing` ActiveX kontrol tipini belirtmek için gereken `OleControlType` enumunu içerir.

## Step 2: Load the source Word document

Değiştirmek istediğiniz bir Word dosyasıyla başlamalısınız. Aşağıdaki kod, belirttiğiniz klasörden `input.docx` dosyasını yükler.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Dosya bulunamazsa Aspose.Words bir `FileNotFoundException` fırlatır. Daha nazik bir hata yönetimi istiyorsanız çağrıyı bir `try/catch` bloğuna sarın.

## Step 3: Create a DocumentBuilder to edit the document

`DocumentBuilder`, metin, resim ve kontrol eklemek için çalışan motorudur. Bir sonraki öğenin yerleştirileceği konumu gösteren bir imleç tutar.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Varsayılan olarak, builder’ın imleci ilk bölümün başında konumlanır. Düğmeyi başka bir yere koymak isterseniz `MoveToDocumentEnd()` veya `MoveToParagraph(index)` gibi yöntemlerle imleci hareket ettirebilirsiniz.

## Step 4: Insert an ActiveX CommandButton control

Şimdi öğreticinin çekirdeği geliyor: **ActiveX kontrol kelimesi** olarak görünen tıklanabilir bir düğme eklemek. `InsertForms2OleControl` yöntemi iki argüman alır—kontrol tipi ve kontrolün başlığı (veya adı).

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Neden `OleControlType.CommandButton` kullanılır?**  
  Word’e klasik Forms 2.0 komut düğmesi oluşturmasını söyler; bu düğme bir başlık gösterir ve daha sonra bir makro ya da VBA scriptiyle bağlanabilir.

* **Başlık ne işe yarar?**  
  `"ClickMe"` dizesi düğmenin görünen metni olur. UI’nize uygun herhangi bir şeyle değiştirebilirsiniz.

### Inserting the button at a specific location

Düğmeyi belirli bir paragraftan sonra eklemeniz gerekiyorsa, önce builder’ı hareket ettirin:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Step 5: Save the modified document

Kontrolü ekledikten sonra değişiklikleri yeni bir dosyaya (ya da orijinali üzerine) kaydedin.

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`output.docx` dosyasını masaüstü Word sürümünde açtığınızda **ClickMe** (veya kullandığınız başlığa göre **Submit**) adlı düğmeyi göreceksiniz. Tasarım modunda düğmeye tıklamak varsayılan olarak bir şey yapmaz; daha sonra Word’ün “Developer” sekmesinden bir makro atayabilirsiniz.

## Full, runnable example

Aşağıda tüm iş akışını gösteren bağımsız bir program yer alıyor. Yeni bir konsol uygulamasının `Program.cs` dosyasına kopyalayıp çalıştırın.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Expected output

* Konsol, çıktı yolunu içeren başarı mesajını yazar.
* `output.docx` dosyasını açtığınızda builder’ın eklediği konumda bir **ClickMe** düğmesi görünür.
* Düğme, Word’ün **Developer → Design Mode** menüsü üzerinden seçilebilir, yeniden boyutlandırılabilir veya bir makroya atanabilir.

## Common questions and edge‑case handling

| Question | Answer |
|----------|--------|
| **How to insert an ActiveX button in the header/footer?** | `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` ile builder’ı başlık/altbilgiye taşıdıktan sonra `InsertForms2OleControl` çağırın. |
| **What if I need a checkbox instead of a button?** | `OleControlType.CheckBox` kullanın ve `"Agree"` gibi bir başlık verin. |
| **Will the button work in Word Online?** | Hayır. Word Online, eski Forms 2.0 ActiveX kontrollerini desteklemez. Düğme yalnızca masaüstü istemcisinde görüntülenir. |
| **Can I set the button’s size programmatically?** | Ekledikten sonra `builder.CurrentParagraph.Runs[0].GetShape()` ile `Shape` nesnesini alın ve `Width`/`Height` değerlerini ayarlayın. |
| **Is there a way to assign a macro from code?** | Aspose.Words makro düzenlemeyi açmaz. Belgeyi Word’te açıp makro eklemeniz ya da Office Interop API’sini kullanmanız gerekir. |

## Tips for production use

* **Avoid hard‑coded paths** – `Path.Combine` ve konfigürasyon dosyalarını kullanın.
* **Dispose of `Document`** – büyük dosyalarla çalışıyorsanız belleği hızlıca serbest bırakmak için `using` ifadesiyle sarmalayın.
* **Validate the output** – `doc.GetChildNodes(NodeType.Shape, true)` ile döngüye girerek belgenin bir `OleControl` şekli içerdiğini programatik olarak kontrol edin.
* **Security note** – ActiveX kontrolleri istemci makinesinde kod çalıştırabilir. Belgeleri yalnızca güvenilir kullanıcılara dağıtın ve dijital imzaları değerlendirin.

## Conclusion

Artık C# kullanarak bir Word belgesine **ActiveX kontrol kelimesi** eklemeyi biliyorsunuz. Bir belgeyi yükleyip, bir `DocumentBuilder` oluşturup, `InsertForms2OleControl` ile bir komut düğmesi ekleyip ve dosyayı kaydederek etkileşimli Word formları otomatikleştirebilirsiniz. Diğer `OleControlType` değerleriyle deney yapın, kontrolleri başlıklara ya da tablolara yerleştirin ve makrolarla birleştirerek daha zengin kullanıcı deneyimleri oluşturun.

---

*Next steps*: explore **how to insert ActiveX** controls of other types, learn **how to add command button** event handlers via VBA, and read about **insert ActiveX button** best practices for cross‑platform compatibility.


## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}