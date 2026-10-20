---
category: general
date: 2026-07-16
description: Aspose.Words kullanarak Java'da pasta grafiği oluşturun. Tek bir öğreticide
  bağlantı çizgileri eklemeyi, grafik açıklamasını göstermeyi ve bir dilimi patlatmayı
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: tr
lastmod: 2026-07-16
og_description: Aspose.Words kullanarak Java'da pasta grafiği oluşturun. Bu rehber,
  lider çizgileri eklemeyi, grafik açıklamasını göstermeyi ve bir dilimi patlatmayı
  (explode) göstererek, dakikalar içinde şık bir görsel elde etmenizi sağlar.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Aspose.Words Java ile Pasta Grafiği Oluşturma – Tam Biçimlendirme Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Aspose.Words Java ile Pasta Grafiği Oluşturma – Tam Adım Adım Kılavuz
url: /tr/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java ile Pasta Grafiği Oluşturma – Tam Adım‑Adım Kılavuz

Hiç **create pie chart** işlemini Java’da düşük seviyeli çizim API’leriyle uğraşmadan programatik olarak yapmayı düşündünüz mü? Tek başınıza değilsiniz. Birçok geliştirici raporlar, gösterge panelleri veya otomatik belgeler için hızlı bir görsele ihtiyaç duyar ve bu işi halletmek için Aspose.Words’e yönelir çünkü ağır işleri halleder.  

Bu öğreticide, sadece **creates a pie chart** yapmakla kalmayıp **add leader lines**, **show chart legend** ve hatta **explode a slice** özelliğiyle vurgulama yapmayı gösteren eksiksiz, çalıştırılabilir bir örnek üzerinden ilerleyeceğiz. Sonunda, bir müşteriyi etkileyecek kadar şık bir `.docx` dosyanız olacak.

> **Quick win:** Aşağıdaki kod parçacığı, Aspose.Words for Java 23.9 (veya daha yeni bir sürüm) ile kutudan çıkar çıkmaz çalışır. Ek bağımlılık yok, sadece JAR.

## Neler Öğreneceksiniz

- Boş bir Word belgesi oluşturmak için `DocumentBuilder` kullanın.
- Özel bir boyutta **pie chart** ekleyin.
- **explode slice** özelliğini kullanarak bir veri noktasını vurgulayın.
- **leader lines** özelliğini etkinleştirerek patlatılmış dilimin etikete bağlı kalmasını sağlayın.
- **chart legend** özelliğini açarak okuyucuların her dilimi anında tanımasını sağlayın.
- Sonucu Microsoft Word veya LibreOffice’te açabileceğiniz bir `.docx` dosyasına kaydedin.

**Önkoşullar** – Şunlara ihtiyacınız var:

1. Java 17 (veya daha yeni) yüklü.
2. Aspose.Words for Java JAR'ı sınıf yolunuzda.
3. Temel bir IDE veya metin düzenleyici—IntelliJ IDEA, Eclipse, VS Code, tercihiniz ne olursa olsun.

Şimdi, derinlemesine inceleyelim.

## Adım 1: Belgeyi ve Builder'ı Başlatma – **create pie chart** için Hazırlık

İlk olarak temiz bir belge tuvali gerekir. `Document` tüm Word dosyasını temsil ederken, `DocumentBuilder` içeriği eklememizi sağlayan yardımcıdır.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Why this matters:** Yeni bir `Document` ile başlamak, grafik oluşturmayı etkileyebilecek gizli stiller veya kalıntı nesnelerinin olmamasını garanti eder.

## Adım 2: **pie chart** Ekleme – Boyut Önemlidir

Aspose.Words, grafik eklemeyi tek satırda yapar. Burada 400 × 300 puan (yaklaşık 5.5 × 4.2 inç) boyutunda bir pasta grafiği istiyoruz.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Pro tip:** Farklı bir boyuta ihtiyacınız varsa sadece iki sayısal argümanı değiştirin. API puan cinsindendir, 72 puan = 1 inç.

## Adım 3: **How to explode slice** – Önemli bir veri noktasını vurgulama

Bir dilimi patlatmak, onu pastanın geri kalanından çıkararak okuyucunun gözünü çeker. `setExplosion` metodu, puan cinsinden bir mesafeyi temsil eden bir tamsayı alır.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **What if you have multiple series?** Farklı dilimleri patlatmak için `setExplosion` metodunu herhangi bir seri indeksinde (`get(1)`, `get(2)`, …) çağırabilirsiniz.

## Adım 4: **Add leader lines** ve **show chart legend** – Bağlantıyı kurma

Bir dilim patlatıldığında etiket uzaklaşabilir. Lider çizgiler, etiketi bağlayarak okunabilirliği korur. Aynı zamanda bir gösterge, tüm dilimler için hızlı bir anahtar sunar.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Why enable leader lines?** Lider çizgiler olmadan etiket havada süzülüyormuş gibi görünebilir ve hangi dilime ait olduğu konusunda kullanıcıları şaşırtabilir.  
> **Need a custom legend position?** `chart.getLegend().setPosition(LegendPosition.TOP)` ya da başka bir enum değeri kullanın.

