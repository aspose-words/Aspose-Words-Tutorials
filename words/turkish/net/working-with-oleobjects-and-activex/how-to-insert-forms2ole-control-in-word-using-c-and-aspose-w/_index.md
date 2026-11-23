---
category: general
date: 2026-11-22
description: C# ile Word'e Forms2Ole kontrolü eklemeyi öğrenin. Bu adım adım rehber,
  DocumentBuilder, komut düğmesi yerleştirme ve .docx dosyasını kaydetmeyi kapsar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: tr
lastmod: 2026-11-22
og_description: C# ile Word’e Forms2Ole kontrolü ekleyin. Aspose.Words ve DocumentBuilder
  kullanarak bir komut düğmesi eklemek için bu kılavuzu izleyin.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: C# ile Word'e Forms2Ole kontrolü ekleme – tam rehber
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C# ve Aspose.Words kullanarak Word'e Forms2Ole kontrolü nasıl eklenir
url: /tr/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Forms2Ole kontrolünü C# ve Aspose.Words kullanarak nasıl eklenir

Word'de **Forms2Ole kontrolü eklemeniz** gerekiyorsa, bu öğretici C# ile bunu tam olarak nasıl yapacağınızı gösterir. Doldurulabilir bir şablon oluşturuyor ya da form oluşturmayı otomatikleştiriyor olun, aşağıdaki çözüm bir komut düğmesini programlı olarak eklemenizi sağlar.

Boş bir belge oluşturmayı, kontrolü yerleştirmek için `DocumentBuilder` kullanmayı ve sonucu `.docx` olarak kaydetmeyi öğreneceksiniz. Kılavuz ayrıca koordinat sistemleri ve eski Word sürümleriyle uyumluluk gibi yaygın tuzakları da kapsar.

## Önkoşullar

* .NET 6.0 veya daha yeni (kod .NET Framework 4.6+ ile de çalışır)
* Aspose.Words for .NET (NuGet paketi `Aspose.Words`)
* C# ve Word nesne modeli hakkında temel bir anlayış
* Visual Studio veya VS Code gibi bir IDE

## Adım 1: Projeyi kurun ve ad alanlarını içe aktarın

Yeni bir console uygulaması oluşturun ve Aspose.Words paketini ekleyin:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

`Program.cs` dosyasında gerekli ad alanlarını içe aktarın:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Pro tip:** `Forms2OleControl` API'si için tam destek alabilmek adına en son Aspose.Words sürümünü kullanın.

## Adım 2: Boş bir belge oluşturun ve DocumentBuilder'ı başlatın

`Document` sınıfı Word dosyasını temsil eder, `DocumentBuilder` ise içerik eklemek için yöntemler sağlar.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` bir imleç gibi çalışır; bu satırdan sonra belge içinde istediğiniz yere öğeler yerleştirmeye başlayabilirsiniz.

## Adım 3: Düğmenin konumunu ve boyutunu tanımlayın

Word koordinatları puan (point) cinsinden ölçer (1 pt ≈ 1/72 in). `System.Drawing`'den `Rectangle` yapısı kontrolün sınırlarını tanımlar.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` kontrolü geçerli sayfanın sol‑üst köşesine yerleştirir.
* Düğmeyi başka bir yere taşımak için `x` ve `y` değerlerini ayarlayın (örnek: `new Rectangle(150, 200, 100, 30)`).

## Adım 4: Forms2Ole komut düğmesini ekleyin

Şimdi kontrolü eklemek için `InsertForms2OleControl` yöntemini kullanın. Bu metod kontrol tipini, bir adı ve yukarıda tanımlanan sınırları (bounds) ister.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

Dönen `Forms2OleControl` nesnesi, `Enabled`, `Visible` gibi özellikleri değiştirmenize veya daha sonra bir makro adı eklemenize olanak tanır.

### Neden Forms2Ole Kullanılır?

* **Eski uyumluluk** – Forms2Ole kontrolleri Word 97‑2003 (`.doc`) ve daha yeni `.docx` dosyalarında çalışır.
* **Makro desteği** – VBA makrolarını tetikleyebilirler, bu da onları etkileşimli şablonlar için ideal kılar.
* **Kesin konumlandırma** – İçerik kontrollerinin aksine, tam koordinatları kontrol edersiniz.

## Adım 5: Belgeyi kaydedin

Son olarak, dosyayı diske yazın. Yazma izniniz olan bir klasör seçin.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`output.docx` dosyasını Microsoft Word'de açın. İlk sayfanın sol‑üst köşesinde **ClickMe** etiketiyle bir düğme göreceksiniz. Word'de üzerine tıkladığınızda bir makro atayana kadar hiçbir şey yapmaz, ancak kontrol tamamen işlevseldir.

## Yaygın kenar durumlarını ele alma

| Situation | How to address it |
|-----------|-------------------|
| **Düğme sayfa dışına çıkıyor** | `Rectangle` koordinatlarının sayfa kenar boşlukları içinde olduğundan emin olun. Güvenli sınırları hesaplamak için `builder.PageSetup.PageWidth` ve `PageHeight` kullanın. |
| **Kontrol eski Word sürümlerinde görünmüyor** | Belgeyi `.doc` olarak kaydedin (`doc.Save("output.doc", SaveFormat.Doc)`) böylece Forms2Ole uyumluluğu Word 97‑2003 ile garanti edilir. |
| **Başlığı değiştirmek gerekiyor** | Eklemeden sonra `commandButton.Caption = "Submit";` şeklinde ayarlayın. |
| **Makro atama** | `commandButton.MacroName = "MyMacro"` olarak ayarlayın; makro belgenin VBA projesinde mevcut olmalıdır. |
| **Birden fazla düğme** | Farklı `Rectangle` değerleri ve benzersiz adlarla Adım 4'ü tekrarlayın. |

## Tam, çalıştırılabilir örnek

Her şeyi bir araya getirerek, kopyalayıp yapıştırıp çalıştırabileceğiniz bağımsız bir program aşağıdadır:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Beklenen çıktı:** Programı çalıştırdıktan sonra, `output.docx` Word'de açılır ve ilk sayfanın sol‑üst köşesinde *Click Me!* etiketiyle tıklanabilir bir düğme bulunur.

## Sonuç

Artık C# ve Aspose.Words kullanarak Word'e **Forms2Ole kontrolü eklemeyi** biliyorsunuz. Süreç bir `Document` oluşturmayı, bir `Rectangle` konumlandırmayı ve `DocumentBuilder` aracılığıyla `InsertForms2OleControl` çağırmayı içerir. Tam kod örneği ve kenar durumu rehberi sayesinde, komut düğmelerini herhangi bir otomatik Word iş akışına entegre edebilirsiniz.

### Sonraki adımlar

* `CheckBox` veya `OptionButton` gibi diğer `ControlType` değerlerini keşfedin.
* Forms2Ole kontrollerini VBA makrolarıyla birleştirerek etkileşimli formlar oluşturun.
* Belirli paragraflara veya tablolara düğme yerleştirmek için `DocumentBuilder.MoveTo` kullanın.
* Gelişmiş özellik ayarları için Aspose.Words’ün **Forms2Ole** dokümantasyonunu inceleyin.

Kodlamaktan keyif alın ve C# ve Aspose.Words ile daha zengin Word belgeleri oluşturmaktan zevk alın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [C# kullanarak bir Word belgesine OLE komut düğmesi ekleme](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [Aspose.Words ile Word'e ActiveX kontrolü ekleme – adım adım rehber](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Aspose.Words ile Word Belgesine Komut Düğmesi Ekleme – Tam Kılavuz](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}