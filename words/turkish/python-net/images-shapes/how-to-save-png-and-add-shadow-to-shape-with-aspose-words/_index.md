---
category: general
date: 2026-08-17
description: Aspose.Words for Python kullanarak PNG kaydetme. Şekle gölge eklemeyi,
  belgeyi PDF olarak kaydetmeyi ve Word'ü PNG'ye dönüştürmeyi tek bir rehberde öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: tr
lastmod: 2026-08-17
og_description: Aspose.Words ile PNG kaydetme. Bu öğreticide bir şekle gölge ekleme,
  belgeyi PDF olarak kaydetme ve Word'ü PNG'ye dışa aktarma gösterilmektedir.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Aspose.Words ile PNG kaydetme ve şekle gölge ekleme
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Aspose.Words ile PNG kaydetme ve şekle gölge ekleme
url: /tr/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PNG Kaydetme ve Aspose.Words ile Şekle Gölge Ekleme

Bir Word dosyasından **PNG nasıl kaydedilir** ihtiyacınız varsa, bu rehber size eksiksiz, çalıştırılabilir bir çözüm sunar. Ayrıca **şekle gölge ekleme**, **belgeyi PDF olarak kaydetme** ve **Word'ü PNG olarak dışa aktarma** işlemlerini Aspose.Words ortamından çıkmadan göreceksiniz.

Bu öğretici, boş bir Word belgesini PDF ve PNG görüntüsüne dönüştürmek için gereken her şeyi, bir dikdörtgen şekline basit bir gölge efekti uygulayarak kapsar. Harici araçlara gerek yoktur ve kod, Aspose.Words for Python via .NET 7 veya daha yeni sürümlerle çalışır.

## Başaracaklarınız

* Programlı olarak yeni bir Word belgesi oluşturun.  
* Bir dikdörtgen şekli ekleyin ve gölge efektini yapılandırın.  
* Aynı belgeyi PDF dosyası olarak kaydedin.  
* Belgeyi PNG görüntüsü olarak dışa aktarın.  

Bu adımlar, **PNG nasıl kaydedilir** sorusuna yanıt verirken aynı zamanda **şekle gölge ekleme** ve **belgeyi PDF olarak kaydetme** işlemlerini tek bir iş akışında ele alır.

## Önkoşullar

* Python 3.9 veya daha yeni bir sürüm.  
* Aspose.Words for Python via .NET kurulu (`pip install aspose-words`).  
* Belirttiğiniz çıktı dizinine yazma izni.  

Henüz Aspose.Words kurmadıysanız, şu komutu çalıştırın:

```bash
pip install aspose-words
```

## Aspose.Words ile PNG Kaydetme

