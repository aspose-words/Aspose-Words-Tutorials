---
category: general
date: 2026-07-23
description: Aspose.Words kullanarak Word belgesi düğmesi oluşturma – .docx dosyasına
  ActiveX CommandButton eklemek için adım adım rehber.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: tr
lastmod: 2026-07-23
og_description: 'Aspose.Words ile Word belgesi düğmesi oluşturun: Bir Word dosyasına
  ActiveX CommandButton eklemeyi dakikalar içinde öğrenin.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Word Belgesi Oluşturma Düğmesi – Aspose.Words Tam Kılavuzu
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Aspose.Words ile Word belgesi oluşturma düğmesi – Tam Kod Örneği
url: /tr/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile Word Belgesi Düğmesi Oluşturma – Tam Programlama Rehberi

Hiç **create word document button** oluşturmanız gerekti, ama hangi API'yi kullanacağınızdan emin değildiniz mi? Yalnız değilsiniz—çoğu geliştirici, bir .docx dosyasına etkileşimli denetimler eklemeye çalıştığında bir duvara çarpar. İyi haber? Aspose.Words for .NET ile sadece birkaç satır kodla Word belgesine tam işlevsel bir ActiveX CommandButton ekleyebilirsiniz.

Bu öğreticide tüm süreci adım adım inceleyeceğiz: projeyi kurmaktan, bir `DocumentBuilder` başlatmaya, düğmeyi `InsertForms2OleControl` ile eklemeye ve sonunda dosyayı Word'un denetimi tanıması için kaydetmeye kadar. Sonunda, tıklanabilir bir düğme içeren, kullanıma hazır bir Word dosyanız olacak—COM interop karmaşası gerekmeyecek.

## Gereksinimler

- **.NET 6.0** veya daha yeni (kod .NET Framework 4.6+ ile de çalışır).  
- **Aspose.Words for .NET** NuGet paketi (sürüm 23.9 veya daha yeni).  
- C# temellerine bir giriş (sözdizimini yeni başlayanlar için dost tutacağız).  
- Visual Studio 2022 veya tercih ettiğiniz herhangi bir IDE.

Hepsi bu—ekstra COM referansları, Office interop yok, sadece saf yönetilen kod.

---

## 1. Adım: Aspose.Words'i **create word document button** için Ayarlama

İlk olarak, Aspose.Words paketini projenize ekleyin:

```bash
dotnet add package Aspose.Words
```

Ya da Visual Studio NuGet UI'sını kullanıyorsanız, “Aspose.Words” aratıp **Install** düğmesine tıklayın. Bu tek satır, `Document`, `DocumentBuilder` ve daha sonra ihtiyaç duyacağımız `InsertForms2OleControl` metoduna erişim sağlar.

> **Pro tip:** NuGet paketlerinizi güncel tutun; yeni sürümler genellikle ActiveX işleme için hata düzeltmeleri içerir.

---

## 2. Adım: **DocumentBuilder**'ı bir **ActiveX CommandButton** için Başlatma

Şimdi yeni bir Word belgesi oluşturup bir `DocumentBuilder` başlatıyoruz. `DocumentBuilder`'ı, tuval üzerine içerik çizen bir fırça olarak düşünebilirsiniz.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

`System.Drawing`'i içe aktarmamıza dikkat edin—`Rectangle` yapısı düğmenin konum ve boyutunu tanımlar. İşte **ActiveX CommandButton**'ın yer alacağı yer.

---

## 3. Adım: **InsertForms2OleControl** ile **add a CommandButton** Kullanma

İşte öğreticinin kalbi: düğmenin kendisini eklemek. `InsertForms2OleControl` metodu üç argüman alır—denetim tipi, bir `Rectangle` ve isteğe bağlı bir ad. `OleControlType.CommandButton` kullanarak istediğimiz denetimi belirleyeceğiz.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Bu tek çağrı şunları yapar:

1. **OLE nesnesi** oluşturur ve Word dosyasına ekler.  
2. **ActiveX CommandButton** olarak kaydeder; Word bunu tıklanabilir bir UI öğesi olarak gösterir.  
3. **Rectangle** ile belirttiğimiz konuma yerleştirir.

