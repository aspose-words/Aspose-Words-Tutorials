---
date: 2025-12-27
description: Aspose.Words for Java’da LoadOptions ayarını nasıl yapacağınızı, geçici
  klasörü nasıl belirleyeceğinizi, Word sürümünü nasıl ayarlayacağınızı, metafile’ları
  PNG’ye nasıl dönüştüreceğinizi ve şekli matematiğe nasıl dönüştüreceğinizi öğrenerek
  esnek belge işleme sağlayın.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java'da LoadOptions Nasıl Ayarlanır
url: /tr/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java'da LoadOptions Nasıl Ayarlanır

Bu öğreticide, Aspose.Words for Java ile çalışırken çeşitli gerçek‑dünya senaryoları için **LoadOptions nasıl ayarlanır** konusunu adım adım inceleyeceğiz. LoadOptions, bir belgenin nasıl açılacağı üzerinde ince ayar yapmanızı sağlar—kirli alanları güncellemek, şifreli dosyalarla çalışmak, şekilleri Office Math'e dönüştürmek veya kütüphanenin geçici verileri nerede saklayacağını belirtmek gibi. Sonuna geldiğinizde, yükleme davranışını uygulamanızın tam gereksinimlerine göre özelleştirebileceksiniz.

## Hızlı Yanıtlar
- **LoadOptions nedir?** Aspose.Words'un bir belgeyi nasıl yükleyeceğini etkileyen yapılandırma nesnesi.  
- **Alanları yükleme sırasında güncelleyebilir miyim?** Evet—`setUpdateDirtyFields(true)` ayarlayın.  
- **Şifre korumalı bir dosyayı nasıl açarım?** Şifreyi `LoadOptions` yapıcı metoduna geçirin.  
- **Geçici klasörü değiştirmek mümkün mü?** `setTempFolder("path")` kullanın.  
- **Şekilleri Office Math'e dönüştüren yöntem hangisidir?** `setConvertShapeToOfficeMath(true)`.

## LoadOptions Neden Kullanılır?
LoadOptions, yükleme sonrası işleme adımlarını önlemenizi, bellek kullanımını azaltmanızı ve belgenin tam olarak ihtiyacınız olan şekilde yorumlanmasını sağlar. Örneğin, metafile'ları yükleme sırasında PNG'ye dönüştürmek, sonraki rasterleştirme sorunlarını engeller; MS Word sürümünü belirtmek ise eski dosyalarla çalışırken düzenin korunmasına yardımcı olur.

## Ön Koşullar
- Java 17 veya üzeri  
- Aspose.Words for Java (en son sürüm)  
- Üretim kullanımı için geçerli bir Aspose lisansı  

## Adım‑Adım Kılavuz

### Kirli Alanları Güncelleme

Bir belge, düzenlenmiş ancak henüz yenilenmemiş alanlar içeriyorsa, Aspose.Words'a bu alanları yükleme sırasında otomatik olarak güncellemesini söyleyebilirsiniz.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*`setUpdateDirtyFields(true)` çağrısı, belge açılır açılmaz kirli alanların yeniden hesaplanmasını sağlar.*

### Şifreli Belgeyi Yükleme

Kaynak dosyanız şifre korumalıysa, `LoadOptions` örneğini oluştururken şifreyi sağlayın. Farklı bir formata kaydederken yeni bir şifre de belirleyebilirsiniz.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Şekli Office Math'e Dönüştürme

Bazı eski belgeler denklemleri çizim şekilleri olarak saklar. Bu seçeneği etkinleştirmek, bu şekilleri daha sonra düzenlemesi kolay yerel Office Math nesnelerine dönüştürür.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### MS Word Sürümünü Belirtme

Hedef Word sürümünü belirtmek, kütüphanenin doğru render kurallarını seçmesine yardımcı olur; özellikle eski dosya formatlarıyla çalışırken faydalıdır.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Geçici Klasör Kullanma

