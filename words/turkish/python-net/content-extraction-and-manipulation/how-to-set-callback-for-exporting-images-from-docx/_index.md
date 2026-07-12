---
category: general
date: 2026-06-24
description: Markdown olarak kaydederken DOCX'ten görüntüleri dışa aktarmak için geri
  çağırma (callback) nasıl ayarlanır. Görüntüleri nasıl çıkaracağınızı, Word'ten SVG'yi
  nasıl çıkaracağınızı ve DOCX'i özel işleme ile Markdown olarak nasıl kaydedeceğinizi
  öğrenin.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: tr
og_description: Markdown'a dönüştürürken DOCX'ten resimleri dışa aktarmak için geri
  aramayı (callback) nasıl ayarlayacağınızı öğrenin. Bu rehber, resimleri ve SVG'leri
  verimli bir şekilde nasıl çıkaracağınızı gösterir.
og_title: DOCX'ten Görselleri Dışa Aktarmak İçin Geri Çağrıyı Nasıl Ayarlarsınız
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: DOCX'ten Görselleri Dışa Aktarmak İçin Geri Çağrıyı Nasıl Ayarlarsınız
url: /tr/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX'ten Görüntüleri Dışa Aktarmak İçin Geri Çağrıyı (Callback) Nasıl Ayarlarsınız

Markdown'e dönüştürürken **callback'i nasıl ayarlayacağınızı** ve **DOCX'ten görüntüleri dışa aktarabileceğinizi** hiç merak ettiniz mi? Tek başınıza değilsiniz. Birçok geliştirici, varsayılan dönüşüm tüm görüntüleri genel bir klasöre döktüğünde ya da daha da kötüsü SVG grafiklerini tamamen kaybettiğinde bir duvara çarpar.  

Bu öğreticide, “callback'i nasıl ayarlayacağınız” sorusuna yanıt veren, **görüntüleri nasıl çıkaracağınızı** gösteren ve hatta **Word'den SVG çıkarımını** kapsayan eksiksiz, çalıştırmaya hazır bir çözümü adım adım inceleyeceğiz. Sonunda, her görüntü kaynağı için özel bir adlandırma şemasıyla **DOCX'i Markdown olarak kaydedebileceksiniz**—manuel müdahale gerekmeyecek.

## Öğrenecekleriniz

- Dönüşüm sırasında görüntü dosya adlarını kontrol etmenin en temiz yolu olarak callback'in neden tercih edildiği.  
- Aspose.Words’ün `MarkdownSaveOptions.resource_saving_callback` özelliğine nasıl bağlanılacağı.  
- **PNG**, **JPG**, **SVG** ve diğer gömülü kaynakları çıkaran adım adım kod.  
- İsim çakışmalarını, büyük dosyaları ve platformlar arası yol farklılıklarını yönetme ipuçları.  

> **Pro tip:** Zaten daha büyük bir işlem hattında Aspose.Words kullanıyorsanız, bu callback'i kodunuzun geri kalanına dokunmadan ekleyebilirsiniz.

---

