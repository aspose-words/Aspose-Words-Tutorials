---
date: 2026-01-24
description: Aspose.Words for Java ile XML verilerini birleştirmeyi, Java’da belge
  oluşturmayı otomatikleştirmeyi ve dinamik belgeler için Mustache sözdizimini kullanmayı
  öğrenin.
linktitle: Using XML Data
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java'da XML Nasıl Birleştirilir
url: /tr/java/document-manipulation/using-xml-data/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# XML'i Aspose.Words for Java ile Birleştirme

Bu kapsamlı rehberde Aspose.Words for Java kullanarak **XML'i nasıl birleştireceğinizi** keşfedeceksiniz. Temel ve iç içe mail‑merge senaryolarını adım adım inceleyecek, **Mustache sözdizimini nasıl kullanacağınızı** gösterecek ve **Java tarzı belge oluşturma** projelerini nasıl otomatikleştireceğinizi açıklayacağız. Sonunda sadece birkaç satır kodla XML kaynaklarından doğrudan kişiselleştirilmiş Word belgeleri oluşturabileceksiniz.

## Hızlı Yanıtlar
- **Mail merge için birincil sınıf nedir?** `Document` ve onun `MailMerge` özelliği.  
- **İç içe XML tablolarını birleştirebilir miyim?** Evet – hiyerarşik veri için `executeWithRegions` kullanın.  
- **Mustache sözdizimi destekleniyor mu?** `setUseNonMergeFields(true)` ile etkinleştirin.  
- **Üretim için lisansa ihtiyacım var mı?** Ticari bir Aspose.Words lisansı gereklidir.  
- **Hangi Java sürümü uyumludur?** Java 8+ ve üzeri tamamen desteklenir.

## Aspose.Words'da XML Mail Merge Nedir?
XML mail merge, XML tabanlı veri setlerini bir Word şablonundaki yer tutuculara bağlamanızı sağlar. Motor, her yer tutucuyu ilgili XML düğüm değeriyle değiştirerek manuel düzenleme gerektirmeyen tamamlanmış bir belge üretir.

## XML‑Tabanlı Belge Oluşturma için Aspose.Words Neden Kullanılmalı?
- **Microsoft Office bağımlılığı olmadan Java** projelerinde belge oluşturmayı otomatikleştirin.  
- **Karmaşık hiyerarşiler için destek** – iç içe tablolar, yinelenen bölümler ve koşullu içerik.  
- **Mustache sözdizimi**, gelişmiş şablonlama için esnek, merge‑field olmayan yer tutucular sağlar.  
- **Çapraz platform** – Windows, Linux ve macOS'ta çalışır.

## Önkoşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

