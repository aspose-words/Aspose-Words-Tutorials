---
category: general
date: 2026-06-21
description: Aspose.Words kullanarak Python'da dikdörtgen şekil oluşturun. Şekle gölge
  eklemeyi, şekil dolgu rengini ayarlamayı ve belgeyi dakikalar içinde PDF olarak
  kaydetmeyi öğrenin.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: tr
og_description: Python ile Aspose.Words kullanarak dikdörtgen şekli oluşturun. Bu
  kılavuz, şekle gölge eklemeyi, şekil dolgu rengini ayarlamayı ve belgeyi PDF olarak
  kaydetmeyi gösterir.
og_title: Python'da dikdörtgen şekli oluşturma – Aspose.Words öğreticisi
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Python'da dikdörtgen şekli oluşturma – Aspose.Words öğreticisi
url: /tr/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python’da Dikdörtgen Şekil Oluşturma – Aspose.Words öğreticisi

Python’da kod yazarken bir Word belgesinde **dikdörtgen şekil nasıl oluşturulur** diye hiç merak ettiniz mi? Tek başınıza değilsiniz. Birçok geliştirici, renkli bir kutu ve hafif bir gölge gibi hızlı bir görsel öğeye ihtiyaç duyduklarında ve ardından tüm belgeyi PDF olarak dışa aktarmak istediklerinde bir engelle karşılaşıyor.

Bu rehberde, **dikdörtgen şekil oluşturur**, **şekil dolgu rengini ayarlar**, **şekle gölge ekler** ve sonunda **belgeyi PDF olarak kaydeder** tam, çalıştırılabilir bir örnek üzerinden adım adım ilerleyeceğiz. Belirsiz referanslar yok, sadece bugün kopyalayıp yapıştırıp çalıştırabileceğiniz somut kod.

## Gereksinimler

- Python 3.8 ve üzeri (kullandığımız sözdizimi herhangi bir yeni sürümde çalışır).
- Aktif bir Aspose.Words for Python lisansı veya ücretsiz deneme (kütüphane saf‑Python’dur, COM etkileşimi gerekmez).
- Kullanım rahatlığı sağlayan bir metin editörü veya IDE—VS Code harika çalışır, ama herhangi biri yeterlidir.

Hepsi bu. Ağır çerçeveler yok, ek OS‑seviyesi bağımlılıklar yok. Hadi başlayalım.

## Adım 1: Aspose.Words for Python’ı Kurun

İlk olarak. Henüz yapmadıysanız, paketi PyPI’dan indirin:

```bash
pip install aspose-words
```

Bu adımın önemi: Aspose.Words, reliance edeceğimiz `Document` ve `DocumentBuilder` sınıflarını sağlar. Kütüphane olmadan, `insert_shape` gibi sonraki çağrılar mevcut olmaz, bu yüzden script bir satır bile çizmeye çalışmadan önce çökebilir.

> **Pro ipucu:** Sanal ortamınızı düzenli tutun. Kurulumdan önce `python -m venv .venv && source .venv/bin/activate` komutunu çalıştırın, böylece kütüphane sistem paketlerinden izole kalır.

## Adım 2: Yeni Bir Document ve DocumentBuilder Oluşturun

Şimdi gerçekten **dikdörtgen şekil oluşturuyoruz** – ama önce boş bir tuvale ihtiyacımız var.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

`Document` nesnesi tüm dosyayı temsil eder, `DocumentBuilder` ise imlecin nerede olduğunu bilen ve o noktaya öğeler ekleyebilen kullanışlı bir yardımcıdır. Builder’ı sayfaya yazan bir kalem olarak düşünün.

## Adım 3: Dikdörtgen Şekli Ekle

İşte asıl eylemin gerçekleştiği yer. Sabit bir genişlik ve yükseklikte **dikdörtgen şekil oluşturacağız**, ardından sayfada konumlandıracağız.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Neden dikdörtgen? Dolgu renkleri ve gölgeleri sergileyebilen en basit şekildir. Daha sonra bir daire ya da yıldız ihtiyacınız olursa, sadece `ShapeType.RECTANGLE` değerini başka bir enum değeriyle değiştirin.

## Adım 4: Şekil Dolgu Rengini Ayarla

Düz beyaz bir kutu pek heyecan verici değil, bu yüzden **şekil dolgu rengini** hafif bir şeye ayarlayalım—raporlar için açık mavi iyi bir seçimdir.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Önceden tanımlı `aw.Color` üyelerinden (`red`, `green`, `dark_gray` vb.) herhangi birini kullanabilir veya bir RGB demeti geçirebilirsiniz (`aw.Color.from_argb(255, 30, 144, 255)`). Dolgu rengi, gölge veya kenarlık uygulanmadan önce kullanıcının gördüğü şeydir.

## Adım 5: Şekle Gölge Ekle

Şimdi görsel son dokunuş: **şekle gölge ekle**. Gölge derinlik kazandırır ve dikdörtgenin sayfada öne çıkmasını sağlar.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Gölge nasıl eklenir**? Yukarıdaki kod tam olarak bunu yapar, ancak her bir özelliğin neden önemli olduğunu inceleyelim:

- `visible` – efekti açar/kapatır.
- `color` – rengi tanımlar; koyu gri doğal aydınlatmayı taklit eder.
- `blur` – yüksek değerler daha yumuşak bir kenar üretir.
- `offset_x` / `offset_y` – gölgeyi şekilden uzaklaştırır; farklı ışık açılarını taklit etmek için bunları ayarlayın.
- `transparency` – 0 katıdır, 1 görünmez; 0.2 hafif bir izlenim verir.
- `type` – `OUTER` gölgeyi şeklin dışına atar, `INNER` ise içine yerleştirir.

