---
category: general
date: 2026-10-23
description: C# ile boş bir Word belgesi oluşturun ve Aspose.Words kullanarak bir
  düğme dahil ActiveX denetimlerini nasıl ekleyeceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: tr
lastmod: 2026-10-23
og_description: C# ile boş bir Word belgesi oluşturun ve Aspose.Words kullanarak bir
  düğme dahil ActiveX denetimlerini nasıl ekleyeceğinizi öğrenin.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Boş bir Word belgesi oluşturun ve C#'ta bir ActiveX düğmesi ekleyin
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Boş bir Word belgesi oluşturun ve C#'ta bir ActiveX düğmesi ekleyin
url: /tr/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş bir Word belgesi oluşturun ve C#'ta bir ActiveX düğmesi ekleyin

Programlı olarak **create blank Word document** oluşturmanız gerekiyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. Yeni bir belge oluşturan, bir ActiveX CommandButton ekleyen ve dosyayı kaydeden eksiksiz, çalıştırılabilir bir örnek göreceksiniz—tümü Aspose.Words for .NET ile.

Word dosyalarıyla çalışmak genellikle sadece düz metinden daha fazlasını gerektirir. **ActiveX button** eklemek, makro‑etkin şablonlarda veya yalnızca Windows çözümlerinde kullanılabilecek etkileşimli işlevsellik yerleştirmenizi sağlar. Bu öğreticinin sonunda herhangi bir ActiveX kontrolü ekleyebileceksiniz, ancak en yaygın senaryoya odaklanıyoruz: bir **word document activex button** form gönderir.

## Önkoşullar

