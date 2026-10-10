---
category: general
date: 2026-10-10
description: C# ile Aspose.Words kullanarak düğme metnini ayarlayın ve bir ActiveX
  düğmesi ekleyin. Düğmeyi nasıl ekleyeceğinizi, düğme kontrolü oluşturmayı ve bir
  Word belgesinde başlığı nasıl özelleştireceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: tr
lastmod: 2026-10-10
og_description: C# ile Aspose.Words kullanarak düğme metnini ayarlayın ve bir ActiveX
  düğmesi ekleyin. Bir düğme eklemek, düğme kontrolü oluşturmak ve başlığını özelleştirmek
  için bu adım adım kılavuzu izleyin.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: C#'ta düğme metnini ayarlayın ve bir ActiveX düğmesi ekleyin – tam kılavuz
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Düğme metnini ayarla ve C#'ta bir ActiveX düğmesi ekle
url: /tr/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#’ta düğme metnini ayarlama ve bir ActiveX düğmesi ekleme

Bir Word belgesindeki ActiveX düğmesinin **düğme metnini ayarlamak** istiyorsanız, bu kılavuz tam olarak nasıl yapılacağını gösterir. Eğitim sonunda **düğme ekleyebilecek**, bir **düğme kontrolü oluşturabilecek** ve sadece birkaç C# satırıyla başlığını özelleştirebileceksiniz.

