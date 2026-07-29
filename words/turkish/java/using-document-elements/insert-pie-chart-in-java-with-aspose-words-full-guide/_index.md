---
category: general
date: 2026-07-29
description: Aspose.Words for Java kullanarak pasta grafiği ekleyin ve halka grafiği
  oluşturmayı, pasta grafiğini biçimlendirmeyi, Word grafiğini biçimlendirmeyi ve
  grafik boyutunu özelleştirmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: tr
lastmod: 2026-07-29
og_description: Aspose.Words for Java ile pasta grafiği ekleyin ve hızlıca halka grafiği
  oluşturmayı, pasta grafiğini biçimlendirmeyi, Word grafiğini biçimlendirmeyi ve
  profesyonel belgeler için grafik boyutunu özelleştirmeyi öğrenin.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Java'da pasta grafiği ekleme – Tam Aspose.Words Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Aspose.Words ile Java'da Pasta Grafiği Ekleme – Tam Kılavuz
url: /tr/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java ile Aspose.Words kullanarak pasta grafiği ekleme – Tam Kılavuz

Bir Word belgesine **pasta grafiği eklemeyi** Java kodundan nasıl yapacağınızı hiç merak ettiniz mi? Tek başınıza değilsiniz—birçok geliştirici, verileri programatik olarak görselleştirmenin hızlı bir yoluna ihtiyaç duyduklarında bu engelle karşılaşıyor. İyi haber? Aspose.Words for Java ile sadece birkaç satır kodla bunu yapabilirsiniz ve aynı zamanda **donut grafiği oluşturabilir**, **pasta grafiğini biçimlendirebilir**, **grafik Word biçimlendirmesi** yapabilir ve **grafik boyutunu özelleştirebilirsiniz**.

Bu öğreticide, boş bir belge oluşturup içine bir pasta grafiği ekleyen, birkaç görsel özelliği ayarlayan ve sonunda dosyayı kaydeden gerçek bir örnek üzerinden ilerleyeceğiz. Sonuna geldiğinizde, grafik otomasyonu gerektiren herhangi bir Java projesine yapıştırabileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız. Ek kütüphaneler, Office interop ile manuel uğraşma yok—sadece temiz, derlenmiş Java.

## Gereksinimler

- **Java 17** (veya daha yeni bir JDK; API geriye dönük uyumludur)
- **Aspose.Words for Java** 22.12 veya daha yenisi – Maven artefaktını ya da .jar dosyasını Aspose sitesinden alabilirsiniz.
- Basit bir IDE (IntelliJ IDEA, Eclipse, VS Code…) – `main` metodunu çalıştırabilen herhangi bir şey.
- İsteğe bağlı: Değerlendirme filigranını istemiyorsanız bir lisans dosyası.

Bu gereksinimlere sahipseniz, doğrudan koda geçebiliriz.

## Adım 1: Aspose.Words ile pasta grafiği ekleme

İlk olarak **pasta grafiği ekliyoruz** yeni bir belgeye. Bu adım, diğer tüm işlemler için temel oluşturur; çünkü grafik nesnesi serilere, veri noktalarına ve görsel ayarlamalara erişim sağlar.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Neden önemli:** `DocumentBuilder.insertChart` sadece grafiği oluşturmakla kalmaz, aynı zamanda manipüle edebileceğimiz bir `Chart` nesnesi döndürür. Genişlik ve yükseklik argümanları, **grafik boyutunu** oluşturma sırasında özelleştirmenizi sağlar, böylece sonradan yeniden boyutlandırmaya gerek kalmaz.

## Adım 2: Donut grafiği oluşturma (isteğe bağlı)

Tasarımınız ortada bir boşluk gerektiriyorsa—klasik bir donut grafiği düşünün—Aspose bunu tek satırda yapar. Aynı `Chart` örneği, delik boyutunu ayarlayarak normal bir pasta grafiğinden donut’a dönüştürülebilir.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **İpucu:** Delik boyutu sadece `ChartType.DONUT` için geçerlidir. Tipi `PIE` bırakırsanız, çağrı yok sayılır; bu yüzden denemekten çekinmeyin.

## Adım 3: Pasta grafiği dilimlerini biçimlendirme

İyi bir görsel, genellikle belirli bir dilimi vurgular. Burada **pasta grafiğini biçimlendiriyoruz**; ilk dilimi 20 puan dışarı doğru “patlatıyoruz”. Bu, okuyucunun en önemli veri noktasına odaklanmasını sağlar.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Profesyonel ipucu:** Birden fazla seriniz varsa `pieChart.getSeries()` üzerinden döngü kurup, renk, kenarlık veya veri etiketi gibi özellikleri ayrı ayrı ayarlayabilirsiniz. Bu, **grafik Word biçimlendirmesi** için zengin stil uygulamanın yoludur.

## Adım 4: Grafik verilerini ekleme

