---
date: 2026-01-09
description: Aspose.Words for Java kullanarak OOXML formatında belgeleri kaydederken
  docx dosyasını şifrelemeyi ve sıkıştırma seviyesini değiştirmeyi öğrenin.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Şifreyle docx dosyasını şifrele – OOXML'i Aspose.Words Java ile kaydet
url: /tr/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Şifreli docx – Aspose.Words Java ile OOXML kaydetme

## Aspose.Words for Java'da Belgeleri OOXML Formatında Kaydetmeye Giriş

Bu kılavuzda, **encrypt docx with password** nasıl yapılacağını ve Aspose.Words for Java kullanarak belgeleri OOXML formatında nasıl kaydedeceğinizi öğreneceksiniz. OOXML (Office Open XML), Microsoft Word ve birçok diğer ofis uygulaması tarafından kullanılan modern dosya formatıdır. En yaygın seçenekleri—parola koruması, uyumluluk seviyeleri, özellik güncellemeleri, eski karakter işleme ve **how to change compression level**—adım adım inceleyeceğiz, böylece çıktıyı tam ihtiyaçlarınıza göre özelleştirebileceksiniz.

## Hızlı Yanıtlar
- **Bir Word dosyasını nasıl koruyabilirim?** Kaydetmeden önce `OoxmlSaveOptions.setPassword("yourPassword")` kullanın.  
- **Hangi OOXML uyumluluk seviyesini seçmeliyim?** Modern Office sürümleriyle maksimum uyumluluk için ISO 29500 2008 Strict.  
- **Eski kontrol karakterlerini koruyabilir miyim?** Evet, `setKeepLegacyControlChars(true)` etkinleştirin.  
- **Sıkıştırma seviyesini nasıl değiştiririm?** Gerekli olduğunda `setCompressionLevel(CompressionLevel.SUPER_FAST)` veya `MAXIMUM` ayarlayın.  
- **Bu seçenekler dosya boyutunu etkiler mi?** Sıkıştırma seviyesi ve eski karakter işleme, son .docx boyutunu belirgin şekilde değiştirebilir.

## “encrypt docx with password” nedir?

Bir DOCX dosyasını şifrelemek, belgenin AES‑256 şifreleme ile kaydedildiği ve Word ya da uyumlu bir görüntüleyicide açmak için bir parola gerektirdiği anlamına gelir. Bu, dosyalar e-posta, bulut depolama veya intranet portalları aracılığıyla paylaşıldığında gizli bilgileri korumak için gereklidir.

## Neden OOXML kaydetme seçeneklerini kullanmalısınız?

- **Güvenlik:** Parola koruması yetkisiz erişimi önler.  
- **Uyumluluk:** Uyumluluk ayarları dosyanın farklı Word sürümlerinde çalışmasını sağlar.  
- **Performans:** Sıkıştırmayı ayarlamak kaydetme hızını artırabilir veya dosya boyutunu azaltabilir.  
- **Koruma:** Eski kontrol karakterlerini tutmak, eski belgeleri dönüştürürken özgünlüğün korunmasını sağlar.

## Gereksinimler
- Projenize eklenmiş Aspose.Words for Java kütüphanesi (Maven/Gradle veya manuel JAR).  
- Java 8 veya üzeri.  
- İşlemek istediğiniz bir kaynak belge (`.docx` veya `.doc`).

## Parola Şifrelemesiyle Belge Kaydetme

Belgenizi OOXML formatında kaydederken bir parola ile şifreleyebilirsiniz. İşte nasıl yapılacağı:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

> **Pro ipucu:** Güçlü bir parola seçin ve güvenli bir şekilde saklayın; parola şifreli dosyadan geri alınamaz.

## OOXML Uyumluluğunu Ayarlama

Belgeyi kaydederken OOXML uyumluluk seviyesini belirtebilirsiniz. Örneğin, ISO 29500:2008 (Strict) olarak ayarlayabilirsiniz. İşte nasıl:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## “Last Saved Time” Özelliğini Güncelleme

Belgeyi kaydederken "Last Saved Time" özelliğini güncellemeyi seçebilirsiniz. İşte nasıl:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Eski Kontrol Karakterlerini Tutma

Belgenizde eski kontrol karakterleri varsa, kaydederken bunları tutmayı seçebilirsiniz. İşte nasıl:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## OOXML Kaydederken Sıkıştırma Seviyesini Değiştirme

Belgeyi kaydederken sıkıştırma seviyesini ayarlayabilirsiniz. Örneğin, minimum sıkıştırma için `SUPER_FAST` veya en küçük dosya boyutu için `MAXIMUM` olarak ayarlayabilirsiniz. İşte nasıl:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

Bunlar, Aspose.Words for Java kullanarak OOXML formatında belgeleri kaydederken kullanabileceğiniz temel seçenek ve ayarlardan bazılarıdır. Daha fazla seçeneği keşfetmek ve belge‑kaydetme sürecinizi ihtiyaçlarınıza göre özelleştirmekten çekinmeyin.

## Aspose.Words for Java'da Belgeleri OOXML Formatında Kaydetmek için Tam Kaynak Kodu

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

## Sonuç

Bu kapsamlı kılavuzda, **encrypt docx with password** nasıl yapılacağını ve Aspose.Words for Java kullanarak belgeleri OOXML formatında nasıl kaydedeceğimizi inceledik. Dosyalarınızı korumanız, sıkı OOXML uyumluluğunu sağlamanız, belge özelliklerini güncellemeniz, eski kontrol karakterlerini korumanız veya **change compression level** gibi ihtiyaçlarınız olsun, Aspose.Words gereksinimlerinizi karşılamak için çok yönlü bir araç seti sunar.

## Sıkça Sorulan Sorular

**S: Parola korumalı bir belgeden parolayı nasıl kaldırırım?**  
C: Belgeyi doğru parola ile açın, ardından `OoxmlSaveOptions` içinde parola belirtmeden kaydedin. Bu, korumasız bir kopya oluşturur.

**S: OOXML formatında bir belgeyi kaydederken özel özellikler ayarlayabilir miyim?**  
C: Evet. `save()` çağrısından önce `Document` nesnesi üzerinde `BuiltInDocumentProperties` ve `CustomDocumentProperties` kullanın.

**S: OOXML formatında bir belgeyi kaydederken varsayılan sıkıştırma seviyesi nedir?**  
C: Varsayılan `CompressionLevel.NORMAL`dır. Hız için `SUPER_FAST` veya en küçük dosya boyutu için `MAXIMUM` seçebilirsiniz.

**S: `keepLegacyControlChars` etkinleştirilmesi modern Word sürümleriyle uyumluluğu etkiler mi?**  
C: Modern Word, eski kontrol karakterlerine sahip dosyaları açabilir, ancak bazı eski özellikler farklı görünebilir. Bu seçeneği yalnızca orijinal içeriği tam olarak korumanız gerektiğinde kullanın.

**S: Tek bir çağrıda birden fazla kaydetme seçeneğini (ör. parola + sıkıştırma) birleştirmek mümkün mü?**  
C: Kesinlikle. `doc.save()`'e geçirmeden önce tek bir `OoxmlSaveOptions` örneğinde tüm istenen özellikleri yapılandırın.

**Son Güncelleme:** 2026-01-09  
**Test Edilen Versiyon:** Aspose.Words for Java 24.12  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}