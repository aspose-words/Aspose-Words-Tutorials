---
title: Bölünmüş Tablo
linktitle: Bölünmüş Tablo
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgelerindeki tabloları nasıl böleceğinizi öğrenin. Adım adım kılavuzumuz tablo yönetimini kolay ve verimli hale getirir.
weight: 10
url: /tr/net/programming-with-tables/split-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bölünmüş Tablo

## giriiş

Hiç Word belgesinde büyük bir tabloyla çalışırken buldunuz ve bunu iki küçük, daha yönetilebilir tabloya bölebilmeyi istediniz mi? Bugün, bunu Aspose.Words for .NET kullanarak tam olarak nasıl başarabileceğinizi ele alacağız. İster kapsamlı veri tablolarıyla ister karmaşık belge yapılarıyla uğraşıyor olun, tabloları bölmek okunabilirliği ve organizasyonu artırmaya yardımcı olabilir. Aspose.Words for .NET kullanarak bir tabloyu bölmek için adım adım süreci inceleyelim.

## Ön koşullar

Eğitime başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  Aspose.Words for .NET Kütüphanesi: Aspose.Words for .NET kütüphanesini indirip kurduğunuzdan emin olun. Bunu şu adresten edinebilirsiniz:[Aspose sürüm sayfası](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio gibi .NET Framework desteği olan bir geliştirme ortamı kurun.
3. Örnek Belge: Bir Word belgesi hazırlayın (`Tables.docx`) bölme işlemini uygulayacak en az bir tabloya sahip olmalıdır.

## Ad Alanlarını İçe Aktar

Öncelikle projenize gerekli namespace'leri import edin. Bu, Aspose.Words tarafından sağlanan sınıflara ve metodlara erişmenizi sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Adım 1: Belgeyi Yükleyin

Bölmek istediğiniz tabloyu içeren belgeyi yükleyerek başlayalım. Belgenize doğru yolu belirttiğinizden emin olun.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

## Adım 2: Bölünecek Tabloyu Belirleyin

Sonra, bölmek istediğiniz tabloyu tanımlayın ve alın. Bu örnekte, belgedeki ilk tabloyu hedefleyeceğiz.

```csharp
Table firstTable = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## Adım 3: Bölmek İçin Satırı Seçin

Tabloyu bölmek istediğiniz satırı belirleyin. Burada, tabloyu üçüncü satırdan (dahil) bölüyoruz.

```csharp
Row row = firstTable.Rows[2];
```

## Adım 4: Yeni Bir Tablo Konteyneri Oluşturun

Orijinal tablodan taşınacak satırları tutacak yeni bir tablo kabı oluşturun.

```csharp
Table table = (Table)firstTable.Clone(false);
```

## Adım 5: Yeni Tablo Konteynerini Ekleyin

Yeni tablo kapsayıcısını belgedeki orijinal tablonun hemen sonrasına ekleyin.

```csharp
firstTable.ParentNode.InsertAfter(table, firstTable);
```

## Adım 6: Bir Arabellek Paragrafı Ekleyin

İki tablonun ayrı kalmasını sağlamak için aralarına bir paragraf ekleyin.

```csharp
firstTable.ParentNode.InsertAfter(new Paragraph(doc), firstTable);
```

## Adım 7: Satırları Yeni Tabloya Taşı

Satırları orijinal tablodan yeni tablo kabına taşıyın. Bu döngü belirtilen satır (dahil) taşınana kadar devam eder.

```csharp
Row currentRow;
do
{
    currentRow = firstTable.LastRow;
    table.PrependChild(currentRow);
} while (currentRow != row);
```

## Adım 8: Belgeyi Kaydedin

Son olarak, değiştirilen belgeyi tabloları bölerek kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithTables.SplitTable.docx");
```

## Çözüm

İşte karşınızda! Bu adımları izleyerek, .NET için Aspose.Words kullanarak bir Word belgesindeki tabloyu kolayca bölebilirsiniz. Bu yaklaşım, büyük tabloları daha etkili bir şekilde yönetmenize yardımcı olarak belgelerinizin okunabilirliğini ve organizasyonunu iyileştirir. Deneyin ve Word belgelerindeki tablolarla çalışmanızı nasıl kolaylaştırdığını görün.

## SSS

### Bir tabloyu birden fazla satıra bölebilir miyim?
Evet, her bölme noktası için işlemi tekrarlayarak tabloyu birden fazla satıra bölebilirsiniz.

### Orijinal tablonun biçimlendirmesine ne olur?
Yeni tablo, orijinal tablonun biçimlendirmesini devralır. Herhangi bir özel biçimlendirme değişikliği, gerektiği gibi yeni tabloya uygulanabilir.

### Tabloları tekrar birleştirmek mümkün mü?
Evet, benzer yöntemleri kullanarak satırları bir tablodan diğerine taşıyarak tabloları birleştirebilirsiniz.

### Bu yöntem iç içe geçmiş tablolarda işe yarar mı?
Evet, Aspose.Words for .NET iç içe geçmiş tablolardaki işlemleri de destekler.

### Bu süreci birden fazla belge için otomatikleştirebilir miyim?
Kesinlikle! Birden fazla belge için tablo bölme işlemini otomatikleştirmek için bir betik veya uygulama oluşturabilirsiniz.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