Düğmenin başlığını veya diğer özelliklerini eklemeden sonra, temel `OleFormat` üzerinden değiştirebilirsiniz. Çoğu senaryo için varsayılan başlık (“CommandButton1”) yeterlidir.

---

## 4. Adım: **CommandButton** İçeren Word Belgesini Kaydetme

Kaydetmek basittir—yazma izniniz olan bir klasöre yönlendirin. Dosya uzantısı `.docx` olmalıdır, aksi takdirde düğme kaybolur.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

`CommandButton.docx` dosyasını Microsoft Word'de açtığınızda, ilk sayfanın sol‑üst köşesinde küçük bir düğme göreceksiniz. Varsayılan olarak tıkladığınızda bir şey yapmaz (bu VBA gerektirir), ancak denetim tamamen işlevseldir ve daha sonra bağlanabilir.

> **Neden çalışıyor:** Aspose.Words, OLE akışını doğrudan DOCX paketine yazar, Word'ün çalışma zamanında denetimi oluşturma ihtiyacını ortadan kaldırır. Bu, düğmenin tam olarak yerleştirildiği yerde görünmesini garanti eder.

---

## 5. Adım: Word'de Düğmeyi Doğrulama

Oluşturulan dosyayı açın:

1. Microsoft Word'ü başlatın.  
2. **File → Open** menüsünden `CommandButton.docx` dosyasını seçin.  
3. “CommandButton1” yazılı dikdörtgen bir düğme görmelisiniz.  

Düğmeyi görmüyorsanız, **Design Mode**'un etkin olduğundan emin olun (Developer → Design Mode). Bu, ActiveX denetimlerinin görsel temsilini açar/kapatır.

---

## 6. Adım: Gelişmiş Seçenekler – **ActiveX CommandButton** Özelleştirme

Aşağıda işinize yarayabilecek birkaç hızlı ayar bulunmaktadır:

| Amaç | Kod Parçası |
|------|--------------|
| Başlığı değiştir | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Makro adını ayarla (Word makro desteği gerekir) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Ekleme sonrası yeniden boyutlandır | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Bu parçacıklar `InsertForms2OleControl`'ün esnekliğini gösterir. `OleControlType` enum'ını değiştirerek `CheckBox` veya `ListBox` gibi diğer ActiveX denetimlerini de gömebilirsiniz.

---

## Tam Çalışan Örnek

Aşağıda, sıfırdan **creates a word document button** yapan, kopyala‑yapıştır hazır tam program yer almaktadır:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Programı çalıştırdığınızda beklenen çıktı:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Ortaya çıkan dosyayı açın; kodun yerleştirdiği konumda düğmeyi göreceksiniz.

---

## Yaygın Tuzaklar & Kaçınma Yolları

- **Missing `System.Drawing` reference** – `Rectangle` yapısı burada bulunur; olmadan derleyici hata verir.  
- **Using an older Aspose.Words version** – Eski sürümler `InsertForms2OleControl`'ü tam desteklemez. En son kararlı pakete yükseltin.  
- **Saving as `.doc` instead of `.docx`** – OLE akışı eski ikili formatta kesilir, düğme kaybolur.  
- **Running on a headless server without Word installed** – Düğme dosyada kalır, ancak Word olmadan önizleme yapamazsınız. Bu, otomatik üretim hatları için sorun teşkil etmez.

---

## Sonraki Adımlar – **create word document button** İş Akışını Genişletme

Temel bilgileri kavradığınıza göre, aşağıdaki ileri seviye fikirleri değerlendirebilirsiniz:

- **VBA makroları** ekleyerek düğmeye özel iş mantığı bağlamak.  
- Dinamik formlar için döngü içinde **birden çok düğme** oluşturmak.  
- **Aspose.PDF** ile aynı belgeyi PDF'ye dışa aktarırken görsel düzeni korumak (düğme PDF'de statik bir resim olur).  
- **

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak ilgili konuları kapsamaktadır. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımları keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words for .NET ile Word Belgesi Oluşturma](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Aspose.Words ile Word'de Dikdörtgen Şekil Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words kullanarak Word Belgesine Satır İçi Görsel Ekleme](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}