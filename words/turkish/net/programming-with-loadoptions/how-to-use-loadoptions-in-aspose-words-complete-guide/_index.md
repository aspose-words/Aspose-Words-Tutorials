---
category: general
date: 2026-01-10
description: Aspose.Words'te eksik yazı tiplerini yönetmek için LoadOptions kullanımını
  öğrenin. Adım adım kod, ipuçları ve sağlam belge yükleme için en iyi uygulamalar.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: tr
og_description: Aspose.Words'ta eksik yazı tiplerini yönetmek için LoadOptions nasıl
  kullanılır. Açıklamalar ve pratik ipuçlarıyla tam, çalıştırılabilir bir örnek alın.
og_title: Aspose.Words'ta LoadOptions Nasıl Kullanılır – Tam Kılavuz
tags:
- Aspose.Words
- C#
- .NET
title: Aspose.Words'ta LoadOptions Nasıl Kullanılır – Tam Rehber
url: /tr/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words’da LoadOptions Nasıl Kullanılır – Tam Kılavuz

Hiç **LoadOptions nasıl kullanılır** sorusunu, eksik bazı yazı tiplerine sahip olabilecek bir Word belgesi yüklerken aklınıza getirdiniz mi? Bu konuda yalnız değilsiniz. Gerçek dünyadaki birçok projede belgeler farklı makineler arasında taşınıyor ve hedef sistem genellikle yazarın kullandığı tam yazı tiplerine sahip olmuyor. Sonuç? Beklenmedik yazı tipi ikameleri, düzeni bozabilir, önemli karakterleri gizleyebilir veya sadece marka tutarsızlığı yaratabilir.  

Neyse ki Aspose.Words, eksik yazı tiplerini *ele almanın* temiz bir yolunu sunuyor: bir `LoadOptions` nesnesi ve uyarı geri araması (warning callback). Bu öğreticide **LoadOptions nasıl kullanılır** öğrenerek bu yazı tipi ikameleri uyarılarını yakalayacak, kaydedecek ve iş akışınızı sağlam tutacaksınız.

Kapsam:

* Uyarı geri araması sınıfının oluşturulması  
* `LoadOptions` nesnesinin bu geri arama ile yapılandırılması  
* Eksik yazı tiplerini izlerken belgeyi yükleme  
* Sorun giderme ipuçları ve çözümün genişletilmesi  

Harici bir dokümantasyona gerek yok—gereken her şey burada.

---

## Gereksinimler

İşe başlamadan önce şunların yüklü olduğundan emin olun:

* **Aspose.Words for .NET** (2026 itibarıyla en son sürüm) NuGet üzerinden kurulu  
* Bir .NET geliştirme ortamı (Visual Studio, Rider veya VS Code)  
* Yüklü olmayan bir yazı tipine referans veren örnek bir DOCX (biz buna `input.docx` diyeceğiz)  

Hepsi bu—başka bir kütüphane gerekmiyor.

---

## Adım 1 – Yazı Tipi İkamesini Yakalamak İçin Bir Uyarı Geri Araması Tanımlayın

İlk parça, `IWarningCallback` arayüzünü uygulayan bir sınıftır. Aspose.Words, dikkate değer bir durumla (örneğin eksik bir yazı tipi) karşılaştığında `Warning` metodunu çağırır.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Neden önemli:**  
`WarningType.FontSubstitution` üzerine filtre uygulayarak alakasız uyarılardan (ör. kullanımdan kaldırılmış özellikler) kaçınırız. Geri arama size tam kontrol sağlar—dosyaya kaydedebilir, bir istisna fırlatabilir veya programatik olarak bir yedek yazı tipi eklemeyi deneyebilirsiniz.

---

## Adım 2 – Geri Aramayı Kullanarak LoadOptions’u Yapılandırın

Artık bir işleyicimiz olduğuna göre, Aspose.Words’a bunu kullanmasını söylememiz gerekir. İşte **LoadOptions nasıl kullanılır** pratiği.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**İpucu:** `LoadOptions` birçok başka ayar sunar (ör. `Password`, `LoadFormat`, `Encoding`). Bunları zincirleyebilirsiniz, ancak eksik yazı tiplerini ele alırken `WarningCallback` sahnenin yıldızıdır.

---

## Adım 3 – Yapılandırılmış Seçeneklerle Belgeyi Yükleyin

`LoadOptions` hazır olduğunda belgeyi yüklemek çok basittir. Aspose.Words, bulamadığı her yazı tipi için otomatik olarak geri aramayı tetikler.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**Beklenen çıktı:**  

`input.docx` içinde yüklü olmayan *“GothicBold”* adlı bir yazı tipi kullanılıyorsa, aşağıdaki gibi bir şey görürsünüz:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

Uyarı satırı **tam olarak eksik yazı tipiyle karşılaşıldığında** görüntülenir ve anında geri bildirim sağlar.

---

## Adım 4 – (İsteğe Bağlı) Belgeyi İşlemeye Devam Edin

Genellikle sadece dosyayı yüklemek yeterli değildir. Aşağıda, uyarı kurulumumuzla sorunsuz çalışan birkaç yaygın post‑yükleme işlemi bulabilirsiniz.

### 4.1 Belgeyi PDF Olarak Kaydedin

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 Eksik Yazı Tiplerini Bilinen Bir Yedekle Değiştirin