## Adım 5: Belgeyi Kaydetme – Son **create pie chart** adımı

Son olarak belgeyi diske kalıcı hâle getiriyoruz. Yazma izniniz olan bir klasöre yolu ayarlamayı unutmayın.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Programı çalıştırın, oluşturulan `PieChartDemo.docx` dosyasını açın; patlatılmış ilk dilim, lider çizgileri ve görünür bir gösterge içeren güzel biçimlendirilmiş bir pasta grafiği görmelisiniz.

![Patlatılmış dilim, lider çizgileri ve gösterge ile pasta grafiği örneği](pie-chart-example.png){: .center-image alt="Patlatılmış dilim, lider çizgileri ve gösterge ile pasta grafiği örneği"}

### Beklenen Çıktı

Word dosyasını açtığınızda grafik yaklaşık olarak şu şekilde görünür:

- 400 × 300 pt bir pie chart.
- İlk dilim 10 pt kaydırılmış.
- İnce bir lider çizgi, patlatılmış dilimi etiketine bağlar.
- Grafiğin altında bir gösterge, her serinin adını listeler.

Lider çizgiyi görmüyorsanız, `setLeaderLines(true)` metodunun patlatma ayarından *sonra* çağrıldığından emin olun—sıra önemlidir.

## Yaygın Tuzaklar ve Nasıl Önlenir

| Sorun | Neden Oluşur | Çözüm |
|-------|--------------|------|
| **No legend appears** | `setShowLegend(true)` atlanmış ya da yanlış grafik nesnesinde çağrılmış. | `Chart` nesnesini şekilden aldıktan **sonra** `chart.setShowLegend(true)` çağırdığınızdan emin olun. |
| **Leader line missing** | Dilim patlatılmamış veya grafik tipi lider çizgileri desteklemiyor. | Sadece `ChartType.PIE` (veya `PIE_3D`) lider çizgileri destekler. Önce `setExplosion`, ardından `setLeaderLines(true)` çağırın. |
| **Slice doesn’t move** | Patlatma değeri çok düşük (0‑2 pt). | Tamsayıyı artırın, ör. `setExplosion(10)` gibi daha dramatik bir etki için daha yüksek bir değer kullanın. |
| **Chart looks distorted** | Kare olmayan bir boyut (genişlik ≠ yükseklik) pastayı ezebilir. | Genişlik ve yüksekliği eşit ya da yakın tutun; 400 × 300 çalışır ama 400 × 400 mükemmel bir daire verir. |

## Gelişmiş Ayarlamalar (İsteğe Bağlı)

Temel seviyenin ötesine geçmek isterseniz şunları değerlendirin:

- **Özel renkler**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Veri etiketleri**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3‑D efekti**: `ChartType.PIE` yerine `ChartType.PIE_3D` kullanın.

Bu seçenekler, görseli kurumsal marka yönergelerine uyacak şekilde ince ayar yapmanıza olanak tanır.

## Özet – Neler Başardık

Boş bir Word belgesiyle başladık, **created a pie chart**, **exploded the first slice**, **added leader lines**, ve **showed the chart legend**. Tüm akış, kısa bir `main` metoduna sığdırıldı; böylece daha büyük raporlama hatlarına kolayca entegre edilebilir.

## Sonraki Adımlar

- **Daha fazla seri ekleyin**: Grafiği bir veritabanı veya CSV'den gerçek verilerle doldurun.
- **PDF olarak dışa aktar**: `doc.save("output.pdf", SaveFormat.PDF);` kullanarak PDF sürümü oluşturun.
- **Diğer şekillerle birleştirin**: Tam bir rapor için tablolar, görseller veya ek grafikler ekleyin.

Diğer grafik türleri—sütun, çubuk, çizgi—ile ilgileniyorsanız sadece `ChartType.PIE` yerine uygun enum değerini koyun ve aynı biçimlendirme adımlarını izleyin.

*İyi grafikler!* Bir şey beklendiği gibi çalışmadıysa yorum bırakmaktan çekinmeyin ya da gösterge konumunu nasıl özelleştirdiğinizi paylaşın. Geri bildiriminiz hepimizin daha iyi otomatik belgeler oluşturmasına yardımcı olur.

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım‑adım açıklamalar içerir.

- [Java için Aspose.Words kullanarak sütun grafiği nasıl oluşturulur](/words/english/java/document-conversion-and-export/using-charts/)
- [Java için Aspose.Words ile PDF Belgeleri Nasıl Oluşturulur | Document Processing API](/words/english/java/)
- [Java için Aspose.Words Kullanarak Belgelere Filigran Ekleme](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}