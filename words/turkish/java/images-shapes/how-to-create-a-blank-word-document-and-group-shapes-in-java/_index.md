---
category: general
date: 2026-09-24
description: Java'da boş bir Word belgesi oluşturmayı ve Aspose.Words kullanarak dikdörtgen
  ve çizgi gibi şekilleri gruplamayı öğrenin. Adım adım kod içerir.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: tr
lastmod: 2026-09-24
og_description: Java'da boş bir Word belgesi oluşturun ve şekilleri gruplamayı, bir
  dikdörtgen şekli eklemeyi ve Aspose.Words ile şekil boyutunu ayarlamayı öğrenin.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Boş bir Word belgesi oluşturun ve Java’da şekilleri gruplayın – adım adım
  rehber
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Java'da boş bir Word belgesi oluşturma ve şekilleri gruplama
url: /tr/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş bir Word belgesi oluşturma ve Java'da şekilleri gruplama

Eğer **boş bir Word belgesi oluşturmanız** ve ardından birden fazla çizim nesnesini düzenlemeniz gerekiyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. Aspose.Words for Java kullanarak bir grup şekil ekleyebilir, bir dikdörtgen şekil ekleyebilir, bir çizgi çizebilir ve her şeklin boyut ve konumunu kontrol edebilirsiniz—hepsi tek bir çalıştırılabilir programda.

Belgeyi başlatmaktan son `.docx` dosyasını kaydetmeye kadar her adımı adım adım izleyebilirsiniz. Sonunda **şekilleri nasıl gruplandıracağınızı**, **dikdörtgen şekil eklemeyi** ve **şekil boyutunu ayarlamayı** anlayacak ve Word dosyalarınızın tam istediğiniz gibi görünmesini sağlayacaksınız.

## Önkoşullar

