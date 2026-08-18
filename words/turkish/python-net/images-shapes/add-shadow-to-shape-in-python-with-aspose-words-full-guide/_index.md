---
category: general
date: 2026-06-30
description: Aspose.Words for Python kullanarak şekle gölge ekleyin. Gölge mesafesini
  nasıl ayarlayacağınızı, bulanıklığı nasıl özelleştireceğinizi öğrenin ve şekil gölgesiyle
  bir PDF'yi hızlıca kaydedin.
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: tr
og_description: Aspose.Words for Python ile bir Word belgesindeki şekle gölge ekleyin.
  Bu öğreticide gölge mesafesini, bulanıklığını ve rengini nasıl ayarlayacağınız ve
  ardından PDF olarak kaydedeceğiniz gösterilmektedir.
og_title: Python'da Şekle Gölge Ekle – Tam Aspose.Words Rehberi
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Aspose.Words ile Python'da Şekle Gölge Ekle – Tam Rehber
url: /tr/python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python'da Aspose.Words ile Şekle Gölge Ekle – Tam Kılavuz

Aspose.Words for Python kullanarak bir Word belgesine şekle gölge eklemek düşündüğünüzden çok daha kolay. **gölge mesafesini nasıl ayarlayacağınızı** ya da **şekle gölge nasıl ekleyeceğinizi** merak ettiyseniz, bu kılavuz tam size göre.

Önümüzdeki birkaç dakikada, yeni bir belge oluşturma, bir dikdörtgen ekleme, gölge özelliklerini ayarlama ve sonunda efekti gösteren bir PDF kaydetme sürecini adım adım inceleyeceğiz. Sonunda, dikdörtgen, elips ya da özel bir çizim gibi herhangi bir şekle gölge ekleyebileceksiniz; API belgelerini karıştırmanıza gerek kalmayacak.

> **Önkoşullar** – Python 3.7+ yüklü olmalı, bir Aspose.Words for Python lisansınız (veya ücretsiz deneme sürümünüz) olmalı ve Python betikleme konusunda temel bir bilginiz olmalı. Başka bir dış kütüphane gerekmiyor.

---

## Şekle Gölge Ekle – Adım Adım Genel Bakış

Aşağıda gerçekleştireceklerimizin hızlı bir yol haritası bulunuyor:

1. **Yeni bir belge** ve onu düzenlemek için bir `DocumentBuilder` oluşturun.  
2. **İhtiyacınız olan boyutta bir dikdörtgen şekli** ekleyin.  
3. **Gölgeyi etkinleştirip özelleştirin** – işte anahtar kelimenin parladığı yer.  
4. **Belgeyi** gölgesiyle birlikte PDF olarak kaydedin.

Her adım kendi bölümünde ele alınmıştır, böylece kod parçacıklarını doğrudan IDE’nize kopyalayıp yapıştırabilirsiniz.

---

## Adım 1: Belge ve Builder'ı Başlatma

İlk iş, bir `Document` olmadan çalışacak bir şeyiniz olmaz. `DocumentBuilder` ise sizin fırçanızdır.

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*Neden önemli*: `Document` nesnesi tüm dosyayı temsil ederken, `DocumentBuilder` metin, tablo ve şekil eklemeyi basitleştirir. Builder'ı, sayfa üzerinde hareket ettirebileceğiniz bir imleç gibi düşünün.

---

## Adım 2: Dikdörtgen Şekil Ekleme

Şimdi gölge etkisi için bir kanvas olan dikdörtgeni ekleyeceğiz. Farklı bir geometriye ihtiyacınız varsa `RECTANGLE` yerine `ELLIPSE`, `STAR` ya da başka bir `ShapeType` kullanabilirsiniz.

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*İpucu*: Boyutlar puan cinsindendir (1 pt ≈ 1/72 inç). Düzeninize göre ayarlayın; gölge otomatik olarak ölçeklenecektir.

---

## Gölge Mesafesini Nasıl Ayarlarım

