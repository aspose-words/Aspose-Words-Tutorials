---
category: general
date: 2025-12-19
description: LaTeX denklemleriyle markdown rehberi – Aspose.Words kullanarak C#'ta
  docx dosyasını markdown'a dönüştürmeyi, denklemleri LaTeX'e aktarmayı ve görüntüleri
  benzersiz adlarla klasöre kaydetmeyi öğrenin.
draft: false
keywords:
- markdown with latex equations
- convert docx to markdown
- save images to folder
- export equations to latex
- generate unique image names
language: tr
og_description: LaTeX denklemleriyle markdown öğreticisi, docx'i markdown'a dönüştürmeyi,
  denklemleri LaTeX'e aktarmayı ve kaydedilen görüntüler için benzersiz dosya adları
  oluşturmayı gösterir.
og_title: LaTeX denklemleriyle markdown – Tam C# Dönüşüm Kılavuzu
tags:
- Aspose.Words
- C#
- Markdown
- LaTeX
title: 'LaTeX denklemleriyle markdown: DOCX''i Markdown''a dönüştür ve görselleri
  dışa aktar'
url: /tr/net/programming-with-markdownsaveoptions/markdown-with-latex-equations-convert-docx-to-markdown-and-e/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown with latex equations: DOCX'i Markdown'a Dönüştürme ve Görselleri Dışa Aktarma

Hiç **markdown with latex equations**'e ihtiyaç duydunuz ama bir Word dosyasından nasıl çıkaracağınızı bilemediniz mi? Yalnız değilsiniz—birçok geliştirici, belgeleri Office'ten statik site jeneratörlerine taşırken bu soruna takılıyor.

Bu öğreticide, **docx'i markdown'a dönüştüren**, **denklemleri latex'e dışa aktaran** ve **görselleri klasöre kaydeden** **benzersiz görsel adları oluşturma** mantığıyla tam bir uçtan uca çözüm üzerinden geçeceğiz; tümü Aspose.Words for .NET kullanılarak.

Sonunda, temiz Markdown dosyaları, LaTeX‑hazır matematik ve düzenli bir görsel dizini üreten, çalıştırmaya hazır bir C# programına sahip olacaksınız—manuel kopyala‑yapıştırma gerekmez.

## Gereksinimler

- .NET 6 (veya herhangi bir yeni .NET çalışma zamanı)  
- Aspose.Words for .NET 23.10 veya daha yeni sürüm (NuGet paketi `Aspose.Words`)  
- Normal metin, Office Math nesneleri ve birkaç resim içeren örnek bir `input.docx`  
- Sevdiğiniz bir IDE (Visual Studio, Rider veya VS Code)  

Hepsi bu. Ekstra kütüphane yok, karmaşık komut satırı araçları yok—sadece saf C#.

## Adım 1: Belgeyi Güvenli Şekilde Yükleme (Recovery Mode)

Birçok kişi tarafından düzenlenmiş olabilecek dosyalarla çalışırken, bozulma gerçek bir risktir. Aspose.Words, *RecoveryMode*'u etkinleştirmenize olanak tanır; böylece yükleyici, bir istisna fırlatmak yerine bozuk bölümleri onarmaya çalışır.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // Load the document with recovery mode – this handles possible corruption.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);
```

**Neden önemli:**  
Kaynak dosya rastgele XML düğümleri veya bozuk bir görüntü akışı içeriyorsa, recovery mode hâlâ kullanılabilir bir `Document` nesnesi sağlar. Bu adımı atlamak, özellikle her yüklemeyi kontrol edemediğiniz CI boru hatlarında, ciddi bir çöküşe neden olabilir.

> **Pro tip:** Toplu işlemler yaparken, yüklemeyi bir `try/catch` bloğuna sarın ve daha sonraki inceleme için olası `DocumentCorruptedException`'ları kaydedin.

## Adım 2: DOCX'i LaTeX Denklemleriyle Markdown'a Dönüştürme

Şimdi öğreticinin kalbine geliyoruz: **markdown with latex equations** istiyoruz. Aspose.Words'ün `MarkdownSaveOptions` ayarı, `OfficeMathExportMode.LaTeX`'i belirlemenize izin verir; bu da her Office Math nesnesini `$…$` veya `$$…$$` içinde sarılmış bir LaTeX dizesine dönüştürür.

```csharp
        // Export Office Math equations to LaTeX while saving as Markdown.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);
```

The resulting `output_math.md` will look something like:

```markdown
Here is an inline equation $E = mc^2$ inside a sentence.

And a displayed equation:

