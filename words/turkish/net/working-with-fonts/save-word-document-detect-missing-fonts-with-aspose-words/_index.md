---
category: general
date: 2026-03-22
description: Aspose.Words kullanarak Word belgesini kaydedin ve eksik yazı tiplerini
  tespit edin. Eksik yazı tiplerini nasıl izleyebileceğinizi ve C#’ta yazı tipi hatalarını
  nasıl yakalayabileceğinizi öğrenin.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: tr
og_description: Word Belgesini kaydedin ve C#'ta eksik yazı tiplerini tespit edin.
  Bu kılavuz, eksik yazı tiplerini izlemeyi ve bir uyarı geri çağrısı kullanarak yazı
  tipi hatalarını yakalamayı gösterir.
og_title: Word Belgesini Kaydet – Aspose.Words ile Eksik Yazı Tiplerini Tespit Et
tags:
- Aspose.Words
- C#
- Document Processing
title: Word Belgesini Kaydet – Aspose.Words ile Eksik Yazı Tiplerini Tespit Et
url: /tr/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesini Kaydet – Aspose.Words ile Eksik Yazı Tiplerini Algıla

Hiç **Word belgesini kaydet**meniz gerekti, ancak içindeki bazı yazı tiplerinin bu dönüşümde hayatta kalıp kalmayacağından emin olmadınız mı? Bu, düşündüğünüzden daha sık olur, özellikle belgeler farklı yazı tipi kütüphanelerine sahip makineler arasında taşındığında. İyi haber? Aspose.Words, **Word belgesini kaydederken eksik yazı tiplerini algılamanın** yerleşik bir yolunu sunar, böylece dosya bir kullanıcının ekranına ulaşmadan önce kaydedebilir, uyarı verebilir veya hatta değiştirebilirsiniz.

Bu öğreticide, yalnızca bir Word belgesini kaydetmekle kalmayıp aynı zamanda **eksik yazı tiplerini izler** ve **yazı tipi hatalarını yakalar** özel bir uyarı işleyicisi kullanarak tam, çalıştırmaya hazır bir örnek üzerinden ilerleyeceğiz. Sonuna kadar uyarı geri çağrısının neden önemli olduğunu, nasıl bağlanacağını ve bir ikame gerçekleştiğinde konsol çıktısının nasıl göründüğünü tam olarak öğreneceksiniz.  
Ekstra süsleme yok—şu anda bir .NET projesine ekleyebileceğiniz kod.

> **Önkoşullar**  
> • .NET 6 (veya herhangi bir yeni .NET Framework) yüklü  
> • Visual Studio 2022 veya tercih ettiğiniz IDE  
> • **Aspose.Words for .NET** lisanslı bir kopya (ücretsiz deneme sürümü test için çalışır)  

Eğer bunlara sahipseniz, başlayalım.

---

## Word Belgesini Kaydet ve Eksik Yazı Tiplerini Algıla

Temel fikir basit: `Document.Save` metodunu çağırmadan önce, `IWarningCallback` arayüzünü uygulayan bir nesneyi `Document.WarningCallback` özelliğine atayın. Aspose.Words, sisteminizin bulamadığı bir yazı tipine kaynak belge referans verdiğinde ortaya çıkan **yazı tipi ikamesi** uyarıları da dahil olmak üzere karşılaştığı her uyarı için bu nesneyi çalıştırır.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**Görmeyi bekleyecekleriniz:**  
`input.docx` bir yazı tipine referans veriyor ve bu yazı tipi yüklü değilse, konsol şu şekilde bir şey yazdırır:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Bu satır, tam olarak hangi yazı tipinin eksik olduğunu ve Aspose.Words'un bunun yerine ne kullandığını gösterir—dosyayı dağıtmadan önce **yazı tipi hatalarını yakalamak** için mükemmeldir.

---

## Uyarı Geri Çağrısı ile Eksik Yazı Tiplerini İzleme (Adım‑Adım)

### 1️⃣ Aspose.Words'u Kurun

Projenizin NuGet konsolunu açın ve şu komutu çalıştırın:

```bash
dotnet add package Aspose.Words
```

Bu, en son kararlı sürümü (şu anda 24.10) çeker. Kütüphaneyi güncel tutmak, en yeni **eksik yazı tiplerini algıla** yeteneklerini ve hata düzeltmelerini almanızı sağlar.

### 2️⃣ Uyarı İşleyicisini Tanımlayın

Neden ayrı bir sınıfa ihtiyacımız var? `IWarningCallback`'i uygulamak, tüm uyarı mantığını tek bir yerde merkezileştirmenizi sağlar. Ayrıca bir dosyaya kaydedebilir, telemetri gönderebilir veya eksik bir yazı tipi iş akışınız için kritik bir hata ise bir istisna fırlatabilirsiniz.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Pro ipucu:** Birçok belge boyunca **eksik yazı tiplerini izlemek** istiyorsanız, mesajları işleyicinin içinde bir `List<string>` içinde saklayın ve raporlama için daha sonra dışa aktarın.

### 3️⃣ Kaynak Belgenizi Yükleyin