Büyük belgeler geçici dosyalar (ör. resim çıkarma) oluşturabilir. Bu dosyaları istediğiniz bir klasöre yönlendirebilir, bu da sandbox ortamları için çok yararlıdır.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Uyarı Geri Çağrısı

Yükleme sırasında Aspose.Words, desteklenmeyen özellikler gibi uyarılar üretebilir. Bir geri çağrı (callback) uygulayarak bu olayları kaydedebilir veya yanıt verebilirsiniz.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Metafile'ları PNG'ye Dönüştürme

WMF gibi metafile'lar, yükleme sırasında PNG'ye rasterleştirilebilir; bu, platformlar arası tutarlı render elde etmeyi sağlar.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Aspose.Words for Java'da Load Options ile Çalışmak İçin Tam Kaynak Kodu

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		// Prints warnings and their details as they arise during document loading.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Yaygın Kullanım Senaryoları ve İpuçları

- **Toplu dönüşüm hatları** – `setTempFolder` ile zamanlanmış bir iş birleştirerek yüzlerce dosyayı sistem geçici dizinini doldurmadan işleyin.  
- **Eski belge göçü** – `setMswVersion` ve `setConvertShapeToOfficeMath` birlikte kullanılarak eski mühendislik belgeleri modern formata aktarılırken denklemler korunur.  
- **Güvenli belge işleme** – `loadEncryptedDocument` ile `OdtSaveOptions` kombinasyonu, dosyaları yeni bir şifreyle farklı bir formata yeniden şifrelemenizi sağlar.  

## Sık Sorulan Sorular

**S: Belge yükleme sırasında uyarıları nasıl yönetebilirim?**  
C: *Warning Callback* örneğinde gösterildiği gibi özel bir `IWarningCallback` uygulayın ve `loadOptions.setWarningCallback(...)` ile kaydedin. Böylece uyarıyı kaydedebilir, yok sayabilir veya şiddetine göre iptal edebilirsiniz.

**S: Yükleme sırasında şekilleri Office Math nesnelerine dönüştürebilir miyim?**  
C: Evet—`loadOptions.setConvertShapeToOfficeMath(true)` çağrısını `Document` oluşturulmadan önce yapın. Kütüphane, uyumlu şekilleri otomatik olarak yerel Office Math nesneleriyle değiştirir.

**S: Belge yükleme için MS Word sürümünü nasıl belirtirim?**  
C: `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (veya diğer enum değerlerinden biri) kullanarak Aspose.Words'un hangi Word sürümünün render kurallarını uygulayacağını belirtebilirsiniz.

**S: LoadOptions içindeki `setTempFolder` metodunun amacı nedir?**  
C: Yükleme sırasında (ör. çıkarılan resimler) oluşturulan tüm geçici dosyaları kontrol ettiğiniz bir klasöre yönlendirir; sistem geçici dizinlerinin kısıtlı olduğu ortamlar için kritiktir.

**S: WMF gibi metafile'ları yükleme sırasında PNG'ye dönüştürmek mümkün mü?**  
C: Kesinlikle—`loadOptions.setConvertMetafilesToPng(true)` ile etkinleştirin. Bu, raster görüntülerin PNG olarak saklanmasını sağlar ve modern görüntüleyicilerle uyumluluğu artırır.

## Sonuç

Aspose.Words for Java'da **LoadOptions nasıl ayarlanır** konusundaki temel teknikleri, kirli alanları güncellemekten şifreli dosyalarla çalışmaya, şekilleri dönüştürmeye, Word sürümünü belirtmeye, geçici depolamayı yönlendirmeye ve daha fazlasına kadar ele aldık. Bu seçenekleri kullanarak, çeşitli giriş senaryolarına uyum sağlayan sağlam ve yüksek performanslı belge işleme hatları oluşturabilirsiniz.

---

**Son Güncelleme:** 2025-12-27  
**Test Edilen Versiyon:** Aspose.Words for Java 24.11  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}