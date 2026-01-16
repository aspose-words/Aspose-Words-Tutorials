---
date: 2026-01-16
description: Aspose.Words for Java kullanarak Word’de yazım hatalarını nasıl vurgulayacağınızı
  öğrenin ve satır başına karakter sayısını nasıl ayarlayacağınızı, görünüm seçeneklerini
  nasıl özelleştireceğinizi ve stilleri nasıl temizleyeceğinizi keşfedin.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words Java ile Word'de Yazım Hatalarını Vurgulama
url: /tr/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java'da Belge Seçenekleri ve Ayarlarını Kullanma

## Aspose.Words for Java'da Belge Seçenekleri ve Ayarlarını Kullanma'ya Giriş

Bu kapsamlı rehberde, Aspose.Words for Java kullanarak **Word'de yazım hatalarını nasıl vurgulayacağınızı** öğrenecek ve görüntüleme seçenekleri, sayfa düzeni ve stil temizliği gibi ilgili ayarları da kavrayacaksınız. İster deneyimli bir geliştirici olun ister yeni başlıyor olun, aşağıdaki örnekler Word sürümleri arasında çalışan sağlam, hata‑bilinçli belgeler oluşturmanıza yardımcı olacaktır.

## Hızlı Yanıtlar
- **Word'de yazım hatalarını nasıl vurgulayabilirim?** `Document` nesnesi üzerinde `setShowSpellingErrors(true)` kullanın.  
- **Dilbilgisi hatalarını da gösterebilir miyim?** Evet—`setShowGrammaticalErrors(true)` çağırın.  
- **Satır başına karakter sayısını ayarlayan yöntem nedir?** `getPageSetup().setCharactersPerLine(int)`.  
- **Belirli bir Word sürümü için hangi API optimize eder?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Kullanılmayan stilleri temizlemenin bir yolu var mı?** `setUnusedStyles(true)` ile `CleanupOptions` kullanın ve `doc.cleanup(options)` çağırın.

## Word'de yazım hatalarını nasıl vurgularım?

Aspose.Words, yazım hatası vurgulamayı açmayı oldukça basit hale getirir. Belge Microsoft Word'de açıldığında, yanlış yazılmış kelimeler tanıdık kırmızı alt çizgiyle görünür ve son kullanıcıların sorunları anında fark etmesini sağlar.

## Satır başına karakter sayısını nasıl ayarlarsınız

Satır başına karakter sayısını kontrol etmek, sabit genişlikli düzenler (ör. kod listeleri veya eski formlar) için çok önemlidir. `PageSetup` sınıfı, bu değeri tam olarak tanımlamanızı sağlayan `setCharactersPerLine(int)` metodunu sunar.

## Dilbilgisi hatalarını nasıl gösterirsiniz

Yazımın ötesinde, dilbilgisi hatası gösterimini de etkinleştirebilirsiniz. Bu, stil kılavuzlarına uyması gereken içerik taslağı hazırlamak veya düzeltme araçları oluşturmak için faydalıdır.

## Optimizing Documents for Compatibility

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

Belge yönetiminin temel bir yönü, Microsoft Word'ün farklı sürümleriyle uyumluluğu sağlamaktır. Aspose.Words for Java, belgeleri belirli Word sürümleri için optimize etmenin basit bir yolunu sunar. Yukarıdaki örnekte, belgeyi Word 2016 için optimize ediyoruz ve sorunsuz uyumluluk sağlıyoruz.

## Identifying Grammatical and Spelling Errors

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

Belgelerle çalışırken doğruluk çok önemlidir. Aspose.Words for Java, belgelerinizde dilbilgisi ve yazım hatalarını vurgulamanızı sağlar ve bu da düzeltme ve düzenleme sürecini daha verimli kılar.

## Cleaning Up Unused Styles and Lists

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

Belge stillerini ve listelerini verimli bir şekilde yönetmek, belge tutarlılığını korumak için gereklidir. Aspose.Words for Java, kullanılmayan stilleri ve listeleri temizlemenizi sağlar ve böylece akıcı ve düzenli bir belge yapısı elde edilir.

