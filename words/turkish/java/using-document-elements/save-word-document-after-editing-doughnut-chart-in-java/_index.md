---
category: general
date: 2026-09-11
description: Aspose.Words for Java ile bir donut grafiğini düzenledikten sonra Word
  belgesini kaydedin. Donut deliği boyutunu nasıl değiştireceğinizi, donut grafiğini
  nasıl döndüreceğinizi ve donut grafik özelliklerini nasıl düzenleyeceğinizi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: tr
lastmod: 2026-09-11
og_description: Aspose.Words for Java kullanarak bir halka grafiğini düzenledikten
  sonra Word belgesini kaydedin. Bu öğreticide, halka deliğinin boyutunu nasıl değiştireceğiniz,
  halka grafiğini nasıl döndüreceğiniz ve grafiğin görünümünü nasıl özelleştireceğiniz
  gösterilmektedir.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Doughnut grafiğini düzenledikten sonra Word belgesini kaydet – Java rehberi
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Java'da halka grafiğini düzenledikten sonra Word belgesini kaydet
url: /tr/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java'da doughnut grafiği düzenledikten sonra Word belgesini kaydetme

Eğer özelleştirilmiş bir doughnut grafiği içeren **Word belgesini** kaydetmeniz gerekiyorsa, bu kılavuz tam olarak nasıl yapılacağını gösterir. Sadece birkaç Java satırıyla doughnut deliğini değiştirebilir, doughnut grafiğini döndürebilir ve ardından sonucu diske yazabilirsiniz.

Aspose.Words for Java kullanan eksiksiz, çalıştırılabilir bir örnek göreceksiniz; ayrıca birden fazla grafiği işleme, düğüm tiplerini doğrulama ve yaygın hatalardan kaçınma ipuçları bulacaksınız. Harici referanslara gerek yok—gereken her şey dahil.

## Önkoşullar

- Java 17 veya daha yeni bir sürüm yüklü
- Bağımlılıkları yönetmek için Maven veya Gradle
- Aspose.Words for Java (version 23.9 or later) added to your project  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- `input.docx` adlı, tek bir doughnut grafiği içeren bir Word dosyası

## Adım 1: Word belgesini yükleyin

İlk adım, kaynak dosyayı açmaktır. Bu adım, sonraki tüm işlemlerin bellek içindeki `Document` nesnesi üzerinde çalışması gerektiği için çok önemlidir.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Neden?** Belgeyi yüklemek, şekilleri, tabloları ve grafikleri dolaşmanıza izin veren bir DOM temsili oluşturur. Dosya açılamazsa, Aspose.Words bir istisna fırlatır, böylece yolun yanlış olduğunu hemen anlarsınız.

## Adım 2: doughnut grafik şeklinin konumunu bulun

Bir grafik, bir `Shape` düğümünün içinde depolanır. Grafik barındıran ilk şekli alır ve renderlayıcısını `Chart` tipine dönüştürürüz.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Neden?** `isChart()` kontrolü, belgede grafikten önce resimler veya diğer şekiller bulunduğunda `ClassCastException` oluşmasını önler. Bu, karışık içerikli belgeler için kodu dayanıklı hâle getirir.

## Adım 3: doughnut deliği boyutunu değiştirin  

Şimdi doughnut deliğini düzenliyoruz. `setHoleSize` yöntemi, grafiğin yarıçapının yüzde olarak bir değerini (10 – 90) bekler.

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Neden?** doughnut deliğini değiştirmek (`change doughnut hole` / `change chart hole size`) merkezi alanı vurgulamanıza veya vurgusunu azaltmanıza olanak tanır. 10‑90 % aralığının dışındaki değerler API tarafından göz ardı edilir.

## Adım 4: doughnut grafiğini döndürün  

İlk dilimin nereden başlayacağını kontrol etmek için ilk‑dilim açısını ayarlayın. Bu, **doughnut grafiğini döndürür**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Neden?** Grafiği döndürmek, belirli bir dilimin üstte görünmesini istediğinizde veya bir tasarım gereksinimiyle eşleşmesi gerektiğinde faydalıdır.

## Adım 5: Güncellenen belgeyi kaydedin  

Son olarak, değişiklikleri yeni bir dosyaya yazın. İşte **Word belgesini** düzenlenmiş grafikle kaydettiğiniz an.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Beklenen sonuç:** `output.docx` orijinal içeriği içerir, ancak doughnut grafiğinin deliği artık %30 ve ilk dilimi 45 °'de başlar. Dosyayı Microsoft Word'de açtığınızda dönüştürülmüş grafik gösterilir.

## Tam çalışan örnek

Aşağıda IDE'nize kopyalayıp yapıştırabileceğiniz eksiksiz program yer alıyor. **doughnut grafiğini düzenlemek** ve **Word belgesini kaydetmek** için gereken tüm importları ve hata yönetimini içerir.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Beklenen çıktı

`output.docx` dosyasını açtığınızda:

- doughnut grafiğinin merkezi delik, grafiğin yarıçapının yaklaşık üçte birini kaplar.  
- İlk dilim 45 derece konumunda başlar ve tüm grafik saat yönünde kaydırılır.  

Her iki görsel değişiklik de Word'de anında yansıtılır.

## Yaygın varyasyonlar ve kenar durumları

| Situation | How to handle |
|-----------|----------------|
| **Birden fazla grafik** | Iterate through `doc.getChildNodes(NodeType.SHAPE, true)` and filter `shape.isChart()`; apply `setHoleSize` / `setFirstSliceAngle` to each `Chart`. |
| **Grafik doughnut değil** | Check `chart.getType()`; only call `setHoleSize` when `chart.getType() == ChartType.DOUGHNUT`. |
| **Deliği dinamik olarak değiştirme ihtiyacı** | Compute the desired percentage based on data values, then call `setHoleSize(computedValue)`. |
| **Akıma kaydetme** | Use

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren eksiksiz çalışan kod örnekleri sunar.

- [Aspose.Words for Java kullanarak sütun grafiği oluşturma](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words for Java ile belgeyi PDF olarak kaydetme](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aspose.Words for Java kullanarak Word belgesini şifreyle kaydetme](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}