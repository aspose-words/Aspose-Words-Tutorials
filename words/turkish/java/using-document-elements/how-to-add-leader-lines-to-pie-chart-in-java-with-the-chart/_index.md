---
category: general
date: 2026-08-20
description: Java'da pasta grafiğine hızlıca lider çizgileri ekleyin. Chart API'yi
  kullanarak dilimleri eklemeyi, patlatmayı, yeniden renklendirmeyi ve etiketlemeyi
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: tr
lastmod: 2026-08-20
og_description: Java'da pasta grafiğine bağlantı çizgileri ekleyin, kısa bir örnekle.
  Chart API'yi kullanarak dilimleri eklemek, patlatmak, yeniden renklendirmek ve etiketlemek
  için bu kılavuzu izleyin.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Java'da pasta grafiğine bağlantı çizgileri ekleyin – adım adım Chart API
  rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Java'da Chart API ile pasta grafiğine lider çizgileri nasıl eklenir
url: /tr/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java'da Chart API ile pasta grafiğine lider çizgileri ekleme

Java'da **pasta grafiğine lider çizgileri ekle**meniz gerekiyorsa, bu kılavuz size tüm süreci adım adım gösterir. Bir pasta grafiği eklemeyi, bir dilimi vurgulamak için patlatmayı, rengini değiştirmeyi ve sonunda patlatılan bölümü etiketleyen lider çizgileri etkinleştirmeyi göreceksiniz.

Örnek, birçok Java raporlama kütüphanesinde bulunan standart Chart API'yi kullanır. Harici bir araç gerekmez ve kod herhangi bir JDK 8+ ortamında çalışır.

## Öğrenecekleriniz

* `Chart` tipinde `ChartType.PIE` bir `Chart` oluşturun ve özel bir boyut belirleyin.  
* İlk dilimi vurgulamak için patlatın.  
* Patlatılan dilimin sektör rengini maviye ayarlayın.  
* **pasta grafiğine lider çizgileri ekle** böylece dilim etiketi net bir şekilde bağlanır.

Chart kütüphanesinin sınıf yolunda (classpath) bulunduğu bir Java projeniz zaten olmalı. Maven kullanıyorsanız, önkoşullar bölümünde gösterilen bağımlılığı ekleyin.

## Önkoşullar

* JDK 8 veya daha yeni bir sürüm yüklü.  
* Chart kütüphanesi (ör. `com.example.chart:chart-api:2.5.0`).  
* Java sınıfları ve metod çağrıları konusunda temel bilgi.

---

## Pasta grafiğine lider çizgileri ekleme

Aşağıda her adımı gösteren tam, çalıştırılabilir bir program bulunmaktadır. Kod kasıtlı olarak bağımsızdır, böylece kopyalayıp yapıştırarak değişiklik yapmadan çalıştırabilirsiniz.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Her adımın açıklaması

| Adım | Kodun yaptığı şey | Neden önemli |
|------|-------------------|----------------|
| **1️⃣ Pasta grafiği ekle** | `builder.insertChart(ChartType.PIE, 400, 300)` 400 × 300 piksel bir pasta grafiği oluşturur. | Grafik konteynerini oluşturur ve boyutlarını tanımlar; bu, etiket yerleşimini ve lider çizgi uzunluğunu etkiler. |
| **2️⃣ İlk dilimi patlat** | `setExplosion(20)` dilimi yarıçapın %20'si kadar kaydırır. | Patlatılmış bir dilim izleyicinin dikkatini çeker ve lider çizginin görünür olmasını sağlar. |
| **3️⃣ Sektör rengini ayarla** | `setSectorColor(Color.BLUE)` dilimin dolgusunu maviye değiştirir. | Renk kontrastı okunabilirliği artırır, özellikle dilim vurgulandığında. |
| **4️⃣ Lider çizgileri etkinleştir** | `setLeaderLines(true)` dilimi etiketine bağlayan bağlayıcı çizgileri açar. | Lider çizgileri, dilim dışa doğru hareket ettirildiğinde bile etiketin okunabilir kalmasını sağlar. |

`saveAsPng` çağrısı isteğe bağlıdır ancak görsel sonucu doğrulamak için faydalıdır. Programı çalıştırdıktan sonra aşağıdaki gibi bir görüntü görmelisiniz.

