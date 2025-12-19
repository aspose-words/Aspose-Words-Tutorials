---
category: general
date: 2025-12-18
description: Word belgesini Markdown’a dönüştürürken resimleri nasıl yeniden adlandıracağınızı
  öğrenin; ayrıca docx’i Markdown’a dönüştürmek ve docx’i Markdown’a verimli bir şekilde
  dışa aktarmak için adım adım talimatlar.
draft: false
keywords:
- how to rename images
- convert word to markdown
- export docx to markdown
- how to convert docx
- how to extract images
language: tr
og_description: Word'ten Markdown'a dönüşüm sırasında görüntüleri yeniden adlandırmayı
  keşfedin; docx'i markdown'a dışa aktarma ve görüntüleri çıkarma için tam kod örnekleriyle.
og_title: görselleri yeniden adlandırma – Word'ten Markdown'a dönüşüm rehberi
tags:
- Aspose.Words
- C#
- Markdown conversion
title: Word'ten Markdown'a dönüştürürken resimleri yeniden adlandırma – tam rehber
url: /tr/java/document-conversion-and-export/how-to-rename-images-when-converting-word-to-markdown-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# görüntüleri yeniden adlandırma – Word'ten Markdown'a Tam Kılavuz

Word .docx dosyasını temiz Markdown'a dönüştürürken **görüntüleri nasıl yeniden adlandıracağınızı** hiç merak ettiniz mi? Tek başınıza değilsiniz. Birçok geliştirici, varsayılan görüntü adlarının GUID'lerin karışık bir karmaşasına dönüşmesiyle takılmaktadır; bu da son Markdown'un okunmasını ve bakımını zorlaştırır.  

Bu rehberde, sadece **görüntüleri nasıl yeniden adlandıracağınızı** göstermekle kalmayıp, aynı zamanda **Word'ü markdown'a dönüştürme**, **docx'i markdown'a dışa aktarma** ve hatta **görüntüleri nasıl çıkaracağınızı** ayrı bir işlem için gösteren eksiksiz, çalıştırılabilir bir çözümü adım adım inceleyeceğiz. Sonunda, tüm bunları tek bir C# betiğiyle yapabileceksiniz—ekstra araçlar gerekmez, manuel yeniden adlandırma da yok.

> **Hızlı önizleme:** .NET için Aspose.Words kullanacağız, bir `MarkdownSaveOptions` geri çağrısı ayarlayacağız ve gömülü her görüntüyü benzersiz, insan‑okunur bir dosya adına yeniden adlandıracağız. Tüm kod kopyala‑yapıştır için hazır.

---

## Öğrenecekleriniz

- **Görüntüleri yeniden adlandırmanın önemi** – okunabilirlik, SEO ve sürüm kontrolü.
- **Word'ü Markdown'a nasıl dönüştüreceğinizi** Aspose.Words kullanarak.
- **DOCX'i Markdown'a nasıl dışa aktaracağınızı** özel kaynak işleme ile.
- **Görüntüleri nasıl çıkaracağınızı** bir DOCX'ten alıp istediğiniz klasöre kaydetmeyi.
- Pratik ipuçları, uç‑durum yönetimi ve tam, çalıştırılabilir bir örnek.

**Önkoşullar**

- .NET 6.0 veya üzeri (kod .NET Core ve .NET Framework ile de çalışır).
- Aspose.Words for .NET kütüphanesi (ücretsiz deneme veya lisanslı sürüm).
- Temel C# bilgisi – bir `Console.WriteLine` yazabiliyorsanız yeterli.

## Word'ten Markdown'a Dönüştürme Sırasında Görüntüleri Yeniden Adlandırma

Bu, öğreticinin kalbidir. `MarkdownSaveOptions.ResourceSavingCallback` bize gömülü her kaynak (görüntüler, ses vb.) için bir kanca sağlar. Geri çağrı içinde yeni bir dosya adı oluşturur, akışı diske yazar ve Aspose'a yeni adın ne olması gerektiğini söyleriz.

![Görüntüleri yeniden adlandırma örneği – yeniden adlandırılmış görüntü dosyalarının ekran görüntüsü](/images/how-to-rename-images-example.png "dönüştürme sırasında görüntüleri yeniden adlandırma")

### Adım 1: Aspose.Words'ı Kurun

Projenize NuGet paketini ekleyin:

```bash
dotnet add package Aspose.Words
```

Ya da Paket Yöneticisi Konsolu üzerinden:

