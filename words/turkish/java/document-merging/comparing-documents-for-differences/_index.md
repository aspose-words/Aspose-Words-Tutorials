---
title: Belgeleri Farklılıklar Açısından Karşılaştırma
linktitle: Belgeleri Farklılıklar Açısından Karşılaştırma
second_title: Aspose.Words Java Belge İşleme API'si
description: Java'da Aspose.Words kullanarak belgeleri farklılıklar açısından nasıl karşılaştıracağınızı öğrenin. Adım adım kılavuzumuz doğru belge yönetimini sağlar.
weight: 12
url: /tr/java/document-merging/comparing-documents-for-differences/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Belgeleri Farklılıklar Açısından Karşılaştırma

## giriiş

İki Word belgesi arasındaki her bir farkı nasıl tespit edeceğinizi hiç merak ettiniz mi? Belki bir belgeyi gözden geçiriyorsunuz veya bir işbirlikçinin yaptığı değişiklikleri bulmaya çalışıyorsunuz. Manuel karşılaştırmalar sıkıcı ve hataya açık olabilir, ancak Java için Aspose.Words ile bu çok kolay! Bu kitaplık, belge karşılaştırmasını otomatikleştirmenizi, revizyonları vurgulamanızı ve değişiklikleri zahmetsizce birleştirmenizi sağlar.

## Ön koşullar

Koda geçmeden önce aşağıdakilerin hazır olduğundan emin olun:  
1. Sisteminizde Java Geliştirme Kiti (JDK) yüklü.  
2.  Aspose.Words for Java kütüphanesi. Şunları yapabilirsiniz[buradan indirin](https://releases.aspose.com/words/java/).  
3. IntelliJ IDEA veya Eclipse gibi bir geliştirme ortamı.  
4. Java programlama konusunda temel bilgi.  
5.  Geçerli bir Aspose lisansınız varsa, bir tane edinin[burada geçici lisans](https://purchase.aspose.com/temporary-license/).

## Paketleri İçe Aktar

Aspose.Words'ü kullanmak için gerekli sınıfları içe aktarmanız gerekir. Aşağıda gerekli içe aktarmalar verilmiştir:

```java
import com.aspose.words.*;
import java.util.Date;
```

Bu paketlerin projenizin bağımlılıklarına doğru şekilde eklendiğinden emin olun.


Bu bölümde süreci basit adımlara ayıracağız.


## Adım 1: Belgelerinizi Ayarlayın

Başlamak için iki belgeye ihtiyacınız var: biri orijinali, diğeri ise düzenlenmiş sürümü temsil ediyor. Bunları şu şekilde oluşturabilirsiniz:

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

 Bu, temel içerikle bellekte iki belge oluşturur. Ayrıca, mevcut Word belgelerini kullanarak yükleyebilirsiniz`new Document("path/to/document.docx")`.


## Adım 2: Mevcut Revizyonları Kontrol Edin

Word belgelerindeki revizyonlar izlenen değişiklikleri temsil eder. Karşılaştırmadan önce, hiçbir belgenin önceden var olan revizyonları içermediğinden emin olun:

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

Eğer düzeltmeler varsa, devam etmeden önce bunları kabul edebilir veya reddedebilirsiniz.


## Adım 3: Belgeleri Karşılaştırın

 Kullanın`compare` farklılıkları bulma yöntemi. Bu yöntem hedef belgeyi (`doc2`) kaynak belgeyle (`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

Burada:
- AuthorName, değişiklikleri yapan kişinin adıdır.
- Tarih karşılaştırma zaman damgasıdır.


## Adım 4: Süreç Revizyonları

Karşılaştırıldığında, Aspose.Words kaynak belgede revizyonlar üretecektir (`doc1`). Bu revizyonları inceleyelim:

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

Bu döngü, her revizyon hakkında, değişikliğin türü ve etkilenen metin gibi ayrıntılı bilgiler sağlar.


## Adım 5: Tüm Revizyonları Kabul Et

Kaynak belgeyi istiyorsanız (`doc1`) hedef belgeyle eşleşmesi için (`doc2`), tüm revizyonları kabul et:

```java
doc1.getRevisions().acceptAll();
```

 Bu güncellemeler`doc1` yapılan tüm değişiklikleri yansıtmak için`doc2`.


## Adım 6: Güncellenen Belgeyi Kaydedin

Son olarak güncellenen belgeyi diske kaydedin:

```java
doc1.save("Document.Compare.docx");
```

Değişiklikleri onaylamak için belgeyi yeniden yükleyin ve kalan revizyon olmadığını doğrulayın:

```java
doc1 = new Document("Document.Compare.docx");
if (doc1.getRevisions().getCount() == 0) {
    System.out.println("Documents are now identical.");
}
```


## Adım 7: Belgenin Eşitliğini Doğrulayın

Belgelerin aynı olduğundan emin olmak için metinlerini karşılaştırın:

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

Eğer metinler uyuşuyorsa tebrikler! Belgeleri başarıyla karşılaştırdınız ve senkronize ettiniz!


## Çözüm

Aspose.Words for Java sayesinde belge karşılaştırması artık bir angarya değil. Sadece birkaç satır kodla, farklılıkları belirleyebilir, revizyonları işleyebilir ve belge tutarlılığını sağlayabilirsiniz. İster işbirlikçi bir yazma projesi yönetiyor olun, ister yasal belgeleri denetliyor olun, bu özellik oyunun kurallarını değiştiriyor.

## SSS

### Resim ve tablo içeren belgeleri karşılaştırabilir miyim?  
Evet, Aspose.Words resim, tablo ve biçimlendirme içerenler de dahil olmak üzere karmaşık belgelerin karşılaştırılmasını destekler.

### Bu özelliği kullanmak için lisansa ihtiyacım var mı?  
 Evet, tam işlevsellik için bir lisans gereklidir. Bir tane edinin[burada geçici lisans](https://purchase.aspose.com/temporary-license/).

### Önceden yapılmış revizyonlar varsa ne olur?  
Çatışmaları önlemek için belgeleri karşılaştırmadan önce bunları kabul veya reddetmelisiniz.

### Belgedeki revizyonları vurgulayabilir miyim?  
Evet, Aspose.Words revizyonların nasıl görüntüleneceğini özelleştirmenize (örneğin değişiklikleri vurgulamanıza) olanak tanır.

### Bu özellik diğer programlama dillerinde de mevcut mu?  
Evet, Aspose.Words .NET ve Python da dahil olmak üzere birden fazla dili destekler.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
