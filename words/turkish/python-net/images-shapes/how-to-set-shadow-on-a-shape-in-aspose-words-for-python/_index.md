---
category: general
date: 2026-09-27
description: Aspose.Words for Python ile bir şekle gölge ayarlamayı öğrenin. Bu kılavuz,
  şekle gölge ekleme, gölge efekti uygulama ve gölge rengini ayarlamayı kapsar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- add shadow to shape
- apply shadow effect
- set shadow color
- how to add shadow
language: tr
lastmod: 2026-09-27
og_description: Aspose.Words for Python kullanarak bir şekle gölge nasıl ayarlanır.
  Şekle gölge eklemek, gölge efektini uygulamak ve gölge rengini ayarlamak için adım
  adım kılavuzu izleyin.
og_image_alt: Screenshot showing how to set shadow on a shape in a Word document
og_title: Aspose.Words for Python'da bir şekle gölge nasıl ayarlanır
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to set shadow on a shape with Aspose.Words for Python. This
    guide covers add shadow to shape, apply shadow effect, and set shadow color.
  headline: How to set shadow on a shape in Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Shapes
- Shadow effect
title: Aspose.Words for Python'da bir şekle gölge nasıl ayarlanır
url: /tr/python/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Python'da bir şekle gölge ayarlama

Bir çizim nesnesi için **gölge ayarlama** ihtiyacınız varsa, bu rehber tam süreci gösterir. Şekle nasıl gölge ekleyeceğinizi, gölgenin bulanıklığını, offset'ini ve rengini nasıl yapılandıracağınızı ve güncellenmiş belgeyi koddan çıkmadan nasıl kaydedeceğinizi göreceksiniz.

Bu öğretici, zaten temel bir Aspose.Words for Python ortamına sahip olduğunuzu varsayar. Makalenin sonunda, bir DOCX dosyasındaki herhangi bir şekle profesyonel görünümlü bir gölge efekti uygulayabileceksiniz.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* Python 3.8+ yüklü.
* Aspose.Words for Python via .NET (`pip install aspose-words`) yüklü.
* En az bir şekil (ör. bir dikdörtgen veya resim) içeren bir Word belgesi (`input.docx`).  
  Belge boşsa, kod gösterim amacıyla yeni bir şekil oluşturacaktır.

Bu öğeler, sonraki adımların import hatası almadan çalışmasını garanti eder.

## Adım 1: Word belgesini yükleyin veya oluşturun

İlk işlem bir `Document` nesnesi elde etmektir. Mevcut bir dosyayı yükleyebilir veya yeni bir tane oluşturabilirsiniz.

```python
import aspose.words as aw

# Load an existing document, or create a new blank document if the file does not exist.
try:
    doc = aw.Document("YOUR_DIRECTORY/input.docx")
except Exception:
    doc = aw.Document()          # Creates an empty document
    # Optional: add a paragraph so the document is not completely empty.
    builder = aw.DocumentBuilder(doc)
    builder.writeln("Document created for shadow demo.")
```

*Bu adımın önemi*: `Document` nesnesi tüm Word‑işleme işlemlerinin giriş noktasıdır. Onsuz şekillere erişemez veya görsel efektler uygulayamazsınız.

## Adım 2: Hedef şekli alın

Bir şeklin görünümünü değiştirmek için şekil düğümüne bir referansa ihtiyacınız var. Aşağıdaki örnek, belge hiyerarşisinde bulunan ilk şekli alır.

```python
# Retrieve the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# If the document has no shapes, create one for demonstration purposes.
if shape is None:
    builder = aw.DocumentBuilder(doc)
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
    shape.wrap_type = aw.drawing.WrapType.INLINE
```

*Bu adımın önemi*: `add shadow to shape` somut bir shape nesnesi gerektirir. Kod, belgenin şekil içermediği uç durumu güvenli bir şekilde ele alır ve öğreticinin her okuyucu için çalışmasını sağlar.

## Adım 3: Gölge görünümünü yapılandırın

Şimdi şeklin `shadow` özelliğini ayarlayarak **gölge efekti uygulayabilirsiniz**. Aşağıdaki ayarlar hafif, koyu bir gölge verir.

```python
# Set the shadow blur radius (softness). Larger values produce a more diffused shadow.
shape.shadow.blur = 5.0

# Horizontal displacement of the shadow in points.
shape.shadow.offset_x = 2.0

# Vertical displacement of the shadow in points.
shape.shadow.offset_y = 2.0

# Set the shadow color. This demonstrates **set shadow color** to black.
shape.shadow.color = aw.Color.black

# Enable the shadow (some older versions require explicit visibility).
shape.shadow.visible = True
```

*Her özelliğin önemi*:

| Özellik | Etkisi |
|----------|--------|
| `blur`   | Gölgenin ne kadar bulanık görüneceğini kontrol eder. |
| `offset_x` / `offset_y` | Gölgenin şekle göre yönünü ve uzaklığını belirler. |
| `color`  | Gölgenin rengini tanımlar; istediğiniz herhangi bir `aw.Color` kullanabilirsiniz. |
| `visible`| Gölgenin çıktı dosyasında render edilmesini sağlar. |