Gölgenin **mesafesi**, gölgenin şekilden ne kadar uzakta görüneceğini belirler. Daha büyük bir mesafe, ışık kaynağının daha uzakta olduğunu taklit ederken, daha küçük bir değer hafif bir yükselme sağlar.

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **Not**: Mesafe, `angle` ile birlikte çalışır. Açıyı değiştirerek gölgeyi şeklin etrafında döndürebilir, `distance` ile de dışa doğru itebilirsiniz.

---

## Şekle Gölge Ekle – Bulanıklık, Renk ve Açıyı Özelleştirme

Gölge eklemek sadece açma tuşuna basmak değildir; gerçekçi bir etki için genellikle bulanıklık, renk ve yön ayarlarını da yapmanız gerekir.

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*Bu ayarlar neden?*  
- **Blur radius** (bulanıklık yarıçapı) kenarı yumuşatarak sert bir silüet oluşmasını engeller.  
- **Angle** (açı) ışık kaynağını simüle eder; 45° genellikle dengeli bir varsayılan değerdir.  
- **Color** (renk) herhangi bir `Color` nesnesi olabilir; daha yumuşak bir etki için `Color.gray` deneyin.

---

## Adım 4: Belgeyi PDF Olarak Kaydetme

Şekil ve gölgesi hazır olduğunda, sonucu saklamak çok basittir. Aspose.Words, PDF’e dönüşümü otomatik olarak yapar ve görsel bütünlüğü korur.

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*Beklenen çıktı*: Oluşturulan `ShadowShape.pdf` dosyasını açın. 200 × 100 pt boyutunda bir dikdörtgen, 45° açıyla 4 pt uzakta ve 5 pt bulanıklıkta bir gölge göreceksiniz. Gölge, şekli hafifçe saran gri‑siyah bir halo gibi görünmelidir.

---

## Yaygın Sorular & Kenar Durumları

### Farklı bir şekle ihtiyacım olursa ne yapmalıyım?

`aw.drawing.ShapeType.RECTANGLE` ifadesini başka bir enum değeriyle, örneğin `aw.drawing.ShapeType.ELLIPSE` ile değiştirin. Aynı gölge özellikleri geçerli olur—ekstra kod gerekmez.

### Birden fazla şekle aynı anda gölge uygulayabilir miyim?

Evet. Oluşturduğunuz şekiller üzerinde döngü kurup her birinin `shadow_format` özelliğini ayrı ayrı yapılandırabilirsiniz. İşte hızlı bir örnek:

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### Gölgenin opaklığını nasıl değiştiririm?

`shadow.transparency` özelliğini kullanın (0 = opak, 1 = tamamen şeffaf):

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## Tam Çalışan Örnek

Aşağıda eksiksiz bir betik bulunuyor—kopyalayın, çıktı klasörünü ayarlayın ve çalıştırın. Hiçbir parça eksik değil.

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

Betik çalıştırıldıktan sonra oluşan PDF’i açın. Dikdörtgenin net, kaydırılmış bir gölgesi olacak—tam da **add shadow to shape** (şekle gölge ekleme) vaadi gibi.

---

## Sonuç

Aspose.Words for Python kullanarak bir Word belgesine **şekle gölge ekleme** işlemini, **gölge mesafesini ayarlama**, bulanıklık, açı ve renk özelleştirme adımlarını ve son olarak efekti koruyan bir PDF dışa aktarma sürecini gösterdik. Bu teknik, herhangi bir şekil türü için çalışır ve döngüler, opaklık ayarları ya da hatta degrade gölgeler gibi eklemelerle genişletilebilir.

Bir sonraki meydan okumaya hazır mısınız? Birden fazla gölgeyi birleştirme, şekilleri katmanlama ya da her grafiğin kendi stilize gölgesi olduğu bir rapor üretme gibi konuları deneyin. Deneyim, kavramları pekiştirecek ve belge otomasyonu için yeni olasılıkları ortaya çıkaracaktır.

Bu kılavuzu faydalı bulduysanız, paylaşın, Aspose.Words deposunu yıldızlayın ya da kendi gölge ayarları ipuçlarınızı yorum olarak bırakın. Kodlamanın tadını çıkarın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}