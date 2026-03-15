---
category: general
date: 2026-03-14
description: Aspose.Words kullanarak docx dosyasından görselleri çıkarırken Word'ü
  hızlıca Markdown'a dönüştürün. Geliştiriciler için adım adım C# örneği.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- Aspose.Words C#
- markdown conversion tutorial
- docx image handling
language: tr
og_description: Aspose.Words ile Word'ü Markdown'a dönüştürün ve docx'ten görselleri
  çıkarın. Sorunsuz bir dönüşüm için bu ayrıntılı rehberi izleyin.
og_title: Word'ü Markdown'a Dönüştür – Tam C# Eğitimi
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: Word'ü Markdown'a Dönüştür – Görsel Çıkarma ile Tam Kılavuz
url: /tr/net/programming-with-markdownsaveoptions/convert-word-to-markdown-full-guide-with-image-extraction/
---

as is.

Now produce final translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'ü Markdown'a Dönüştür – Tam C# Öğreticisi

Word'ü **Markdown'a dönüştürmek** istediğinizde gömülü resimleri nasıl koruyacağınızı bilemediniz mi? Yalnız değilsiniz. Birçok geliştirici, metnin başarılı bir şekilde aktığını fakat resimlerin ortadan kaybolduğunu fark eder. İyi haber? Birkaç satır C# ve güçlü Aspose.Words kütüphanesiyle **Word'ü Markdown'a dönüştürebilir** *ve* **docx'ten resimleri çıkarabilirsiniz** tek bir sorunsuz işlemde.

Bu öğreticide, NuGet paketinin kurulumu, bir `.docx` dosyasının yüklenmesi, markdown kaydedici yapılandırması ve her resmi özel bir klasöre kaydeden ve resim bağlantılarını yeniden yazan bir geri çağırma (callback) eklemesi gibi tüm adımları göstereceğiz. Sonunda, kullanıma hazır bir Markdown dosyanız ve orijinal Word belgesindeki tüm resimleri içeren düzenli bir `resources` dizininiz olacak.

## Öğrenecekleriniz

- C# projesinde Aspose.Words for .NET'in nasıl kurulacağını.  
- **Word'ü Markdown'a dönüştürürken** resimleri korumak için gereken tam kodu.  
- **docx'ten resimleri çıkarmak** için `ResourceSavingCallback` neden vazgeçilmez olduğunu.  
- Yaygın tuzaklar (ör. yol ayırıcıları, aynı ada sahip dosyalar) ve bunlardan nasıl kaçınılacağını.  
- Oluşturulan Markdown'un doğru render edildiğinden emin olmak için hızlı doğrulama adımları.

### Önkoşullar

