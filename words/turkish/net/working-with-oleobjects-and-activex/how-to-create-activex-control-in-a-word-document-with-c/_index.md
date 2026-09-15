---
category: general
date: 2026-09-14
description: C# ile bir Word belgesine ActiveX kontrolü oluşturun. ActiveX eklemeyi,
  etkileşimli bir düğme eklemeyi ve .docx dosyasını programlı olarak oluşturmayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: tr
lastmod: 2026-09-14
og_description: C# ile bir Word belgesine ActiveX kontrolü oluşturun. ActiveX eklemek,
  etkileşimli bir düğme eklemek ve dosyayı kaydetmek için bu tam örneği izleyin.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: C# kullanarak Word’te ActiveX kontrolü oluşturma – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: C# ile bir Word belgesinde ActiveX kontrolü nasıl oluşturulur
url: /tr/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile bir Word belgesinde ActiveX kontrolü nasıl oluşturulur

Microsoft Word dosyası içinde **ActiveX kontrolü oluşturmanız** gerekiyorsa, bu kılavuz size eksiksiz, doğrudan çalıştırılabilir bir çözüm gösterir. ActiveX CommandButton nasıl eklenir, özellikleri nasıl ayarlanır ve ortaya çıkan `.docx` dosyası yalnızca C# kodu kullanılarak nasıl kaydedilir, tam olarak göreceksiniz.

Bir Word belgesine etkileşimli bir düğme eklemek, son kullanıcıların makroları veya özel mantığı doğrudan belge arayüzünden tetiklemelerini istediğinizde yaygın bir gereksinimdir. Aşağıdaki örnek, üçüncü taraf araçlara başvurmadan **ActiveX nasıl eklenir** gösterir ve ayrıca **Word belgesi nasıl programlı olarak oluşturulur** konusunu da kapsar.

Bu öğreticinin sonunda **kod ile düğme oluşturabilir**, başlığını özelleştirebilir ve ActiveX kontrolünü koruyan taşınabilir bir Word dosyası üretebilirsiniz.

## Önkoşullar

- .NET 6.0 veya daha yeni bir sürüm (Aspose.Words for .NET kütüphanesi .NET Core ve .NET Framework ile çalışır)
- `Aspose.Words` NuGet paketine bir referans  
  ```bash
  dotnet add package Aspose.Words
  ```
- C# ve nesne‑yönelimli programlama hakkında temel bilgi

## Adım 1: Projeyi kurun ve ad alanlarını içe aktarın

