---
category: general
date: 2026-11-25
description: Python ile bir Word belgesindeki şekle gölge ekleyin. Word’de dikdörtgen
  şekli nasıl ekleyeceğinizi ve Aspose.Words kullanarak şeffaf gölgeyi nasıl uygulayacağınızı
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: tr
lastmod: 2026-11-25
og_description: Python kullanarak bir Word belgesindeki şekle gölge ekleyin. Bu öğreticide,
  Word'e bir dikdörtgen şekli ekleme ve Aspose.Words ile %30 şeffaflıkta gölge ayarlama
  gösterilmektedir.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Python ile bir Word belgesindeki şekle gölge ekleyin – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Python kullanarak bir Word belgesindeki şekle gölge ekleme
url: /tr/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python kullanarak bir Word belgesine şekle gölge ekleme

Eğer bir Word belgesinde **şekle gölge eklemek** istiyorsanız, bu kılavuz size tam, çalıştırılabilir bir çözüm gösterir. Word dosyası oluşturmayı, bir dikdörtgen şekli eklemeyi ve %30 şeffaf bir gölge uygulamayı—hepsini Aspose.Words for Python kütüphanesiyle nasıl yapacağınızı göreceksiniz.

Word belgeleriyle programatik olarak çalışmak, manuel biçimlendirmeden sizi kurtarır ve raporlar, sözleşmeler ya da pazarlama broşürleri gibi belgeleri ölçekli bir şekilde üretmenizi sağlar. Bu öğreticinin sonunda “**Python ile Word belgesi nasıl oluşturulur**” sorusuna hazır‑çalıştır kod örneğiyle cevap verebileceksiniz.

## Önkoşullar

Başlamadan önce şunların yüklü olduğundan emin olun:

* Python 3.8 veya daha yeni bir sürüm.
* Aktif bir Aspose.Words for Python lisansı (deneme sürümü değerlendirme için çalışır).
* `pip install aspose-words` komutuyla kurulmuş `aspose-words` paketi.
* Çıktı dosyasının yazılabileceği bir klasör (kod içinde `YOUR_DIRECTORY` ifadesini kendi yolunuzla değiştirin).

Başka bir bağımlılık gerekmez.

## Adım 1: Yeni bir Word belgesi oluşturun

