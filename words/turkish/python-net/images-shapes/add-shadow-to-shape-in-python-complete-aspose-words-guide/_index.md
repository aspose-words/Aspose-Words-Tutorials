---
category: general
date: 2026-08-11
description: Aspose.Words for Python kullanarak şekle gölge ekleyin. Şekle gölge eklemeyi,
  şekle bulanıklık uygulamayı ve ofset ile rengi özelleştirmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- add shape shadow
- apply blur to shape
- Aspose.Words shadow effect
- Python Word shape styling
language: tr
lastmod: 2026-08-11
og_description: Aspose.Words for Python ile şekle gölge ekleyin. Bu rehber, şekle
  bulanıklık uygulamayı, ofsetleri ayarlamayı ve sadece birkaç satır kodla gölge renklerini
  seçmeyi gösterir.
og_image_alt: Word document screenshot showing a shape with a black shadow applied
og_title: Python'da şekle gölge ekleyin – adım adım Aspose.Words öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  headline: Add shadow to shape in Python – complete Aspose.Words guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  name: Add shadow to shape in Python – complete Aspose.Words guide
  steps:
  - name: Adding shadow to a specific shape by name
    text: 'If your document contains several shapes, you may want to target one by
      its `name` property:'
  - name: Skipping non‑visual nodes
    text: Sometimes a shape node can be a placeholder (e.g., a drawing canvas without
      visual content). Guard against this by checking `shape.is_image` or `shape.is_picture_frame`
      before applying the shadow.
  - name: Working with grouped shapes
    text: When shapes are grouped, the group itself is a `Shape` node. To apply a
      shadow to each member, iterate through `shape.get_child_nodes(aw.NodeType.SHAPE,
      True)`.
  - name: What’s next?
    text: '- Explore **apply blur to shape** for other effects like glow or soft edges.
      - Combine shadows with **shape borders** or **reflection** to create richer
      graphics. - Convert the edited document to PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`)
      for distribution.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Python'da şekle gölge ekleme – tam Aspose.Words rehberi
url: /tr/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Şekle gölge ekleme Python’da – tam Aspose.Words rehberi

Bir Word belgesine **şekle gölge eklemeniz** gerekiyorsa, bu öğretici Aspose.Words for Python ile bunu tam olarak nasıl yapacağınızı gösterir. Rapor oluşturucu ya da belge‑şablonlama hizmeti geliştiriyor olun, şekle gölge eklemeyi, şekle bulanıklık uygulamayı ve gölgenin görünümünü sadece birkaç satır kodla ince ayarlamayı öğreneceksiniz.

Rehber, ihtiyacınız olan her şeyi kapsar: gerekli içe aktarmalar, hedef şeklin bulunması (iç içe düğümler dahil), gölge özelliklerinin yapılandırılması, yaygın kenar durumlarının ele alınması ve değiştirilmiş belgenin kaydedilmesi. Sonunda, .docx dosyalarıyla çalışan herhangi bir Python projesine ekleyebileceğiniz yeniden kullanılabilir bir kod parçacığı elde edeceksiniz.

## Önkoşullar

- **Python 3.8+** yüklü.
- **Aspose.Words for Python via .NET** (`pip install aspose-words` ile kurulur).
- En az bir şekil (ör. bir dikdörtgen, resim veya SmartArt) içeren bir Word belgesi (`input.docx`).
- Python ve Aspose.Words nesne modeli hakkında temel bilgi.

## Adım 1: Aspose.Words’u içe aktarın ve belgeyi açın

İlk adım, `aspose.words` paketini (genellikle `aw` takma adıyla) içe aktarmak ve kaynak belgeyi yüklemektir.

```python
import aspose.words as aw

# Load the Word document from the file system
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

*Bu neden önemlidir*: Belgeyi açmak, şekillerin bulunduğu düğüm ağacına erişmenizi sağlar. `aw.Document` sınıfı, sonraki tüm manipülasyonların giriş noktasıdır.

## Adım 2: İlk şekli bulun (iç içe düğümler dahil)

Şekiller, bir `Paragraph`ın doğrudan çocuğu olabileceği gibi diğer kapsayıcıların (tablolar gibi) içinde de bulunabilir. `is_deep` bayrağı `True` olarak ayarlandığında, iç içe olsalar bile ilk şekli almanızı sağlar.

