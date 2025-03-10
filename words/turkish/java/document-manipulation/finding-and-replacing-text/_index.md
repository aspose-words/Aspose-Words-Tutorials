---
title: Java için Aspose.Words'de Metin Bulma ve Değiştirme
linktitle: Metin Bulma ve Değiştirme
second_title: Aspose.Words Java Belge İşleme API'si
description: Aspose.Words for Java ile Word belgelerinde metin bulmayı ve değiştirmeyi öğrenin. Kod örnekleriyle adım adım kılavuz. Java belge düzenleme becerilerinizi geliştirin.
weight: 15
url: /tr/java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Metin Bulma ve Değiştirme


## Java için Aspose.Words'de Metin Bulma ve Değiştirmeye Giriş

Aspose.Words for Java, Word belgeleriyle programatik olarak çalışmanıza olanak tanıyan güçlü bir Java API'sidir. Word belgeleriyle uğraşırken sık karşılaşılan görevlerden biri metni bulmak ve değiştirmektir. Şablonlardaki yer tutucuları güncellemeniz veya daha karmaşık metin düzenlemeleri yapmanız gerekip gerekmediğine bakılmaksızın, Aspose.Words for Java hedeflerinize verimli bir şekilde ulaşmanıza yardımcı olabilir.

## Ön koşullar

Metin bulma ve değiştirme ayrıntılarına dalmadan önce, aşağıdaki ön koşulların mevcut olduğundan emin olun:

