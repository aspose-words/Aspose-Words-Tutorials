---
category: general
date: 2026-06-27
description: Aspose.Words for Java kullanarak DOCX'i hızlıca PNG'ye dönüştürün. Tüm
  sayfaları PNG olarak dışa aktarmayı ve bir seferde sayfa başına satır ve sütun sayısını
  ayarlamayı öğrenin.
draft: false
keywords:
- convert docx to png
- export all pages png
- how to set rows per page
- how to set columns per page
language: tr
og_description: Aspose.Words ile Java’da DOCX’i PNG’ye dönüştürün. Bu kılavuz, tüm
  sayfaları PNG olarak dışa aktarmayı ve sayfa başına satır ve sütun sayısını yapılandırmayı
  gösterir.
og_title: DOCX'i PNG'ye Dönüştür – Java Grid Export Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert DOCX to PNG quickly using Aspose.Words for Java. Learn to export
    all pages PNG and set rows per page and columns per page in one go.
  headline: Convert DOCX to PNG – Complete Java Guide with Grid Layout
  type: TechArticle
tags:
- Aspose.Words
- Java
- DOCX
- PNG
- Image conversion
title: DOCX'i PNG'ye Dönüştür – Grid Düzeniyle Tam Java Kılavuzu
url: /tr/java/document-conversion-and-export/convert-docx-to-png-complete-java-guide-with-grid-layout/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX'i PNG'ye Dönüştür – Izgara Düzeniyle Tam Java Rehberi

Hiç **DOCX'i PNG'ye dönüştürmek** istediğinizde her sayfayı tek tek kaydetmek zorunda kalmanın sıkıntısını düşündünüz mü? Tek başınıza değilsiniz. Birçok geliştirici, özellikle ön izleme küçük resimleri veya hızlı paylaşım için birden fazla sayfayı aynı anda gösteren tek bir görüntüye ihtiyaç duyduklarında bir çıkmaza giriyor.  

İyi haber: Aspose.Words for Java ile **tüm sayfaları PNG olarak dışa aktarabilir** ve **sayfa başına satır sayısını** ve **sayfa başına sütun sayısını** nasıl ayarlayacağınızı bile belirleyebilirsiniz. Bu öğreticide, bir Word belgesini yüklemekten düzenli bir ızgara görüntüsü üretmeye kadar tüm süreci adım adım inceleyeceğiz.

## Bu Öğreticide Neler Ele Alınıyor

Ön koşulları listeleyerek başlayacağız, ardından çözümü net adımlara böleceğiz. Sonuna geldiğinizde şunları yapabilecek durumdasınız:

* Diskten herhangi bir `.docx` dosyasını yükleyin.  
* `ImageSaveOptions` sınıfını yapılandırarak **tüm sayfaları PNG** olarak tek seferde dışa aktarın.  
* **Sayfa başına satır sayısını** ve **sayfa başına sütun sayısını** nasıl ayarlayacağınızı kullanarak 2 × 2 (veya istediğiniz) bir ızgara tanımlayın.  
* Sonucu, istediğiniz yerde gömebileceğiniz tek bir PNG dosyası olarak kaydedin.

Harici betikler, komut satırı hileleri yok—sadece projenize ekleyebileceğiniz saf Java kodu.

### Ön Koşullar

| Gereksinim | Neden Önemli |
|-------------|----------------|
| Java 8 ve üzeri | Aspose.Words 23.9+ en az Java 8 gerektirir. |
| Aspose.Words for Java JAR | `Document` ve `ImageSaveOptions` sınıflarını sağlar. |
| Test etmek için bir `.docx` dosyası | Dönüştüreceğiniz kaynak. |
| IDE veya yapı aracı (Maven/Gradle) | Örneği derlemek ve çalıştırmak için. |

Bu kutuları zaten işaretlediyseniz, harika—şimdi başlayalım.

## Adım 1: Projenizi Kurun ve Aspose.Words'u İçe Aktarın

İlk olarak Aspose.Words bağımlılığını ekleyin. Maven kullanıyorsanız, `pom.xml` dosyanıza şu satırı yapıştırın:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Gradle için ise şu şekilde görünür:

```groovy
implementation 'com.aspose:aspose-words:23.9'
```

Kütüphane sınıf yolunda olduğunda kodlamaya başlayabilirsiniz. İçe aktarma satırı oldukça basittir:

```java
import com.aspose.words.*;
```

> **Pro ipucu:** Bir bağımlılık yöneticisi kullanmıyorsanız, Aspose jar dosyalarınızı bir `libs/` klasörüne koyun ve derleme yoluna ekleyin.

## Adım 2: Kaynak Belgeyi Yükleyin

