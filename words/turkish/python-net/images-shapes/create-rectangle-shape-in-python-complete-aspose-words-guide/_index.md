---
category: general
date: 2026-06-24
description: Aspose.Words ile Python’da dikdörtgen şekil oluşturun, şekle gölge eklemeyi,
  gölge açısını ayarlamayı öğrenin ve belgeyi dakikalar içinde PDF olarak kaydedin.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: tr
og_description: Python'da dikdörtgen şekli oluşturun, şekle gölge ekleyin, gölge açısını
  ayarlayın ve belgeyi Aspose.Words ile PDF olarak kaydedin. Bu adım adım kılavuzu
  izleyin.
og_title: Python'da Dikdörtgen Şekli Oluşturma – Tam Aspose.Words Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Python'da Dikdörtgen Şekil Oluşturma – Tam Aspose.Words Rehberi
url: /tr/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python’da Dikdörtgen Şekli Oluşturma – Tam Aspose.Words Rehberi

Word belgesinde **dikdörtgen şekil** oluşturmayı hiç merak ettiniz mi? Belki kalın bir açıklama kutusuna, bir diyagram için görsel bir işarete ya da sadece rapor için şık bir dikdörtgene ihtiyacınız var. Hangi durumda olursanız olun, doğru yerdesiniz. Bu öğreticide, dikdörtgeni eklemek, hafif bir gölge eklemek, gölge açısını ayarlamak ve sonunda **belgeyi PDF olarak kaydetmek** sürecini adım adım inceleyeceğiz.

**Aspose.Words for Python via .NET** kullanacağız; bu güçlü kütüphane, Word dosyalarını Word programını açmadan manipüle etmenizi sağlıyor. Bu rehberin sonunda, *“şekle gölge nasıl eklenir”* sorusuna güvenle cevap verebilecek ve herhangi bir projeye ekleyebileceğiniz çalışır bir betiğe sahip olacaksınız.

---

## Gereksinimler

İlerlemeye başlamadan önce aşağıdakilerin kurulu olduğundan emin olun:

- **Python 3.8+** yüklü olmalı.  
- **Aspose.Words for Python via .NET** (`aspose-words` paketi). Şu komutla kurun:

  ```bash
  pip install aspose-words
  ```

- Oluşturulan PDF’nin kaydedileceği yazılabilir bir klasör.  
- (İsteğe bağlı) Bir IDE ya da metin düzenleyici — VS Code gayet uygundur.

Hepsi bu. Ek DLL’lere, Office kurulumuna ya da başka bir şeye gerek yok, sadece tek bir pip paketi.

---

## 1. Adım: Belge ve Builder’ı Hazırlama

İlk yapmanız gereken, **dikdörtgen şekil** oluşturmayı destekleyecek nesneleri yaratmak: bir `Document` ve bir `DocumentBuilder`. Builder, kaleminiz gibi; sizin için her şeyi çizer.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Neden önemli:** `Document` nesnesi tüm .docx dosyasını temsil ederken, `DocumentBuilder` `insert_shape` gibi şekil çizimini kolaylaştıran metodları sağlar.

---

## 2. Adım: Dikdörtgen Şekli Ekleme

Builder’ımız olduğuna göre, nihayet **dikdörtgen şekil** oluşturabiliriz. `insert_shape` metodunun üç parametresi vardır: şekil tipi, genişlik ve yükseklik. Orantılı bir görünüm için 200 pt genişlik ve 100 pt yükseklik kullanacağız.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Bu aşamada belgeye **dikdörtgen şekil** başarıyla eklenmiş olur. Daha sonra oluşturulan DOCX’i (daha sonra açacağız) açtığınızda, imlecin bulunduğu yerde sade bir dikdörtgen göreceksiniz.

---

## 3. Adım: Gölge Biçimlendirme Nesnesine Erişim

**Şekle gölge eklemek** için önce şeklin gölge biçimlendirme nesnesini almamız gerekir. Aspose.Words’ta her şeklin `shadow_format` adlı bir özelliği vardır ve bu özellik gölgeyle ilgili tüm ayarları ortaya çıkarır.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

`shadow` referansına sahip olmak, görünürlük, bulanıklık, mesafe, açı, renk ve şeffaflık gibi ayarları sadece birkaç satır kodla değiştirmemizi sağlar.

---

## 4. Adım: Gölgeyi Etkinleştir ve Görünümünü Ayarla

İşte sihrin gerçekleştiği kısım. **Şekle gölge ekleyecek**, hafifçe bulanıklaştıracak, biraz kaydıracak, yönünü (**gölge açısını ayarla**) belirleyecek ve yarı saydam siyah bir ton vereceğiz.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Pro ipucu:** Daha dramatik bir etki isterseniz `blur_radius` değerini artırın ya da `transparency` değerini düşürün. Tamamen opak ve keskin bir gölge için `blur_radius = 0` ve `transparency = 0` kullanabilirsiniz.