Eğer dramatik bir düşen gölgeye ihtiyacınız olursa, `blur` değerini 10‑15’e yükseltin ve `offset_x`/`offset_y` değerlerini 6‑8’e çıkarın.

## Adım 6: Belgeyi PDF Olarak Kaydet

Tüm bu çalışma, **belgeyi PDF olarak kaydedip** paylaşamazsak anlamsızdır. Aspose.Words bunu tek satırda yapar:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Neden PDF? PDF’ler platformlar arasında düzeni korur, bu da onları raporlar, faturalar veya herhangi bir yazdırılabilir materyal için ideal kılar. `save` metodu dosya uzantısını otomatik olarak algılar ve doğru formatı seçer—yolun `.pdf` ile bittiğinden emin olun.

### Beklenen Sonuç

`ShapeWithShadow.pdf` dosyasını açtığınızda, ilk sayfanın üst kısmına yakın bir konumda, hafif bir koyu gri gölgeyle sağa ve aşağıya biraz kaydırılmış açık mavi bir dikdörtgen görmelisiniz. Şeklin kenarları net, gölge hafif ve dosya boyutu genellikle 100 KB’nın altındadır.

## Bonus: Gölge Ayarları – “gölge nasıl eklenir” sorusunun yanıtları

Şöyle düşünebilirsiniz, *“Şekli hareket ettirmeden gölge yönünü değiştirebilir miyim?”* Kesinlikle. Gölgenin konumu şeklin koordinatlarından bağımsızdır; sadece `offset_x` ve `offset_y` değerlerini ayarlayın. Pozitif değerler gölgeyi sağa/aşağıya, negatif değerler sola/yukarıya kaydırır. Üst‑sol ışık kaynağı için `offset_x = -3` ve `offset_y = -3` kullanın.

Diğer sık sorulan soru: *“Aynı şekil üzerinde birden fazla gölgeye ihtiyacım olursa?”* Aspose.Words bir şekil başına yalnızca tek bir gölgeyi destekler. Katmanlı efektler istiyorsanız, şeklin bir kopyasını oluşturup hafifçe kaydırın ve her birine farklı bir gölge uygulayın. Biraz hileli ama işe yarar.

## Tam Betik – Çalıştırmaya Hazır

Aşağıda tam, bağımsız betik yer alıyor. `create_rectangle_with_shadow.py` adlı bir dosyaya kopyalayın ve `python create_rectangle_with_shadow.py` komutuyla çalıştırın.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Not:** `YOUR_DIRECTORY` ifadesini makinenizde var olan mutlak ya da göreli bir yol ile değiştirin. Klasör mevcut değilse, Python bir `FileNotFoundError` hatası verir.

## Yaygın Tuzaklar ve Nasıl Kaçınılır

| Sorun | Neden Oluşur | Çözüm |
|-------|--------------|-------|
| Gölge görünmüyor | `shadow.visible` varsayılan `False` olarak bırakıldı | `shadow.visible = True` olduğundan emin olun |
| Şekil görünmez | Dolgu rengi `aw.Color.transparent` veya `None` olarak ayarlandı | `aw.Color.light_blue` gibi katı bir renk kullanın |
| PDF boş | `doc.save` çağrısı unutuldu veya yanlış uzantı ile kaydedildi | `doc.save("output.pdf")` çağırın ve yolu doğrulayın |
| Çalışma zamanı hatası `ImportError` | Aspose.Words yüklü değil veya yanlış Python ortamı | Aktif venv içinde `pip install aspose-words` çalıştırın |

## Sonraki Adımlar – Daha Fazla Şekil ve Biçimlendirme Keşfedin

Artık **dikdörtgen şekil oluşturma** konusunda uzmanlaştığınıza göre, şunları yapabilirsiniz:

- `ShapeType.RECTANGLE` yerine `ShapeType.ELLIPSE` veya `ShapeType.PENTAGON` kullanarak diğer geometrileri deneyin.
- Şeklin içine metin eklemek için `builder.move_to(rectangle.absolute_position)` ardından `builder.writeln("Hello World")` kullanın.
- Karmaşık diyagramlar için birden fazla şekli `group = aw.drawing.GroupShape(doc)` ile bir gruba birleştirin.
- Gölgenin nasıl aktığını görmek için DOCX (`doc.save("output.docx")`) veya HTML (`doc.save("output.html")`) gibi diğer formatlara dışa aktarın.

Bu uzantıların her biri aynı temel kavramlar üzerine inşa edilir: **şekle gölge ekle**, **şekil dolgu rengini ayarla** ve **belgeyi PDF olarak kaydet** (veya başka bir format).

### Görsel Önizleme *(isteğe bağlı)*

![Python’da gölgeyle dikdörtgen şekil oluşturma](https://example.com/rectangle-shadow.png "Python’da gölgeyle dikdörtgen şekil oluşturma")

*Ekran görüntüsü, hafif mavi bir dikdörtgen ve ince bir dış gölge ile son PDF çıktısını gösterir.*

## Sonuç

Python’da **dikdörtgen şekil oluşturma**, özel bir dolgu uygulama, **şekle gölge ekleme** ve sonunda **belgeyi PDF olarak kaydetme** için gerekli tüm adımları gözden geçirdik. Kod tamamen çalıştırılabilir, açıklamalar her özelliğin *neden*ini kapsıyor ve yaygın kenar durumlarına ve sonraki‑

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanıza ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Java için Word Belgesi Oluştur – Gölge Efektiyle Dikdörtgen Şekil Ekle](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [C# kullanarak Word’de dikdörtgen şekil oluştur – Adım‑adım Kılavuz](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Şekil Gölge Öğreticisi – C#’ta Word Şekline Gölge Ekle](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}