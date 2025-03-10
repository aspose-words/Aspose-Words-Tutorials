---
title: Java için Aspose.Words'de Listelerin Kullanımı
linktitle: Listeleri Kullanma
second_title: Aspose.Words Java Belge İşleme API'si
description: Bu adım adım eğitimle Aspose.Words for Java'da listeleri kullanmayı öğrenin. Belgelerinizi etkili bir şekilde düzenleyin ve biçimlendirin.
weight: 18
url: /tr/java/using-document-elements/using-lists/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Listelerin Kullanımı


Bu kapsamlı eğitimde, Microsoft Word belgeleriyle programatik olarak çalışmak için güçlü bir API olan Aspose.Words for Java'da listeleri etkili bir şekilde nasıl kullanacağınızı keşfedeceğiz. Listeler, belgelerinizdeki içeriği yapılandırmak ve düzenlemek için olmazsa olmazdır. Listelerle çalışmanın iki temel yönünü ele alacağız: her bölümde listeleri yeniden başlatmak ve liste düzeylerini belirtmek. Hadi başlayalım!

## Java için Aspose.Words'e Giriş

Listelerle çalışmaya başlamadan önce, Java için Aspose.Words ile tanışalım. Bu API, geliştiricilere Java ortamında Word belgeleri oluşturma, düzenleme ve işleme araçları sağlar. Basit belge oluşturmadan karmaşık biçimlendirme ve içerik yönetimine kadar çeşitli görevler için çok yönlü bir çözümdür.

### Ortamınızı Kurma

 Başlamak için, geliştirme ortamınızda Aspose.Words for Java'nın yüklü ve ayarlanmış olduğundan emin olun. İndirebilirsiniz[Burada](https://releases.aspose.com/words/java/). 

## Her Bölümde Listeleri Yeniden Başlatma

Birçok senaryoda, belgenizin her bölümünde listeleri yeniden başlatmanız gerekebilir. Bu, raporlar, kılavuzlar veya akademik makaleler gibi birden fazla bölümü olan yapılandırılmış belgeler oluşturmak için yararlı olabilir.

İşte Java için Aspose.Words'ü kullanarak bunu nasıl başaracağınıza dair adım adım bir kılavuz:

### Belgenizi Başlatın: 
Yeni bir belge nesnesi oluşturarak başlayın.

```java
Document doc = new Document();
```

### Numaralandırılmış Liste Ekle: 
Belgenize numaralandırılmış bir liste ekleyin. Varsayılan numaralandırma stilini kullanacağız.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Liste Ayarlarını Yapılandırın: 
\Her bölümde listenin yeniden başlatılmasını etkinleştir.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### DocumentBuilder Kurulumu: 
Belgenize içerik eklemek için bir DocumentBuilder oluşturun.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Liste Öğeleri Ekle: 
Belgenize liste öğeleri eklemek için bir döngü kullanın. 15. öğeden sonra bir bölüm sonu ekleyeceğiz.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Belgenizi Kaydedin: 
İstediğiniz seçeneklerle belgeyi kaydedin.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

Bu adımları izleyerek, her bölümde yeniden başlayan listeler içeren, net ve düzenli içerik yapısını koruyan belgeler oluşturabilirsiniz.

## Liste Düzeylerini Belirleme

Java için Aspose.Words, özellikle belgenizde farklı liste biçimlerine ihtiyaç duyduğunuzda kullanışlı olan liste düzeylerini belirtmenize olanak tanır. Bunu nasıl yapacağınızı inceleyelim:

### Belgenizi Başlatın: 
Yeni bir belge nesnesi oluşturun.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Numaralandırılmış Liste Oluşturun: 
Microsoft Word'den numaralandırılmış liste şablonunu uygulayın.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Liste Düzeylerini Belirleyin: 
Farklı liste seviyelerinde gezinin ve içerik ekleyin.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Madde İşaretli Liste Oluşturun: 
Şimdi maddeler halinde bir liste oluşturalım.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Belirtilen Madde İşaretli Liste Düzeyleri: 
Numaralandırılmış listeye benzer şekilde seviyeleri belirtin ve içerik ekleyin.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Durdurma Listesi Biçimlendirmesi: 
Liste biçimlendirmesini durdurmak için listeyi null olarak ayarlayın.