```powershell
Install-Package Aspose.Words
```

### Adım 2: Yeniden Adlandırma Geri Çağrısı ile MarkdownSaveOptions'ı Hazırlayın

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Define the folder where images will be saved
string imageFolder = Path.Combine(Environment.CurrentDirectory, "myImages");
Directory.CreateDirectory(imageFolder);

// Create Markdown save options
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

// Set up the callback that runs for each embedded resource
mdOptions.ResourceSavingCallback = (resource, stream) =>
{
    // Only act on images – other resources (like audio) are left untouched
    if (resource.Type == ResourceType.Image)
    {
        // Generate a friendly, unique name: img_<guid>.png
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Build the full path and copy the stream
        string fullPath = Path.Combine(imageFolder, newFileName);
        using (FileStream file = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            stream.CopyTo(file);
        }

        // Tell Aspose the new filename so the Markdown reference is correct
        resource.FileName = newFileName;
    }
};
```

**Neden bu çalışır:**  
- Geri çağrı bir `ResourceSavingArgs` nesnesi (`resource`) ve bir `Stream` alır.  
- `resource.Type == ResourceType.Image` kontrolü yaparak görüntü olmayan kaynaklarla karışıklığı önleriz.  
- `Guid.NewGuid():N` tire olmadan 32 karakterlik bir onaltılık dize verir, benzersizliği garanti eder.  
- `resource.FileName` güncellenmesi Markdown görüntü bağlantısını (`![](img_…png)`) yeniden yazar.

### Adım 3: DOCX'i Yükleyin ve Markdown Olarak Kaydedin

```csharp
// Path to the source Word document
string docxPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document
Document doc = new Document(docxPath);

