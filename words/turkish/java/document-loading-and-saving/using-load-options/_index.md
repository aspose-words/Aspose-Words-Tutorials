---
"description": "Java için Aspose.Words'de Yükleme Seçeneklerinde Ustalaşma. Verimli Java belge işleme için belge yüklemeyi özelleştirin, şifrelemeyi yönetin, şekilleri dönüştürün, Word sürümlerini ayarlayın ve daha fazlasını yapın."
"linktitle": "Yükleme Seçeneklerini Kullanma"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words'de Yükleme Seçeneklerini Kullanma"
"url": "/tr/java/document-loading-and-saving/using-load-options/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Yükleme Seçeneklerini Kullanma


## Java için Aspose.Words'de Yükleme Seçenekleriyle Çalışmaya Giriş

Bu eğitimde, Java için Aspose.Words'de Yükleme Seçenekleri ile nasıl çalışılacağını inceleyeceğiz. Yükleme Seçenekleri, belgelerin nasıl yüklenip işlendiğini özelleştirmenize olanak tanır. Kirli alanları güncelleme, şifrelenmiş belgeleri yükleme, şekilleri Office Math'e dönüştürme, MS Word sürümünü ayarlama, geçici bir klasör belirtme, uyarıları işleme ve meta dosyalarını PNG'ye dönüştürme gibi çeşitli senaryoları ele alacağız. Adım adım inceleyelim.

## Kirli Alanları Güncelle

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

Bu kod parçacığı bir belgedeki kirli alanların nasıl güncelleneceğini gösterir. `setUpdateDirtyFields(true)` Yöntem, belge yükleme sırasında kirli alanların güncellenmesini sağlamak için kullanılır.

## Şifrelenmiş Belgeyi Yükle

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

Burada, bir parola kullanarak şifrelenmiş bir belge yüklüyoruz. `LoadOptions` oluşturucu belge parolasını kabul eder ve ayrıca belgeyi kaydederken yeni bir parola da belirtebilirsiniz `OdtSaveOptions`.

## Şekli Office Matematiğe Dönüştür

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

Bu kod, belge yükleme sırasında şekillerin Office Math nesnelerine nasıl dönüştürüleceğini gösterir. `setConvertShapeToOfficeMath(true)` yöntem bu dönüşümü mümkün kılar.

## MS Word Sürümünü Ayarla

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

Belge yükleme için MS Word sürümünü belirtebilirsiniz. Bu örnekte, sürümü Microsoft Word 2010 olarak ayarlıyoruz `setMswVersion`.

## Geçici Klasörü Kullan

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

Geçici klasörü kullanarak ayarlayarak `setTempFolder`, belge işleme sırasında geçici dosyaların nerede saklanacağını kontrol edebilirsiniz.

## Uyarı Geri Araması

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Belge yükleme sırasında ortaya çıkan uyarıları işleyin.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Bu kod, belge yükleme sırasında uyarıları işlemek için bir uyarı geri aramasının nasıl ayarlanacağını gösterir. Uyarılar oluştuğunda uygulamanızın davranışını özelleştirebilirsiniz.

## Meta Dosyalarını PNG'ye Dönüştür

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

Belge yükleme sırasında meta dosyalarını (örneğin WMF) PNG görüntülerine dönüştürmek için şunu kullanabilirsiniz: `setConvertMetafilesToPng(true)` yöntem.

## Java için Aspose.Words'de Yükleme Seçenekleriyle Çalışmak İçin Tam Kaynak Kodu

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
	// Varsayılan olarak MS Word 2019 spesifikasyonuna göre belgeleri yükleyecek yeni bir LoadOptions nesnesi oluşturun
	// ve yükleme sürümünü Microsoft Word 2010 olarak değiştirin.
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
		// Belge yükleme sırasında ortaya çıkan uyarıları ve ayrıntılarını yazdırır.
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

## Çözüm

Bu eğitimde, Java için Aspose.Words'de Yükleme Seçenekleri ile çalışmanın çeşitli yönlerini inceledik. Yükleme Seçenekleri, belgelerin nasıl yüklenip işlendiğini özelleştirmede önemli bir rol oynar ve belge işlemenizi özel ihtiyaçlarınıza göre uyarlamanıza olanak tanır. Bu kılavuzda ele alınan temel noktaları özetleyelim:

## SSS

### Belge yüklenirken uyarıları nasıl yönetebilirim?

Aşağıda gösterildiği gibi bir uyarı geri araması ayarlayabilirsiniz. `warningCallback()` Yukarıdaki yöntemi özelleştirin. `DocumentLoadingWarningCallback` Uygulamanızın gereksinimlerine göre uyarıları işleyen sınıf.

### Bir belgeyi yüklerken şekilleri Office Math nesnelerine dönüştürebilir miyim?

Evet, şekilleri kullanarak Office Math nesnelerine dönüştürebilirsiniz. `loadOptions.setConvertShapeToOfficeMath(true)`.

### Belge yükleme için MS Word sürümünü nasıl belirlerim?

Kullanmak `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` Belgenin yüklenmesi için MS Word sürümünü belirtmek için.

### Amacı nedir? `setTempFolder` Yükleme Seçenekleri'nde yöntem nedir?

The `setTempFolder` yöntemi, belge işleme sırasında geçici dosyaların depolanacağı klasörü belirtmenize olanak tanır.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}