Bir DOCX'i yüklemek, `Document` yapıcısına dosya yolunu vermek kadar basittir. Bu, **docx'i png'ye dönüştür** sürecinin ilk somut adımıdır.

```java
// Step 2: Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

`YOUR_DIRECTORY` kısmını Word dosyanızın bulunduğu gerçek klasörle değiştirin. Dosya bulunamazsa Aspose bir `FileNotFoundException` fırlatır; bu yüzden yolun doğru olduğundan emin olun.

## Adım 3: PNG İçin Image Save Options Oluşturun

Şimdi Aspose'a PNG çıktısı istediğimizi söylüyoruz. `ImageSaveOptions` sınıfı, dönüşümü ince ayar yapmamıza olanak tanır; özellikle **tüm sayfaları PNG olarak dışa aktar** bayrağı kritik önemdedir.

```java
// Step 3: Create image save options for PNG format
ImageSaveOptions pngOptions = new ImageSaveOptions(SaveFormat.PNG);
```

Bu noktada seçenek nesnesi hazır, ancak çoklu sayfaları nasıl ele alacağımızı henüz belirtmedik.

## Adım 4: Tüm Sayfaları PNG Olarak Dışa Aktarın

Varsayılan olarak Aspose her sayfayı ayrı bir dosya olarak kaydeder. Hepsini bir araya getirmek için `pageCount` değerini `0` olarak ayarlayın. Aspose terminolojisinde `0`, “tüm sayfalar” anlamına gelir.

```java
// Step 4: Export all pages (0 means all pages)
pngOptions.setPageCount(0);
```

Şimdi kütüphane, **tüm sayfaları PNG olarak dışa aktar** isteğinizi anlıyor. Sadece ilk üç sayfayı isteseydiniz `pngOptions.setPageCount(3);` kullanırdınız.

## Adım 5: Sayfaları Bir Izgara Düzeninde Yerleştirin

İşte **sayfa başına satır sayısını** ve **sayfa başına sütun sayısını** nasıl ayarlayacağınızın devreye girdiği kısım. Sayfaları bir iletişim sayfası gibi ızgara şeklinde düzenlemesini Aspose'tan isteyeceğiz.

```java
// Step 5: Arrange pages in a grid layout
pngOptions.setPageLayout(ImageSaveOptions.PageLayout.GRID);
```

`GRID` düzeni, motorun sayfaları yatay ve dikey olarak, bir sonraki adımda belirleyeceğimiz boyutlara göre döşemesini sağlar.

## Adım 6: Izgara Boyutlarını Tanımlayın (Satır × Sütun)

İhtiyacınıza uygun herhangi bir kombinasyonu seçebilirsiniz. Aşağıdaki örnek 2 × 2 bir ızgara oluşturur, ancak kolayca 3 × 4 ya da tek satır gibi bir yapıya geçebilirsiniz.

```java
// Step 6: Define the grid dimensions (2 rows × 2 columns)
pngOptions.setRowsPerPage(2);      // how to set rows per page
pngOptions.setColumnsPerPage(2);   // how to set columns per page
```

Hücre sayısından daha fazla sayfanız varsa Aspose otomatik olarak bir sonraki satıra geçer. Tersine, daha az sayfanız varsa boş hücreler şeffaf kalır.

## Adım 7: Belgeyi Tek Bir PNG Görüntüsü Olarak Kaydedin

Son olarak, Aspose'a birleştirilmiş görüntüyü diske yazmasını söylüyoruz. Dosya adı istediğiniz gibi olabilir; sadece `.png` uzantısını koruyun.

```java
// Step 7: Save the document as a single PNG image using the grid layout
document.save("YOUR_DIRECTORY/Grid.png", pngOptions);
```

Program tamamlandığında aynı klasörde `Grid.png` dosyasını bulacaksınız. Açın ve `input.docx` dosyanızın ilk dört sayfasının düzenli bir 2 × 2 ızgarada göründüğünü göreceksiniz.

### Beklenen Çıktı

| Sayfa | Izgaradaki Konumu |
|------|-------------------|
| 1    | Sol‑üst           |
| 2    | Sağ‑üst           |
| 3    | Sol‑alt           |
| 4    | Sağ‑alt           |

Kaynak belgenizde dörtten fazla sayfa varsa, beşinci sayfa yeni bir satıra başlar (`rowsPerPage` artırırsanız) ya da 2 × 2 ızgarada kalırsa atlanır. PNG, orijinal sayfa boyutlarını korur; nihai görüntü boyutu `satır × sayfaYüksekliği` çarpı `sütun × sayfaGenişliği` olur.

## Tam Çalışan Örnek

Aşağıda, doğrudan çalıştırabileceğiniz tam Java programı yer alıyor. `DocxToPngGrid.java` adlı bir sınıfa kopyalayıp yapıştırın, yolları ayarlayın ve çalıştırın.

```java
import com.aspose.words.*;

