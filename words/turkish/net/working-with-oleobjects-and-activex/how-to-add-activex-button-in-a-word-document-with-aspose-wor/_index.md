---
category: general
date: 2026-08-14
description: Aspose.Words kullanarak bir Word belgesine ActiveX düğmesi ekleme – boş
  bir Word belgesi oluşturmayı ve programlı olarak bir ActiveX düğmesi eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: tr
lastmod: 2026-08-14
og_description: Aspose.Words ile bir Word belgesine ActiveX düğmesi ekleme. Bu öğreticide
  boş bir Word belgesi oluşturmayı, bir ActiveX düğmesi eklemeyi ve sonucu kaydetmeyi
  gösterir.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Word'de ActiveX düğmesi ekleme – Aspose.Words rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Aspose.Words ile bir Word belgesine ActiveX düğmesi ekleme
url: /tr/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile bir Word belgesine ActiveX düğmesi ekleme

Oluşturulan bir Word dosyasına **ActiveX ekleme** denetimlerini eklemeniz gerekiyorsa, bu kılavuz size tam adımları gösterir. **ActiveX düğmesi eklemeyi** programlı olarak öğreneceksiniz, **boş Word belgesi oluşturma** ile başlayıp Microsoft Word'de açılabilecek bir dosya kaydetme ile sonlanacak.

ActiveX kodu çalıştıran veya bir makroyu tetikleyen bir düğme eklemek, otomatik rapor oluşturucular, form şablonları veya etkileşimli sözleşmeler için yaygın bir gereksinimdir. Aspose.Words for .NET kullanarak belgeyi Office'i başlatmadan oluşturabilirsiniz; bu, sürecin hızlı ve sunucu dostu olmasını sağlar.

## Önkoşullar

* .NET 6.0 (veya daha yeni) SDK yüklü.
* Visual Studio 2022 veya herhangi bir C# uyumlu IDE.
* Aspose.Words for .NET NuGet paketi (`Aspose.Words` sürüm 24.9 veya daha yeni).  
  Şu komutla yükleyin:
  ```bash
  dotnet add package Aspose.Words
  ```
* ActiveX düğmesini test etmeyi planlıyorsanız bir Windows ortamı, çünkü ActiveX denetimleri Microsoft Word'ün Windows sürümünü gerektirir.

## Adım 1: Boş bir Word belgesi oluşturma

