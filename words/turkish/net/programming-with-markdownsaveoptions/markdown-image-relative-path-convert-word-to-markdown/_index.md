---
category: general
date: 2026-04-28
description: Word'ü markdown'a dönüştürürken markdown görüntü göreli yolunu nasıl
  ayarlayacağınızı, Word'ten görüntüleri nasıl çıkaracağınızı ve dışa aktarılan görüntüler
  için kaynak klasörü nasıl oluşturacağınızı öğrenin.
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: tr
og_description: Word'ü markdown'a dönüştürürken markdown görüntü göreli yolunu ayarlayın,
  Word'ten görüntüleri çıkarın ve dışa aktarılan görüntüler için bir kaynak klasörü
  oluşturun.
og_title: Markdown resim göreceli yolu – Word'ü Markdown'a dönüştür
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: markdown görsel göreceli yolu – Word'ü Markdown'a dönüştür
url: /tr/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown image relative path – Word'ü Markdown'a Dönüştürme

Word'ü **markdown**'a **dönüştürürken** **markdown image relative path**'e ihtiyaç duydunuz mu? Tek başınıza değilsiniz. Çoğu geliştirici, oluşturulan Markdown'ın görüntüleri düz bir klasöre işaret etmesi ve statik bir site ya da GitHub deposunda beklediğiniz göreli bağlantı yapısını bozan bir sorunla karşılaşıyor.

Bu öğreticide, **Word'ten görüntüleri çıkaran**, **bir resources klasörü oluşturan** ve görüntü referanslarını temiz bir *markdown image relative path* kullanacak şekilde yeniden yazan eksiksiz, uçtan uca bir çözümü adım adım inceleyeceğiz. Sonunda, yayınlamaya hazır bir `.md` dosyanız ve orijinal `.docx` dosyasından çıkarılan tüm resimleri içeren düzenli bir `Resources` dizininiz olacak.

> **Neler elde edeceksiniz:** tek bir C# programı (harici script yok), *neden* her parçanın önemli olduğunu açıklayan net bir anlatım ve kendi projelerinizde kopyala‑yapıştır yapabileceğiniz birkaç pratik ipucu.

---

## Prerequisites

Kodlara geçmeden önce şunların yüklü olduğundan emin olun:

- **.NET 6.0** veya daha yeni bir sürüm (isteğe bağlı olarak .NET Framework 4.7+ hedefleyebilirsiniz, ancak yeni projeler için .NET 6 ideal).
- **Aspose.Words for .NET** (yazım anındaki en yeni NuGet paketi, sürüm 23.12). Şu komutla kurun:
  ```bash
  dotnet add package Aspose.Words
  ```
- Görüntü içeren bir Word belgesi – örneğin `WithImages.docx`.
- Markdown ve görüntülerin kaydedileceği bir klasör, örnek: `C:\Projects\MarkdownExport`.

Ek bir kütüphane gerekmez; geri kalan her şey Aspose.Words tarafından halledilir.

---

## Step 1: Load the source Word document (the starting point for convert word to markdown)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*Why this matters:* Belgeyi yüklemek, daha sonra **docx'ten görüntüleri dışa aktarmak** için ihtiyacımız olan görüntü parçalarını içeren iç node ağacına erişmemizi sağlar. Yükleme başarısız olursa sonraki adımlar çalışmaz, bu yüzden yol ve dosya izinlerini iki kez kontrol edin.

---

## Step 2: Configure `MarkdownSaveOptions` with a custom callback (the heart of create resources folder)

`ResourceSavingCallback`, Aspose.Words bir görüntü dosyası yazmak istediğinde devreye girmenizi sağlar. Callback içinde **Resources alt klasörünü** oluşturacak ve oluşturulan markdown'ın bir *markdown image relative path* kullanmasını sağlayacağız.

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

`resourcesFolder` değişkenini callback'in yapıcısına gönderdiğimize dikkat edin—bu, klasör yolunu esnek tutar ve kod içinde sabit string kullanmaktan kaçınır.

---