![Geri çağrıyı ayarlama diyagramı](https://example.com/images/how-to-set-callback.png "geri çağrıyı ayarla")

## Ön Koşullar

- Python 3.8+ (örnek f‑string kullandığı için 3.6+ yeterlidir).  
- `aspose-words` paketi yüklü (`pip install aspose-words`).  
- Raster görüntüler **ve** vektör grafikler (SVG) içeren bir DOCX dosyası.  
- Python fonksiyonları ve dosya I/O konusunda temel bilgi.

Bu koşullara sahipseniz, başlayalım.

---

## DOCX'ten Görüntüleri Dışa Aktarmak İçin Geri Çağrıyı (Callback) Nasıl Ayarlarsınız

Çözümün çekirdeği bir **kaynak‑kaydetme callback'i** içinde yer alır. Aspose.Words, `document.save` çağrıldığında yazmak istediği her görüntü veya SVG için bu delegeyi çalıştırır. `(new_name, data)` ikilisini döndürerek hem dosya adını hem de bayt içeriğini belirlersiniz.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### Neden Bir Callback?

Callback olmadan Aspose.Words, `image1.png`, `image2.svg` gibi adlarla dosyalar oluşturur ve bunları Markdown dosyasının yanındaki bir klasöre koyar. Bu, hızlı demolar için yeterli olabilir, ancak üretimde genellikle şunlar gerekir:

1. **Deterministik adlar** – sürüm kontrolü veya CDN yayınlaması için kullanışlı.  
2. **Çakışma önleme** – aynı orijinal ada sahip iki görüntü birbirinin üzerine yazılmaz.  
3. **Özel klasör yapıları** – tüm varlıkları `/assets/docs/` altında toplamak isteyebilirsiniz.

Callback, bu üç endişe üzerinde tam kontrol sağlar.

---

## Kaynak Callback Kullanarak DOCX'ten Görüntüleri Dışa Aktarma

Aşağıda callback uygulaması yer alıyor. İkili veriyi hash'leyerek benzersiz bir sonek üretir, orijinal dosya uzantısını korur ve yeni dosya adını ham baytlarla birlikte döndürür.

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### Kenar‑Durum İşleme

- **Büyük dosyalar:** SHA‑256 herhangi bir boyutta sorunsuz çalışır; hash bellek içinde hesaplandığı için devasa PDF'leri işlerken bellek tüketimine dikkat edin.  
- **Eksik uzantılar:** Bazı eski Word dosyaları görüntüyü açık bir uzantı olmadan saklayabilir. Bu durumda `extension` boş olur; varsayılan olarak `.bin` kullanabilir veya ilk birkaç bayta bakarak formatı tahmin edebilirsiniz.  
- **Görüntü olmayan kaynaklar:** Callback, her dış kaynağa (ör. OLE nesneleri) çağrılır. Sadece görüntü/SVG ilgileniyorsanız, `resource.type` ile filtreleyin.

---

## Word'den Görüntü ve SVG Çıkarma

Şimdi callback'i Markdown kaydetme işlem hattına bağlayacağız. `MarkdownSaveOptions` nesnesi, bu amaçla `resource_saving_callback` özelliğini sunar.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

`resource_folder` ayarı isteğe bağlıdır ancak genellikle kullanışlıdır. Bunu atladığınızda, görüntüler Markdown dosyasının yanına yerleşir ve proje kökünüz dağınık hâle gelebilir.

### Belgeyi Kaydetme

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

Betik çalıştırıldığında aşağıdaki gibi bir dizi dosya göreceksiniz:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

Ve oluşturulan `output.md` dosyası, bu kesin dosya adlarına işaret eden görüntü bağlantılarını içerir:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

Bu, **görüntüleri çıkarma** kısmının harekette olduğu anlamına geliyor—her resim, raster ya da vektör, artık ayrı ve benzersiz adlandırılmış bir varlık.

---

## Özel Görüntü İşleme ile DOCX'i Markdown Olarak Kaydetme

Hepsini bir araya getirdiğimizde, `convert_docx_to_md.py` adlı bir dosyaya kopyalayıp yapıştırabileceğiniz tam betik aşağıdadır:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**Neden çalışıyor:**  
- `resource_callback`, her görüntünün benzersiz ve yeniden üretilebilir bir ad almasını garanti eder.  
- `resource_folder`, varlıkları ayırarak Markdown dosyasını düzenli tutar.  
- `os.makedirs` çağrıları, betik yeni bir makinede çalıştığında “klasör bulunamadı” hatalarını önler.

---

## Word'den SVG Çıkarma – Vektör Grafikler Ne Olacak?

SVG'ler, callback tarafından PNG'ler gibi aynı şekilde işlenir çünkü onlar da bir `resource` türüdür. Tek fark, bazı eski Word sürümlerinin SVG'leri *OfficeArt* nesneleri olarak gömmesidir; Aspose.Words bu nesneleri otomatik olarak raster PNG'ye dönüştürür, **preserve SVG** bayrağını açıkça etkinleştirmezseniz.

```python
md_options.export_svg = True  # Keep original SVG markup
```

Bu satırı kaydetmeden önce ekleyin; callback `.svg` uzantılı kaynakları alır ve keskin vektör verisini korur—duyarlı web belgeleri için mükemmeldir.

---

## Yaygın Sorular & Dikkat Edilmesi Gerekenler

| Soru | Cevap |
|----------|--------|
| **İki görüntü aynıysa ne olur?** | SHA‑256 hash'i aynı olur, bu da dosya adlarının çakışmasına yol açar. Her iki kopyayı da tutmanız gerekiyorsa, hash hesabına orijinal `resource.name`i de ekleyin (ör. `hash(resource.name + resource.data)`). |
| **Dosya tipine göre klasörü değiştirebilir miyim?** | Evet. `resource_callback` içinde `extension`ı inceleyip `f"png/{new_name}"` gibi bir yol döndürebilirsiniz. |
| **Linux/macOS'ta çalışır mı?** | Kesinlikle. Kod `os.path` kullanarak yol ayırıcılarını soyutlar. Ücretli bir sürüm kullanıyorsanız, lisans dosyasının (`aspose.words.lic`) erişilebilir olduğundan emin olun. |
| **Büyük belgelerde bellek kullanımı nasıl?** | Callback, her kaynak için **tam bayt dizisini** alır; yani görüntü geçici olarak bellekte bulunur. Çok‑gigabaytlık dosyalar için veriyi doğrudan diske akıtıp `return None` yerine callback içinde kaydetmeyi düşünebilirsiniz. |

---

## Sonuç

Artık **callback'i nasıl ayarlayacağınızı** ve **DOCX'i Markdown olarak kaydederken görüntü çıkarımını** kontrol edebiliyorsunuz. Bu yaklaşım, **DOCX'ten görüntüleri dışa aktarmanızı**, **Word'den SVG çıkarmanızı** ve Markdown dosyanızı temiz ve deterministik tutmanızı sağlar.  

Tek bir, bağımsız betikte belgeyi yükleme, bir kaynak‑kaydetme callback'i tanımlama, `MarkdownSaveOptions` yapılandırma ve isim çakışmaları ile vektör grafikler gibi kenar‑durumları ele alma adımlarını kapsadık. Sonuç, benzersiz adlandırılmış varlıklarla birlikte mükemmel bağlantılandırılmış bir Markdown dosyası—statik site jeneratörleri, dokümantasyon hatları veya temiz, yeniden kullanılabilir varlıklar gerektiren herhangi bir iş akışı için hazır.

**Sonraki adımlar?**  
- Bu betiği MkDocs gibi bir statik site jeneratörüyle zincirleyerek Word tabanlı dokümanları otomatik olarak yayınlayın.  
- Görüntüleri dış dosya olarak değil, satır içi olarak tutmak isterseniz `markdown_options.export_images_as_base64 = True` seçeneğini deneyin.  
- Aspose.Words’ün diğer callback'lerini (ör. `document_saving_callback`) keşfederek Markdown çıktısını da kontrol edin.

Diğer Office formatlarından **görüntü çıkarma** konusunda daha fazla sorunuz varsa veya belirli bir adlandırma kuralı için callback'i özelleştirmeye ihtiyacınız varsa, aşağıya yorum bırakın. İyi kodlamalar!

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, tam çalışan kod örnekleri ve adım adım açıklamalar içerir; böylece API özelliklerini daha da derinlemesine öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}