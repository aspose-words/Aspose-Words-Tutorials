---
category: general
date: 2026-05-30
description: Aspose kullanarak Word'e dikdörtgen ekleme ve gölge ekleme – şekil gölge
  etkisiyle bir Word belgesi oluşturmak için adım adım Python rehberi.
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: tr
og_description: Aspose kullanarak Word'e dikdörtgen ekleme ve gölge ekleme – Python'da
  şekil gölgesi efektiyle bir Word belgesi oluşturmayı öğrenin.
og_title: Aspose kullanarak Word'de dikdörtgen ekleme ve gölge ekleme
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Aspose kullanarak Word'de dikdörtgen ekleme ve gölge ekleme
url: /tr/python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Aspose Kullanarak Dikdörtgen Ekleme ve Gölge Ekleme

Hiç **how to insert rectangle** bir Word dosyasına UI'ı açmadan eklemenin nasıl olduğunu merak ettiniz mi? Tek değilsiniz. Birçok geliştirici, raporlar, faturalar veya sertifikaları anında oluşturmak zorunda ve basit bir dikdörtgeni hoş bir gölgeyle çizmek, çıktının daha profesyonel görünmesini sağlar. Bu öğreticide, bir Word belgesi oluşturma, bir dikdörtgen şekli ekleme ve Aspose.Words for Python kullanarak gerçekçi bir gölge uygulama adımlarını adım adım göstereceğiz.

Aspose paketinin kurulumundan gölgenin mesafesi, bulanıklığı ve opaklığını ayarlamaya kadar her şeyi ele alacağız. Sonunda, herhangi bir otomasyon hattına ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığına sahip olacaksınız. Sihir yok, sadece net kod ve birkaç pratik ipucu.

## Prerequisites

İlerlemeye başlamadan önce şunların yüklü olduğundan emin olun:

- Python 3.8+ (kod 3.9, 3.10 ve daha yeni sürümlerde çalışır)
- Aktif bir Aspose.Words for Python lisansı veya ücretsiz bir değerlendirme anahtarı
- `aspose-words` paketi (`pip install aspose-words` ile kurulur)
- Oluşturulan **create word document aspose** dosyasının kaydedileceği yazılabilir bir klasör

Hepsi bu—ekstra DLL gerekmez, COM interop yok, sadece saf Python.

## Step 1: Initialize the Document (How to create word document aspose)

İlk iş: yeni bir `Document` nesnesi oluşturmanız gerekir. Bunu boş bir tuval gibi düşünün. Aşağıdaki kod belgeyi ve şekil eklememizi sağlayacak bir `DocumentBuilder` oluşturur.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

*Why this matters:* `DocumentBuilder`, paragraflar, tablolar ve—evet—şekiller eklemek için yüksek seviyeli bir API sunar, düşük seviyeli düğüm ağaçlarıyla uğraşmanıza gerek kalmaz. Builder'ı atlayıp düğümleri doğrudan manipüle ederseniz, bakımı zor, çok satırlı bir kodla karşılaşırsınız.

## Step 2: Insert the Rectangle (how to insert rectangle)

Şimdi gerçekten **how to insert rectangle** ekliyoruz. Aspose.Words bir dikdörtgeni genel bir şekil türü olarak ele alır. Genişlik ve yüksekliği puan cinsinden belirtirsiniz (1 puan ≈ 1/72 inç). Düzeninize uygun olacak şekilde sayıları istediğiniz gibi ayarlayabilirsiniz.

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **Pro tip:** Dikdörtgeni sayfada belirli bir konuma yerleştirmeniz gerekiyorsa, eklemeden sonra `shape.left` ve `shape.top` değerlerini ayarlayın. Bu, piksel‑tam kontrol sağlar.

## Step 3: Access the Shape’s Shadow Format (add shadow to shape)

Bir şeklin görsel şıklığı `ShadowFormat` içinde saklanır. Bunu alarak gölgenin görünümünü tanımlayan tüm özelliklere erişiriz.

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

Bu aşamada gölge hâlâ görünmez—talimatlarınızı bekleyen gizli bir katman gibi düşünün.