- Java 17 veya üzeri (kod, herhangi bir yeni JDK ile derlenir)
- Aspose.Words for Java kütüphanesi ([Aspose web sitesinden](https://products.aspose.com/words/java) indirin)
- Bir IDE veya derleme aracı (Maven/Gradle) ki Aspose.Words JAR'ını sınıf yoluna ekleyebilsin
- Java sözdizimi hakkında temel bilgi

> **Pro ipucu:** Bağımlılık yönetimi için Maven kullanın; `com.aspose:aspose-words:23.12` (veya en son sürüm) satırını `pom.xml` dosyanıza ekleyin.

## Adım 1: Boş bir Word belgesi oluşturma

İlk görev **boş bir Word belgesi oluşturmaktır**. Bu, daha sonra şekiller ekleyebileceğiniz temiz bir tuval sağlar.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Neden önemli:* Bir `Document` nesnesi tüm `.docx` dosyasını temsil eder. Boş bir belgeyle başlamak, ekleyeceğiniz şekilleri etkileyebilecek gizli biçimlendirmelerin olmamasını sağlar.

## Adım 2: Grup şekli ekleme – birden fazla nesne için kapsayıcı

Bir **grup şekli**, birden fazla şekli birlikte taşımanıza, yeniden boyutlandırmanıza veya döndürmenize izin veren bir kapsayıcı gibi davranır. Bu, Word'de **şekilleri nasıl gruplandıracağınızın** temelidir.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Açıklama:* `insertGroupShape` yöntemi bir `GroupShape` nesnesi oluşturur ve mevcut imleç konumuna yerleştirir. Bu gruba `appendChild` ile eklediğiniz sonraki tüm şekiller tek bir birim olarak ele alınacaktır.

## Adım 3: Dikdörtgen şekil ekleme ve boyutunu ayarlama

Şimdi gruba **dikdörtgen şekil ekliyoruz** ve **şekil boyutunu** tam olarak ayarlıyoruz.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Neden şekil boyutunu ayarlamanız gerekir:* Genişlik ve yükseklik, dikdörtgenin sayfada nasıl göründüğünü kontrol eder. `setLeft` ve `setTop` yöntemleri, dikdörtgeni grubun orijinine göre konumlandırır ve size piksel‑tam düzen kontrolü sağlar.

## Adım 4: Çizgi şekli ekleme ve boyutlarını yapılandırma

Bir çizgi, başka bir yaygın çizim nesnesidir. Çizgiye **dikdörtgen şekil**‑benzeri mantık ekleyeceğiz ve aynı boyutlandırma prensiplerinin geçerli olduğunu göstereceğiz.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Önemli nokta:* Bir çizginin yüksekliği olmasa da uzunluğunu tanımlamak için hâlâ `setWidth` kullanırsınız. Konumlandırma (`setLeft`, `setTop`) diğer şekillerle aynı koordinat sistemini izler.

## Adım 5: Gruplandırılmış şekillerle belgeyi kaydetme

Son olarak, belgeyi kaydederek değişiklikleri kalıcı hale getirin. Bu, sonucu doğrulamak için Microsoft Word'de açabileceğiniz bir `.docx` dosyası oluşturur.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Beklenen çıktı:** `GroupShapeDemo.docx` dosyasını açtığınızda, içinde gruplanmış bir dikdörtgen ve çizgi bulunan boş bir sayfa gösterilir. Şekillerden birini seçmek tüm grubu seçer ve onları birlikte taşımanıza olanak tanır.

## Yaygın sorular ve kenar‑durumları yönetimi

| Soru | Cevap |
|----------|--------|
| *Gruba iki'den fazla şekil ekleyebilir miyim?* | Evet. Her ek şekil için `group.appendChild(yourShape)` çağırın. |
| *Boyut için farklı bir birim (ör. santimetre) gerekirse ne yapmalıyım?* | Aspose.Words puan (point) birimini kullanır (1 point = 1/72 inç). `Points = centimeters * 28.3465` ifadesiyle dönüştürün. |
| *Grup, belge başka bir makinede açıldığında düzenini korur mu?* | Kesinlikle. Tüm boyut ve konum verileri `.docx` dosyasında saklanır, bu da düzenin taşınabilir olmasını sağlar. |
| *Şekilleri daha sonra gruptan nasıl çıkarırım?* | `GroupShape` nesnesini alın, ardından `group.getChildNodes(NodeType.SHAPE, true)` üzerinde döngü yaparak her çocuğu gruptan dışarı taşıyın. |
| *Tüm grubu döndürmem gerekirse ne yapmalıyım?* | Kaydetmeden önce `group.setRotationAngle(double angleInDegrees)` kullanın. |

## Tam, çalıştırılabilir örnek

Aşağıda IDE'nize kopyalayıp yapıştırabileceğiniz tam program bulunmaktadır. Gerekli tüm importları ve yorumları içerir.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Programı çalıştırın, Microsoft Word'de `GroupShapeDemo.docx` dosyasını açın ve açıklandığı gibi gruplanmış şekilleri göreceksiniz.

## Sonuç

Artık Aspose.Words for Java kullanarak **boş bir Word belgesi oluşturmayı**, **Word'de şekilleri gruplamayı**, **dikdörtgen şekil eklemeyi** ve **şekil boyutunu ayarlamayı** biliyorsunuz. Şekilleri bir `GroupShape` içine yerleştirerek toplu konumlandırma, ölçekleme ve döndürme üzerinde tam kontrol elde edersiniz—otomatik raporlara gömülü diyagramlar, akış şemaları veya özel grafikler için mükemmeldir.

**Sonraki adımlar:**  
- Resimler veya metin kutuları gibi daha karmaşık nesnelerle **şekilleri nasıl gruplandıracağınızı** keşfedin.  
- Tüm grubu döndürmek için `setRotationAngle` ile deneyler yapın.  
- Bu tekniği posta birleştirme (mail‑merge) ile birleştirerek markalı grafikler içeren kişiselleştirilmiş belgeler oluşturun.

Kodu kendi projeleriniz için özgürce uyarlayın ve sonuçlarınızı yorumlarda paylaşın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalarla tam çalışan kod örnekleri içerir.

- [Java ile Word'de dikdörtgen şekil oluşturma – Tam Kılavuz](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Java ile Word Belgesi Oluşturma – Gölge Efektiyle Dikdörtgen Şekil Ekle](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekil Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}