---
date: '2026-03-23'
description: Aspose.Words for Java kullanarak Word belgelerini PDF'ye dönüştürürken
  yer imleri eklemeyi ve anahat seviyelerini yapılandırmayı öğrenin. Bu rehber, Word
  PDF yer imlerini dönüştürmeyi kapsar ve gezinmeyi iyileştirir.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Aspose.Words Java ile PDF'lere Yer İmleri Nasıl Eklenir
url: /tr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java ile PDF'lerde Yer İşaretleri Nasıl Eklenir

## Introduction
Eğer bir PDF'yi kolayca gezilebilir hâle getiren **yer işaretleri eklemek** konusunda zorlandıysanız, doğru yerdesiniz. Bu öğreticide, Aspose.Words for Java kullanarak Word belgelerini PDF'ye dönüştürürken **yer işaretleri ekleme** ve anahat seviyelerini ayarlama sürecini adım adım inceleyeceğiz. Sonunda, bir Word dosyasında iç içe yer işaretleri oluşturma ve mantıklı bir yer işareti hiyerarşisine sahip temiz, aranabilir bir PDF dışa aktarma iş akışını tam olarak anlayacaksınız.

**Öğrenecekleriniz**
- Projenizde Aspose.Words for Java'ı kurma  
- Bir Word belgesi içinde iç içe yer işaretleri oluşturma  
- PDF gezinme deneyimini geliştirmek için yer işareti anahat seviyelerini yapılandırma  
- Yer işareti yapısını koruyarak belgeyi PDF olarak kaydetme  

### Quick Answers
- **Yer işaretleri eklemenin temel faydası nedir?** Okuyucuların bölümlere doğrudan atlamasını sağlar, kullanılabilirliği artırır.  
- **Java'da PDF yer işaretlerini hangi kütüphane yönetir?** Aspose.Words for Java (isteğe bağlı Aspose.PDF ile son işlem).  
- **Bu özellik için lisansa ihtiyacım var mı?** Geliştirme için bir deneme sürümü yeterlidir; üretim için ticari lisans gereklidir.  
- **Yer işaretlerinin hiyerarşisini kontrol edebilir miyim?** Evet, `PdfSaveOptions` aracılığıyla anahat seviyelerini ayarlayarak.  
- **Bu yaklaşım büyük belgeler için uygun mu?** Kesinlikle—Aspose.Words içeriği verimli bir şekilde akıtır.

## What is “how to add bookmarks” in the context of PDF conversion?
Yer işaretleri eklemek, bir Word belgesine adlandırılmış bağlantılar yerleştirmek ve bu bağlantıların PDF'ye aktarılması anlamına gelir. PDF açıldığında, bu yer işaretleri gezinme bölmesinde görünür ve kullanıcıların bölümleri, alt bölümleri veya özel noktaları anında bulmasını sağlar.

## Why use Aspose.Words for Java to convert Word → PDF bookmarks?
Aspose.Words, Word'de tanımladığınız yer işareti hiyerarşisini tam olarak korur; birçok ücretsiz dönüştürücü bunları düzleştirir veya atar. Ayrıca **anahat seviyeleri** atamanıza izin vererek PDF'in içindekiler görünümünde ince ayar yapabilirsiniz.

## Prerequisites
- **Libraries**: Aspose.Words for Java (25.3 ve üzeri).  
- **Development environment**: JDK 8 ve üzeri, IntelliJ IDEA veya Eclipse gibi bir IDE.  
- **Build tool**: Maven veya Gradle (hangisini tercih ederseniz).  
- **Basic Java knowledge** ve Maven/Gradle aşinalığı.

### Setting Up Aspose.Words
Kütüphaneyi projenize aşağıdaki snippet'lerden birini kullanarak ekleyin.

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### License Acquisition
Aspose.Words ticari bir üründür, ancak ücretsiz bir deneme ile başlayabilirsiniz:

