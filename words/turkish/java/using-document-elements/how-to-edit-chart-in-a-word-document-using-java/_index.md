---
category: general
date: 2026-09-11
description: Java ile bir Word belgesindeki grafiği nasıl düzenlersiniz – grafik ayarlarını
  güncellemeyi, grafik ızgaralarını etkinleştirmeyi, grafik seçeneklerini değiştirmeyi
  ve güncellenmiş belgeyi kaydetmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: tr
lastmod: 2026-09-11
og_description: Java ile bir Word belgesindeki grafiği nasıl düzenlersiniz. Grafik
  ayarlarını güncellemek, grafik ızgaralarını etkinleştirmek, grafik seçeneklerini
  değiştirmek ve güncellenmiş belgeyi kaydetmek için bu kılavuzu izleyin.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Java kullanarak bir Word belgesindeki grafiği nasıl düzenlersiniz – tam
  kılavuz
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Java kullanarak bir Word belgesindeki grafiği nasıl düzenlersiniz
url: /tr/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word belgesinde Java kullanarak grafik nasıl düzenlenir

Bir Word dosyasında **grafik nasıl düzenlenir** ihtiyacınız varsa, bu rehber size tam adımları gösterir. Grafik ayarlarını nasıl güncelleyeceğinizi, grafik ızgaralarını etkinleştireceğinizi, grafik seçeneklerini değiştireceğinizi ve sonunda **güncellenmiş belgeyi kaydetmeyi** format kaybı olmadan öğreneceksiniz.

Grafiklerle programlı olarak çalışmak çoğu zaman bir kara kutu işlemi gibi hissettirebilir, özellikle mezürler veya ızgaralar gibi görsel detayları ayarlamak istediğinizde. Bu öğretici, belgeyi yüklemekten değişiklikleri kalıcı hale getirmeye kadar bilmeniz gereken her şeyi kapsar. Harici araçlara gerek yok—sadece Aspose.Words for Java kütüphanesi (sürüm 24.9 veya daha yeni).

Bu makalenin sonunda şunları yapabilecek duruma geleceksiniz:

* Bir grafik içeren `.docx` dosyasını yüklemek.
* Grafik şekline ulaşmak ve özelliklerini değiştirmek.
* Grafik ızgaralarını (mezürleri) etkinleştirmek ve diğer seçenekleri ayarlamak.
* **Güncellenmiş belgeyi** yeni bir dosyaya **kaydetmek**.

## Önkoşullar

* Makinenizde yüklü Java 17 veya daha yeni bir sürüm.  
* Bağımlılıkları yönetmek için Maven veya Gradle.  
* Aspose.Words for Java 24.9+ ( `setShowGraduations` metodunu getiren sürüm).  
* En az bir grafik içeren bir Word belgesi (`input.docx`).

Aspose.Words, Word belgelerini programlı olarak okumanıza, değiştirmenize ve kaydetmenize olanak tanıyan tam özellikli bir API olarak düşünebilirsiniz—tıpkı bir web tarayıcısında DOM ile çalışıyormuş gibi.

## Adım 1: Projeyi kurun ve kütüphaneyi içe aktarın

Yeni bir Maven projesi oluşturun ya da mevcut bir projeye bağımlılığı ekleyin:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Pro ipucu:** `setShowGraduations` metoduna sahip olduğunuzdan emin olmak için en son kararlı sürümü kullanın. Eski sürümler derlenmez.

## Adım 2: Grafik içeren Word belgesini yükleyin

Herhangi bir **grafik nasıl düzenlenir** iş akışının ilk adımı, kaynak dosyayı yüklemektir. Aspose.Words, tüm belgeyi `Document` sınıfı ile temsil eder.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

`Document` nesnesi, şekiller, tablolar ve paragraflar dahil dosya içindeki her düğüme erişim sağlar.  

## Adım 3: Belgede ilk grafik şekline ulaşın

Grafikler, renderlayıcısı bir `Chart` olan `Shape` düğümleri olarak depolanır. Bir grafiği düzenlemek için önce o düğümü almanız gerekir.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Belge birden fazla grafik içeriyorsa, `shapes` üzerinde döngü kurun ve `chartShape.getChart() != null` kontrolünü yaparak tip dönüşümünü gerçekleştirin. Bu, `ClassCastException` hatasını önler ve yalnızca geçerli grafik nesnelerinde **grafik seçeneklerini değiştirmeyi** sağlar.

## Adım 4: Grafik ızgaralarını (mezürleri) etkinleştirin – sürüm 24.9’da yeni bir özellik

