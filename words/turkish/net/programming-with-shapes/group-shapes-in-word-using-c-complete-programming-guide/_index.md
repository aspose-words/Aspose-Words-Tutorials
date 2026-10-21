---
category: general
date: 2026-10-13
description: C# ile Word’de şekilleri gruplayın – Aspose.Words kullanarak şekilleri
  nasıl gruplayacağınızı ve gruba şekil eklemeyi birkaç kolay adımda öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: tr
lastmod: 2026-10-13
og_description: C# ve Aspose.Words kullanarak Word’de şekilleri gruplayın. Bu kılavuzu
  izleyerek şekilleri nasıl gruplayacağınızı ve bir Word belgesinde gruba şekil eklemeyi
  öğrenin.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: C# ile Word’de şekilleri gruplama – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C# kullanarak Word’de şekilleri gruplayın – tam programlama rehberi
url: /tr/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Şekilleri C# ile Gruplama – tam programlama rehberi

Word'de **şekilleri programlı olarak gruplamanız** gerekiyorsa, bu rehber tam olarak nasıl yapılacağını gösterir. İlk iki cümlenin sonunda gerekli kodu, her adımın nedenini ve **şekilleri gruba ekleme** yöntemini sürpriz olmadan öğreneceksiniz.

`.docx` dosyasını yüklemekten güncellenmiş belgeyi kaydetmeye kadar her şeyi ele alacağız. Eğitim, temel C# bilginiz ve Aspose.Words for .NET kütüphanesine referansınız olduğunu varsayar. Harici bir dokümantasyona ihtiyaç yok—sadece kopyalayıp yapıştırın ve çalıştırın.

## Önkoşullar

- .NET 6.0 veya üzeri (kod .NET Framework 4.7+ ile de çalışır)
- Aspose.Words for .NET NuGet paketi (`Install-Package Aspose.Words`)
- En az iki şekil (ör. resimler, AutoShapes) içeren bir Word belgesi (`input.docx`)

> **Pro ipucu:** Test yapıyorsanız, Word arayüzünden iki dikdörtgen içeren basit bir Word dosyası oluşturun. `input.docx` olarak, kontrol ettiğiniz bir klasöre kaydedin.

## Word'de Şekilleri Gruplama – adım adım rehber

Aşağıda süreci beş mantıksal adıma bölüyoruz. Her adım, tam C# kodunu, satırın *neden* gerektiğine dair bir açıklamayı ve yaygın tuzaklara kısa bir notu içerir.

### Adım 1: Word belgesini yükleme

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Neden:** `Document`, herhangi bir Word manipülasyonu için giriş noktasıdır. Tam dosya yolunu sağlamak belgeyi belleğe yükler, böylece düğüm ağacını sorgulayabilir ve değiştirebiliriz.

**Tüzak:** Çalışma dizini farklı olduğunda göreli bir yol vermek başarısız olabilir. Mutlak bir yol kullanın veya `AppContext.BaseDirectory` ile `Path.Combine` kullanın.

### Adım 2: Gruplamak istediğiniz şekilleri alın

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Neden:** `GetChild`, belge ağacında dolaşır ve istenen tipin *n‑inci* düğümünü döndürür. `isDeep` değerini `true` olarak ayarlamak, yalnızca geçerli bölümü değil, tüm belgeyi arar.

**Köşe durumu:** Belge iki şekilden az içeriyorsa, `firstShape` veya `secondShape` `null` olur ve dönüştürmeye çalıştığımızda bir istisna fırlatılır. Buna karşı önlem alın:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### Adım 3: Yeni bir `GroupShape` kapsayıcı oluşturma

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Neden:** `GroupShape`, birden fazla `Shape` nesnesini tutabilen bir üst düğüm görevi görür. `Shape` sınıfından miras alır, bu yüzden normal bir şeklin izin verildiği her yere (ör. bir paragrafın içine) eklenebilir.

### Adım 4: Tek tek şekilleri gruba ekleme

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Neden:** `AppendChild`, şekilleri orijinal konumlarından yeni gruba taşır. Bu çağrıdan sonra orijinal şekiller bağımsız düğüm olarak var olmaz; `groupShape`'in bir parçası haline gelir.