- Java Geliştirme Ortamı
- Java için Aspose.Words kütüphanesi
- Üzerinde çalışılacak bir örnek Word belgesi

 Aspose.Words for Java kütüphanesini şu adresten indirebilirsiniz:[Burada](https://releases.aspose.com/words/java/).

## Basit Metni Bulma ve Değiştirme

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Bir DocumentBuilder Oluşturun
DocumentBuilder builder = new DocumentBuilder(doc);

// Metni bul ve değiştir
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

 Bu örnekte bir Word belgesi yüklüyoruz, bir`DocumentBuilder` ve şunu kullanın`replace` Belge içerisinde "eski-metin"i "yeni-metin" ile bulup değiştirme yöntemi.

## Düzenli İfadeleri Kullanma

Düzenli ifadeler, metin arama ve değiştirme için güçlü desen eşleştirme yetenekleri sağlar. Aspose.Words for Java, daha gelişmiş bulma ve değiştirme işlemleri için düzenli ifadeleri destekler.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Bir DocumentBuilder Oluşturun
DocumentBuilder builder = new DocumentBuilder(doc);

// Metin bulmak ve değiştirmek için düzenli ifadeleri kullanın
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

Bu örnekte, belgedeki metni bulmak ve değiştirmek için düzenli ifade desenini kullanıyoruz.

## Alanların İçindeki Metni Yoksayma

Aspose.Words'ü, bulma ve değiştirme işlemlerini gerçekleştirirken alanlar içindeki metni yoksayacak şekilde yapılandırabilirsiniz.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Bir FindReplaceOptions örneği oluşturun ve IgnoreFields'ı true olarak ayarlayın
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Metni değiştirirken seçenekleri kullanın
doc.getRange().replace("text-to-replace", "new-text", options);

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

Bu, birleştirme alanları gibi alanların içindeki metnin değiştirilmesini engellemek istediğinizde yararlıdır.

## İçindeki Metni Yoksayma Revizyonları Sil

Aspose.Words'ü, bulma ve değiştirme işlemleri sırasında silme revizyonlarının içindeki metni yoksayacak şekilde yapılandırabilirsiniz.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Bir FindReplaceOptions örneği oluşturun ve IgnoreDeleted değerini true olarak ayarlayın
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Metni değiştirirken seçenekleri kullanın
doc.getRange().replace("text-to-replace", "new-text", options);

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

Bu, izlenen değişikliklerde silinmek üzere işaretlenen metnin değiştirilmesini engellemenize olanak tanır.

## Ekleme Revizyonları İçindeki Metni Yoksayma

Aspose.Words'ü, bulma ve değiştirme işlemleri sırasında ekleme revizyonlarının içindeki metni yok sayacak şekilde yapılandırabilirsiniz.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Bir FindReplaceOptions örneği oluşturun ve IgnoreInserted değerini true olarak ayarlayın
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Metni değiştirirken seçenekleri kullanın
doc.getRange().replace("text-to-replace", "new-text", options);

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

Bu, izlenen değişikliklerde eklenmiş olarak işaretlenen metnin değiştirilmesini engellemenize olanak tanır.

## Metni HTML ile Değiştirme

Metni HTML içeriğiyle değiştirmek için Aspose.Words for Java'yı kullanabilirsiniz.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Özel bir değiştirme geri aramasıyla bir FindReplaceOptions örneği oluşturun
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Metni değiştirirken seçenekleri kullanın
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

 Bu örnekte özel bir`ReplaceWithHtmlEvaluator` metni HTML içeriğiyle değiştirmek.

## Başlıklar ve Altbilgilerdeki Metni Değiştirme

Word belgenizin üstbilgi ve altbilgilerindeki metinleri bulabilir ve değiştirebilirsiniz.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Başlık ve altbilgi koleksiyonunu edinin
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Metnini değiştirmek istediğiniz üstbilgi veya altbilgi türünü seçin (örneğin, HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Bir FindReplaceOptions örneği oluşturun ve bunu altbilgi aralığına uygulayın
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

Bu, özellikle başlık ve altbilgilerde metin değiştirmeleri yapmanıza olanak tanır.

## Üstbilgi ve Altbilgi Siparişleri için Değişiklikler Gösteriliyor

Belgenizdeki üstbilgi ve altbilgi sıralarındaki değişiklikleri göstermek için Aspose.Words'ü kullanabilirsiniz.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// İlk bölümü al
Section firstPageSection = doc.getFirstSection();

//Bir FindReplaceOptions örneği oluşturun ve bunu belgenin aralığına uygulayın
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Başlık ve altbilgi sıralarını etkileyen metni değiştirin
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

Bu, belgenizdeki üstbilgi ve altbilgi siparişleriyle ilgili değişiklikleri görselleştirmenizi sağlar.

## Metni Alanlarla Değiştirme

Aspose.Words for Java'yı kullanarak metni alanlarla değiştirebilirsiniz.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Bir FindReplaceOptions örneği oluşturun ve alanlar için özel bir değiştirme geri araması ayarlayın
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Metni değiştirirken seçenekleri kullanın
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

 Bu örnekte metni alanlarla değiştiriyoruz ve alan türünü belirtiyoruz (örneğin,`FieldType.FIELD_MERGE_FIELD`).

## Değerlendirici ile Değiştirme

Değiştirme metnini dinamik olarak belirlemek için özel bir değerlendirici kullanabilirsiniz.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Bir FindReplaceOptions örneği oluşturun ve özel bir değiştirme geri araması ayarlayın
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Metni değiştirirken seçenekleri kullanın
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

Bu örnekte özel bir değerlendirici kullanıyoruz (`MyReplaceEvaluator`) metni değiştirmek için.

## Regex ile değiştirme

Java için Aspose.Words, metni düzenli ifadeler kullanarak değiştirmenize olanak tanır.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Metin bulmak ve değiştirmek için düzenli ifadeleri kullanın
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

Bu örnekte, belgedeki metni bulmak ve değiştirmek için düzenli ifade desenini kullanıyoruz.

## Değiştirme Modelleri İçinde Tanıma ve Değiştirmeler

Aspose.Words for Java'yı kullanarak değiştirme desenleri içinde değiştirmeler yapabilir ve tanıyabilirsiniz.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// UseSubstitutions'ı true olarak ayarlayan bir FindReplaceOptions örneği oluşturun
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Metni bir desenle değiştirirken seçenekleri kullanın
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

Bu, daha gelişmiş değişimler için değişim desenleri içerisinde değişimler yapmanıza olanak tanır.

## Bir Dize ile Değiştirme

Aspose.Words for Java'yı kullanarak metni basit bir dizeyle değiştirebilirsiniz.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Metni bir dizeyle değiştir
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

Bu örnekte, belge içinde "değiştirilecek metin" ifadesini "yeni-dize" ile değiştiriyoruz.

## Eski Siparişi Kullanma

Bul ve değiştir işlemlerini gerçekleştirirken eski sırayı kullanabilirsiniz.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Bir FindReplaceOptions örneği oluşturun ve UseLegacyOrder'ı true olarak ayarlayın
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Metni değiştirirken seçenekleri kullanın
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

Bu, bul ve değiştir işlemleri için eski düzeni kullanmanıza olanak tanır.

## Tablodaki Metni Değiştirme

Word belgenizdeki tabloların içindeki metinleri bulabilir ve değiştirebilirsiniz.

```java
// Belgeyi yükle
Document doc = new Document("your-document.docx");

// Belirli bir tabloyu al (örneğin, ilk tablo)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

//Tablodaki metni değiştirmek için FindReplaceOptions'ı kullanın
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Değiştirilen belgeyi kaydet
doc.save("modified-document.docx");
```

Bu, özellikle tablolar içerisinde metin değiştirmeleri yapmanıza olanak tanır.

## Çözüm

Aspose.Words for Java, Word belgelerinde metin bulma ve değiştirme için kapsamlı yetenekler sunar. Basit metin değiştirmeleri veya düzenli ifadeler, alan manipülasyonları veya özel değerlendiriciler kullanarak daha gelişmiş işlemler yapmanız gerekip gerekmediğine bakılmaksızın, Aspose.Words for Java sizin için her şeyi kapsar. Bu güçlü Java kütüphanesinin tüm potansiyelinden yararlanmak için Aspose tarafından sağlanan kapsamlı belgeleri ve örnekleri incelediğinizden emin olun.

## SSS

### Aspose.Words for Java'yı nasıl indirebilirim?

 Aspose.Words for Java'yı web sitesini ziyaret ederek indirebilirsiniz.[bu bağlantı](https://releases.aspose.com/words/java/).

### Metin değiştirme için düzenli ifadeleri kullanabilir miyim?

Evet, Aspose.Words for Java'da metin değiştirme için düzenli ifadeler kullanabilirsiniz. Bu, daha gelişmiş ve esnek bul ve değiştir işlemleri gerçekleştirmenizi sağlar.

### Değiştirme sırasında alanların içindeki metni nasıl yok sayabilirim?

Değiştirme sırasında alanların içindeki metni yoksaymak için,`IgnoreFields` mülkiyeti`FindReplaceOptions` ile`true`Bu, birleştirme alanları gibi alanlardaki metinlerin değiştirmeden hariç tutulmasını sağlar.

### Başlık ve altbilgilerdeki metinleri değiştirebilir miyim?

 Evet, Word belgenizin üstbilgileri ve altbilgilerindeki metni değiştirebilirsiniz. Sadece uygun üstbilgiye veya altbilgiye erişin ve`replace` istenilen yöntemle`FindReplaceOptions`.

### UseLegacyOrder seçeneği ne işe yarar?

 The`UseLegacyOrder` seçenek`FindReplaceOptions` bul ve değiştir işlemlerini gerçekleştirirken eski sırayı kullanmanıza olanak tanır. Bu, eski sıra davranışının istendiği belirli senaryolarda yararlı olabilir.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
