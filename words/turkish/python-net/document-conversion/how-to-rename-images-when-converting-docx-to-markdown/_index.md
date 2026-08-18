---
category: general
date: 2026-06-30
description: DOCX'i markdown'a dönüştürürken resimlerin adını nasıl değiştireceğinizi
  öğrenin. Resim adlarını değiştirin ve Word belgesini özel resim dosya adlarıyla
  markdown olarak kaydedin.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: tr
og_description: DOCX'i markdown'a dönüştürürken resimlerin adını nasıl değiştirirsiniz.
  Bu kılavuz, resim adlarını nasıl değiştireceğinizi, Word'ü markdown olarak nasıl
  kaydedeceğinizi ve özel resim dosya adlarını nasıl kullanacağınızı gösterir.
og_title: DOCX'i Markdown'a Dönüştürürken Görselleri Nasıl Yeniden Adlandırılır
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: DOCX'ten Markdown'a Çevirirken Görselleri Nasıl Yeniden Adlandırılır
url: /tr/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX'i Markdown'e Dönüştürürken Görselleri Nasıl Yeniden Adlandırılır

Bir DOCX dosyasını Markdown'e dönüştürürken görsellerin **otomatik olarak nasıl yeniden adlandırılacağını** hiç merak ettiniz mi? Tek başınıza değilsiniz. Birçok dokümantasyon hattında varsayılan görsel adları (örneğin `image1.png`) izlemek için bir kabusa dönüşür, özellikle aynı markdown ekipler arasında sürüm kontrolüne alındığında.  

İyi haber şu ki Aspose.Words for Python, **görsel adlarını** anında değiştirmeyi çocuk oyuncağı haline getiriyor ve Markdown dosyanızı temiz tutarken özel adlandırılmış varlıkların düzenli bir klasörünü koruyabilirsiniz.  

Bu öğreticide şunları öğreneceksiniz:

* Python’da bir Word belgesi (`.docx`) yüklemek.  
* Her görsele GUID tabanlı bir dosya adı veren bir geri çağırma (callback) ile Markdown kaydetme sürecine müdahale etmek.  
* Belgeyi Markdown olarak kaydetmek, böylece oluşturulan dosya yeni adlandırılmış görsellere referans verir.  

Temel Python bilgisine ve Aspose.Words kurulumuna sahipseniz, beş dakikadan kısa bir sürede çalışır hâle geleceksiniz. Harici betikler yok, manuel yeniden adlandırma yok—sadece sizin için ağır işi yapan tek bir, bağımsız program.

---

## Önkoşullar — Başlamadan Önce Neye İhtiyacınız Var

| Gereksinim | Neden Önemli |
|-------------|----------------|
| **Python 3.7+** | Örnek, 3.6’da tanıtılan f‑string’leri ve tip ipuçlarını kullanıyor, ancak 3.7+ `os.path.splitext` kolaylıklarını sunar. |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | Bu kütüphane, reliance ettiğimiz `aw.Document` sınıfını ve `MarkdownSaveOptions`’ı sağlar. |
| **Write permission** to the output folder | Geri çağırma yeni görsel dosyaları oluşturacak, bu yüzden betiğin bunları yazma izni olmalı. |
| **A DOCX file** you want to convert | Basit bir rapordan karmaşık bir kılavuza kadar her şey çalışır. |

> **Pro ipucu:** Sanal bir ortam (virtual environment) kullanıyorsanız, Aspose.Words’u kurmadan önce ortamı etkinleştirin. Bağımlılıkları izole eder ve sürüm çakışmalarını önler.

---

## Adım 1: Word Belgesini Yükleyin  

Bir **docx'i markdown'a dönüştürmek** istediğinizde ilk yapmanız gereken kaynak dosyayı açmaktır. Aspose.Words, düşük seviyeli OPC işlemlerini soyutlar, bu yüzden tek bir satır işi görür.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Bu neden önemli:* Belgeyi yüklemeden kaynaklarını inceleyemezsiniz ve Markdown dışa aktarıcısı yazacak bir şey bulamaz. `aw.Document` nesnesi, tüm Word paketini bellekte tutar, böylece kaydetmeden önce güvenle manipüle edebilirsiniz.

---

