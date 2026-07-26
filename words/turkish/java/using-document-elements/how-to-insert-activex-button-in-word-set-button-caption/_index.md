---
category: general
date: 2026-07-26
description: Aspose.Words kullanarak bir Word belgesine ActiveX düğmesi ekleme – düğme
  başlığını, konumunu ve boyutunu sadece birkaç satırda nasıl ayarlayacağınızı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: tr
lastmod: 2026-07-26
og_description: Aspose.Words ile bir Word belgesine ActiveX düğmesi nasıl eklenir.
  Düğme başlığını, konumunu ve boyutunu ayarlamak için bu adım adım öğreticiyi izleyin.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Word'de ActiveX Düğmesi Nasıl Eklenir – Hızlı Rehber
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Word'de ActiveX Düğmesi Nasıl Eklenir – Düğme Başlığını Ayarla
url: /tr/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de ActiveX Düğmesi Nasıl Ekleilir – Düğme Başlığını Ayarlama

Word dosyasına UI'yi açmadan **ActiveX** kontrollerini nasıl ekleyeceğinizi hiç merak ettiniz mi? Tek başınıza değilsiniz. Birçok kurumsal uygulamada bir makroyu çalıştıran tıklanabilir bir düğmeye ihtiyacınız var ve bunu programlı olarak yapmak saatler tasarruf sağlar. Bu rehber, Aspose.Words for Java kullanarak **ActiveX** CommandButton'ı nasıl ekleyeceğinizi ve—evet—kullanıcının neye tıklaması gerektiğini bilmesi için **düğme başlığını nasıl ayarlayacağınızı** tam olarak gösterir.

Kütüphaneyi kurmaktan yeni bir belge oluşturmaya, düğmeyi eklemeye, boyut ve konumunu ayarlamaya, dostça bir başlık vermeye ve nihayet dosyayı kaydetmeye kadar tüm süreci adım adım anlatacağız. Sonunda, Word'de açıldığında makronuzu çalıştırmaya hazır tam işlevsel bir ActiveX düğmesi içeren çalıştırılabilir bir `.docx` dosyanız olacak.

---

## Neler Öğreneceksiniz

- Java projesinde Aspose.Words'ü kurun ve referans verin.  
- Yeni bir `Document` ve `DocumentBuilder` oluşturun.  
- **ActiveX** CommandButton kontrolünü tek bir kod satırıyla ekleyin.  
- **Düğme başlığını ayarlayın**, konumunu ayarlayın ve boyutlarını tanımlayın.  
- Belgeyi kaydedin ve sonucu görmek için Word'de açın.

ActiveX konusunda önceden deneyim gerekmez; sadece temel Java bilgisi ve bir Aspose.Words kopyası yeterlidir.

---

## Gereksinimler

- Makinenizde Java 8 veya daha yeni bir sürüm yüklü.  
- Bağımlılık yönetimi için Maven veya Gradle (Maven örneğini göstereceğiz).  
- **Aspose.Words for Java**'ın lisanslı veya deneme sürümü (ücretsiz deneme bu demo için yeterli).  
- Oluşturulan dosyayı test etmek için Microsoft Word (herhangi bir güncel sürüm).

---

## Adım 1: Projenize Aspose.Words'ü Ekleyin

İlk iş olarak Aspose.Words bağımlılığını ekleyin. Maven kullanıyorsanız, bunu `pom.xml` dosyanıza ekleyin:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Gradle kullanıcıları şunu ekleyebilir:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Kısa bir `mvn clean install` (veya `gradle build`) işleminden sonra kütüphane sınıf yolunuza eklenecek ve kod yazmaya hazır olacaksınız.

---

## Adım 2: Yeni Bir Belge ve Builder Oluşturun

`Document`, tüm Word dosyasını temsil ederken `DocumentBuilder` onun üzerinde düzenleme yapmanızı sağlar. Builder'ı, yeni bir tuval üzerine çizen bir kalem gibi düşünün.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Neden boş bir belgeyle başlıyoruz? Eklediğiniz her öğe üzerinde tam kontrol sahibi olmanızı garantiler ve daha sonra karşınıza çıkabilecek gizli biçimlendirmelerle karşılaşmazsınız.

---

## Adım 3: ActiveX CommandButton Kontrolünü Ekleyin

Şimdi gösterinin yıldızı geliyor. Aspose.Words, belirttiğiniz herhangi bir ActiveX kontrolünü yerleştirebilen `insertForms2OleControl` metodunu sunar. Burada **CommandButton** istiyoruz.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Bu metod bir `Forms2OleControl` nesnesi döndürür ve düğmenin özelliklerine programlı erişim sağlar. İşte **how to insert activex**'in tek satırla yapılabildiği yer—düşük seviyeli COM API'leriyle uğraşmanıza gerek kalmaz.

