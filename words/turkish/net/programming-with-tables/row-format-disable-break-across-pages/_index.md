---
title: Satır Biçimi Sayfalar Arası Kesmeyi Devre Dışı Bırak
linktitle: Satır Biçimi Sayfalar Arası Kesmeyi Devre Dışı Bırak
second_title: Aspose.Words Belge İşleme API'si
description: Tablo okunabilirliğini ve biçimlendirmesini korumak için Aspose.Words for .NET'i kullanarak Word belgelerindeki sayfalar arası satır sonlarını nasıl devre dışı bırakacağınızı öğrenin.
weight: 10
url: /tr/net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Satır Biçimi Sayfalar Arası Kesmeyi Devre Dışı Bırak

## giriiş

Word belgelerindeki tablolarla çalışırken, satırların sayfalar arasında bölünmemesini sağlamak isteyebilirsiniz; bu, belgelerinizin okunabilirliğini ve biçimlendirmesini korumak için önemli olabilir. .NET için Aspose.Words, sayfalar arasında satır sonlarını devre dışı bırakmanın kolay bir yolunu sağlar.

Bu eğitimde, Aspose.Words for .NET kullanarak bir Word belgesindeki sayfalar arasında satır sonlarını devre dışı bırakma sürecini adım adım ele alacağız.

## Ön koşullar

Başlamadan önce aşağıdaki ön koşullara sahip olduğunuzdan emin olun:
- Aspose.Words for .NET kütüphanesi kuruldu.
- Birden fazla sayfaya yayılan bir tablodan oluşan bir Word belgesi.

## Ad Alanlarını İçe Aktar

Öncelikle projenize gerekli namespace'leri import edin:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Adım 1: Belgeyi Yükleyin

Birden fazla sayfaya yayılan tabloyu içeren belgeyi yükleyin.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Adım 2: Tabloya Erişim

Belgedeki ilk tabloya erişin. Bu, değiştirmek istediğiniz tablonun belgedeki ilk tablo olduğunu varsayar.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Adım 3: Tüm Satırlar İçin Sayfalar Arası Geçişi Devre Dışı Bırakın

 Tablodaki her satırda dolaşın ve`AllowBreakAcrossPages`mülk`false`Bu, satırların sayfalar arasında bölünmemesini sağlar.

```csharp
// Tablodaki tüm satırlar için sayfalar arası kesmeyi devre dışı bırakın.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Adım 4: Belgeyi Kaydedin

Değiştirilen belgeyi belirttiğiniz dizine kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Çözüm

Bu eğitimde, .NET için Aspose.Words kullanarak bir Word belgesindeki sayfalar arasında satır sonlarının nasıl devre dışı bırakılacağını gösterdik. Yukarıda özetlenen adımları izleyerek, tablo satırlarınızın bozulmadan kalmasını ve sayfalar arasında bölünmemesini sağlayarak belgenin okunabilirliğini ve biçimlendirmesini koruyabilirsiniz.

## SSS

### Sayfalar arasında satır sonlarını tüm satırlar yerine belirli bir satır için devre dışı bırakabilir miyim?  
 Evet, istediğiniz satıra erişip satır sonlarını ayarlayarak belirli satırlar için satır sonlarını devre dışı bırakabilirsiniz.`AllowBreakAcrossPages`mülk`false`.

### Bu yöntem birleştirilmiş hücrelere sahip tablolar için işe yarar mı?  
 Evet, bu yöntem birleştirilmiş hücrelere sahip tablolar için işe yarar. Özellik`AllowBreakAcrossPages` hücre birleştirmeden bağımsız olarak tüm satıra uygulanır.

### Bu yöntem tablonun başka bir tablonun içinde yer alması durumunda işe yarar mı?  
Evet, aynı şekilde iç içe geçmiş tablolara erişebilir ve bunları değiştirebilirsiniz. İç içe geçmiş tabloya dizinine veya diğer özelliklerine göre doğru şekilde başvurduğunuzdan emin olun.

### Bir satırın sayfalar arasında bölünmeye izin verip vermediğini nasıl kontrol edebilirim?  
 Bir satırın sayfalar arasında geçişe izin verip vermediğini şuraya erişerek kontrol edebilirsiniz:`AllowBreakAcrossPages` mülkiyeti`RowFormat` ve değerini kontrol ediyoruz.

### Bu ayarı bir belgedeki tüm tablolara uygulamanın bir yolu var mı?  
Evet, belgedeki tüm tablolar arasında dolaşabilir ve bu ayarı her birine uygulayabilirsiniz.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