| Gereksinim | Sebep |
|-------------|--------|
| .NET 6.0 veya daha yeni (veya .NET Framework 4.7+) | Aspose.Words her iki platformu da destekler; yeni çalışma zamanları daha iyi performans sağlar. |
| Visual Studio 2022 (veya herhangi bir C# IDE) | Hata ayıklamayı ve paket yönetimini kolaylaştırır. |
| NuGet geri yükleme için internet bağlantısı | Kütüphane resmi beslemeden indirilir. |
| Metin **ve** resim içeren bir örnek `input.docx` | Resim çıkarımını gözlemlemek için. |

Ek bir üçüncü‑taraf aracı gerekmez—Aspose.Words her şeyi arka planda halleder.

---

## Adım 1: Aspose.Words'u NuGet Üzerinden Kurun

İlk olarak, Aspose.Words paketini projenize ekleyin. **Package Manager Console**'u açın ve şu komutu çalıştırın:

```powershell
Install-Package Aspose.Words
```

Alternatif olarak UI'yı kullanın: proje üzerine sağ‑tıklayın → *Manage NuGet Packages* → “Aspose.Words” aratın → **Install**'a tıklayın. Bu, gerekli çekirdek DLL'leri ve ileride ihtiyacımız olacak `Saving` ad alanını getirir.

> **Pro ipucu:** Sürümü sabitleyin (ör. `22.12.0`) böylece kütüphane otomatik güncellendiğinde beklenmedik kırılmalarla karşılaşmazsınız.

---

## Adım 2: Kaynak Word Belgesini Yükleyin

Kütüphane hazır olduğuna göre, `.docx` dosyasını yükleyebiliriz. Mutlak ya da göreli bir yol kullanarak kaynak belgenize işaret edin.

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file. Replace the placeholder with your actual path.
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **Neden önemli:** `Document` tüm Word paketini ayrıştırır, bize paragraflara, tablolara ve daha sonra çıkaracağımız gizli resim parçalarına erişim sağlar.

---

## Adım 3: Markdown Kaydetme Seçeneklerini Oluşturun

Aspose.Words, dönüşüm davranışını ayarlamamıza izin veren bir `MarkdownSaveOptions` sınıfı sunar. En azından bir örnek oluştururuz; daha sonra bir geri çağırma ekleyeceğiz.

```csharp
// Instantiate the options object.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

`ExportImagesAsBase64` (false olarak ayarlanmalı çünkü ayrı resim dosyaları istiyoruz) ya da `ExportHeadersFooters` gibi özellikleri ihtiyacınıza göre ayarlayabilirsiniz.

---

## Adım 4: ResourceSavingCallback'i Yapılandırın – DOCX'ten Resimleri Çıkarın

Bu, öğreticinin kalbidir. `ResourceSavingCallback`, kaydedicinin **her kaynak** (resimler, yazı tipleri vb.) için yazma isteğinde bulunduğunda tetiklenir. Kendi işleyicimizi sağlayarak resmin nereye kaydedileceğine ve Markdown dosyasının ona nasıl referans vereceğine karar veririz.

```csharp
mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
    (sender, args) =>
    {
        // 1️⃣ Define the folder where we’ll dump extracted pictures.
        string imageFolder = @"YOUR_DIRECTORY\resources\";

        // 2️⃣ Ensure the folder exists – create it on the fly.
        Directory.CreateDirectory(imageFolder);

        // 3️⃣ Preserve the original filename (e.g., Image1.png).
        string imageFileName = Path.GetFileName(args.FileName);
        string targetPath   = Path.Combine(imageFolder, imageFileName);

        // 4️⃣ Write the image stream to disk.
        using (FileStream fs = new FileStream(targetPath, FileMode.Create))
        {
            args.Stream.CopyTo(fs);
        }

        // 5️⃣ Tell the Markdown generator to use a relative path.
        //    This is the step that **extract images from docx** correctly.
        args.ResourceFileName = $"resources/{imageFileName}";
    });
```

### Bunun Yaptıkları

1. **`resources`** adlı bir alt‑klasör oluşturur (eğer zaten yoksa).  
2. Gelen her resim akışını bu klasöre, karışıklığı önlemek için orijinal dosya adıyla kopyalar.  
3. Markdown bağlantısını (`![alt](resources/Image1.png)`) günceller, böylece dosya render edildiğinde resim gösterilir.

> **Köşe durumu:** İki resim aynı ada sahipse, sonraki olan öncekinin üzerine yazar. Bunu önlemek için bir GUID ekleyebilir ya da kaydetmeden önce `Path.GetUniqueFileName` (özel bir yardımcı) kullanabilirsiniz.

---

## Adım 5: Belgeyi Markdown Olarak Kaydedin

Geri çağırma bağlandıktan sonra, tek satırlık bir komutla Markdown dosyasını yazdırırız.

```csharp
// Choose the output path for the Markdown file.
string markdownPath = @"YOUR_DIRECTORY\output.md";