`Document` yapıcı metodu bir dosya yolu, bir akış (stream) ya da ham baytları kabul edebilir. Çoğu durumda, bir kullanıcıdan ya da başka bir sistemden aldığınız bir `.docx` dosyasına işaret edeceksiniz.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Dosya büyükse, bellek baskısını azaltmak için tembel yüklemeyi (lazy loading) etkinleştiren `LoadOptions` kullanmayı düşünün.

### 4️⃣ Geri Çağrıyı Bağlayın

Örneği `doc.WarningCallback`'e atayın. Bu noktadan itibaren, her uyarı (yazı tipi ikameleri dahil) işleyiciniz üzerinden geçecektir.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Belgeyi Kaydedin

Şimdi güvenle `Save` metodunu çağırabilirsiniz. Uyarı işleyicisi, kaydetme işlemi sırasında **senkron** olarak çalışır, bu yüzden çıktıyı hemen görürsünüz.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Farklı bir formata (PDF, HTML, vb.) kaydetmeyi tercih ederseniz, aynı uyarı mekanizması çalışır—Aspose.Words, dönüşümden önce hâlâ eksik yazı tiplerini raporlayacaktır.

---

## Yazı Tipi Hatalarını Yakalama – Yaygın Kenar Durumları

Temel akış çoğu senaryoyu kapsasa da, gerçek dünya projeleri genellikle birkaç sorunla karşılaşır. Aşağıda karşılaşabileceğiniz bazı varyasyonlar ve bunları nasıl ele alacağınız yer alıyor.

### Başlık/Alt Bilgide Eksik Yazı Tipi

Başlık ve alt bilgiler ayrı düğümlerdir, ancak uyarı sistemi onları gövde metniyle aynı şekilde ele alır. Ek bir kod gerekmez; geri çağrı bu yazı tipleri için de tetiklenir. Sadece tam belgeyi yüklediğinizden emin olun (varsayılan davranış bunu yapar).

### Tek Bir Belgede Birden Çok İkame

Bir belge birden fazla bilinmeyen yazı tipi kullanıyorsa, işleyici her ikame için bir kez çağrılır. Konsolu doldurmayı önlemek için mesajları tekilleştirebilirsiniz:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Uyarıları İstisnalara Dönüştürme

Bazen eksik bir yazı tipi kabul edilemez bir durum olur. Kaydetmeyi iptal etmek için işleyicinin içinde bir istisna fırlatın:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

`doc.Save` metodunu bir `try/catch` bloğuna sararak istisnayı nazikçe ele almayı unutmayın.

---

## Sonucu Doğrulama – Ne Beklenir

Kaydetme tamamlandıktan sonra, `output.docx` dosyasını Microsoft Word'de (veya uyumlu bir görüntüleyicide) açın. Orijinaliyle aynı görsel düzeni görmelisiniz, ancak ikame edilen yazı tipleri konsolda gördüğünüz yedek (fallback) olarak görünecektir. Çift kontrol için şunları yapabilirsiniz:

1. **File → Options → Advanced → Show document content → Use draft quality**'yi açın – bu, Word'ün gizli yazı tipi ikamelerini ortaya çıkarmasını sağlar.  
2. Word'ün **Replace Fonts** iletişim kutusunu (`Ctrl+Shift+F`) kullanarak hangi yazı tiplerinin gerçekten gömülü olduğunu görün.

Her şey uyuyorsa, **Word belgesini kaydetmiş** ve **eksik yazı tiplerini algılamış** ve **yazı tipi hatalarını yakalamış** olursunuz. 🎉

---

## Tam Çalışan Örnek (Kopyala‑Yapıştır Hazır)

Aşağıda, yeni bir Console App projesine ekleyebileceğiniz tüm program yer alıyor. `YOUR_DIRECTORY` ifadesini makinenizdeki gerçek bir klasör yolu ile değiştirin.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Beklenen konsol çıktısı** (örnek):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

Bu kadar—gizli adım yok, peşinde koşmanız gereken dış doküman yok.

---

## Sonuç

Size, Aspose.Words'un uyarı geri çağrısını kullanarak **Word belgesini kaydetme** sırasında aktif bir şekilde **eksik yazı tiplerini algılama**, **eksik yazı tiplerini izleme** ve **yazı tipi hatalarını yakalama** yöntemini gösterdik. Küçük bir `IWarningCallback` uygulaması bağlayarak, kaydetme sırasında yazı tipi ikameleri hakkında tam görünürlük elde eder, böylece ihtiyacınıza göre kaydetmeyi loglayabilir, değiştirebilir veya iptal edebilirsiniz.

Bir sonraki meydan okumaya hazır mısınız? İşleyiciyi, uyarıları yapılandırılmış bir JSON günlüğüne yazacak şekilde genişletmeyi deneyin ya da aynı belgeyi font bilgilerini koruyarak dönüştürmek için Aspose.PDF ile birleştirin. Ayrıca eksik yazı tiplerini doğrudan çıktı dosyasına gömmeyi de keşfedebilirsiniz—Aspose.Words, `LoadOptions.FontSettings` aracılığıyla yazı tipi gömme desteği sunar.

Deneyin, kodu kendi pipeline'ınıza göre ayarlayın ve nasıl çalıştığını bize bildirin. Kodlamanın tadını çıkarın!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}