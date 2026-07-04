---
category: general
date: 2026-05-04
description: Aspose.Words for Python kullanarak dikdörtgen şekli oluşturmayı, gölgeli
  şekil eklemeyi, gölge rengini değiştirmeyi, gölge mesafesini ayarlamayı ve belgeyi
  PDF olarak kaydetmeyi öğrenin.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: tr
og_description: Aspose.Words for Python ile dikdörtgen şekli oluşturun, şekil eklemeyi,
  gölge rengini değiştirmeyi, gölge mesafesini ayarlamayı öğrenin ve belgeyi PDF olarak
  kaydedin.
og_title: Dikdörtgen şekli oluştur – Gölge ekle, Rengi değiştir ve PDF olarak kaydet
tags:
- Aspose.Words
- Python
- PDF generation
title: Python'da dikdörtgen şekli oluşturma – Gölge ekleme ve PDF olarak kaydetme
  tam rehberi
url: /tr/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dikdörtgen şekli oluşturma – Python Geliştiricileri için Tam Kılavuz

Word belgesinde **create rectangle shape** ihtiyacı hiç duydunuz mu ve ona cilalı bir gölge nasıl eklenir merak ettiniz mi? Belki bir rapor oluşturucu geliştiriyorsunuz ve görsel şıklık önem taşıyor—özellikle son çıktı bir PDF olduğunda. İyi haber? Aspose.Words for Python ile sadece **how to add shape** değil, aynı zamanda gölgenin renginden mesafesine kadar her özelliğini ayarlayabilir ve ardından **save document as pdf** tek bir akıcı adımda yapabilirsiniz.

Bu rehberde tüm süreci adım adım inceleyeceğiz. Kopyalayıp‑yapıştırabileceğiniz tam kodu göreceksiniz, her satırın *neden* önemli olduğunu anlayacaksınız ve kenar durumlarını (örneğin şeffaf gölgeler veya standart dışı DPI) ele almak için birkaç ipucu öğreneceksiniz. Sonunda **create rectangle shape**, gölgesini özelleştirme ve ter dökmeksizin net bir PDF dışa aktarma yeteneğine sahip olacaksınız.

## Önkoşullar

- Python 3.8+ makinenizde kurulu.  
- `pip install aspose-words` ile Aspose.Words for Python.  
- Nesne‑yönelimli Python hakkında temel bilgi (fazla bir şey değil).  

Eğer zaten bir sanal ortam kurduysanız, sadece kurulum komutunu çalıştırın ve hazırsınız.

## Adım 1: Belge ve Builder'ı Başlatma

Şekil eklemeden (**how to add shape**) önce, üzerinde çalışabileceğiniz boş bir belgeye ihtiyacınız var. `Document` sınıfı tüm dosyayı temsil eder ve `DocumentBuilder` sizin fırçanızdır.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Neden önemli:* `Document` tüm bölümleri, sayfaları ve kaynakları tutar. `DocumentBuilder` içeriği tam istediğiniz yere eklemenizi sağlayan akıcı bir API sunar—bir kelime işlemcideki imleç gibi düşünün.

## Adım 2: Dikdörtgen Şekli Ekleme

Şimdi gerçekten **how to add shape** yapıyoruz. `insert_shape` yöntemi şekil tipini ve boyutlarını (puan cinsinden) gerektirir. Burada 200 × 100 pt bir dikdörtgen seçiyoruz ve ona açık mavi bir dolgu veriyoruz.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Pro ipucu:* Şeklin mevcut metinle hizalanması gerekiyorsa, eklemeden önce `builder.move_to` kullanın veya oluşturulduktan sonra `left`/`top` özelliklerini ayarlayın.

## Adım 3: Gölgeyi Açma

Gölgesi olmayan bir şekil düz görünür. **set shadow distance** yapmak ve efekti görünür kılmak için gölge formatını alın ve etkinleştirin.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Neden bu adım:* Gölge formatı ayrı bir nesnedir; `visible` özelliğini açmak yapmanız gereken ilk şeydir, aksi takdirde diğer gölge özellikleri yok sayılır.

## Adım 4: Gölgeyi Stilize Etme – Renk, Bulanıklık, Mesafe, Yön

Burası sihrin gerçekleştiği yer. **change shadow color** yapacağız, bulanıklık yarıçapını ayarlayacağız, gölgenin dikdörtgenden ne kadar uzakta duracağını belirleyecek ve 45° döndüreceğiz.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Her özelliğin açıklaması:*

