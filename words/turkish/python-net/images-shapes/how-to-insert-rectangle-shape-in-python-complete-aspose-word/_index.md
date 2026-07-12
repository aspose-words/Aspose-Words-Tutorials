---
category: general
date: 2026-06-27
description: Aspose.Words ile Python'da dikdörtgen şekil eklemeyi, gölge rengini değiştirmeyi,
  dış gölge eklemeyi ve şekle gölge efekti uygulamayı tek bir öğreticide öğrenin.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: tr
og_description: Python’da dikdörtgen şekli eklemeyi, gölge rengini değiştirmeyi, dış
  gölge eklemeyi ve Aspose.Words ile şekle gölge efekti uygulamayı öğrenin.
og_title: Python'da Dikdörtgen Şekli Nasıl Ekleyeceksiniz – Aspose.Words Öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Python'da Dikdörtgen Şekli Nasıl Eklenir – Tam Aspose.Words Rehberi
url: /tr/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python’da Dikdörtgen Şekil Nasıl Eklenir – Tam Aspose.Words Kılavuzu

Hiç **dikdörtgen şekil ekleme** yöntemini Python ile bir Word belgesine nasıl ekleyeceğinizi merak ettiniz mi? Tek başınıza değilsiniz—birçok geliştirici rapor otomasyonu ya da şablon oluştururken bu sorunu yaşıyor. İyi haber şu ki Aspose.Words bu işlemi çocuk oyuncağı haline getiriyor ve bu öğreticide, dikdörtgeni çizmeyi ve ona şık bir dış gölge eklemeyi adım adım göstereceğiz.

Ayrıca **gölge rengini nasıl değiştirirsiniz**, **dış gölgeyi nasıl eklersiniz** ve son adım olarak **gölge efektini şekle nasıl uygularsınız** konularını da ele alacağız. Sonunda, programlı bir şekilde herhangi bir .docx dosyasına ekleyebileceğiniz tamamen stilize bir dikdörtgene sahip olacaksınız.

## Önkoşullar

- Makinenizde Python 3.8+ yüklü  
- `pip install aspose-words` ile Aspose.Words for Python  
- Python betikleme konusunda temel bilgi (derin Word‑API bilgisi gerekmez)  

Eğer bunlara sahipseniz harika—hadi başlayalım. Yoksa önce kütüphaneyi edinin; rehberin geri kalanı import’in sorunsuz çalıştığını varsayar.

## Aspose.Words for Python ile Dikdörtgen Şekil Nasıl Eklenir

İlk adım, birincil anahtar kelimenin vaat ettiği gibi: **dikdörtgen şekil ekleme**. Yeni bir belge oluşturacağız, bir `DocumentBuilder` başlatacağız ve sayfaya bir dikdörtgen bırakacağız.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Neden önemli:** `insert_shape` çağrısı *dikdörtgen şekil ekleme* işleminin çekirdeğidir. Bir `Shape` nesnesi döndürür; bu nesneyi daha sonra boyut, konum, dolgu, kenarlık gibi özelliklerle manipüle edebilirsiniz. Ayrıca bir `fill_color` ayarladık; bunu yapmazsanız gölge beyaz sayfada kaybolabilir ve görülmesi zorlaşır.

### Pro ipucu
Dikdörtgeni belirli bir konuma yerleştirmeniz gerekiyorsa, eklemeden önce `builder.move_to` kullanın ya da oluşturduktan sonra `rectangle.left` ve `rectangle.top` değerlerini ayarlayın.

## Bir Şeklin Gölge Rengini Değiştirme

Şimdi dikdörtgen belge içinde, **gölge rengini nasıl değiştirirsiniz** sorusuna bakalım. Aspose.Words bir `ShadowEffect` nesnesi sunar; bu nesnenin `color` özelliğine istediğiniz RGB değerini atayabilirsiniz.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Neden bunu istersiniz:** Koyu siyah bir gölge özellikle açık renkli belgelerde çok sert görünebilir. Rengi ayarlamak, kurumsal renklerle eşleşmenizi ya da daha yumuşak bir görsel etki elde etmenizi sağlar.

### Kenar durumu
`shadow.opacity` ayarlamayı unutursanız, varsayılan tamamen opaktır ve gölge katı bir şekil gibi görünür. Renk değişikliğini uygun bir opaklık seviyesiyle birlikte kullanın.

