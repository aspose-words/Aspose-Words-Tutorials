---
category: general
date: 2026-10-26
description: Java'da adım adım kodla halka grafiği oluşturun ve pasta grafiği ekleyin.
  Esnek grafik görselleştirmeleri için tam iş akışını öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: tr
lastmod: 2026-10-26
og_description: Bu rehberle Java’da halka grafiği oluşturun; ayrıca esnek görselleştirmeler
  için pasta grafiği eklemeyi de gösterir.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Halka grafiği oluştur ve pasta grafiği ekle – Java rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Donut grafiği nasıl oluşturulur ve pasta grafiği nasıl eklenir
url: /tr/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Doughnut grafiği oluşturma ve pie grafiği ekleme

Java'da **doughnut chart** oluşturmanız gerekiyorsa, bu öğretici size adım adım rehberlik eder. Ayrıca aynı builder API'sini kullanarak **pie chart** nasıl ekleyeceğinizi göstereceğiz, böylece görsel stiller arasında sorunsuzca geçiş yapabilirsiniz. Kılavuzun sonunda, her iki grafik türünü de üreten ve yaygın özelleştirmeleri gösteren tam, çalıştırılabilir bir programınız olacak.

Bu öğreticide şunlar ele alınır:

* Seçilen kütüphane tarafından sağlanan chart builder'ın başlatılması.  
* Bir doughnut chart oluşturma ve delik boyutunu yapılandırma.  
* Bir pie chart ekleme ve vurgulamak için bir dilimi patlatma.  
* Eksik seriler veya desteklenmeyen grafik türleri gibi kenar durumlarını ele alma ipuçları.

Sadece güncel bir JDK'ye (8 veya üzeri) ve classpath'inizde chart library JAR'ına ihtiyacınız var. Harici hizmetlere gerek yok.

---

## Önkoşullar

| Item | Reason |
|------|--------|
| Java Development Kit (JDK) 8+ | Örneği derlemek ve çalıştırmak için gereklidir. |
| Chart library (e.g., **Aspose.Cells for Java** or **JFreeChart**) | Kodda kullanılan `ChartBuilder`, `ChartType` ve seri manipülasyon metodlarını sağlar. |
| An IDE or a text editor | Java kaynak dosyasını yazmak ve çalıştırmak için. |

Kütüphane JAR'ının projenizin derleme yoluna eklendiğinden emin olun. Maven kullanıyorsanız uygun bağımlılığı ekleyin; aksi takdirde JAR'ı `libs` klasörüne koyun ve derleme sırasında referans verin.

---

## Adım 1: Chart builder'ı kurun

İlk adım, grafik nesnelerini oluşturacak bir `ChartBuilder` (veya eşdeğeri) örneği yaratmaktır. Bu nesne bir fabrika görevi görür ve grafiğin yerleştirileceği çalışma sayfasını veya kanvası tutar.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Neden önemlidir:**  
Builder, grafiği belirli bir çalışma sayfasına bağlar, böylece sonraki tüm grafik nesneleri aynı çizim yüzeyini paylaşır. Bu adımı atlamak, görsel öğeler için bir hedef konum bırakmaz.

---

## Adım 2: **doughnut chart oluştur**