$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$
```

**Neden bunu isteyebilirsiniz:**  
Çoğu statik site jeneratörü (Hugo, Jekyll, MkDocs) MathJax veya KaTeX eklentisini etkinleştirdiğinizde LaTeX ayırıcılarını zaten anlar. Doğrudan LaTeX'e dışa aktararak, aksi takdirde regex hileleri gerektirecek bir son‑işlem adımından kaçınırsınız.

### Kenar Durumları

- **Karmaşık denklemler:** Çok derin iç içe yapılar hâlâ doğru render eder, ancak `OutOfMemoryException` alırsanız `MathRenderer` bellek sınırını artırmanız gerekebilir.  
- **Karışık içerik:** Bir paragraf normal metin ve bir denklemi karıştırıyorsa, Aspose.Words otomatik olarak bunları ayırır ve çevreleyen markdown'ı korur.

## Adım 3: Görselleri Benzersiz İsimlerle Klasöre Kaydetme

Word belgeniz resimler içeriyorsa, muhtemelen markdown'ın referans verebileceği ayrı görüntü dosyaları olarak istiyorsunuzdur. `MarkdownSaveOptions` üzerindeki `ResourceSavingCallback`, her bir görüntünün nasıl kaydedileceği üzerinde tam kontrol sağlar.

```csharp
        // Customize image handling during Markdown export.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                // Generate a unique file name for each image.
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);

                // Ensure the Images folder exists.
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);

                // Save the image to the file system.
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);
```

**Markdown şu anda şöyle görünüyor:**  

```markdown
![Image description](Images/img_3f9c2a1e-7b5d-4c8f-9d6e-2b5c7a9e1f0a.png)
```

**Neden benzersiz isimler oluşturmalısınız?**  
Aynı resim birden fazla kez görünürse, orijinal ismi kullanmak üzerine yazmalara neden olur. GUID‑tabanlı isimler her dosyanın farklı olmasını garantiler; bu, dönüşümü paralel işler halinde çalıştırdığınızda özellikle kullanışlıdır.

### İpuçları ve Dikkat Edilmesi Gerekenler

- **Performans:** Her görüntü için GUID oluşturmak ihmal edilebilir bir ek yük ekler, ancak binlerce görüntü işliyorsanız deterministik bir hash'e (ör. görüntü baytlarının SHA‑256'sı) geçebilirsiniz.  
- **Dosya formatı:** `resource.Save`, görüntüyü orijinal formatında yazar. Tüm PNG'lere ihtiyacınız varsa, `resource.Save(imageFile);` satırını `resource.Save(imageFile, ImageSaveOptions.CreateSaveOptions(SaveFormat.Png));` ile değiştirin.

## Adım 4: Satır İçi Şekillerle PDF Dışa Aktarma (İsteğe Bağlı)

Bazen aynı belgenin bir PDF sürümüne hâlâ ihtiyaç duyabilirsiniz, belki yasal inceleme için. `ExportFloatingShapesAsInlineTag` ayarı, kayan nesneleri (ör. metin kutuları) PDF içinde satır içi etiketler olarak tutar ve düzen bütünlüğünü korur.

```csharp
        // Save the document as PDF, exporting floating shapes as inline tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

PDF çıktısı iş akışınızın bir parçası değilse bu adımı atlayabilirsiniz—atladığınızda hiçbir şey kırılmaz.

## Tam Çalışan Örnek (Tüm Adımlar Birleştirildi)

Aşağıda, bir konsol uygulamasına kopyalayıp‑yapıştırabileceğiniz tam program yer alıyor. `YOUR_DIRECTORY` ifadesini gerçek bir mutlak ya da göreli yol ile değiştirin.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // 1️⃣ Load with recovery mode.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ Export markdown with LaTeX equations.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);

        // 3️⃣ Save images to a folder, using unique GUID names.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);

        // 4️⃣ (Optional) Export PDF with inline shape tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

Bu programı çalıştırdığınızda üç dosya üretilir:

| Dosya | Amaç |
|------|------|
| `output_math.md` | LaTeX‑hazır denklemler içeren Markdown |
| `output_images.md` | Benzersiz‑adlandırılmış PNG'lere işaret eden görsel bağlantıları içeren Markdown |
| `output_shapes.pdf` | Kayan şekilleri satır içi etiketler olarak koruyan PDF sürümü (isteğe bağlı) |

## Sonuç

Artık **markdown with latex equations** boru hattına sahipsiniz; bu, **docx'i markdown'a dönüştürür**, **denklemleri latex'e dışa aktarır** ve **her resim için benzersiz görsel adları oluştururken** **görselleri klasöre kaydeder**. Yaklaşım tamamen bağımsızdır, herhangi bir modern .NET projesinde çalışır ve yalnızca Aspose.Words NuGet paketini gerektirir.

Sırada ne var? Oluşturulan markdown'ı Hugo gibi bir statik site jeneratörüne bağlayın, MathJax'ı etkinleştirin ve belgelerinizin kapalı‑office formatından güzel, web‑hazır bir siteye dönüşümünü izleyin. Tabloya mı ihtiyacınız var? Aspose.Words ayrıca `MarkdownSaveOptions.ExportTableAsHtml`'i destekler, böylece karmaşık düzenleri bozulmadan tutabilirsiniz.

If

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}