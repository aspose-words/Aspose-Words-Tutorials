---
"description": "Aspose.Words for .NET kullanarak biçimlendirmeyi koruyarak belgeleri nasıl içe aktaracağınızı öğrenin. Kod örnekleriyle adım adım kılavuz."
"linktitle": "Kaynak Numaralandırmasını Koru"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Kaynak Numaralandırmasını Koru"
"url": "/tr/net/join-and-append-documents/keep-source-numbering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kaynak Numaralandırmasını Koru

## giriiş

.NET için Aspose.Words ile çalışırken, biçimlendirmeyi koruyarak belgeleri bir kaynaktan diğerine aktarmak, şu şekilde verimli bir şekilde gerçekleştirilebilir: `NodeImporter` sınıf. Bu eğitim sizi adım adım süreçte yönlendirecektir.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
- Bilgisayarınızda Visual Studio yüklü.
- Aspose.Words for .NET yüklü. Eğer yüklü değilse, şuradan indirin: [Burada](https://releases.aspose.com/words/net/).
- C# ve .NET programlamanın temel bilgisi.

## Ad Alanlarını İçe Aktar

Öncelikle projenize gerekli ad alanlarını ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## Adım 1: Projenizi Kurun

Öncelikle Visual Studio'da yeni bir C# projesi oluşturun ve NuGet Paket Yöneticisi aracılığıyla Aspose.Words'ü yükleyin.

## Adım 2: Belgeleri Başlatın
Kaynak örneklerini oluşturun (`srcDoc`) ve varış noktası (`dstDoc`) belgeleri.

```csharp
// Belge dizininize giden yol 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Adım 3: İçe Aktarma Seçeneklerini Yapılandırın
Numaralandırılmış paragraflar da dahil olmak üzere kaynak biçimlendirmesini korumak için içe aktarma seçeneklerini ayarlayın.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## Adım 4: Paragrafları içe aktarın
Kaynak belgedeki paragraflar arasında gezinin ve bunları hedef belgeye aktarın.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## Adım 5: Belgeyi Kaydedin
Birleştirilen belgeyi istediğiniz yere kaydedin.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## Çözüm

Sonuç olarak, biçimlendirmeyi koruyarak belgeleri içe aktarmak için Aspose.Words for .NET'i kullanmak, aşağıdakilerle basittir: `NodeImporter` sınıf. Bu yöntem, belgelerinizin orijinal görünümünü ve yapısını sorunsuz bir şekilde korumasını sağlar.

## SSS

### Farklı biçimlendirme stillerine sahip belgeleri içe aktarabilir miyim?
Evet, `NodeImporter` sınıf, çeşitli biçimlendirme stillerine sahip belgelerin içe aktarılmasını destekler.

### Belgelerim karmaşık tablolar ve resimler içeriyorsa ne yapmalıyım?
Aspose.Words for .NET, içe aktarma işlemleri sırasında tablolar ve resimler gibi karmaşık yapıları işler.

### Aspose.Words .NET'in tüm sürümleriyle uyumlu mudur?
Aspose.Words, sorunsuz entegrasyon için .NET Framework ve .NET Core sürümlerini destekler.

### Belge aktarımı sırasında oluşan hataları nasıl çözebilirim?
İçe aktarma işlemi sırasında oluşabilecek istisnaları ele almak için try-catch bloklarını kullanın.

### Aspose.Words for .NET hakkında daha detaylı dokümanları nerede bulabilirim?
Ziyaret edin [belgeleme](https://reference.aspose.com/words/net/) kapsamlı kılavuzlar ve API referansları için.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}