doc.Save(markdownPath, mdOptions);
```

Bu çağrı tamamlandığında şunlara sahip olacaksınız:

- `output.md` içinde Markdown metni ve `![Image1](resources/Image1.png)` gibi resim referansları.  
- Orijinal `.docx` dosyasından çıkarılan tüm resimlerin bulunduğu bir `resources` klasörü.

---

## Adım 6: Sonucu Doğrulayın

`output.md` dosyasını herhangi bir Markdown görüntüleyicide (VS Code, GitHub, Typora) açın. Orijinal belgenin başlıkları, listeleri ve **resimlerin doğru şekilde render edildiğini** görmelisiniz. Bir resim eksikse:

1. `resources` klasörünün dosyayı içerdiğini kontrol edin.  
2. Markdown'taki göreli yolun (`resources/<dosyaadı>`) klasör adıyla tam olarak eşleştiğinden emin olun (Linux'ta büyük/küçük harfe duyarlıdır).  
3. Resim dosyasının bozuk olmadığını doğrulayın – doğrudan bir resim görüntüleyicide açın.

---

## Tam Çalışan Örnek

Aşağıda, doğrudan çalıştırabileceğiniz tam program yer alıyor. `YOUR_DIRECTORY` yer tutucusunu gerçek klasör yolunuzla değiştirin.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class WordToMarkdown
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Load the source Word document.
        // -------------------------------------------------
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // -------------------------------------------------
        // 2️⃣ Prepare Markdown save options.
        // -------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // Export images as separate files, not Base64.
            ExportImagesAsBase64 = false
        };

        // -------------------------------------------------
        // 3️⃣ Set up the callback to **extract images from docx**.
        // -------------------------------------------------
        mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
            (sender, args) =>
            {
                string imageFolder = @"YOUR_DIRECTORY\resources\";
                Directory.CreateDirectory(imageFolder);

                string imageFileName = Path.GetFileName(args.FileName);
                string targetPath = Path.Combine(imageFolder, imageFileName);

                using (FileStream fs = new FileStream(targetPath, FileMode.Create))
                {
                    args.Stream.CopyTo(fs);
                }

                // Update the reference used inside the Markdown file.
                args.ResourceFileName = $"resources/{imageFileName}";
            });

        // -------------------------------------------------
        // 4️⃣ Save as Markdown.
        // -------------------------------------------------
        string outputPath = @"YOUR_DIRECTORY\output.md";
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Check output.md and the resources folder.");
    }
}
```

**Beklenen çıktı:** `output.md` dosyasını açtığınızda aşağıdakine benzer bir şey görmelisiniz:

```markdown
# Sample Title

Here is some introductory text.

![Image1](resources/Image1.png)

More paragraphs…

![Diagram](resources/Diagram.jpg)
```

Tüm resimler, orijinal Word dosyasındaki gibi metnin yanında yan yana görünür.

---

## Yaygın Sorular & Dikkat Edilmesi Gerekenler

**S: Çıkarma sırasında resim formatını değiştirebilir miyim?**  
C: Evet. Geri çağırma içinde akışı (ör. PNG'ye) yeniden kodlayabilirsiniz. `System.Drawing` ya da `ImageSharp` kullanarak `args.Stream` üzerinde işlem yapın.

**S: Word belgesi SVG veya EMF resimleri içeriyorsa ne olur?**  
C: Aspose.Words, çoğu vektör formatını varsayılan olarak raster PNG'ye dönüştürür. Orijinal vektörü korumanız gerekiyorsa `mdOptions.ExportImageResolution` ayarlayın ve akışı ona göre yönetin.

**S: Bu .NET Core üzerinde Linux'ta çalışır mı?**  
C: Kesinlikle. `resources` yolunun ileri eğik çizgi (`/`) kullandığından ya da gösterildiği gibi `Path.Combine` ile oluşturulduğundan emin olun. Linux dosya sistemlerinin büyük/küçük harfe duyarlı olduğunu unutmayın, klasör adlarını tutarlı tutun.

**S: Dipnotları veya yorumları bastırmak istiyorum, nasıl yaparım?**  
C: Kaydetmeden önce `mdOptions.ExportFootnotes` veya `mdOptions.ExportComments` özelliklerini ayarlayın.

---

## Sonuç

**Word'ü Markdown'a dönüştürürken** güvenilir bir şekilde **docx'ten resimleri çıkarmak** için **tam, uçtan uca bir çözüm** ele aldık. Aspose.Words'un `MarkdownSaveOptions` ve `ResourceSavingCallback` özelliklerini kullanarak hem metin dönüşümüne hem de resim yönetimine ince ayar yapabilirsiniz. Kod kendi içinde bağımsızdır, herhangi bir .NET platformunda çalışır ve mevcut iş akışlarınıza minimum çaba ile entegre edilebilir.

Bir sonraki adıma hazır mısınız? Toplu dönüşümleri otomatikleştirmeyi, bu mantığı bir ASP.NET API'sine entegre etmeyi ya da geri çağırmayı her çıkarılan resim için küçük önizlemeler oluşturacak şekilde genişletmeyi düşünebilirsiniz. Temel dönüşümü sağladıktan sonra sınır yok!

---

![convert word to markdown örneği](convert-word-to-markdown.png "convert word to markdown örneği")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}