---

## 5. Adım: Belgeyi PDF Olarak Kaydetme

**Dikdörtgen şekil** oluşturduk, **şekle gölge ekledik**, şimdi de **belgeyi PDF olarak kaydedelim** ki sonuç her cihazda aynı görünsün. Aspose.Words bu işlemi tek satırda halleder.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Betik çalıştırıldığında `output` klasöründe `shadowed_rectangle.pdf` dosyası oluşur. Herhangi bir PDF görüntüleyicide açtığınızda, 45 derecelik yumuşak bir gölgeye sahip temiz bir dikdörtgen göreceksiniz — tam da yapılandırdığımız gibi.

---

## Tam Çalışan Örnek

Aşağıda, yukarıdaki tüm adımları birleştiren eksiksiz, çalıştırmaya hazır bir betik bulunuyor. `create_rectangle_with_shadow.py` adıyla bir dosyaya kopyalayıp `python create_rectangle_with_shadow.py` komutuyla çalıştırın.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Beklenen çıktı:** Tek bir dikdörtgen ve hafif, diyagonal bir gölge gösteren bir PDF dosyası. Fazladan sayfa, gizli artefakt yok — sadece oluşturduğumuz şekil.

---

## Sık Sorulan Sorular & Özel Durumlar

### Farklı bir şekle ihtiyacım olursa ne yapmalıyım?

Aspose.Words birçok `ShapeType` değerini destekler (elips, yıldız, çağrı kutusu vb.). `aw.drawing.ShapeType.RECTANGLE` ifadesini istediğiniz enum ile değiştirmeniz yeterlidir; örneğin `aw.drawing.ShapeType.ELLIPSE`.

### Birden fazla gölge ekleyebilir miyim?

API, her şekil için yalnızca bir `ShadowFormat` sunar, ancak şekli çoğaltıp her kopyayı farklı konumlandırıp şeffaflık ayarlarını değiştirerek birden fazla gölge etkisi taklit edebilirsiniz.

### Gölge rengini markamın rengine göre nasıl ayarlarım?

`shadow.color` özelliğine istediğiniz `aw.drawing.Color` değerini atayın. Örneğin marka mavisi için `aw.drawing.Color.from_argb(255, 0, 120, 215)` kullanabilirsiniz.

### PDF yerine DOCX olarak kaydetmek istersem?

`document.save(pdf_path)` satırını `document.save("output/shadowed_rectangle.docx")` ile değiştirin. Gölge renderlaması her iki formatta da korunur.

### Gölge eski PDF görüntüleyicilerde çalışır mı?

Aspose.Words gölgeyi vektörel bir efekt olarak renderlar ve bu geniş bir destek alır. Ancak çok eski görüntüleyiciler efekti düzleştirebilir; hedef kitlenizin cihazlarında test etmek her zaman iyi bir alışkanlıktır.

---

## PDF’nizi Parlatmak İçin İpuçları

- **Kenarlık ekleyin:** `rectangle.line_format.width = 1.5` ve bir renk belirleyerek net bir çerçeve oluşturun.  
- **Dikdörtgeni ortalayın:** Şekli eklemeden önce `builder.move_to_document_start()` çağırın, ardından `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER` ayarlayın.  
- **Metinle birleştirin:** Dikdörtgenin ardından bir `TextFragment` ekleyerek etiketleyin, örneğin `"Önemli Bölüm"`.

Bu küçük dokunuşlar, basit bir dikdörtgeni rapor, teklif ya da e‑kitaplarda profesyonel bir çağrı kutusuna dönüştürebilir.

---

## Sonuç

Artık Python’da **dikdörtgen şekil** oluşturma, **şekle gölge ekleme**, **gölge açısını ayarlama** ve **belgeyi PDF olarak kaydetme** konularında eksiksiz bir tarifiniz var ve Aspose.Words ile bunu nasıl yapacağınızı biliyorsunuz. Adımlar basit, kod tamamen bağımsız ve her satırın neden önemli olduğunu gördünüz — belgeyi başlatmaktan son PDF’yi cilalamaya kadar.

Bir sonraki adımda, **şekle gölge ekleme** konusunu daha karmaşık çizimlere uygulamayı, degrade doldurmaları denemeyi ya da şekiller içinde tablolar üretmeyi keşfedebilirsiniz. Kütüphane ayrıca şekilleri yer imlerine bağlamayı destekler; bu da etkileşimli PDF’ler için kullanışlıdır.

Denediğiniz bir varyasyon var mı? Yorumlarda paylaşın ya da aklınıza takılan soruları sorun. İyi kodlamalar ve belgelerinize ekstra derinlik katmanın tadını çıkarın!

![Rectangle shape with shadow – example of create rectangle shape in Python](/images/rectangle-shadow.png)


## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakın konuları ele alır. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}