* .NET 6.0 veya daha yeni bir sürüm (kod ayrıca .NET Framework 4.7+ ile de çalışır)
* Visual Studio 2022 (veya herhangi bir C# IDE'si)
* **Aspose.Words for .NET** NuGet paketi  
  ```bash
  dotnet add package Aspose.Words
  ```
* C# sözdizimiyle temel aşinalık

> **Pro tip:** Aspose.Words ticari bir kütüphanedir, ancak test için ücretsiz geçici bir lisans sunar. Değerlendirme filigranından kaçınmak için lisansı erken kurun.

## Adım 1: Aspose.Words ile boş bir Word belgesi oluşturun

İlk adım bir `Document` nesnesi örneklemektir. Bu, bellekte boş bir `.docx` dosyasını temsil eder.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` hiçbir bölüm, sayfa veya içerik olmadan başlar. Sıfırdan raporlar oluşturmak gibi **create blank word document** senaryoları için ihtiyacınız olan temiz bir sayfadır.

## Adım 2: Belgeyi düzenlemek için bir DocumentBuilder edinin

`DocumentBuilder`, metin, resim ve kontrol eklemek için kullanışlı bir API sağlar. ActiveX kontrolünü konumlandırmak için bunu kullanacağız.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

Builder otomatik olarak varsayılan bir bölüm ve ilk sayfayı ekler, böylece nesneleri hemen eklemeye başlayabilirsiniz.

## Adım 3: Belgeye ActiveX kontrolleri nasıl eklenir

Aspose.Words, OLE/ActiveX nesnelerini gömmek için `InsertForms2OleControl` yöntemini sunar. Bu yöntem kontrol tipini, genişliği ve yüksekliği (puan cinsinden) gerektirir. Aşağıda bir **CommandButton** ekliyoruz—eski Word şablonlarında gördüğünüz klasik form düğmesi.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**Neden bu çalışır:** `Forms2OleControlType.COMMANDBUTTON`, belgenin ActiveX'i destekleyen bir Windows ortamında açıldığında tıklama olaylarına yanıt verebilen bir düğme oluşturmasını Word'e söyler.

## Adım 4: Bir ActiveX kontrolü oluşturun – özelliklerini ayarlayın

Şimdi düğmeye programatik bir ad ve görünür bir başlık veriyoruz. Bu, geliştiricilerin sıkça göz ardı ettiği **create activex control** bölümüdür.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` VBA makrolarından (`ActiveDocument.InlineShapes("btnSubmit")`) başvuracağınız tanımlayıcıdır.
* `Caption` düğmenin üzerinde gösterilen etikettir.

## Adım 5: ActiveX düğmesiyle Word belgesini kaydedin

Son olarak, belgeyi diske yazın. Dosya uzantısı `.docx` olmalıdır (veya daha sonra makro eklemeyi planlıyorsanız `.docm`). Örnek, bir yer tutucu klasöre kaydediyor—kendi yolunuzla değiştirin.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Oluşan dosyayı Microsoft Word'de (yalnızca Windows) açtığınızda, VBA koduna bağlanabilen işlevsel bir **word document activex button** göreceksiniz.

## Tam çalışan örnek

Aşağıda yeni bir konsol projesine kopyalayıp‑yapıştırabileceğiniz eksiksiz program yer alıyor.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Programı çalıştırdığınızda beklenen çıktı**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Oluşturulan `ActiveXButton.docx` dosyasını Word'de açın, ve ilk sayfanın üst kısmına konumlandırılmış **Submit** etiketli bir düğme göreceksiniz.

## Kenar durumları ve yaygın tuzaklar

| Durum | Dikkat edilmesi gereken | Öneri |
|-----------|-------------------|----------------|
| macOS veya Linux'ta çalıştırma | ActiveX yalnızca Windows teknolojisidir, bu yüzden düğme bir yer tutucu olarak görünecektir. | Öğreticiyi yalnızca Windows hedefli şablonlar için kullanın. |
| Belge Word Online'da açıldı | ActiveX kontrolleri tarayıcı görünümünde desteklenmez. | Bir yedek UI sağlayın veya kullanıcıları dosyayı masaüstü istemcisinde açmaya yönlendirin. |
| Makro‑etkin bir dosyaya ihtiyaç | `.docx` dosyaları VBA kodu depolayamaz. | `.docm` olarak kaydedin (`document.Save("MyFile.docm", SaveFormat.Docm)`) ve makroyu ayrı ekleyin. |
| Kontrol boyutu uyumsuzluğu | Genişlik/yükseklik değerleri puan cinsindendir (1 pt ≈ 1/72 in). | İstediğiniz görsel boyutu elde etmek için sayısal değerleri ayarlayın. |

## Sıkça Sorulan Sorular

**Bir düğme dışındaki ActiveX kontrolleri nasıl eklenir?**  
Aynı `InsertForms2OleControl` yöntemini kullanın ancak `COMBOBOX` veya `LISTBOX` gibi farklı bir `Forms2OleControlType` enum değeri geçirin.

**Düğmenin yazı tipini veya rengini değiştirebilir miyim?**  
ActiveX düğmesinin görünümü, ana uygulama (Word) ve temel Windows teması tarafından belirlenir. Belge açıldıktan sonra VBA aracılığıyla `ForeColor` ve `BackColor` gibi özellikleri değiştirebilirsiniz.

**C#'tan doğrudan bir tıklama işleyicisi eklemenin bir yolu var mı?**  
Hayır. Tıklama olayı, düğme Word süreci içinde çalıştığı için VBA veya bir Word eklentisi tarafından işlenmelidir; .NET uygulamanız tarafından değil.

## Sonuç

Artık programlı olarak **create blank Word document** nasıl yapılacağını ve Aspose.Words for .NET kullanarak bir **ActiveX button** nasıl gömüleceğini biliyorsunuz. Kapsanan adımlar:

1. `Document` örnekleyin.
2. `DocumentBuilder`'ı dosyayla çalışmak için kullanın.
3. `InsertForms2OleControl`'ı çağırarak **how to insert activex** kontrollerini ekleyin.
4. Kontrolün özelliklerini yapılandırın (**create activex control**).
5. Dosyayı kaydedin, VBA entegrasyonu için hazır bir **word document activex button** elde edin.

Buradan diğer kontrol tiplerini eklemeyi, VBA makrolarını bağlamayı veya düğmeyi (statik bir görüntü olarak) koruyarak belgeyi PDF'ye dönüştürmeyi keşfedebilirsiniz. Farklı boyutlar, başlıklar ve adlarla deney yapın.

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren eksiksiz çalışan kod örnekleri içerir.

- [Word belgesine Aspose.Words ile ActiveX düğmesi ekleme](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [ActiveX Düğmesiyle Word Belgesi Oluşturma – C# Kılavuzu](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}