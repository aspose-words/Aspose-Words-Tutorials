---
category: general
date: 2026-09-05
description: Aspose.Words C# kullanarak Word belgesi oluşturun ve ActiveX komut düğmesi
  eklemeyi, düğme boyutunu ayarlamayı ve etkileşimli düğme işlevselliği eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: tr
lastmod: 2026-09-05
og_description: C# ile Word belgesi oluşturun ve bir ActiveX komut düğmesi ekleyin.
  Bu öğreticide düğme boyutunu nasıl ayarlayacağınız ve etkileşimli düğme özellikleri
  ekleyeceğiniz gösterilmektedir.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: C# ile ActiveX komut düğmesi kullanarak Word belgesi oluşturma – adım adım
  rehber
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: C#'ta ActiveX komut düğmesiyle Word belgesi nasıl oluşturulur
url: /tr/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile ActiveX komut düğmesi ekleyerek Word belgesi oluşturma

Programatik olarak **Word belgesi** oluşturmanız ve tıklanabilir bir UI öğesi eklemeniz gerekiyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. Aspose.Words for .NET kullanarak **Word belgesi** oluşturabilir, **komut düğmesi ekleyebilir** ve görünümünü kontrol edebilirsiniz—Microsoft Word'ü açmadan.

**ActiveX** denetimlerini nasıl ekleyeceğinizi, **düğme boyutunu nasıl ayarlayacağınızı** ve düğmeyi etkileşimli bir UI bileşeni gibi nasıl davranacağını öğreneceksiniz. COM veya VBA konusunda önceden deneyim gerekmez; sadece bir .NET geliştirme ortamı ve Aspose.Words kütüphanesi yeterlidir.

## Öğrenecekleriniz

Bu öğreticinin sonunda şunları yapabileceksiniz:

* C# ile sıfırdan **Word belgesi oluşturma**.
* **ActiveX komut düğmesi ekleme** (klasik “Click Me” kontrolü).
* **Düğme boyutunu** ve konumunu kesin olarak ayarlama.
* İsteğe bağlı olarak basit **etkileşimli düğme** mantığı ekleme (ör. bir makro yer tutucu).
* Dosyayı Microsoft Word ya da uyumlu bir görüntüleyicide açılabilecek bir `.docx` olarak kaydetme.

### Önkoşullar

