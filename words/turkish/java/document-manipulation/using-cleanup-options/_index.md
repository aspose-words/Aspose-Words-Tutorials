---
title: Java için Aspose.Words'de Temizleme Seçeneklerini Kullanma
linktitle: Temizleme Seçeneklerini Kullanma
second_title: Aspose.Words Java Belge İşleme API'si
description: Aspose.Words for Java Temizleme Seçenekleriyle Belge Netliğini Geliştirin. Boş paragrafları, kullanılmayan bölgeleri ve daha fazlasını nasıl kaldıracağınızı öğrenin.
weight: 10
url: /tr/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Temizleme Seçeneklerini Kullanma


## Java için Aspose.Words'de Temizleme Seçeneklerinin Kullanımına Giriş

Bu eğitimde, Aspose.Words for Java'da posta birleştirme işlemi sırasında belgeleri düzenlemek ve temizlemek için temizleme seçeneklerinin nasıl kullanılacağını inceleyeceğiz. Temizleme seçenekleri, boş paragrafları, kullanılmayan bölgeleri ve daha fazlasını kaldırmak gibi belge temizlemenin çeşitli yönlerini kontrol etmenizi sağlar.

## Ön koşullar

 Başlamadan önce, projenize Aspose.Words for Java kütüphanesinin entegre olduğundan emin olun. Bunu şuradan indirebilirsiniz:[Burada](https://releases.aspose.com/words/java/).

## Adım 1: Boş Paragrafları Kaldırma

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Birleştirme alanlarını ekle
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Temizleme seçeneklerini ayarlayın
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Noktalama işaretleriyle temizleme paragraflarını etkinleştir
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Posta birleştirmeyi yürüt
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Belgeyi kaydet
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

Bu örnekte, yeni bir belge oluşturuyoruz, birleştirme alanları ekliyoruz ve temizleme seçeneklerini boş paragrafları kaldıracak şekilde ayarlıyoruz. Ayrıca, noktalama işaretli paragrafların kaldırılmasını etkinleştiriyoruz. Posta birleştirmeyi yürüttükten sonra, belge belirtilen temizleme uygulanmış olarak kaydedilir.

## Adım 2: Birleştirilmemiş Bölgeleri Kaldırma

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Kullanılmayan bölgeleri kaldırmak için temizleme seçeneklerini ayarlayın
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Bölgelerle posta birleştirmeyi yürüt
doc.getMailMerge().executeWithRegions(data);

// Belgeyi kaydet
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

Bu örnekte, birleştirme bölgeleri olan mevcut bir belgeyi açıyoruz, temizleme seçeneklerini kullanılmayan bölgeleri kaldıracak şekilde ayarlıyoruz ve ardından posta birleştirmeyi boş verilerle yürütüyoruz. Bu işlem, kullanılmayan bölgeleri belgeden otomatik olarak kaldırır.

## Adım 3: Boş Alanları Kaldırma

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Boş alanları kaldırmak için temizleme seçeneklerini ayarlayın
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Posta birleştirmeyi yürüt
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Belgeyi kaydet
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

Bu örnekte, birleştirme alanlarını içeren bir belge açıyoruz, temizleme seçeneklerini boş alanları kaldıracak şekilde ayarlıyoruz ve posta birleştirmeyi verilerle yürütüyoruz. Birleştirmeden sonra, boş alanlar belgeden kaldırılacaktır.

## Adım 4: Kullanılmayan Alanları Kaldırma

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Kullanılmayan alanları kaldırmak için temizleme seçeneklerini ayarlayın
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Posta birleştirmeyi yürüt
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Belgeyi kaydet
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

Bu örnekte, birleştirme alanlarıyla bir belge açıyoruz, temizleme seçeneklerini kullanılmayan alanları kaldıracak şekilde ayarlıyoruz ve posta birleştirmeyi verilerle yürütüyoruz. Birleştirmeden sonra, kullanılmayan tüm alanlar belgeden kaldırılacaktır.

## Adım 5: İçeren Alanları Kaldırma

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// İçeren alanları kaldırmak için temizleme seçeneklerini ayarlayın
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Posta birleştirmeyi yürüt
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Belgeyi kaydet
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

Bu örnekte, birleştirme alanlarını içeren bir belge açıyoruz, temizleme seçeneklerini içeren alanları kaldıracak şekilde ayarlıyoruz ve posta birleştirmeyi verilerle yürütüyoruz. Birleştirmeden sonra, alanların kendisi belgeden kaldırılacaktır.

## Adım 6: Boş Tablo Satırlarını Kaldırma

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Boş tablo satırlarını kaldırmak için temizleme seçeneklerini ayarlayın
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Posta birleştirmeyi yürüt
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Belgeyi kaydet
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

Bu örnekte, bir tablo ve birleştirme alanları içeren bir belge açıyoruz, temizleme seçeneklerini boş tablo satırlarını kaldıracak şekilde ayarlıyoruz ve posta birleştirmeyi verilerle yürütüyoruz. Birleştirmeden sonra, boş tablo satırları belgeden kaldırılacaktır.

## Çözüm

Bu eğitimde, posta birleştirme işlemi sırasında belgeleri düzenlemek ve temizlemek için Aspose.Words for Java'daki temizleme seçeneklerini nasıl kullanacağınızı öğrendiniz. Bu seçenekler, belge temizliği üzerinde ayrıntılı denetim sağlayarak, cilalı ve özelleştirilmiş belgeleri kolaylıkla oluşturmanıza olanak tanır.

## SSS

### Aspose.Words for Java'da temizleme seçenekleri nelerdir?

Aspose.Words for Java'daki temizleme seçenekleri, posta birleştirme işlemi sırasında belge temizliğinin çeşitli yönlerini kontrol etmenizi sağlayan ayarlardır. Boş paragraflar, kullanılmayan bölgeler ve daha fazlası gibi gereksiz öğeleri kaldırmanızı sağlayarak, son belgenizin iyi yapılandırılmış ve cilalı olmasını sağlar.

### Belgemdeki boş paragrafları nasıl kaldırabilirim?

 Aspose.Words for Java kullanarak belgenizden boş paragrafları kaldırmak için,`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` true seçeneğine tıklayın. Bu, içeriği olmayan paragrafları otomatik olarak ortadan kaldırarak daha temiz bir belge elde etmenizi sağlar.

###  Amacı nedir?`REMOVE_UNUSED_REGIONS` cleanup option?

 The`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` seçeneği, posta birleştirme işlemi sırasında karşılık gelen verisi olmayan bir belgedeki bölgeleri kaldırmak için kullanılır. Kullanılmayan yer tutuculardan kurtularak belgenizin düzenli kalmasına yardımcı olur.

### Aspose.Words for Java kullanarak bir belgeden boş tablo satırlarını kaldırabilir miyim?

 Evet, boş tablo satırlarını bir belgeden kaldırmak için şu ayarı yapabilirsiniz:`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`temizleme seçeneğini true olarak ayarlayın. Bu, veri içermeyen tüm tablo satırlarını otomatik olarak silerek belgenizde iyi yapılandırılmış bir tablo olmasını sağlar.

###  Ayarladığımda ne olur?`REMOVE_CONTAINING_FIELDS` option?

 Ayarlama`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` seçeneği, birleştirme alanı ve onu içeren paragrafı da dahil olmak üzere birleştirme alanının tamamını, posta birleştirme işlemi sırasında belgeden kaldıracaktır. Bu, birleştirme alanlarını ve ilişkili metinlerini ortadan kaldırmak istediğinizde yararlıdır.

### Kullanılmayan birleştirme alanlarını belgemden nasıl kaldırabilirim?

 Kullanılmayan birleştirme alanlarını bir belgeden kaldırmak için,`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` seçeneğini true olarak ayarlayın. Bu, posta birleştirme sırasında doldurulmayan birleştirme alanlarını otomatik olarak ortadan kaldırarak daha temiz bir belge elde edilmesini sağlar.

###  Aradaki fark nedir?`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

 The`REMOVE_EMPTY_FIELDS` seçeneği, posta birleştirme işlemi sırasında veri içermeyen veya boş olan birleştirme alanlarını kaldırır. Öte yandan,`REMOVE_UNUSED_FIELDS`seçeneği birleştirme sırasında veriyle doldurulmayan birleştirme alanlarını kaldırır. Aralarındaki seçim, içeriği olmayan alanları mı yoksa belirli birleştirme işleminde kullanılmayan alanları mı kaldırmak istediğinize bağlıdır.

### Noktalama işaretlerinin bulunduğu paragrafların kaldırılmasını nasıl sağlayabilirim?

 Noktalama işaretli paragrafların kaldırılmasını etkinleştirmek için,`cleanupParagraphsWithPunctuationMarks` true seçeneğini seçin ve temizlik için dikkate alınacak noktalama işaretlerini belirtin. Bu, gereksiz noktalama işaretlerinden oluşan paragrafları kaldırarak daha rafine bir belge oluşturmanıza olanak tanır.

### Aspose.Words for Java'da temizleme seçeneklerini özelleştirebilir miyim?

Evet, temizleme seçeneklerini özel ihtiyaçlarınıza göre özelleştirebilirsiniz. Hangi temizleme seçeneklerinin uygulanacağını seçebilir ve bunları belge temizleme gereksinimlerinize göre yapılandırabilir, böylece nihai belgenizin istediğiniz standartları karşılamasını sağlayabilirsiniz.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
