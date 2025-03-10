---
title: Özel Xml Parçasına Eşlenen Tekrarlayan Bölüm Tablosu Oluşturma
linktitle: Özel Xml Parçasına Eşlenen Tekrarlayan Bölüm Tablosu Oluşturma
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak bir Word belgesinde CustomXmlPart'a eşlenen tekrarlayan bir bölüm içeren bir tablonun nasıl oluşturulacağını öğrenin.
weight: 10
url: /tr/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Özel Xml Parçasına Eşlenen Tekrarlayan Bölüm Tablosu Oluşturma

## giriiş

Bu eğitimde, Aspose.Words for .NET kullanarak özel bir XML parçasına eşlenen tekrarlayan bir bölüme sahip bir tablo oluşturma sürecini ele alacağız. Bu, özellikle yapılandırılmış verilere dayalı belgeleri dinamik olarak oluşturmak için yararlıdır.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
1.  Aspose.Words for .NET kütüphanesi yüklendi. Bunu şuradan indirebilirsiniz:[Aspose web sitesi](https://releases.aspose.com/words/net/).
2. C# ve XML hakkında temel bilgi.

## Ad Alanlarını İçe Aktar

Projenize gerekli ad alanlarını eklediğinizden emin olun:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Adım 1: Belgeyi ve DocumentBuilder'ı Başlatın

 İlk olarak yeni bir belge oluşturun ve başlatın`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 2: Özel XML Parçası Ekle

Belgeye özel bir XML parçası ekleyin. Bu XML, tablomuza eşlemek istediğimiz verileri içerir:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Adım 3: Tablo Yapısını Oluşturun

 Sonra şunu kullanın:`DocumentBuilder` tablo başlığını oluşturmak için:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Adım 4: Tekrarlayan Bölüm Oluşturun

 Bir tane oluştur`StructuredDocumentTag` (SDT) tekrar eden bölüm için ve bunu XML verilerine eşleyin:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Adım 5: Tekrarlayan Bölüm Öğesi Oluşturun

Tekrar eden bölüm öğesi için bir SDT oluşturun ve bunu tekrar eden bölüme ekleyin:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Adım 6: XML Verilerini Tablo Hücrelerine Eşleyin

Başlık ve yazar için SDT'ler oluşturun, bunları XML verilerine eşleyin ve satıra ekleyin:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Adım 7: Belgeyi Kaydedin

Son olarak belgeyi belirtilen dizine kaydedin:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Çözüm

Bu adımları izleyerek, Aspose.Words for .NET kullanarak özel bir XML parçasına eşlenen tekrarlayan bir bölüme sahip bir tabloyu başarıyla oluşturdunuz. Bu, yapılandırılmış verilere dayalı dinamik içerik oluşturulmasına olanak tanır ve belge oluşturmayı daha esnek ve güçlü hale getirir.

## SSS

### StructuredDocumentTag (SDT) nedir?
İçerik denetimi olarak da bilinen SDT, bir belgede yapılandırılmış verileri barındırmak için kullanılan sınırlı bir bölgedir.

### Özel XML kısmında başka veri tipleri kullanabilir miyim?
Evet, özel XML parçanızı herhangi bir veri türüyle yapılandırabilir ve buna göre eşleyebilirsiniz.

### Tekrarlanan bölüme nasıl daha fazla satır eklerim?
Tekrarlanan bölüm, eşlenen XML yolundaki her öğe için satır yapısını otomatik olarak çoğaltır.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
