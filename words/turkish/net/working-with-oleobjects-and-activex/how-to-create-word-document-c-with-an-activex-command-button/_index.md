---
category: general
date: 2026-10-26
description: C# ile Word belgesi oluşturmayı ve programlı olarak bir ActiveX düğmesi
  eklemeyi öğrenin. Bu adım adım kılavuz, bir komut düğmesi eklemeyi, tasarım aşamasında
  gizlemeyi ve dosyayı kaydetmeyi kapsar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: tr
lastmod: 2026-10-26
og_description: C# ile Word belgesi oluşturun ve programlı olarak bir ActiveX düğmesi
  ekleyin. Yalnızca çalışma zamanında görünen bir komut düğmesi gömmek için bu kapsamlı
  öğreticiyi izleyin.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: ActiveX komut düğmesi ile C#’ta Word belgesi oluşturma – tam rehber
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: ActiveX komut düğmesiyle C# kullanarak Word belgesi nasıl oluşturulur
url: /tr/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ActiveX komut düğmesi ile Word belgesi C# oluşturma

Etkileşimli bir düğme içeren **Word belgesi C# oluşturmanız** gerekiyorsa, bu kılavuz size tam olarak nasıl yapılacağını gösterir. İlk iki cümlenin sonunda genel yaklaşımı öğrenecek ve sonraki adımlar, yazmanız gereken her kod satırını adım adım anlatacak.

ActiveX düğmesi eklemeyi, tasarım sırasında gizlemeyi ve yalnızca kullanıcı dosyayı açtığında görünür hâle getirmeyi öğreneceksiniz. Eğitim ayrıca güvenlik uyarıları ve sürüm uyumluluğu gibi yaygın tuzakları da kapsar, böylece güvenilir belgeler dağıtabilirsiniz.

## Önkoşullar

* .NET 6.0 veya daha yeni bir sürüm yüklü  
* **Aspose.Words for .NET**'in lisanslı bir kopyası (ücretsiz deneme sürümü deneyim için çalışır)  
* C# ve Visual Studio'ya (veya .NET destekleyen herhangi bir IDE'ye) temel aşinalık  

`Aspose.Words` dışındaki ek NuGet paketlerine ihtiyaç yok.

## Adım 1: Word belgesi C# oluşturma ve DocumentBuilder'ı başlatma

İlk adım, bir `Document` nesnesi ve bir `DocumentBuilder` örneği oluşturmaktır. `Document`, tüm .docx dosyasını temsil ederken, `DocumentBuilder` içerik eklemek için akıcı yöntemler sunar.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Neden önemli:** Bir `DocumentBuilder` olmadan OpenXML DOM'unu manuel olarak manipüle etmeniz gerekir, bu da hata yapmaya açık ve okunması zor bir süreçtir. Builder bu detayları soyutlar ve düzgün biçimlendirilmiş bir Word dosyası garantiler.

## Adım 2: ActiveX düğmesi ekleme – CommandButton kontrolü ekleme

Şimdi belirli bir konuma bir **CommandButton ActiveX kontrolü** ekliyoruz. Dikdörtgen, düğmenin konumunu (X, Y) ve boyutunu (genişlik, yükseklik) nokta cinsinden tanımlar.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Neden önemli:** `InsertForms2OleControl`, gerçek bir ActiveX OLE nesnesi oluşturan tek Aspose.Words yöntemidir. `Forms2OleControlType.CommandButton` enum değeri, Word'e genel bir OLE konteyneri yerine tıklanabilir bir düğme gömmesini söyler.

## Adım 3: Programatik olarak komut düğmesi ekleme – çalışma zamanına kadar gizleme

Word, eklenen her şekli varsayılan olarak görünür kabul eder. Şablonu tasarlarken düğmeyi görünmez tutmak için, builder'ın yeni oluşturduğu şeklin `Hidden` özelliğini ayarlayın.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Neden önemli:** `Hidden = true` ayarı, düğmenin tasarım görünümünü karıştırmasını önler. Belge Word'de açıldığında, çalışma zamanı ortamı kontrolü otomatik olarak gösterir ve amaçlanan kullanıcı deneyimini korur.

## Adım 4: Dosyayı kaydet – komut düğmeli Word belgesi oluşturma

Son olarak, belgeyi diske yazın. Uygulamanızın yazabileceği bir yol seçin ve modern uyumluluğu sağlamak için `.docx` uzantısını kullanın.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Neden önemli:** `.docx` olarak kaydetmek, gömülü ActiveX kontrolünün Office Open XML standardına uygun olmasını garanti eder; bu standart Word 2007 ve sonrasında desteklenir. Eski `.doc` desteğine ihtiyacınız varsa, uzantıyı değiştirip `SaveFormat.Doc` kullanın.