![Pasta grafiğine lider çizgileri ekleme](https://example.com/assets/pie-leader-lines.png "Pasta grafiğine lider çizgileri ekleme – patlatılmış dilim mavi renk ve lider çizgileri ile")

*Şekil: İlk dilimin patlatıldığı, mavi renklendirildiği ve bir lider çizgisiyle etiketine bağlandığı bir pasta grafiği.*

## Lider çizgileri özelleştirme (ileri düzey)

Temel `setLeaderLines(true)` çağrısı kütüphanenin varsayılan stilini kullanır. Görünümü daha da kontrol edebilirsiniz:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Bu seçenekler, kurumsal marka ile uyum sağlamak veya erişilebilirliği artırmak istediğinizde kullanışlıdır.

### Birden fazla seriyi işleme

Pasta grafiğiniz birden fazla seri içeriyorsa, lider çizgilerini yalnızca belirli bir dilim için istiyor olabilirsiniz. Doğru öğeyi hedeflemek için seri indeksini kullanın:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Bir dilim patlatılmadığında, lider çizgi genellikle otomatik olarak gizlenir, ancak `setLeaderLineEnabled(true)` ile zorlayabilirsiniz.

## Yaygın tuzaklar ve nasıl önlenir

| Sorun | Belirti | Çözüm |
|--------|---------|-----|
| **Lider çizgileri görünmüyor** | Grafik bağlayıcılar olmadan render edilir. | Dilimin patlatıldığından (`setExplosion` > 0) emin olun veya dilimde lider çizgileri açıkça etkinleştirin. |
| **Etiket çakışmaları** | Etiketler birbirine çarpışıyor. | Grafik boyutunu artırın veya `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)` ayarlayın. |
| **Renk uygulanmadı** | Dilimin varsayılan renk kalır. | Doğru seri indeksini hedeflediğinizi (`getSeries().get(0)`) doğrulayın. |
| **Görsel kaydedilmedi** | `saveAsPng` bir istisna fırlatıyor. | Çıktı dizini için yazma izinlerini ve kütüphanenin PNG dışa aktarımını desteklediğini kontrol edin. |

Bu sorunları erken ele almak, çalışma zamanı sürprizlerini önler ve düzgün bir grafik üretir.

## Tam kaynak kodu listesi

Kolaylık sağlamak için, importlar ve yorumlar dahil tam kaynak dosyasını tekrar aşağıda bulabilirsiniz:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

Bu programı çalıştırdığınızda `pie-with-leader-lines.png` oluşturulur; bu dosya patlatılmış mavi bir dilim ve dilim etiketine işaret eden net lider çizgileri içeren bir pasta grafiği gösterir.

## Sonuç

Artık Java'da Chart API kullanarak **pasta grafiğine lider çizgileri ekleme** nesnelerini nasıl yapacağınızı biliyorsunuz. İşlem, bir `ChartType.PIE` eklemek, istenen dilimi patlatmak, rengini özelleştirmek ve lider çizgileri etkinleştirmekten oluşur. İsteğe bağlı stil seçenekleriyle çizgi rengini, kalınlığını ve etiket yerleşimini ince ayar yaparak herhangi bir görsel gereksinimi karşılayabilirsiniz.

Sonra, **pie chart explosion Java**, **set sector color Chart API** ve **builder.insertChart usage** gibi ilgili konuları keşfetmeyi düşünün; böylece donut grafikleri, yığılmış pasta grafikleri veya etkileşimli panolar gibi daha karmaşık görselleştirmeler oluşturabilirsiniz.

Farklı dilim indeksleri, renkler ve lider‑çizgi stilleriyle denemeler yapmaktan çekinmeyin—her ayarlama ile grafikleriniz daha bilgilendirici ve görsel olarak çekici hale gelecektir. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalarla tam çalışan kod örnekleri içerir ve ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olur.

- [Java için Aspose.Words kullanarak sütun grafiği oluşturma](/words/english/java/document-conversion-and-export/using-charts/)
- [Bir grafiğin eksenine tarih saat değerleri ekleme](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [.NET için Aspose.Words kullanarak Word'e sütun grafiği ekleme](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}