Yeni bir konsol projesi oluşturun (veya kodu mevcut herhangi bir C# uygulamasına entegre edin). Derleyicinin Word‑işleme sınıflarını bulabilmesi için gerekli ad alanlarını içe aktarın.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Bu adımın önemi** – `Aspose.Words` API'si, Word dosyalarını nesne seviyesinde manipüle etmenizi sağlayan `Document`, `DocumentBuilder` ve `Forms2OleControl` sınıflarını sağlar. Bu referanslar olmadan kodun geri kalanı derlenemez.

## Adım 2: Yeni bir Word belgesi ve DocumentBuilder oluşturun

`Document` nesnesi tüm `.docx` paketini temsil eder, `DocumentBuilder` ise içerik eklemek için akıcı bir API sunar.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Açıklama** – Yeni bir `Document` örneği oluşturmak size temiz bir tuval sağlar. Builder'ın imleci ilk bölümün başında başlar ve bir sonraki ekleme için hazırdır.

## Adım 3: ActiveX CommandButton ekleyin

`InsertForms2OleControl` kullanarak belirli bir konuma ActiveX kontrolü yerleştirin. Metot, kontrol tipini ve X/Y koordinatlarını ve boyutu (nokta cinsinden) tanımlayan bir `RectangleF` gerektirir.

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Neden çalışır** – `OleControlType.CommandButton` API'ye standart bir Windows CommandButton oluşturmasını söyler. Dikdörtgen, düğmeyi sayfanın sol‑üst köşesine göre konumlandırır ve **etkileşimli düğme eklemenizi** tam istediğiniz yere sağlar.

## Adım 4: Düğmenin özelliklerini yapılandırın

Şimdi düğmenin görünen metnini (`Caption`) ve iç adını (`Name`) ayarlayın. Bu özellikler, kullanıcıların gördükleri ve VBA kodunun daha sonra başvurabileceği şeylerdir.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Pratik ipucu** – `Name` belgenin içinde benzersiz olmalıdır; aksi takdirde VBA makroları yanlış kontrole başvurabilir.

## Adım 5: Belgeyi kaydedin

Son olarak, dosyayı diske yazın. ActiveX kontrolü Word paketinin içinde depolanır, bu yüzden kaydedilen dosya Microsoft Word'de açıldığında tam işlevselliğini korur.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Sonuç** – `CommandButton.docx` dosyasını Word'de açtığınızda “Click Me” etiketiyle bir tıklanabilir CommandButton gösterilir. Kontrol, Word arayüzü (`Developer → Design Mode → Properties`) üzerinden bir makroya bağlanabilir.

## Tam kaynak listesi

Tüm adımları bir araya getirerek kopyalayıp yapıştırabileceğiniz ve çalıştırabileceğiniz tek bir, bağımsız program elde edersiniz.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Beklenen çıktı

Programı çalıştırmak bir onay satırı yazdırır:

```
Document saved to C:\Temp\CommandButton.docx
```

Oluşturulan dosyayı Microsoft Word'de açtığınızda, belirtilen koordinatlarda yer alan bir **CommandButton** göreceksiniz. Tasarım modunda düğmeye tıklamak onu vurgular; çalışma modunda ise standart bir ActiveX düğmesi gibi davranır.

## Yaygın varyasyonlar ve kenar durumları

| Senaryo | Ayarlama |
|----------|------------|
| **Farklı kontrol tipi** | `OleControlType.CommandButton` yerine `OleControlType.CheckBox`, `OleControlType.OptionButton` vb. kullanın. |
| **Birden fazla düğme** | `InsertForms2OleControl` metodunu tekrarlayarak çağırın ve her yeni düğme için `RectangleF` koordinatlarını güncelleyin. |
| **Dinamik boyutlandırma** | Dikdörtgen boyutlarını sayfa boyutuna (`builder.PageSetup.PageWidth`) göre hesaplayın. |
| **Akıma kaydetme** | Web API'den dosyayı döndürmeniz gerektiğinde `document.Save(stream, SaveFormat.Docx)` kullanın. |
| **Word 97‑2003 formatı** | ActiveX kontrolünü hâlâ gömülü tutan bir `.doc` dosyası üretmek için kaydetme formatını `SaveFormat.Doc` olarak değiştirin. |

> **Pro ipucu:** Oluşturulan belgeyi hedef Word sürümünde her zaman test edin, çünkü eski sürümler varsayılan olarak ActiveX kontrollerini devre dışı bırakabilecek güvenlik ayarlarını zorlayabilir.

## Sıkça Sorulan Sorular

**Bu .NET Core ile çalışır mı?**  
Evet. Aspose.Words kütüphanesi çapraz‑platformdur ve .NET Core ve .NET 5/6+ ile tamamen uyumludur.

**Düğmeye programlı olarak bir makro atayabilir miyim?**  
API doğrudan VBA kodu gömmez. Belge oluşturulduktan sonra Word'de açın, Geliştirici sekmesini etkinleştirin ve `btnClick` öğesine başvuran bir makro kaydedin veya yazın.

**Düğme görünmezse ne olur?**  
Word'de `Developer` sekmesinin etkin olduğundan ve belgenin **Protected View** (Korunan Görünüm) içinde açılmadığından emin olun. Ayrıca dikdörtgen koordinatlarının sayfa kenar boşlukları içinde olduğuna bakın.

## Sonuç

Artık C# kullanarak bir Word dosyası içinde **ActiveX kontrolü oluşturmayı** biliyorsunuz. Öğretici **ActiveX nasıl eklenir**, **etkileşimli düğme ekleme**, **Word belgesi nasıl sıfırdan oluşturulur** konularını kapsadı ve kaydedildikten sonra kalıcı olan **kod ile düğme oluşturma** örneğini gösterdi.  

Bundan sonra ek ActiveX tiplerini keşfedebilir, düğmeyi VBA makrolarına bağlayabilir veya mantığı daha büyük bir belge‑oluşturma hizmetine yerleştirebilirsiniz. İhtiyacınız olan kullanıcı deneyimine tam uyması için farklı boyutlar, konumlar ve kontrol özellikleriyle deneyler yapın.

---

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Yeni Word Belgesi Oluştur](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Word Belgesinde VBA Projesi Oluştur](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Aspose.Words for .NET ile Word Belgesi Oluştur ve Stil Ver](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}