Belirli bir yedek (ör. *“Calibri”*) tercih ediyorsanız, kaydetmeden önce `FontSettings`i ayarlayabilirsiniz:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 Tüm Uyarıları Bir Dosyaya Kaydedin

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

Bu kod parçacıkları, **LoadOptions nasıl kullanılır** temel senaryonun ötesinde esneklik sağlar ve üretim‑ağırlıklı çözümler için uygundur.

---

## Yaygın Tuzaklar ve **Eksik Yazı Tiplerini** Zarifçe **Ele Alma** Yöntemleri

| Tuzak | Neden Oluşur | Çözüm / Önlem |
|------|--------------|---------------|
| **Geri arama eklenmemiş** | `WarningCallback` ayarlamayı unutursunuz. | Belgeyi yüklemeden önce her zaman bir `LoadOptions` nesnesi oluşturup işleyicinizi atayın. |
| **Geri arama sadece yazdırır, saklamaz** | Web servisinde konsol çıktısı kaybolur. | `Console.WriteLine` yerine bir logger (Serilog, NLog) kullanın veya kalıcı bir depoya yazın. |
| **Birden fazla eksik yazı tipi, sadece ilki raporlanır** | Geri arama ilk uyarıda istisna fırlatır. | Geri aramayı hafif tutun; gerçekten iptal etmek istiyorsanız dışarıda fırlatın. |
| **İkame edilen yazı tipi hatalı görünüyor** | Varsayılan ikame görsel olarak farklı bir font seçebilir. | `FontSettings.SubstitutionSettings.FontSubstitutionRules` ile tercih ettiğiniz yedek fontu önceliklendirin. |
| **Büyük belgelerde performans düşüşü** | Uyarı geri araması binlerce kez tetiklenir. | Uyarıları toplu olarak bir listede biriktirin ve yükleme sonrası işleyin, ya da yalnızca benzersiz font adlarını filtreleyin. |

Bu senaryolara hâkim olmak, **eksik yazı tiplerini** sürpriz olmadan yönetmenizi sağlar.

---

## Tam Çalışan Örnek – Tüm Parçalar Bir Arada

Aşağıda, tüm akışı gösteren eksiksiz, doğrudan çalıştırılabilir bir program yer alıyor. Bir konsol projesine yapıştırın, Aspose.Words NuGet paketini ekleyin ve sorunsuz çalışacaktır.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**Bu programı çalıştırdığınızda**:

1. Tüm yazı tipi ikame uyarılarını konsola yazdırır.  
2. Orijinal düzeni `output.pdf` olarak kaydeder.  
3. Yedek olarak *Calibri* veya *Arial* kullanan ikinci bir PDF (`output-with-fallback.pdf`) oluşturur.

---

## Sıkça Sorulan Sorular (SSS)

**S: Bu yöntem DOC, RTF veya HTML dosyaları için de çalışır mı?**  
C: Evet. `LoadOptions` format bağımsızdır; doğru dosya yolunu verdiğiniz sürece uyarı geri araması, desteklenen tüm formatlarda eksik yazı tipleri için tetiklenir.

**S: Uyarıları tamamen gizleyebilir miyim?**  
C: Boş bir geri arama (`new IWarningCallback { Warning = _ => {} }`) atayabilir veya `LoadOptions.WarningCallback = null` yapabilirsiniz. Ancak görünürlüğü kaybetmek, kritik font sorunlarını kaçırmanıza yol açabilir.

**S: Eksik yazı tiplerini gömülü olanlarla değiştirmek istiyorum, nasıl?**  
C: `FontSettings` ile bir yedek font dosyası ekleyin (`AddFontSource`). Bunu ikame kurallarıyla birleştirerek sorunsuz bir deneyim elde edebilirsiniz.

**S: Geri arama çoklu iş parçacığında güvenli mi?**  
C: Büyük belgeleri paralel yüklerken geri arama birden çok iş parçacığından çağrılabilir. Paylaşılan kaynakların (ör. log dosyaları) senkronize olduğundan emin olun.

---

## Sonuç

**LoadOptions nasıl kullanılır** sorusunu, **eksik yazı tiplerini** şık bir şekilde ele alacak şekilde yanıtladık. Özel bir `IWarningCallback` tanımlayarak, bunu bir `LoadOptions` nesnesine bağlayarak ve belgeyi bu seçeneklerle yükleyerek, font ikame olayları hakkında gerçek zamanlı bilgi sahibi olursunuz. Ardından uyarıları kaydedebilir, yedek fontlar ekleyebilir veya gömebilir, çıktınızın tam istediğiniz gibi görünmesini sağlayabilirsiniz.

Unutmayın, temel adımlar şunlardır:

1. `WarningType.FontSubstitution` üzerine odaklanan bir uyarı geri araması uygulayın.  
2. Bu geri aramayı bir `LoadOptions` nesnesine bağlayın.  
3. Belgeyi bu seçeneklerle yükleyin.  
4. (İsteğe bağlı) İkame kurallarını, loglamayı veya diğer işlemleri ekleyin.

Deneyin—konsol loggerını yapılandırılmış bir logger ile değiştirin, kritik eksik fontlar için e‑posta uyarıları ekleyin veya bu deseni daha büyük bir belge işleme hattına entegre edin. Yaklaşım, tek bir dosya ya da toplu işlerde binlerce dosya işlese de sorunsuz ölçeklenir.

Kodlamanın tadını çıkarın ve belgelerinizin her zaman doğru tipografiyle görüntülendiğinden emin olun!  

---

![how to use loadoptions example]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}