## Adım 2: **Görsel Kaynaklarını Yeniden Adlandıran** Bir Geri Çağırma Yazın  

Aspose.Words, `MarkdownSaveOptions` içine bir `resource_saving_callback` takmanıza izin verir. Geri çağırma, her kaynak (görseller, CSS vb.) diske yazılmadan hemen önce tetiklenir. `resource.file_name` değerini değiştirerek **özel görsel dosya adları** uygulayabiliriz.

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### Neden GUID Kullanılır?

* **Benzersizlik** – Bir GUID (`uuid4`), iki görselin bile birden fazla çalışmada çakışmayacağını garanti eder.  
* **İzlenebilirlik** – Daha sonra hata ayıklamanız gerekirse, GUID orijinal Word paragraf numarasıyla birlikte kaydedilebilir.  
* **Taşınabilirlik** – Orijinal Word adlandırma şemasına bağımlı değildir; bu şema boşluklar veya Markdown bağlantılarını kırabilecek özel karakterler içerebilir.

---

## Adım 3: Geri Çağırmayı Markdown Kaydetme Seçeneklerine Bağlayın  

Şimdi Aspose’a, bir görsel çıktıya klasöre yazıldığında yeniden adlandırma mantığımızı kullanmasını söylüyoruz.

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*Açıklama:* `MarkdownSaveOptions` sınıfı, satır sonlarından görsel klasör konumuna kadar her şeyi kontrol eder. `resource_saving_callback` ayarlandığında, gömülü her kaynak için çalışan bir **kanca** (hook) elde edersiniz; bu da **görsel adlarını** dosya diske ulaşmadan önce değiştirmenize olanak tanır.

---

## Adım 4: Belgeyi Markdown Olarak Kaydedin – Son Parça  

Geri çağırma yerinde olduğunda, son adım basittir.

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

Betik tamamlandığında şunları bulacaksınız:

* `CustomResources.md` – Word dosyanızın Markdown temsili.  
* `images/` klasörü (veya ayarladığınız başka bir klasör) içinde `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png` gibi dosyalar.  

Markdown dosyası yeni GUID tabanlı dosya adlarını referans alacak, böylece herhangi bir downstream işlemci (GitHub, MkDocs vb.) doğru görselleri manuel olarak yeniden adlandırmanıza gerek kalmadan alacaktır.

### Beklenen Çıktı (alıntı)

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

GUID’ler her çalıştırmada farklı olur, ancak desen aynı kalır.

---

## Kenar Durumları ve Yaygın Soruların Yönetimi  

### Belge görüntü dışı kaynaklar içerirse ne olur?  

Geri çağırmamız zaten dosya uzantısını kontrol eder ve görüntü olmayan her şey için `True` döner. Bu, CSS dosyaları, fontlar veya gömülü OLE nesnelerinin orijinal adlarını korur; bu genellikle **save word as markdown** yaptığınızda istediğiniz şeydir.

### GUID yerine özel bir adlandırma şeması kullanabilir miyim?  

Kesinlikle. `uuid.uuid4()` çağrısını, bir dize döndüren herhangi bir fonksiyonla değiştirin. Örneğin, orijinal paragraf indeksini ön ek olarak ekleyebilirsiniz:

```python
new_name = f"para{resource.resource_id}{ext}"
```

Sadece ortaya çıkan adın belge boyunca benzersiz olduğundan emin olun.

### Büyük belgelerde performansı nasıl etkiler?  

Geri çağırma her kaynak için bir kez çalışır, bu yüzden ek yük minimaldir—çoğunlukla bir GUID üretme süresi. 200 sayfalık bir rapor ve onlarca görsel bile modern bir dizüstü bilgisayarda bir saniyeden kısa sürede tamamlanır.

### Görsel dosya adlarının deterministik (ör. CI build’leri için) olması gerekirse ne yapmalıyım?  

`uuid.uuid4()` yerine orijinal görsel baytlarının bir hash’ini kullanın:

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

Bu, aynı kaynak görseli üzerinde betiği her çalıştırdığınızda aynı dosya adını üretir.

---

## Tam Çalışan Betik – Kopyala, Yapıştır, Çalıştır  



## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [save docx as markdown – Full C# Guide with Image Extraction](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}