---
language: tr
url: /turkish/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Aspose.Words Belgelerinde Eksik Yazı Tiplerini Algılamak – Tam C# Rehberi

Aspose.Words ile bir Word dosyasını yüklediğinizde **eksik yazı tiplerini nasıl algılayacağınızı** hiç merak ettiniz mi? Günlük işimde, orijinal belge yüklü olmayan bir yazı tipi kullandığı için birkaç PDF'nin hatalı göründüğü durumlarla karşılaştım. İyi haber? Aspose.Words, bir yazı tipini ne zaman değiştirdiğini tam olarak size söyleyebilir ve bu bilgiyi basit bir uyarı geri çağrısı (warning callback) ile yakalayabilirsiniz.  

Bu öğreticide, **tam ve çalıştırılabilir bir örnek** üzerinden her yazı tipi değişimini nasıl kaydedeceğinizi, geri çağrının neden önemli olduğunu ve sağlam eksik‑yazı tipi algılaması için birkaç ekstra ipucunu göstereceğiz. Gereksiz ayrıntı yok, sadece ihtiyacınız olan kod ve mantık, bugün çalıştırmanız için.

---

## Öğrenecekleriniz

- **Aspose.Words warning callback**'i uygulayarak yazı tipi değişim olaylarını yakalama.  
- **LoadOptions C#**'ı yapılandırarak belge yüklenirken geri çağrının tetiklenmesini sağlama.  
- Eksik‑yazı tipi algılamasının gerçekten çalıştığını doğrulama ve konsol çıktısının nasıl göründüğünü anlama.  
- Büyük toplular veya başsız (headless) ortamlar için isteğe bağlı ayarlamalar.  

**Önkoşullar** – .NET 6 veya üzeri, temel C# bilgisi ve Aspose.Words for .NET'in (kod 23.12 ile test edilmiştir) güncel bir sürümüne ihtiyacınız var. Bu koşullara sahipseniz, hemen başlayabilirsiniz.

---

## Eksik Yazı Tiplerini Uyarı Geri Çağrısı ile Algılamak

Çözümün kalbi, `IWarningCallback` uygulamasıdır. Aspose.Words birçok durum için bir `WarningInfo` nesnesi yayar, ancak biz sadece `WarningType.FontSubstitution` ile ilgileniyoruz. Şimdi bunu nasıl bağlayacağımıza bakalım.

### Adım 1: Bir Font‑Uyarı Toplayıcı Oluşturun

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Bu neden önemli*: `WarningType.FontSubstitution` üzerinden filtreleme yaparak alakasız uyarılardan (örneğin kullanımdan kaldırılmış özellikler) kaynaklanan gürültüyü önlüyoruz. `info.Description` zaten orijinal yazı tipi adını ve kullanılan yedek yazı tipini içeriyor, bu da size net bir denetim izi sağlıyor.

---

## Geri Çağrıyı Kullanmak İçin LoadOptions'ı Yapılandırın

Şimdi Aspose.Words'e dosya yüklerken toplama aracımızı kullanmasını söyleyelim.

### Adım 2: LoadOptions'ı Ayarlayın

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Bu neden önemli*: `LoadOptions`, geri çağrıyı, şifreleme parolalarını ve diğer yükleme davranışlarını takabileceğiniz tek yerdir. `Document` yapıcıdan ayrı tutmak, kodun birçok dosya için yeniden kullanılabilir olmasını sağlar.

---

## Belgeyi Yükleyin ve Eksik Yazı Tiplerini Yakalayın

Geri çağrı bağlandıktan sonra tek yapmanız gereken belgeyi yüklemek.

### Adım 3: DOCX'inizi (veya desteklenen herhangi bir formatı) Yükleyin

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

`Document` yapıcı dosyayı ayrıştırdığında, eksik bir yazı tipi bizim `FontWarningCollector`'ımızı tetikler. Konsolda aşağıdaki gibi satırlar göreceksiniz:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Bu satır, **eksik yazı tiplerini algılamanın** çalıştığının somut kanıtıdır.

---

## Çıktıyı Doğrulama – Ne Beklemelisiniz

