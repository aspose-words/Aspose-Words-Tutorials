---
category: general
date: 2026-08-23
description: C# Word otomasyonunda gönder düğmesi oluşturun. ActiveX düğmesi eklemeyi,
  düğme adını, başlığını ve metnini programlı olarak ayarlamayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: tr
lastmod: 2026-08-23
og_description: C# Word otomasyonunda gönder düğmesi oluşturun. Bu kılavuz, bir ActiveX
  düğmesi eklemeyi, adını, başlığını ve metnini Aspose.Words kullanarak nasıl ayarlayacağınızı
  gösterir.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: C# Word otomasyonunda gönder düğmesi oluşturma
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: C# Word otomasyonunda gönder düğmesi nasıl oluşturulur
url: /tr/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# Word otomasyonu içinde gönder düğmesi (submit button) oluşturma

C# kullanarak bir Word belgesi içinde **create submit button** oluşturmanız gerekiyorsa, bu kılavuz size tüm süreci adım adım gösterir. ActiveX düğmesi eklemeyi, programatik bir ad atamayı ve düğmenin başlığını (caption) ayarlamayı öğrenecek, böylece normal bir *Submit* kontrolü gibi görünecek.

Word’de form kontrollerini otomatikleştirmek, manuel düzenleme işini ortadan kaldırabilir ve yüzlerce belge arasında tutarlılığı sağlayabilir. Aşağıdaki adımlarda ayrıca **set button text**, **set button name** ve **set button caption** nasıl yapılır da öğreneceksiniz—bu özellikler düğmenin makro‑tabanlı bir iş akışına katıldığı durumlarda çok önemlidir.

## Prerequisites

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 (veya daha yeni bir sürüm).
* **Aspose.Words for .NET** referansı (`DocumentBuilder.InsertForms2OleControl` metodunu sağlayan kütüphane).
* C# ve Word’ün ActiveX form kontrolleri hakkında temel bilgi.

Aspose.Words’u NuGet üzerinden kurabilirsiniz:

```bash
dotnet add package Aspose.Words
```

> **İpucu:** ActiveX kontrolleriyle ilgili hata düzeltmelerinden ve yeni özelliklerden yararlanmak için Aspose.Words’un en son kararlı sürümünü kullanın.

## Overview of the solution

Kılavuz üç net adıma bölünmüştür:

1. **Add ActiveX button** – `InsertForms2OleControl` metodunu kullanarak belgeye bir komut düğmesi yerleştirin.  
2. **Set button name** – `Name` özelliğiyle benzersiz bir programatik tanımlayıcı atayın.  
3. **Set button caption** – `Caption` özelliğiyle düğmenin görünen metnini tanımlayın (bu aynı zamanda UI’da gördüğünüz **set button text** değerini kontrol eder).

Kılavuzun sonunda, herhangi bir Word otomasyon projesinde yeniden kullanabileceğiniz tam işlevsel bir **create submit button** rutinine sahip olacaksınız.

## Step 1: Add an ActiveX button to the document

İlk görev **add activex button** işlemini Word dosyasına eklemektir. Aspose.Words bu amaçla `Forms2OleControlType.CommandButton` enum’ını sunar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Bu adımın önemi:**  
ActiveX kontrolleri, VBA makrolarını çalıştırabilen veya harici kodla etkileşime girebilen tek Word form öğesidir. Kontrolü eklemek, sonraki adımların yapılandırabileceği bir yer tutucu oluşturur.

> **Kenar durumu:** Belge zaten aynı ada sahip bir kontrol içeriyorsa, Word yeni kontrolü otomatik olarak yeniden adlandırır (ör. `CommandButton1`). Bir sonraki adımda adı açıkça ayarlamak bu çakışmaları önler.

## Step 2: Set the button name

Güvenilir bir **set button name** değeri, kontrolü VBA’dan ya da C# kodunuzun diğer bölümlerinden referans almanız gerektiğinde kritiktir. `Name` özelliği düğmeye programatik bir tanımlayıcı verir.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Neden bir ad ayarlamalısınız:**  
Belge açıldığında VBA, düğmeyi `ActiveDocument.InlineShapes("btnSubmit")` ifadesiyle alabilir. `btnSubmit` gibi anlamlı bir ad, belgenin XML’ini incelerken niyeti de netleştirir.

