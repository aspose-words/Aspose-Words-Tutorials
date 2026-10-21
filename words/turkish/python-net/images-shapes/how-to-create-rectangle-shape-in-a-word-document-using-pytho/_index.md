---
category: general
date: 2026-09-30
description: Aspose.Words for Python kullanarak dikdörtgen şekli oluşturmayı, şekle
  gölge eklemeyi ve şekilli Word belgesini kaydetmeyi öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: tr
lastmod: 2026-09-30
og_description: Word belgesinde hızlıca dikdörtgen şekli oluşturun. Bu eğitim, şekil
  eklemeyi, şekle gölge uygulamayı, gölge bulanıklığını ayarlamayı ve şekilli Word
  belgesini kaydetmeyi gösterir.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Python ile Word’de dikdörtgen şekli oluşturma – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Python kullanarak bir Word belgesinde dikdörtgen şekli nasıl oluşturulur
url: /tr/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python kullanarak bir Word belgesinde dikdörtgen şekli oluşturma

Bir Word dosyasında **dikdörtgen şekli oluşturmanız** gerekiyorsa, bu kılavuz size tam, çalıştırılabilir bir çözüm gösterir. Şekli nasıl ekleyeceğinizi, gölge etkisini nasıl uygulayacağınızı, bulanıklığı nasıl ayarlayacağınızı ve sonunda **şekilli Word belgesini kaydetmeyi** öğreneceksiniz; böylece sonuç Microsoft Word ya da uyumlu bir görüntüleyicide açılabilir.

Örnek, **Aspose.Words for Python via .NET** kütüphanesini kullanır; bu kütüphane Microsoft Office yüklü olmadan Word belgelerini manipüle etmenizi sağlar. API hakkında önceden bir deneyime ihtiyacınız yoktur—sadece temel Python bilgisi yeterlidir.

## Neler elde edeceksiniz

- Yeni bir belgenin ilk bölümüne bir dikdörtgen eklemek.  
- Bulanıklık, kaydırma ve renk ayarlarıyla yumuşak bir gölge yapılandırmak.  
- Belgeyi diske kaydetmek ve görsel sonucu doğrulamak.

## Önkoşullar

- Python 3.8 ve üzeri.  
- `aspose-words` paketi yüklü (`pip install aspose-words`).  
- Çıktı dizinine yazma izni.

## Dikdörtgen şekli oluşturma ve görünümünü yapılandırma

İlk adım, boş bir belge oluşturup içine bir dikdörtgen şekli eklemektir. Şekil, gölge etkisinin uygulanacağı bir tuval görevi görür.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Neden önemli:**  
Dikdörtgen oluşturmak, daha sonra stil verebileceğiniz somut bir nesne (`shape`) sağlar. Açık boyutlar belirlemek, şeklin her platformda aynı görünmesini garantiler.

## Word belgesine şekil ekleme

Yukarıdaki kod zaten dikdörtgeni ekliyor, ancak ileride ek şekiller (ör. daire, ok) eklemeniz gerekebilir. Aynı desen geçerlidir: belgenin gövdesinde `append_child` metodunu çağırın ve istenen `ShapeType` değerini iletin.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**İpucu:** Desteklenen tüm şekilleri keşfetmek için `ShapeType` enum’ını kullanın. Bu, kodun okunabilirliğini artırır ve “sihirli sayılar” kullanımını önler.

## Şekle gölge uygulama ve gölge bulanıklığını ayarlama

Gölge, derinlik ve görsel ilgi katar. `ShadowEffect` sınıfı, bulanıklık, kaydırma ve rengi kontrol etmenizi sağlar. Aşağıda dikdörtgene yumuşak bir siyah gölge uyguluyoruz.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Neden bulanıklık ayarlamalısınız?**  
`blur` gölgenin ne kadar dağınık görüneceğini belirler. Düşük bir değer (ör. 1.0) keskin bir kenar verirken, yüksek bir değer (ör. 5.0) nazik bir geçiş oluşturur; bu genellikle daha estetik bir görünüm sağlar.

**Köşe durumu:** `blur` değerini 0 yaparsanız gölge katı bir siluet olur. Bazı görüntüleyiciler bunu aliasing artefaktlarıyla gösterebilir; bu yüzden daha pürüzsüz bir çıktı için 0’dan büyük bir değer seçin.

## Şekilli Word belgesini kaydetme

Belgeyi kaydetmek, tüm değişiklikleri kalıcı hâle getirir. `save` metodu, modern bir Word işlemcisiyle açılabilen bir `.docx` dosyası yazar.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

`output.docx` dosyasını açtığınızda, sol‑üst köşeden bir inç uzaklıkta konumlandırılmış bir dikdörtgen ve sağa ve aşağıya iki puan kaydırılmış yumuşak bir siyah gölge göreceksiniz. Gölgenin bulanıklığı, şeklin sayfadan yükselmiş gibi görünmesini sağlar.

**Profesyonel ipucu:** Döngü içinde birçok belge üretmeniz gerekiyorsa, aynı `Document` örneğini yeniden kullanın ve yinelemeler arasında gövdesini temizleyerek bellek kullanımını azaltın.

## Yaygın varyasyonlar ve sorun giderme

| Durum | Değiştirilecek şey | Sebep |
|-----------|----------------|--------|
| Farklı gölge rengi | `shadow.color = aw.Color.red` | Marka renklerini kullanın veya önemli şekilleri vurgulayın. |
| Daha büyük gölge kaydırması | `shadow.offset_x`/`shadow.offset_y` değerlerini artırın | UI mock‑up’larda derinliği vurgulamak için. |
| Gölge yok | `shape.shadow = shadow` satırını kaldırın | Minimalist raporlar için kullanışlı. |
| DOCX yerine PDF dışa aktar | `doc.save("output.pdf")` | PDF, yalnızca okunabilir dağıtım için idealdir. |

Şekil görünmüyorsa, doğru bölüme (`get_first_section()`) eklediğinizden ve değişikliklerden sonra belgenin kaydedildiğinden emin olun.

## Tam, çalıştırılabilir örnek

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Betik çalıştırıldığında `output.docx` içinde yumuşak gölgeli bir dikdörtgen oluşturulur. Dosyayı Microsoft Word’de açarak görsel etkinin açıklamaya uygun olduğunu doğrulayın.

## Sonuç

Artık **dikdörtgen şekli oluşturma**, **Word belgesine şekil ekleme**, **şekle gölge uygulama**, **gölge bulanıklığını ayarlama** ve son olarak **şekilli Word belgesini kaydetme** konularını Aspose.Words for Python kullanarak biliyorsunuz. Aynı desen, diğer şekil tipleri, renkler ve efektler için de genişletilebilir; böylece Office otomasyonuna ihtiyaç duymadan belge grafikleri üzerinde tam kontrol elde edersiniz.

**Sonraki adımlar**

- `Shape.fill` özelliğiyle degrade ya da resim arka planları ekleyin.  
- `Paragraph` nesnelerini kullanarak dikdörtgenin içine metin yerleştirin.  
- Birden fazla şekli birleştirerek karmaşık diyagramlar oluşturun, ardından dağıtım için PDF’ye dışa aktarın.  

Kodu kendi raporlama veya şablonlama ihtiyaçlarınıza göre uyarlamaktan çekinmeyin ve sonuçlarınızı yorumlarda paylaşın!

## Sonra Ne Öğrenmelisiniz?


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım‑adım açıklamalarla tam çalışan kod örnekleri içerir.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}