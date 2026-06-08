---
category: general
date: 2026-06-08
description: Aspose.Words for Python kullanarak şekle gölge ekleyin ve sadece birkaç
  adımda şekil dolgu rengini ayarlayın. Çalıştırılabilir kodla tam iş akışını öğrenin.
draft: false
keywords:
- add shadow to shape
- set shape fill color
- Aspose.Words Python shadow
- shape formatting Python
- PDF generation Aspose
language: tr
og_description: Aspose.Words for Python ile şekle gölge ekleyin ve şekil dolgu rengini
  anında ayarlayın. PDF çıktısı oluşturmak için bu adım adım öğreticiyi izleyin.
og_title: Python'da Şekle Gölge Ekle – Tam Aspose.Words Rehberi
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  headline: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  name: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  steps:
  - name: Create the Document and Builder
    text: '```python import aspose.words as aw from aspose.words.drawing import ShadowEffect,
      ShadowType, Color'
  - name: Insert a Rectangle Shape and Set Its Fill Color
    text: '```python # Insert a rectangle shape of width 200 points and height 100
      points. rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE,
      200, 100)'
  - name: Define the Shadow Effect
    text: '```python # Create a new shadow effect object. shape_shadow = ShadowEffect()
      shape_shadow.type = ShadowType.OUTER # outer shadow around the shape shape_shadow.blur_radius
      = 10.0 # softer edges shape_shadow.distance = 5.0 # how far the shadow sits
      from the shape shape_shadow.direction = 45 # angle in'
  - name: Apply the Shadow to the Shape
    text: '```python # Attach the shadow effect to the rectangle. rectangle_shape.shadow_effect
      = shape_shadow ```'
  - name: Save the Document as PDF
    text: '```python # Choose a folder you have write access to. output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
      doc.save(output_path) print(f"Document saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Python'da Şekle Gölge Ekle – Tam Aspose.Words Öğreticisi
url: /tr/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python’da Şekle Gölge Ekle – Tam Aspose.Words Öğreticisi

Aspose.Words for Python ile bir belge oluştururken **şekle gölge eklemeyi** hiç merak ettiniz mi? Tek başınıza değilsiniz. Bir rapor şablonu, bir pazarlama broşürü ya da teknik bir diyagram oluşturuyor olun, ince bir gölge bir dikdörtgeni öne çıkarır ve daha profesyonel görünmesini sağlar.  

Bu rehberde ayrıca **şeklin dolgu rengini ayarlamayı** da göstereceğiz, böylece PDF dışa aktarımı için tamamen stilize bir dikdörtgen elde edersiniz. Çözüm basit, kod çalıştırmaya hazır ve her satırın mantığı sade bir İngilizce ile açıklanıyor.

## Bu Öğreticide Neler Ele Alınıyor

- Aspose.Words belgesi ve builder’ının başlatılması.  
- Bir dikdörtgen şekli eklenmesi ve **dolgu renginin ayarlanması**.  
- Bu şekle **gölge efekti** tanımlanması ve uygulanması.  
- Sonucun PDF olarak kaydedilmesi.  
- Tam, çalıştırılabilir örnek ve yaygın hatalar için ipuçları.

Makalenin sonunda sadece birkaç Python satırıyla herhangi bir Word ya da PDF dosyasına stilize bir dikdörtgen ekleyebileceksiniz. Harici araçlar, tahmin yürütme yok.

> **Önkoşullar** – Python 3.7+ ve `aspose-words` paketi (`pip install aspose-words`) gerekir. Tercih ettiğiniz bir IDE ya da metin editörü yeterli; Visual Studio Code harika çalışır.

---

## Şekle Gölge Ekle – Adım Adım

Aşağıda süreci mantıksal parçalara ayırıyoruz. Her adım, ihtiyacınız olan tam kodu, *neden* önemli olduğunu kısa bir açıklama ve ileride takılmamanız için bir ipucu içerir.

### Adım 1: Belge ve Builder Oluşturma

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# Create a new, empty document.
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add content.
builder = aw.DocumentBuilder(doc)
```

**Neden önemli:** `Document` her şeyin—sayfalar, stiller, görseller ve şekiller—kapsayıcısıdır. `DocumentBuilder` ise düşük seviyeli düğüm ağaçlarıyla uğraşmadan nesneleri yerleştirmemizi sağlayan yüksek seviyeli API’dir.

### Adım 2: Dikdörtgen Şekli Ekleme ve Dolgu Rengini Ayarlama

```python
# Insert a rectangle shape of width 200 points and height 100 points.
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Set the interior color of the shape.
rectangle_shape.fill_color = Color.BLUE   # <-- set shape fill color
```

**Neden önemli:** Şekil, gölgemiz için bir tuval görevi görür. **Şeklin dolgu rengini ayarlayarak** dikdörtgenin sadece şeffaf bir kutu olmadığından, gölgenin vurgulayabileceği görünür bir öğe olmasını sağlarız. `Color.BLUE` yerine istediğiniz herhangi bir RGB değeri ya da daha fazla şıklık isterseniz bir degrade kullanabilirsiniz.

> **Pro ipucu:** Aynı rengi birçok şekil için tekrar kullanacaksanız, bir değişkende saklayın (`my_fill = Color.from_argb(0, 120, 200, 255)`) ve bu referansı yeniden kullanın.

### Adım 3: Gölge Efektini Tanımlama

```python
# Create a new shadow effect object.
shape_shadow = ShadowEffect()
shape_shadow.type = ShadowType.OUTER          # outer shadow around the shape
shape_shadow.blur_radius = 10.0               # softer edges
shape_shadow.distance = 5.0                   # how far the shadow sits from the shape
shape_shadow.direction = 45                   # angle in degrees (45° = diagonal)
shape_shadow.color = Color.from_argb(128, 0, 0, 0)  # semi‑transparent black
```

**Neden önemli:** Gölge sadece görsel bir süs değil; derinlik ve hiyerarşi aktarır. `blur_radius` yumuşaklığı, `distance` kaydırmayı, `direction` ise ışık kaynağını simüle eder. Bu değerleri tasarım dilinize göre ayarlayın.

### Adım 4: Gölgeyi Şekle Uygulama

```python
# Attach the shadow effect to the rectangle.
rectangle_shape.shadow_effect = shape_shadow
```

**Neden önemli:** Bu satır çalışana kadar şekil düz kalır. `shadow_effect` ataması, Aspose.Words’e belge kaydedildiğinde tanımlı gölgeyle dikdörtgeni render etmesini söyler.

### Adım 5: Belgeyi PDF Olarak Kaydetme

```python
# Choose a folder you have write access to.
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

**Neden önemli:** PDF olarak kaydetmek görsel stilleri kilitler, gölgenin tasarladığınız gibi görünmesini sağlar. Daha sonra düzenleme ihtiyacınız olursa `.docx` olarak da kaydedebilirsiniz—Aspose.Words her iki formatı da sorunsuz yönetir.

---

## Şekil Dolgu Rengini Ayarlama – Görünümü Özelleştirme

Farklı bir ton istiyorsanız, `Color.BLUE` atamasını aşağıdaki örneklerden biriyle değiştirin:

```python
# Solid RGB color
rectangle_shape.fill_color = Color.from_argb(255, 255, 165, 0)   # orange

# Semi‑transparent fill
rectangle_shape.fill_color = Color.from_argb(128, 0, 128, 0)    # 50% transparent green
```

> **Neden isteyebilirsiniz:** Yarı şeffaf bir dolgu ve gölge, modern UI mock‑up’larında popüler bir “cam” efekti yaratabilir.

---

## Tam Çalışan Örnek

İşte tüm betiği tek bir blokta. `shadow_shape.py` adlı bir dosyaya kopyalayıp yapıştırın ve çalıştırın—`aspose-words` kurulu olduğu varsayımıyla.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# 1️⃣ Create document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert rectangle and set fill color
rect = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rect.fill_color = Color.BLUE          # set shape fill color

# 3️⃣ Configure shadow
shadow = ShadowEffect()
shadow.type = ShadowType.OUTER
shadow.blur_radius = 10.0
shadow.distance = 5.0
shadow.direction = 45
shadow.color = Color.from_argb(128, 0, 0, 0)

# 4️⃣ Apply shadow
rect.shadow_effect = shadow

# 5️⃣ Save as PDF
output = "ShadowShape.pdf"
doc.save(output)
print(f"✅ PDF generated: {output}")
```

**Beklenen çıktı:** `ShadowShape.pdf` dosyasını açtığınızda, sağ‑alt köşeye doğru hafifçe kaydırılmış, yumuşak bir siyah gölgeye sahip mavi bir dikdörtgen göreceksiniz. Gölge hafif bulanık olacak ve şekle kaldırılmış bir görünüm kazandıracak.

---

## Yaygın Hatalar & Pro İpuçları

| Sorun | Neden Oluşur | Çözüm |
|------|----------------|-----|
| **Gölge görünmüyor** | Şeklin dolgu rengi tamamen şeffaf ya da PDF görüntüleyici gölgeleri devre dışı bırakmış. | `fill_color` opak olduğundan emin olun (`alpha = 255`) veya gölgenin `color` opaklığını ayarlayın. |
| **Dosya yolu hatası** | `YOUR_DIRECTORY` mevcut değil ya da yazma izniniz yok. | `os.makedirs("YOUR_DIRECTORY", exist_ok=True)` kodunu `doc.save` öncesinde ekleyin. |
| **Yanlış import** | `ShadowEffect`'i yanlış alt‑modülden içe aktarmaya çalışmak. | Tam olarak gösterildiği gibi içe aktarın: `from aspose.words.drawing import ShadowEffect, ShadowType, Color`. |
| **Beklenmeyen renk** | `Color.from_argb`'i hatalı sırayla (alpha, kırmızı, yeşil, mavi) kullanmak. | Sıralamayı hatırlayın: **alpha**, **red**, **green**, **blue**. |

---

## Sonraki Adımlar – Şekil Araç Setinizi Genişletin

Artık **şekle gölge eklemeyi** ve **şekil dolgu rengini ayarlamayı** bildiğinize göre şu konuları keşfedebilirsiniz:

- **Gradyan dolgular** (`LinearGradientBrush`) ile daha zengin arka planlar.  
- **Birden fazla gölge** (iç + dış) `ShadowEffect` nesnelerini zincirleyerek.  
- **Diğer şekil tipleri** (`Ellipse`, `Polygon`) ile ikonlar ya da akış diyagramı öğeleri oluşturma.  
- **PDF’yi** Flask ya da Django kullanarak bir web yanıtına ya da e‑posta ekine gömme.

Bu konular, burada ele alınan temel kavramlar üzerine inşa edildiği için kendinizi rahat hissedeceksiniz.

---

## Sonuç

Aspose.Words for Python’da **şekle gölge ekleme** ve **şekil dolgu rengini ayarlama** sürecini baştan sona yürüttük. Belge oluşturulmasından PDF dışa aktarımına kadar kod kendi içinde tutarlı ve üretim ortamına hazır.  

Bulanıklık yarıçapını, mesafeyi ya da rengi marka yönergelerinize göre ayarlamaktan çekinmeyin. Bir kenar durumuyla karşılaşırsanız ya da yeni bir özellik talebiniz olursa, aşağıya yorum bırakın—mutlu kodlamalar!

## Bir Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve ilgili konuları derinlemesine ele alan kaynaklardır. Her biri adım adım açıklamalar ve tam çalışan kod örnekleri içerir, böylece ek API özelliklerini öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Set Up Aspose.Words License in Python](/words/english/python-net/getting-started/aspose-words-license-python-setup/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}