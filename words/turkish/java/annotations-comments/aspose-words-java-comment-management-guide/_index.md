---
date: '2026-05-18'
description: Aspose.Words for Java ile Word belgelerinde yorumları nasıl yöneteceğinizi
  öğrenin. Add comment java, print word comments, delete word comment ve add comment
  reply işlemlerini verimli bir şekilde yapın.
keywords:
- how to manage comments
- add comment java
- print word comments
- java document comments
- delete word comment
- add comment reply
schemas:
- author: Aspose
  dateModified: '2026-05-18'
  description: Learn how to manage comments in Word documents with Aspose.Words for
    Java. Add comment java, print word comments, delete word comment, and add comment
    reply efficiently.
  headline: How to Manage Comments in Word Documents Using Aspose.Words for Java
  type: TechArticle
- questions:
  - answer: Yes, with a valid license; a free trial is available for evaluation.
    question: Can I use Aspose.Words for Java in a commercial application?
  - answer: Yes, provide the password when loading the document via `LoadOptions`.
    question: Does the library work with password‑protected Word files?
  - answer: Aspose.Words for Java supports JDK 8 through JDK 21, covering both legacy
      and modern environments.
    question: Which Java versions are supported?
  - answer: Use `LoadOptions.setLoadFormat(LoadFormat.DOCX)` and enable `LoadOptions.setMemoryOptimization(true)`
      to reduce memory footprint.
    question: How do I handle documents larger than 200 MB?
  - answer: Iterate `doc.getComments()` and write each comment’s properties to a CSV
      using standard Java I/O.
    question: Is there a way to export comments to a CSV file?
  type: FAQPage
title: Aspose.Words for Java Kullanarak Word Belgelerinde Yorumları Yönetme
url: /tr/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java Kullanarak Word Belgelerinde Yorumları Yönetme

Yorumları programlı olarak yönetmek, özellikle yanıt eklemeniz, istenmeyen notları silmeniz veya her yorumun ne zaman yapıldığını izlemeniz gerektiğinde bir labirentte dolaşmak gibi hissettirebilir. Bu öğreticide Aspose.Words for Java ile **yorumları nasıl yöneteceğinizi** verimli bir şekilde keşfedecek, bir yorum eklemekten UTC zaman damgasını almaya kadar her şeyi kapsayacaksınız.

## Hızlı Yanıtlar
- **Java'da bir yorumu nasıl eklerim?** `Document` → `Comment` nesnelerini kullanın ve `CommentRangeStart` üzerinde `appendChild` metodunu çağırın.
- **Bir Word dosyasındaki tüm yorumları yazdırabilir miyim?** `doc.getComments()` üzerinde döngü yapın ve her yorumun metnini ve yazarını çıktı olarak verin.
- **Bir yorumu silmenin bir yolu var mı?** Yorum düğümünü belgenin yorum koleksiyonundan kaldırın.
- **Bir yoruma yanıt nasıl eklerim?** Bir `Comment` nesnesi oluşturun, `ParentComment` özelliğini ayarlayın ve belgeye ekleyin.
- **Yorumun zaman damgasını nasıl alabilirim?** UTC bir `java.time` değeri döndüren `Comment.getDateTime()` metoduna erişin.

## Word Belgelerinde Yorum Yönetimi Nedir?
Yorum yönetimi, bir Word dosyası içinde yorum nesnelerinin programlı olarak oluşturulması, alınması, değiştirilmesi ve kaldırılmasını ifade eder. Manuel düzenleme olmadan otomatik inceleme iş akışlarını mümkün kılar; geliştiricilerin yorum eklemesini, yanıt vermesini, çözümlemesini ve programlı olarak çıkarmasını sağlar ve bu da ekipler arasında iş birliği ve denetim süreçlerini kolaylaştırır.

## Yorumları Yönetmek İçin Neden Aspose.Words for Java Kullanılmalı?
Aspose.Words **35+ giriş ve çıkış formatını** destekler ve standart sunucu donanımında **500 sayfalık belgeleri 3 saniyeden kısa sürede** işleyebilir; Microsoft Word gerektirmez. Zengin API'si, yorum nesneleri, zaman damgaları ve yanıt hiyerarşileri üzerinde ayrıntılı kontrol sağlar.