## Tam çalışan örnek

Her şeyi bir araya getirerek, kopyalayıp yapıştırıp çalıştırabileceğiniz tam program aşağıdadır:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Beklenen çıktı:** Programı çalıştırdıktan sonra `C:\Temp\ActiveX.docx` dosyasını Microsoft Word'de açın. Boş bir belge göreceksiniz; düğme tasarım modunda görünmez. Alan kodlarını göstermek/kapatmak için **Alt + F9** tuşlarına basın, ardından düğme alanına tıklayın—Word ActiveX kontrolünü renderlayacak ve onunla etkileşime girebileceksiniz (ör. özelliklerini görmek için çift tıklayın).

## Kenar durumları ve en iyi uygulama ipuçları

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **Kullanıcı ActiveX'i devre dışı bırakır** | Word bir güvenlik uyarısı gösterebilir veya kontrolü engelleyebilir. | Son kullanıcıları Trust Center'da “ActiveX controls” özelliğini etkinleştirmeleri için yönlendirin veya makro‑imzalı bir alternatif sağlayın. |
| **Belge Word Online'da açılır** | Word Online ActiveX'i desteklemez; düğme atlanır. | Bulut uyumluluğu gerekiyorsa geri dönüş hiperlinki veya içerik kontrolü kullanın. |
| **Farklı DPI ayarları** | Dikdörtgen boyutu yüksek DPI ekranlarda daha büyük ya da daha küçük görünebilir. | `GraphicsUnit.Point` (varsayılan) kullanın ve yaygın DPI ayarlarında (96 dpi, 120 dpi) test edin. |
| **Birden fazla düğme** | `GetChildNodes(NodeType.Shape, true)[0]` çağrısı yalnızca ilk şekli alır. | `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` üzerinden döngü kurup eklediğiniz her şeklin `Hidden` özelliğini ayarlayın. |
| **Eski .doc formatı** | Bazı ActiveX özellikleri `.doc` olarak kaydedildiğinde kaybolur. | Katı bir eski gereksiniminiz yoksa `.docx` tercih edin. |

**Pro ipucu:** Düğmeyi ekledikten sonra, Word arayüzü üzerinden `OnAction` özelliğine bir makro atayabilirsiniz. Bu, ek C# kodu yazmadan özel tıklama davranışı tanımlamanızı sağlar.

## Sıkça Sorulan Sorular

* **Bu .NET Core ile çalışır mı?**  
  Evet. Aspose.Words for .NET, .NET 5, .NET 6 ve sonrasıyla tamamen uyumludur. Aynı NuGet paketine referans verin.

* **Belge oluşturulduktan sonra düğme başlığını değiştirebilir miyim?**  
  `InsertForms2OleControl` içinde ayarlanan başlık, varsayılan tasarım‑zamanı metni olur. Kullanıcılar Word'de düzenleyebilir, ancak `Shape.OleFormat` API'si aracılığıyla OLE nesnesinin özelliklerine erişerek başlığı programatik olarak da güncelleyebilirsiniz.

* **Düğmenin farklı bir boyuta ihtiyacım olursa ne yapmalıyım?**  
  `RectangleF` değerlerini ayarlayın. İlk iki parametre X‑ ve Y‑koordinatları, son iki parametre ise nokta cinsinden genişlik ve yüksekliktir (1 pt = 1/72 inç).

## Sonuç

Artık Aspose.Words kullanarak **Word belgesi C# oluşturma** ve **programatik olarak komut düğmesi ekleme** konusunda bilgi sahibisiniz. Eğitim, belgeyi başlatmayı, bir ActiveX düğmesi eklemeyi, çalışma zamanına kadar gizlemeyi ve son dosyayı kaydetmeyi kapsadı. Bu yapı taşlarıyla oluşturduğunuz herhangi bir Word şablonuna etkileşimli kontroller yerleştirebilirsiniz.

Sonra, **how to add ActiveX button** olay işleme, **create command button word** VBA ile stil verme ve **programmatically add command button** mevcut belgelere ekleme gibi ilgili konuları keşfedin. Bu deseni onay kutuları, combo kutular veya özel OLE nesnelerine genişletmek aynı adımları izler—sadece `Forms2OleControlType` enum değerini değiştirin.

Deney yapmaya başlayın: başlığı değiştirin, konumu ayarlayın veya birden fazla kontrolü bir araya getirin. Ne kadar çok pratik yaparsanız, C#'tan zengin, etkileşimli Word belgeleri sunma konusunda o kadar akıcı olursunuz. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki eğitimler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Word belgesine programatik olarak komut düğmesi ekleme](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Aspose.Words ile Word belgesine ActiveX düğmesi ekleme](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [ActiveX Düğmeli Word Belgesi Oluşturma – C# Kılavuzu](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}