1. **Free Trial** – Tam özellikleri test etmek için [Aspose's release page](https://releases.aspose.com/words/java/) adresinden indirin.  
2. **Temporary License** – Kısa vadeli projeler için [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) üzerinden başvurun.  
3. **Purchase** – Kalıcı bir lisansı [Aspose’s purchasing portal](https://purchase.aspose.com/buy) üzerinden alın.

`.lic` dosyasını elde ettikten sonra, uygulama başlangıcında yükleyerek tüm özelliklerin kilidini açın.

## Step‑by‑Step Guide

### Creating Nested Bookmarks
**Overview:** Üç yer işareti içeren basit bir Word belgesi oluşturacağız; bir yer işareti diğerinin içinde iç içe olacak.

#### Step 1: Initialize Document and Builder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Bu, boş bir Word belgesi ve metin ile yer işaretleri eklememizi sağlayan bir builder nesnesi oluşturur.

#### Step 2: Insert the First (parent) Bookmark
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### Step 3: Nest a Second Bookmark Inside the First
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### Step 4: Close the Parent Bookmark
```java
builder.endBookmark("Bookmark 1");
```

#### Step 5: Add an Independent Third Bookmark
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

Bu aşamada Word belgesi, daha sonra PDF anahat seviyelerine dönüştürebileceğimiz net bir hiyerarşi içerir.

### Configuring Bookmark Outline Levels
**Overview:** Anahat seviyeleri, PDF görüntüleyicisine her yer işaretinin gezinme bölmesinde ne kadar derin olduğunu söyler.

#### Step 1: Prepare `PdfSaveOptions`
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### Step 2: Assign Levels to Each Bookmark
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```
Seviye 1 en üst düzeyde, seviye 2 bir alt öğe olarak ve bu şekilde devam eder.

#### Step 3: Save the Document as PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
Ortaya çıkan PDF, tanımladığımız hiyerarşiyi yansıtan yapılandırılmış bir yer işareti bölmesi gösterecektir.

## Common Issues and Solutions
| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Bookmarks disappear in PDF | `PdfSaveOptions` not configured | Ensure `outlineLevels` are added before saving. |
| Nested bookmark shows at top level | Wrong level number | Verify that child bookmarks receive a higher numeric level. |
| Missing `endBookmark` call | Unbalanced start/end calls | Double‑check each `startBookmark` has a matching `endBookmark`. |

## Practical Applications
- **Legal contracts** – Maddelere ve alt maddelere hızlı geçiş.  
- **Technical reports** – Metodoloji, sonuçlar ve ekler gibi büyük bölümlerde gezinme.  
- **E‑learning PDFs** – Her bölüm için tıklanabilir bir içindekiler tablosu sağlama.

## Performance Tips
- Kullanılmayan bölümleri kaydetmeden önce kaldırarak PDF'i hafif tutun.  
- Çok büyük dosyalar için bellek ayak izini azaltmak amacıyla akış (`doc.save(OutputStream)`) kullanın.

## Conclusion
Artık Aspose.Words for Java ile Word belgelerini PDF'ye dönüştürürken **yer işaretleri ekleme** ve anahat seviyelerini ayarlama konusunda bilgi sahibisiniz. Bu teknik, PDF gezinmesini büyük ölçüde iyileştirir, belgelerinizi daha profesyonel ve kullanıcı dostu hâle getirir.

**Next steps:** `PdfBookmark` nesneleri aracılığıyla yer işaretlerine özel simgeler eklemeyi deneyin veya bu iş akışını birden çok Word dosyasını otomatik olarak dönüştüren toplu iş hizmetine entegre edin.

## FAQ Section
1. **How do I install Aspose.Words for Java?**  
   Include it as a dependency via Maven or Gradle, then set up your license file.  
2. **Can I use bookmarks without outline levels?**  
   Yes, but outline levels give a clearer hierarchy in the PDF viewer.  
3. **What are the limits on bookmark nesting?**  
   There’s no strict limit, but keep the structure readable for end users.  
4. **How does Aspose handle large documents?**  
   It streams content efficiently; however, consider optimizing resources for very large files.  
5. **Can I modify bookmarks after saving the PDF?**  
   Yes—use Aspose.PDF for Java to edit bookmarks post‑conversion.

## Frequently Asked Questions

**Q: Does this method work with the latest Aspose.Words version?**  
A: Absolutely. The API for bookmark outline levels has been stable since version 20.  

**Q: Is a separate Aspose.PDF library required to view bookmarks?**  
A: No. The bookmarks are embedded in the PDF and visible in any standard PDF viewer.  

**Q: Can I programmatically change bookmark titles after the PDF is created?**  
A: Yes, by loading the PDF with Aspose.PDF and updating the `PdfBookmark` collection.  

**Q: Will this approach work on non‑Windows platforms?**  
A: Aspose.Words for Java is platform‑independent; it runs on any OS with a supported JDK.  

**Q: How can I test the bookmark hierarchy without opening the PDF?**  
A: Use `PdfBookmarkCollection` from Aspose.PDF to enumerate and verify levels programmatically.

---

**Last Updated:** 2026-03-23  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose  

**Resources**  
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)  
- [Download Latest Releases](https://releases.aspose.com/words/java/)  
- [Purchase a License](https://purchase.aspose.com/buy)  
- [Free Trial](https://releases.aspose.com/words/java/)  
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)  
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}