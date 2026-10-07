---
category: general
date: 2026-10-07
description: Aspose.Words C# ile bir Word belgesine OLE komut düğmesi eklemeyi öğrenin.
  DocumentBuilder, özellikler ve dosyanın kaydedilmesini kapsayan adım adım rehber.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: tr
lastmod: 2026-10-07
og_description: C# kullanarak bir Word belgesine OLE komut düğmesi ekleyin. Aspose.Words
  ile işlevsel bir CommandButton eklemek, yapılandırmak ve kaydetmek için bu kısa
  öğreticiyi izleyin.
og_image_alt: Insert OLE command button example in Word document
og_title: C# ile Word'e OLE komut düğmesi ekleme – tam Aspose.Words rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: C# kullanarak bir Word belgesine OLE komut düğmesi ekleme
url: /tr/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# kullanarak bir Word belgesine OLE komut düğmesi ekleme

Programlı olarak bir Word dosyasına **OLE komut düğmesi** eklemeniz gerekiyorsa, bu rehber Aspose.Words for .NET ile bunu nasıl yapacağınızı tam olarak gösterir. Form doldurulmuş bir rapor oluşturuyor ya da kullanıcı etkileşimi gerektiren bir şablonu otomatikleştiriyor olun, aşağıdaki adımlar size eksiksiz, çalıştırılabilir bir çözüm sunar.

Boş bir belge oluşturmayı, `DocumentBuilder` ile bir `Forms2OleControl` yerleştirmeyi, düğmenin başlığını ve adını ayarlamayı ve sonunda `.docx` dosyasını kaydetmeyi öğreneceksiniz. Aspose.Words kütüphanesi dışındaki herhangi bir araç gerekmiyor.

## Önkoşullar

