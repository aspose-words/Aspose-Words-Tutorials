---
category: general
date: 2026-08-17
description: Aspose.Words kullanarak Word'e OleControlType.CommandButton örneği ekleyin.
  Form denetimlerini bir Word belgesine programlı olarak nasıl ekleyeceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: tr
lastmod: 2026-08-17
og_description: OleControlType.CommandButton örneğini Aspose.Words ile Word’e ekleyin.
  Form denetimlerini bir Word belgesine eklemek için bu kılavuzu izleyin.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Word'de OleControlType.CommandButton örneği ekle
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Word'de OleControlType.CommandButton örneği ekle
url: /tr/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de OleControlType.CommandButton örneği ekleme

Word dosyasına **insert OleControlType.CommandButton example** eklemeniz gerekiyorsa, bu kılavuz size nasıl yapılacağını gösterir. Aspose.Words kullanarak **how to add form controls to a Word document** öğrenecek ve tam, çalıştırılabilir bir C# programı elde edeceksiniz.

ActiveX düğmeleri gibi form kontrolleri, sözleşmeler, anketler veya dahili araçlar için faydalı olan etkileşimli Word şablonları oluşturmanızı sağlar. Aşağıdaki adımlar, proje kurulumundan kaydedilen `.docx` dosyasında düğmenin doğru şekilde göründüğünün doğrulanmasına kadar her şeyi kapsar.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

- .NET 6.0 SDK veya daha yeni bir sürüm yüklü  
- Visual Studio 2022 (veya herhangi bir C# IDE)  
- Aspose.Words for .NET lisansı veya ücretsiz geçici bir lisans  
- C# ve Word dosyası kavramlarına temel aşinalık  

> **Pro ipucu:** Ücretsiz deneme sürümünü kullanıyorsanız, lisans dosyasını çalıştırılabilir dosyayla aynı klasöre koyun ve `Main` başlangıcında yükleyin.

## Adım 1: Yeni bir konsol projesi oluşturun ve Aspose.Words ekleyin

Bir terminal açın ve şu komutu çalıştırın:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Bu, temiz bir proje oluşturur ve en yeni Aspose.Words paketini çeker; bu paket, **insert OleControlType.CommandButton example** için gerekli `Document`, `DocumentBuilder` ve `InsertForms2OleControl` API'lerini sağlar.

## Adım 2: Tam programı yazın

`Program.cs` dosyasını aşağıdaki kodla oluşturun veya değiştirin. Gerekli tüm `using` yönergeleri, lisans yükleme ve orijinal kod parçacığında gösterilen dört adımlı iş akışı burada yer alır.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Her satırın önemi

* **License loading** – değerlendirme kısıtlamalarına takılmadığınızdan emin olur.  
* **`Document doc = new Document();`** – tüm Word içeriği için bir kapsayıcı oluşturur; bu, **insert OleControlType.CommandButton example**'ın temelidir.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – metin, resim ve kontrol eklemek için akıcı bir API sağlar.  
* **`InsertForms2OleControl`** – **how to add form controls to a Word document** işlemini gerçekleştiren temel yöntemdir. `OleControlType.CommandButton` enum değeri Aspose.Words'e bir ActiveX düğmesi oluşturmasını söyler.  
* **`new Rectangle(100, 100, 80, 30)`** – düğmeyi sol ve üst kenarlardan 100 pt uzaklıkta konumlandırır, genişliği 80 pt ve yüksekliği 30 pt'dir. Düzeninize uyacak şekilde bu sayıları ayarlayın.  
* **`doc.Save`** – .docx dosyasını diske yazar; dosya artık gömülü düğmeyi içerir.

## Adım 3: Programı derleyin ve çalıştırın

Proje klasöründen şu komutu yürütün:

```bash
dotnet run
```

Aşağıdaki konsol mesajını görmelisiniz:

```
Document saved to ActiveXButton.docx
```

`ActiveXButton.docx` dosyasını Microsoft Word'de açın. Sayfanın ortalarına doğru konumlandırılmış **ClickMe** adlı bir düğme göreceksiniz. Düğmeye tıkladığınızda varsayılan ActiveX davranışı tetiklenir (genellikle bir makro eklemediğiniz sürece hiçbir işlem yapmaz).

![insert olecontroltype.commandbutton örneği](/images/activex-button.png "Word belgesine eklenmiş ActiveX CommandButton")

*Resim alt metni:* insert olecontroltype.commandbutton example – bir Word belgesinde gösterilen ActiveX CommandButton.

## Adım 4: Düğmeyi özelleştirme (isteğe bağlı)

Temel **insert OleControlType.CommandButton example** varsayılan bir düğme oluşturur. Başlığını, yazı tipini değiştirebilir veya altındaki OLE nesnesini düzenleyerek bir makro ekleyebilirsiniz. Aşağıda eklemeden sonra düğmenin başlığını değiştirmek için kısa bir yöntem yer alıyor:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Not:** OLE özelliklerinin doğrudan manipülasyonu, altındaki COM arayüzünün anlaşılmasını gerektirir. Çoğu senaryoda, varsayılan başlık yeterlidir.

## Adım 5: Yaygın tuzaklar ve nasıl önlenir

| Sorun | Neden oluşur | Çözüm |
|-------|--------------|------|
| Düğme Word'de görünmüyor | Belge `.docx` olarak kaydedildi ancak OLE kontrollerini kaldıran bir görüntüleyicide (ör. Google Docs) açıldı. | Dosyayı Microsoft Word veya düzenleme yetkisi olan Word Online'da açın. |
| Çalışma zamanı hatası `ArgumentOutOfRangeException` | `Rectangle` koordinatları sayfa kenar boşluklarının dışındadır. | Sayfa boyutu içinde değerler kullanın (ör. A4 için 0‑500). |
| Lisans istisnası | Deneme lisansı 30 gün sonra sona erer. | Geçerli bir lisans dosyası yükleyin veya Aspose'tan uzatılmış bir deneme isteyin. |

## Adım 6: Bu örneğin daha büyük otomasyon projelerine nasıl uyduğunu

Ölçekli olarak **how to add form controls to Word document** eklemeniz gerektiğinde—örneğin yüzlerce sözleşme şablonu üretirken—ekleme mantığını yeniden kullanılabilir bir metoda sarın:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Ardından `AddCommandButton` metodunu veri satırlarını işleyen döngüler içinde çağırabilirsiniz; böylece her oluşturulan belge benzersiz bir düğme adı (ör. `Approve_001`, `Approve_002`) içerir.

## Sonuç

Artık Aspose.Words for .NET kullanarak **how to add form controls to a Word document** gösteren eksiksiz bir **insert OleControlType.CommandButton example**'a sahipsiniz. Kılavuz, proje kurulumunu, tam kaynak kodunu, özelleştirme ipuçlarını ve yaygın sorun giderme adımlarını kapsadı.

Bundan sonra şunları keşfedebilirsiniz:

- **CheckBox** veya **ComboBox** gibi diğer kontrol türlerini ekleme (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Düğmeyi daha zengin etkileşim için bir VBA makrosuna bağlama.  
- Form alanlarını koruyarak aynı belgeden PDF'ler oluşturma.

Farklı boyutlar, konumlar ve kontrol adlarıyla deneyler yaparak kendi kullanım senaryonuza en uygun hâle getirin. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Word Belgesine Combo Box Form Alanı Ekle](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Word Belgesine Check Box Form Alanı Ekle](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Word Belgesine Metin Girişi Form Alanı Ekle](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}