public class DocxToPngGrid {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the DOCX file
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Prepare PNG save options
            ImageSaveOptions pngOptions = new ImageSaveOptions(SaveFormat.PNG);
            pngOptions.setPageCount(0);                     // export all pages PNG
            pngOptions.setPageLayout(ImageSaveOptions.PageLayout.GRID);

            // 3️⃣ Configure grid (2 rows × 2 columns)
            pngOptions.setRowsPerPage(2);   // how to set rows per page
            pngOptions.setColumnsPerPage(2); // how to set columns per page

            // 4️⃣ Save the combined image
            document.save("YOUR_DIRECTORY/Grid.png", pngOptions);

            System.out.println("Conversion complete! Check Grid.png.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

Şu komutla çalıştırın:

```bash
javac -cp "path/to/aspose-words-23.9.jar" DocxToPngGrid.java
java -cp ".:path/to/aspose-words-23.9.jar" DocxToPngGrid
```

Konsolda `Conversion complete!` mesajını göreceksiniz ve hedef klasörde bir `Grid.png` dosyası oluşmuş olacak.

## Yaygın Sorular & Kenar Durumları

**Farklı bir görüntü formatına ihtiyacım olursa?**  
`SaveFormat.PNG` yerine `SaveFormat.JPEG` ya da `SaveFormat.TIFF` kullanın. Kodun geri kalanı aynı kalır.

**Görüntü kalitesini kontrol edebilir miyim?**  
Evet. JPEG için `pngOptions.setJpegQuality(90);` çağırabilirsiniz. PNG kayıpsız olduğu için kalite ayarı yoktur.

**Büyük belgelerle ne olur?**  
Çok sayıda sayfa olduğunda ortaya çıkan PNG hafıza açısından çok büyük olabilir. `rowsPerPage`/`columnsPerPage` değerlerini artırmayı ya da çıktıyı birden fazla görüntüye bölmeyi düşünün.

**Lisans gerekir mi?**  
Aspose.Words lisanssız değerlendirme modunda çalışır, ancak oluşturulan PNG bir filigran içerir. Filigranı kaldırmak için lisans satın alın.

## Üretim Kullanımı İçin Pro İpuçları

* **`ImageSaveOptions` nesnesini yeniden kullanın** – Bir toplu işlemde birden çok belge dönüştürüyorsanız, seçenekleri bir kez oluşturup yeniden kullanarak ekstra nesne tahsisinden kaçının.  
* **Akış (stream) çıktısı** – Dosyaya kaydetmek yerine `ByteArrayOutputStream`'e yazıp PNG'yi HTTP üzerinden gönderebilirsiniz.  
* **İş parçacığı güvenliği** – `Document` nesneleri iş parçacığı‑güvenli değildir; her iş parçacığı için yeni bir `Document` oluşturun.  
* **Bellek profili** – 100 sayfadan fazla PDF'lerde heap kullanımını izleyin; JVM `-Xmx` bayrağını artırmanız gerekebilir.

## Sonuç

Aspose.Words for Java kullanarak **docx'i png'ye dönüştür** işlemini, dosyayı yüklemekten **tüm sayfaları PNG olarak dışa aktar** ayarına, **sayfa başına satır sayısını** ve **sayfa başına sütun sayısını** nasıl ayarlayacağınıza kadar adım adım gösterdik. Tek bir PNG, çok sayfalı bir Word belgesinin kompakt bir görsel özetini sunar—ön izlemeler, e‑posta ekleri veya hızlı paylaşım için mükemmeldir.

Bir sonraki meydan okumaya hazır mısınız? Her sayfaya bir filigran eklemeyi deneyin ya da UI tasarımınıza uygun farklı ızgara boyutlarıyla oynayın. Bu dönüşümü bir PDF oluşturucu ile zincirleyerek tek bir akışta çok‑formatlı raporlar da üretebilirsiniz.

Herhangi bir sorunla karşılaşırsanız, aşağıya yorum bırakın—mutlu kodlamalar!  

![docx'i png'ye dönüştürme örneği](placeholder.png){alt="docx'i png'ye dönüştürme örneği"}

## Sonra Ne Öğrenmelisiniz?


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve ilgili konuları derinlemesine ele alan örnek kodlar ve adım adım açıklamalar içerir.

- [Cómo convertir DOCX a PNG en Java – Aspose.Words](/words/spanish/java/document-converting/converting-documents-images/)
- [Wie man DOCX in PNG in Java konvertiert – Aspose.Words](/words/german/java/document-converting/converting-documents-images/)
- [Comment convertir DOCX en PNG en Java – Aspose.Words](/words/french/java/document-converting/converting-documents-images/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}