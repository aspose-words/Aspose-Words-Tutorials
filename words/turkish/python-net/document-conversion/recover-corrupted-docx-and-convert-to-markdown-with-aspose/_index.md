---
category: general
date: 2026-08-04
description: Aspose.Words kurtarma modunu kullanarak bozuk docx dosyalarını kurtarın
  ve docx'i markdown'a dönüştürün, denklemleri LaTeX olarak dışa aktarın.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to use recovery mode
- export equations latex
language: tr
lastmod: 2026-08-04
og_description: Aspose.Words kurtarma modu ile bozuk docx dosyalarını kurtarın, ardından
  denklemleri LaTeX olarak dışa aktararak docx'i markdown'a dönüştürün. PDF ve TXT
  çıktıları da oluşturmak için bu adım adım kılavuzu izleyin.
og_image_alt: Screenshot of Aspose.Words Python code converting a corrupted docx to
  markdown with LaTeX equations
og_title: Bozuk docx dosyasını kurtarın ve markdown'a dönüştürün – Aspose rehberi
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  headline: Recover corrupted docx and convert to markdown with Aspose
  type: TechArticle
- description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  name: Recover corrupted docx and convert to markdown with Aspose
  steps:
  - name: Export floating shapes as inline tags
    text: Floating images or text boxes can cause layout issues when converting to
      PDF. Setting `export_floating_shapes_as_inline_tag` forces Aspose.Words to treat
      those shapes as regular inline elements, preserving the visual flow.
  - name: Adjust the shadow of the first shape
    text: You might want to enhance the appearance of a specific shape before saving
      the final PDF. The code below accesses the first `Shape` node, enables its shadow,
      and tweaks visual parameters.
  - name: Expected output
    text: '| File | Description | |------|-------------| | `output.md` | Markdown
      version of the original DOCX. All equations appear as LaTeX (`$...$` or `$$...$$`).
      | | `output.txt` | Plain‑text dump'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document conversion
title: Bozuk docx dosyasını kurtarın ve Aspose ile markdown'a dönüştürün
url: /tr/python/document-conversion/recover-corrupted-docx-and-convert-to-markdown-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bozuk docx dosyalarını kurtarın ve Aspose ile markdown'a dönüştürün

Eğer **bozuk docx** dosyalarını **kurtarmanız** gerekiyorsa, Aspose.Words, hasarlı Word belgelerini otomatik olarak onarabilen yerleşik bir kurtarma modu sağlar. Dosya onarıldıktan sonra **docx'i markdown'a dönüştürebilir** ve hatta **denklemleri latex olarak dışa aktarabilirsiniz**, bilimsel belgelerde sorunsuz kullanım için. Bu öğreticide, bunu Python'da tam olarak nasıl yapacağınızı ve PDF ile düz metin çıktısı için birkaç ekstra seçeneği gösteriyoruz.

Şunları öğreneceksiniz:

* Kurtarma modunu kullanarak potansiyel olarak kırık bir DOCX dosyasını yükleyin.  
* Geri kazanılan belgeyi LaTeX‑formatlı denklemlerle Markdown olarak kaydedin.  
* LaTeX denklemlerini içeren bir düz‑metin (TXT) sürümü oluşturun.  
* Yüzen şekilleri satır içi öğeler olarak etiketleyerek PDF'ye dışa aktarın.  
* Bir şeklin gölgesini ayarlayın ve son PDF'yi üretin.  

Harici bir araç gerekmiyor—sadece ücretsiz Aspose.Words for Python kütüphanesi.

## Önkoşullar

| Gereksinim | Neden Önemli |
|-------------|----------------|
| Python 3.8+ | Aspose.Words for Python tarafından gereklidir |
| `aspose-words` package (`pip install aspose-words`) | Kodda kullanılan `aw` ad alanını sağlar |
| A DOCX file that may be damaged (e.g., `corrupted.docx`) | Kurtarma iş akışını gösterir |
| Write permission to the output directory | Komut dosyası birkaç dosya (`.md`, `.txt`, `.pdf`) yazar |

Değerlendirme limitlerini aşıyorsanız, Aspose.Words lisansının (ücretsiz deneme veya satın alınmış) doğru şekilde yapılandırıldığından emin olun.

## Aspose.Words ile bozuk docx dosyasını kurtarın

İlk adım, Aspose.Words'a giriş dosyasını potansiyel olarak bozuk olarak ele almasını söylemektir. Bu, `LoadOptions.recovery_mode` ile yapılır.

