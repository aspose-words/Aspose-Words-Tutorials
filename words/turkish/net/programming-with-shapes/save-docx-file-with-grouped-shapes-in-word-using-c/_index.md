---
category: general
date: 2026-08-04
description: Docx dosyasını programlı olarak kaydederken Word'de dikdörtgen şekli
  ekleyin ve şekilleri gruplayın. Şekil boyutlarını ayarlamayı ve metin kutusu oluşturmayı
  programlı olarak öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: tr
lastmod: 2026-08-04
og_description: C# kullanarak dikdörtgen şekli ekleyip, Word'de şekilleri gruplayarak,
  şekil boyutlarını ayarlayarak ve programlı olarak metin kutusu oluşturarak docx
  dosyasını kaydedin.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Word'de Gruplandırılmış Şekiller İçeren docx Dosyasını Kaydet – C# Adım
  Adım Rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C# kullanarak Word'de gruplanmış şekillerle docx dosyasını kaydet
url: /tr/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# kullanarak Word'de gruplanmış şekillerle docx dosyasını kaydet

Birbirleriyle düzenlenmiş birkaç şekil içeren bir **save docx file**'a ihtiyacınız varsa, bu kılavuz C# ile bunu nasıl yapacağınızı gösterir. **add rectangle shape**'i nasıl ekleyeceğinizi, bir Word belgesinde birden fazla şekli nasıl gruplayacağınızı, **set shape dimensions**'i nasıl ayarlayacağınızı ve **create textbox programmatically**'i nasıl oluşturacağınızı öğreneceksiniz. Çözüm, en son Aspose.Words for .NET ile çalışır ve .NET 6 veya daha yeni sürümlerde çalışır.

Kılavuz, proje kurulumundan son `doc.Save` çağrısına kadar her adımı anlatır. Sonunda, herhangi bir console veya ASP.NET projesine yapıştırabileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız. Harici betikler veya DOCX dosyasının manuel düzenlenmesi gerekmez.

## Önkoşullar

* .NET 6 SDK (veya daha yeni) yüklü.
* **Aspose.Words for .NET** için geçerli bir lisans (ücretsiz deneme testi için çalışır).
* Visual Studio 2022, VS Code veya .NET projelerini derleyebilen herhangi bir IDE.

Kod yalnızca Aspose.Words ad alanını kullanır, bu yüzden ek NuGet paketlerine gerek yok.

## Word'de Gruplanmış Şekillerle docx Dosyasını Kaydet

Çözümün temeli, bir dikdörtgen ve bir metin kutusu içeren bir `GroupShape` oluşturmak, ardından grubu belgeye eklemek ve `doc.Save` çağrısını yapmaktır. Aşağıdaki bölümler süreci yönetilebilir parçalara ayırır.

### 1. Yeni bir belge ve bir builder oluşturun

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Bu adımın önemi* – Yeni bir `Document` nesnesi boş bir *.docx* dosyasını temsil eder. `DocumentBuilder`, `InsertNode` gibi yüksek seviyeli yöntemler sağlar; bu yöntemi grup şekli yerleştirmek için kullanacağız.

### 2. Gruba dikdörtgen şekli ekle

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Bu adımın önemi* – **add rectangle shape** işlemi, kesin boyut ve konuma sahip bir görsel öğenin nasıl tanımlanacağını gösterir. Dikdörtgen `group` içinde yer alır, bu yüzden grubu hareket ettirdiğinizde dikdörtgen otomatik olarak hareket eder.

### 3. Word belgesinde şekilleri grupla

`GroupShape` sınıfı birden fazla çizim nesnesini bir araya getirir. Gruplama, birkaç nesneyi tek bir birim olarak (örneğin, birlikte taşıma, döndürme veya kopyalama) ele almak istediğinizde faydalıdır.

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Neden grupluyoruz* – Gruplama, düzen karmaşıklığını azaltır. Her şekli sayfada ayrı ayrı konumlandırmak yerine, grubun `Left`, `Top`, `Width` ve `Height` değerlerini bir kez ayarlarsınız.

### 4. Kesin düzen için şekil boyutlarını ayarla

