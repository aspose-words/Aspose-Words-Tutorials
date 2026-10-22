---
category: general
date: 2026-10-13
description: C# kullanarak belgelerde yazı tipi ikamesini öğrenin. Bu kılavuz, big5
  kodlamasını nasıl ayarlayacağınızı, bir DOCX dosyasını nasıl yükleyeceğinizi ve
  eski yazı tiplerini modern olanlarla nasıl değiştireceğinizi gösterir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: tr
lastmod: 2026-10-13
og_description: Belgedeki font değişimi, eski Çin dosyalarıyla çalışırken çok önemlidir.
  Big5 kodlamalı bir DOCX dosyasını yüklemek ve eski fontları değiştirmek için bu
  adım adım öğreticiyi izleyin.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: C# ile belgelerde yazı tipi değiştirme – kapsamlı rehber
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: C# ile belgede yazı tipi ikamesi nasıl yapılır
url: /tr/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Belge içinde Yazı Tipi Değiştirme – Tam C# Öğreticisi

Eğer **font substitution in document** özelliğini kullanarak eski Çin dosyalarını doğru şekilde görüntülemek istiyorsanız, bu kılavuz tam olarak nasıl yapılacağını gösterir. Doğru metin kodlamasını yapılandırarak ve eski bir yazı tipini modern bir yazı tipiyle değiştirerek, son DOCX’in istediğiniz gibi görüntülenmesini garantilersiniz.

Belge işleme, kaynak **big5** gibi eski bir kodlama kullandığında veya sistemde artık bulunmayan bir yazı tipine referans verdiğinde sık sık kırılır. Bu öğretici, **big5 kodlaması** ile bir DOCX’i nasıl yükleyeceğinizi, **legacy font replacement** (eski yazı tipi değiştirme) işlemini nasıl uygulayacağınızı ve herhangi bir Windows makinesinde çalışan temiz bir çıktı üretmeyi adım adım anlatır.

Öğrenecekleriniz:

* **big5 kodlaması** ile bir `LoadOptions` nesnesi oluşturma.  
* **C# LoadOptions** kullanarak bir DOCX dosyasını açma.  
* Eski bir yazı tipini modern bir eşdeğere eşleyerek **font substitution in document** gerçekleştirme.  
* Eksik yazı tipleri ve birden fazla yazı tipi ailesi için kenar‑durumlarını ele alma.

Aspose.Words for .NET kütüphanesi dışındaki hiçbir araç gerekmez; tam kodu bir konsol projesine kopyalayıp hemen çalıştırabilirsiniz.

## Gereksinimler

* .NET 6.0 veya üzeri (örnek .NET 6 konsol sözdizimini kullanır).  
* Aspose.Words for .NET – `dotnet add package Aspose.Words` komutuyla kurun.  
* **big5 kodlaması** ile kaydedilmiş ve eski yazı tipi `MingLiU-ExtB`’ye referans veren bir DOCX dosyası.  
* C# ve Visual Studio ya da tercih ettiğiniz herhangi bir IDE hakkında temel bilgi.

## Adım 1: Projeyi kurun ve ad alanlarını içe aktarın

Yeni bir konsol uygulaması oluşturun ve gerekli `using` yönergelerini ekleyin. Bu, kodun ekstra değişiklik yapmadan derlenmesini sağlar.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **İpucu:** `Main` metodunu mümkün olduğunca basit tutun; bu, okunabilirliği artırır ve öğreticiyi daha kolay takip etmenizi sağlar.

## Adım 2: Doğru metin kodlamasıyla (Traditional Chinese için big5) yükleme seçeneklerini tanımlayın

`LoadOptions` sınıfı, Aspose.Words’e kaynak dosyadaki ham baytları nasıl yorumlayacağını söyler. **big5 kodlaması**, o eski kod sayfasıyla kaydedilmiş Geleneksel Çince karakterler için kritiktir.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Neden önemli:** Kodlamayı atlayıp varsayılan UTF‑8’i kullanırsanız, karakterler bozuk semboller (mojibake) olarak görünebilir. `big5` belirtmek, herhangi bir yazı tipi değiştirmesinden önce orijinal gliflerin korunmasını sağlar.

## Adım 3: Belirtilen kodlamayı kullanarak DOCX dosyasını yükleyin

`loadOptions` örneğini `Document` yapıcısına geçirin. Bu, dosyayı **Chinese için belge kodlamasını** daha önce tanımladığınız şekilde yükler.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

