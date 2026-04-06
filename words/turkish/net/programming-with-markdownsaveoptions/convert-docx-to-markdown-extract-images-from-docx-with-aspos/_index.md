---
category: general
date: 2026-04-05
description: DOCX'i Markdown'a dönüştürmeyi ve DOCX'ten resimleri C# ile çıkarmayı
  öğrenin. Tam kod ve ipuçlarıyla adım adım rehber.
draft: false
keywords:
- convert docx to markdown
- extract images from docx
- Aspose.Words markdown conversion
- C# document processing
- image extraction C#
language: tr
og_description: Aspose.Words kullanarak DOCX'i Markdown'a dönüştürün ve DOCX'ten görselleri
  çıkarın. Kod, açıklama ve en iyi uygulama ipuçlarıyla tam bir C# öğreticisi.
og_title: DOCX'i Markdown'a Dönüştür – DOCX'ten Görselleri C# ile Çıkar
tags:
- Aspose.Words
- C#
- Markdown
- DOCX
- Image extraction
title: DOCX'i Markdown'a Dönüştür – Aspose.Words ile DOCX'ten Görselleri Çıkar
url: /tr/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-extract-images-from-docx-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX'i Markdown'e Dönüştür – DOCX'ten Görselleri C# ile Çıkar

DOCX'i **Markdown'e dönüştürmek** istediğinizde ama çıktıda görsellerin kaybolmasıyla mı mücadele ettiniz? Tek başınıza değilsiniz. Birçok projede markdown sürümü sürüm kontrolü veya statik‑site jeneratörleri için mükemmeldir, ancak resimler geride kalır ve zengin bir belgeyi çorak bir metin dosyasına dönüştürür.  

İyi haber? Birkaç satır C# ve Aspose.Words ile **DOCX'i Markdown'e dönüştürebilir** *ve* **DOCX'ten görselleri otomatik olarak çıkarabilirsiniz**. Bu kılavuz, tüm süreci adım adım anlatır, her parçanın neden önemli olduğunu açıklar ve görsel klasörünüzü düzenli tutmanın yollarını gösterir.

## Öğrenecekleriniz

- Resim içeren bir DOCX dosyasını nasıl yüklersiniz.
- Her görselin nereye kaydedileceğini belirleyen özel bir `IResourceSavingCallback` nasıl tanımlanır.
- Oluşturulan markdown'ın çıkarılan görsellere doğru şekilde referans vermesi için `MarkdownSaveOptions` nasıl yapılandırılır.
- Çift görsel adları veya PNG olmayan formatlar gibi kenar durumlarını ele almak için ipuçları.
- Bugün çalıştırabileceğiniz, tamamen kopyala‑yapıştır hazır bir kod örneği.

### Önkoşullar

- .NET 6.0 veya üzeri (API .NET Core, .NET Framework ve .NET 5+ üzerinde çalışır).
- **Aspose.Words for .NET** lisansı (ücretsiz deneme sürümü test için yeterlidir).
- C# ve Visual Studio (veya tercih ettiğiniz IDE) konusunda temel bilgi.

Eğer bunlara sahipseniz, hemen başlayalım.

---

## Adım 1: Projeyi Oluşturun ve Aspose.Words'u Yükleyin

İlk olarak yeni bir console uygulaması oluşturun (veya mevcut bir çözüme entegre edin).

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

> **Pro ipucu:** En yeni NuGet sürümünü (Nisan 2026 itibarıyla 24.12) kullanın; böylece en yeni markdown dışa aktarma iyileştirmelerinden faydalanırsınız.

---

## Adım 2: Görselleri İstediğiniz Yere Kaydedecek Bir Geri Çağırma (Callback) Oluşturun

