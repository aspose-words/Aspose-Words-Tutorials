---
date: 2025-11-28
description: Aspose.Words for Java kullanarak hücre kenarlıklarını nasıl değiştireceğinizi
  ve tabloları nasıl biçimlendireceğinizi öğrenin. Bu adım adım kılavuz, kenarlık
  ayarlamayı, ilk sütun stilini uygulamayı, tablo içeriğini otomatik sığdırmayı ve
  tablo stillerini uygulamayı kapsar.
language: tr
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: Tablolarda Hücre Kenarlıklarını Değiştirme – Aspose.Words for Java
url: /java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tablo Hücre Kenarlıklarını Değiştirme – Aspose.Words for Java

## Giriş

Belge biçimlendirmesinde tablolar kritik bir rol oynar ve **hücre kenarlıklarını nasıl değiştireceğinizi bilmek**, net ve profesyonel düzenler oluşturmak için esastır. Java ve Aspose.Words ile geliştirme yapıyorsanız, zaten güçlü bir araç setine sahipsiniz. Bu öğreticide, tabloları biçimlendirme, hücre kenarlıklarını değiştirme, *ilk sütun stilini* uygulama ve belgelerinizin daha şık görünmesi için *içeriğe otomatik sığdırma* (auto‑fit) kullanım sürecini adım adım inceleyeceğiz.

## Hızlı Yanıtlar
- **Tabloları oluşturmak için birincil sınıf nedir?** `DocumentBuilder` tabloları ve hücreleri programlı olarak oluşturur.  
- **Tek bir hücrenin kenarlık kalınlığını nasıl değiştiririm?** `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)` kullanın.  
- **Önceden tanımlı bir tablo stilini uygulayabilir miyim?** Evet – `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)` çağırın.  
- **Bir tabloyu içeriğine otomatik sığdıran yöntem hangisidir?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Üretim ortamında lisansa ihtiyacım var mı?** Deneme dışı kullanım için geçerli bir Aspose.Words lisansı gereklidir.

## Aspose.Words’te “hücre kenarlıklarını değiştirme” nedir?

Hücre kenarlıklarını değiştirmek, hücreleri ayıran görsel çizgileri—renk, genişlik ve çizgi stilini—özelleştirmek anlamına gelir. Aspose.Words, bu özellikleri tablo, satır veya tek tek hücre seviyesinde ayarlamanıza olanak tanıyan zengin bir API sunar ve belgelerinizin görünümünü ince ayarlarla kontrol etmenizi sağlar.

## Java için Aspose.Words tablo stilini neden kullanmalısınız?

- **Platformlar arasında tutarlı görünüm** – aynı stil kodu Windows, Linux ve macOS’ta çalışır.  
- **Microsoft Word’e bağımlılık yok** – belgeleri sunucu tarafında oluşturabilir veya değiştirebilirsiniz.  
- **Zengin stil kütüphanesi** – yerleşik tablo stilleri (ör. *ilk sütun stili*) ve tam otomatik sığdırma yetenekleri.  

## Ön Koşullar

