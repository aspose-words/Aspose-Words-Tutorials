---
"description": "Aspose.Words for .NET kullanarak Word'e İçindekiler Tablosu eklemeyi öğrenin. Sorunsuz belge gezintisi için adım adım kılavuzumuzu izleyin."
"linktitle": "Word Belgesine İçindekiler Tablosu Ekle"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Word Belgesine İçindekiler Tablosu Ekle"
"url": "/tr/net/add-content-using-documentbuilder/insert-table-of-contents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesine İçindekiler Tablosu Ekle

## giriiş
Bu eğitimde, Aspose.Words for .NET kullanarak Word belgelerinize İçindekiler Tablosu'nu (TOC) nasıl etkili bir şekilde ekleyeceğinizi öğreneceksiniz. Bu özellik, uzun belgeleri düzenlemek ve gezinmek, okunabilirliği artırmak ve belge bölümlerine hızlı bir genel bakış sağlamak için önemlidir.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

- C# ve .NET framework'üne dair temel bilgi.
- Bilgisayarınızda Visual Studio yüklü.
- Aspose.Words for .NET kütüphanesi. Eğer henüz yüklemediyseniz, şuradan indirebilirsiniz: [Burada](https://releases.aspose.com/words/net/).

## Ad Alanlarını İçe Aktar

Başlamak için, gerekli ad alanlarını C# projenize aktarın:

```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

Süreci net adımlara bölelim:

## Adım 1: Aspose.Words Belgesini ve DocumentBuilder'ı Başlatın

İlk olarak yeni bir Aspose.Words başlatın `Document` nesne ve bir `DocumentBuilder` çalışmak için:

```csharp
// Belgeyi ve DocumentBuilder'ı Başlat
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 2: İçindekiler Tablosunu Ekleyin

Şimdi, İçindekiler Tablosunu şunu kullanarak ekleyin: `InsertTableOfContents` yöntem:

```csharp
// İçindekiler Tablosunu Ekle
builder.InsertTableOfContents("\\o \"1-3\" \\h \\z \\u");
```

## Adım 3: Belge İçeriğini Yeni Bir Sayfada Başlatın

Doğru biçimlendirmeyi sağlamak için gerçek belge içeriğini yeni bir sayfada başlatın:

```csharp
// Bir sayfa sonu ekle
builder.InsertBreak(BreakType.PageBreak);
```

## Adım 4: Belgenizi Başlıklarla Yapılandırın

Uygun başlık stillerini kullanarak belgenizin içeriğini düzenleyin:

```csharp
// Başlık stilleri ayarla
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 1.1");
builder.Writeln("Heading 1.2");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 2");
builder.Writeln("Heading 3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading3;
builder.Writeln("Heading 3.1.1");
builder.Writeln("Heading 3.1.2");
builder.Writeln("Heading 3.1.3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.2");
builder.Writeln("Heading 3.3");
```

## Adım 5: İçindekiler Tablosunu Güncelleyin ve Doldurun

İçindekiler tablosunu belge yapısını yansıtacak şekilde güncelleyin:

```csharp
// İçindekiler alanlarını güncelleyin
doc.UpdateFields();
```

## Adım 6: Belgeyi Kaydedin

Son olarak belgenizi belirtilen dizine kaydedin:

```csharp
// Belgeyi kaydet
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
doc.Save(dataDir + "InsertTableOfContentsUsingAsposeWords.docx");
```

## Çözüm

Aspose.Words for .NET kullanarak İçindekiler Tablosu eklemek basittir ve belgelerinizin kullanılabilirliğini önemli ölçüde artırır. Bu adımları izleyerek karmaşık belgeleri etkili bir şekilde düzenleyebilir ve bunlar arasında gezinebilirsiniz.

## SSS

### İçindekiler bölümünün görünümünü özelleştirebilir miyim?
Evet, Aspose.Words for .NET API'lerini kullanarak İçindekiler tablosunun görünümünü ve davranışını özelleştirebilirsiniz.

### Aspose.Words alanların otomatik olarak güncellenmesini destekliyor mu?
Evet, Aspose.Words, belgedeki değişikliklere bağlı olarak İçindekiler gibi alanları dinamik olarak güncellemenize olanak tanır.

### Tek bir belgede birden fazla İçindekiler Tablosu oluşturabilir miyim?
Aspose.Words, tek bir belge içerisinde farklı ayarlara sahip birden fazla İçindekiler Tablosu oluşturulmasını destekler.

### Aspose.Words Microsoft Word'ün farklı sürümleriyle uyumlu mudur?
Evet, Aspose.Words Microsoft Word formatlarının çeşitli sürümleriyle uyumluluğu garanti eder.

### Aspose.Words için daha fazla yardım ve desteği nerede bulabilirim?
Daha fazla yardım için şu adresi ziyaret edin: [Aspose.Words Forum](https://forum.aspose.com/c/words/8) veya kontrol edin [resmi belgeler](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}