- [Aspose.Words for Java](https://products.aspose.com/words/java/) yüklü (en son sürüm).  
- Müşteriler, siparişler ve satıcılar için örnek XML dosyaları (öğreticide `Mail merge data - Customers.xml`, `Orders.xml` ve `Vendors.xml` kullanılır).  
- Birleştirme alanları içeren Word şablon belgeleri (ör. `Registration complete.docx`, `Invoice.docx`, `Vendor.docx`).  

## XML'i Birleştirme – Temel Mail Merge

Temel bir mail merge, tek bir XML tablosunu Word şablonuna aktarır. Aşağıdaki adımları izleyin:

1. XML dosyasını bir `DataSet` içine yükleyin.  
2. Hedef Word belgesini açın.  
3. Birleştirmeyi tablo adıyla yürütün.  
4. Birleştirilmiş belgeyi kaydedin.

```java
DataSet customersDs = new DataSet();
customersDs.readXml("Your Directory Path" + "Mail merge data - Customers.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Registration complete.docx");
doc.getMailMerge().execute(customersDs.getTables().get("Customer"));
doc.save("Your Directory Path" + "BasicMailMerge.docx");
```

**Pro ipucu:** Basit birleştirmeler için XML yapınızı düz tutun – her tablo doğrudan bir dizi birleştirme alanına eşlenmelidir.

## XML'i Birleştirme – İç İçe Mail Merge

XML'iniz ebeveyn‑çocuk ilişkileri (ör. satır öğeleri içeren siparişler) içerdiğinde, iç içe birleştirme gerekir. `executeWithRegions` yöntemi her bölgeyi özyinelemeli olarak işler.

1. Hiyerarşik XML'i bir `DataSet` içine yükleyin.  
2. Kesin biçimlendirme gerekiyorsa boşluk kırpmayı devre dışı bırakın.  
3. Tüm iç içe tabloları işlemek için `executeWithRegions` çağırın.  
4. Sonucu kaydedin.

```java
DataSet pizzaDs = new DataSet();
pizzaDs.readXml("Your Directory Path" + "Mail merge data - Orders.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Invoice.docx");
doc.getMailMerge().setTrimWhitespaces(false);
doc.getMailMerge().executeWithRegions(pizzaDs);
doc.save("Your Directory Path" + "NestedMailMerge.docx");
```

**Yaygın tuzak:** `setTrimWhitespaces(false)` ayarlamayı unutmak, özellikle para birimi veya sayısal alanlarda, son belgede istenmeyen boşluklara neden olabilir.

## Mustache Sözdizimini bir DataSet ile Kullanma

Mustache sözdizimi, şablonunuzun içinde merge‑field olmayan yer tutucular (ör. `{{CustomerName}}`) eklemenizi sağlar. Bunu etkinleştirip bölge‑tabanlı birleştirme çalıştırın.

1. Satıcı XML'ini yükleyin.  
2. ` Mustache desteğini açın.  
3. Bölgeyle birleştirmeyi yürütün.  
4. Çıktıyı kaydedin.

```java
DataSet ds = new DataSet();
ds.readXml("Your Directory Path" + "Mail merge data - Vendors.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Vendor.docx");
doc.getMailMerge().setUseNonMergeFields(true);
doc.getMailMerge().executeWithRegions(ds);
doc.save("Your Directory Path" + "MustacheSyntaxUsingDataSet.docx");
```

**Mustache neden kullanılmalı?** Veriye referans vermek için temiz, dil‑bağımsız bir yol sunar; şablonlarınızı okumayı ve sürdürmeyi kolaylaştırır, özellikle **XML‑tabanlı belge oluşturma** iş akışlarında.

## Yaygın Sorunlar ve Çözümler

| Sorun | Çözüm |
|-------|----------|
| XML düğümleri birleştirme alanlarıyla eşleşmiyor | XML öğesi adlarının birleştirme alanı adlarıyla tam olarak eşleştiğini (büyük/küçük harfe duyarlı) doğrulayın. |
| Birleştirilen değerlerin etrafında boşluklar görünüyor | `doc.getMailMerge().setTrimWhitespaces(false)` kullanarak orijinal boşlukları koruyun. |
| İç içırın. |

## SSS

### XML verilerimi mail merge için nasıl hazırlayabilirim?
XML'inizin, her `<TableName>` öğesinin satır (`<Row>`) ve sütunları içerdiği ve bunların Word şablonunuzdaki birleştirme alanlarıyla eşleştiği tablo benzeri bir yapıyı izlediğinden emin olun.

### Mail merge değerleri için kırpma davranışını özelleştirebilir miyim?
Evet. XML'de göründüğü gibi baştaki/sondaki boşlukları korumak için `doc.getMailMerge().setTrimWhitespaces(false)` kullanın.

### Mustache sözdizimi nedir ve ne zaman kullanmalıyım?
Mustache sözdizimi (`{{FieldName}}`), geleneksel birleştirme alanlarıyla sınırlı olmayan esnek yer tutucular sağlar. Daha temiz bir şablona ihtiyaç duyduğunuzda veya veri mantığını Word alan kodlarından ayırmak istediğinizde `setUseNonMergeFields(true)` ile etkinleştirin.

### Bu yaklaşım ile Java projelerinde belge oluşturmayı nasıl otomatikleştiririm?
Yukarıdaki kod parçacıklarını hizmet katmanınıza entegre edin, XML'i veritabanlarından veya API'lerden okuyun ve yeni bir belge gerektiğinde (ör. fatura oluşturma, sözleşme hazırlama) birleştirme rutinini çağırın.

### Üretim kullanımı için ticari lisans gerekli mi?
Evet, Aspose.Words üretim ortamları için geçerli bir lisans gerektirir. Değerlendirme amacıyla ücretsiz geçici bir lisans mevcuttur.

**Son Güncelleme:** 2026-01-24  
**Test Edilen:** Aspose.Words for Java (en son sürüm)  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}