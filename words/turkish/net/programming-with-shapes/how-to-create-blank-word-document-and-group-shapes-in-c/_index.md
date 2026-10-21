---
category: general
date: 2026-10-07
description: C#'ta boş bir Word belgesi oluşturun ve dikdörtgen şekli eklemeyi, resim
  şekli eklemeyi ve dinamik raporlar için birden fazla şekli gruplamayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: tr
lastmod: 2026-10-07
og_description: Aspose.Words ile C#'ta boş bir Word belgesi oluşturun. Dikdörtgen
  şekil eklemeyi, resim şekli eklemeyi ve profesyonel belgeler için birden fazla şekli
  gruplamayı öğrenin.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: C#'ta boş Word belgesi oluşturun ve şekilleri gruplayın – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C#'ta boş Word belgesi oluşturma ve şekilleri gruplama
url: /tr/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# ile boş Word belgesi oluşturma ve şekilleri gruplama

Programatik olarak **create blank Word document** oluşturmanız gerekiyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. **add rectangle shape**, **insert image shape** ve **group multiple shapes** nasıl yapılacağını göreceksiniz, böylece daha sonra **add image to Word** yaptığınızda tek bir nesne gibi davranırlar.

Koddan Word dosyalarıyla çalışmak göz korkutucu gelebilir, ancak Aspose.Words süreci basitleştirir. Bu öğreticinin sonunda, gruplandırılmış bir dikdörtgen ve logo içeren temiz, boş bir Word dosyası üreten yeniden kullanılabilir bir C# snippet'ine sahip olacaksınız. Sonucu faturalar, raporlar veya herhangi bir otomatik belge iş akışına yerleştirebilirsiniz.

## Önkoşullar

* .NET 6.0 veya daha yenisi (kod .NET Framework 4.7+ ile de çalışır).  
* Geçerli bir Aspose.Words for .NET lisansı veya ücretsiz değerlendirme anahtarı.  
* Koddan referans alabileceğiniz bir klasöre yerleştirilmiş bir görüntü dosyası (ör. `logo.png`).  
* Visual Studio 2022 veya herhangi bir C# uyumlu IDE.

Ek bir NuGet paketi `Aspose.Words` dışında gerekli değildir.

## Aspose.Words ile boş Word belgesi oluşturma

İlk adım her zaman **create blank Word document** yapmaktır. Bu nesne sonraki tüm şekillere ev sahipliği yapacaktır.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` tüm `.docx` dosyasını temsil eder. Bu noktada dosya boştur, bu da *create blank Word document* gereksinimini karşılar.

## Birden fazla şekli gruplamak için bir kapsayıcı oluşturma

Şekilleri gruplamak, onları birlikte taşımanıza, döndürmenize veya yeniden boyutlandırmanıza olanak tanır. Aspose.Words bu amaçla `GroupShape` sınıfını sağlar.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

`Bounds` dikdörtgeni, grubun sayfada nerede görüneceğini belirler. Grubu ilk paragrafta konumlandırarak **create blank Word document**'in hemen bir görsel kapsayıcı içermesini sağlarsınız.

## Grubun içinde dikdörtgen şekli ekleme

Yaygın bir gereksinim, arka plan veya kenarlık olarak **add rectangle shape** yapmaktır. Aşağıdaki kod bir dikdörtgen oluşturur ve önceden tanımlanan gruba ekler.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Dikdörtgen `GroupShape` içinde bulunduğu için, daha sonra ekleyeceğiniz diğer şekillerle birlikte hareket edecektir. Bu, **group multiple shapes** işlevselliğinin özüdür.

## Gruba görüntü şekli ekleme

Sonra, **insert image shape** (logo) ekleyecek ve dikdörtgenin yanına yerleştireceksiniz. Bu, **add image to Word** iş akışını gösterir.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

`SetImage` yöntemi dosyayı okur ve doğrudan Word belgesine gömer, böylece kaynak dosya taşınsa bile görüntünün kalıcı olmasını sağlar. Bu, **insert image shape** adımını tamamlar ve **add image to Word** gereksinimini sonlandırır.

## Belgeyi kaydetme

Son olarak, dosyayı diske kaydedin. Kaydedilen dosya boş belgeyi, gruplanmış dikdörtgeni ve gömülü logoyu içerir.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

`GroupShape.docx` dosyasını Microsoft Word'de açtığınızda, yan yana konumlandırılmış açık gri bir dikdörtgen ve logoyu içeren tek bir grup göreceksiniz. Grubun herhangi bir parçasını seçmek, tüm koleksiyonu taşımanıza veya yeniden boyutlandırmanıza izin verir ve şekillerin gerçekten **group multiple shapes** olduğunu kanıtlar.

## Tam, çalıştırılabilir örnek

Aşağıda kopyalayıp yapıştırıp çalıştırabileceğiniz tam program bulunmaktadır. `YOUR_DIRECTORY` ifadesini makinenizde mevcut olan mutlak ya da göreli bir yol ile değiştirin.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Beklenen çıktı

* `YOUR_DIRECTORY` içinde `GroupShape.docx` adlı bir dosya.  
* Dosyayı Word'de açtığınızda, solda gri bir dikdörtgen ve sağda `logo.png` bulunan tek bir görsel grup gösterilir.  
* Görsel grubun herhangi bir parçasını seçmek, tüm koleksiyonu taşımanıza veya yeniden boyutlandırmanıza izin verir ve şekillerin doğru şekilde **group multiple shapes** olduğunu doğrular.

## Yaygın sorular ve uç‑durum yönetimi

| Soru | Cevap |
|---|---|
| **Aynı gruba iki'den fazla şekil ekleyebilir miyim?** | Evet. Her ek `Shape` için `group.AppendChild(yourShape)` çağırın. Grup, istediğiniz sayıda çizim nesnesi içerebilir. |
| **Görüntü dosyası eksik olursa ne olur?** | `SetImage` bir `FileNotFoundException` fırlatır. Çağrıyı try‑catch bloğuna alın ve bir yedek (ör. yer tutucu şekil) sağlayın. |
| **Şekiller için `WrapType` ayarlamam gerekiyor mu?** | Varsayılan olarak şekiller satır içi (inline) olur. Yüzen davranış gerekiyorsa, gruba eklemeden önce `picture.WrapType = WrapType.Inline;` ya da başka bir sarma modunu ayarlayın. |
| **Belge boyutu grubun sınırlarını nasıl etkiler?** | `Bounds` dikdörtgeni puan cinsinden tanımlanır (1 pt ≈ 1/72 in). Grubu farklı bir sayfa düzenine (ör. A4 vs. Letter) yerleştiriyorsanız boyutu ayarlayın. |
| **Aynı grubu başka bir belgede yeniden kullanabilir miyim?** | Evet. Grubu `GroupShape cloned = (GroupShape)group.Clone(true);` ile kopyalayın ve farklı bir `Document` içine ekleyin. |

## Profesyonel ipuçları

* **`DocumentBuilder`'ı yeniden kullanın** gruptan önce veya sonra metin eklemek için. Mevcut imleç konumunu otomatik olarak dikkate alır.  
* Dikdörtgenin etrafında görünür bir kenarlık istiyorsanız **`Shape.StrokeColor`** ayarlayın.  
* Logonun pikselleşmesini önlemek için **yüksek çözünürlüklü PNG'ler** kullanın.

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)
- [C# Kullanarak Word'de Dikdörtgen Şekli Oluşturma – Adım Adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Kullanarak Word Belgesine Satır İçi Görüntü Ekleme](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}