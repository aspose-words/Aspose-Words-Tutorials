---
date: 2025-12-29
description: Aspose.Words for Java kaydetme seçeneklerini kullanarak docx dosyasını
  şifreyle nasıl şifreleyeceğinizi öğrenin. OOXML dosyalarınızı sorunsuz bir şekilde
  güvenli, optimize ve özelleştirin.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java Kullanarak DOCX'i Şifreyle Şifreleme
url: /tr/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# DOCX'i Parola ile Şifreleme Aspose.Words for Java Kullanarak

Bu rehberde Aspose.Words for Java kullanarak OOXML formatında belgeleri kaydederken **docx'i parola ile nasıl şifreleyeceğinizi** keşfedeceksiniz. Gizli raporları koruyor ya da sözleşme taslaklarını güvenli hale getiriyor olun, aşağıdaki adımlar parola korumasını nasıl uygulayacağınızı ve diğer OOXML kaydetme seçeneklerini nasıl ince ayar yapacağınızı tam olarak gösterir.

## Hızlı Yanıtlar
- **Bir DOCX dosyasını parola ile şifreleyebilir miyim?** Evet, kaydetmeden önce `OoxmlSaveOptions.setPassword()` kullanın.  
- **OOXML kaydetme ayarlarını hangi sınıf kontrol eder?** `OoxmlSaveOptions` (Aspose.Words'un bir parçası).  
- **Parola koruması için lisansa ihtiyacım var mı?** Üretim kullanımı için geçerli bir Aspose.Words lisansı gereklidir.  
- **Şifrelemeyi uyumluluk ayarlarıyla birleştirebilir miyim?** Kesinlikle – aynı `OoxmlSaveOptions` örneğinde hem `setPassword` hem de `setCompliance` ayarlarını yapın.  
- **Mevcut sıkıştırma seviyeleri nelerdir?** `CompressionLevel` aracılığıyla `NORMAL`, `SUPER_FAST` ve `MAXIMUM`.

## “docx'i parola ile şifreleme” nedir?
Bir DOCX dosyasını şifrelemek, dosyanın içeriğinin şifreli bir biçimde saklanması ve yalnızca doğru parola girildiğinde açılabilmesi anlamına gelir. Bu, yetkisiz erişime karşı hassas bilgileri korur ve parola sağlandığında standart Word araçlarının dosyayı açmasına izin verir.

## Şifreleme için Aspose.Words kaydetme seçeneklerini neden kullanmalısınız?
Aspose.Words, **aspose words save options** adlı zengin bir seçenek seti sunar; bu sayede yalnızca şifrelemeyi değil, aynı zamanda uyumluluk seviyelerini, sıkıştırmayı ve eski karakter işleme seçeneklerini de Java kodundan kontrol edebilirsiniz. Bu, manuel son‑işlemeyi veya üçüncü‑taraf araçlarını ortadan kaldırır.

## Önkoşullar
- Java Development Kit (JDK 8 veya üzeri)  
- Projenize eklenmiş Aspose.Words for Java kütüphanesi (Maven/Gradle ya da JAR)  
- Üretim için geçerli bir Aspose.Words lisansı (değerlendirme için isteğe bağlı)

## Parola Şifrelemesiyle Belge Kaydetme

Belgenizi OOXML formatında kaydederken parola ile şifreleyebilirsiniz. İşte nasıl yapılacağı:

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

## OOXML Uyumluluğunu Ayarlama

Belgeyi kaydederken OOXML uyumluluk seviyesini belirtebilirsiniz. Örneğin, ISO 29500:2008 (Strict) olarak ayarlayabilirsiniz. İşte nasıl:

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

## Son Kaydedilen Zaman Özelliğini Güncelleme

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

## Eski Kontrol Karakterlerini Korumak

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

## Sıkıştırma Seviyesini Ayarlama

Belgeyi kaydederken sıkıştırma seviyesini ayarlayabilirsiniz. Örneğin, minimum sıkıştırma için **SUPER_FAST** olarak ayarlayabilirsiniz. İşte nasıl:

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

Bunlar, Aspose.Words for Java kullanarak OOXML formatında belge kaydederken kullanabileceğiniz temel seçenek ve ayarlardan bazılarıdır. Daha fazla seçeneği keşfetmekten ve belge‑kaydetme sürecinizi ihtiyacınıza göre özelleştirmekten çekinmeyin.

## Aspose.Words for Java ile Belgeleri OOXML Formatında Kaydetmek İçin Tam Kaynak Kodu

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

Bu kapsamlı rehberde, Aspose.Words for Java kullanarak **docx'i parola ile nasıl şifreleyeceğinizi** ve OOXML kaydetme seçeneklerinin bir dizi ayarını ince ayar yapmayı inceledik. Gizli içeriği korumanız, katı ISO uyumluluğunu karşılamanız, eski karakterleri korumanız veya sıkıştırmayı kontrol etmeniz gerekse, kütüphane aynı `OoxmlSaveOptions` API'si üzerinden ayrıntılı kontrol sağlar.

## Sıkça Sorulan Sorular

**S: Parola korumalı bir belgede parola korumasını nasıl kaldırırım?**  
C: Belgeyi doğru parola ile açın, ardından `setPassword` çağırmadan tekrar kaydedin. Yeni dosya korumasız olacaktır.

**S: OOXML formatında belge kaydederken özel özellikler ayarlayabilir miyim?**  
C: Evet. `save` çağırmadan önce `Document` nesnesi üzerinde `BuiltInDocumentProperties` veya `CustomDocumentProperties` kullanın.

**S: OOXML formatında belge kaydederken varsayılan sıkıştırma seviyesi nedir?**  
C: Varsayılan `NORMAL`dır. Hız için `SUPER_FAST` veya daha küçük dosya boyutu için `MAXIMUM` seçebilirsiniz.

**S: aspose words save options eski Word sürümleriyle çalışır mı?**  
C: Evet. `MsWordVersion` ve uyumluluk ayarlarını değiştirerek Word 2007‑2019 hedefleyebilir ve uyumluluğu sağlayabilirsiniz.

**S: Tek bir işlemde birden fazla kaydetme seçeneğini birleştirmek mümkün mü?**  
C: Kesinlikle. Tek bir `OoxmlSaveOptions` örneği oluşturun, istenen tüm özellikleri (parola, uyumluluk, sıkıştırma vb.) ayarlayın ve `doc.save()` metoduna geçirin.

---

**Son Güncelleme:** 2025-12-29  
**Test Edilen Versiyon:** Aspose.Words for Java 24.12  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}