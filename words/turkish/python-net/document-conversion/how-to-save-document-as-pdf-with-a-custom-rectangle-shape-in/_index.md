---
category: general
date: 2026-10-07
description: Aspose.Words for Python kullanarak bir dikdörtgen şekli ve özel gölge
  eklerken belgeyi PDF olarak kaydetmeyi öğrenin. Adım adım kod dahil.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: tr
lastmod: 2026-10-07
og_description: Aspose.Words for Python kullanarak özel bir dikdörtgen şekliyle belgeyi
  PDF olarak kaydedin. Çizim, stil ve Word'ü PDF'ye aktarma adımlarını içeren tam
  örneği izleyin.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Belgeyi dikdörtgen şekilli PDF olarak kaydedin – tam Python rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Python'da özel bir dikdörtgen şekliyle belgeyi PDF olarak kaydetme
url: /tr/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python'da özel bir dikdörtgen şekliyle belgeyi PDF olarak kaydetme

Özel grafikler eklerken **save document as PDF** yapmanız gerekiyorsa, bu kılavuz size nasıl yapılacağını gösterir. Boş bir Word dosyası oluşturmayı, **drawing a rectangle shape** yapmayı, boyutunu ayarlamayı, görünür bir gölge uygulamayı ve sonunda Aspose.Words for Python kütüphanesini kullanarak **export Word to PDF** işlemini adım adım anlatacağız.

Tam olarak konumlandırılmış bir dikdörtgen içeren bir PDF elde edeceksiniz; raporlar, faturalar veya herhangi bir belge‑otomasyon senaryosu için hazır. Harici araçlara gerek yok—sadece Python ve Aspose.Words paketi.

## İhtiyacınız olanlar

| Gereksinim | Neden önemli |
|-------------|----------------|
| Python 3.8+ | Aspose.Words for Python API modern yorumlayıcıları hedefler. |
| `aspose-words` package (`pip install aspose-words`) | Kod örneklerinde kullanılan `aw` ad alanını (namespace) sağlar. |
| Basic familiarity with Python and object‑oriented programming | Bu öğreticide `Document` ve `Shape` gibi nesnelerle çalışılır. |
| Write permission to a folder where the PDF will be saved | `save document as pdf` adımı bir dosyayı diske yazar. |

> **Pro tip:** Bağımlılıkları izole tutmak için bir sanal ortam (`python -m venv venv`) kullanın.

## Dikdörtgen şekilli belgeyi PDF olarak kaydetme

Aşağıda tam ve çalıştırılabilir bir örnek bulunmaktadır. Her adım açıklanmıştır, böylece **neden** bu işlemi yaptığımızı, sadece **ne** yaptığını değil, anlayabilirsiniz.

### Adım 1: Yeni boş bir belge başlatma

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Yeni bir `Document` nesnesi oluşturmak size temiz bir sayfa koleksiyonu sağlar. Daha sonra **export Word to PDF** yapmak isterseniz mevcut bir *.docx* dosyasını da yükleyebilirsiniz, ancak boş başlamak örneği odaklı tutar.

### Adım 2: Belgeye dikdörtgen şekli ekleme

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

`add rectangle shape` adımı `ShapeType.RECTANGLE` kullanır. Şekli bir paragrafın sonuna ekleyerek, Aspose.Words son PDF'de nerede render edileceğini bilir.

### Adım 3: Dikdörtgen boyutlarını ayarlama

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Açık **rectangle dimensions** ayarlamak, şeklin farklı platformlarda tutarlı görünmesini sağlar. İmparatorluk birimlerini tercih ederseniz `convert_to_inches` yardımcılarını da kullanabilirsiniz.

### Adım 4: (İsteğe bağlı) Görünür özel gölge uygulama

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Gölge, dikdörtgenin PDF içinde öne çıkmasını sağlar. `shadow.visible` bayrağı gereklidir; olmadan diğer özellikler etkisiz kalır.

### Adım 5: Belgeyi PDF olarak kaydetme

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

`document.save` metodunu **.pdf** uzantısıyla çağırmak, Aspose.Words’ün yerleşik PDF renderlayıcısını kullanarak otomatik olarak **save document as pdf** yapar. Ek bir dönüşüm adımına gerek yoktur; bu yüzden bu yöntem **export Word to PDF** için önerilen yoldur.

> **Neden bu çalışır:** Aspose.Words, dikdörtgen ve gölgesi dahil belge düzenini doğrudan PDF akışına yazar. İşlem kayıpsızdır ve vektör kalitesini korur.

## Tam kaynak kodu (tek script)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

Bu scripti çalıştırdığınızda aşağıdaki gibi bir `shadow_rectangle.pdf` oluşturulur:

![Kaydedilen PDF'te dikdörtgen şekli gösteren oluşturulan PDF diyagramı](placeholder-image.png)

*PDF, belgede ortalanmış siyah gölgeli bir dikdörtgen içeren tek bir sayfa içerir.*

## Yaygın sorular ve uç durumlar

| Soru | Cevap |
|----------|--------|
| **Dikdörtgeni belirli bir konuma yerleştirebilir miyim?** | Evet. Kaydetmeden önce `rectangle.left` ve `rectangle.top` (puan cinsinden) ayarlayın. |
| **Birden fazla şekle ihtiyacım olursa ne olur?** | Ek `Shape` nesneleri oluşturun, her birini yapılandırın ve aynı ya da farklı paragraflara ekleyin. |
| **Gölge PDF boyutunu etkiler mi?** | Sadece çok az; gölge vektör meta verisi olarak saklanır, raster görüntü olarak değil. |
| **Mevcut *.docx* dosyalarını dönüştürmek için bunu kullanabilir miyim?** | Kesinlikle. `aw.Document()` yerine `aw.Document("input.docx")` kullanın ve diğer adımlar aynı kalır. |
| **Dikdörtgenin doldurma rengini değiştirmek mümkün mü?** | `rectangle.fill_color = aw.drawing.Color.light_blue` (veya tercih ettiğiniz herhangi bir `Color`) şeklinde ayarlayın. |

## Sonraki adımlar

Artık özel bir dikdörtgenle **save document as PDF** yapabildiğinize göre, şunları keşfedebilirsiniz:

* **Export Word to PDF** başlıklar, altbilgiler ve sayfa numaralarıyla.  
* **Add other drawing objects** (`Ellipse`, `Polygon`) aynı `Shape` sınıfını kullanarak.  
* **Batch process** bir klasördeki Word dosyalarını, aynı dikdörtgen kaplamasını her birine uygulayarak.  

Bu uzantılar aynı modeli izler: bir şekil oluşturun, özelliklerini yapılandırın ve **save document as pdf** yapın.

---

**Özet:** Bu öğretici, Aspose.Words for Python kullanarak **save document as PDF** yaparken **add rectangle shape**, **set rectangle dimensions** ve özel bir gölge uygulamayı gösterdi. Tam script kopyalanmaya, çalıştırılmaya ve kendi belge‑otomasyon akışlarınıza uyarlamaya hazır. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Dikdörtgen şekli oluştur, gölge ekle ve PDF olarak kaydet](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words ile PDF'ye dikdörtgen ekle – Adım Adım Kılavuz](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Aspose.Words ile Belgeyi PDF Olarak Kaydet – Tam C# Kılavuzu](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}