Şimdi tanımlı bir boyutta doughnut chart oluşturuyoruz. Delik boyutu, grafiğin merkezinin ne kadarının boş olacağını belirler ve normal bir pie'ı doughnut'a dönüştürür.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Açıklama:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` grafik nesnesini oluşturur ve çalışma sayfasında yer ayırır.  
* `setHoleSize(30)` pie'ı %30 boş merkezli bir doughnut'a dönüştürür.  
* `add("{10, 20, 30, 40}", true)` dört veri noktasını sağlar; `true` bayrağı kütüphaneye değerleri tek bir seri olarak ele almasını söyler.

**Kenar durumu:** Seçilen grafik türü bir delik desteklemiyorsa (ör. çubuk grafik), `getDoughnutChart()` çağrısı bir istisna fırlatır. Delik boyutunu ayarlamadan önce her zaman grafik türünü doğrulayın.

---

## Adım 3: **pie chart ekle**

Doughnut hazır olduğunda, aynı builder'ı kullanarak **pie chart** nasıl **insert** edeceğimizi gösteriyoruz. Bu adım, iki grafik türü arasındaki benzerliği vurgular ve bir dilimi nasıl öne çıkaracağınızı gösterir.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Açıklama:**  

* `ChartType.PIE` builder'a klasik bir pie chart oluşturmasını söyler.  
* `setExplode(10)` ilk dilimi yarıçapın %10'u kadar kaydırır, önemli bir veri noktasını vurgulamak için yaygın bir tekniktir.  

**İpucu:** `setExplode` metodu yalnızca bir pie chart'ın ilk serisi üzerinde çalışır. Birden fazla seriniz varsa, doğru indeksi hedeflemeniz gerekir.

---

## Adım 4: Çalışma kitabını kaydet

Son olarak, çalışma kitabını bir dosyaya yazarak grafikleri Excel'de veya uyumlu herhangi bir görüntüleyicide görebilirsiniz.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Neden şimdi kaydedilir:** Çalışma kitabını kalıcı hale getirmek, tüm çizim işlemlerini tamamlar. Dosyayı kaydetmeden görüntümeye çalışmak boş veya eksik bir belgeyle sonuçlanır.

**Sonuç:** *DoughnutAndPieChart.xlsx* dosyasını açtığınızda, solda %30 delikli bir doughnut grafiği ve sağda patlatılmış birinci dilime sahip bir pie chart görülür.

---

## Adım 5: Yaygın varyasyonlar ve sorun giderme

| Situation | Adjustment |
|-----------|------------|
| **Farklı grafik boyutları** | `insertChart` içinde genişlik ve yükseklik argümanlarını değiştirin. |
| **Birden fazla veri serisi** | `add` metodunu birden fazla kez çağırın veya 2‑D dizi string'i geçirin. |
| **Dinamik delik boyutu** | Delik boyutunu veri aralığına göre hesaplayın, ardından `setHoleSize` çağırın. |
| **Birden fazla dilimi patlat** | Kaydırmak istediğiniz her dilim için `chart.getSeries().get(i).setExplode(percent)` döngüsü oluşturun. |
| **Kütüphane doughnut'ı desteklemiyor** | Bir pie chart kullanın ve manuel olarak beyaz bir daire üst katmanı çizin, ancak bu daha az hassastır. |

**Pro ipucu:** Büyük çalışma kitaplarıyla çalışırken grafik ekledikten sonra her zaman `builder.flush()` (varsa) çağırın. Bu, iç tamponları serbest bırakır ve bellek sızıntılarını önler.

---

![Java kodu ile doughnut grafiği oluşturma ve pie grafiği ekleme](https://example.com/images/doughnut-pie-java.png "Java'da doughnut grafiği örneği oluşturma")

*Görsel, her iki grafiğin yan yana olduğu son çalışma kitabı düzenini göstermektedir.*

---

## Sonuç

Artık Java'da akıcı bir builder API kullanarak **doughnut chart** oluşturmayı ve **pie chart** eklemeyi biliyorsunuz. Tam örnek, başlatma, boyut yapılandırması, delik ayarı, dilim patlatma ve dosya çıktısını kapsar. Bundan sonra, raporlama ihtiyaçlarınıza uygun renkler, lejandlar ve veri etiketleri gibi ek özelleştirmeleri keşfedebilirsiniz.

**Sonraki adımlar**

* Gradient doldurmalar ve veri etiketleri gibi **chart customization Java** özelliklerini deneyin.  
* Grafik oluşturmayı, talep üzerine çalışma kitabını dönen bir web servisine entegre edin.  
* Builder yaklaşımını diğer kütüphanelerle (ör. JFreeChart) karşılaştırarak projeniz için en uygun olanı seçin.

Grafik çiziminde iyi çalışmalar!

---

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Java ile bir Word belgesinde doughnut grafiği nasıl oluşturulur](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Java'da doughnut grafiği düzenledikten sonra Word belgesini kaydet](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Java'da Pie Chart ekleme – Dilimleri Patlatma, Döndürme ve Vurgulama](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}