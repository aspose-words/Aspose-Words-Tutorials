---
category: general
date: 2026-07-16
description: Aspose.Words for Java kullanarak bir Word belgesinde programlı olarak
  düğme boyutunu ayarlayın. ActiveX düğmesi eklemeyi, düğme konumunu ayarlamayı ve
  daha fazlasını öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: tr
lastmod: 2026-07-16
og_description: Java kullanarak bir Word belgesinde düğme boyutunu ayarlayın. Bu adım
  adım kılavuz, ActiveX düğmesi eklemeyi, düğme konumunu ayarlamayı ve programlı olarak
  düğme eklemeyi gösterir.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Java ile Word'de Düğme Boyutunu Ayarlama – Tam Aspose.Words Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Java ile Word’de Düğme Boyutunu Ayarlama – Tam Aspose.Words Rehberi
url: /tr/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java ile Word'de Düğme Boyutunu Ayarlama – Tam Aspose.Words Rehberi

Word dosyası içinde UI'yi açmadan **set button size** nasıl yapılır diye hiç merak ettiniz mi? Tek başınıza değilsiniz. Anlık olarak form doldurulmuş bir belge oluşturmanız gerektiğinde—örneğin “Submit” düğmesi içeren bir işe alım paketi—bunu programlı olarak yapmak saatlerce manuel işi tasarruf ettirir.

Bu öğreticide **insert ActiveX button** adımlarını, boyutlarını ayarlamayı, doğru konumlandırmayı ve son olarak dosyayı kaydetmeyi adım adım göstereceğiz. Sonunda Aspose.Words for Java kullanarak herhangi bir Word belgesine **programmatically add button** kontrolleri ekleyebileceksiniz.

## Önkoşullar – Başlamadan Önce Neye İhtiyacınız Var

