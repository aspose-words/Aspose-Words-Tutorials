---
date: 2025-12-20
description: Aspose.Words for Java ile HTML'yi nasıl yükleyeceğinizi ve HTML'yi DOCX'e
  nasıl dönüştüreceğinizi öğrenin. Adım adım rehber, DOCX dosyalarını nasıl kaydedeceğinizi
  ve yapılandırılmış belge etiketlerini nasıl kullanacağınızı gösterir.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java kullanarak HTML'yi yükleme ve DOCX olarak kaydetme
url: /tr/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# HTML'yi Yükleme ve Aspose.Words for Java ile DOCX Olarak Kaydetme

## Aspose.Words for Java ile HTML Belgelerini Yükleme ve Kaydetmeye Giriş

Bu makalede, **HTML'yi nasıl yükleyeceğinizi** ve Aspose.Words for Java kütüphanesini kullanarak bir DOCX dosyası olarak nasıl kaydedeceğinizi inceleyeceğiz. Aspose.Words, Word belgelerini programatik olarak manipüle etmenizi sağlayan güçlü bir API'dir ve HTML içe/dışa aktarma konusunda kapsamlı destek sunar. Yükleme seçeneklerini ayarlamaktan sonucu bir Word belgesi olarak kalıcı hale getirmeye kadar tüm süreci adım adım göstereceğiz.

## Hızlı Yanıtlar
- **HTML'yi yüklemek için birincil sınıf nedir?** `Document` ve `HtmlLoadOptions`.
- **Hangi seçenek Structured Document Tags'i etkinleştirir?** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **HTML'yi tek adımda DOCX'e dönüştürebilir miyim?** Evet – HTML'yi yükleyin ve `doc.save(...".docx")` çağrısını yapın.
- **Geliştirme için lisansa ihtiyacım var mı?** Test için ücretsiz deneme sürümü yeterlidir; üretim ortamı için ticari lisans gereklidir.
- **Hangi Java sürümü gereklidir?** Java 8 veya üzeri desteklenir.

## Aspose.Words bağlamında “HTML'yi nasıl yüklenir” nedir?
HTML'yi yüklemek, bir HTML dizesini veya dosyasını okuyup Aspose.Words `Document` nesnesine dönüştürmek anlamına gelir. Bu nesne daha sonra düzenlenebilir, biçimlendirilebilir veya API'nin desteklediği herhangi bir formata (DOCX, PDF, RTF vb.) kaydedilebilir.

## HTML‑to‑DOCX dönüşümü için Aspose.Words neden tercih edilmeli?
- **Düzeni korur** – tablolar, listeler ve görseller olduğu gibi kalır.
- **Structured Document Tags'i destekler** – Word içinde içerik denetimleri oluşturmak için idealdir.
- **Microsoft Office gerekmez** – herhangi bir sunucu veya bulut ortamında çalışır.
- **Yüksek performans** – büyük HTML dosyalarını hızlı bir şekilde işler.

## Önkoşullar

1. **Aspose.Words for Java Kütüphanesi** – [buradan](https://releases.aspose.com/words/java/) indirin.
2. **Java Geliştirme Ortamı** – JDK 8+ yüklü ve yapılandırılmış olmalı.
3. **Java I/O konusunda temel bilgi** – HTML dizesini beslemek için `ByteArrayInputStream` kullanacağız.

## HTML Belgelerini Nasıl Yüklenir

Aşağıda, **structured document tag** özelliğini etkinleştirerek bir HTML parçacığını yükleyen kısa bir örnek yer almaktadır.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**Açıklama**

- Basit bir `<select>` denetimi içeren bir `HTML` dizesi oluşturuyoruz.
- `HtmlLoadOptions`, HTML'nin nasıl yorumlanacağını belirlememizi sağlar. Tercih edilen denetim tipini `STRUCTURED_DOCUMENT_TAG` olarak ayarlamak, Aspose.Words'in HTML form denetimlerini Word içerik denetimlerine dönüştürmesini sağlar.
- `Document` yapıcı yöntemi, UTF‑8 kodlamasıyla bir `ByteArrayInputStream` üzerinden HTML'yi okur.

## DOCX Olarak Nasıl Kaydedilir (HTML'den DOCX'e Dönüştürme)

HTML bir `Document` nesnesine yüklendikten sonra, DOCX dosyası olarak kaydetmek oldukça basittir:

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

`"Your Directory Path"` ifadesini, çıktının oluşturulmasını istediğiniz gerçek klasör yolu ile değiştirin.

## HTML Belgelerini Yükleme ve Kaydetme İçin Tam Kaynak Kodu

Aşağıda, yükleme ve kaydetme adımlarını birleştiren, doğrudan çalıştırılabilir tam örnek bulunmaktadır. IDE'nize kopyalayıp yapıştırabilirsiniz.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## Yaygın Hatalar & İpuçları

| Sorun | Neden Oluşur | Nasıl Çözülür |
|-------|--------------|---------------|
| **Eksik yazı tipleri** | HTML, sunucuda yüklü olmayan yazı tiplerine referans verir. | `FontSettings` ile DOCX'e yazı tiplerini gömün veya gerekli yazı tiplerinin sunucuda bulunmasını sağlayın. |
| **Görseller gösterilmiyor** | Göreceli görsel yolları çözülemez. | Mutlak URL'ler kullanın veya görselleri bir `MemoryStream` içine yükleyip `HtmlLoadOptions.setImageSavingCallback` ile ayarlayın. |
| **Denetim tipi dönüştürülmüyor** | `setPreferredControlType` ayarlanmamış veya yanlış enum kullanılmış. | `HtmlControlType.STRUCTURED_DOCUMENT_TAG` kullandığınızdan emin olun. |
| **Kodlama sorunları** | HTML dizesi farklı bir karakter setiyle kodlanmış. | Dizeyi byte dizisine çevirirken her zaman `StandardCharsets.UTF_8` kullanın. |

## Sık Sorulan Sorular

### Aspose.Words for Java nasıl kurulur?
Aspose.Words for Java, [buradan](https://releases.aspose.com/words/java/) indirilebilir. İndirme sayfasındaki kurulum kılavuzunu izleyerek JAR dosyalarını projenizin sınıf yoluna ekleyin.

### Aspose.Words ile karmaşık HTML belgeleri yükleyebilir miyim?
Evet, Aspose.Words for Java, iç içe tablolar, CSS stilleri ve JavaScript içermeyen etkileşimli öğeler gibi karmaşık HTML'leri işleyebilir. `HtmlLoadOptions` (ör. `setLoadImages` veya `setCssStyleSheetFileName`) ayarlarını ihtiyacınıza göre yapılandırın.

### Aspose.Words başka hangi belge formatlarını destekliyor?
Aspose.Words, DOC, DOCX, RTF, HTML, PDF, EPUB, XPS ve daha birçok formatı destekler. API, bu formatların herhangi birine tek satır kodla kaydetme imkanı sunar.

### Aspose.Words kurumsal düzeyde belge otomasyonu için uygun mu?
Kesinlikle. Büyük işletmeler, rapor otomasyonu, toplu belge dönüşümü ve Microsoft Office bağımlılığı olmadan sunucu tarafı belge işleme için Aspose.Words kullanmaktadır.

### Aspose.Words for Java için daha fazla dokümantasyon ve örnek nereden bulunur?
Tam API referansını ve ek öğreticileri Aspose.Words for Java dokümantasyon sitesinde inceleyebilirsiniz: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Son Güncelleme:** 2025-12-20  
**Test Edilen Sürüm:** Aspose.Words for Java 24.12 (yazım anındaki en yeni sürüm)  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}