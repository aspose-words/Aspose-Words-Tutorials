---
"description": "Aspose.Words for Java ile belgeleri OOXML formatında nasıl kaydedeceğinizi öğrenin. Dosyalarınızı zahmetsizce güvenceye alın, optimize edin ve özelleştirin."
"linktitle": "Belgeleri OOXML Formatında Kaydetme"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Aspose.Words for Java'da Belgeleri OOXML Formatında Kaydetme"
"url": "/tr/java/document-loading-and-saving/saving-documents-as-ooxml-format/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java'da Belgeleri OOXML Formatında Kaydetme


## Aspose.Words for Java'da Belgeleri OOXML Biçiminde Kaydetmeye Giriş

Bu kılavuzda, Aspose.Words for Java kullanarak belgelerin OOXML formatında nasıl kaydedileceğini inceleyeceğiz. OOXML (Office Open XML), Microsoft Word ve diğer ofis uygulamaları tarafından kullanılan bir dosya biçimidir. Belgeleri OOXML formatında kaydetmek için çeşitli seçenekleri ve ayarları ele alacağız.

## Ön koşullar

Başlamadan önce projenizde Aspose.Words for Java kütüphanesinin kurulu olduğundan emin olun.

## Bir Belgeyi Parola Şifreleme ile Kaydetme

Belgenizi OOXML formatında kaydederken bir parola ile şifreleyebilirsiniz. Bunu nasıl yapabileceğiniz aşağıda açıklanmıştır:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Belgeyi yükle
Document doc = new Document("Document.docx");

// OoxmlSaveOptions'ı oluşturun ve parolayı ayarlayın
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Belgeyi şifreleyerek kaydedin
doc.save("EncryptedDoc.docx", saveOptions);
```

## OOXML Uyumluluğunu Ayarlama

Belgeyi kaydederken OOXML uyumluluk düzeyini belirtebilirsiniz. Örneğin, bunu ISO 29500:2008 (Strict) olarak ayarlayabilirsiniz. İşte nasıl:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Belgeyi yükle
Document doc = new Document("Document.docx");

// Word 2016 için optimize edin
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// OoxmlSaveOptions'ı oluşturun ve uyumluluk düzeyini ayarlayın
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Belgeyi uyumluluk ayarıyla kaydedin
doc.save("ComplianceDoc.docx", saveOptions);
```

## Son Kaydedilen Zaman Özelliğini Güncelliyor

Belgeyi kaydederken "Son Kaydedilen Zaman" özelliğini güncellemeyi seçebilirsiniz. İşte nasıl:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Belgeyi yükle
Document doc = new Document("Document.docx");

// OoxmlSaveOptions'ı oluşturun ve Son Kaydedilen Zaman özelliğini güncellemeyi etkinleştirin
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Belgeyi güncellenmiş özellik ile kaydedin
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Miras Kontrol Karakterlerini Koruma

Belgeniz eski denetim karakterleri içeriyorsa, kaydederken bunları tutmayı seçebilirsiniz. İşte nasıl:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Eski denetim karakterlerini içeren bir belgeyi yükleyin
Document doc = new Document("LegacyControlChars.doc");

// OoxmlSaveOptions'ı FLAT_OPC biçimiyle oluşturun ve eski kontrol karakterlerinin tutulmasını etkinleştirin
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Belgeyi eski denetim karakterleriyle kaydedin
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Sıkıştırma Seviyesini Ayarlama

Belgeyi kaydederken sıkıştırma seviyesini ayarlayabilirsiniz. Örneğin, minimum sıkıştırma için SUPER_FAST olarak ayarlayabilirsiniz. İşte nasıl:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Belgeyi yükle
Document doc = new Document("Document.docx");

// OoxmlSaveOptions'ı oluşturun ve sıkıştırma düzeyini ayarlayın
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Belgeyi belirtilen sıkıştırma düzeyiyle kaydedin
doc.save("FastCompressionDoc.docx", saveOptions);
```

Bunlar, Aspose.Words for Java kullanarak belgeleri OOXML formatında kaydederken kullanabileceğiniz bazı temel seçenekler ve ayarlardır. Daha fazla seçeneği keşfetmekten ve belge kaydetme sürecinizi gerektiği gibi özelleştirmekten çekinmeyin.

## Aspose.Words for Java'da Belgeleri OOXML Formatında Kaydetmek İçin Tam Kaynak Kodu

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## Çözüm

Bu kapsamlı kılavuzda, Aspose.Words for Java kullanarak belgeleri OOXML formatında nasıl kaydedeceğinizi inceledik. Belgelerinizi parolalarla şifrelemeniz, belirli OOXML standartlarına uyumu sağlamanız, belge özelliklerini güncellemeniz, eski kontrol karakterlerini korumanız veya sıkıştırma seviyelerini ayarlamanız gerekip gerekmediğine bakılmaksızın, Aspose.Words gereksinimlerinizi karşılamak için çok yönlü bir araç seti sunar.

## SSS

### Parola korumalı bir belgeden parola korumasını nasıl kaldırabilirim?

Parola korumalı bir belgeden parola korumasını kaldırmak için, belgeyi doğru parolayla açabilir ve ardından kaydetme seçeneklerinde parola belirtmeden kaydedebilirsiniz. Bu, belgeyi parola koruması olmadan kaydedecektir.

### Bir belgeyi OOXML formatında kaydederken özel özellikler ayarlayabilir miyim?

Evet, bir belgeyi OOXML biçiminde kaydetmeden önce özel özellikler ayarlayabilirsiniz. `BuiltInDocumentProperties` Ve `CustomDocumentProperties` Yazar, başlık, anahtar kelimeler ve özel özellikler gibi çeşitli özellikleri ayarlamak için sınıflar.

### Bir belgeyi OOXML formatında kaydederken varsayılan sıkıştırma düzeyi nedir?

Aspose.Words for Java kullanılarak bir belge OOXML biçiminde kaydedilirken varsayılan sıkıştırma düzeyi: `NORMAL`Sıkıştırma seviyesini değiştirebilirsiniz `SUPER_FAST` veya `MAXIMUM` ihtiyaç duyulduğu takdirde.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}