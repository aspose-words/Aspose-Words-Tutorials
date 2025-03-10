---
title: Üstbilgi Altbilgi Oluştur
linktitle: Üstbilgi Altbilgi Oluştur
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgelerinde başlık ve altbilgilerin nasıl ekleneceğini ve özelleştirileceğini öğrenin. Bu adım adım kılavuz profesyonel belge biçimlendirmesini garanti eder.
weight: 10
url: /tr/net/working-with-headers-and-footers/create-header-footer/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üstbilgi Altbilgi Oluştur

## giriiş

Belgelerinize başlıklar ve altbilgiler eklemek, profesyonelliklerini ve okunabilirliklerini artırabilir. Aspose.Words for .NET ile Word belgeleriniz için başlıklar ve altbilgileri kolayca oluşturabilir ve özelleştirebilirsiniz. Bu eğitimde, bu özellikleri sorunsuz bir şekilde uygulayabilmenizi sağlayarak sizi adım adım süreçte yönlendireceğiz.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

-  Aspose.Words for .NET: Şuradan indirin ve kurun:[indirme bağlantısı](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Kodunuzu yazıp çalıştırabileceğiniz Visual Studio gibi bir ortam.
- Temel C# Bilgisi: C# ve .NET framework'ünün anlaşılması.
- Örnek Belge: Üstbilgi ve altbilgileri uygulamak için örnek bir belge veya eğitimde gösterildiği gibi yeni bir tane oluşturun.

## Ad Alanlarını İçe Aktar

Öncelikle Aspose.Words sınıflarına ve metotlarına erişmek için gerekli namespace'leri import etmeniz gerekiyor.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Adım 1: Belge Dizinini Tanımlayın

Belgenizin kaydedileceği dizini tanımlayın. Bu, yolu etkili bir şekilde yönetmeye yardımcı olur.

```csharp
// Belgeler dizinine giden yol
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Adım 2: Yeni Bir Belge Oluşturun

 Yeni bir belge oluşturun ve`DocumentBuilder`içerik eklenmesini kolaylaştırmak için.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 3: Sayfa Kurulumunu Yapılandırın

İlk sayfanın farklı bir üstbilgi/altbilgiye sahip olup olmayacağı da dahil olmak üzere sayfa ayarlarını yapın.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Adım 4: İlk Sayfaya Bir Başlık Ekleyin

İlk sayfanın başlık bölümüne gidin ve başlık metnini yapılandırın.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Adım 5: Birincil Başlık Ekleyin

Birincil başlık bölümüne geçin ve bir resim ve metin ekleyin.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Başlığa bir resim ekle
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Adım 6: Birincil Altbilgi Ekleyin

Birincil altbilgi bölümüne geçin ve altbilgi içeriğini biçimlendirmek için bir tablo oluşturun.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Sayfa numaralandırması ekle
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Adım 7: İçerik ve Sayfa Sonları Ekleyin

Belgenin sonuna gidin, sayfa sonu ekleyin ve farklı sayfa ayarlarıyla yeni bir bölüm oluşturun.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Adım 8: Önceki Bölümden Başlıkları ve Alt Bilgileri Kopyalayın

Önceki bir bölümden üstbilgi ve altbilgileri yeniden kullanmak istiyorsanız, bunları kopyalayın ve gerekli değişiklikleri yapın.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Çözüm

Bu adımları izleyerek, Aspose.Words for .NET kullanarak Word belgelerinize üstbilgi ve altbilgileri etkili bir şekilde ekleyebilir ve özelleştirebilirsiniz. Bu, belgenizin görünümünü ve profesyonelliğini geliştirerek daha okunabilir ve ilgi çekici hale getirir.

## SSS

### Aspose.Words for .NET nedir?

Aspose.Words for .NET, geliştiricilerin .NET uygulamaları içerisinde Word belgelerini programlı bir şekilde oluşturmalarına, düzenlemelerine ve dönüştürmelerine olanak tanıyan bir kütüphanedir.

### Üstbilgiye veya altbilgiye resim ekleyebilir miyim?

 Evet, üstbilgiye veya altbilgiye kolayca resim ekleyebilirsiniz.`DocumentBuilder.InsertImage` yöntem.

### İlk sayfa için farklı üstbilgi ve altbilgileri nasıl ayarlarım?

 İlk sayfa için farklı üstbilgiler ve altbilgiler ayarlayabilirsiniz.`DifferentFirstPageHeaderFooter` mülkiyeti`PageSetup` sınıf.

### Aspose.Words hakkında daha fazla dokümanı nerede bulabilirim?

 Kapsamlı belgeleri şurada bulabilirsiniz:[Aspose.Words API dokümantasyon sayfası](https://reference.aspose.com/words/net/).

### Aspose.Words için destek mevcut mu?

 Evet, Aspose, kendi aracılığıyla destek sunuyor[destek forumu](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