İlk adım bir `Document` nesnesi örneklemektir. Bu nesne, bellekteki tüm .docx dosyasını temsil eder.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` sanal bir imleç gibi çalışır. Metotlarını çağırdığınızda kütüphane, ilgili öğeleri mevcut imleç konumuna ekler.

## Adım 2: Dikdörtgen şekli ekleyin

Sonra **dikdörtgen şekli ekleyin** builder’ın `insert_shape` metodu ile. Metot, şekil tipini ve boyutunu puan cinsinden (1 puan = 1/72 inç) ister.

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Boyutları tasarımınıza göre değiştirebilirsiniz. Dikdörtgen, belgenin çizim katmanının bir parçası olur; bu sayede daha sonra dolgu, kenarlık ya da gölge gibi özelliklerini değiştirebilirsiniz.

## Adım 3: Şeklin gölge biçimine erişin

Her çizim nesnesi, gölge görünümünü kontrol eden bir `shadow_format` özelliği sunar. Şeffaflık, offset, bulanıklık ve renk ayarlarını yapabilmek için bu özelliği alın.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

Bu aşamada şeklin varsayılan gölgesi (gölge yok) vardır. `ShadowFormat` nesnesi, gerçekçi bir etki oluşturmak için ihtiyaç duyduğunuz tüm parametreleri tutar.

## Adım 4: Gölgeyi %30 şeffaf yapın

Şeffaflık, `0` (tamamen opak) ile `1` (tamamen şeffaf) arasında bir değerle ifade edilir. `0.3` olarak ayarlamak, %30 şeffaf bir gölge oluşturur; bu, metni boğmadan derinlik eklemek için genellikle yeterlidir.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Bu ek özellikler zorunlu değildir, ancak etkinin nasıl ince ayar yapılacağını gösterir. `visible` bayrağı kritiktir; onu unutursanız diğer ayarlar yapılandırılmış olsa bile gölge görünmez.

## Adım 5: Sonucu görmek için belgeyi kaydedin

Son olarak belgeyi diske yazın. Oluşan `.docx` dosyasını Microsoft Word ya da uyumlu bir görüntüleyicide açtığınızda, şeffaf gölgesi uygulanmış dikdörtgeni göreceksiniz.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

`output.docx` dosyasını açtığınızda, alt‑sağ köşeye hafifçe kaydırılmış ince gri bir gölgeye sahip sade bir dikdörtgen göreceksiniz. Gölgenin %30 şeffaflığı, şeklin sayfadan yükselmiş gibi görünmesini sağlar.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Python ile oluşturulmuş bir Word belgesinde şekle gölge ekleme örneği"}

## Tam, çalıştırılabilir betik

Tüm parçaları bir araya getirdiğinizde, hemen kopyalayıp yapıştırıp çalıştırabileceğiniz bağımsız bir betik elde edersiniz.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Beklenen çıktı:** Oluşturulan `output.docx` dosyasını açtığınızda, hafif, yarı‑şeffaf bir gölge atan tek bir sayfa ve bir dikdörtgen görüntülenir. Ek bir biçimlendirmeye gerek yoktur.

## Yaygın varyasyonlar ve kenar durumları

| Durum | Kodu nasıl uyarlamalısınız |
|-----------|-----------------------|
| **Farklı şekil tipi** (ör. elips) | `aw.drawing.ShapeType.RECTANGLE` ifadesini `aw.drawing.ShapeType.ELLIPSE` ile değiştirin. |
| **Özel gölge rengi** | Kırmızımsı bir gölge için `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` ayarlayın. |
| **Birden fazla şekil** | `builder.insert_shape` metodunu tekrarlı olarak çağırın; her çağrı ayrı bir `Shape` nesnesi döndürür ve bağımsız olarak biçimlendirilebilir. |
| **PDF olarak kaydetme** | `doc.save(output_path)` satırını `doc.save(output_path.replace('.docx', '.pdf'))` ile değiştirin ve `.pdf` uzantısını kullanın. |
| **Lisans olmadan çalıştırma** | Ücretsiz deneme sürümü ilk sayfaya filigran ekler. Üretim kullanımı için bir lisans alarak bunu kaldırabilirsiniz. |

Bu varyasyonlar, aynı desenin—belge oluşturma, şekil ekleme, `shadow_format` ayarlama, kaydetme—çoğu otomasyon senaryosunu kapsadığını gösterir.

## İpuçları ve en iyi uygulamalar

* **Builder’ı yeniden kullanın**: Tüm belge boyunca tek bir `DocumentBuilder` örneği tutarak gereksiz nesne oluşturmayı önleyin.
* **Kaynakları serbest bırakın**: Uzun‑çalışan servislerde, kaydetme sonrası `doc.dispose()` çağırarak yerel belleği temizleyin.
* **Çıktıyı doğrulayın**: Open XML standardına uyumu garanti altına almak istiyorsanız, kaydetmeden önce `doc.validate(aw.ValidationType.FULL_VALIDATION)` kullanın.
* **Sürüm uyumluluğu**: Kod, Aspose.Words for Python ≥ 22.9 ile çalışır. Paketinizi `pip install --upgrade aspose-words` komutuyla güncel tutun.

## Sonuç

Artık Python kullanarak bir Word belgesinde **şekle gölge eklemeyi** biliyorsunuz. Beş adımı—belge oluşturma, **dikdörtgen şekli ekleme**, gölgeyi yapılandırma ve kaydetme—takip ederek raporlar, faturalar veya pazarlama materyalleri için şık belge üretimini otomatikleştirebilirsiniz.

Bundan sonra, gradient dolgu, metin kaydırma veya belgeyi PDF’ye dönüştürme gibi diğer biçimlendirme seçeneklerini keşfedebilirsiniz. Bu konuların her biri, bu öğreticide tanıtılan aynı `DocumentBuilder` ve şekil‑biçimlendirme kavramları üzerine inşa edilmiştir.

Kodlamanın tadını çıkarın ve basit bir gölgenin otomatik Word belgelerinize katacağı görsel derinliğin keyfini sürün!

## Bir Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımları keşfetmeniz için adım‑adım açıklamalı tam çalışan kod örnekleri içerir.

- [Python kullanarak bir Word belgesinde dikdörtgen şekil oluşturma](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Python’da Şekle Gölge Ekle – Tam Aspose.Words Öğreticisi](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Boş Word Belgesi Oluşturma ve Şekle Gölge Ekle – Tam Python Kılavuzu](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}