## Dış Gölge Efekti Ekleme

Birçok kişinin bir sonraki sorusu **dış gölge nasıl eklenir**. `ShadowStyle.OUTER` bayrağı, Aspose.Words’a gölgeyi şeklin dış hatları boyunca render etmesini söyler, iç kısmında değil.

Yukarıdaki kod parçacığı zaten `ShadowStyle.OUTER` kullanıyor, ancak açıklık getirmek için bu ayarı ayrı bir örnekle gösterelim:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

`ShadowStyle.INNER`a geçerseniz gölge *dikdörtgenin içinde* görünür; bu, kabartma efektleri için faydalıdır. Çoğu belge‑tasarım senaryosunda dış stil, doğal bir drop‑shadow görünümü verir.

## Gölge Efektini Şekle Uygulama

`rectangle.shadow = shadow` atamasıyla **gölge efektini şekle uyguladık**. Şimdi her şeyi birleştirip belgeyi kaydedelim ve etkinin kalıcı olduğunu doğrulayalım.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

`RectangleWithShadow.docx` dosyasını Microsoft Word’de açtığınızda, hafif mavi bir dikdörtgenin 45° açıyla hafif bulanık ve kaydırılmış gri bir dış gölgesi olduğunu görmelisiniz. Gölge, tam olarak yapılandırdığımız gibi olacaktır.

### Yaygın hatalar
- **Klasör eksik:** `doc.save` klasör yoksa hata verir. Önce klasörü oluşturun ya da `os.makedirs` kullanın.  
- **Sürüm uyumsuzluğu:** Gölge API’si Aspose.Words 22.9+ gerektirir; eski sürümler gölge ayarlarını sessizce yok sayar.

## Tam Çalışan Örnek

Aşağıda, tüm adımları birleştiren, çalıştırmaya hazır tam betik yer alıyor. `rectangle_shadow.py` adlı bir dosyaya kopyalayıp `python rectangle_shadow.py` komutuyla çalıştırın.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Beklenen çıktı:** Tek bir dikdörtgen ve gri bir dış gölge içeren bir Word belgesi (`RectangleWithShadow.docx`). Görsel etkiyi doğrulamak için Word’de açın.

## Sık Sorulan Sorular

| Soru | Cevap |
|------|-------|
| *Farklı bir şekil tipi kullanabilir miyim?* | Kesinlikle—`ShapeType.RECTANGLE` yerine `ShapeType.OVAL`, `ShapeType.TRIANGLE` vb. kullanın, aynı gölge mantığı geçerli olur. |
| *Daha kalın bir kenarlık istiyorum?* | Gölgeyi uygulamadan önce `rectangle.line_width = 2.0` (point) ayarlayın. |
| *Gölgeyi animasyonlu yapabilir miyim?* | Aspose.Words ile doğrudan mümkün değil; animasyon için HTML/CSS’ye dışa aktarmanız gerekir. |
| *Bu macOS’ta çalışır mı?* | Evet—Python çalıştığı sürece Aspose.Words platform‑bağımsızdır. |

## Sonuç

**Dikdörtgen şekil ekleme**, **gölge rengini değiştirme**, **dış gölge ekleme** ve **gölge efektini şekle uygulama** konularını Aspose.Words for Python ile adım adım gösterdik. Tam script, herhangi bir otomasyon hattına kolayca eklenebilir ve saniyeler içinde profesyonel görünümlü bir dikdörtgen ve cilalı bir gölge sağlar.

Bir sonraki adım için hazır mısınız? Dolgu rengini değiştirin, farklı `direction` açıları deneyin ya da aynı sayfaya birden fazla şekil ekleyin. Ayrıca Aspose.Words’ün zengin metin‑formatlama API’sini keşfederek gölgeleri stilize metinle birleştirebilir, göz alıcı raporlar oluşturabilirsiniz.

Bu öğreticiyi faydalı bulduysanız beğenin, ekip arkadaşlarınızla paylaşın ya da kendi varyasyonlarınızı yorum olarak bırakın. İyi kodlamalar!

![Diagram showing how to insert rectangle shape with an outer shadow applied in a Word document](/images/rectangle-shadow.png)


## Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve ilgili konuları derinlemesine ele alan kaynaklardır. Her biri, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımları keşfetmeniz için adım adım kod örnekleri içerir.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}