---
"description": "Aspose.Words for Java'da belgeleri metin dosyaları olarak nasıl kaydedeceğinizi öğrenin. Java kod örnekleriyle adım adım kılavuzumuzu izleyin."
"linktitle": "Belgeleri Metin Dosyaları Olarak Kaydetme"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Aspose.Words for Java'da Belgeleri Metin Dosyaları Olarak Kaydetme"
"url": "/tr/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java'da Belgeleri Metin Dosyaları Olarak Kaydetme


## Aspose.Words for Java'da Belgeleri Metin Dosyaları Olarak Kaydetmeye Giriş

Bu eğitimde, Aspose.Words for Java kütüphanesini kullanarak belgeleri metin dosyaları olarak nasıl kaydedeceğimizi inceleyeceğiz. Aspose.Words, Word belgeleriyle çalışmak için güçlü bir Java API'sidir ve düz metin de dahil olmak üzere belgeleri farklı biçimlerde kaydetmek için çeşitli seçenekler sunar. Bunu başarmak için adımları ele alacağız ve bu arada örnek Java kodu sağlayacağız.

## Ön koşullar

Başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

- Sisteminizde Java Development Kit (JDK) yüklü.
- Projenize entegre edilmiş Aspose.Words for Java kütüphanesi. Buradan indirebilirsiniz [Burada](https://releases.aspose.com/words/java/).
- Temel Java programlama bilgisi.

## Adım 1: Bir Belge Oluşturun

Bir belgeyi metin dosyası olarak kaydetmek için, öncelikle Aspose.Words kullanarak bir belge oluşturmamız gerekir. İşte biraz içerikle bir belge oluşturmak için basit bir Java kod parçası:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Bu kodda yeni bir belge oluşturuyoruz ve içine farklı dillerdeki metinler de dahil olmak üzere bazı metinler ekliyoruz.

## Adım 2: Metin Kaydetme Seçeneklerini Tanımlayın

Sonra, belgenin bir metin dosyası olarak nasıl kaydedileceğini belirten metin kaydetme seçeneklerini tanımlamamız gerekir. Bidi işaretleri, liste girintisi ve daha fazlası gibi çeşitli ayarları yapılandırabiliriz. İki örneğe bakalım:

### Örnek 1: Bidi İşaretlerinin Eklenmesi

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Bu örnekte, bir tane oluşturuyoruz `TxtSaveOptions` nesneyi seçin ve ayarlayın `AddBidiMarks` mülk `true` metin çıktısına bidi işaretleri eklemek için.

### Örnek 2: Liste Girintisi için Sekme Karakterinin Kullanılması

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Burada, liste girintisi için 1 sayısıyla sekme karakteri kullanacak şekilde kaydetme seçeneklerini yapılandırıyoruz.

## Adım 3: Belgeyi Metin Olarak Kaydedin

Artık metin kaydetme seçeneklerini tanımladığımıza göre, belgeyi bir metin dosyası olarak kaydedebiliriz. Aşağıdaki kod bunu nasıl yapacağınızı gösterir:

```java
doc.save("output.txt", saveOptions);
```

Yer değiştirmek `"output.txt"` metin dosyasını kaydetmek istediğiniz dosya yolunu belirtin.

## Aspose.Words for Java'da Belgeleri Metin Dosyaları Olarak Kaydetmek İçin Tam Kaynak Kodu

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Üç düzeyde girintiye sahip bir liste oluşturun.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Üç düzeyde girintiye sahip bir liste oluşturun.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Çözüm

Bu eğitimde, Java için Aspose.Words'de belgeleri metin dosyaları olarak nasıl kaydedeceğimizi öğrendik. Bir belge oluşturma, metin kaydetme seçeneklerini tanımlama ve belgeyi metin biçiminde kaydetme adımlarını ele aldık. Aspose.Words, belgeleri kaydetme konusunda kapsamlı esneklik sağlayarak çıktıyı özel gereksinimlerinize göre uyarlamanıza olanak tanır.

## SSS

### Metin çıktısına bidi işareti nasıl eklerim?

Metin çıktısına bidi işaretleri eklemek için, `AddBidiMarks` mülkiyeti `TxtSaveOptions` ile `true`. Örneğin:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Liste girinti karakterini özelleştirebilir miyim?

Evet, liste girinti karakterini yapılandırarak özelleştirebilirsiniz. `ListIndentation` mülkiyeti `TxtSaveOptions`Örneğin, liste girintisi için sekme karakteri kullanmak üzere aşağıdakileri yapabilirsiniz:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words for Java çok dilli metinleri işlemek için uygun mudur?

Evet, Aspose.Words for Java çok dilli metinleri işlemek için uygundur. Çeşitli dilleri ve karakter kodlamalarını destekler, bu da onu farklı dillerdeki belgelerle çalışmak için çok yönlü bir seçenek haline getirir.

### Aspose.Words for Java için daha fazla dokümana ve kaynağa nasıl erişebilirim?

Aspose.Words for Java için kapsamlı dokümanları ve kaynakları Aspose dokümantasyon web sitesinde bulabilirsiniz: [Java Belgeleri için Aspose.Words](https://reference.aspose.com/words/java/).

### Aspose.Words for Java'yı nereden indirebilirim?

Aspose.Words for Java kütüphanesini Aspose web sitesinden indirebilirsiniz: [Java için Aspose.Words'ü indirin](https://releases.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}