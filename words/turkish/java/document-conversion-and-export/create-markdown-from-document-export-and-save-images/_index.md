---
category: general
date: 2026-02-18
description: Belgeden markdown oluşturun, belgeyi markdown olarak dışa aktarmak ve
  resimleri alt klasöre kaydetmek için kolay adımlar. C#'ta belgeyi markdown olarak
  kaydetmeyi öğrenin.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: tr
og_description: C# ile bir belgeden markdown oluşturun ve belgeyi markdown’a dışa
  aktarırken resimleri bir alt klasöre kaydetmeyi öğrenin. Adım adım rehberi izleyin.
og_title: Belgeden markdown oluştur – Görselleri dışa aktar ve kaydet
tags:
- C#
- Aspose.Words
- Markdown export
title: Belgeden markdown oluştur – Görselleri dışa aktar ve kaydet
url: /tr/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Belgeden markdown oluştur – Dışa aktar ve resimleri kaydet

Her zaman **belgeden markdown oluştur**mak isteyip gömülü resimleri düzenli tutmanın yolunu bilemediniz mi? Tek başınıza değilsiniz. Birçok projede raporlar, kılavuzlar veya blog taslaklarını programlı olarak oluştururuz ve çıktıda resim dosyalarının dağınık bir şekilde bulunması en son istediğimiz şeydir.  

Bu öğreticide, **belgeyi markdown olarak dışa aktar**, her resmi ayrı bir *md‑resources* alt klasörüne kaydet ve sonunda **Aspose.Words for .NET API** kullanarak belgeyi markdown olarak kaydetmek için tamamen çalıştırılabilir bir çözümü adım adım inceleyeceğiz. Sonunda, herhangi bir C# kod tabanına ekleyebileceğiniz tek bir metoda ve kenar durumlarıyla başa çıkmak için birkaç ipucu elde edeceksiniz.

> **Hızlı bakış:**  
> • `MarkdownSaveOptions` ayarlayın  
> • Görselleri bir alt klasöre yönlendiren bir `IResourceSavingCallback` sağlayın  
> • Yapılandırılmış seçeneklerle `Document.Save` çağırın  

Neden bir callback kullandığımızı ve sonradan işleme tercih etmediğimizi merak ediyorsanız, okumaya devam edin – gerekçeler adım adım açıklanacak.

---

## Gereksinimler

- .NET 6.0 veya üzeri (kod .NET Framework 4.7+ ile de çalışır)  
- Aspose.Words for .NET (NuGet paketi `Aspose.Words`)  
- Bir kaynak `Document` nesnesi (ör. .docx, .pdf, .rtf, vb.)  

Ek bir kütüphane gerekmez; callback API'si Aspose.Words içinde yer alır.

---

## Adım 1: Belgeden markdown oluştur – kaydetme seçeneklerini yapılandırma

İlk yaptığımız şey `MarkdownSaveOptions` nesnesini örneklemek. Bu nesne, dönüşümün nasıl davranacağını belirler; hangi Markdown çeşidinin kullanılacağı, görsellerin Base64 olarak gömülüp gömülmeyeceği ve oluşturulan dosyaların nereye yerleştirileceği gibi ayarları içerir.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **Neden önemli:**  
> `MarkdownSaveOptions` açıkça oluşturulmazsa, kütüphane varsayılan ayarları kullanır ve görselleri doğrudan Markdown dosyasına Base64 dizgeleri olarak gömer. Bu dosyayı şişirir ve temiz bir *images* klasörü oluşturma amacını bozar.

---

## Adım 2: Belgeyi markdown olarak dışa aktar ve kaynak işleme tanımla

Şimdi kaydedicinin **her görseli nereye** koyacağını belirtiyoruz. `IResourceSavingCallback` arayüzü, dışa aktarma sırasında bulunan her kaynak (görsel, SVG, vb.) için çalışan bir kanca sunar. Callback içinde şunları yapıyoruz:

1. Hedef klasörün var olduğundan emin olun (`md-resources/`).  
2. `OutputFileName` değerini klasör ve orijinal kaynak adıyla ayarlayın.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **Sık sorulan soru:** *Görselleri kaydetmek yerine gömmek istersem ne yapmalıyım?*  
> Callback'i atlayın veya `args.OutputFileName = null;` ayarlayın – kaydedici görseli otomatik olarak Base64 dizgesi olarak gömer.