**İpucu:** Gruplama, alt şekillerin göreli konumlarını otomatik olarak ayarlar. Belirli bir düzen gerekiyorsa, alt öğeleri eklemeden önce `GroupShape.Bounds` özelliğini ayarlayın.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### Adım 5: Grup şekli belge gövdesine ekleme

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Neden:** `GroupShape`, görüntülenebilmesi için bir paragrafın (veya tablo hücresinin) içine yerleştirilmelidir. İlk paragrafın sonuna ekleyerek mevcut düzeni bozmadan görünür bir konum garantileriz.

### Adım 6: Değiştirilen belgeyi kaydetme

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Neden:** `Save`, bellek içindeki değişiklikleri bir `.docx` dosyasına yazar. Aşırı yüklemeyi değiştirerek bir akısa ya da PDF'e de kaydedebilirsiniz.

**Sonuç doğrulama:** `output.docx` dosyasını Microsoft Word'de açın. İki orijinal şeklin şimdi tek bir grup nesnesi olarak birleştiğini görmelisiniz. Grubu seçtiğinizde standart Word grup tutamaçları gösterilir.

## Şekilleri programlı olarak gruplama – daha derin içgörüler

- **Düğüm sahipliği:** `AppendChild` çağrısı yaptığınızda, şeklin `ParentNode` referansı otomatik olarak değişir. Bu, belgeyi bozabilecek “sahipsiz” düğümlerin oluşmasını önler.
- **Biçimlendirmeyi koruma:** Gruplama, şekil biçimlendirmesini (dolgu rengi, çizgi stili vb.) **kaybetmez**. Tüm alt şekiller orijinal özelliklerini korur.
- **İç içe gruplar:** `GroupShape`, başka `GroupShape` nesneleri içerebilir, çok seviyeli hiyerarşiler sağlar. İç grubu diğer bir şekil gibi ele alın.

## Şekilleri gruba ekleyin ve daha sonra yönetin

İlk grup oluşturulduktan sonra daha fazla şekil eklemeniz gerekiyorsa, aynı `GroupShape` örneğini yeniden kullanabilirsiniz:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

Daha sonra grubu çözmeniz gerektiğinde, `groupShape.GetChildNodes(NodeType.Shape, true)` üzerinde döngü yapın ve her bir alt öğeyi istediğiniz yere yeniden ekleyin.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Neden önemli:** Bazı iş akışları, birden fazla nesneyi hizalamak gibi geçici gruplamayı ve ardından bireysel düzenlemeler için grubu çözmeyi gerektirir.

## Tam Çalıştırılabilir Örnek

Aşağıda, olduğu gibi derleyip çalıştırabileceğiniz bağımsız bir program bulunmaktadır. `YOUR_DIRECTORY` ifadesini makinenizdeki gerçek bir klasör yolu ile değiştirin.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Beklenen çıktı:** `output.docx` dosyasını açtığınızda, iki orijinal şekil tek bir grup nesnesi olarak görünür. Grubu seçmek, tanıdık Word grup tutamaçlarını gösterir ve tüm seti birlikte taşımanıza, yeniden boyutlandırmanıza veya döndürmenize olanak tanır.

## Sonuç

Artık C# ve Aspose.Words kullanarak **Word'de şekilleri gruplamayı** biliyorsunuz ve **şekilleri gruba ekleme** ve daha sonra bunları manipüle etme ya da grubu çözme adımlarını gördünüz. Bu teknik, rapor düzenlerini otomatikleştirmek, birleşik diyagramlar oluşturmak veya birden çok nesnenin kesin konumlandırılmasını gerektiren Word şablonları hazırlamak için idealdir.

Sonraki adımda, farklı bağlantı türleriyle **şekilleri nasıl gruplayacağınızı**, gruplara **gelişmiş biçimlendirme** uygulamayı veya gruplu sonucu PDF olarak dışa aktarmayı keşfedin. Karmaşık grafikler oluşturmak için iç içe gruplarla deneyler yapın.

Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki eğitimler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Word Belgelerinde Şekil Ekleme – Aspose.Words for .NET Kullanarak](/words/english/net/working-with-shapes/insert-shape/)
- [Word Belgesinde Grup Şekli Oluşturma – Aspose.Words for .NET Kullanarak](/words/english/net/working-with-shapes/add-group-shape/)
- [Word Şekillerine Gölge Efekti Ekleme – Tam C# Rehberi](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}