- **Java Development Kit (JDK) 8+** – kod herhangi bir yeni JDK'da çalışır.
- **Aspose.Words for Java** kütüphanesi (en son JAR'ı resmi siteden indirin).  
- Seçtiğiniz **IDE** — IntelliJ IDEA, Eclipse veya basit bir metin editörü de iş görür.
- Java sözdizimine temel aşinalık; derin Word‑otomasyon bilgisi gerekmez.

> *Pro tip:* Proje sınıf yolunda Aspose.Words JAR'ını tutun, aksi takdirde `com.aspose.words.*`'i içe aktarmaya çalıştığınız anda `ClassNotFoundException` alırsınız.

## Adım 1: Yeni bir Word Belgesi Oluşturma

İlk olarak boş bir belge ve bir `DocumentBuilder` oluştururuz. Builder'ı, dosyanın içinde istediğimiz her şeyi çizmeye yarayan bir kalem gibi düşünün.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Neden önemli:** `Document` nesnesi tüm .docx dosyasını temsil ederken, `DocumentBuilder` paragraf, tablo ve—evet—ActiveX kontrolleri eklememizi sağlayan iş gücüdür.

## Adım 2: ActiveX Düğmesi Ekleme – “Insert ActiveX Button” Anı

Şimdi belgeye gerçekten **insert activex button** ekliyoruz. Aspose.Words, `insertForms2OleControl` adlı kullanışlı bir yöntem sunar ve bu yöntem bir `Forms2OleControl` nesnesi döndürür.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *Arka planda ne oluyor?* `Forms2OleControlType.COMMAND_BUTTON` Word'e klasik bir CommandButton istediğimizi söyler; bu, UI'deki Geliştirici sekmesinden sürükleyebileceğiniz aynı türdür.

## Adım 3: Düğme Boyutunu ve Konumunu Ayarlama – Temel “Set Button Size” Mantığı

İşte anahtar kelimenin parladığı yer. **set button size** ve ayrıca **set button location** yapacağız, böylece kontrol sayfada tam istediğimiz yerde görünür.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Neden umursamalısınız:** Noktalar Word'ün yerel ölçü birimidir (1 point = 1/72 inç). `setLeft`, `setTop`, `setWidth` ve `setHeight`'i ayarlayarak piksel‑tam kontrol elde edersiniz—artık “ekranda doğru görünüyor ama yazıcıda değil” sorunu yok.

> *Yaygın tuzak:* Genişlik ya da yüksekliği ayarlamayı unutmak, düğmeyi varsayılan boyutta bırakır ve bu tıklamak için çok küçük olabilir. Her zaman ikisini de belirtin.

## Adım 4: Belgeyi Kaydetme – “Create Word Document Button” Tamamlandı

Son olarak dosyayı diske yazarız. İsim, .docx içinde **creating a Word document button** oluşturduğumuzu ima eder.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Microsoft Word'de `CommandButtonDemo.docx` dosyasını açtığınızda, sol kenardan 100 pt, üstten 150 pt uzaklıkta yer alan ve 80 × 30 pt boyutunda bir **Submit** düğmesi göreceksiniz. UI'de tıkladığınızda varsayılan ActiveX davranışı tetiklenir (gerekirse daha sonra VBA ile bağlayabilirsiniz).

### Beklenen Çıktı Ekran Görüntüsü

![Word belgesinde eklenen düğme ve ayarlanan düğme boyutu gösteriliyor](https://example.com/images/set-button-size.png "Aspose.Words for Java kullanılarak düğme boyutu ayarlanmış bir Word dosyasının ekran görüntüsü")

*Alt metin:* Java kullanarak bir Word belgesinde düğme boyutunu ayarlama

## Adım 5 (İsteğe Bağlı): Daha Fazla Kontrol Ekleme veya Düğmeyi Stilize Etme

Eğer tek bir Submit düğmesinin ötesinde **programmatically add button** kontrolleri eklemeniz gerekiyorsa, yeni adlar ve başlıklarla ekleme bloğunu tekrarlamanız yeterlidir. Ayrıca yazı tipini, arka plan rengini ayarlayabilir veya daha sonra VBA makrolarını bağlayabilirsiniz.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *İpucu:* Profesyonel bir görünüm için tüm düğme boyutlarını tutarlı tutun. Hızlı bir yol, genişlik/yüksekliği sabitlerde saklamaktır.

## Sık Sorulan Sorular & Kenar Durumları

### “Düğme boyutunu nokta yerine santimetre ile ayarlayabilir miyim?”

Word API'si yalnızca nokta birimini kabul eder, ancak santimetreyi noktalara dönüştürebilirsiniz (`points = cm * 28.3465`). Metriği tercih ederseniz küçük bir yardımcı yöntem yazın.

### “Düğmenin belirli bir sayfada görünmesini istesem ne olur?”

Düğmeyi ekledikten sonra, `builder.moveToPage(pageNumber)` kullanarak imleci belirli bir sayfaya taşıyabilirsiniz. Kontrolü taşımanın hemen ardından ekleyin, ardından konumunu yukarıda gösterildiği gibi ayarlayın.

### “.doc (Word 97‑2003) dosyalarıyla çalışır mı?”

Evet—Aspose.Words otomatik olarak eski formatları işler. Sadece `doc.save("Demo.doc")` içinde dosya uzantısını değiştirin.

## Tam, Çalıştırılabilir Örnek

Aşağıda, Aspose.Words JAR'ının sınıf yolunda olduğu varsayılarak, bir Java sınıfına kopyalayıp hemen çalıştırabileceğiniz tam program yer almaktadır.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Programı çalıştırın, oluşturulan `CommandButtonDemo.docx` dosyasını açın ve iki düzgün boyutlandırılmış düğmenin etkileşim için hazır olduğunu göreceksiniz.

## Sonuç – Word'de Düğme Boyutunu Ayarlamayı Öğrendiniz

Az önce Aspose.Words for Java kullanarak **set button size** ve **set button location** için tam, uçtan uca bir çözüm üzerinden geçtik. Adımları izleyerek **insert activex button**, **programmatically add button** kontrolleri ekleyebilir ve nihayetinde **create word document button** öğelerini tam ihtiyacınıza göre davranacak şekilde oluşturabilirsiniz.

Sonraki adım ne? Düğmeyi bir tablo hücresine yerleştirmeyi deneyin veya gönderimden önce form alanlarını doğrulayan bir VBA makrosu ekleyin. Aynı desen, onay kutuları veya açılır kutular gibi diğer ActiveX kontrolleri için de çalışır—sadece `Forms2OleControlType.COMMAND_BUTTON`'ı uygun enum değeriyle değiştirin.

Herhangi bir sorunla karşılaşırsanız, aşağıya yorum bırakın. Kodlamaktan keyif alın ve otomatik Word belgesi oluşturmanın gücünün tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words for Java'da LoadOptions Nasıl Ayarlanır](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words for Java kullanarak Word belgelerinden altbilgileri nasıl kaldırılır](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java: Word Belge İşleme İçin Kapsamlı Rehber](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}