`aw.Color.black` yerine `aw.Color.from_argb(255, 0, 0, 0)` gibi özel bir RGBA değeri ya da başka önceden tanımlı bir renk kullanabilirsiniz.

## Adım 4: Değiştirilen belgeyi kaydedin

Gölgeyi yapılandırdıktan sonra değişiklikleri yeni bir dosyaya kalıcı hâle getirin.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved with shadow effect at: {output_path}")
```

`output.docx` dosyasını Microsoft Word'de açtığınızda, seçilen şekil 2 pt sağa ve 2 pt aşağı kaydırılmış yumuşak siyah bir gölge gösterir.

## Tam çalışan örnek

Tüm adımları bir araya getirerek IDE'nize kopyalayıp yapıştırabileceğiniz bağımsız bir betik elde edersiniz.

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str):
    # Load or create the document.
    try:
        doc = aw.Document(input_path)
    except Exception:
        doc = aw.Document()
        builder = aw.DocumentBuilder(doc)
        builder.writeln("Document created for shadow demo.")

    # Retrieve the first shape; create one if none exist.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        builder = aw.DocumentBuilder(doc)
        shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
        shape.wrap_type = aw.drawing.WrapType.INLINE

    # Apply shadow settings.
    shape.shadow.blur = 5.0
    shape.shadow.offset_x = 2.0
    shape.shadow.offset_y = 2.0
    shape.shadow.color = aw.Color.black
    shape.shadow.visible = True

    # Save the result.
    doc.save(output_path)
    print(f"Shadow applied and saved to {output_path}")

# Example usage
if __name__ == "__main__":
    add_shadow_to_first_shape(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx"
    )
```

Betik çalıştırıldığında, ilk şekil yapılandırılmış gölgeyi taşıyan `output.docx` oluşturulur.

## Yaygın tuzaklar ve nasıl önlenir

| Sorun | Sebep | Çözüm |
|-------|--------|-----|
| `shape` is `None` even after loading a document | Belge hiçbir çizim nesnesi içermiyor. | Adım 2'de gösterilen yedek şekil oluşturma bloğunu kullanın. |
| Shadow does not appear in Word | `shape.shadow.visible` `False` olarak bırakılmış veya belge eski bir formatta (ör. `.doc`) kaydedilmiş. | `visible = True` olduğundan emin olun ve `.docx` olarak kaydedin. |
| Color looks different than expected | Belgenin teması açık renkleri geçersiz kılıyor. | Tema geçersiz kılındıktan sonra `shape.shadow.color` ayarlayın veya `aw.Color.from_argb` kullanın. |

Bu uç durumları ele almak, çözümün üretim kodu için dayanıklı olmasını sağlar.

## Etkiyi genişletme (sonraki adımlar)

Artık **gölge ekleme** yöntemini bildiğinize göre ilgili iyileştirmeleri keşfedebilirsiniz:

* `shape.shadow` alt‑özelliklerini ayarlayarak **gölge efekti** uygulama, degrade veya çoklu gölgeler ekleme.
* Kullanıcı girişi veya tema renklerine göre dinamik olarak **gölge rengini ayarlama**.
* **add shadow to shape** işlemini döndürme, çizgi stili veya 3‑D efektler gibi diğer biçimlendirme eylemleriyle birleştirme.
* `doc.get_child_nodes(aw.NodeType.SHAPE, True)` üzerinden döngü yaparak belgedeki her şekle otomatik gölge ekleme.

Bu genişletmeler, görsel olarak tutarlı ve profesyonel çıktılar üreten gelişmiş belge‑oluşturma hatları oluşturmanıza olanak tanır.

## Sonuç

Artık Aspose.Words for Python kullanarak bir şekle **gölge ayarlama** için tam, çalıştırılabilir bir çözümünüz var. Rehber, belge yükleme, şekil alma veya oluşturma, bulanıklık, offset ve **gölge rengini ayarlama** yapılandırma ve dosyayı kaydetme adımlarını kapsadı. Bu deseni otomasyon projelerinizdeki herhangi bir şekle uygulayın ve tasarım gereksinimlerinizi karşılamak için ek görsel ayarlamalarla deney yapın.

--- 

*Kodları diğer şekil türleri, renkler veya offset değerleri için özgürce uyarlayabilirsiniz. Herhangi bir sorunla karşılaşırsanız, “Yaygın tuzaklar” tablosunu incelemek iyi bir ilk adımdır.*

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalarla tam çalışan kod örnekleri içerir ve kendi projelerinizde ek API özelliklerini öğrenmenize ve alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olur.

- [C#'da şekle gölge ekleme – Gölge Efekti Uygulama Tam Kılavuzu](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/)
- [Word'de şekle gölge ekleme – Tam Aspose.Words Kılavuzu](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Dikdörtgen şekil oluştur, gölge ekle ve PDF olarak kaydet](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}