* .NET 6.0 veya daha yeni bir sürüm (kod ayrıca .NET Framework 4.7+ ile de çalışır)
* Geçerli bir Aspose.Words for .NET lisansı veya ücretsiz deneme anahtarı
* Visual Studio 2022 (veya tercih ettiğiniz herhangi bir C# IDE)
* C# sözdizimi ve Word OLE kavramlarına temel aşinalık

> **Pro ipucu:** Ücretsiz deneme sürümünü kullanıyorsanız, oluşturulan belge küçük bir filigran içerecektir. Lisanslı bir sürüm bunu otomatik olarak kaldırır.

## Adım 1: Aspose.Words'i Yükleyin

NuGet aracılığıyla projenize Aspose.Words paketini ekleyin:

```bash
dotnet add package Aspose.Words
```

Paket, OLE kontrolleri için gerekli olan `Aspose.Words.Drawing` ve `Aspose.Words.Drawing.Ole` ad alanlarını içerir.

## Adım 2: DocumentBuilder ile OLE komut düğmesi ekleyin

Bu öğreticinin çekirdeği `InsertForms2OleControl` metodudur. Belirli bir konum ve boyutta **Forms2 OLE CommandButton** oluşturur.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Neden bu çalışıyor

- `DocumentBuilder` programlı olarak Word belgeleri oluşturmak için birincil API'dir.  
- `InsertForms2OleControl`, Aspose.Words'e **Forms2 OLE kontrolü** gömmesini söyler; bu, komut düğmeleri, onay kutuları vb. destekleyen eski Word form teknolojisidir.  
- `OleControlType.CommandButton` enum değeri, eklenen kontrolün **komut düğmesi** olduğunu belirtir—**OLE komut düğmesi eklemek** istediğinizde talep ettiğiniz tam tip.  
- `Rectangle`, görsel konumlamayı belirler. X/Y koordinatlarını veya genişlik/yüksekliği düzenleyerek yerleşiminize uyarlayın.

## Adım 3: Belgeyi Kaydedin

Düğmeyi yapılandırdıktan sonra belgeyi diske yazın. Aspose.Words tarafından desteklenen herhangi bir formatı seçebilirsiniz (`.docx`, `.pdf`, `.odt`, …). Bu öğreticide belgeyi Word dosyası olarak kaydedeceğiz.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`CommandButton.docx` dosyasını Microsoft Word'de açtığınızda, **Click Me** etiketiyle bir tıklanabilir düğme göreceksiniz. Word'de buna tıkladığınızda, düğme bir OLE form kontrolü olduğu için varsayılan “Makro Çalıştır” iletişim kutusu açılır; gerektiğinde daha sonra bir makro veya VBA kodu ekleyebilirsiniz.

## Adım 4: Sonucu Doğrulayın (beklenen çıktı)

Üretilen dosyayı açın:

1. Düğme, belirttiğiniz koordinatlarda (sayfanın sol ve üstünden yaklaşık 1.4 in) görünür.  
2. Başlık **Click Me** olarak görüntülenir.  
3. `cmdSubmit` adındaki özellik, Word'ün **Developer → Properties** panelinde görünür; bu, kontrolü VBA'dan referans almanız gerektiğinde faydalıdır.

![Word belgesinde OLE komut düğmesi örneği](insert-ole-button.png)

*Resim alt metni*: **Word belgesinde OLE komut düğmesi örneği** (erişilebilirlik ve SEO için birincil anahtar kelime içerir).

## Kenar Durumları ve Yaygın Sorular

### 1. Düğme beklediğim yerde görünmezse ne olur?

- Word, piksel yerine nokta (point) birimini kullanır. Ekran piksellerini noktalara dönüştürün (`points = pixels * 72 / DPI`).  
- Dikdörtgenin sayfa kenar boşluklarıyla çakışmadığından emin olun; aksi takdirde Word kontrolü kaydırabilir.

### 2. Düğmeyi mevcut bir belgeye ekleyebilir miyim?

Evet. Belgeyi `new Document("Existing.docx")` ile yükleyin ve aynı `DocumentBuilder` iş akışını kullanın. `InsertForms2OleControl` çağırmadan önce builder'ın imlecini (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")` vb.) hareket ettirmeyi unutmayın.

### 3. Düğmeye bir makro nasıl eklenir?

Aspose.Words VBA kodu oluşturmaz, ancak belge oluşturulduktan sonra bir makro gömebilirsiniz:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Bu, Linux üzerindeki .NET Core ile çalışır mı?

OLE kontrolü, COM'a dayandığı için Windows‑özel bir özelliktir. Linux'ta düğme eklenecek, ancak etkileşimli davranış olmadan statik bir resim olarak görünecektir. Çapraz platform etkileşimli formlar için içerik kontrolleri (`StructuredDocumentTag`) kullanmayı düşünün.

### 5. Farklı bir boyuta veya birden fazla düğmeye ihtiyacım olursa?

Benzersiz koordinatlarla ek `Rectangle` nesneleri oluşturun ve `InsertForms2OleControl` çağrısını tekrarlayın. Her düğmenin kendi `Caption` ve `Name` özelliği olabilir.

## Tam Çalışan Örnek

Aşağıda, bir konsol uygulamasına kopyalayıp yapıştırabileceğiniz tam program bulunmaktadır. Gerekli tüm `using` yönergeleri, hata yönetimi ve yorumları içerir.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Programı çalıştırın, oluşturulan `CommandButton.docx` dosyasını açın ve **Click Me** düğmesini daha fazla özelleştirmeye hazır olarak göreceksiniz.

## Sonuç

Artık C# ve Aspose.Words kullanarak bir Word belgesine **OLE komut düğmesi eklemeyi** biliyorsunuz. Öğreticide şunlar ele alındı:

- Aspose.Words paketinin kurulumu  
- `OleControlType.CommandButton` ile `DocumentBuilder.InsertForms2OleControl` kullanımı  
- Düğme özelliklerinin ayarlanması (`Caption`, `Name`)  
- Çıktının kaydedilmesi ve doğrulanması  

Buradan, onay kutuları, combo kutular veya tüm Excel çalışma sayfalarını gömmek için **Aspose.Words OLE control** gibi ilgili konuları keşfedebilirsiniz. Ayrıca daha büyük şablonlarda **Word OLE command button** otomasyonunu deneyebilir veya OLE kontrollerini modern **content controls** ile değiştirerek daha iyi çapraz platform desteği elde edebilirsiniz.

Uygulamanızın ihtiyaçlarına göre rectangle değerlerini uyarlamaktan, birden fazla düğme eklemekten veya VBA makroları eklemekten çekinmeyin. Kodlamanın tadını çıkarın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Word Belgesine Ole Nesnesi Ekle](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Ole Nesnesini Simgesi Olarak Word Belgesine Ekle](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Ole Paketiyle Word'e Ole Nesnesi Ekle](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}