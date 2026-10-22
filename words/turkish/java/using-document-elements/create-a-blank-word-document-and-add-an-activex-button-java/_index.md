---
category: general
date: 2026-10-16
description: Java ile boş bir Word belgesi oluşturun ve Aspose.Words kullanarak bir
  ActiveX düğmesi eklemeyi, başlığını ayarlamayı ve boyutlarını düzenlemeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: tr
lastmod: 2026-10-16
og_description: Java ile boş bir Word belgesi oluşturun, ardından bir ActiveX düğmesi
  ekleyin, başlığını ayarlayın ve Aspose.Words kullanarak boyutlarını tanımlayın.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Boş bir Word belgesi oluşturun ve bir ActiveX düğmesi ekleyin – Java rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Boş bir Word belgesi oluşturun ve bir ActiveX düğmesi ekleyin (Java)
url: /tr/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Boş bir Word belgesi oluşturun ve bir ActiveX düğmesi ekleyin (Java)

Programlı olarak **boş bir Word belgesi oluşturmanız** gerekiyorsa, bu kılavuz Java ve Aspose.Words ile bunu nasıl yapacağınızı gösterir. Ayrıca **bir ActiveX düğmesi eklemeyi**, **düğme başlığını ayarlamayı** ve **düğme boyutlarını ayarlamayı** öğrenecek ve kontrolün tam istediğiniz gibi görünmesini sağlayacaksınız.

Bu öğreticide şunlar ele alınmaktadır:

* Aspose.Words for Java ile boş bir Word dosyası başlatma.  
* Bir ActiveX `CommandButton` kontrolü ekleme.  
* Düğmenin başlığını ve boyutunu yapılandırma.  
* Son `.docx` dosyasını kaydetme.

Temel Java bilgisine ve Aspose.Words for Java kütüphanesinin (kod 23.9 ve sonrası ile çalışır) güncel bir sürümüne sahip olmalısınız. Ek bağımlılıklar gerekmez.

![ActiveX düğmesiyle boş bir Word belgesi oluşturma](/images/activex-button-example.png){: .align-center alt="ActiveX düğmesiyle boş bir Word belgesi oluşturma"}

## Aspose.Words ile boş bir Word belgesi oluşturma

İlk adım, boş bir `Document` nesnesi örneklemektir. Bu nesne, tüm Word dosyasını bellek içinde temsil eder ve düzenleme için `DocumentBuilder` sınıfını sağlar.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Neden bu önemlidir:**  
Boş bir belge oluşturmak, temiz bir tuval sağlar; daha sonraki düzen hesaplamalarını etkileyebilecek gizli stiller veya bölümlerden kaçınmanızı sağlar.

## Belgeye bir ActiveX düğmesi ekleme

Aspose.Words, `Forms2OleControl` sınıfı aracılığıyla eski ActiveX kontrollerini gömmenize izin verir. Aşağıdaki kod, geçerli imleç konumunda bir `CommandButton` kontrolü ekler.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**İpucu:** `setOleClassName` değeri `"Forms.CommandButton.1"` standart Microsoft Forms düğmesi için ProgID'dir. Farklı bir ProgID (ör. `"Forms.CheckBox.1"`) kullanmak, farklı bir kontrol türü ekleyecektir.

## Düğme başlığını ayarlama

Başlık, düğme yüzünde görünen metindir. Belgeyi kaydetmeden önce istediğiniz zaman değiştirebilirsiniz.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Neden buna ihtiyacınız var:**  
Kullanıcılar, bir kontrolün amacı açık olduğunda onu anlar. Anlamlı bir başlık ayarlamak, özellikle belge Windows'ta Word ile açıldığında kullanılabilirliği artırır.

## Düğme boyutlarını ayarlama

Konum ve boyut, puan cinsinden belirtilir (1 puan = 1/72 inç). Değerleri düzeninize göre ayarlayın.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Yaygın varyasyonlar:**

| Senaryo | Ayarlama |
|----------|------------|
| Dokunmatik ekranlar için daha büyük düğme | `setWidth` ve `setHeight` değerlerini orantılı olarak artırın |
| Sayfada ortalanmış düğme | `left = (pageWidth - width) / 2` hesaplayın |
| Bir sütunda birden fazla düğme | Her yeni düğme için `setTop` değerini artırın |

## ActiveX düğmesi içeren belgeyi kaydetme

Son olarak, belgeyi diske yazın. `.docx` formatı, ActiveX kontrolünü Windows sürümlerindeki Microsoft Word için korur.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Beklenen sonuç:**  
`ActiveXCommandButton.docx` dosyasını Word (Windows) ile açtığınızda, sol kenar boşluğundan 100 pt, üst kenar boşluğundan 200 pt konumda **Click Me** etiketiyle bir tıklanabilir düğme gösteren boş bir sayfa görüntülenir.

## Tam, çalıştırılabilir örnek

Aşağıdaki sınıfı IDE'nize kopyalayın, Aspose.Words for Java JAR dosyasını proje sınıf yoluna ekleyin ve çalıştırın.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Programı çalıştırdığınızda çalışma dizininde `ActiveXCommandButton.docx` oluşturulur. Microsoft Word (Windows) ile açarak düğmenin tam olarak yapılandırıldığı gibi göründüğünü doğrulayın.

## Neden bu yaklaşım önerilir

* **Basitlik:** Yalnızca temel Aspose.Words API'si kullanılır; COM interop veya ek kütüphaneler gerekmez.  
* **Taşınabilirlik:** Kod, Java destekleyen herhangi bir platformda çalışır, ancak ActiveX kontrolü yalnızca Windows sürümlerindeki Word'de çalışır.  
* **Sürdürülebilirlik:** Tüm özellikler (başlık, boyutlar, konum) net, kendini belgeleyen yöntemlerle ayarlanır; gelecekteki ayarlamalar basittir.

## Yaygın tuzaklar ve nasıl önlenir

| Tuzak | Çözüm |
|---------|------------|
| Düğme macOS veya Linux'ta Word'de görünmüyor | ActiveX kontrolleri yalnızca Windows içindir. Çapraz platform belgeler için farklı bir kontrol (ör. içerik kontrolü) kullanın. |
| Başlık kesiliyor | Düğme genişliğinin metin için yeterli olduğundan emin olun; `setWidth` değerini artırın veya daha kısa bir başlık kullanın. |
| Düğme diğer içerikle çakışıyor | `setTop` ve `setLeft` değerlerini ayarlayın veya kontrolün önüne yeni bir paragraf ekleyerek ona ayrı bir alan sağlayın. |

## Sonraki adımlar

Artık **boş bir Word belgesi oluşturabilir**, **bir ActiveX düğmesi ekleyebilir**, **düğme başlığını ayarlayabilir** ve **düğme boyutlarını belirleyebilirsiniz**; şimdi şunları keşfedebilirsiniz:

* VBA makroları aracılığıyla olay işleme kodu ekleme (bir makro modülü gömmeyi gerektirir).  
* Form benzeri belgeler için tablo düzeninde birden fazla kontrol ekleme.  
* Çapraz platform form çözümleri için Aspose.Words’ **FormField** API'lerini kullanma.

Belirli belge tasarımınıza uyması için farklı boyutlar, konumlar ve başlıklarla denemeler yapın. Kodlamanın tadını çıkarın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanıza ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Java ile Word Belgesi Oluştur – Gölge Efektiyle Dikdörtgen Şekil Ekle](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java'da DocumentBuilder kullanarak form alanları oluşturma ve içerik ekleme](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java kullanarak belgeye filigran ekleme](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}