Programı bir terminalden ya da Visual Studio'dan çalıştırın. Kaynak belge yüklü olmayan bir yazı tipi içeriyorsa, en az bir “Font substituted” satırı göreceksiniz. Belge yalnızca yüklü yazı tipleri kullanıyorsa, geri çağrı sessiz kalır ve sadece “Document loaded successfully.” mesajını alırsınız.

**İpucu**: Çift kontrol için Word dosyasını Microsoft Word'de açın ve yazı tipi listesini inceleyin. *Home → Font* grubundaki *Replace Fonts* altında görünen herhangi bir yazı tipi, değişim adayıdır.

---

## İleri Seviye: Toplu Olarak Eksik Yazı Tiplerini Algılamak

Çoğu zaman onlarca dosyayı taramanız gerekir. Aynı desen büyük ölçekte de sorunsuz çalışır:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

`FontWarningCollector` her tetiklendiğinde konsola yazdığından, ekstra bir altyapı eklemeden dosya başına rapor alırsınız. Üretim senaryolarında çıktıyı bir dosyaya ya da veritabanına yönlendirmek isteyebilirsiniz – sadece `Console.WriteLine` ifadesini tercih ettiğiniz logger ile değiştirin.

---

## Yaygın Tuzaklar & Profesyonel İpuçları

| Sorun | Neden Oluşur | Çözüm |
|-------|--------------|-------|
| **Uyarı çıkmaz** | Belge aslında yalnızca yüklü yazı tiplerini içeriyor. | Word'de dosyayı açarak ya da sisteminizden kasıtlı olarak bir yazı tipini kaldırarak doğrulayın. |
| **Geri çağrı çalışmaz** | `LoadOptions.WarningCallback` hiç atanmadı ya da daha sonra yeni bir `LoadOptions` örneği kullanıldı. | Tek bir `LoadOptions` nesnesi tutun ve her yüklemede aynı nesneyi yeniden kullanın. |
| **Alakalı olmayan çok fazla uyarı** | `WarningType.FontSubstitution` ile filtreleme yapmadınız. | Gösterildiği gibi `if (info.Type == WarningType.FontSubstitution)` koşulunu ekleyin. |
| **Büyük dosyalarda performans düşüşü** | Geri çağrı her uyarıda çalışıyor, büyük belgelerde bu sayısı artabiliyor. | Diğer uyarı türlerini `LoadOptions.WarningCallback` üzerinden devre dışı bırakın veya dosyanın tipini biliyorsanız `LoadOptions.LoadFormat`'ı belirli bir tipe ayarlayın. |

---

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Beklenen konsol çıktısı** (eksik bir yazı tipiyle karşılaşıldığında):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Değişim gerçekleşmezse sadece başarı satırını göreceksiniz.

---

## Sonuç

Artık **herhangi bir belgeyi Aspose.Words ile işlerken eksik yazı tiplerini algılamak** için tam, üretim‑hazır bir yönteme sahipsiniz. **Aspose.Words warning callback**'i ve **LoadOptions C#** yapılandırmasını kullanarak her yazı tipi değişimini kaydedebilir, düzen sorunlarını tespit edebilir ve PDF'lerinizin istenen görünümünü koruyabilirsiniz.  

Tek bir dosyadan büyük bir toplu işleme kadar desen aynı kalır—`IWarningCallback`'i uygulayın, `LoadOptions`'a takın ve Aspose.Words'ün ağır işini yapmasına izin verin.  

Bir sonraki adım için ne yapacaksınız? Bu yöntemi **yazı tipi gömme** veya **yedek yazı tipi aileleri** ile birleştirerek sorunu otomatik olarak çözebilir, ya da daha derin içerik analizi için **DocumentVisitor** API'sini keşfedebilirsiniz. Kodlamanın tadını çıkarın, ve tüm yazı tipleriniz her zaman beklendiği gibi olsun!  

---

![Aspose.Words'ta eksik yazı tiplerini algılamak – konsol çıktısı ekran görüntüsü](https://example.com/images/detect-missing-fonts.png "eksik yazı tiplerini algılayan konsol çıktısı")

{{< layout-end >}}

{{< layout-end >}}