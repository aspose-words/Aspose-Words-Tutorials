---
"description": "Aspose.Words for .NET kullanarak tekrarlayan tablo başlığı satırlarına sahip Word belgelerinin nasıl oluşturulacağını öğrenin. Profesyonel ve cilalı belgeler sağlamak için bu kılavuzu izleyin."
"linktitle": "Sonraki Sayfalarda Satırları Tekrarla"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Sonraki Sayfalarda Satırları Tekrarla"
"url": "/tr/net/programming-with-tables/repeat-rows-on-subsequent-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sonraki Sayfalarda Satırları Tekrarla

## giriiş

Programatik olarak bir Word belgesi oluşturmak, özellikle birden fazla sayfada biçimlendirmeyi korumanız gerektiğinde, göz korkutucu bir görev olabilir. Word'de bir tablo oluşturmayı denediniz mi, ancak başlık satırlarınızın sonraki sayfalarda tekrarlanmadığını fark ettiniz mi? Korkmayın! .NET için Aspose.Words ile, tablo başlıklarınızın her sayfada tekrarlanmasını kolayca sağlayabilir ve belgelerinize profesyonel ve cilalı bir görünüm kazandırabilirsiniz. Bu eğitimde, basit kod örnekleri ve ayrıntılı açıklamalar kullanarak bunu başarmak için gereken adımlarda size yol göstereceğiz. Hadi başlayalım!

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. Aspose.Words for .NET: İndirebilirsiniz [Burada](https://releases.aspose.com/words/net/).
2. Bilgisayarınızda .NET Framework yüklü olmalıdır.
3. Visual Studio veya .NET geliştirmeyi destekleyen herhangi bir IDE.
4. C# programlamanın temel bilgisi.

Devam etmeden önce Aspose.Words for .NET'i yüklediğinizden ve geliştirme ortamınızı ayarladığınızdan emin olun.

## Ad Alanlarını İçe Aktar

Başlamak için, projenize gerekli ad alanlarını içe aktarmanız gerekir. Aşağıdaki using yönergelerini C# dosyanızın en üstüne ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Bu ad alanları, Word belgelerini ve tablolarını yönetmek için gereken sınıfları ve yöntemleri içerir.

## Adım 1: Belgeyi Başlatın

İlk olarak yeni bir Word belgesi oluşturalım ve `DocumentBuilder` masamızı oluşturmak için.

```csharp
// Belge dizininize giden yol 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Bu kod yeni bir belgeyi başlatır ve `DocumentBuilder` Belge yapısının oluşturulmasına yardımcı olan nesne.

## Adım 2: Tabloyu Başlatın ve Başlık Satırlarını Tanımlayın

Daha sonra tabloyu başlatacağız ve sonraki sayfalarda tekrarlanmasını istediğimiz başlık satırlarını tanımlayacağız.

```csharp
builder.StartTable();
builder.RowFormat.HeadingFormat = true;
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.CellFormat.Width = 100;

builder.InsertCell();
builder.Writeln("Heading row 1");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Heading row 2");
builder.EndRow();
```

Burada yeni bir tablo başlatıyoruz, `HeadingFormat` mülk `true` satırların başlık olduğunu belirtmek ve hücrelerin hizalamasını ve genişliğini tanımlamak için kullanılır.

## Adım 3: Tabloya Veri Satırları Ekleyin

Şimdi tablomuza birden fazla veri satırı ekleyeceğiz. Bu satırlar sonraki sayfalarda tekrarlanmayacak.

```csharp
builder.CellFormat.Width = 50;
builder.ParagraphFormat.ClearFormatting();
for (int i = 0; i < 50; i++)
{
    builder.InsertCell();
    builder.RowFormat.HeadingFormat = false;
    builder.Write("Column 1 Text");
    
    builder.InsertCell();
    builder.Write("Column 2 Text");
    builder.EndRow();
}
```

Bu döngü, her satırda iki sütun olacak şekilde tabloya 50 satır veri ekler. `HeadingFormat` ayarlandı `false` bu satırlar için, çünkü bunlar başlık satırları değil.

## Adım 4: Belgeyi Kaydedin

Son olarak belgeyi belirtilen dizine kaydediyoruz.

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

Bu, belgeyi belirtilen adla belge dizininize kaydeder.

## Çözüm

Ve işte karşınızda! Sadece birkaç satır kodla, Aspose.Words for .NET kullanarak, sonraki sayfalarda tekrar eden başlık satırları olan tablolar içeren bir Word belgesi oluşturabilirsiniz. Bu, yalnızca belgelerinizin okunabilirliğini artırmakla kalmaz, aynı zamanda tutarlı ve profesyonel bir görünüm de sağlar. Şimdi, devam edin ve bunu projelerinizde deneyin!

## SSS

### Başlık satırlarını daha fazla özelleştirebilir miyim?
Evet, başlık satırlarına ek biçimlendirme uygulayabilirsiniz. `ParagraphFormat`, `RowFormat`, Ve `CellFormat`.

### Tabloya daha fazla sütun eklemek mümkün müdür?
Kesinlikle! Daha fazla hücre ekleyerek ihtiyaç duyduğunuz kadar sütun ekleyebilirsiniz. `InsertCell` yöntem.

### Diğer satırların sonraki sayfalarda tekrarlanmasını nasıl sağlayabilirim?
Herhangi bir satırın tekrarlanmasını sağlamak için, `RowFormat.HeadingFormat` mülk `true` o belirli satır için.

### Bu yöntemi bir belgedeki mevcut tablolar için kullanabilir miyim?
Evet, mevcut tablolara erişerek bunları değiştirebilirsiniz. `Document` nesne ve benzer biçimlendirmeyi uygulama.

### Aspose.Words for .NET'te başka hangi tablo biçimlendirme seçenekleri mevcuttur?
Aspose.Words for .NET, hücre birleştirme, kenarlık ayarları ve tablo hizalaması dahil olmak üzere çok çeşitli tablo biçimlendirme seçenekleri sunar. Şuraya göz atın: [belgeleme](https://reference.aspose.com/words/net/) Daha detaylı bilgi için.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}