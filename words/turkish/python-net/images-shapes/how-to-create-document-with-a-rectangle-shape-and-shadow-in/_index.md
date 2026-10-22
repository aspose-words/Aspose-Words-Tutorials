---
category: general
date: 2026-10-04
description: Python'da belge oluşturma ve Aspose.Words kullanarak şekle gölge ekleme.
  Gölge rengini ayarlamayı, dikdörtgen şekli eklemeyi ve dış gölgeyi özelleştirmeyi
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: tr
lastmod: 2026-10-04
og_description: Python'da belge nasıl oluşturulur ve şekle gölge eklenir. Bu kılavuz,
  gölge rengini nasıl ayarlayacağınızı, dikdörtgen şekli nasıl ekleyeceğinizi ve Aspose.Words
  kullanarak dış gölgeyi nasıl uygulayacağınızı gösterir.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Python'da dikdörtgen şekilli ve gölgeli bir belge nasıl oluşturulur
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Python'da Dikdörtgen Şekilli ve Gölgelikli Belge Nasıl Oluşturulur
url: /tr/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python'da Dikdörtgen Şekli ve Gölge ile Belge Oluşturma

Eğer **how to create document** içinde stilize bir dikdörtgen barındıran bir belgeye ihtiyacınız varsa, bu kılavuz eksiksiz bir çözüm sunar. **add shadow to shape** nasıl yapılır, gölgenin rengi nasıl ayarlanır ve ofset ile bulanıklığı nasıl kontrol edilir—tüm bunları Aspose.Words for Python ile göreceksiniz. Eğitim sonunda, dağıtıma hazır, şık görünümlü bir `.docx` dosyası oluşturabileceksiniz.

Aşağıdaki adımlar, kütüphanenin kurulumu부터 gölgenin görünümünün özelleştirilmesine kadar her şeyi kapsar. Harici bir dokümantasyona ihtiyaç yok; kodu kopyalayıp çalıştırabilir ve kendi projelerinize uyarlayabilirsiniz. Ayrıca **insert rectangle shape**, **outer shadow style** seçimini ve görünmez gölgeler ya da hatalı sarma ayarları gibi yaygın sorunları nasıl ele alacağınızı öğreneceksiniz.

## Prerequisites

Başlamadan önce şunların yüklü olduğundan emin olun:

* Python 3.8 veya daha yeni bir sürüm.
* Aktif bir Aspose.Words for Python lisansı (veya ücretsiz deneme anahtarı).
* Python betikleme konusunda temel bilgi.
* Oluşturulan belgenin kaydedileceği bir dosya sistemi konumuna erişim.

SDK’yı pip ile kurabilirsiniz:

```bash
pip install aspose-words
```

## Step 1: Import the library and create a new blank document

Yeni bir belge oluşturmak, herhangi bir Word otomasyon senaryosundaki ilk adımdır. `aw.Document()` yapıcı fonksiyonu, metin, resim veya şekil ekleyebileceğiniz boş bir dosya sağlar.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

`DocumentBuilder` nesnesi, içerik eklemeyi basitleştirir. Mevcut imleç konumunu takip eder, böylece bölümleri manuel olarak yönetmeden öğeleri sıralı bir şekilde ekleyebilirsiniz.

## Step 2: Insert a rectangle shape of the desired size

Dikdörtgen şekil, görsel öğeler için bir kapsayıcı görevi görür. Genişlik ve yüksekliğini puan cinsinden (1 pt ≈ 1/72 in) tanımlayabilirsiniz.

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

Bu aşamada şeklin görsel bir stili yoktur; sadece düz bir kontur olarak görünür. Sonraki adımlar ona derinlik ve renk kazandıracaktır.

## Step 3: Set the shape to flow inline with the surrounding text

Bir şekil **inline** olduğunda, bir paragraftaki karakter gibi davranır. Bu, dikdörtgenin belge düzeninde beklediğiniz yerde kalmasını sağlar.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Şeklin metnin üzerinde yüzen bir konumda olmasını isterseniz `WrapType.SQUARE` veya `WrapType.TOP_BOTTOM` kullanabilirsiniz; ancak çoğu rapor için inline şekil, düzeni öngörülebilir kılar.

## Step 4: Make the shadow visible and choose its color

Görünmez bir gölge hiçbir görsel fayda sağlamaz. `visible` bayrağı efekti etkinleştirir ve `color` özelliği gölgenin tonunu belirler. Siyah renk klasik ve ince bir derinlik sunar.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

