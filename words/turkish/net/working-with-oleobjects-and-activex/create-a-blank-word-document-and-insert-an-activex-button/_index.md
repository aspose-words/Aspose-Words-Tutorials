---
category: general
date: 2026-11-18
description: Boş bir Word belgesi oluşturun ve C# ile bir ActiveX düğmesi ekleyin.
  Kontrol eklemeyi, düğme başlığını ayarlamayı ve dosyayı kaydetmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: tr
lastmod: 2026-11-18
og_description: C# kullanarak boş bir Word belgesi oluşturun ve bir ActiveX düğmesi
  ekleyin. Kontrol eklemek, düğme başlığını ayarlamak ve sonucu kaydetmek için bu
  kapsamlı öğreticiyi izleyin.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Boş bir Word belgesi oluşturun ve bir ActiveX düğmesi ekleyin – adım adım
  rehber
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Boş bir Word belgesi oluşturun ve bir ActiveX düğmesi ekleyin
url: /tr/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş bir Word belgesi oluşturun ve bir ActiveX düğmesi ekleyin

**Boş bir Word belgesi** oluşturup içine etkileşimli bir ActiveX düğmesi yerleştirmeniz gerekiyorsa, bu kılavuz Aspose.Words for .NET ile bunu nasıl yapacağınızı adım adım gösterir. Tam kodu görecek, her satırın neden önemli olduğunu anlayacak ve **düğme başlığını ayarlamayı** öğreneceksiniz; böylece kontrol kullanıcı etkileşimine hazır görünecek.

Ana hedefin yanı sıra **ActiveX ekleme**, **kontrol ekleme** adımları ve **özelleştirilmiş başlıklı ActiveX düğmesi ekleme** inceliklerini de ele alacağız. Sonunda gömülü UI öğeleri gerektiren herhangi bir belge‑otomasyon senaryosu için yeniden kullanılabilir bir deseniniz olacak.

## Öğrenecekleriniz

* Programatik olarak **boş bir Word belgesi oluşturmayı**.  
* **ActiveX düğmesi eklemek** ve özelliklerini yapılandırmak için gereken kesin API çağrılarını.  
* **Düğme başlığını ayarlamayı** (set button caption) böylece kontrol istediğiniz metni göstersin.  
* Dosyayı istediğiniz bir konuma kaydetme ve yaygın hatalarla başa çıkma ipuçları.

### Önkoşullar

* .NET 6.0 veya üzeri (kod .NET Framework 4.6+ ile de çalışır).  
* Aspose.Words for .NET yüklü (`Install-Package Aspose.Words`).  
* C# ve Visual Studio ya da herhangi bir .NET‑uyumlu IDE hakkında temel bilgi.

---

## Aspose.Words ile boş bir Word belgesi oluşturma

İlk adım, içi boş bir `Document` nesnesi örneklemektir. Bu nesne, içerik ekleyene kadar hiçbir şey içermeyen bir Word dosyasını temsil eder.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Bu neden önemlidir*: Boş bir `Document`, size temiz bir tuval sağlar. Daha sonra paragraf, tablo ya da kontrol eklerken mevcut biçimlendirmelerle uğraşmazsınız.

---

## Belgeyle çalışmak için bir DocumentBuilder başlatma

`DocumentBuilder`, mevcut imleç konumunda içerik eklemenizi sağlayan bir yardımcı sınıftır. Belgedeki konumunuzu otomatik olarak izler.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Bu neden önemlidir*: Bir `DocumentBuilder` olmadan düşük seviyeli düğüm ağacını manuel olarak manipüle etmeniz gerekir. Builder, metin, resim ve ActiveX kontrollerinin eklenmesini basitleştirir.

---

## ActiveX düğmesi ekleme (insert activex button)

Şimdi `InsertForms2OleControl` kullanarak bir ActiveX kontrolü gömeceğiz. Metodun üç argümana ihtiyacı vardır:

1. Kontrol türü (`OleControlType.CommandButton`).  
2. Kontrol için iç ad (VBA veya makro kodu tarafından kullanılır).  
3. Sayfadaki konum ve boyutu tanımlayan bir `RectangleF`.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Bu neden önemlidir*: **Word belgesine activex ekleme**nin çekirdeği budur. Dikdörtgenin koordinatları puan cinsindendir (1 point = 1/72 inç). Düğmeyi istediğiniz yere konumlandırmak için bu değerleri ayarlayın.

### İpucu

