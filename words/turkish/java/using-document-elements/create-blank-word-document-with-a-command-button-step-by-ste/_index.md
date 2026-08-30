---
category: general
date: 2026-08-04
description: Aspose.Words kullanarak boş bir Word belgesi oluşturun ve komut düğmesi
  ekleyin. C#'ta düğme boyutunu ayarlamayı ve tıklanabilir bir düğme eklemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: tr
lastmod: 2026-08-04
og_description: Aspose.Words ile boş bir Word belgesi oluşturun ve bir komut düğmesi
  ekleyin. Bu kılavuz, düğme boyutunu ayarlamayı, tıklanabilir bir düğme eklemeyi
  ve dosyayı kaydetmeyi gösterir.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Boş Word belgesi oluşturun ve bir komut düğmesi ekleyin – tam C# öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Komut düğmesiyle boş Word belgesi oluşturma – adım adım rehber
url: /tr/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Komut düğmesiyle boş Word belgesi oluşturma – adım adım rehber

Eğer etkileşimli bir düğme içeren **create blank word document** oluşturmanız gerekiyorsa, bu öğretici Aspose.Words for .NET ile bunu tam olarak nasıl yapacağınızı gösterir. **insert command button** öğrenecek, görünümünü ayarlayacak ve tıklanabilir hâle getireceksiniz—hepsi birkaç C# satırıyla.

Kılavuz, proje kurulumundan son dosyanın kaydedilmesine kadar her şeyi kapsar, böylece tam çözümü kendi uygulamanıza kopyala‑yapıştırabilirsiniz. Yol boyunca **add clickable button**, **set button size**, ve **create command button**'ı programlı olarak nasıl ekleyeceğinizi de açıklayacağız.

## Önkoşullar

