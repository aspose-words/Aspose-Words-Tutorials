---
category: general
date: 2026-08-04
description: C# kullanarak programlı olarak Word belgesi oluşturun. Aspose.Words ile
  sadece birkaç adımda programlı olarak komut düğmesi eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: tr
lastmod: 2026-08-04
og_description: Aspose.Words ile programlı olarak Word belgesi oluşturun. Bu kılavuz,
  programlı olarak komut düğmesi eklemeyi, yapılandırmayı ve dosyayı kaydetmeyi gösterir.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Programatik olarak Word belgesi oluşturma – tam C# öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Word belgesini programlı olarak oluşturma – adım adım rehber
url: /tr/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programatik Olarak Word Belgesi Oluşturma – Tam C# Eğitimi

Programatik olarak **word belgesi oluşturmanız** gerekiyorsa, bu rehber Aspose.Words for .NET ile bunu tam olarak nasıl yapacağınızı gösterir. Sadece birkaç C# satırıyla boş bir `.docx` dosyası oluşturabilir, **programatik olarak komut düğmesi** denetimlerini ekleyebilir, özelliklerini ayarlayabilir ve sonucu kaydedebilirsiniz.  

Aşağıdaki adımlar, proje kurulumundan uç durumların ele alınmasına kadar her şeyi kapsar, böylece kodu kendi uygulamanıza kopyalayıp değişiklik yapmadan çalıştırabilirsiniz.

## Ne elde edeceksiniz

* Yeni bir Word belgesini tamamen bellek içinde başlatın.  
* **Programatik olarak komut düğmesi** OLE denetimlerini istediğiniz konum ve boyutta ekleyin.  
* Düğmenin başlığını, iç adını ve diğer OLE özelliklerini yapılandırın.  
* Oluşturulan belgeyi disk üzerine veya daha sonraki işleme için bir akışa kaydedin.

### Önkoşullar

* .NET 6.0 veya daha yeni (kod .NET Framework 4.6+ ile de çalışır).  
* Geçerli bir Aspose.Words for .NET lisansı (veya ücretsiz deneme).  
* C# ve Visual Studio (veya tercih ettiğiniz herhangi bir IDE) hakkında temel bilgi.  

> **Pro tip:** Lisans olmadan örneği çalıştırırsanız, Aspose.Words ilk sayfaya küçük bir değerlendirme filigranı ekleyecektir.

## Adım 1: Projeyi kurun ve gerekli ad alanlarını içe aktarın

Yeni bir Console App oluşturun (veya mevcut bir servise entegre edin) ve Aspose.Words NuGet paketini ekleyin:

```bash
dotnet add package Aspose.Words
```

Ardından `.cs` dosyanızın en üstüne gerekli ad alanlarını ekleyin:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Bu içe aktarmalar, konumlandırma için kullanılan `Document`, `DocumentBuilder`, `Forms2OleControl` ve `RectangleF` yapısına erişim sağlar.

## Adım 2: Yeni bir Word belgesi başlatın

**Programatik olarak word belgesi oluşturma** iş akışındaki ilk işlem, bir `Document` nesnesi örneklemektir. Bu nesne, açıkça kaydedene kadar yalnızca bellek içinde bulunur.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder`, bir sonraki öğenin nereye yerleştirileceğini izleyen bir imleç gibi davranır. Onu kullanmak kodu özlü tutar ve Word'e doğrudan yazıyormuş gibi bir deneyim sağlar.

## Adım 3: Bir komut düğmesi OLE denetimi ekleyin

Aspose.Words, komut düğmeleri, onay kutuları veya açılır kutular gibi OLE nesnelerini gömmek için `InsertForms2OleControl` metodunu sağlar. Metod üç argüman gerektirir:

1. `ControlType` enum değeri (burada `CommandButton`).  
2. Denetimin X‑Y konumunu ve genişlik‑yüksekliğini tanımlayan bir `RectangleF` (puan cinsinden ölçülür, 72 pt = 1 inch).  
3. İsteğe bağlı olarak ek OLE özellikleri (temel düğme için gerekli değildir).  

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Neden çalışır:** `InsertForms2OleControl`, belgede bir OLE konteyneri oluşturur ve bir `Forms2OleControl` sarmalayıcı döndürür. Bu sarmalayıcı, düşük seviyeli COM etkileşimiyle uğraşmadan temel OLE nesnesini (gerçek düğmeyi) manipüle etmenizi sağlar.

## Adım 4: Düğmenin başlığını ve iç adını yapılandırın

Ekleme sonrası, genellikle düğmeye kullanıcıya görünen bir etiket ve makronuzun veya eklentinizin daha sonra başvurabileceği bir iç tanımlayıcı vermek istersiniz.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption`, Word UI'da düğme üzerinde gösterilen metindir.  
* `Name`, VBA veya dış otomasyon betikleri tarafından kullanılan programatik tanımlayıcıdır.

