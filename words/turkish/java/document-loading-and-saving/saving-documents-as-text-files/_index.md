---
date: 2025-12-24
description: Aspose.Words for Java kullanarak Word belgelerinden düz metin dosyası
  oluşturmayı öğrenin. Bu kılavuz, Word'ü txt'ye nasıl dönüştüreceğinizi, sekme girintisi
  kullanmayı ve Word'ü txt olarak kaydetmeyi gösterir.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java ile düz metin dosyası nasıl oluşturulur
url: /tr/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile düz metin dosyası nasıl oluşturulur

## Aspose.Words for Java'da Belgeleri Metin Dosyaları Olarak Kaydetmeye Giriş

Bu öğreticide, Aspose.Words for Java kütüphanesini kullanarak bir Word belgesinden **düz metin dosyası nasıl oluşturulur** öğreneceksiniz. **convert word to txt** yapmanız, rapor üretimini otomatikleştirmeniz veya yalnızca ham metni daha fazla işleme için çıkarmanız gerekse, bu kılavuz belge oluşturulmasından **use tab indentation** gibi kaydetme seçeneklerinin ince ayarına kadar tüm süreci adım adım gösterir. Hadi başlayalım!

## Hızlı Yanıtlar
- **Belge oluşturmak için birincil sınıf nedir?** `Document` from Aspose.Words.  
- **Sağdan sola diller için bidi işaretlerini ekleyen seçenek hangisidir?** `TxtSaveOptions.setAddBidiMarks(true)`.  
- **Liste öğelerini sekmelerle nasıl girintileyebilirim?** Set `ListIndentation.Character` to `'\t'`.  
- **Geliştirme için lisansa ihtiyacım var mı?** A free trial works for testing; a license is required for production.  
- **Dosyayı özel bir ad ve yol ile kaydedebilir miyim?** Yes—pass the full path to `doc.save()`.

## Önkoşullar

Başlamadan önce aşağıdaki önkoşulların yerine getirildiğinden emin olun:

- Sisteminizde Java Development Kit (JDK) kurulu.  
- Projenize Aspose.Words for Java kütüphanesini entegre edin. [buradan](https://releases.aspose.com/words/java/) indirebilirsiniz.  
- Java programlamaya temel bilgi.

## Adım 1: Belge Oluşturma

**save word as txt** yapmak için önce bir `Document` örneğine ihtiyacımız var. Aşağıda, belge oluşturan ve çok dilli birkaç satır metin yazan basit bir Java kod parçacığı bulunmaktadır:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Bu kodda yeni bir belge oluşturuyor, İngilizce, İbranice ve Arapça metin ekliyor ve İbranice paragraf için sağdan sola biçimlendirmeyi etkinleştiriyoruz.

## Adım 2: Metin Kaydetme Seçeneklerini Tanımlama

Şimdi, belgenin düz metin dosyası olarak nasıl kaydedileceğini yapılandırıyoruz. Aspose.Words, bidi işaretlerinden liste girintilemesine kadar her şeyi kontrol etmenizi sağlayan `TxtSaveOptions` sınıfını sunar.

### Örnek 1: Bidi İşaretleri Ekleme (txt'yi doğru RTL desteğiyle kaydetme)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

`AddBidiMarks` değerini `true` olarak ayarlamak, sağdan sola karakterlerin **düz metin dosyası** içinde doğru şekilde temsil edilmesini sağlar.

### Örnek 2: Liste Girintilemesi için Sekme Karakteri Kullanma (sekme girintisi kullan)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Burada Aspose.Words'e her liste seviyesinin önüne bir sekme karakteri (`'\t'`) eklemesini söylüyoruz; bu sayede metin çıktısı daha okunaklı olur.

## Adım 3: Belgeyi Metin Olarak Kaydetme

Kaydetme seçenekleri hazır olduğuna göre, belgeyi **düz metin dosyası** olarak kalıcı hâle getirebilirsiniz:

```java
doc.save("output.txt", saveOptions);
```

`"output.txt"` ifadesini, dosyanın kaydedilmesini istediğiniz tam yol ile değiştirin.

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
        // Create a list with three levels of indentation.
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
        // Create a list with three levels of indentation.
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

## Yaygın Sorunlar ve Çözümler

| Sorun | Çözüm |
|-------|----------|
| **Bidi karakterleri bozuk metin olarak görünüyor** | Ensure `setAddBidiMarks(true)` is enabled and the output file is opened with UTF‑8 encoding. |
| **Liste girintisi yanlış görünüyor** | Verify `ListIndentation.Count` and `Character` are set to the desired values (tab `'\t'` or space `' '` ). |
| **Dosya oluşturulmadı** | Check that the directory path exists and the application has write permissions. |

## Sık Sorulan Sorular

### Metin çıktısına nasıl bidi işaretleri ekleyebilirim?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Liste girintileme karakterini özelleştirebilir miyim?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words for Java çok dilli metinleri işlemek için uygun mu?

Evet, Aspose.Words for Java geniş bir dil ve karakter kodlaması yelpazesini destekler; bu da çok dilli içeriği çıkarmak ve düz metin olarak kaydetmek için idealdir.

### Aspose.Words for Java için daha fazla dokümantasyon ve kaynağa nasıl erişebilirim?

Aspose.Words for Java Documentation sayfasında kapsamlı dokümantasyon ve kaynakları bulabilirsiniz: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Aspose.Words for Java'ı nereden indirebilirim?

Kütüphaneyi resmi siteden indirebilirsiniz: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### Toplu işlemde **convert word to txt** yapmam gerekirse ne yapmalıyım?

Yukarıdaki kodu, her `.docx` dosyasını yükleyen, aynı `TxtSaveOptions` uygulayan ve her birini `.txt` olarak kaydeden bir döngü içinde sarın. Her yinelemeden sonra `Document` nesnelerini serbest bırakarak kaynakları yönettiğinizden emin olun.

### API, dosya yerine doğrudan bir akısa (stream) kaydetmeyi destekliyor mu?

Evet, `doc.save(outputStream, saveOptions)` ile bir `OutputStream`e geçerek bellek içi işleme veya web hizmetleriyle entegrasyon sırasında doğrudan akısa kaydedebilirsiniz.

**Son Güncelleme:** 2025-12-24  
**Test Edilen Versiyon:** Aspose.Words for Java 24.12 (latest)  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}