İlk görev, bellekte **boş Word belgesi oluşturma**dır. Aspose.Words bu amaçla `Document` sınıfını sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document`, tüm .docx dosyasını temsil eder. Bu noktada belge hiçbir sayfa içermez, ancak içeriği hemen eklemeye başlayabilirsiniz.

## Adım 2: DocumentBuilder'ı Başlatma

`DocumentBuilder`, belgeye metin, resim ve diğer nesneleri eklemenizi sağlayan bir yardımcıdır. Az önce oluşturduğunuz `Document` örneği üzerinde çalışır.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder, bir imleç konumu tutar; bu satırdan sonra eklediğiniz her şey ilk sayfanın başında görünür.

## Adım 3: ActiveX CommandButton denetimi ekleme

Aspose.Words, ActiveX dahil eski form denetimlerini eklemek için `InsertForms2OleControl` metodunu sunar. Metod, denetim tipini ve boyutunu point cinsinden gerektirir.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

Dönen `Forms2OleControl` nesnesi, denetimin adını ve başlığını (caption) gibi özellikleri yapılandırmanıza olanak tanır.

## Adım 4: Düğmenin özelliklerini yapılandırma

Anlamlı bir `Name` ayarlamak, denetimi daha sonra VBA kodundan referans almanızı sağlar. `Caption`, kullanıcının düğmede gördüğü metindir.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro ipucu:** İsmi kısa ve alfanümerik tutun; Word, boşluk veya özel karakter içeren isimleri reddeder.

## Adım 5: Belgeyi kaydetme

Son olarak, belgeyi diske yazın. Modern Word dosyaları için `.docx` uzantısını kullanın; ActiveX düğmesi `.doc` dosyalarında da aynı şekilde çalışır, ancak yeni projeler için `.docx` tercih edilen formattır.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

`ActiveXButton.docx` dosyasını Microsoft Word'de açtığınızda tıklanabilir bir **Submit** düğmesi göreceksiniz. Makroları etkinleştirirseniz, `btnSubmit_Click` öğesine VBA kodu ekleyebilir ve kullanıcı düğmeye tıkladığında çalışmasını sağlayabilirsiniz.

## Tam, çalıştırılabilir örnek

Tüm parçaları bir araya getirerek kopyalayıp yapıştırabileceğiniz ve çalıştırabileceğiniz bağımsız bir program elde edersiniz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Beklenen çıktı** – Programı çalıştırdıktan sonra konsol kaydetme konumunu yazdırır ve oluşturulan dosyayı Word'de açtığınızda ilk sayfanın üst kısmında **Submit** etiketiyle bir düğme gösterilir.

## Yaygın sorular ve kenar durumlarıyla başa çıkma

### Düğme tüm Word sürümlerinde çalışıyor mu?

ActiveX denetimleri, Windows üzerindeki masaüstü Word sürümünde desteklenir. Word Online, macOS için Word veya mobil istemcilerde görüntülenmezler. Çapraz platform etkileşimi gerekiyorsa, bunun yerine içerik denetimlerini veya HTML tabanlı çözümleri kullanmayı düşünün.

### Farklı bir boyut veya konuma ihtiyacım olursa?

`InsertForms2OleControl`, denetimi mevcut builder imlecinde konumlandırır. Taşımak için, eklemeden önce `builder.MoveTo` ile imleci ayarlayın veya oluşturulduktan sonra denetimin `Left` ve `Top` özelliklerini değiştirin:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Başka ActiveX tipleri ekleyebilir miyim?

Evet. `Forms2OleControlType` enum'ı `CheckBox`, `OptionButton`, `ListBox` ve daha fazlasını içerir. `CommandButton` yerine istediğiniz enum değerini koyun ve özellikleri buna göre ayarlayın.

### Düğmenin bir şey yapması için makro gerekli mi?

Düğme, VBA kodu ekleyene kadar hiçbir şey yapmaz. Word'de **Alt+F11** tuşlarına basarak VBA editörünü açın, `btnSubmit_Click` öğesini bulun ve istediğiniz mantığı yazın. Oluşturulan belge, **SaveFormat.Doc** (eski `.doc`) formatını etkinleştirirseniz VBA projesini tutar, ancak `.docx` dosyaları VBA makrolarını saklayamaz. Gömülü VBA'ya ihtiyacınız varsa `.doc` formatını kullanın.

## Sonuç

Artık Aspose.Words kullanarak bir Word dosyasına **ActiveX ekleme** denetimlerini nasıl ekleyeceğinizi biliyorsunuz. **Boş Word belgesi oluşturma**, bir `DocumentBuilder` başlatma, **ActiveX düğmesi ekleme**, özelliklerini yapılandırma ve dosyayı kaydetme adımlarını izleyerek .NET kodunuzdan doğrudan etkileşimli Word şablonları oluşturabilirsiniz.

Sonra, **ActiveX düğmesi ekleme** olay işleme, tablolar veya resimler için **create word document aspose** ekleme ve kurumsal dağıtım için makro‑etkin belgeleri güvence altına alma gibi ilgili konuları keşfedin. Farklı denetim tipleri ve düzen seçenekleriyle deney yaparak kullanıcı deneyimini uygulamanızın ihtiyaçlarına göre özelleştirin.

Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words Kullanarak Başlık ve Altbilgi ile Word Belgesi Oluşturma](/words/english/net/header-footer-formatting/create-header-footer/)
- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Kullanarak Tablo ile Word Belgesi Oluşturma](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}