1. **Java Development Kit (JDK) 8+** – `java` komutunun PATH’inizde olduğundan emin olun.  
2. **IDE** – IntelliJ IDEA, Eclipse veya tercih ettiğiniz herhangi bir editör.  
3. **Aspose.Words for Java** – en son JAR dosyasını [resmi siteden](https://releases.aspose.com/words/java/) indirin.  
4. **Temel Java bilgisi** – Maven/Gradle projesi oluşturup harici JAR ekleyebilecek seviyede olmalısınız.

## Paketleri İçe Aktarma

Tablolarla çalışmaya başlamak için temel Aspose.Words sınıflarına ihtiyacınız var:

```java
import com.aspose.words.*;
```

Bu tek import, `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` ve birçok yardımcı sınıfa erişim sağlar.

## Hücre Kenarlıklarını Değiştirme

Aşağıda basit bir tablo oluşturacak, genel kenarlıklarını değiştirecek ve ardından tek tek hücreleri özelleştireceğiz.

### Adım 1: Yeni Bir Belge Yükleme

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Adım 2: Tablo Oluşturma ve Genel Kenarlıkları Ayarlama

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Adım 3: Tek Bir Hücrenin Kenarlıklarını Değiştirme

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### Kodun yaptığı şey
- **Genel kenarlıklar** – `table.setBorders` tüm tabloya 2 puanlık siyah bir çizgi verir.  
- **Hücre gölgelendirmesi** – Tek tek hücreleri (kırmızı ve yeşil) renklendirmeyi gösterir.  
- **Özel hücre kenarlıkları** – Üçüncü hücreye tüm kenarlarda 4 puanlık bir kenarlık eklenir, böylece öne çıkar.

## Tablo Stilleri Uygulama (İlk Sütun Stili dahil)

Tablo stilleri, tek bir çağrı ile tutarlı bir görünüm sağlar. Ayrıca *ilk sütun stilini* etkinleştirme ve tabloyu içeriğine otomatik sığdırma işlemlerini de göstereceğiz.

### Adım 4: Stil İçin Yeni Bir Belge Oluşturma

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Adım 5: Önceden Tanımlı Stil Uygulama ve İlk Sütun Biçimlendirmesini Etkinleştirme

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Adım 6: Tabloyu Veriyle Doldurma

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Bunun önemi
- **Stil tanımlayıcısı** – `MEDIUM_SHADING_1_ACCENT_1` tabloya temiz, gölgeli bir görünüm kazandırır.  
- **İlk sütun stili** – İlk sütunu vurgulamak, özellikle raporlarda okunabilirliği artırır.  
- **Satır bantları** – Alternatif satır renkleri büyük tabloları göz yorgunluğunu azaltarak daha rahat okunur hâle getirir.  
- **Otomatik sığdırma** – Tablo genişliğinin içeriğe uyum sağlamasını sağlar, kesik metinlerin önüne geçer.

## Yaygın Sorunlar ve Çözüm Önerileri

| Sorun | Yaygın Neden | Hızlı Çözüm |
|-------|--------------|-------------|
| Kenarlıklar görünmüyor | Kenarlıkları ayarladıktan sonra `clearFormatting()` kullanılması | Kenarlıkları **temizleme işleminden sonra** ayarlayın veya yeniden uygulayın. |
| Birleştirilmiş hücrelerde gölgelendirme yok | Gölgelendirme birleştirmeden önce uygulanması | Hücreleri birleştirdikten **sonra** gölgelendirme uygulayın. |
| Tablo genişliği sayfa kenarlarını aşıyor | Otomatik sığdırma uygulanmamış | `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` çağırın veya sabit bir genişlik belirleyin. |
| Stil uygulanmadı | Yanlış `StyleIdentifier` değeri | Kullanmakta olduğunuz Aspose.Words sürümünde tanımlı olduğundan emin olun. |

## Sık Sorulan Sorular

**S: Varsayılan seçeneklerde bulunmayan özel tablo stilleri kullanabilir miyim?**  
C: Evet, özel stilleri programatik olarak oluşturup uygulayabilirsiniz. Ayrıntılar için [Aspose.Words belgelerine](https://reference.aspose.com/words/java/) bakın.

**S: Hücrelere koşullu biçimlendirme nasıl uygulanır?**  
C: Hücre değerlerini kontrol eden standart Java mantığını kullanın, ardından uygun biçimlendirme metodlarını (ör. değer bir eşiği aşarsa arka plan rengini değiştir) çağırın.

**S: Birleştirilmiş hücreleri normal hücreler gibi biçimlendirebilir miyim?**  
C: Kesinlikle. Hücreleri birleştirdikten sonra aynı `CellFormat` API’lerini kullanarak gölgelendirme veya kenarlık ekleyebilirsiniz.

**S: Tabloyu kullanıcı girdisine göre dinamik olarak yeniden boyutlandırmam gerekirse ne yapmalıyım?**  
C: Sütun genişliklerini ayarlayın veya yeni veri ekledikten sonra `autoFit` metodunu tekrar çağırarak yerleşimi yeniden hesaplatın.

**S: Tablo stiline dair daha fazla örnek nerede bulunur?**  
C: Resmi [Aspose.Words API belgeleri](https://reference.aspose.com/words/java/) kapsamlı bir örnek seti içerir.

## Sonuç

Artık **hücre kenarlıklarını nasıl değiştireceğiniz**, *ilk sütun stilini* nasıl uygulayacağınız ve Aspose.Words for Java ile **tablo içeriğini otomatik sığdırma** konularında eksiksiz bir araç setine sahipsiniz. Bu teknikleri ustalıkla kullanarak, raporlar, faturalar ve diğer iş‑kritik çıktılar için veri açısından zengin ve görsel olarak çekici belgeler üretebilirsiniz.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Son Güncelleme:** 2025-11-28  
**Test Edilen Sürüm:** Aspose.Words for Java 24.12 (yazım anındaki en yeni sürüm)  
**Yazar:** Aspose