Dosya bulunamazsa, program bir `FileNotFoundException` fırlatır. Yolun doğru olduğundan ve uygulamanın okuma iznine sahip olduğundan emin olun.

## Adım 4: Eski bir yazı tipini modern bir eşdeğerle değiştirin

Birçok eski Çince belge, yeni Windows kurulumlarında bulunmayabilecek `MingLiU-ExtB` yazı tipine referans verir. Bunu yaygın olarak bulunan Unicode yazı tipi `Microsoft JhengHei` ile eşlemek, doğru görüntülenmeyi sağlar.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Açıklama:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` global bir değiştirme kuralı kaydeder. Aspose.Words her `MingLiU-ExtB` ile karşılaştığında, onu `Microsoft JhengHei` ile değiştirir.  
* İsteğe bağlı döngü, büyük belgelerde birden fazla yazı tipi ailesi olduğunda faydalı olan eşlemeyi ekrana yazdırır.

## Adım 5: İşlenmiş belgeyi kaydedin

Değiştirme işlemi tamamlandıktan sonra belgeyi yeni bir dosyaya yazın. Çıktı, modern yazı tipini kullanarak Çince metni gösterecek ve eksik glif uyarılarını ortadan kaldıracaktır.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Sonuç dosyasını Microsoft Word ya da herhangi bir DOCX görüntüleyicide açın; Geleneksel Çince karakterlerin `Microsoft JhengHei` ile temiz bir şekilde render edildiğini görmelisiniz.

## Kenar durumları ve yaygın tuzakların ele alınması

| Durum | Önerilen yaklaşım |
|-----------|----------------------|
| **Kaynak yazı tipi belgede listelenmemiş** | `doc.FontInfos.Substitution.Add` ile bir joker karakter deseni kullanın, ör. `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **Birden fazla eski yazı tipi değiştirilmesi gerekiyor** | Her çift için `Add` çağırın veya bir yapılandırma dosyasından bir değiştirme sözlüğü yükleyin. |
| **Hedef yazı tipi hedef makinede bulunamıyor** | Windows ile birlikte gelen bir yazı tipi seçin (ör. `Arial Unicode MS`) veya `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll` kullanarak yazı tipini gömün. |
| **Kodlama hataları hâlâ görünüyor** | Kaynak dosyanın gerçekten **big5** kullandığını doğrulayın; dosyayı bir hex editörle inceleyebilir veya `File.ReadAllBytes` ile bayt desenlerini karşılaştırabilirsiniz. |

## Tam çalışan örnek

Aşağıda eksiksiz, bağımsız bir program yer almaktadır. `Program.cs` içine kopyalayın, dosya yollarını ayarlayın ve çalıştırın.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**Beklenen sonuç:** `big5_doc_fixed.docx` dosyasını açtığınızda, tüm Geleneksel Çince karakterler doğru şekilde render edilir, eksik glif uyarısı olmaz; çünkü `MingLiU-ExtB` `Microsoft JhengHei` ile değiştirilmiştir.

## Sonuç

Artık C# kullanarak **font substitution in document** görevleri için güvenilir bir yönteme sahipsiniz. **big5 kodlamasını** yapılandırarak, DOCX’i `LoadOptions` ile yükleyerek ve eski yazı tiplerini modern eşdeğerlerle eşleyerek, eski Çince dosyaların karşılaştığı render sorunlarını ortadan kaldırırsınız.

Bundan sonra şunları yapabilirsiniz:

* Değiştirme haritasını ek eski yazı tiplerini kapsayacak şekilde genişletin.  
* Belgeler dizini üzerinde döngü kurarak işlemi toplu hâle getirin.  
* Yazı tipi değiştirmeyi, filigran ekleme veya PDF dönüşümü gibi diğer belge dönüşümleriyle birleştirin.

Farklı hedef yazı tipleriyle denemeler yapmaktan veya tam taşınabilirlik için özel yazı tipleri gömmekten çekinmeyin. Herhangi bir sorunla karşılaşırsanız, yukarıdaki kenar‑durum tablosuna geri dönün veya gelişmiş yazı tipi yönetimi için Aspose.Words belgelerine bakın.

İyi kodlamalar!


## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımları keşfetmeniz için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Log Font Substitution Warnings – Complete Aspose.Words Guide](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Load With Encoding In Word Document](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}