## Önkoşullar
- Java Development Kit (JDK) 8 veya üzeri yüklü.
- Java sözdizimi ve nesne‑yönelimli kavramlara temel aşinalık.
- Proje yönetimini kolaylaştırmak için IntelliJ IDEA veya Eclipse gibi bir IDE.
- Geçerli bir Aspose.Words for Java lisansı (deneme veya satın alınmış).

### Aspose.Words for Java Kurulumu
Aspose.Words, Maven veya Gradle artefaktı olarak sunulur. Derleme sisteminize uygun bağımlılığı ekleyin.

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

#### Lisans Alımı
Aspose.Words ticari bir kütüphanedir, ancak tam özellik erişimi için ücretsiz deneme ile başlayabilir veya geçici bir lisans talep edebilirsiniz. Lisans seçeneklerini incelemek için [satın alma sayfasını](https://purchase.aspose.com/buy) ziyaret edin.

## Java Stiliyle Yorum Nasıl Eklenir?
`Document`, belleğe yüklenmiş bir Word dosyasını temsil eden temel Aspose.Words nesnesidir. `Comment`, yazar, metin ve zaman damgası bilgilerini depolayabilen tek bir yorum düğümünü temsil eder. Üst‑seviye bir yorum eklemek için bir `Document` yükleyin veya oluşturun, istediğiniz yazar ve metinle bir `Comment` örneği oluşturun ve hedef konumdaki bir `CommentRangeStart` öğesine ekleyin. Bu yaklaşım, yorumu sadece birkaç satır kodla ekler.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

## Java'da Yorum Yanıtı Nasıl Eklenir?
`Comment` nesneleri, `ParentComment` özelliği kullanılarak yanıt zincirleri oluşturmak için bağlanabilir. Bu özelliği mevcut bir yoruma ayarladığınızda, yeni yorum o ebeveynin çocuğu (yanıtı) olur. Bir alt `Comment` oluşturun, `ParentComment` özelliğini orijinal yoruma atayın ve belgeye ekleyin. Bu, yanıtı doğrudan ebeveynin altına yerleştirir ve tartışma hiyerarşisini korur.  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

## Word Yorumları Nasıl Yazdırılır?
`Document.getComments()` Word dosyasında bulunan tüm `Comment` düğümlerinin bir koleksiyonunu döndürür. Bu koleksiyon üzerinde döngü yaparak her yorumun yazarına, metnine ve zaman damgasına erişebilirsiniz. Belgeyi yükleyin, `getComments()` metodunu çağırın ve her `Comment` için ayrıntılarını konsola veya loga yazdırın. Bu, dosyaya gömülü tüm geri bildirimlerin hızlı bir özetini sağlar.  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

## Word Yorumunu Nasıl Silinir?
`Comment.remove()` bir yorum düğümünü belge ağacından ayırır ve etkili bir şekilde siler. Önce `Document.getComments()` koleksiyonunda istenen yorumu bulun, ardından `remove()` metodunu çağırın. Bu işlem, tüm hiyerarşiyi temizlemeyi seçerseniz alt yanıtları da kaldırır ve yorumun dosyadan tamamen silinmesini sağlar.  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

## Yorum Nasıl Tamamlandı Olarak İşaretlenir?
`Comment.setDone(boolean)` bir yorumu çözümlenmiş olarak işaretler ve Word arayüzündeki görsel “Done” bayrağını değiştirir. Bir yorum oluşturduktan veya bulduktan sonra, sorunun ele alındığını göstermek için `setDone(true)` çağırın. Bu bayrak, inceleyenlerin tamamlanmış öğeleri hızlıca tanımasına yardımcı olur ve gerektiğinde `setDone(false)` ile temizlenebilir.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

## Yorumdan UTC Tarih ve Saat Nasıl Alınır?
`Comment.getDateTime()` yorumun oluşturulma zaman damgasını UTC'de bir `java.time.OffsetDateTime` olarak döndürür. Belgeyi yükledikten sonra bu özelliğe erişerek her yorum için kesin zaman bilgisi elde edersiniz; bu, denetim izleri ve sürüm kontrolü için faydalıdır. Gerekirse diğer saat dilimlerine de dönüştürebilirsiniz.  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## Pratik Uygulamalar
Bu yorum‑yönetimi özelliklerini anlamak ve kullanmak, birçok gerçek‑dünya iş akışını dönüştürebilir:

- **Ortak Düzenleme:** Ekipler belgeyi terk etmeden yorum ekleyebilir, yanıtlayabilir ve çözümleyebilir.
- **Belge İnceleme Boru Hatları:** Otomatik betikler tüm geri bildirimleri çıkarabilir, özet raporlar oluşturabilir ve öğeleri tamamlandı olarak işaretleyebilir.
- **Denetim ve Uyumluluk:** UTC zaman damgaları, her yorumun ne zaman yapıldığını gösteren değiştirilemez bir kayıt sağlar; düzenleyici takibi için faydalıdır.

## Performans Düşünceleri
Büyük dosyalar işlenirken aşağıdaki en iyi uygulama ipuçlarını aklınızda tutun:

- Yorumları belleğe tüm yorum ağacını yüklemek yerine toplu olarak işleyin.
- `Document.getComments().clear()` metodunu yalnızca tüm yorumları bir kerede temizlemeniz gerektiğinde kullanın.
- Bellek‑optimizeli yorum işleme avantajından yararlanmak için en son Aspose.Words sürümüne yükseltin.

## Yaygın Sorunlar ve Çözümler
| Sorun | Çözüm |
|-------|----------|
| **Yorumlara erişirken NullPointerException** | `getComments()` çağırmadan önce belgenin tamamen yüklendiğinden (`Document.load`) emin olun. |
| **Yanıtlar Word UI'da görünmüyor** | `ParentComment` özelliğini doğru şekilde ayarlayın; yanıt mevcut bir yoruma referans vermelidir. |
| **Zaman damgaları UTC yerine yerel saat gösteriyor** | UTC'yi zorlamak için `Comment.getDateTime().withOffsetSameInstant(ZoneOffset.UTC)` kullanın. |

## Sıkça Sorulan Sorular

**Q: Aspose.Words for Java'ı ticari bir uygulamada kullanabilir miyim?**  
A: Evet, geçerli bir lisansla; değerlendirme için ücretsiz deneme mevcuttur.

**Q: Kütüphane şifre korumalı Word dosyalarıyla çalışıyor mu?**  
A: Evet, belgeyi `LoadOptions` ile yüklerken şifreyi sağlayın.

**Q: Hangi Java sürümleri destekleniyor?**  
A: Aspose.Words for Java, JDK 8'den JDK 21'e kadar destekler; hem eski hem de modern ortamları kapsar.

**Q: 200 MB'den büyük belgelerle nasıl başa çıkabilirim?**  
A: `LoadOptions.setLoadFormat(LoadFormat.DOCX)` kullanın ve bellek ayak izini azaltmak için `LoadOptions.setMemoryOptimization(true)` etkinleştirin.

**Q: Yorumları bir CSV dosyasına dışa aktarmanın bir yolu var mı?**  
A: `doc.getComments()` üzerinde döngü yapın ve her yorumun özelliklerini standart Java I/O kullanarak bir CSV'ye yazın.

**Son Güncelleme:** 2026-05-18  
**Test Edildi:** Aspose.Words for Java 24.12  
**Yazar:** Aspose  

```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```

{{< blocks/products/products-backtop-button >}}

## İlgili Öğreticiler

- [Aspose.Words Java Kullanarak Word Belgelerinde Değişiklikleri İzleme: Belge Revizyonlarına Tam Kılavuz](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words for Java ile Açıklamaları ve Yorumları Ustalıkla Kullanma Öğreticileri](/words/java/annotations-comments/)
- [Aspose.Words for Java Ustalıkla: Word Belgelerinde Yer İmleri Ekleme ve Yönetme](/words/java/content-management/aspose-words-java-manage-bookmarks/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

```java
NodeCollection<Comment> comments = doc.getChildNodes(NodeType.COMMENT, true);
for (Comment comment : (Iterable<Comment>) comments) {
    if (comment.getAncestor() == null) {
        System.out.println("Top-level comment:");
        System.out.println("\t" + comment.getText().trim() + ", by " + comment.getAuthor());
        for (Comment reply : comment.getReplies()) {
            System.out.println("\t" + reply.getText().trim() + ", by " + reply.getAuthor());
        }
    }
}
```

```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```

```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```