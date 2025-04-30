---
"description": "Aspose.Words for .NET kullanarak Word belgelerini birleştirirken farklı sayfa yapılandırmalarının nasıl ayarlanacağını öğrenin. Adım adım kılavuz dahildir."
"linktitle": "Farklı Sayfa Düzeni"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Farklı Sayfa Düzeni"
"url": "/tr/net/join-and-append-documents/different-page-setup/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Farklı Sayfa Düzeni

## giriiş

Merhaba! Aspose.Words for .NET ile belge düzenlemenin büyüleyici dünyasına dalmaya hazır mısınız? Bugün, oldukça şık bir şeyle uğraşıyoruz: Word belgelerini birleştirirken farklı sayfa düzenleri kurmak. İster raporları birleştirin, ister bir roman yazın veya sadece eğlence için belgelerle uğraşın, bu kılavuz sizi adım adım yönlendirecek. Başlayalım!

## Ön koşullar

İşin içine girmeden önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1. Aspose.Words for .NET: Aspose.Words for .NET'in yüklü olduğundan emin olun. [buradan indirin](https://releases.aspose.com/words/net/).
2. .NET Framework: Aspose.Words for .NET'i destekleyen herhangi bir sürüm.
3. Geliştirme Ortamı: Visual Studio veya herhangi bir .NET uyumlu IDE.
4. Temel C# Bilgisi: Sadece söz dizimi ve yapıyı anlamak için gereken temel bilgiler.

## Ad Alanlarını İçe Aktar

Öncelikle, C# projenize gerekli ad alanlarını içe aktaralım. Bu ad alanları, Aspose.Words'ün özelliklerine erişmek için çok önemlidir.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.Tables;
```

Tamam, meselenin özüne gelelim. Tüm süreci takip etmesi kolay adımlara böleceğiz.

## Adım 1: Projenizi Kurun

### Adım 1.1: Yeni Bir Proje Oluşturun

Visual Studio'yu başlatın ve yeni bir C# Konsol Uygulaması oluşturun. "DifferentPageSetupExample" gibi havalı bir isim verin.

### Adım 1.2: Aspose.Words Referansını Ekleyin

Aspose.Words'ü kullanmak için onu projenize eklemeniz gerekir. Henüz yapmadıysanız, Aspose.Words for .NET paketini indirin. Aşağıdaki komutla NuGet Paket Yöneticisi üzerinden yükleyebilirsiniz:

```bash
Install-Package Aspose.Words
```

## Adım 2: Belgeleri Yükleyin

Şimdi, birleştirmek istediğimiz belgeleri yükleyelim. Bu örnek için iki Word belgesine ihtiyacınız olacak: `Document source.docx` Ve `Northwind traders.docx`Bu dosyaların proje dizininizde olduğundan emin olun.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Adım 3: Kaynak Belge için Sayfa Kurulumunu Yapılandırın

Kaynak belgenin sayfa düzeninin hedef belgeyle eşleştiğinden emin olmamız gerekir. Bu adım, kusursuz bir birleştirme için çok önemlidir.

### Adım 3.1: Hedef Belgeden Sonra Devam Et

Kaynak belgenin hedef belgeden hemen sonra devam etmesini ayarlayın.

```csharp
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

### Adım 3.2: Sayfa Numaralandırmasını Yeniden Başlatın

Sayfa numaralandırmasını kaynak belgenin başından yeniden başlatın.

```csharp
srcDoc.FirstSection.PageSetup.RestartPageNumbering = true;
srcDoc.FirstSection.PageSetup.PageStartingNumber = 1;
```

## Adım 4: Sayfa Kurulum Ayarlarını Eşleştirin

Herhangi bir düzen tutarsızlığını önlemek için kaynak belgenin ilk bölümündeki sayfa düzeni ayarlarının hedef belgenin son bölümündeki ayarlarla eşleştiğinden emin olun.

```csharp
srcDoc.FirstSection.PageSetup.PageWidth = dstDoc.LastSection.PageSetup.PageWidth;
srcDoc.FirstSection.PageSetup.PageHeight = dstDoc.LastSection.PageSetup.PageHeight;
srcDoc.FirstSection.PageSetup.Orientation = dstDoc.LastSection.PageSetup.Orientation;
```

## Adım 5: Paragraf Biçimlendirmesini Ayarlayın

Akışın düzgün olmasını sağlamak için kaynak belgedeki paragraf biçimlendirmesini ayarlamamız gerekiyor.

Kaynak belgedeki tüm paragrafları yineleyin ve ayarlayın `KeepWithNext` mülk.

```csharp
foreach (Paragraph para in srcDoc.GetChildNodes(NodeType.Paragraph, true))
{
    para.ParagraphFormat.KeepWithNext = true;
}
```

## Adım 6: Kaynak Belgeyi Ekleyin

Son olarak, orijinal biçimlendirmenin korunduğundan emin olarak kaynak belgeyi hedef belgeye ekleyin.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Adım 7: Birleştirilmiş Belgeyi Kaydedin

Şimdi güzelce birleştirilmiş belgenizi kaydedin.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.DifferentPageSetup.docx");
```

## Çözüm

Ve işte karşınızda! Aspose.Words for .NET kullanarak farklı sayfa düzenlerine sahip iki Word belgesini birleştirdiniz. Bu güçlü kütüphane, belgeleri programatik olarak yönetmeyi oldukça kolaylaştırır. Karmaşık raporlar oluşturuyor, kitaplar bir araya getiriyor veya çok bölümlü belgeleri yönetiyor olun, Aspose.Words sizin yanınızda.

## SSS

### Bu yöntemi iki belgeden fazlasında kullanabilir miyim?
Kesinlikle! Birleştirmek istediğiniz her ek belge için adımları tekrarlamanız yeterlidir.

### Belgelerimin kenar boşlukları farklıysa ne olur?
Sayfa genişliğini, yüksekliğini ve yönünü eşleştirdiğimiz gibi kenar boşluğu ayarlarını da eşleştirebilirsiniz.

### Aspose.Words .NET Core ile uyumlu mu?
Evet, Aspose.Words for .NET, .NET Core ile tam uyumludur.

### Her iki belgenin stillerini koruyabilir miyim?
Evet, `ImportFormatMode.KeepSourceFormatting` seçeneği kaynak belgedeki stillerin korunmasını sağlar.

### Aspose.Words ile ilgili daha fazla yardımı nereden alabilirim?
Şuna bir göz atın: [Aspose.Words belgeleri](https://reference.aspose.com/words/net/) veya ziyaret edin [destek forumu](https://forum.aspose.com/c/words/8) Daha fazla yardım için.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}