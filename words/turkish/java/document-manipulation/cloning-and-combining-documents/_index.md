---
"description": "Aspose.Words for Java'da belgeleri nasıl klonlayacağınızı ve birleştireceğinizi öğrenin. Kaynak kod örnekleriyle adım adım kılavuz."
"linktitle": "Belgeleri Klonlama ve Birleştirme"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words'de Belgeleri Klonlama ve Birleştirme"
"url": "/tr/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Belgeleri Klonlama ve Birleştirme


## Java için Aspose.Words'de Belgeleri Klonlama ve Birleştirmeye Giriş

Bu eğitimde, Java için Aspose.Words kullanarak belgelerin nasıl klonlanacağını ve birleştirileceğini inceleyeceğiz. Bir belgenin klonlanması, belgelerin değiştirme noktalarına, yer imlerine ve posta birleştirme işlemleri sırasında eklenmesi dahil olmak üzere çeşitli senaryoları ele alacağız.

## Adım 1: Bir Belgeyi Klonlama

Java için Aspose.Words'de bir belgeyi klonlamak için şunu kullanabilirsiniz: `deepClone()` yöntem. İşte basit bir örnek:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Bu kod orijinal belgenin derin bir klonunu oluşturacak ve onu yeni bir dosya olarak kaydedecektir.

## Adım 2: Belgeleri Değiştirme Noktalarına Ekleme

Başka bir belgedeki belirli değiştirme noktalarına belgeler ekleyebilirsiniz. Bunu nasıl yapabileceğiniz aşağıda açıklanmıştır:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Bu örnekte, şunu kullanıyoruz: `FindReplaceOptions` değiştirme için bir geri arama işleyicisi belirtmek için nesne. `InsertDocumentAtReplaceHandler` sınıf, ekleme mantığını yönetir.

## Adım 3: Belgeleri Yer İşaretlerine Ekleme

Başka bir belgedeki belirli bir yer işaretine belge eklemek için aşağıdaki kodu kullanabilirsiniz:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Burada, yer imini adına göre buluyoruz ve `insertDocument` içeriğini ekleme yöntemi `subDoc` yer imi konumunda belge.

## Adım 4: Posta Birleştirme Sırasında Belgeleri Ekleme

Aspose.Words for Java'da bir posta birleştirme işlemi sırasında belgeleri ekleyebilirsiniz. İşte nasıl:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

Bu örnekte, şunu kullanarak bir alan birleştirme geri araması ayarlıyoruz: `InsertDocumentAtMailMergeHandler` "Document_1" alanıyla belirtilen belgenin eklenmesini işleyen sınıf.

## Çözüm

Aspose.Words for Java'da belgeleri klonlama ve birleştirme çeşitli teknikler kullanılarak gerçekleştirilebilir. Bir belgeyi klonlamanız, değiştirme noktalarına, yer imlerine veya posta birleştirme sırasında içerik eklemeniz gerekip gerekmediğine bakılmaksızın, Aspose.Words belgeleri sorunsuz bir şekilde işlemek için güçlü özellikler sunar.

## SSS

### Aspose.Words for Java'da bir belgeyi nasıl klonlarım?

Java için Aspose.Words'de bir belgeyi klonlamak için şunu kullanabilirsiniz: `deepClone()` yöntem. İşte bir örnek:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Bir belgeyi yer imlerine nasıl ekleyebilirim?

Aspose.Words for Java'da bir yer imine belge eklemek için, yer imini adına göre bulabilir ve ardından `insertDocument` İçeriği ekleme yöntemi. İşte bir örnek:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Aspose.Words for Java'da posta birleştirme sırasında belgeleri nasıl eklerim?

Aspose.Words for Java'da posta birleştirme sırasında bir alan birleştirme geri araması ayarlayarak ve eklenecek belgeyi belirterek belge ekleyebilirsiniz. İşte bir örnek:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

Bu örnekte, `InsertDocumentAtMailMergeHandler` sınıf, posta birleştirme sırasında "DocumentField" için ekleme mantığını yönetir.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}