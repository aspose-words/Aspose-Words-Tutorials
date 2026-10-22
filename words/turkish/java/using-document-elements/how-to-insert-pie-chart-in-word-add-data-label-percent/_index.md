---
category: general
date: 2026-07-20
description: Aspose.Words ile Word’e pasta grafiği nasıl eklenir. Veri etiketi yüzde
  eklemeyi ve grafikte yüzde değerlerini göstermeyi öğrenin, profesyonel belgeler
  için.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: tr
lastmod: 2026-07-20
og_description: Aspose.Words kullanarak Word’e pasta grafiği nasıl eklenir. Bu kılavuz,
  veri etiketi yüzdesi eklemeyi ve grafikte yüzde değerlerini sadece birkaç satırda
  nasıl göstereceğinizi gösterir.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: Word'de pasta grafiği nasıl eklenir – hızlı rehber
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: Word'de pasta grafiği nasıl eklenir – veri etiketi yüzde ekle
url: /tr/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de pasta grafiği nasıl eklenir – veri etiketi yüzdesi ekleme

Ever wondered **how to insert pie chart** into a Word document without wrestling with the UI? You’re not alone. In many reporting scenarios you need to *add pie chart to Word* and, more importantly, **show percent on pie chart** so readers instantly grasp the data distribution.

Bu öğreticide Aspose.Words for Java kullanarak tam süreci adım adım göstereceğiz. Sonunda **add data label percent**, **display percentages on chart** nasıl yapılacağını tam olarak bilecek ve ilk seferde doğru görünen şık bir pasta grafiği elde edeceksiniz. Ekstra eklentiler yok, manuel ayarlamalar yok—herhangi bir projeye ekleyebileceğiniz temiz kod.

---

## Önkoşullar

- Java 17 (veya daha yeni) – Aspose.Words'un desteklediği mevcut LTS sürümü.
- Aspose.Words for Java 24.x (yazının yazıldığı tarih itibarıyla en yeni, Temmuz 2026).
- Kütüphaneyi çekmek için temel bir Maven veya Gradle yapılandırması.
- Sevdiğiniz bir IDE (IntelliJ IDEA, Eclipse, VS Code… herhangi biri yeterli).

Eğer bunlara sahipseniz, harika—hadi başlayalım.

---

## Adım 1: Projeyi kurun ve kütüphaneyi içe aktarın

İlk olarak, Aspose.Words bağımlılığını `pom.xml` (Maven) veya `build.gradle` (Gradle) dosyanıza ekleyin. Bu, `Document`, `DocumentBuilder` ve grafik sınıflarına erişim sağlar.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Sürüm numarasını güncel tutun; daha yeni sürümler genellikle grafikle ilgili düzeltmeler ekler ve **display percentages on chart** daha güvenilir hâle gelir.

---

## Adım 2: Yeni bir Word belgesi ve bir builder oluşturun

Builder, içerik eklemek için çok amaçlı bir araçtır. Burada yeni bir belge oluşturup ona bir `DocumentBuilder` ekliyoruz.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Neden bir builder'a ihtiyacımız var? Düşük seviyeli OpenXML yapılarını soyutlayarak, *ne* istediğimize (örneğin **add pie chart to word**) odaklanmamızı sağlar; *XML'in nasıl göründüğü* ile uğraşmak zorunda kalmayız.

---

## Adım 3: Pasta grafiğini ekleyin