| Gereksinim | Sebep |
|-------------|--------|
| .NET 6.0 veya üzeri | C# kodu için çalışma zamanını sağlar. |
| Aspose.Words for .NET (en son sürüm) | Örnekte kullanılan `Document`, `DocumentBuilder` ve `Forms2OleControl` API'lerini sağlar. |
| Visual Studio 2022 (veya herhangi bir C# IDE) | Örneği derlemeyi ve çalıştırmayı kolaylaştırır. |
| Temel C# bilgisi | Kod akışını anlamak için gereklidir. |

> **Pro ipucu:** Aspose.Words'un deneme sürümünü kullanıyorsanız, kodu çalıştırmadan önce lisansı ayarladığınızdan emin olun; aksi takdirde değerlendirme filigranları görürsünüz.

## Word belgesi oluşturma – genel iş akışı

İşlem dört mantıksal adımdan oluşur:

1. **Yeni bir belge** ve onu düzenlemek için bir `DocumentBuilder` başlatma.  
2. `InsertForms2OleControl` kullanarak **ActiveX komut düğmesi ekleme**.  
3. **Düğmeyi yapılandırma** – başlık, boyut ve konum.  
4. **Belgeyi** diske **kaydetme**.

Her adım aşağıdaki kendi bölümünde açıklanmıştır.

![ActiveX düğmeli Word belgesi](/images/activex-button.png "C# ile oluşturulmuş ActiveX komut düğmesi içeren bir Word belgesinin ekran görüntüsü")

## ActiveX komut düğmesi ekleme

**ActiveX ekleme** bölümü `InsertForms2OleControl` yöntemiyle başlar. Bu yöntem, Word'ün bir ActiveX nesnesi olarak gördüğü COM‑tabanlı bir denetim oluşturur.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Neden bu çalışıyor:** `OleControlType.CommandButton`, Aspose.Words'a klasik VB‑stilinde bir düğme oluşturmasını söyler. Boyut ve konum, nokta cinsinden ifade edilir (1 nokta = 1/72 inç), bu da yerleşim üzerinde hassas kontrol sağlar.

## Komut düğmesi ekleme ve düğme boyutunu ayarlama

Denetim eklendikten sonra görsel özelliklerini ayarlayabilirsiniz. **Komut düğmesi ekleme** adımı aynı zamanda **düğme boyutunu ayarlama** konusunu da kapsar.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Açıklama:**  

* `Caption`, düğmede gösterilen etikettir.  
* `Width` ve `Height`, ilk eklemeden sonra **düğme boyutunu ayarlamanıza** olanak tanır—boyut çalışma zamanındaki verilere bağlı olduğunda faydalıdır.  
* `Left` ve `Top`, belgeyi yeniden oluşturmadan denetimin konumunu değiştirir.

> **Yaygın tuzak:** Piksel yerine nokta kullanmayı unutmak, düğmenin çok küçük ya da çok büyük görünmesine neden olur. Ekran ölçümlerinden başlıyorsanız her zaman piksel değerlerini (`px * 72 / DPI`) dönüştürün.

## Etkileşimli düğme ekleme (isteğe bağlı)

Bir ActiveX düğmesi tıklandığında bir makro çalıştırabilir, ancak C#'tan VBA kodu gömmek saf bir Aspose.Words iş akışı kapsamında değildir. Bunun yerine, Word'ün bir makro adı olarak tanıyacağı bir yer tutucu özellik ekleyebilirsiniz.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Kullanıcı oluşturulan `.docx` dosyasını Word'de açtığında, düğmeye tıklamak `MyMacroName`'i çalıştırmaya çalışacaktır. Makro mevcut değilse, Word kullanıcıyı oluşturması için uyarır.

**Neden bunu kullanabilirsiniz:** Bir makronun alanları doldurduğu kurumsal formlarda, C# kodunun sadece düğmeyi yerleştirmesi yeterlidir; makro mantığı belgenin VBA projesinde bulunur.

## Belgeyi kaydetme ve sonucu doğrulama

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Beklenen çıktı:** `CommandButton.docx` dosyasını Microsoft Word'de açtığınızda, sol kenar boşluğundan 100 nokta, üstten 120 nokta uzaklıkta **Click Me** etiketiyle bir düğme gösterilir. Düğmenin boyutları **200 nokta × 80 nokta**dır. Düğmeye tıklamak (varsa) makro yer tutucusunu tetikler.

## Tam çalışan örnek

Aşağıda her şeyi bir araya getiren tam, çalıştırılabilir program yer almaktadır. Yeni bir Console App projesine kopyalayın, Aspose.Words NuGet paketini ekleyin ve çalıştırın.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Programı çalıştırın, ardından oluşturulan dosyayı açın. **Etkileşimli düğmeyi** daha fazla özelleştirme için hazır göreceksiniz.

## Sıkça Sorulan Sorular

| Soru | Cevap |
|----------|--------|
| **Bu .NET Core ile çalışır mı?** | Evet. Aspose.Words .NET Standard'ı destekler, bu yüzden aynı kod .NET 5/6/7'de çalışır. |
| **Diğer ActiveX denetimlerini (ör. CheckBox) kullanabilir miyim?** | Kesinlikle. `OleControlType.CommandButton` yerine `OleControlType.CheckBox`, `OleControlType.OptionButton` vb. kullanın. |
| **Yatay sayfada daha büyük bir düğmeye ihtiyacım olursa?** | `Width`, `Height`, `Left` ve `Top` özelliklerini orantılı olarak ayarlayın. Noktaların sayfa yönüne bakılmaksızın aynı kaldığını unutmayın. |
| **Düğmenin tıklanabilir olması için bir makro gerekli mi?** | Hayır. Düğme bir UI öğesi olarak tamamen işlevseldir; makro sadece tıklandığında özel davranış ekler. |

## Sonuç

Artık Aspose.Words ile **Word belgesi oluşturma**, **komut düğmesi ekleme**, **düğme boyutunu ayarlama** ve isteğe bağlı olarak düğmeyi bir makroya bağlayarak **etkileşimli düğme** davranışı ekleme konusunda bilgi sahibisiniz. Bu yaklaşım, form oluşturmayı otomatikleştirmenize, dinamik raporlar üretmenize veya C#'tan doğrudan Word‑tabanlı UI prototipleri oluşturmanıza olanak tanır.

Sonra şunları keşfedebilirsiniz:

* **Anket formları için ActiveX onay kutuları ekleme**.  
* `DocumentBuilder` kullanarak düğmenin etrafına **zengin metin içeriği ekleme**.  
* **Düğmeyi işlevsel tutarken belgeyi koruma**.

Farklı denetim tipleri, boyutlar ve makro adlarıyla denemeler yapmaktan çekinmeyin; böylece senaryonuza en uygun çözümü bulabilirsiniz. Kodlamanın tadını çıkarın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for .NET ile Word Belgesi Oluşturma](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Aspose.Words kullanarak Word Belgesine Satır İçi Görsel Ekleme](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Aspose.Words ile Tablo Kullanarak Word Belgesi Oluşturma](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}