ActiveX kontrolleri, Word’de etkileşimli formlar oluşturmak istediğinizde yaygın olarak kullanılır—ister bir sözleşme şablonu, bir anket ya da dahili bir araç geliştirin. Örnek, Microsoft Office yüklü olmadan Word dosyalarını manipüle etmenizi sağlayan Aspose.Words for .NET kütüphanesini kullanır.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 SDK veya daha yeni bir sürüm  
* Visual Studio 2022 (veya C# destekleyen herhangi bir IDE)  
* Aspose.Words for .NET lisansı (öğrenme amaçlı ücretsiz değerlendirme sürümü yeterlidir)  

Ayrıca `Aspose.Words` NuGet paketine bir referans eklemeniz gerekir:

```bash
dotnet add package Aspose.Words
```

## Word belgesine nasıl düğme eklenir

İlk adım, yeni bir `Document` ve bir `DocumentBuilder` oluşturmaktır. Builder, içerik eklemek için giriş noktasıdır; ActiveX kontrolleri de buna dahildir.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Neden önemli:** `Document`, tüm .docx dosyasını temsil ederken `DocumentBuilder`, `InsertParagraph` ve `InsertFormField` gibi yüksek‑seviye yöntemler sağlar. Temiz bir belgeyle başlamak, düğmenin tam istediğiniz konumda görünmesini garantiler.

## Forms2OleControl ile düğme kontrolü oluşturma

Şimdi gerçek düğme kontrolünü oluşturacağız. `Forms2OleControl`, Aspose.Words’ün tüm ActiveX nesneleri için kullandığı sınıftır ve `COMMANDBUTTON` tipi Word içinde tıklanabilir bir düğme olarak görünür.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Açıklama:**  
* `InsertForms2OleControl` kontrolü, sağladığınız tam koordinatlarda yerleştirir.  
* Boyut, puan cinsinden tanımlanır (1 puan = 1/72 inç). Bu sayıları düzenleyerek yerleşiminize uyarlayabilirsiniz.

## ActiveX kontrolünü ekleyin ve benzersiz bir ad verin

Her ActiveX nesnesinin daha sonra (örneğin VBA’da olay işleme sırasında) referans alabilmek için ayrı bir adı olmalıdır.

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**İpucu:** İsimde boşluk veya özel karakter kullanmayın; Word, adı iç modelinde bir tanımlayıcı olarak işler.

## ActiveX düğmesinin metnini (başlığını) ayarlama

İşte **set button text** anahtar kelimesinin devreye girdiği yer. `Caption` özelliği, kullanıcıların düğmede gördüğü etiketi belirler.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Kaydetmeden önce istediğiniz zaman başlığı değiştirebilirsiniz. Daha sonra UI’yı yerelleştirmeniz gerekirse, sadece `SetCaption` metodunu farklı bir dizeyle tekrar çağırmanız yeterlidir.

## Belgeyi kaydedin ve sonucu doğrulayın

Son olarak belgeyi diske yazın. Dosyayı Microsoft Word’de açtığınızda, özel başlıklı düğme görünecektir.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Beklenen çıktı:** *ActiveXButton.docx* dosyasını Word’de açtığınızda, belirtilen koordinatlarda **Click Me** etiketiyle bir düğme göreceksiniz. Düğmeye tıkladığınızda, varsayılan Word komut düğmesi davranışı tetiklenir (daha sonra VBA ile özelleştirilebilir).

![Set button text example](https://example.com/activex-button.png){alt="Set button text örneği"}

## ActiveX düğmesi ekleyin ve olayları yönetin (isteğe bağlı)

Düğmenin özel bir eylem gerçekleştirmesini istiyorsanız, `Click` olayına yanıt veren bir VBA makrosu ekleyebilirsiniz. Makro programatik olarak enjekte edilebilir, ancak bu kılavuzun kapsamı dışındadır. Önemli olan, düğmenin zaten var olması ve başlığının ayarlanmış olmasıdır—seçeceğiniz herhangi bir olay işleme için hazırdır.

## Yaygın hatalar ve nasıl önlenir

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| Düğme hizalanmamış görünüyor | Koordinatlar puan cinsindendir, piksel değil | Piksel değerlerini puana dönüştürün (`points = pixels * 72 / DPI`) |
| Kaydetmeden sonra başlık değişmiyor | `SetCaption` `Save` sonrası çağrılmış | `doc.Save` çağrısından **önce** başlığı her zaman ayarlayın |
| Kontrol eski Word sürümlerinde görünmüyor | Bazı eski Word sürümleri tam ActiveX desteği sunmaz | Hedef Word sürümünde test edin; yedek olarak `CheckBox` veya `DropDownList` kullanın |
| Çıktıda lisans uyarısı | Değerlendirme lisansı süresi dolmuş | `License license = new License(); license.SetLicense("Aspose.Words.lic");` ile geçerli bir lisans uygulayın |

## Tam, çalıştırılabilir örnek

Aşağıda kopyalayıp yapıştırarak çalıştırabileceğiniz tam program yer alıyor. Gerekli tüm `using` yönergelerini içerir ve belge oluşturma’dan kaydetmeye kadar tüm iş akışını gösterir.

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
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Programı `dotnet run` ile çalıştırın. Çalıştırdıktan sonra *ActiveXButton.docx* dosyasını açarak düğmenin başlığının **Click Me** olduğunu doğrulayın.

## Öğrendiklerinizin özeti

* Aspose.Words kullanarak bir ActiveX düğmesinin **set button text** özelliğini nasıl ayarlayacağınızı öğrendiniz.  
* **how to insert button**, **create button control** ve **add activex control** adımlarını tam olarak gördünüz.  
* Artık herhangi bir form‑tabanlı Word otomasyon projesi için uyarlayabileceğiniz yeniden kullanılabilir bir kod parçacığınız var.

## Sonraki adımlar

* `Forms2OleControlType` değerlerinden `CHECKBOX` veya `LISTBOX` gibi diğerlerini keşfederek daha zengin formlar oluşturun.  
* Düğmeyi bir VBA makrosu ile birleştirerek hesaplamalar veya veri doğrulama yapın.  
* Belge doldurulduktan sonra kullanıcı girişlerini okumak için Aspose.Words’ün `FormField` API’sını kullanın.

Boyut, konum ve başlığı tasarım gereksinimlerinize göre deneyerek özelleştirmekten çekinmeyin. Herhangi bir sorunla karşılaşırsanız, Aspose.Words belgeleri bu öğreticide kullanılan her sınıf için ayrıntılı referanslar sunar.

İyi kodlamalar!


## Bir sonraki öğrenmeniz gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım‑adım açıklamalı tam çalışan kod örnekleri içerir.

- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}