## Step 4: Configure the Shadow (how to add shape shadow, apply shadow effect word)

İşte sihrin gerçekleştiği yer. Gölgeyi açacağız ve görünümünü ince ayar yapacağız. Aşağıdaki değerler, çoğu belge için iyi çalışan yumuşak, diyagonal bir gölge üretir; ancak denemeler yapabilirsiniz.

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### What each property does

| Property | Effect | Typical Range |
|----------|--------|---------------|
| `visible` | Turns the shadow on/off | `True` / `False` |
| `distance` | How far the shadow sits from the shape | 2 – 10 pts |
| `blur` | Softness of the shadow edges | 4 – 12 pts |
| `color` | Shadow hue; dark gray is a safe default | Any `aw.Color` |
| `opacity` | Transparency; 0 = invisible, 1 = solid | 0.3 – 0.8 for subtle look |
| `angle` | Direction the light comes from | 0 – 360° |

**Why adjust these?** İyi ayarlanmış bir gölge, düz bir dikdörtgeni sayfadan yükselmiş gibi gösterir, derinlik katar ve hiçbir resme ihtiyaç duymaz. `opacity` değerini çok yüksek ayarlarsanız gölge sert görünür; çok düşük ayarlarsanız ise kaybolur.

## Step 5: Save the Document (create word document aspose)

Son olarak dosyayı diske yazdırın. Aspose.Words tarafından desteklenen herhangi bir uzantıyı (`.docx`, `.pdf`, `.html`) kullanabilirsiniz. Bu öğreticide `.docx` ile kalacağız.

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Oluşturulan dosyayı Microsoft Word ile açın; net bir dikdörtgen ve hafif bir gölge göreceksiniz—tam da profesyonel bir şablondan beklediğiniz gibi.

![Aspose.Words kullanarak dikdörtgen şekli ve gölge ekleme](/images/rectangle-shadow.png){alt="Aspose.Words kullanarak dikdörtgen şekli ve gölge ekleme"}

*Yukarıdaki ekran görüntüsü, gölge uygulanmış dikdörtgeni gösterir. Hafif bulanıklık ve 45° açı, doğal bir görünüm sağlar.*

## Common Variations and Edge Cases

### Adding Multiple Shapes

Birden fazla dikdörtgene ihtiyacınız varsa, sadece `insert_shape` çağrısını tekrarlayın. Çakışmayı önlemek için builder’ın imlecini (`builder.move_to(shape)`) hareket ettirmeyi veya `shape.left`/`shape.top` değerlerini ayarlamayı unutmayın.

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### Changing the Shape Type

Bu kılavuz dikdörtgenlere odaklansa da aynı desen oval, yıldız veya özel serbest‑form şekilleri için de çalışır. `ShapeType.RECTANGLE` yerine `ShapeType.OVAL`, `ShapeType.CLOUD` vb. kullanın; gölge ayarları aynı kalır.

### Saving to Other Formats

Aspose.Words tek bir satırla PDF, PNG veya hatta XPS olarak dışa aktarabilir:

```python
doc.save("output/ShapeWithShadow.pdf")
```

Gölge renderlaması tüm formatlarda korunur, dolayısıyla PDF’niz Word dosyanız gibi görünecektir.

### Handling Large Documents

Devasa raporlar üretirken, tüm şekilleri ekledikten sonra `doc.update_page_layout()` çağrısını düşünün. Bu, bir layout geçişi zorlayarak PDF’ye dönüştürürken performansı artırabilir.

## Full Working Example (All Steps Combined)

Aşağıda `rectangle_shadow.py` adlı bir dosyaya kopyalayıp yapıştırabileceğiniz tam betik yer alıyor. `python rectangle_shadow.py` komutuyla çalıştırın ve `output` klasörüne bakın.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Bu betiği çalıştırdığınızda, daha önce tartıştığımız aynı belge oluşturulur. Sayıları istediğiniz gibi değiştirin; kod kasıtlı olarak basit tutulmuştur, böylece korkmadan deneme yapabilirsiniz.

## Frequently Asked Questions

**Q: Does this work on Linux?**


## What Should You Learn Next?

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}