Aspose.Words, markdown dışa aktarımı sırasında yazılan her kaynağı (görseller, SVG'ler vb.) yakalamanıza izin verir. `IResourceSavingCallback` uygulayarak şunları yapabilirsiniz:

1. Markdown dosyanızın yanına bir klasör seçin.
2. Benzersiz bir dosya adı oluşturun (böylece mevcut bir görseli asla üzerine yazmazsınız).
3. Formatı belirleyin (burada tutarlılık için PNG zorunlu kılıyor).

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Saves each image extracted from the DOCX into a dedicated folder
/// with a GUID‑based filename. The markdown file will reference the
/// new filename via <c>args.ResourceFileName</c>.
/// </summary>
class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageResourceSaver(string targetFolder)
    {
        _targetFolder = targetFolder;
        // Ensure the folder exists before we start writing files.
        Directory.CreateDirectory(_targetFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique name to avoid collisions.
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Full physical path where the image will be written.
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // Tell the markdown exporter what name to use in the .md file.
        args.ResourceFileName = newFileName;

        // Provide a stream that writes to the desired location.
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}
```

### Neden GUID‑tabanlı bir ad?

Kaynak DOCX aynı orijinal ada sahip iki resim içeriyorsa, basit bir kopyala‑yapıştır birini üzerine yazar. `Guid.NewGuid()` kullanmak benzersizliği garantiler; bu, dönüşümü otomatik bir pipeline’da birçok kez çalıştırdığınızda özellikle kullanışlıdır.

---

## Adım 3: DOCX'i Yükleyin ve Markdown Seçeneklerini Bağlayın

Şimdi belgeyi belleğe alıp az önce oluşturduğumuz geri çağırmayı ekliyoruz.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------------
        // 1️⃣  Define paths – adjust these to match your environment.
        // --------------------------------------------------------------------
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMarkdown = @"C:\Docs\DocWithImages.md";
        string imagesFolder = @"C:\Docs\MarkdownResources";

        // --------------------------------------------------------------------
        // 2️⃣  Load the Word document.
        // --------------------------------------------------------------------
        Document doc = new Document(sourceDocx);

        // --------------------------------------------------------------------
        // 3️⃣  Configure MarkdownSaveOptions with our custom saver.
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This tells Aspose.Words to call ImageResourceSaver for each image.
            ResourceSavingCallback = new ImageResourceSaver(imagesFolder)
        };

        // --------------------------------------------------------------------
        // 4️⃣  Perform the conversion.
        // --------------------------------------------------------------------
        doc.Save(outputMarkdown, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputMarkdown}");
        Console.WriteLine($"Images saved to:   {imagesFolder}");
    }
}
```

### Kodun ne yaptığını adım adım inceleyelim

| Adım | Amaç |
|------|------|
| **Yolları tanımla** | Projenizi esnek tutar; yeniden derlemeden istediğiniz klasöre işaret edebilirsiniz. |
| **DOCX'i yükle** | `Document` Word dosyasını ayrıştırır, tüm öğelere (paragraflar, tablolar, resimler) erişim sağlar. |
| **`MarkdownSaveOptions`'ı yapılandır** | `ResourceSavingCallback` görselleri çıkaran kancadır. Bu olmadan Aspose.Words ayarlara bağlı olarak görselleri base64 olarak gömebilir ya da tamamen atabilir. |
| **Kaydet** | `doc.Save` markdown dosyasını yazar ve her görsel için geri çağırmayı tetikler. |

---

## Adım 4: Çıktıyı Doğrulayın – Ne Görmelisiniz?

Programı çalıştırdıktan sonra `DocWithImages.md` dosyasını açın. Aşağıdaki gibi markdown görsel bağlantılarını göreceksiniz:

```markdown
![img_1a2b3c4d5e6f7g8h9i0j.png](MarkdownResources/img_1a2b3c4d5e6f7g8h9i0j.png)
```

Ve `C:\Docs\MarkdownResources` içinde GUID adlı bir dizi PNG dosyası bulacaksınız. Her birini açın – orijinal DOCX içinde gömülü resimlerle aynı olmalı.

Markdown dosyasını, göreli yolları destekleyen bir görüntüleyicide (ör. VS Code önizlemesi, GitHub veya bir statik‑site jeneratörü) açarsanız, görseller Word'de olduğu gibi görüntülenecektir.

### Yaygın Tuzaklar & Nasıl Önlenir

| Belirti | Muhtemel Neden | Çözüm |
|---------|----------------|------|
| Görseller kırık bağlantı olarak görünüyor | `ResourceFileName` ayarlanmamış, bu yüzden markdown var olmayan bir dosyaya işaret ediyor. | Geri çağırma içinde `args.ResourceFileName = newFileName;` satırının olduğundan emin olun. |
| PNG dosyaları çok büyük | Orijinal görseller JPEG veya BMP idi; PNG'ye dönüştürmek boyutu artırabilir. | `args.ResourceContentType` ile orijinal formatı tespit edin ve koruyun: `args.ResourceFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";` |
| Çift görseller hâlâ görünüyor | Statik bir dosya adı yerine GUID kullanmadınız. | GUID mantığına geri dönün veya görsel tipine göre bir sayaç ekleyin. |
| Dönüşüm `FileNotFoundException` hatası veriyor | DOCX dosya yolu yanlış veya klasörde okuma izni yok. | Yolu kontrol edin ve gerekli dosya sistemi izinlerini verin. |

---

## Adım 5: İleri Düzey Ayarlamalar (İsteğe Bağlı)

### 5.1 Orijinal Görsel Formatlarını Koruyun

Çıktı görsellerinin orijinal uzantılarını korumak isterseniz geri çağırmayı şu şekilde değiştirin:

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
    // Default to .png if Aspose couldn't determine an extension.
    if (string.IsNullOrEmpty(ext)) ext = ".png";

    string newFileName = $"img_{Guid.NewGuid():N}{ext}";
    string fullPath = Path.Combine(_targetFolder, newFileName);
    args.ResourceFileName = newFileName;
    args.Stream = new FileStream(fullPath, FileMode.Create);
}
```

### 5.2 Görselleri Base64 Olarak Göm (Ayrı Dosyalar İstemediğinizde)

Bazen tek dosyalı bir markdown tercih edilir (ör. e‑posta ile gönderim). Seçeneği şu şekilde değiştirin:

```csharp
mdOptions.ImagesFolder = string.Empty; // disables external folder
mdOptions.ExportImagesAsBase64 = true;
```

Ancak unutmayın: **DOCX'ten görselleri çıkar** çoğu statik‑site iş akışı için birincil hedeftir, bu yüzden klasör yaklaşımı genellikle daha iyi bir seçimdir.

---

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

Aşağıda tüm program tek bir dosyada verilmiştir. Yolları kendi ortamınıza göre değiştirin ve çalıştırın.

```csharp
// ---------------------------------------------------------------
// Convert DOCX to Markdown – Extract Images from DOCX
// ---------------------------------------------------------------
// NuGet: Aspose.Words (>= 24.12)
// ---------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageResourceSaver(string targetFolder) => Directory.CreateDirectory(_targetFolder = targetFolder);

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
        if (string.IsNullOrEmpty(ext)) ext = ".png";
        string newFileName = $"img_{Guid.NewGuid():N}{ext}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        args.ResourceFileName = newFileName;
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}