Şimdi **how to insert pie chart**'in özüne geliyoruz. Builder'a belirli bir boyutta pasta grafiği yerleştirmesini istiyoruz. Boyutlar puan cinsindendir (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

Bu noktada grafik boş, ancak yer tutucu belgeye zaten eklenmiş durumda. Programlı olarak **add pie chart to word** yaptınız.

---

## Adım 4: Grafiği veriyle doldurun

Bir pasta grafiğinin en az bir değer serisine ihtiyacı vardır. Pazar payını temsil eden örnek verileri ekleyelim.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Eğer birden fazla seri (katmanlı pasta, donut vb.) ihtiyacınız olursa `pieChart.getSeries().add()` çağırıp adımları tekrarlayabilirsiniz. Her dilim için **display percentages on chart** istediğinizde aynı mantık geçerlidir.

---

## Adım 5: **add data label percent** – dilimlerde yüzdeyi göster

Bu, çoğu geliştiricinin unutduğu kısımdır: veri etiketlerini yüzde gösterecek şekilde yapılandırmak. Olmazsa, grafik yalnızca ham sayıları gösterir ve bu belirsiz olabilir.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

`setShowPercent(true)` çağrısı, Aspose.Words'e etiketi “%30”, “%45” gibi göstereceğini söyler. Bu, **show percent on pie chart**'i ekstra biçimlendirme yapmadan yapmanın tam yoludur.

---

## Adım 6: Belgeyi kaydedin

Son olarak, belgeyi diske yazın. `.docx`, `.pdf` veya hatta `.html` seçebilirsiniz. Bu rehberde modern `.docx` formatını kullanacağız.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Programı çalıştırın, `PieChartDemo.docx` dosyasını açın ve her dilimde yüzde etiketleriyle düzgün bir şekilde render edilmiş bir pasta grafiği göreceksiniz.

---

## Beklenen çıktı

Aşağıda oluşturulan Word dosyasının bir ekran görüntüsü var. Her dilimin payını yüzde olarak gösterdiğine dikkat edin—**add data label percent** ayarladığımızda tam olarak istediğimiz şey.

![Yüzde etiketli bir pasta grafiği içeren Word belgesinin ekran görüntüsü](/images/pie-chart-percent.png){.center width=600px alt="Word'de yüzde etiketli pasta grafiği eklemenin nasıl yapılacağını gösteren ekran görüntüsü"}

*Alt metin ana anahtar kelimeyi içerir, hem SEO hem de erişilebilirlik açısından uygundur.*

---

## Sık sorulan sorular ve uç‑durum yönetimi

| Question | Answer |
|----------|--------|
| **Yüzde etiketlerinin fontunu değiştirebilir miyim?** | Evet. `setShowPercent(true)` etkinleştirildikten sonra `DataLabel` nesnesini alıp `Font` özelliğini ayarlayabilirsiniz (`dataLabel.getFont().setSize(10);`). |
| **Pasta yerine donut grafik ihtiyacım olursa ne yapmalıyım?** | `insertChart` çağrısında `ChartType.PIE` yerine `ChartType.DOUGHNUT` kullanın. Aynı **add data label percent** mantığı çalışır. |
| **Eski Word sürümleri (2007‑2010) yüzde değerlerini doğru gösteriyor mu?** | Aspose.Words, temel XML'i sürüm bağımsız bir şekilde yazar; bu yüzden yüzde değerleri grafikleri destekleyen herhangi bir Word sürümünde (2007+) görünür. |
| **Grafiğe bir başlık nasıl eklenir?** | Kaydetmeden önce `pieChart.getTitle().setText("Market Share");` kullanın. |
| **Grafiği belirli bir paragraf ya da tablo hücresine ekleyebilir miyim?** | Kesinlikle. `insertChart` çağırmadan önce `DocumentBuilder`'ı istediğiniz konuma taşıyın (`builder.moveToParagraph(index, true);` veya `builder.moveToCell(table, row, column, true);`). |

---

## Alandan ipuçları ve püf noktaları

- **Pro tip:** Bir döngüde birçok grafik üretmeyi planlıyorsanız, tek bir `DocumentBuilder` örneğini yeniden kullanın; bu bellek tüketimini azaltır.
- **Watch out for:** Çok küçük dilimler (< 2 %). Aspose.Words, karışıklığı önlemek için etiketi atlayabilir; `dataLabel.setShowLabel(true);` ile zorlayabilirsiniz.
- **Performance note:** Grafik renderleme CPU‑yoğun bir işlemdir. Toplu rapor üretiminde çoklu iş parçacığı (multi‑threading) düşünün ancak her iş parçacığının kendi `Document` örneği üzerinde çalıştığından emin olun.
- **Version check:** `setShowPercent` yöntemi Aspose.Words 22.8'de tanıtıldı. Daha eski bir sürüm kullanıyorsanız, yükseltin veya yüzde değerlerini manuel olarak hesaplayıp özel etiket olarak ayarlayın.

---

## Özet

Aspose.Words kullanarak bir Word belgesine **how to insert pie chart** eklemeyi, **add data label percent** nasıl yapılacağını gösterdik ve **display percentages on chart** en kolay yolunu gösterdik. Sadece birkaç Java satırıyla **add pie chart to word** ve **show percent on pie chart** yapabilir, ham sayıları anında okunabilir görsellere dönüştürebilirsiniz.

---

## Sıradaki adım ne?

- Diğer grafik tipleri (`BAR`, `LINE`, `AREA`) ile deney yapın ve aynı **add data label percent** mantığının nasıl uygulandığını görün.
- Grafikleri tablolarla birleştirerek daha zengin raporlar oluşturun—Aspose.Words bir grafiği veri tablosunun yanına yerleştirmeyi çok basit hâle getirir.
- Aynı belgeyi PDF veya HTML'ye dışa aktararak yüzde değerlerinin farklı formatlarda nasıl render edildiğini keşfedin.

Boyutları, renkleri veya veri kaynağını (ör. bir veritabanı sorgusu) istediğiniz gibi değiştirin ve Word raporlarınızın canlandığını izleyin. Bir sorunla karşılaşırsanız, aşağıya yorum bırakın—iyi grafiklemeler!

---

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words for .NET Kullanarak Word'e Sütun Grafiği Ekleme](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET ile Word Belgesine Alan Grafiği Ekleme](/words/english/net/working-with-charts/insert-area-chart/)
- [Aspose.Words for .NET Kullanarak Word'e Balon Grafiği Ekleme](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}