Düğmenin belirli bir sayfada görünmesini istiyorsanız, önce builder’ın imlecini taşıyın:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Düğme başlığını ayarlama (set button caption)

Kontrol yerleştirildikten sonra özelliklerini değiştirebilirsiniz. En görünür özellik `Caption`’dır; bu, düğmede gösterilecek metni belirler.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Bu neden önemlidir*: Kullanıcılar iç adı değil, başlığı görür. Başlığı değiştirmek, düğmenin son belgede anlamlı olmasını sağlar.

---

## Düğme içeren belgeyi kaydetme

Son olarak belgeyi diske yazın. İstediğiniz herhangi bir desteklenen formatı (`.docx`, `.pdf`, vb.) seçebilirsiniz. Burada Word belgesi olarak kaydediyoruz.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Bu neden önemlidir*: Dosyanın kalıcı olması, Microsoft Word’de açıp düğmeyi test etmenizi sağlar. Belge açıldığında düğme “Press” başlığıyla görünür; varsayılan olarak bir VBA makrosu ekli değildir, ancak kontrol tamamen çalışır ve daha sonra kodla bağlanabilir.

### Beklenen sonuç

`with_button.docx` dosyasını Word’de açtığınızda, **Press** etiketiyle bir dikdörtgen düğme gösteren boş bir sayfa görürsünüz. Düğmeye tıklamak varsayılan olarak bir şey yapmaz çünkü bir VBA makrosu ekli değildir; ancak kontrol tam işlevseldir ve daha sonra koda bağlanabilir.

---

## Belirli bir paragrafta kontrol ekleme (how to add control)

Bazen düğmeyi belirli bir paragrafın içine, örneğin bazı açıklama metinlerinden sonra yerleştirmek istersiniz. Kontrolü eklemeden önce builder’ı konumlandırmak için `MoveTo` kullanın.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Bu neden önemlidir*: Bu desen, **kontrol ekleme**nin bağlam içinde nasıl yapılacağını gösterir ve belge düzeninin mantıklı kalmasını sağlar.

---

## Yaygın hatalar ve nasıl önlenir

| Sorun | Neden oluşur | Çözüm |
|-------|----------------|-----|
| Düğme sayfanın dışına çıkıyor | Dikdörtgen koordinatları sayfa kenar boşluklarının dışındadır | `builder.PageSetup` ile sayfa boyutlarını alın ve güvenli bir `RectangleF` hesaplayın. |
| Başlık görünmüyor | `Caption` kontrol tamamen başlatılmadan önce ayarlandı | `InsertForms2OleControl` çağrısından **sonra** `Caption` ayarlayın, adım 4’te gösterildiği gibi. |
| Belge düğmesiz kaydediliyor | Eklemeden sonra builder’ın imleci başka bir yere taşındı ve değişiklikler kaydedilmedi | Builder’ı aynı sayfada tutun veya kaydetmeden önce `builder.Document.UpdatePageLayout()` çağırın. |

---

## Tam, çalıştırılabilir örnek

Aşağıda kopyalayıp yapıştırıp çalıştırabileceğiniz tam program yer alıyor. Boş bir Word dosyası oluşturur, bir ActiveX düğmesi ekler, başlığını ayarlar ve sonucu kaydeder.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Çıktı**: Programı çalıştırdıktan sonra `C:\Temp\with_button.docx` dosyasını Microsoft Word’de açın. “Below is an ActiveX button created programmatically:” metninin ardından **Press** etiketiyle bir düğme içeren tek bir sayfa göreceksiniz.

---

## Sonuç

Artık **boş bir Word belgesi oluşturma**, **ActiveX düğmesi ekleme**, **düğme başlığını ayarlama** ve sonucu Aspose.Words for .NET ile **kaydetme** konularını biliyorsunuz. Aynı desen, `OleControlType` değerini değiştirerek diğer ActiveX kontrolleri (checkbox, list box vb.) için de genişletilebilir.

Sonraki adım olarak **ActiveX düğmesi olaylarını VBA ile ekleme** ya da **zaten içerik taşıyan belgelere kontrol ekleme** konularını keşfedebilirsiniz. Her iki konu da burada ele alınan kavramlar üzerine doğrudan inşa edilir.

İyi kodlamalar, ve uygulamanızın UI gereksinimlerine uygun farklı boyut, konum ve başlıklarla denemeler yapmaktan çekinmeyin!

## Bir Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [How to create Word document C# with an ActiveX command button](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}