// Export to Markdown, applying our custom resource handling
string markdownPath = Path.Combine(Environment.CurrentDirectory, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Conversion complete! Markdown saved to {markdownPath}");
Console.WriteLine($"Images saved to {imageFolder}");
```

Hepsi bu kadar. Programı çalıştırdığınızda şunlar üretilir:

- `output.md` – `![](img_1a2b3c4d5e6f7g8h9i0j1k2l3m4n5o6p.png)` gibi görüntü referanslarına sahip temiz Markdown.
- `myImages` adlı bir klasör, her görüntü dosyasını aynı dostane adla içerir.

---

## Word'ü Markdown'a Dönüştür – Tam Örnek

Tek dosyalı bir betik tercih ediyorsanız, aşağıdakini `Program.cs` dosyasına kopyalayıp çalıştırın:

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // ---------- Configuration ----------
        string inputDocx = "YOUR_DIRECTORY/input.docx";
        string outputMd = "YOUR_DIRECTORY/output.md";
        string imagesDir = Path.Combine("YOUR_DIRECTORY", "myImages");
        Directory.CreateDirectory(imagesDir);

        // ---------- Step 1: Set up Markdown options ----------
        var mdOptions = new MarkdownSaveOptions();
        mdOptions.ResourceSavingCallback = (resource, stream) =>
        {
            if (resource.Type == ResourceType.Image)
            {
                string uniqueName = $"img_{Guid.NewGuid():N}.png";
                string destPath = Path.Combine(imagesDir, uniqueName);
                using (var file = new FileStream(destPath, FileMode.Create, FileAccess.Write))
                    stream.CopyTo(file);
                resource.FileName = uniqueName;
            }
        };

        // ---------- Step 2: Load DOCX ----------
        var doc = new Document(inputDocx);

        // ---------- Step 3: Save as Markdown ----------
        doc.Save(outputMd, mdOptions);

        Console.WriteLine($"✅ Done! Markdown at {outputMd}");
        Console.WriteLine($"🖼️ Images saved in {imagesDir}");
    }
}
```

**Her bloğun açıklaması**

| Block | Purpose |
|-------|---------|
| **Configuration** | Yolları tek bir yerde toplar, böylece sadece bir kez düzenlersiniz. |
| **Step 1** | `MarkdownSaveOptions` ve yeniden adlandırma geri çağrısını oluşturur. |
| **Step 2** | `.docx` dosyasını bir Aspose `Document` nesnesine yükler. |
| **Step 3** | Özel seçeneklerle `Save` çağırır, hem Markdown'ı hem de yeniden adlandırılmış görüntüleri yazar. |

Şu şekilde çalıştırın:

```bash
dotnet run
```

Başarıyı onaylayan iki konsol mesajı görmelisiniz.

---

## DOCX'i Markdown'a Dışa Aktarma – Bu Yaklaşımın Manuel Araçlardan Üstün Olmasının Sebepleri

- **Otomasyon** – Word'ü açmaya, kopyala‑yapıştır yapmaya ve dosyaları elle yeniden adlandırmaya gerek yok.
- **Tutarlılık** – Her görüntü öngörülebilir, benzersiz bir ad alır; bu sürüm kontrolü için harikadır (Git, GUID değiştiği için dosyanın değiştiğini düşünmez).
- **Ölçeklenebilirlik** – Onlarca ya da yüzlerce görüntülü belgelerle çalışır; geri çağrı her kaynak için otomatik olarak tetiklenir.
- **Taşınabilirlik** – Oluşturulan Markdown, görüntü bağlantıları göreceli ve temiz olduğu için herhangi bir statik site jeneratöründe (Jekyll, Hugo, MkDocs) çalışır.

## Bir DOCX Dosyasından Görüntüleri Çıkarma (Bonus)

Bazen sadece ham resimleri, Markdown dosyasını değil, elde etmek istersiniz. Aynı geri çağrı yeniden kullanılabilir ya da doğrudan Aspose'un `Document` API'sini kullanabilirsiniz:

```csharp
using Aspose.Words;
using System.IO;

// Load the document
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Iterate over all shapes (including inline images)
int imgCount = 0;
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.HasImage)
    {
        imgCount++;
        string imgPath = Path.Combine("YOUR_DIRECTORY/extractedImages", $"extracted_{imgCount}.png");
        shape.ImageData.Save(imgPath);
    }
}
Console.WriteLine($"{imgCount} images extracted.");
```

**Ana noktalar**

- `NodeType.Shape` hem yüzen hem de satır içi görüntüleri yakalar.
- `shape.ImageData.Save` ikili görüntüyü doğrudan diske yazar.
- Her iki çıktıya da ihtiyacınız varsa bu kod parçacığını Markdown dönüşümüyle birleştirebilirsiniz.

## Pratik İpuçları ve Yaygın Tuzaklar

- **İsim çakışmaları:** GUID kullanmak temelde çakışmaları ortadan kaldırır, ancak insan‑okunur isimlere (ör. `chapter1_figure2.png`) ihtiyacınız varsa, ismi `resource.Name` veya çevredeki paragraf metninden türetebilirsiniz.
- **Büyük belgeler:** Akışlar doğrudan diske kopyalanır; çok büyük dosyalar için önbellekleme veya önce geçici bir konuma yazma düşünün.
- **PNG olmayan görüntüler:** Yukarıdaki geri çağrı `.png` uzantısını zorlar. Kaynak görüntü JPEG ise, orijinal formatı korumak isteyebilirsiniz: `Path.GetExtension(resource.FileName)` veya `resource.ContentType`.
- **Performans:** Geri çağrı senkron çalışır. Paralel olarak onlarca belge işliyorsanız, dönüşümü `Task.Run` içinde sarmalayın veya UI'nin bloke olmasını önlemek için bir iş parçacığı havuzu kullanın.
- **Lisanslama:** Aspose.Words değerlendirme modunda lisans olmadan çalışır, ancak çıktıya bir filigran ekler. Temiz bir sonuç için bir lisans dosyası (`Aspose.Words.lic`) kurun.

## Sonuç

Word belgesini Markdown'a dönüştürürken **görüntüleri nasıl yeniden adlandıracağınızı** ele aldık, tam bir **convert word to markdown** iş akışı gösterdik, özel kaynak işleme ile **export docx to markdown**'ı gösterdik ve hatta bir DOCX dosyasından **görüntüleri nasıl çıkaracağınızı** açıkladık. Kod bağımsız, modern ve üretime hazır.

Deneyin—`.docx` dosyanızı klasöre bırakın, betiği çalıştırın ve temiz Markdown ile düzenli adlandırılmış görüntü dosyalarının ortaya çıkmasını izleyin. Ardından Markdown'u bir statik site jeneratörüne itebilir, görüntüleri Git'e commit edebilir ya da çıktıyı bir dokümantasyon hattına besleyebilirsiniz.

Kenar durumlarıyla ilgili sorularınız mı var ya da bunu bir ASP.NET Core servisine entegre etmek mi istiyorsunuz? Yorum bırakın, bu senaryoları birlikte inceleyelim. İyi dönüşümler!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}