```java
builder.getListFormat().setList(null);
```

### Belgenizi Kaydedin: 
Belgeyi kaydedin.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

Bu adımları izleyerek, özel liste düzeylerine sahip belgeler oluşturabilir, böylece belgelerinizdeki listelerin biçimlendirmesini kontrol edebilirsiniz.

## Tam Kaynak Kodu
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection yalnızca uyumluluk OoxmlComplianceCore.Ecma376'dan yüksekse yazılacaktır.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Microsoft Word liste şablonlarından birine dayalı olarak numaralandırılmış bir liste oluşturun
        //ve bunu belge oluşturucunun geçerli paragrafına uygulayın.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // Bu listede dokuz seviye var, hepsini deneyelim.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Microsoft Word liste şablonlarından birine dayalı madde işaretli bir liste oluşturun
        //ve bunu belge oluşturucunun geçerli paragrafına uygulayın.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Bu, liste biçimlendirmesini durdurmanın bir yoludur.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Şablona dayalı bir liste oluşturun.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // İlk listeyi yeniden kullanmak için, orijinal liste biçimlendirmesinin bir kopyasını oluşturarak numaralandırmayı yeniden başlatmamız gerekir.
        List list2 = doc.getLists().addCopy(list1);
        // Yeni listeyi, yeni bir başlangıç numarası belirlemek de dahil olmak üzere, istediğimiz şekilde değiştirebiliriz.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## Çözüm

Tebrikler! Aspose.Words for Java'da listelerle etkili bir şekilde nasıl çalışacağınızı öğrendiniz. Listeler, belgelerinizdeki içerikleri düzenlemek ve sunmak için çok önemlidir. Her bölümde listeleri yeniden başlatmanız veya liste düzeyleri belirtmeniz gerekip gerekmediğine bakılmaksızın, Aspose.Words for Java profesyonel görünümlü belgeler oluşturmanız için ihtiyaç duyduğunuz araçları sağlar.

Artık bu özellikleri belge oluşturma ve biçimlendirme görevlerinizi geliştirmek için güvenle kullanabilirsiniz. Herhangi bir sorunuz varsa veya daha fazla yardıma ihtiyacınız varsa, çekinmeden bize ulaşın[Aspose topluluk forumu](https://forum.aspose.com/) destek için.

## SSS

### Java için Aspose.Words'ü nasıl yüklerim?
 Java için Aspose.Words'ü şu adresten indirebilirsiniz:[Burada](https://releases.aspose.com/words/java/) ve dokümanlardaki kurulum talimatlarını izleyin.

### Listelerin numaralandırma biçimini özelleştirebilir miyim?
Evet, Aspose.Words for Java, liste numaralandırma biçimlerini özelleştirmek için kapsamlı seçenekler sunar. Ayrıntılar için API belgelerine başvurabilirsiniz.

### Aspose.Words for Java en son Word belge standartlarıyla uyumlu mudur?
Evet, Aspose.Words for Java'yı ISO 29500 dahil olmak üzere çeşitli Word belge standartlarına uyacak şekilde yapılandırabilirsiniz.

### Aspose.Words for Java kullanarak tablolar ve resimler içeren karmaşık belgeler oluşturabilir miyim?
Kesinlikle! Aspose.Words for Java, tablolar, resimler ve daha fazlası dahil olmak üzere gelişmiş belge biçimlendirmesini destekler. Örnekler için belgeleri kontrol edin.

### Aspose.Words for Java için geçici lisansı nereden alabilirim?
Geçici bir lisans alabilirsiniz[Burada](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