```python
import aspose.words as aw

# Step 1: Load a possibly corrupted document using recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # Enables automatic recovery of damaged files
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Neden bu çalışır:**  
`RecoveryMode.RECOVER` yükleyiciyi yapısal hataları yok saymaya ve belge ağacını yeniden oluşturmaya zorlar. Dosya yalnızca kısmen hasarlıysa, metin, resimler ve denklemler dahil çoğu içerik geri yüklenir.

**İpucu:** Belgeyi onarmadan yalnızca doğrulamak istiyorsanız `RecoveryMode.NO_RECOVERY` kullanın. Tam kurtarma için ayarı gösterildiği gibi tutun.

## Docx'i LaTeX denklemleriyle markdown'a dönüştürün

Belge belleğe yüklendikten sonra, onu Markdown olarak kaydedebilirsiniz. `office_math_export_mode` ayarını `LATEX` olarak belirlemek, Aspose.Words'a her Word denklemini bir LaTeX dizesi olarak işleme almasını söyler.

```python
# Step 2: Save the document as Markdown while exporting equations in LaTeX format
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)
```

Oluşan `output.md`, normal bir Markdown dosyası gibi görünecek, ancak her denklem `$...$` (satır içi) veya `$$...$$` (görünüm) LaTeX kodu olarak görünecek. Bu, LaTeX sözdizimini anlayan Pandoc veya Jupyter defterleri gibi sonraki araçlar için gereklidir.

## Hasarlı dosyalar için kurtarma modunu nasıl kullanılır

Kurtarma modu, herhangi bir yükleme işlemi için yeniden kullanılabilir. Aşağıda diğer betiklere kopyalayabileceğiniz kompakt bir desen bulunmaktadır:

```python
def load_with_recovery(path: str) -> aw.Document:
    opts = aw.loading.LoadOptions()
    opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    return aw.Document(path, opts)
```

`load_with_recovery("myfile.docx")` çağrısı, Aspose.Words'un zaten düzeltmeye çalıştığı bir `Document` nesnesi döndürür. Bu işlev, projeler arasında **kurtarma modunun nasıl güvenli bir şekilde kullanılacağını** somutlaştırır.

## Markdown ve txt'ye kaydederken denklemleri latex olarak dışa aktar

Eğer ayrıca bir düz metin (plain‑text) sürümüne ihtiyacınız varsa, aynı `office_math_export_mode` bayrağı `TxtSaveOptions` ile çalışır.

```python
# Step 3: Save the same document as plain‑text (TXT) with LaTeX equations
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)
```

`.txt` dosyası, Word belgesinin ham metnini içerir ve her denklem LaTeX kodu olarak temsil edilir. Bu format, indeksleme veya LaTeX'i anlayan arama motorlarına içerik beslemek için kullanışlıdır.

## Ek seçenekler: Satır içi şekiller ve şekil gölgesi ile PDF

### Yüzen şekilleri satır içi etiketler olarak dışa aktar

Yüzen resimler veya metin kutuları, PDF'ye dönüştürürken düzen sorunlarına yol açabilir. `export_floating_shapes_as_inline_tag` ayarı, Aspose.Words'un bu şekilleri normal satır içi öğeler olarak ele almasını zorlayarak görsel akışı korur.

```python
# Step 4: Export the document to PDF and tag floating shapes as inline elements
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

### İlk şeklin gölgesini ayarlama

Son PDF'yi kaydetmeden önce belirli bir şeklin görünümünü geliştirmek isteyebilirsiniz. Aşağıdaki kod, ilk `Shape` düğümüne erişir, gölgesini etkinleştirir ve görsel parametreleri ayarlar.

```python
# Step 5: Adjust the shadow of the first shape and save the result
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0          # Controls shadow softness
shape_shadow.distance = 3.0      # Distance from the shape
shape_shadow.angle = 45          # Direction of the light source
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

**Sonuç:** `shadowed.pdf`, `output.pdf` ile aynı görünüme sahiptir ancak ilk şekil artık hafif bir siyah gölge verir; bu, sunumlarda okunabilirliği artırabilir.

## Tam çalıştırılabilir betik

Aşağıda tüm adımları birleştiren tam betik bulunmaktadır. `recover_and_convert.py` adlı bir dosyaya kopyalayın, `YOUR_DIRECTORY` ifadesini gerçek bir yol ile değiştirin ve `python recover_and_convert.py` komutunu çalıştırın.

```python
import aspose.words as aw

# -------------------------------------------------
# 1. Load the possibly corrupted DOCX using recovery mode
# -------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)

# -------------------------------------------------
# 2. Save as Markdown with LaTeX equations
# -------------------------------------------------
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)

# -------------------------------------------------
# 3. Save as plain‑text (TXT) with LaTeX equations
# -------------------------------------------------
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)

# -------------------------------------------------
# 4. Export to PDF, converting floating shapes to inline
# -------------------------------------------------
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)

# -------------------------------------------------
# 5. Add a shadow to the first shape and save a new PDF
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0
shape_shadow.distance = 3.0
shape_shadow.angle = 45
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

### Beklenen çıktı

| Dosya | Açıklama |
|------|-------------|
| `output.md` | Orijinal DOCX'in Markdown sürümü. Tüm denklemler LaTeX (`$...$` veya `$$...$$`) olarak görünür. |
| `output.txt` | Düz metin dökümü |

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri içerir.

- [Markdown Nasıl Kullanılır: DOCX'i LaTeX Denklemleriyle Markdown'a Dönüştürme](/words/english/net/programming-with-markdownsaveoptions/how-to-use-markdown-convert-docx-to-markdown-with-latex-equa/)
- [Aspose.Words ile docx nasıl kurtarılır – adım adım](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Bozuk DOCX'i Kurtar ve Word'u Markdown'a Dönüştür](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}