> **İpucu:** Adları kısa, alfanümerik ve bir harfle başlayan şekilde tutun; bu, VBA adlandırma kurallarıyla uyumluluğu sağlar.

## Step 3: Set the button caption (visible text)

Kullanıcıların düğme üzerinde gördüğü metin, **set button caption** özelliğiyle kontrol edilir. Word UI’da bu, düğmenin etiketi olarak görünür ve aynı zamanda **set button text** olarak da adlandırılır.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Başlığın (caption) önemi:**  
Caption, kullanıcıya gösterilen etikettir. Daha sonra değiştirilmesi, düğmenin adını etkilemez; bu sayede `btnSubmit` gibi kod bağımlılıklarını bozmadan UI’yı yerelleştirebilirsiniz.

> **Sık sorulan soru:** *Hem Caption hem de Value ayarlayabilir miyim?*  
> `CommandButton` için `Caption` etiketi kontrol eder, `Value` kullanılmaz. Gizli bir değer gerekiyorsa, bunun yerine özel bir belge özelliği (custom document property) kullanın.

## Full working example

Üç adımı birleştirerek herhangi bir konsol ya da Windows uygulamasına ekleyebileceğiniz tam bir rutin elde edersiniz:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Expected output

Programı çalıştırdığınızda `SubmitButton.docx` oluşturulur. Microsoft Word’de dosyayı açtığınızda:

* Belirtilen konumda bir **Submit** düğmesi görünür.
* Düğmenin adı `btnSubmit` olur (*Developer → Design Mode → Properties* üzerinden kontrol edebilirsiniz).
* Tasarım modunda düğmeye tıkladığınızda başlık *Submit* olarak gösterilir.

Artık form‑tabanlı herhangi bir Word çözümü için yeniden kullanılabilir bir yapı taşı elde ettiniz.

## Additional considerations

### Handling naming collisions

Aynı belge üzerinde rutini birden fazla kez çalıştırırsanız, Word yinelenen kontrolleri otomatik olarak yeniden adlandırabilir. Tekilliği garantilemek için adı bir GUID ile ön ekleyebilirsiniz:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Localizing the button caption

Çok dilli belgeler için başlıkları bir kaynak dosyasında tutup çalışma zamanında atayabilirsiniz:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Responding to the button click

Düğmenin kendisi C# içinde tıklama mantığı içermez. Genellikle bir VBA makrosu eklenir:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

`btnSubmit` olarak **set button name** belirlediğiniz için, makro adı otomatik olarak `<Name>_Click` biçiminde olur.

## Troubleshooting FAQ

| Question | Answer |
|----------|--------|
| **Why does the button appear blank?** | `Caption` özelliğini ayarladığınızdan emin olun; aksi takdirde düğme metin göstermeyecektir. |
| **Can I use a different ActiveX control?** | Evet. `Forms2OleControlType.CommandButton` yerine `CheckBox`, `OptionButton` vb. kullanabilirsiniz; ancak özellikler farklıdır. |
| **Is this compatible with .NET Core?** | Aspose.Words for .NET .NET 6+’ı destekler, bu yüzden aynı kod .NET Core ve .NET Framework üzerinde çalışır. |
| **What if the document already has a button?** | Çakışmaları önlemek için benzersiz bir `Name` (ör. bir GUID ekleyerek) kullanın. |

## Conclusion

Artık C# kullanarak bir Word belgesinde **create submit button** programlı bir şekilde oluşturmayı biliyorsunuz. Üç adımı—**add activex button**, **set button name**, ve **set button caption**—takip ederek, herhangi bir otomatik form çözümü için **set button text**, **set button name** ve **set button caption** işlemlerini güvenle yapabilirsiniz.

Bundan sonra şunları keşfedebilirsiniz:

* **submit button** tıklamasına yanıt veren VBA makroları eklemek.
* Altta yatan XML üzerinden düğmeye özel yazı tipleri veya renkler stil vermek.
* Dinamik formlar için döngü içinde birden fazla düğme üretmek.

Farklı başlıklar, adlar ve konumlarla deneyler yaparak kendi iş akışınıza en uygun hâle getirin. Otomasyonun keyfini çıkarın!

## What Should You Learn Next?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, tam çalışan kod örnekleri ve adım adım açıklamalar içerir; böylece ek API özelliklerini öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}