```python
# Retrieve the first shape in the document, searching recursively
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape before applying a shadow.")
```

*Bu neden önemlidir*: `add shape shadow` işlemi bir `Shape` nesnesi gerektirir. Derin arama, tabloların veya grup kapsayıcıların içinde gizli kalan şekilleri kaçırmanızı önler.

## Adım 3: Gölgeyi etkinleştirin ve temel özellikleri ayarlayın

Aspose.Words bir gölgeyi birkaç özellik ile temsil eder. İlk olarak, `shadow_visible` değerini `True` yaparak gölgeyi açın.

```python
# Enable the shadow effect
shape.shadow_visible = True
```

Şimdi bulanıklık yarıçapını, ofsetleri ve rengi yapılandırabilirsiniz.

## Adım 4: Şekle bulanıklık uygulayın ve ofset değerlerini tanımlayın

Bulanıklık yarıçapı, gölgenin ne kadar yumuşak görüneceğini kontrol eder. `5.0` değeri, belirgin ama aşırı olmayan bir bulanıklık verir. Ofsetler gölgeyi yatay ve dikey olarak hareket ettirir.

```python
# Apply blur to shape – this is the "apply blur to shape" part
shape.shadow_blur = 5.0          # Blur radius in points

# Define horizontal (X) and vertical (Y) offsets
shape.shadow_offset_x = 2.0     # Move shadow 2 points to the right
shape.shadow_offset_y = 2.0     # Move shadow 2 points down
```

*Bu neden önemlidir*: `shadow_blur` ve ofset değerlerini ayarlamak, belgenizin görsel stiline uygun gerçekçi derinlik efektleri oluşturmanızı sağlar.

## Adım 5: Gölge rengini seçin (özel renk ile şekle gölge ekleme)

Herhangi bir `aw.Color` kullanabilirsiniz. Burada siyahı seçiyoruz, ancak `aw.Color.red`, `aw.Color.from_argb(255, 0, 120, 215)` gibi değerlerle değiştirebilirsiniz.

```python
# Set the shadow color – black in this example
shape.shadow_color = aw.Color.black
```

*Bu neden önemlidir*: Renk, gölgenin çevredeki içerikle nasıl etkileşeceğini belirler. Daha koyu gölgeler açık arka planlarda daha görünürken, açık tonlar koyu sayfalarda daha iyi çalışır.

## Adım 6: Güncellenen belgeyi kaydedin

Son olarak, değişiklikleri diske yazın. Orijinal dosyanın üzerine yazabilir ya da yeni bir dosya oluşturabilirsiniz.

```python
output_path = "YOUR_DIRECTORY/output_with_shadow.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

`output_with_shadow.docx` dosyasını Microsoft Word’de açtığınızda, ilk şekil belirtilen bulanıklık ve ofsetle yumuşak bir siyah gölge gösterecektir.

## Tam, çalıştırılabilir örnek

Her şeyi bir araya getirerek, hemen çalıştırabileceğiniz bağımsız bir betik aşağıdadır:

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str,
                              blur: float = 5.0,
                              offset_x: float = 2.0,
                              offset_y: float = 2.0,
                              color: aw.Color = aw.Color.black) -> None:
    """
    Loads a Word document, finds the first shape (deep search),
    and applies a shadow effect.

    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified document will be saved.
    blur : float, optional
        Blur radius for the shadow. Default is 5.0 points.
    offset_x : float, optional
        Horizontal offset of the shadow. Default is 2.0 points.
    offset_y : float, optional
        Vertical offset of the shadow. Default is 2.0 points.
    color : aw.Color, optional
        Shadow color. Default is black.
    """
    # Load the document
    doc = aw.Document(input_path)

    # Retrieve the first shape, searching recursively
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape before calling this function.")

    # Enable shadow and configure its appearance
    shape.shadow_visible = True
    shape.shadow_blur = blur
    shape.shadow_offset_x = offset_x
    shape.shadow_offset_y = offset_y
    shape.shadow_color = color

    # Save the result
    doc.save(output_path)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output_with_shadow.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
```

