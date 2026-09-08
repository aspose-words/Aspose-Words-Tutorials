---
category: general
date: 2026-09-08
description: C# kullanarak boş bir Word belgesi oluşturmayı, dikdörtgen şekli eklemeyi
  ve birden fazla şekli gruplamayı öğrenin. Bu adım adım kılavuzu izleyin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: tr
lastmod: 2026-09-08
og_description: Boş bir Word belgesi oluşturun, dikdörtgen şekli ekleyin ve C#'ta
  birden fazla şekli gruplayın. Bu öğretici, sizi sürecin tamamı boyunca yönlendirecek.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: C# ile gruplanmış şekiller içeren boş Word belgesi oluştur
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Gruplandırılmış şekillerle boş Word belgesi nasıl oluşturulur
url: /tr/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş Word belgesi oluşturma ve şekilleri gruplama

Eğer **boş bir Word belgesi** oluşturup içine özel grafikler eklemek istiyorsanız, bu kılavuz tam olarak nasıl yapılacağını gösterir. **Dikdörtgen şekil ekleme**, **birden fazla şekli gruplama** ve **gruba şekil ekleme** işlemlerini Aspose.Words for .NET kullanarak öğreneceksiniz.

Boş bir belge, temiz bir tuval sağlar ve şekilleri gruplamak, onları tek bir birim olarak taşımanıza, yeniden boyutlandırmanıza veya döndürmenize olanak tanır. Bu öğretici, belgeyi başlatmaktan son dosyayı kaydetmeye kadar tüm adımları kapsar—kodunuzu kendi projenize kopyalayıp anında sonuçları görebilirsiniz.

## Gereksinimler

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 veya daha yeni bir sürüm (kod .NET Framework 4.6+ ile de çalışır)
* Geçerli bir Aspose.Words for .NET lisansı (ücretsiz deneme sürümü test için yeterlidir)
* Visual Studio 2022 veya Visual Studio Code gibi bir IDE
* C# sözdizimi hakkında temel bilgi

`Aspose.Words` dışındaki ek NuGet paketlerine ihtiyaç yoktur.

## Boş Word belgesi nasıl oluşturulur