Verisiz bir grafik sadece süs eşyasıdır. Basit bir veri seti ekleyelim—örneğin çeyrek satış rakamları.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Neden yapıyoruz:** `ChartPoint` nesnelerini açıkça ekleyerek, grafiğin iş mantığımızı yansıtmasını sağlarız. `setShowCategoryName` ve `setShowValue` çağrıları, **pasta grafiğini biçimlendirme** kapsamında etiket ve sayıları göstermeyi sağlar.

## Adım 5: Görünümü ince ayar yapma (grafik boyutunu ve stilini özelleştirme)

İlk boyutların ötesinde, grafiğin lejandını, başlığını veya veri etiketleri için kullanılan yazı tipini de ayarlamak isteyebilirsiniz. Tüm bunlar **grafik boyutunu özelleştirme** ve genel biçimlendirme kapsamına girer.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Köşe durumu:** Daha sonra belgeyi PDF’ye dışa aktarmaya karar verirseniz, grafik vektör verileri puan cinsinden tanımlandığı için pikseller yerine keskin kalır. Bu, **grafik Word biçimlendirmesi** ve sonraki formatlar için bir avantajdır.

## Adım 6: Belgeyi kaydetme ve görüntüleme

Son adım, `doc.save` metodunu çağırmak kadar basittir. Bu, Microsoft Word, LibreOffice veya OpenXML formatını destekleyen herhangi bir görüntüleyicide açabileceğiniz bir `.docx` dosyası yazar.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Sonuç:** `PieChart.docx` dosyasını açtığınızda, patlatılmış bir dilim, başlık ve lejand içeren düzgün boyutlu bir pasta (veya donut) grafiği görürsünüz—hepsi UI’ye dokunmadan otomatik olarak üretilmiştir.

### Beklenen Çıktı

| Element | Görüntülenen şey |
|---------|-------------------|
| Grafik türü | Pasta grafiği (veya `holeSize` > 0 ise donut) |
| Dilim patlatma | İlk dilim 20 pt dışarı kaydırılmış |
| Lejand | Sağ tarafta konumlandırılmış |
| Başlık | Kalın 14 pt “Quarterly Sales Distribution” |
| Veri etiketleri | Her dilimde kategori adı ve değer gösterilir |
| Belge | Paylaşım için hazır standart bir Word `.docx` dosyası |

## Yaygın Sorular & Dikkat Edilmesi Gerekenler

- **Lisans gerekli mi?**  
  Değerlendirme sürümü test için uygundur, ancak bir filigran ekler. Temiz bir çıktı için `aspose.words.lic` dosyanızı sınıf yoluna (classpath) koyun.

- **Bunu Maven ile kullanabilir miyim?**  
  Kesinlikle. `pom.xml` dosyanıza aşağıdaki bağımlılığı ekleyin:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **Birden fazla serim olursa ne yapmalıyım?**  
  `pieChart.getSeries()` üzerinden döngü kurup, `setExplosion`, `setFillColor` gibi ayarları seriye özgü uygulayın. Bu, çok boyutlu veriler için **pasta grafiğini biçimlendirme** yöntemidir.

- **Grafik, oluşturulduktan sonra Word’de düzenlenebilir mi?**  
  Evet—kaydedildikten sonra belgeyi açıp renkleri, yazı tiplerini manuel olarak ayarlayabilir veya gerekirse pasta grafiğini çubuk grafiğe dönüştürebilirsiniz.

## Özet

Aspose.Words for Java kullanarak bir Word belgesine **pasta grafiği ekledik**, **donut grafiği oluşturduk**, **pasta grafiğini biçimlendirdik**, **grafik Word biçimlendirmesi** en iyi uygulamalarını gösterdik ve **grafik boyutunu özelleştirme** ile şık bir görünüm elde ettik. Yukarıdaki tam, çalıştırılabilir örnek, herhangi bir Java projesine eklenebilir ve COM interop ya da Office kurulumları olmadan anında grafik otomasyonu sağlar.

Sırada ne var? Veri kaynağını canlı bir veritabanına bağlayın, eşik değerlerine göre koşullu renkler ekleyin veya aynı belgeyi PDF’ye dışa aktararak baskıya hazır bir rapor oluşturun. Bu adımlar, oluşturduğumuz temelin üzerine inşa edildiği için geçiş sorunsuz olacaktır.

Herhangi bir sorunla karşılaşırsanız ya da ek geliştirme fikirleriniz (ör. yığılmış çubuk veya çizgi grafiği) varsa aşağıya yorum bırakın. İyi grafiklemeler!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve ilgili konuları derinlemesine ele alan tam çalışan kod örnekleri içerir. Her biri adım adım açıklamalarla API özelliklerini daha iyi kavramanızı ve projelerinizde alternatif uygulama yaklaşımları keşfetmenizi sağlar.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}