### İsteğe Bağlı: Düğmeye bir makro atayın

Düğmeye tıklandığında bir VBA makrosu çalıştırmayı planlıyorsanız, makro adını ekleyebilirsiniz:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Uç durum:** Hedef belge, makro olmadan bir makinede açılacaksa, Word bir güvenlik uyarısı gösterir. Makrolarınızı her zaman imzalayın veya kullanıcıları gerekli ayarlar hakkında bilgilendirin.

## Adım 5: Belgeyi kaydedin

Dosyayı diske, bir `MemoryStream`'e veya bir web API'sindeki yanıt nesnesine doğrudan yazabilirsiniz. Konsol demosu için en basit yaklaşım, yerel bir klasöre kaydetmektir:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Oluşan `.docx`, Microsoft Word'de “Click Me” (Tıkla Beni) yazan işlevsel bir komut düğmesiyle açılır. Düğmeye tıkladığınızda, atanmış makro (varsa) tetiklenir veya sadece varsayılan bir mesaj gösterir.

## Tam Çalışan Örnek

Aşağıdaki programı `Program.cs` dosyasına kopyalayın ve çalıştırın. Bu, **programatik olarak word belgesi oluşturma** sürecinin tamamını, hata yönetimi dahil, gösterir.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Beklenen sonuç:** Word'de `CommandButton.docx` dosyasını açtığınızda “Click Me” etiketiyle bir düğme görünür. Düğmenin üzerine geldiğinizde özellikler panelinde `cmdClickMe` adı gösterilir.

## Sık Sorulan Sorular ve Sorun Giderme

| Soru | Cevap |
|----------|--------|
| *Düğmeyi mevcut bir belgeye ekleyebilir miyim?* | Evet. Dosyayı `new Document("Existing.docx")` ile yükleyin, ardından aynı `InsertForms2OleControl` çağrısını kullanın. |
| *`RectangleF` hangi birimleri kullanır?* | Puan (1 inch = 72 pt). Değerleri düğmeyi tam olarak konumlandırmak için ayarlayın. |
| *Düğme Mac için Word'de çalışır mı?* | OLE denetimleri yalnızca Windows Word'de desteklenir. Mac'te düğme statik bir görüntü olarak görünür. |
| *Üretim kullanımı için lisansa ihtiyacım var mı?* | Ticari bir lisans, değerlendirme filigranlarını kaldırır ve tam işlevselliği açar. |
| *Eklemeden sonra düğmenin boyutunu nasıl değiştiririm?* | `commandButton.Width` ve `commandButton.Height` değerlerini değiştirin veya yeni bir `RectangleF` ile yeniden ekleyin. |

## Çözümü Genişletmek

Artık **programatik olarak komut düğmesi** denetimlerini nasıl ekleyeceğinizi bildiğinize göre, aşağıdaki ilgili konuları keşfedebilirsiniz:

* **Diğer form denetimlerini ekleyin** – `ControlType.CheckBox`, `ControlType.OptionButton` vb. kullanın (ikincil anahtar kelime *Aspose.Words InsertForms2OleControl*).  
* **Belgeyi dinamik veri ile doldurun** – veritabanından verileri tablolara veya posta birleştirme alanlarına birleştirin.  
* **PDF olarak dışa aktar** – düğmeyi ekledikten sonra `doc.Save("output.pdf", SaveFormat.Pdf)` çağırarak bir PDF sürümü oluşturun (*C# Word automation* ile ilgili).  

## Sonuç

Artık Aspose.Words for .NET kullanarak **programatik olarak word belgesi oluşturma** ve **programatik olarak komut düğmesi ekleme** için eksiksiz, üretim‑hazır bir deseniniz var. Eğitim, proje kurulumunu, belge başlatmayı, OLE düğme eklemeyi, özellik yapılandırmasını ve dosyanın kaydedilmesini kapsadı. Kodu diğer form denetimlerini eklemek, makrolar eklemek veya mantığı web servislerine ya da arka plan görevlerine entegre etmek için özgürce uyarlayabilirsiniz.

Kodlamaktan keyif alın ve Word belgelerini otomatikleştirmenin tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki eğitimler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words ile Word Belgesi Oluşturma – Adım Adım Kılavuz](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Aspose.Words Kullanarak Tablo ile Word Belgesi Oluşturma](/words/english/net/add-content-using-document-builder/build-table/)
- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}