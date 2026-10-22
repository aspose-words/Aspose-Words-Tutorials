---
category: general
date: 2026-10-16
description: Python kullanarak boş bir Word belgesi oluşturun, Word içinde şekil ekleyin,
  dış gölge ekleyin ve PDF olarak kaydedin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: tr
lastmod: 2026-10-16
og_description: Aspose.Words for Python kullanarak dış gölge şekilli boş bir Word
  belgesi oluşturun. Bu kılavuz, şekli nasıl ekleyeceğinizi, gölgeyi nasıl uygulayacağınızı
  ve dosyayı PDF olarak nasıl kaydedeceğinizi gösterir.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Şekil gölgesiyle boş Word belgesi oluştur – Python rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Python ile gölgeli şekilli boş Word belgesi oluştur
url: /tr/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python'da gölgeli şekilli boş Word belgesi oluşturma

Eğer **boş Word belgesi oluşturmak** ve özel bir grafik eklemek istiyorsanız, bu rehber tam size göre. **Word'e şekil eklemeyi**, bir **dış gölge şekli** uygulamayı ve sonunda **Python kullanarak PDF olarak kaydetmeyi** adım adım göstereceğiz.

Aspose.Words for Python'ı nasıl kuracağınızı, bir dikdörtgen oluşturmayı, gölgesini biçimlendirmeyi ve görsel efekti koruyan bir PDF oluşturmayı öğreneceksiniz. Aspose API'siyle ilgili önceden deneyim gerekmez, ancak temel Python bilgisine ve Python 3.10 veya daha yeni bir sürümünün kurulu olmasına sahip olmalısınız.

## Önkoşullar

* Python 3.10 veya daha yeni bir sürüm kurulu.
* Aktif bir Aspose.Words for Python lisansı (değerlendirme için ücretsiz deneme sürümü yeterli).
* `aspose-words` paketini kurmak için `pip` erişimi.
* PDF'nin kaydedileceği dizine yazma izni.

Kütüphaneyi tek bir komutla kurabilirsiniz:

```bash
pip install aspose-words
```

## Boş Word belgesi oluşturma – ortam kurulumu

İlk adım, şekil için bir tuval görevi görecek boş bir Word dosyası oluşturmaktır.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` tamamen boş bir Word dosyasını temsil eder. `DocumentBuilder` kullanarak `insert_shape` gibi yöntemlere erişirsiniz; bu yöntemi bir sonraki adımda kullanacağız.

## Word'e şekil ekleme ve boyutları ayarlama

Şimdi daha sonra dış gölge alacak bir dikdörtgen ekliyoruz. Boyutlar point cinsinden ifade edilir (1 pt ≈ 1/72 inç).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

`insert_shape` çağrısı, daha fazla özelleştirebileceğiniz bir `Shape` nesnesi döndürür. Bu aşamada belge, Microsoft Word'de açıldığında zaten görünür bir dikdörtgen içerir.

## Dış gölge şekli ekleme – efekti özelleştirme

Aspose.Words, stil, bulanıklık, mesafe ve renk gibi gölge özelliklerini tanımlamak için bir `ShadowEffect` sınıfı sunar.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

`style` değerini `OUTER` olarak ayarlamak, gölgenin dikdörtgenin kenarı dışında görünmesini sağlar ve hafif bir 3‑D görünüm verir. Daha sıkı veya daha yayılmış bir gölge elde etmek için `blur` ve `distance` ile deney yapabilirsiniz.

## PDF olarak kaydetme python – belgeyi tamamlama

Şekli biçimlendirdikten sonra belge doğrudan PDF olarak kaydedilebilir. Aspose.Words dönüşümü dahili olarak yönetir ve gölge efektini korur.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Herhangi bir PDF görüntüleyicide `shape_with_shadow.pdf` dosyasını açtığınızda, dış gölgesiyle birlikte dikdörtgenin Word'de göründüğü gibi olduğunu göreceksiniz.

## Tam çalışan örnek

Aşağıda tüm adımları birleştiren tam script yer almaktadır. `create_word_with_shadow.py` adlı bir dosyaya kopyalayıp çalıştırın.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Beklenen çıktı**

Script'i çalıştırdığınızda bir onay satırı yazdırılır, örneğin:

```
PDF generated at: output/shape_with_shadow.pdf
```

Oluşturulan PDF'yi açtığınızda, yumuşak siyah dış gölgelere sahip 200 pt × 100 pt bir dikdörtgen içeren tek bir sayfa görürsünüz.

## Yaygın varyasyonlar ve uç durumlar

* **Gölge rengini değiştirme** – `aw.Color.black` yerine `aw.Color.red` veya `aw.Color.from_argb(255, 0, 120, 215)` gibi başka bir `aw.Color` değeri kullanın.
* **Farklı bir şekil kullanma** – `aw.drawing.ShapeType.RECTANGLE` değerini `OVAL`, `DIAMOND` veya desteklenen başka bir enum değeriyle değiştirin.
* **PDF yerine DOCX olarak kaydetme** – Word formatını korumak için `doc.save("output/shape.docx")` çağrısını yapın.
* **Birden fazla şekil** – `builder.insert_shape` metodunu tekrar çağırarak ek şekiller oluşturun; her şeklin kendi `ShadowEffect`'i olabilir.

**Pro ipucu:** Şekli belirli bir konuma yerleştirmeniz gerekiyorsa, eklemeden sonra `rectangle.left` ve `rectangle.top` değerlerini ayarlayın. Bu, yerleştirme üzerinde piksel‑tam kontrol sağlar.

## Sonuç

Artık **boş Word belgesi oluşturmayı**, **Word'e şekil eklemeyi**, **dış gölge şekli eklemeyi** ve **Python kullanarak PDF olarak kaydetmeyi** biliyorsunuz. Tam kod örneği uçtan uca iş akışını gösterir ve açıklamalar her API çağrısının neden gerekli olduğunu ortaya koyar.

Buradan itibaren daha gelişmiş stil seçeneklerini keşfedebilir, şeklin içine metin ekleyebilir veya karmaşık diyagramlar oluşturmak için birden fazla şekli birleştirebilirsiniz. Farklı gölge parametreleriyle deney yaparak markanızın görsel diline uygun hale getirin ve bu yaklaşımı daha büyük belge‑oluşturma süreçlerine entegre edin.

Kodlamanın tadını çıkarın!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki eğitimler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Dikdörtgen şekil oluştur, gölge ekle ve PDF olarak kaydet](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Word'den PDF oluştur – Aspose.Words ile Tam Python Rehberi](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Aspose.Words ile Word'de Şekle Gölge Ekle – Adım‑Adım](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}