`setShowGraduations` özelliği, değer eksenindeki küçük ızgaraların görünürlüğünü açıp kapatır. Bunları etkinleştirmek, yoğun veri setlerinde okunabilirliği artırır.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Neden önemli:** Izgaralar, izleyicilere her veri noktasını görsel olarak referans gösterir, böylece eğilimleri daha kolay fark ederler. Varsayılan değer `false` olduğundan, gerektiğinde açıkça etkinleştirmeniz gerekir.

Ayrıca büyük ızgaralar, eksen başlıkları veya lejand konumu gibi diğer öğeleri de özelleştirebilirsiniz. Aşağıda, **grafik seçeneklerini değiştirme** kapsamında grafik başlığını ve lejand konumunu değiştiren bir örnek yer alıyor.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## Adım 5: Güncellenmiş grafik ayarlarıyla belgeyi kaydedin

Grafiği değiştirdikten sonra değişiklikleri kalıcı hale getirin. Bu adım, **güncellenmiş belgeyi kaydet** aşamasını tamamlar.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

Programı çalıştırdığınızda `output.docx` dosyası oluşturulur; grafikte artık ızgaralar, yeni bir başlık ve yeniden konumlandırılmış bir lejand bulunur. Görsel değişiklikleri doğrulamak için dosyayı Microsoft Word’de açın.

## Tam kaynak kodu (çalıştırılabilir)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Beklenen sonuç

`output.docx` dosyasını açtığınızda:

* Grafik, değer ekseninde küçük ızgaralar gösterir.  
* Başlık **“Sales Overview 2026”** olarak görünür.  
* Lejand, grafiğin alt kısmına yerleştirilir.

Orijinal grafikte zaten ızgaralar varsa, görsel görünüm değişmez; bu, kodun **idempotent** olduğunu kanıtlar.

## Yaygın sorular ve kenar‑durum yönetimi

### Belge hiç grafik içermiyorsa ne olur?

Grafik olmayan bir şekli `Chart` tipine dönüştürmeye çalışmak `ClassCastException` hatası verir. Bunu önlemek için şekil tipini kontrol edin:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### İlk grafik yerine belirli bir grafiği nasıl düzenlerim?

`shapes` üzerinde döngü kurun ve bilinen bir başlık ya da alternatif bir tanımlayıcıyla eşleştirin:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Izgaraları daha sonra tekrar devre dışı bırakabilir miyim?

Evet, özelliği `false` olarak ayarlamanız yeterlidir:

```java
chart.setShowGraduations(false);
```

### `.doc` (ikili) dosyalarla da çalışır mı?

Aspose.Words dosya formatını soyutladığı için aynı kod `.doc` ve `.docx` dosyalarında çalışır. Ancak, mezürler gibi bazı yeni grafik özellikleri yalnızca OOXML formatında saklanır; bu yüzden etkiyi yalnızca `.docx` olarak kaydettiğinizde görürsünüz.

## Üretim‑hazır kod için ipuçları

* **Girdi yollarını doğrulayın** – `Files.exists(Paths.get(inputPath))` kullanarak yüklemeden önce kontrol edin.  
* **API çağrılarını** try‑catch bloklarıyla sarın; özellikle bozuk belgelerle çalışırken `Exception` detaylarını ortaya çıkarın.  
* **Kaynakları serbest bırakın** – Aspose.Words hafızayı yönetse de, `doc.close()` (veya mümkünse try‑with‑resources) çağrısı yerel tutamaçları daha erken serbest bırakabilir.  
* **Sürüm kontrolü** – `setShowGraduations` metodunu çağırmadan önce çalışma zamanı kütüphane sürümünün ≥ 24.9 olduğundan emin olun. Programatik bir kontrol için `License.getVersion()` sorgulayabilirsiniz.

## Sonuç

Artık Java kullanarak bir Word belgesindeki **grafik nasıl düzenlenir** konusunu biliyorsunuz. İşlem—belgeyi yükleme, grafiği bulma, grafik ızgaralarını etkinleştirme, grafik seçeneklerini değiştirme ve **güncellenmiş belgeyi kaydetme**—programatik grafik manipülasyonu için en yaygın senaryoları kapsar.  

Buradan itibaren veri serisi renklerini değiştirme, grafik stilleri uygulama veya grafiği resim olarak dışa aktarma gibi ek özelleştirmelere göz atabilirsiniz. Bu görevlerin her biri aynı desen izler: `Chart` örneğini alın, özelliklerini ayarlayın ve **güncellenmiş belgeyi kaydedin**.

İyi kodlamalar, raporlama ihtiyaçlarınıza uygun diğer grafik ayarlarını denemekten çekinmeyin!


## Bir sonraki öğrenmeniz gerekenler


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}