---

## Adım 4: Konum, Boyut ve Düğme Başlığını Ayarlama

Sayfanın ortasında süzülen bir düğme pek işe yarar değildir. Kullanıcıların beklediği yere yerleştirmek, makul bir boyut vermek ve en önemlisi **düğme başlığını ayarlamak** gerekir; böylece tıklamanın ne işe yarayacağını bilirler.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Bu sayılar neden?** Word puan (point) birimini kullanır (1 pt ≈ 1/72 inç). `100 pt` ≈ sol kenardan 1.4 inç, `150 pt` ≈ üstten 2.1 inç—standart A4 sayfasının yaklaşık ortası. Düzeninize göre ayarlayın.

Başlığı ayarlamak çok önemlidir; aksi takdirde düğme boş bir dikdörtgen gibi görünür. `setCaption` metodu herhangi bir dizeyi kabul eder, böylece ihtiyacınız olursa daha sonra yerelleştirebilirsiniz.

---

## Adım 5: Belgeyi Kaydedin

Son olarak belgeyi diske yazın. İstediğiniz klasörü seçebilirsiniz; sadece yolun var olduğundan emin olun.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

`ActiveXButton.docx` dosyasını Word'de açtığınızda **“Click Me.”** etiketiyle güzel bir şekilde yerleştirilmiş bir düğme göreceksiniz. Çift tıkladığınızda Word, makroları etkinleştirmenizi isteyecek (çünkü ActiveX kontrolleri makro‑etkin olarak kabul edilir). Buradan düğmenin `Click` olayına bir VBA rutini bağlayabilirsiniz.

---

## Kaçırabileceğiniz Durumlar ve İpuçları

- **Macro‑Enabled Format**: Word, kullanıcı makroları etkinleştirmediği sürece düz `.docx` dosyalarındaki ActiveX kontrollerini devre dışı bırakır. Düğmenin kutudan çıktığı gibi çalışmasını istiyorsanız, `doc.save(outputPath, SaveFormat.DOCM);` kullanarak `.docm` (makro‑etkin) olarak kaydetmeyi düşünün.  
- **Compatibility**: Word'ün eski sürümleri (2007 öncesi) ikili `.doc` formatını kullanır. Aspose.Words bu formata kaydedebilir, ancak kontrolün özellikleri biraz farklı görünebilir.  
- **Security Settings**: Bazı kurumsal ortamlar ActiveX'i kısıtlar. Düğmeniz görünmüyorsa Word'ün Trust Center → ActiveX Settings bölümünü kontrol edin.  
- **Multiple Buttons**: Birden fazla düğme mi istiyorsunuz? `insertForms2OleControl` çağrısını tekrarlayın ve her düğmenin `Left`/`Top` değerlerini ayarlayın. Dönen nesneleri takip edin, böylece her birine ayrı başlık verebilirsiniz.  
- **Styling the Caption**: Başlık varsayılan yazı tipini devralır. Değiştirmek isterseniz, alttaki XML'i düzenlemeniz veya ekleme sonrası bir Word stili uygulamanız gerekir—bu hızlı rehberin kapsamı dışında, ancak Aspose.Words'ün `ParagraphFormat` API'siyle yapılabilir.

---

## Tam Çalışan Örnek

Aşağıda tamamen hazır, çalıştırılabilir bir Java sınıfı bulunmaktadır. IDE'nize kopyalayıp yapıştırın, çıktı yolunu ayarlayın ve **Run** tuşuna basın.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Beklenen çıktı**: Çalıştırdıktan sonra konsol kaydetme konumunu yazdırır. Oluşturulan dosyayı Word'de açtığınızda sayfanın ortasına doğru yerleştirilmiş, “Click Me” etiketiyle bir düğme görürsünüz. Tıkladığınızda standart ActiveX tıklama olayı tetiklenir (yanıt vermesi için bir VBA makrosu eklemeniz gerekir).

---

## Sonuç

Artık **ActiveX** CommandButton kontrollerini Aspose.Words ile programlı olarak bir Word belgesine nasıl ekleyeceğinizi ve **düğme başlığını nasıl ayarlayacağınızı**, konumunu ve boyutunu nasıl belirleyeceğinizi biliyorsunuz. Bu yaklaşım manuel UI işini ortadan kaldırır, otomatik rapor oluşturucularına sorunsuz bir şekilde entegre olur ve kontrol üzerinde tam kontrol sağlar.


## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert an Image into Word Document Header | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}