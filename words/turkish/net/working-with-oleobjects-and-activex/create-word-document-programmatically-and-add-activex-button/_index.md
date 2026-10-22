---
category: general
date: 2026-08-10
description: Aspose.Words ile programlı olarak Word belgesi oluşturun, ardından bir
  ActiveX kontrolü kelime düğmesi ekleyin. ActiveX komut düğmesini dakikalar içinde
  ekleyin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: tr
lastmod: 2026-08-10
og_description: Aspose.Words kullanarak programlı bir şekilde Word belgesi oluşturun,
  ardından bir ActiveX kontrolü kelime düğmesi ekleyin. ActiveX komut düğmesini hızlıca
  nasıl ekleyeceğinizi öğrenin.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Word belgesini programlı olarak oluştur – C#'ta bir ActiveX düğmesi ekle
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Word belgesini programlı olarak oluştur ve ActiveX düğmesi ekle
url: /tr/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word belgesi programlı olarak oluşturma ve ActiveX düğmesi ekleme

Eğer **programlı olarak word belgesi oluşturmanız** gerekiyorsa, bu kılavuz Aspose.Words for .NET ile tüm süreci adım adım anlatır. Ayrıca **activex kontrol word** öğelerini nasıl **activex komut düğmesi** nesneleri ekleyeceğinizi tek bir, bağımsız örnekle öğreneceksiniz.

Koddan Word dosyaları üretmek, Microsoft Word'ü manuel olarak açma adımını ortadan kaldırır; raporlar, faturalar veya veri‑tabanlı sözleşmeleri otomatik olarak oluşturabilirsiniz. Bu öğreticinin sonunda, etkileşimli bir ActiveX CommandButton içeren bir `.docx` dosyası üreten, çalıştırmaya hazır bir C# konsol uygulamanız olacak.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 SDK veya daha yeni bir sürüm (kod .NET Framework 4.6+ ile de çalışır)
* Visual Studio 2022 veya .NET geliştirmeyi destekleyen herhangi bir IDE
* Geçerli bir Aspose.Words for .NET lisansı (test için ücretsiz deneme anahtarını kullanabilirsiniz)
* C# sözdizimi ve COM/ActiveX kontrolleri kavramına temel aşinalık

> **Pro tip:** Oluşturulan belgeyi Word yüklü olmayan kullanıcılara dağıtmayı planlıyorsanız, ActiveX kontrolünün çalışma zamanı dosyalarını `.docx` dosyasının yanına yerleştirin veya makro‑etkin bir şablon sağlayın.

## Programlı olarak word belgesi oluşturma – başlangıç ayarları

İlk olarak, Aspose.Words NuGet paketini projenize ekleyin:

```bash
dotnet add package Aspose.Words
```

Ardından yeni bir konsol projesi oluşturun (henüz yoksa):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Oluşturulan `Program.cs` dosyasını açın – içeriğini aşağıdaki tam çözümle değiştireceğiz.

## Adım 1: Ad alanlarını içe aktar ve lisansı yapılandır

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Neden önemli*: `Aspose.Words.Drawing` alanını içe aktarmak, Word belgesi içinde bir ActiveX kontrolünü temsil eden `Forms2OleControl` sınıfına erişmenizi sağlar. Lisansı erken ayarlamak, üretimde çalışma zamanı uyarılarını önler.

## Adım 2: Boş bir belge ve DocumentBuilder oluştur

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` nesnesi, bir `.docx` dosyasının bellek içi temsilidir. `DocumentBuilder` ise belge içinde öğeler eklemek için hareket ettirdiğiniz bir imleç gibi çalışır.

## Adım 3: ActiveX CommandButton kontrolünü ekle

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` bir OLE nesnesi oluşturur ve Word bunu bir ActiveX kontrolü olarak işler. Koordinat sistemi nokta birimini (1 point = 1/72 inç) kullanır; bu, Word'ün yerleşim motoruyla eşleşir.

## Adım 4: Düğmenin başlığını ve isteğe bağlı özelliklerini ayarla

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

`Caption` özelliğini ayarlamak, düğmeye etiket vermenin en yaygın yoludur. Düğmenin bir VBA makrosu çalıştırmasını istiyorsanız, makro adını `OnAction` özelliğine atayın. Bu öğretici görsel kısmı ele alır; makro entegrasyonu “Sonraki adımlar” bölümünde ele alınır.

## Adım 5: Belgeyi kaydet

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Programı çalıştırdığınızda, konsolda `ActiveX_CommandButton.docx` dosyasının diske yazıldığını belirten bir mesaj göreceksiniz.

### Tam kaynak kodu (kopyala‑yapıştır hazır)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Kod parçacığını çalıştırdığınızda, tıklanabilir bir **ActiveX command button** içeren bir Word dosyası elde edersiniz. Dosyayı Microsoft Word'de açın, **Design Mode** (Geliştirici sekmesi → Design Mode) etkinleştirin ve düğmenin tam olarak yerleştirdiğiniz yerde göründüğünü göreceksiniz.

## Adım 6: Sonucu doğrula

1. `ActiveX_CommandButton.docx` dosyasını Microsoft Word'de açın.
2. **Developer** sekmesi görünmüyorsa etkinleştirin (`File → Options → Customize Ribbon → check Developer`).
3. **Design Mode**'a tıklayın. Düğme “Submit” etiketiyle görünmelidir.
4. Eğer bir `OnAction` makrosu eklediyseniz, Design Mode kapalıyken düğmeye tıklayarak makroyu çalıştırın.

Düğme görünmüyorsa, Word'ün güvenlik ayarlarının ActiveX kontrollerine izin verdiğinden emin olun (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## Yaygın sorular ve kenar durumları

| Soru | Cevap |
|------|-------|
| **Başka ActiveX türleri ekleyebilir miyim?** | Evet. `Forms2OleControlType` enum'ı `CheckBox`, `OptionButton`, `ComboBox` vb. değerleri içerir. `CommandButton` yerine istediğiniz enum değerini kullanın. |

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakın ilişkili konuları ele alır. Her kaynak, adım adım açıklamalarla tam çalışan kod örnekleri içerir; böylece ek API özelliklerini ustalaşabilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}