| Property | Ne işe yarar | Tipik değerler |
|----------|--------------|----------------|
| `style` | Gölgenin *inner* (iç) ya da *outer* (dış) olmasını belirler. | `OUTER` (en yaygın) |
| `blur_radius` | Yumuşaklığı kontrol eder; yüksek değer = daha bulanık kenarlar. | 0–20 px genellikle |
| `distance` | Gölgenin şekilden ne kadar kaydırıldığını belirler. | 0–10 pt ince için, >10 dramatik için |
| `direction` | Işık kaynağının açısı, x‑ekseninden saat yönünde ölçülür. | 0‑360° |
| `color` | Gölge rengi. | Herhangi bir `aw.Color` (ör. `gray`, `dark_red`) |

*Köşe durumu:* `distance` değerini `0` yaparsanız gölge şeklin tam altında oturur ve şeklin dolgusunu etkili bir şekilde gizler. Görünür bir kaydırma için `0`'ın üzerinde tutun.

## Adım 5: Belgeyi PDF Olarak Kaydetme

Son olarak, **save document as pdf** yapıyoruz. Aspose.Words gölgeyi otomatik olarak rasterleştirir, böylece PDF Word görünümüyle tam aynı görünür.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Neden PDF?* PDF'ler düzeni platformlar arasında korur, bu da onları raporlar, faturalar veya herhangi bir yazdırılabilir belge için mükemmel kılar.

---

![Gölgeyle dikdörtgen şekli oluşturma](https://example.com/images/rectangle-shadow.png){: .align-center alt="gölgeyle dikdörtgen şekli oluşturma örneği"}

*Yukarıdaki görsel, son PDF çıktısını gösterir – hafif mavi bir dikdörtgen ve yumuşak gri dış gölge, tam olarak yapılandırdığımız gibi.*

## Yaygın Sorular & Varyasyonlar

### **transparent** bir gölgeye ihtiyacım olsaydı ne olur?

Gölge renginin alfa kanalını ayarlayın:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Aynı gölgeyi birden fazla şekle uygulayabilir miyim?

Evet. Bir şekilden `ShadowFormat`'ı çıkarın ve diğerine atayın:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### **different shape type** için gölgeyi nasıl değiştiririm?

Tüm şekil tipleri aynı `ShadowFormat` özelliklerini paylaşır, bu yüzden aynı yapılandırma bloğunu yeniden kullanabilirsiniz—sadece `ShapeType.RECTANGLE` yerine `ShapeType.OVAL`, `ShapeType.TRIANGLE` vb. koyun.

### Baskı için **high‑resolution PDFs** ne olacak?

`PdfSaveOptions`'ı daha yüksek DPI ile belirtin:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Özet

Artık **create rectangle shape**, **how to add shape**, gölgenin **shadow colour** özelleştirme, **set shadow distance** ayarlama ve sonunda **save document as pdf** yapmanız için gereken her şeyi ele aldık. Tam, çalıştırılabilir betik şöyle görünüyor:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Betik çalıştırın, ortaya çıkan `ShadowedShape.pdf` dosyasını açın ve ince bir gri gölgeyle net bir dikdörtgen göreceksiniz—profesyonel bir rapordan bekleyeceğiniz tam olarak bu.

## Sonra Ne?

- **Diğer şekil tiplerini keşfedin** (`ShapeType.OVAL`, `ShapeType.LINE`) belgelerinizi zenginleştirmek için.  
- **Birden fazla gölgeyi birleştirin** şekilleri katmanlayarak; parlak bir renk ile iç gölge kullanarak “parıltı” efekti bile oluşturabilirsiniz.  
- **Toplu işleme otomatikleştirin**: veri satırları koleksiyonunda döngü oluşturun, satır başına bir şekil üretin ve her şeyi tek bir PDF'de birleştirin.  
- **Diğer Aspose kütüphaneleriyle bütünleştirin** (ör. Aspose.Slides) aynı görseli PowerPoint'e aktarmanız gerektiğinde.

Denemekten çekinmeyin—`blur_radius`'ı değiştirin, `direction` ile oynayın veya `gray`'i marka‑özel bir renkle değiştirin. API o kadar esnek ki birkaç ayar görsel etkiyi büyük ölçüde değiştirebilir.

Sorularınız veya zor bir senaryonuz mu var? Aşağıya yorum bırakın ya da Aspose topluluk forumlarında soruyu yöneltin. Kodlamanın tadını çıkarın ve o güzel gölgeli dikdörtgenlerin keyfini çıkarın!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}