class Program
{
    static void Main()
    {
        // 👉 Adjust these paths:
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMd  = @"C:\Docs\DocWithImages.md";
        string imgFolder = @"C:\Docs\MarkdownResources";

        // Load the DOCX.
        Document doc = new Document(sourceDocx);

        // Set up markdown options with our image saver.
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageResourceSaver(imgFolder)
        };

        // Perform conversion.
        doc.Save(outputMd, mdOptions);

        Console.WriteLine("✅ DOCX successfully converted to Markdown.");
        Console.WriteLine($"📄 Markdown: {outputMd}");
        Console.WriteLine($"🖼️ Images folder: {imgFolder}");
    }
}
```

`dotnet run` ile çalıştırın. Konsol ✅ satırını yazdırdığında markdown dosyasını açın; görsellerin doğru şekilde görüntülendiğini göreceksiniz.

---

## Sonuç

Artık **DOCX'i Markdown'e dönüştürmek ve DOCX'ten görselleri çıkarmak** için Aspose.Words kullanarak C# içinde **tam, üretim‑hazır bir çözüme** sahipsiniz. Ana anahtar kelime kılavuz boyunca tekrar edildi, bu da arama motorları ve AI asistanları için alaka düzeyini artırır.  

Tek bir geçişte kod:

1. Word belgesini yükler.
2. Her görseli `IResourceSavingCallback` ile yakalar.
3. Görselleri benzersiz bir adla tahmin edilebilir bir klasöre kaydeder.
4. Bu görsellere referans veren markdown üretir.

Buradan itibaren:

- Plug

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}