**Beklenen çıktı**: `output_with_shadow.docx` dosyasını açtığınızda, ilk şekil yatay ve dikey olarak 2 pt ofsetlenmiş, bulanık bir siyah gölge ile gösterilir; bu, gönderdiğiniz parametrelerle eşleşir.

## Birden fazla şekil ve kenar durumlarıyla başa çıkma

### İsme göre belirli bir şekle gölge ekleme

Belgenizde birden fazla şekil varsa, `name` özelliğiyle birini hedeflemek isteyebilirsiniz:

```python
target_name = "MyRectangle"
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)  # start with first shape
while shape is not None and shape.name != target_name:
    shape = shape.next_sibling(aw.NodeType.SHAPE)

if shape is None:
    raise ValueError(f"Shape named '{target_name}' not found.")
```

### Görsel olmayan düğümleri atlama

Bazen bir şekil düğümü, görsel içeriği olmayan bir yer tutucu (ör. çizim kanvası) olabilir. Gölgeyi uygulamadan önce `shape.is_image` veya `shape.is_picture_frame` kontrolü yaparak bunu önleyin.

```python
if not shape.is_image and not shape.is_picture_frame:
    # Proceed only if the shape can display a shadow
    shape.shadow_visible = True
```

### Gruplandırılmış şekillerle çalışma

Şekiller gruplandırıldığında, grup kendisi bir `Shape` düğümüdür. Her üye için gölge uygulamak amacıyla `shape.get_child_nodes(aw.NodeType.SHAPE, True)` üzerinden döngü yapın.

```python
if shape.is_group:
    for child in shape.get_child_nodes(aw.NodeType.SHAPE, True):
        child.shadow_visible = True
        child.shadow_blur = blur
        child.shadow_offset_x = offset_x
        child.shadow_offset_y = offset_y
        child.shadow_color = color
```

Bu varyasyonlar, kodunuzun farklı belge düzenlerinde sağlam çalışmasını sağlar.

## Mükemmel gölgeler için profesyonel ipuçları

- **Tutarlılık**: Raporunuzdaki tüm şekiller için aynı bulanıklık yarıçapını ve ofseti kullanarak görsel dili tutarlı tutun.
- **Performans**: Yüksek çözünürlüklü yüzlerce resme gölge uygulamak dosya boyutunu artırabilir. Daha sonra PDF üretmeyi planlıyorsanız çıktı boyutunu test edin.
- **Renk kontrastı**: Koyu sayfa arka planlarında, görünürlüğü korumak için daha açık bir gölge (`aw.Color.gray`) düşünün.
- **Önizleme**: Word’ün “Shadow” arayüzü Aspose.Words özelliklerini yansıtır; bu yüzden önce manuel olarak deneyebilir, ardından elde edilen değerleri betiğinize kopyalayabilirsiniz.

## Sonuç

Artık Aspose.Words for Python kullanarak bir Word belgesine **şekle gölge eklemenin** nasıl yapılacağını biliyorsunuz. Rehber, bir şeklin bulunması, gölgenin etkinleştirilmesi, **add shape shadow** ile özel bulanıklık, ofset ve renk ayarları ve sonucun kaydedilmesini kapsadı. Yukarıdaki yeniden kullanılabilir fonksiyonla bu efekti herhangi bir belge‑oluşturma hattına entegre edebilirsiniz.

### Sıradaki adım?

- **apply blur to shape** özelliğini, parıltı veya yumuşak kenarlar gibi diğer efektler için keşfedin.
- Gölgeyi **shape borders** veya **reflection** ile birleştirerek daha zengin grafikler oluşturun.
- Düzenlenmiş belgeyi dağıtım için PDF’ye dönüştürün (`doc.save("output.pdf", aw.SaveFormat.PDF)`).

Farklı renkler, bulanıklık seviyeleri ve ofset değerleriyle deney yapmaktan çekinmeyin; böylece kurumsal kimliğinize uygun sonuçlar elde edersiniz. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımları keşfetmeniz için adım‑adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words Şekil Gölge Öğreticisi – C#'ta Word Şekline Gölge Ekleme](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Aspose.Words ile Word'de Dikdörtgen Şekil Oluşturma – Adım‑adım kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words for .NET Kullanarak Word Belgesinde Grup Şekli Oluşturma](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}