---
category: general
date: 2026-08-07
description: Aspose.Words for Python kullanarak PDF'de dikdörtgen çizin ve şekle gölge
  eklemeyi, şekil gölgesini yapılandırmayı ve belgeyi PDF olarak kaydetmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: tr
lastmod: 2026-08-07
og_description: Aspose.Words for Python ile PDF'de dikdörtgen çizin. Bu öğreticide
  şekle gölge ekleme, şekil gölgesini yapılandırma ve belgeyi PDF olarak kaydetme
  konuları gösterilerek profesyonel belge oluşturma sağlanmaktadır.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Aspose.Words for Python ile PDF'de Dikdörtgen Çizin – Kılavuz
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Aspose.Words for Python ile PDF'de dikdörtgen çizin
url: /tr/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PDF'de Dikdörtgen Çizme – Aspose.Words for Python

Python'da **PDF'de dikdörtgen çizmek** istiyorsanız, bu kılavuz size tamamen çalıştırılabilir bir çözüm sunar. **Şekle gölge ekleme**, gölgenin yapılandırılması ve son olarak **belgeyi PDF olarak kaydetme** adımlarını adım adım göreceksiniz.

Gölgelendirilmiş bir dikdörtgen oluşturmak, raporlar, faturalar veya görsel açıklamalar için yaygın bir gereksinimdir. Bu öğreticinin sonunda, gerçekçi bir gölgeye sahip bir dikdörtgen üreten bir PDF oluşturan tek bir betiğe sahip olacak ve boyut, renk ve ofseti istediğiniz tasarıma uyacak şekilde nasıl ayarlayacağınızı anlayacaksınız.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* Python 3.8+ kurulmuş.
* Aspose.Words for Python via .NET paketi (`aspose-words`) – şu komutla kurun:

```bash
pip install aspose-words
```

* PDF'yi kaydetmeyi planladığınız klasöre yazma izni.

Ek bir kütüphane gerekmez; Aspose.Words şekil oluşturma, gölge yapılandırma ve PDF dışa aktarmayı dahili olarak yönetir.

## Adım 1: Yeni boş bir belge oluşturun (PDF'de dikdörtgen çiz – başlatma)

İlk adım bir `Document` nesnesi örneklemektir. Bu nesne tüm PDF dosyasını temsil eder ve bölümler, paragraflar ve şekiller için bir kapsayıcı sağlar.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Neden önemli:** Aspose.Words, PDF üretimini bir Word belge modeli dönüşümü olarak ele alır; bu yüzden nihai çıktı PDF olsa bile bir `Document` ile başlarız.

## Adım 2: Belge gövdesine bir dikdörtgen şekli ekleyin

Dikdörtgen, belirli bir `ShapeType`tır. İlk bölümün gövdesine eklenir; PDF olarak kaydedildiğinde otomatik olarak yeni bir sayfa oluşturur.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Açıklama:** `width` ve `height` özellikleri, şeklin PDF'deki görsel boyutunu kontrol eder. Test sırasında dikdörtgeni doğrulamayı kolaylaştırmak için metin eklenir.

## Adım 3: Şekle gölge ekle – etkinleştir ve özelleştir

Şimdi gölge efektini açıp görünümünü ince ayarlarız. İşte **şekle gölge ekle** anahtar kelimesinin devreye girdiği yer.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Neden şekil gölgesi yapılandırılır?** `blur`, `distance` ve `angle` ayarları, gerçekçi bir aydınlatma simülasyonu yapmanızı sağlar; bu da oluşturulan PDF'lerde okunabilirliği ve görsel hiyerarşiyi artırır.

## Adım 4: Belgeyi PDF olarak kaydet – son çıktı

Dikdörtgen ve gölgesi tanımlandıktan sonra son adım, Word belgesini PDF'e dışa aktarmaktır. Bu, **belgeyi pdf olarak kaydet** gereksinimini karşılar.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

`shadow_rectangle.pdf` dosyasını açtığınızda, “Shadow demo” başlıklı, gri kenarlı bir dikdörtgen ve keskin, diyagonal bir gölge içeren tek bir sayfa göreceksiniz.

### Beklenen çıktı

* `shadow_rectangle.pdf` adlı bir PDF dosyası.
* 200 pt × 100 pt boyutunda bir sayfa.
* 5 pt ofsetli, 45° açıyla ve 8 pt bulanıklıkta görülebilir bir gölge.

## Adım 5: Varyasyonları ve kenar durumlarını keşfedin (isteğe bağlı)

Gerçek dünya projelerinde ihtiyaç duyabileceğiniz yaygın ayarlamalar aşağıdadır:

| Varyasyon | Kod snippet'i | Ne zaman kullanılır |
|-----------|--------------|---------------------|
| **Farklı şekil tipi** (ör. elips) | `aw.drawing.ShapeType.OVAL` yerine `RECTANGLE` | Yuvarlak grafikler veya rozetler için |
| **Özel gölge rengi** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Gri veya marka‑özel bir gölge gerektiğinde |
| **Birden fazla şekil** | Şekil‑oluşturma bloğunu tekrarlayın ve `left`/`top` özelliklerini ayarlayın | Karmaşık diyagramlar oluşturmak için |
| **Şekil içinde metin yok** | `rectangle.text = "..."` satırını kaldırın | Şekil sadece dekoratif olduğunda |
| **Daha yüksek DPI çıktısı** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` ile `PdfSaveOptions` görüntü kalitesi için ayarlanır | Baskı‑hazır PDF'ler için |

**İpucu:** Diğer özellikleri ayarlamadan önce her zaman `shadow.visible = True` yapın; aksi takdirde değişiklikler sessizce yok sayılır.

## Tam betik – kopyala, yapıştır ve çalıştır

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Betik dosyasını terminalinizden veya IDE'nizden çalıştırın. `YOUR_DIRECTORY` kısmını gerçek bir klasör yolu ile değiştirin; örnek: `"/tmp"` veya `"C:\\Users\\Me\\Documents"`.

## Sonuç

Artık Aspose.Words for Python kullanarak **PDF'de dikdörtgen çizme**, **şekle gölge ekleme**, **şekil gölgesini yapılandırma** ve **belgeyi PDF olarak kaydetme** konularını biliyorsunuz. Tam örnek, belge oluşturma aşamasından son dışa aktarmaya kadar her adımı gösterir; isteğe bağlı varyasyonlar ise kodu daha karmaşık senaryolara uyarlamanızı sağlar.

Sonraki adım olarak şunları keşfedebilirsiniz:

* Diğer şekil tiplerini ekleme (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Görsel çekiciliği artırmak için degrade doldurmalar veya kenarlıklar uygulama.
* Fontları gömmek veya görüntü sıkıştırmasını kontrol etmek için `PdfSaveOptions` kullanma.

Parametrelerle deney yapmaktan çekinmeyin; böylece marka ya da tasarım yönergelerinize tam uyum sağlayabilirsiniz. PDF betikleme keyfini çıkarın!


## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımları keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Optimize PDF Bookmarks Using Aspose.Words for Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimize Pdf Loading Python Aspose Words Skip Images](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python Pdf Manipulation](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}