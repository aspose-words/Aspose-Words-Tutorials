---
title: Java için Aspose.Words'de Belge Özelliklerini Kullanma
linktitle: Belge Özelliklerini Kullanma
second_title: Aspose.Words Java Belge İşleme API'si
description: Aspose.Words for Java ile belge yönetimini optimize edin. Bu kapsamlı eğitimde belge özellikleriyle çalışmayı, özel meta veri eklemeyi ve daha fazlasını öğrenin.
weight: 32
url: /tr/java/document-manipulation/using-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Belge Özelliklerini Kullanma


## Belge Özelliklerine Giriş

Belge özellikleri herhangi bir belgenin hayati bir parçasıdır. Belgenin kendisi hakkında başlık, yazar, konu, anahtar sözcükler ve daha fazlası gibi ek bilgiler sağlarlar. Java için Aspose.Words'de hem yerleşik hem de özel belge özelliklerini düzenleyebilirsiniz.

## Belge Özelliklerini Numaralandırma

### Dahili Özellikler

Yerleşik belge özelliklerini almak ve bunlarla çalışmak için aşağıdaki kod parçacığını kullanabilirsiniz:

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

Bu kod, "Başlık", "Yazar" ve "Anahtar Sözcükler" gibi özellikler de dahil olmak üzere belgenin adını ve yerleşik özelliklerini görüntüler.

### Özel Özellikler

Özel belge özellikleriyle çalışmak için aşağıdaki kod parçacığını kullanabilirsiniz:

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

Bu kod parçacığı, Boole değeri, dize, tarih, revizyon numarası ve sayısal değer dahil olmak üzere özel belge özelliklerinin nasıl ekleneceğini göstermektedir.

## Belge Özelliklerini Kaldırma

Belirli belge özelliklerini kaldırmak için aşağıdaki kodu kullanabilirsiniz:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Bu kod, belgeden "Yetkilendirilmiş Tarih" özel özelliğini kaldırır.

## İçeriğe Bağlantıyı Yapılandırma

Bazı durumlarda, belgeniz içinde bağlantılar oluşturmak isteyebilirsiniz. Bunu nasıl yapabileceğiniz aşağıda açıklanmıştır:

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Bağlantılı içerik özelliğine ekle.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Bu kod parçacığı, belgenizde bir yer imi oluşturmayı ve bu yer imine bağlantı veren özel bir belge özelliği eklemeyi gösterir.

## Ölçüm Birimleri Arasında Dönüşüm

Java için Aspose.Words'de ölçü birimlerini kolayca dönüştürebilirsiniz. İşte bunu nasıl yapacağınıza dair bir örnek:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Kenar boşluklarını inç cinsinden ayarlayın.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Bu kod parçacığı çeşitli kenar boşluklarını ve mesafeleri inç cinsinden noktalara dönüştürerek ayarlar.

## Kontrol Karakterlerini Kullanma

Kontrol karakterleri metinle uğraşırken yararlı olabilir. Metninizdeki bir kontrol karakterini nasıl değiştireceğiniz aşağıda açıklanmıştır:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // "\r" kontrol karakterini "\r\n" ile değiştirin.
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

Bu örnekte, satır başını (`\r`) bir satır sonu ve ardından bir satır beslemesi (`\r\n`).

## Çözüm

Belge özellikleri, Aspose.Words for Java'da belgelerinizi etkili bir şekilde yönetmenizde ve düzenlemenizde önemli bir rol oynar. İster yerleşik özelliklerle, ister özel özelliklerle çalışın, ister kontrol karakterlerini kullanın, belge yönetimi yeteneklerinizi geliştirmek için emrinizde bir dizi araç bulunur.

## SSS

### Yerleşik belge özelliklerine nasıl erişebilirim?

 Java için Aspose.Words'deki yerleşik belge özelliklerine erişmek için şunu kullanabilirsiniz:`getBuiltInDocumentProperties` yöntem üzerinde`Document` nesne. Bu yöntem, yineleme yapabileceğiniz yerleşik özelliklerin bir koleksiyonunu döndürür.

### Bir belgeye özel belge özellikleri ekleyebilir miyim?

 Evet, bir belgeye özel belge özellikleri ekleyebilirsiniz.`CustomDocumentProperties` koleksiyon. Dizeler, boole değerleri, tarihler ve sayısal değerler dahil olmak üzere çeşitli veri türleriyle özel özellikler tanımlayabilirsiniz.

### Belirli bir özel belge özelliğini nasıl kaldırabilirim?

 Belirli bir özel belge özelliğini kaldırmak için şunu kullanabilirsiniz:`remove` yöntem üzerinde`CustomDocumentProperties`koleksiyon, kaldırmak istediğiniz özelliğin adını parametre olarak geçirerek.

### Bir belge içindeki içeriğe bağlantı vermenin amacı nedir?

Bir belge içindeki içeriğe bağlanmak, belgenin belirli bölümlerine dinamik referanslar oluşturmanıza olanak tanır. Bu, etkileşimli belgeler veya bölümler arasında çapraz referanslar oluşturmak için yararlı olabilir.

### Aspose.Words for Java'da farklı ölçü birimleri arasında nasıl dönüşüm yapabilirim?

 Java için Aspose.Words'de farklı ölçü birimleri arasında dönüşüm yapabilirsiniz.`ConvertUtil` sınıfı. İnçleri puanlara, puanları santimetrelere ve daha fazlasına dönüştürmek için yöntemler sağlar.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