* .NET 6.0 SDK veya daha yeni bir sürüm yüklü.
* Visual Studio 2022 (veya .NET'i destekleyen herhangi bir IDE).
* Aspose.Words for .NET NuGet paketi (`Aspose.Words` sürüm 23.12 veya daha yeni).
* C# ve nesne‑yönelimli programlamaya temel aşinalık.

Ek Office interop derlemeleri gerekmez çünkü Aspose.Words, Microsoft Word'den tamamen bağımsız çalışır.

## Adım 1: .NET projesini kurun

Word otomasyon kodunu barındıracak bir konsol uygulaması oluşturun.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Bu komut, çalıştırmaya hazır bir `Program.cs` dosyasıyla yeni bir `WordButtonDemo` klasörü oluşturur ve Aspose.Words kütüphanesini ekler.

## Adım 2: Boş Word belgesi oluşturun

İlk işlem **create blank word document**'dir. Aspose.Words, kutudan çıkar çıkmaz boş bir Word dosyasını temsil eden bir `Document` sınıfı sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Boş bir belge oluşturmak, paragraflar, tablolar veya bu durumda bir OLE command button ekleyebileceğiniz temiz bir tuval sağlar.

## Adım 3: DocumentBuilder'ı başlatın

`DocumentBuilder`, belgeye içerik eklemenizi sağlayan yardımcıdır. Bunu az önce oluşturduğunuz belgeye bağlamanız gerekir.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder, mevcut imleç konumunu korur, böylece sonraki eklemeler tam istediğiniz yere yapılır.

## Adım 4: command button ekleyin

Şimdi belgeye **insert command button** (bir OLE `Forms2OleControl`) ekliyoruz. `InsertForms2OleControl` yöntemi üç argüman gerektirir:

1. OLE kontrolünün ProgID'si – standart bir düğme için `"CommandButton"`.
2. **set button size** ve konumu tanımlayan bir `Rectangle`.
3. Düğmede görünen başlık.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Belge Word'de açıldığında, düğme yerel bir form kontrolü gibi davranır—tıklayabilirsiniz ve Word ilişkili makroyu (varsa) çalıştırır. Bu, **add clickable button** gereksinimini karşılar.

### Neden Forms2OleControl Kullanılır?

`Forms2OleControl`, bir OLE nesnesini doğrudan DOCX dosyasına gömer, kontrolün özelliklerini Word Interop derlemesine ihtiyaç duymadan korur. Word sürümleri arasında çalışan **create command button** oluşturmanın en güvenilir yoludur.

## Adım 5: Düğmeyi özelleştirin (isteğe bağlı)

Daha kesin bir **set button size** ayarlamak veya yazı tipi ya da arka plan rengi gibi ek özellikleri değiştirmek isteyebilirsiniz. Aspose.Words, temel OLE nesnesine erişim sağlayarak daha fazla ince ayar yapmanıza izin verir.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Farklı bir boyuta ihtiyacınız varsa, Step 4'teki `Rectangle` değerlerini basitçe ayarlayın. Koordinatlar puan cinsinden ölçülür (1 pt = 1/72 inç), bu yüzden `120` yaklaşık 1.67 inç genişliğe karşılık gelir.

## Adım 6: Belgeyi kaydedin

Son olarak belgeyi diske yazın. Oluşan dosya, tam işlevsel bir command button içeren bir **blank word document** içerir.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

`CommandButtonDemo.docx` dosyasını Microsoft Word'de açtığınızda, “Click Me” etiketiyle bir düğme göreceksiniz. Düğmeye tıkladığınızda, özel bir makro eklemediğiniz sürece varsayılan makro iletişim kutusu görüntülenir.

## Tam kaynak kodu

Aşağıda `Program.cs` içine kopyalayabileceğiniz tam program yer alıyor. Yukarıda açıklanan tüm adımları içerir ve değişiklik yapmadan derlenir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Beklenen sonuç

Programı çalıştırmak `CommandButtonDemo.docx` dosyasını üretir. Dosyayı Word'de açtığınızda şunlar görülür:

* **Click Me** etiketiyle bir düğme içeren tek bir sayfa.
* Düğme **set button size** (120 × 30 puan) değerine uyar.
* Düğmeye tıklamak, Word'ün varsayılan command‑button davranışını tetikler ve **add clickable button** işleminin başarılı olduğunu doğrular.

## Yaygın sorular ve uç durumlar

| Soru | Cevap |
|----------|--------|
| **Bu .doc dosyalarıyla çalışır mı?** | Evet. `doc.Save("file.doc")` içinde dosya uzantısını değiştirin. OLE kontrolü de eski ikili formatta depolanır. |
| **Birden fazla düğmeye ihtiyacım olursa ne olur?** | `InsertForms2OleControl` metodunu tekrarlayarak çağırın, her yeni düğme için `Rectangle` değerlerini ayarlayarak çakışmayı önleyin. |
| **Düğmeye bir makro ekleyebilir miyim?** | Düğme kendisi makro kodu içermez. Belgeye manuel olarak veya `Document` nesnesinin `Modules` koleksiyonu aracılığıyla bir VBA makrosu eklemeniz gerekir. |
| **Düğme PDF dışa aktarmada görünür mü?** | Aspose.Words kullanarak DOCX'i PDF'ye dışa aktardığınızda, düğme etkileşimli bir kontrol yerine statik bir görüntü olarak işlenir. |
| **Hangi Word sürümleri destekleniyor?** | OLE command button, standart Forms2.0 spesifikasyonunu izlediği için Word 2007 ve sonraki sürümlerde çalışır. |

## Sonuç

Artık Aspose.Words for .NET kullanarak **create blank word document**, **insert command button**, **add clickable button** ve **set button size** nasıl yapılacağını biliyorsunuz. Tam örnek, **create command button** iş akışını baştan sona göstererek daha gelişmiş Word otomasyon görevleri için sağlam bir temel sunar.

## Sonraki adımlar

* `InsertForms2OleControl` içindeki ProgID'yi değiştirerek diğer OLE kontrollerini (ör. `CheckBox`, `ListBox`) keşfedin.
* Düğmeyi bir VBA makrosu ile birleştirerek kullanıcı tıkladığında özel eylemler gerçekleştirin.
* Düğmeyi eklemeden önce tablolar, görseller veya dipnotlar gibi ek içerikler eklemek için Aspose.Words’ `DocumentBuilder`'ı kullanın.
* **set button size** değerleriyle deney yaparak belgenizin düzen gereksinimlerine uyum sağlayın.

Kodlamaktan keyif alın ve etkileşimli kontrollerle daha zengin Word belgeleri oluşturmaktan zevk alın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}