## Step 3: Implement the callback that **creates resources folder** and rewrites the path

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*Why this works:* `args.Stream` ham görüntü baytlarını içerir. Bu akışı `Resources` klasörümüz içinde bir dosyaya kopyalayarak **docx'ten görüntüleri dışa aktarmış** oluruz. Ardından `args.ResourceFileName`'i göreli bir URL (`Resources/image.png`) ile değiştiririz. Aspose.Words daha sonra markdown'ı yazdığında tam olarak bu dizeyi enjekte eder ve istediğimiz *markdown image relative path* elde edilir.

---

## Step 4: Verify the generated Markdown (what the final output looks like)

`Doc.md` dosyasını herhangi bir metin editöründe açın. Aşağıdakine benzer bir içerik görmelisiniz:

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

Önemli kısım, her görüntü referansının `Resources/...` dizinine işaret etmesidir – aradığımız **markdown image relative path** budur.

![markdown image relative path example](example.png "markdown image relative path example")

*Tip:* Markdown'ı göreli bağlantıları destekleyen bir görüntüleyicide (VS Code önizlemesi, GitHub veya bir static site generator) açarsanız, ek bir yapılandırma gerekmeden resimler doğru şekilde gösterilir.

---

## Step 5: Common pitfalls and pro‑tips

| Issue | Why it happens | How to fix it |
|-------|----------------|---------------|
| Images end up in the root folder instead of `Resources` | Callback eklenmemiş veya `args.ResourceFileName` üzerine yazılmamış. | `ResourceSavingCallback`'in **doc.Save** çağrısından **önce** ayarlandığından emin olun. |
| Filenames contain illegal characters | Word bazen görüntülere boşluk veya Unicode karakterli isimler verir. | Callback içinde `args.ResourceFileName`'i temizlemek için `Path.GetInvalidFileNameChars()` kullanın. |
| Large documents take a long time to process | Her görüntü senkron olarak yazılıyor. | .NET 6+ üzerindeyseniz ve performans gerekiyorsa asenkron I/O'ya geçin (`await args.Stream.CopyToAsync(fileStream)`). |
| Relative paths break when the markdown is moved | Yol, markdown dosyasının konumuna görecelidir. | `Doc.md` ve `Resources` klasörünü birlikte tutun veya callback'i farklı bir göreli önek (`../assets` gibi) kullanacak şekilde ayarlayın. |

---

## Step 6: Extending the solution (what if you need more control?)

- **Multiple output formats:** `MarkdownSaveOptions` yerine `HtmlSaveOptions` veya `PdfSaveOptions` kullanın, aynı callback'i koruyun—Aspose.Words format ne olursa olsun her görüntü için callback'i tetikler.
- **Custom image naming:** Görüntüleri yeniden adlandırmak isterseniz (ör. `figure-01.png`), dosyayı yazmadan önce `args.ResourceFileName`'i callback içinde değiştirin.
- **Embedding images as Base64:** `args.ResourceFileName`'i bir data URI (`data:image/png;base64,...`) olarak ayarlayın ve dosya yazımını atlayın. Tek dosyalı markdown dışa aktarımları için kullanışlıdır.

---

## Conclusion

Artık **Word'ü markdown'a dönüştüren**, **word'ten görüntüleri çıkaran**, **resources klasörü oluşturan** ve her resim için temiz bir **markdown image relative path** garantileyen tam işlevsel bir C# programınız var. Kod bağımsız, en yeni Aspose.Words sürümüyle çalışıyor ve minimal çabayla herhangi bir .NET projesine eklenebilir.

Sonraki adım? Oluşturduğunuz markdown'ı Hugo ya da Jekyll gibi bir static site generator'a beslemek ya da callback'i doğrudan Base64 gömmek için denemek. SVG görüntüler ya da aşırı büyük dosyalar gibi kenar durumlarıyla karşılaşırsanız, “Common pitfalls” tablosuna geri dönün; genellikle küçük bir ayar sorunu çözüm getirir.

İyi kodlamalar, ve markdown'ınız her zaman doğru klasöre işaret etsin!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}