`aw.drawing.Color.black` ifadesini `aw.drawing.Color.gray` gibi başka bir renk ya da özel bir RGB değeri (`aw.drawing.Color.from_argb(255, 128, 128, 128)`) ile değiştirebilirsiniz.

## Step 5: Define the shadow’s offset and blur to give it depth

Ofset, gölgenin şekilden ne kadar uzağa kaydırıldığını kontrol eder, bulanıklık yarıçapı ise kenarları yumuşatır. Küçük değerler net bir gölge oluşturur; daha büyük değerler ise daha yumuşak bir görünüm verir.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Tasarım yönergelerinize uygun olması için bu sayılarla deneme yapın. Ağır bir düşen gölge için hem ofseti hem de bulanıklığı artırabilirsiniz.

## Step 6: Choose an outer shadow style

Aspose.Words, `INNER`, `OUTER` ve `PERSPECTIVE` gibi çeşitli gölge stilleri sunar. **outer** stili, gölgeyi şeklin kenarının dışına yerleştirir ve temiz, profesyonel bir görünüm sağlar.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Daha dramatik bir etki isterseniz `ShadowStyle.PERSPECTIVE` deneyin—bu, üç boyutlu bir eğim ekler.

## Step 7: Save the document with the shaped shadow

Kaydetmek, dosyayı sonlandırır ve tüm biçimlendirmeyi diske yazar. Yazma izniniz olan bir dizin seçin ve dosyaya açıklayıcı bir ad verin.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Betik çalıştırıldığında, görünür ve renkli bir gölgeye sahip bir dikdörtgen içeren bir Word dosyası oluşur. Sonucu doğrulamak için dosyayı Microsoft Word veya LibreOffice ile açın.

## Full runnable example

Aşağıda, tartışılan tüm adımları içeren tam betik yer almaktadır. Kodu `create_shadowed_shape.py` adlı bir dosyaya kopyalayın ve `python create_shadowed_shape.py` komutuyla çalıştırın.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Expected output**

`ShapeWithShadow.docx` dosyasını açtığınızda, sayfanın ortasında tek bir dikdörtgen göreceksiniz. Dikdörtgen, sağ‑alt köşeye hafifçe kaydırılmış, hafifçe bulanıklaştırılmış ince bir siyah gölgeyle birlikte görünür. Gölge dış stilini benimser, bu yüzden dikdörtgenin iç kısmına dokunmaz.

## Common questions and edge cases

### Why does the shadow sometimes appear invisible?

Gölge yalnızca `shadow.visible` **True** olarak ayarlandığında **ve** şeklin `wrap_type` özelliği görüntülenmesine izin verdiğinde işlenir. Inline şekil güvenilir bir şekilde çalışır; yüzen şekiller ek düzen ayarlamaları gerektirebilir.

### How can I change the shadow color to match a brand palette?

`aw.drawing.Color.black` ifadesini özel bir RGB değeriyle değiştirin:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### What if I need the shape to appear behind text?

`WrapType.BEHIND` olarak sarma tipini ayarlayın ve gerekirse `z_order_position` değerini düzenleyin. Bazı görüntüleyicilerin arka‑metin şekillerini farklı render ettiğini unutmayın.

### Can I apply the same shadow settings to multiple shapes?

Evet. Gölgeyi yapılandıran bir yardımcı fonksiyon oluşturup, eklediğiniz her şekil için bu fonksiyonu çağırabilirsiniz. Bu, kod tekrarını azaltır ve stil tutarlılığını sağlar.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Conclusion

Artık Aspose.Words for Python kullanarak bir dikdörtgen şekli ve özelleştirilmiş gölgesi olan **how to create document** dosyaları oluşturabilirsiniz. Eğitim, dikdörtgen ekleme, şekli inline yapma, gölgeyi etkinleştirme, rengini, ofsetini, bulanıklığını ve stilini ayarlama ve son olarak dosyayı kaydetme konularını kapsadı.

Buradan itibaren **add shadow to shape** gibi diğer şekil tipleri, **set shadow color** dinamik olarak veri bazlı ayarlama veya **how to add shadow** resim ve metin kutularına ekleme gibi ilgili konuları keşfedebilirsiniz. Boyutları, renkleri ve gölge stillerini marka yönergelerinize veya tasarım sisteminize uygun şekilde deneyin.

Daha fazla Word belgesi otomatikleştirmeye hazır mısınız? Bir sonraki adımda tablolar, başlıklar veya dinamik içerik eklemeyi deneyin—her adım burada gösterilen aynı prensiplere dayanır. Kodlamanın tadını çıkarın!

## What Should You Learn Next?

Aşağıdaki eğitimler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım‑adım açıklamalar içerir.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}