İlk adım bir `Document` nesnesi oluşturmaktır. Bu nesne, bir `DocumentBuilder` ile düzenleyebileceğiniz boş bir `.docx` dosyasını temsil eder.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` yapıcı metodu bellekte **boş bir Word belgesi** oluşturur. `DocumentBuilder` ise metin, resim ve çizim nesneleri eklemek için akıcı bir API sunar.

## Belgeye dikdörtgen şekil ekleme

Sonraki adımda bir dikdörtgen şekil ekleyin. Bu dikdörtgen, daha sonra oluşturacağımız grubun ilk çocuğu olacaktır.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

`InsertShape` metodunu `ShapeType.Rectangle` ile çağırmak, **dikdörtgen şekli** geçerli imleç konumuna ekler. Genişlik ve yükseklik puan cinsindendir (1 pt ≈ 1/72 in).

## Birden fazla şekli birlikte gruplama

`GroupShape`, bir konteyner gibi davranır. Grup içindeki tüm alt şekiller birlikte hareket eder ve dönüşür. Önce grubu oluşturun, ardından az önce eklediğimiz dikdörtgeni ekleyin.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

`InsertGroupShape` metodu, builder’ın imlecinde boş bir grup yerleştirir. Dikdörtgeni ekleyerek **birden fazla şekli gruplamış** oluruz—dikdörtgen, grup içindeki düğüm koleksiyonunun bir parçası haline gelir.

## Gruba şekil ekleme ve dosyayı kaydetme

Şimdi ikinci bir şekil—bir elips—ekleyerek birden fazla nesnenin aynı konteyneri paylaştığını gösterelim. Ardından belgeyi kaydedin.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

`InsertShape` çağrısı, döndürülen `Shape` nesnesini `GroupShape`’e eklediğinizde **şekilleri gruba ekler**. `Document`’i kaydetmek, Microsoft Word, LibreOffice veya uyumlu herhangi bir görüntüleyicide açabileceğiniz bir `.docx` dosyası oluşturur.

### Beklenen sonuç

*GroupShapeDemo.docx* dosyasını açtığınızda, içinde açık mavi bir dikdörtgen ve pembe bir elips bulunan gruplu bir nesneyle boş bir sayfa görürsünüz. Grubu seçtiğinizde iki şekil de birlikte hareket eder; bu da **birden fazla şekli gruplama** işleminin başarılı olduğunu gösterir.

## Neden GroupShape kullanmalısınız?

* **Atomik dönüşümler** – Grubu ölçeklendirmek, döndürmek veya taşımak, tüm alt öğeleri aynı anda etkiler.
* **Mantıksal organizasyon** – İlgili grafiklerin bir arada tutulması, belge yapısının bakımını kolaylaştırır.
* **Performans** – Tek bir konteyneri işlemek, birçok bağımsız şekli yönetmekten genellikle daha hızlıdır.

Daha sonra tek bir çocuğu değiştirmek isterseniz, `group.ChildNodes` üzerinden indeks ya da `Name` özelliğiyle erişebilirsiniz.

## Yaygın varyasyonlar ve uç durumlar

| Senaryo                                   | Kodu nasıl uyarlamalısınız                                                    |
|-------------------------------------------|--------------------------------------------------------------------------------|
| **Farklı şekil türleri**                  | `ShapeType.Rectangle` veya `ShapeType.Ellipse` yerine başka bir `ShapeType` kullanın |
| **Şekil içinde metin ekleme**             | Şekli ekledikten sonra `Shape.TextPath.Text = "Hello"` ifadesini ekleyin    |
| **Dönme açısı ayarlama**                  | `group.Rotation = 45;` (derece)                                                |
| **DOCX yerine PDF kaydetme**              | `doc.Save("GroupShapeDemo.pdf");`                                              |
| **Gruba kenarlık uygulama**               | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`            |

## Profesyonel ipuçları

* **Şekillere isim verin** – `rectangle.Name = "MyRect";` ileride onları bulmayı kolaylaştırır.
* **Göreli konumlandırma kullanın** – Grubun sayfa kenar boşluklarına sabitlenmesini istiyorsanız `group.RelativeHorizontalPosition` değerini `RelativeHorizontalPosition.Page` olarak ayarlayın.
* **Kaynakları serbest bırakın** – Daha büyük uygulamalarda `Document` nesnesini bir `using` bloğu içinde tutarak yönetilmeyen belleği zamanında temizleyin.

## Hızlı kopyala‑yapıştır için tam kaynak kodu

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Kodu yeni bir konsol projesine yapıştırın, `Aspose.Words` NuGet paketini geri yükleyin ve çalıştırın. Çıktı dosyası projenin `bin/Debug/net6.0` (veya eşdeğeri) klasöründe oluşur.

## Sonraki adımlar

Artık **boş Word belgesi oluşturma**, **dikdörtgen şekil ekleme** ve **birden fazla şekli gruplama** konularını biliyorsunuz; şimdi şunları keşfedebilirsiniz:

* Gruba **metin kutuları** ekleyerek etiketli diyagramlar oluşturma.
* `doc.Save("image.png", SaveFormat.Png)` ile gruplu grafiği bir görüntüye dışa aktarma.
* Zengin biçimlendirilmiş raporlar için grupları tablolarla birleştirme.

Farklı şekil özellikleri, grup hiyerarşileri ve dışa aktarım formatlarıyla deneyler yaparak Aspose.Words’un çizim yeteneklerinden tam anlamıyla yararlanın.

--- 

*Unutmayın*: Şekilleri gruplamak, Word belgelerinizi düzenli tutmanın ve kodunuzu sürdürülebilir kılmanın güçlü bir yoludur. İyi kodlamalar!

## Bir sonraki öğrenmeniz gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakın ilişkili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım‑adım açıklamalar içerir.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}