İlk önemli adım bir belge ve bir `DocumentBuilder` oluşturmaktır. Builder, şekiller, tablolar veya metin gibi içerik eklemek için akıcı bir API sağlar.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` bellek içinde tüm Word dosyasını temsil eder. `aw.DocumentBuilder` mevcut ekleme konumunu gösterir; başlangıçta bu, ilk (ve tek) bölümün başlangıcıdır.

## Dışa Aktarmadan Önce Şekle Gölge Ekleme

Bir şekil, herhangi bir çizim nesnesi olabilir—dikdörtgen, elips veya özel çokgen. Burada 100 × 100 point bir dikdörtgen oluşturup yumuşak bir gölge uyguluyoruz.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

Gölgeyi kaydetmeden önce neden yapılandırıyoruz? Aspose.Words, gölgeyi PDF ve PNG dışa aktarma aşamalarında işler, böylece görsel etki her iki çıktı formatında da korunur.

### Pro ipucu
Daha keskin bir gölgeye ihtiyacınız varsa, `blur` değerini azaltın. Daha belirgin bir kaydırma için `distance` değerini artırın. `Shadow` sınıfı ayrıca ince ayar kontrolü için `angle` ve `transparency` özelliklerini sunar.

## Belgeyi PDF Olarak Kaydetme

İçerik hazır olduğunda bir Word belgesini PDF olarak kaydetmek tek satır kodla yapılır. `SaveFormat.PDF` sabiti, Aspose.Words'e dönüşümü gerçekleştirmesini söyler.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

Ortaya çıkan PDF, tanımladığınız tam gölgeye sahip dikdörtgeni içerir. Aspose.Words vektör grafiklerini işlediği için PDF boyutu makul kalır.

## Word'ü PNG Olarak Dışa Aktarma

PNG olarak dışa aktarmak her sayfanın raster görüntüsünü oluşturur. Varsayılan olarak Aspose.Words 96 DPI kullanır; `PngSaveOptions` nesnesi sağlayarak bu değeri artırabilir ve daha yüksek çözünürlüklü çıktı elde edebilirsiniz.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

**Word'ü PNG olarak dışa aktardığınızda**, her sayfa ayrı bir PNG dosyası olarak kaydedilir. Örnek belgemiz yalnızca bir sayfa olduğu için sadece tek bir PNG dosyası oluşur.

### İsteğe Bağlı: Yüksek Çözünürlüklü PNG

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

Daha yüksek DPI, PNG'nin baskıda kullanılacağı veya net bir küçük resim gerektiği durumlarda faydalıdır.

## Tam betik – kopyala, yapıştır ve çalıştır

Aşağıda, yukarıda açıklanan tüm adımları uygulayan eksiksiz, bağımsız bir betik yer alıyor. `generate_assets.py` olarak kaydedin ve komut satırından çalıştırın.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Beklenen çıktı

Betik çalıştırıldığında üç dosya oluşturulur:

* `output/output.pdf` – siyah gölge oluşturan bir dikdörtgen içeren PDF.  
* `output/output.png` – aynı sayfanın 96 DPI PNG renderı.  
* `output/high_res_output.png` – daha yüksek kalite için 300 DPI PNG.  

Gölgenin tam olarak tanımlandığı gibi göründüğünü doğrulamak için dosyalardan herhangi birini favori görüntüleyicinizde açın.

## Yaygın sorular ve uç durumlar

**Çıktı dizini mevcut değilse ne olur?**  
Betik, `os.makedirs(output_dir, exist_ok=True)` çağrısını yapar; bu, klasörü otomatik olarak oluşturur. Böylece kaydetme işlemleri sırasında `FileNotFoundError` oluşması önlenir.

**Farklı gölgelerle birden fazla şekil ekleyebilir miyim?**  
Evet. Ek `Shape` nesneleri oluşturun, her bir `shadow` özelliğini bağımsız olarak yapılandırın ve kaydetmeden önce `builder.insert_node(shape)` ile ekleyin.

**Gölge, diğer raster formatlara (ör. JPEG) dönüştürülürken korunur mu?**  
Aspose.Words, `SaveFormat` tarafından desteklenen tüm raster formatlar için gölgeyi işler. `aw.SaveFormat.PNG` yerine `aw.SaveFormat.JPEG` koyabilirsiniz; gölge hâlâ görünecektir.

**Bu, “convert word to pdf” işleminden nasıl farklıdır?**  
`convert word to pdf` temelde adım 4'te yapılan aynı işlemdir. `SaveFormat.PDF` ile aynı `doc.save` çağrısı, dönüşümü dahili olarak yönetir ve düzeni, yazı tiplerini ve gölgeler gibi grafik öğelerini korur.

**Şekil boyutu için bir limit var mı?**  
Şekiller point cinsinden ölçülür (1 pt ≈ 1/72 inç). Çok büyük boyutlar dosya boyutunu artırabilir, ancak Aspose.Words sabit bir limit koymaz. `aw.Shape` oluştururken `width` ve `height` argümanlarını düzenleyerek tasarımınıza uygun hale getirin.

## Sonuç

Artık bir Word belgesinden **PNG nasıl kaydedilir** konusunu biliyor ve aynı zamanda **şekle gölge ekleme**, **belgeyi PDF olarak kaydetme** ve **Word'ü PNG olarak dışa aktarma** işlemlerini Aspose.Words for Python kullanarak öğrenmiş oldunuz. Tam betik, daha büyük belgeler, birden fazla sayfa veya daha karmaşık grafik efektleri için uyarlayabileceğiniz temiz ve tekrarlanabilir bir desen gösterir.

İleriki adımlar şunları içerebilir:

* `ShapeType` değerleriyle (ellipse, cloud vb.) denemeler yapmak.  
* Using `

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren eksiksiz çalışan kod örnekleri sunar.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}