Hem grup hem de onun alt şekilleri açık boyutlara ihtiyaç duyar; aksi takdirde Word, tasarımınıza uymayan varsayılan boyutları uygular.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Neden boyutları ayarlıyoruz* – Kesin ölçüm, dikdörtgen ve metin kutusunun istem dışı çakışmasını önler ve son **save docx file**'ın istenen düzenle eşleşmesini sağlar.

### 5. Grup içinde programlı olarak metin kutusu oluştur

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Bu adımın önemi* – **create textbox programmatically** bölümü, bir şekil içinde zengin metin nasıl gömülür gösterir. `Paragraph` ve `Run` kullanmak, daha sonra biçimlendirme üzerinde tam kontrol sağlar.

### 6. Grup şekli ekle ve **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Bu son adımın önemi* – `InsertNode` çağrısı, gruplanmış şekilleri builder'ın imlecinin bulunduğu yere tam olarak yerleştirir. `doc.Save` yöntemi **save docx file** işlemini gerçekleştirir ve tam özellikli bir Word belgesini diske yazar.

> **Sonuç:** Microsoft Word'de *GroupShape.docx* dosyasını açtığınızda, solda bir dikdörtgen ve sağda bir metin kutusu görüntülenir; her ikisi de tek bir grup içinde birlikte kilitlenmiştir. Grubu bir bütün olarak taşıyabilir, yeniden boyutlandırabilir veya ek biçimlendirme uygulayabilirsiniz.

## Tam, çalıştırılabilir örnek

Aşağıdaki kodu yeni bir console projesine (`dotnet new console`) kopyalayın ve `dotnet run` komutunu çalıştırın. Program, projenin çıktı klasöründe `GroupShape.docx` dosyasını oluşturur.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Beklenen çıktı

* Çıktı dizininde **GroupShape.docx** adlı bir dosya görünür.
* Dosyayı açtığınızda, solda bir dikdörtgen şekil ve sağda “Grouped text” içeren bir metin kutusu gösterilir; ikisi de birlikte kilitlenmiştir.
* Herhangi bir şekli seçmek, tüm grubu hareket ettirir ve **group shapes word** işlevselliğinin amaçlandığı gibi çalıştığını doğrular.

## Yaygın varyasyonlar ve kenar durumları

| Durum | Öneri |
|-----------|----------------|
| İki şekilden fazla gerekliyse | `builder.InsertNode` çağrısından önce `group`'a ek `Shape` nesneleri ekleyin. |
| Grubun belirli bir sayfada görünmesini istiyorsanız | `builder.MoveToDocumentEnd()` veya `builder.MoveToPage(pageNumber)` ile builder'ın imlecini taşıyın. |
| Farklı birimlere (ör. santimetre) ihtiyaç duyuyorsanız | `ConvertUtil.InchToPoint(1.0)` kullanarak inçleri Word'ün beklediği puan birimine dönüştürün. |
| Metin kutusunun metni kaydırmasını istiyorsanız | Metin kutusunu oluşturduktan sonra `textBox.TextBoxWrap = TextBoxWrapType.Square` ayarlayın. |
| Eski .NET Framework sürümleriyle çalışıyorsanız | Aynı API .NET Framework 4.7+ ile çalışır, ancak doğru Aspose.Words sürümüne referans verdiğinizden emin olun. |

**Pro ipucu:** Grup içindeki tüm alt şekilleri ekledikten *sonra* grubun `Width` ve `Height` değerlerini ayarlayın. Bu, grup içeriği tamamen kapsar ve belgenin Word'de açıldığında kırpılmasını önler.

## Sonuç

Artık Aspose.Words for .NET kullanarak **save docx file** yaparken **add rectangle shape**, **group shapes word**, **set shape dimensions** ve **create textbox programmatically** işlemlerini nasıl gerçekleştireceğinizi biliyorsunuz. Tam örnek, grafikler, resimler gibi daha karmaşık düzenlere uyarlayabileceğiniz temiz, tekrarlanabilir bir desen gösterir,

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki eğitimler, bu kılavuzda gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [C# kullanarak Word'de dikdörtgen şekil oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Şekil Gölge Eğitimi – C# ile Word Şekline Gölge Ekle](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}