## Removing Duplicate Styles

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

Yinelenen stiller, belgelerinizde karışıklık ve tutarsızlığa yol açabilir. Aspose.Words for Java ile yinelenen stilleri kolayca kaldırabilir ve belge netliğini ve bütünlüğünü koruyabilirsiniz.

## Customizing Document Viewing Options

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

Belgelerinizin görüntüleme deneyimini özelleştirmek çok önemlidir. Aspose.Words for Java, sayfa düzeni ve yakınlaştırma yüzdesi gibi çeşitli görüntüleme seçeneklerini ayarlamanıza olanak tanır ve belge okunabilirliğini artırır.

## Configuring Document Page Setup

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

Kesin sayfa ayarı, belge biçimlendirmesi için kritik öneme sahiptir. Aspose.Words for Java, düzen modlarını, **satır başına karakter sayısını** ve sayfa başına satır sayısını ayarlamanızı sağlar ve belgelerinizin görsel olarak çekici olmasını temin eder.

## Setting Editing Languages

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

Düzenleme dilleri, belge işleme sürecinde hayati bir rol oynar. Aspose.Words for Java ile belgeinizin dil ihtiyaçlarına uygun olarak düzenleme dillerini ayarlayabilir ve özelleştirebilirsiniz.

## Conclusion

Bu rehberde, Aspose.Words for Java'da mevcut olan çeşitli belge seçenekleri ve ayarlarını inceledik. Optimizasyondan hata gösterimine, stil temizliğinden görüntüleme seçeneklerine kadar, bu güçlü kütüphane belgelerinizi yönetmek ve özelleştirmek için kapsamlı yetenekler sunar.

## FAQ's

### Belirli bir Word sürümü için belgeyi nasıl optimize ederim?

Belirli bir Word sürümü için belgeyi optimize etmek üzere `optimizeFor` metodunu kullanın ve istenen sürümü belirtin. Örneğin, Word 2016 için optimize etmek:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### Bir belgede dilbilgisi ve yazım hatalarını nasıl vurgularım?

Aşağıdaki kodu kullanarak bir belgede dilbilgisi ve yazım hatalarının gösterimini etkinleştirebilirsiniz:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### Kullanılmayan stilleri ve listeleri temizlemenin amacı nedir?

Kullanılmayan stilleri ve listeleri temizlemek, temiz ve düzenli bir belge yapısını korumaya yardımcı olur. Gereksiz kalabalığı ortadan kaldırır, belge okunabilirliğini ve tutarlılığını artırır.

### Bir belgede yinelenen stilleri nasıl kaldırırım?

Bir belgede yinelenen stilleri kaldırmak için `duplicateStyle` seçeneği `true` olarak ayarlanmış `cleanup` metodunu kullanın. İşte bir örnek:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### Bir belgenin görüntüleme seçeneklerini nasıl özelleştiririm?

`ViewOptions` sınıfını kullanarak belge görüntüleme seçeneklerini özelleştirebilirsiniz. Örneğin, görünüm tipini sayfa düzeni olarak ayarlamak ve yakınlaştırmayı %50 yapmak için:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Additional Tips & Common Pitfalls

- **Hem yazım hem de dilbilgisi denetimlerini etkinleştirin** kapsamlı bir düzeltme gerektiğinde. Bayraklardan birini (`setShowGrammaticalErrors` veya `setShowSpellingErrors`) unutmak hataların gözden kaçmasına neden olabilir.
- **Satır başına karakter sayısını ayarlarken**, değerin seçilen yazı tipi ve sayfa kenar boşluklarıyla etkileşime girdiğini unutmayın. Beklenmedik satır sonlarından kaçınmak için gerçek belge düzeniyle test edin.
- **Temizleme işlemleri orijinal dosyada geri alınamaz**. Her zaman bir kopya üzerinde çalışın veya orijinal stilin korunması için sürüm kontrolü kullanın.
- **Düzenleme dili tercihleri** yazım denetimi davranışını etkiler. Çok dilli belgeler hedefliyorsanız, ilgili tüm dilleri `LanguagePreferences` içine ekleyin.

---

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}