> **Kenar durumu:** Bazı eski belgelerde aynı görsel adı birden fazla kez bulunur. Yukarıdaki callback önceki dosyanın üzerine yazar. Bunu önlemek için bir GUID ekleyebilirsiniz:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## Adım 3: Belgeyi markdown olarak kaydet ve kaydedilen görselleri doğrula

Seçenekler tamamen yapılandırıldıktan sonra, tek satırlık son çağrı Markdown dosyasını ve ilişkili görselleri diske yazar.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

Her şey yolunda giderse şunları görürsünüz:

- `MyReport.md` – kaynak belgenizin Markdown temsili.  
- `md-resources/` – .md dosyasının yanında, çıkarılan tüm görselleri içeren klasör (ör. `image001.png`, `image002.jpg`).  

**Örnek Markdown kesiti** (Aspose.Words tarafından otomatik oluşturulur):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **Pro ipucu:** Oluşturulan `.md` dosyasını VS Code’da veya herhangi bir Markdown önizleyicisinde açın; görseller klasör yapısıyla aynı göreli yollara sahip olduğu için anında görüntülenir.

---

## Tam, çalıştırılabilir örnek

Aşağıda yeni bir .NET projesine yapıştırıp çalıştırabileceğiniz, kendi içinde bir konsol programı bulunuyor. Basit bir Word belgesi oluşturur, bir görsel ekler ve ardından **belgeden markdown oluştur**urken görseli bir alt klasöre kaydeder.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**Çalıştırdıktan sonra** şu çıktıyı görmelisiniz:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

`ExportedDoc.md` dosyasını açın – görsel referansı `md-resources/sample-image.png`’e işaret eder ve resim herhangi bir Markdown görüntüleyicide doğru şekilde gösterilir.

---

## Sık sorulan varyasyonlar

| Senaryo | Kodu nasıl uyarlarsınız |
|----------|----------------------|
| **Görsel dışa aktarımını atla** (Base64 göm) | `ResourceSavingCallback`’i tamamen kaldırın veya callback içinde `args.OutputFileName = null;` ayarlayın. |
| **Görsel formatını değiştir** (ör. tüm PNG) | Callback içinde `args.ResourceFileName`’i değiştirin ve isteğe bağlı olarak akışı dönüştürerek yazın. |
| **Özel klasör adı** | `"md-resources/"` ifadesini istediğiniz göreli veya mutlak yol ile değiştirin. |
| **Toplu olarak birden çok belge** | `Document` nesnelerinin bir koleksiyonu üzerinde döngü kurun, aynı `MarkdownSaveOptions` örneğini yeniden kullanın (klasörün temizlendiğinden veya her çalıştırma için benzersiz bir ad alacağından emin olun). |

---

## Sonuç

**Belgeden markdown oluştur**, **belgeyi markdown olarak dışa aktar** ve **görselleri alt klasöre kaydet** işlemlerini temiz, callback‑tabanlı bir yaklaşımla nasıl yapacağınızı gösterdik. Önemli çıkarımlar:

- `MarkdownSaveOptions` ile dışa aktarma üzerinde ince ayar yapın.  
- `IResourceSavingCallback` uygulayarak görselleri ayrı bir klasöre yönlendirin, Markdown dosyanız düzenli kalsın.  
- Aynı desen diğer kaynak türleri (SVG, ses) için de çalışır – sadece `args.ResourceType`’ı inceleyin.  

Sonraki adım olarak **markdown olarak belge kaydet** işlemini özel başlık stilleriyle özelleştirebilir veya bu rutini bir ASP.NET Web API’ye entegre ederek `.md` dosyası ve kaynaklarını içeren bir ZIP döndürebilirsiniz. Her ne olursa olsun, yapı taşları artık sizin aracınızda.

Sorularınız mı var, yoksa kapsamadığımız bir köşe durumu mu var? Aşağıya yorum bırakın, kodlamanız keyifli olsun!

---

![belgeden markdown oluştur örnek](placeholder.png "belgeden markdown oluştur örnek")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}