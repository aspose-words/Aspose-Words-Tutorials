---
category: general
date: 2026-10-23
description: Aspose.Words for Python kullanarak Word'ü PDF olarak kaydetmeyi ve DOCX'i
  Markdown'a dönüştürmeyi, kurtarma modu ve LaTeX matematik desteğiyle öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word as pdf
- convert docx to markdown
- enable recovery mode
- markdown latex math
- export equations latex
language: tr
lastmod: 2026-10-23
og_description: Word'ü PDF olarak kaydedin ve Aspose.Words for Python ile DOCX'i Markdown'a
  dönüştürün. Kılavuz, kurtarma modu, LaTeX matematik dışa aktarımı ve PDF şekil işleme
  konularını kapsar.
og_image_alt: Screenshot illustrating how to save Word as PDF using Aspose.Words in
  Python
og_title: Word'ü PDF olarak kaydedin ve DOCX'i Markdown'a dönüştürün – Tam Python
  Rehberi
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to save Word as PDF and convert DOCX to Markdown using Aspose.Words
    for Python, with recovery mode and LaTeX math support.
  headline: How to save Word as PDF and convert DOCX to Markdown
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF conversion
- Markdown
- LaTeX
title: Word'ü PDF olarak kaydetme ve DOCX'i Markdown'a dönüştürme
url: /tr/python/document-conversion/how-to-save-word-as-pdf-and-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'ü PDF olarak kaydetme ve DOCX'i Markdown'a dönüştürme

Eğer **Word'ü PDF olarak kaydetmeniz** ve aynı DOCX dosyasını Markdown'a dönüştürmeniz gerekiyorsa, bu öğretici size tek bir tekrarlanabilir iş akışı gösterir. Aspose.Words for Python'ın bozuk kaynak dosyalarını nasıl işleyebileceğini, denklemleri LaTeX olarak dışa aktarabileceğini ve PDF çıktısındaki yüzen şekiller üzerinde ince ayarlı kontrol sağlayabileceğini göreceksiniz.

Kılavuz, gerekli tüm importları, seçenek yapılandırmalarını ve kaydetme çağrılarını adım adım gösterir, böylece çalışan bir betiği bugün projenize kopyalayıp yapıştırabilirsiniz.

![Aspose.Words for Python kullanarak Word'ü PDF olarak kaydetmeyi gösteren diyagram](image-placeholder.png "Word'ü PDF olarak kaydetme iş akışını gösteren diyagram")

## Önkoşullar

* Python 3.8+ yüklü.
* Aktif bir Aspose.Words for Python lisansı (veya ücretsiz deneme).
* `aspose-words` paketi `pip install aspose-words` ile yüklü.
* İşlemek istediğiniz bir DOCX dosyası (örnek `input.docx` kullanır).

Bunların hazır olması, kodun ek kurulum adımları olmadan çalışmasını sağlar.

## Adım 1: Kaynak belgeyi yükleme

İlk işlem DOCX dosyasını açmaktır. Aspose.Words dosyayı bir `Document` nesnesine okur ve bu nesne sonraki tüm kaydetme işlemlerinin kaynağı olur.

```python
import aspose.words as aw

# Load the DOCX file from the file system
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

> **Neden önemli:** Belgeyi yüklemek, dosyayı yeniden okumadan farklı kaydetme seçenekleri uygulamanıza olanak tanıyan bellek içi bir temsil oluşturur.

## Adım 2: Bozuk belgeleri sorunsuz işlemek için kurtarma modunu etkinleştirme

Kaynak DOCX bozuk olabilir—eksik bölümler, hatalı XML veya beklenmeyen akışlar—**kurtarma modunu** etkinleştirin. Bu, Aspose.Words'a kritik olmayan hataları görmezden gelmesini ve yine de çıktı üretmesini söyler.

```python
# Configure load options for recovery
load_opts = aw.LoadOptions()
load_opts.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER
# Re‑load the document using the recovery options
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_opts)
```

> **Kurtarma modunu etkinleştirme**, tek bir bozuk dosyanın tüm süreci durdurmaması gereken toplu işlem hatlarında özellikle faydalıdır.

## Adım 3: Markdown kaydetme seçeneklerini hazırlama – Office Math denklemlerini LaTeX olarak dışa aktarma

**DOCX'i Markdown'a dönüştürdüğünüzde**, denklemlerin LaTeX olarak görünmesini istersiniz, böylece sonraki araçlar (ör. Jupyter, statik site jeneratörleri) bunları doğru şekilde render eder.

```python
# Markdown options with LaTeX export for equations
md_opts = aw.saving.MarkdownSaveOptions()
md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

> **Markdown LaTeX matematik** desteği, karmaşık formüllerin dönüşüm sırasında dokunulmadan kalmasını ve bilimsel doğruluğun korunmasını sağlar.

## Adım 4: Düz metin kaydetme seçeneklerini hazırlama – ayrıca Office Math'i LaTeX olarak dışa aktarma

Sadece bir `.txt` sürümüne ihtiyacınız olsa bile, denklemleri LaTeX olarak tutmak sonraki ayrıştırma işlemleri için değerli olabilir.

```python
# Plain‑text options with LaTeX export
txt_opts = aw.saving.TxtSaveOptions()
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

## Adım 5: PDF kaydetme seçeneklerini hazırlama – yüzen şekillerin nasıl etiketleneceğini kontrol etme

Yüzen şekiller (metin kutuları, görseller) PDF'de satır içi etiketler veya ayrı nesneler olarak temsil edilebilir. Aşağıdaki seçenek, birçok erişilebilirlik aracının tercih ettiği gibi onları satır içi tutar.

```python
# PDF options controlling floating shape handling
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True  # Set to False to keep separate
```

> **Denklemleri LaTeX olarak dışa aktarma**, PDF motoru tarafından otomatik olarak işlenir; PDF yolunda LaTeX için ayrı bir işaretçiye ihtiyacınız yoktur.

## Adım 6: Belgeyi tüm istenen formatlarda kaydetme

Şimdi üç tamamen yapılandırılmış seçenek nesneniz var. Her format için tek bir `doc.save` çağrısı çıktı dosyalarını yazar.

```python
# Save as Markdown (with LaTeX math)
doc.save("YOUR_DIRECTORY/output.md", md_opts)

# Save as plain text (with LaTeX math)
doc.save("YOUR_DIRECTORY/output.txt", txt_opts)

# Save as PDF (with inline‑tagged floating shapes)
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

### Beklenen sonuçlar

| Çıktı dosyası | Ana özellikler |
|---------------|----------------|
| `output.md` | Markdown metni, denklemler `$$...$$` LaTeX blokları olarak görünür |
| `output.txt` | Düz metin temsili, LaTeX denklemler satır içinde |
| `output.pdf` | Orijinal düzenin PDF renderı, yüzen şekiller satır içinde etiketlenir |

Her dosyayı yerel görüntüleyicinizde açarak dönüşümün başarılı olduğunu doğrulayabilirsiniz.

## Word'ü PDF olarak kaydetme ve özel seçenekler

Tek amacınız **Word'ü PDF olarak kaydetmek** ise, Markdown ve TXT adımlarını atlayabilir ve PDF seçeneklerine odaklanabilirsiniz:

```python
# Minimal script to save only PDF
import aspose.words as aw

doc = aw.Document("YOUR_DIRECTORY/input.docx")
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

Bu kod parçacığı, şekil etiketlemesi üzerinde kontrol sağlamaya devam ederken **Word'ü PDF olarak kaydetmenin** en basit yolunu gösterir.

## Toplu dönüşümler için kurtarma modunu etkinleştirme

Birçok dosya işlenirken, yükleme‑kaydetme mantığını bir döngü içinde sarın ve aynı `LoadOptions` nesnesini tekrar kullanın:

```python
import os
import aspose.words as aw

load_opts = aw.LoadOptions()
load_opts.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER

for filename in os.listdir("batch_input"):
    if filename.lower().endswith(".docx"):
        path = os.path.join("batch_input", filename)
        doc = aw.Document(path, load_opts)

        # Save PDF only (example)
        pdf_path = os.path.join("batch_output", filename.replace(".docx", ".pdf"))
        pdf_opts = aw.saving.PdfSaveOptions()
        pdf_opts.export_floating_shapes_as_inline_tag = True
        doc.save(pdf_path, pdf_opts)
```

> **Pro ipucu:** Aspose.Words'un döndürdüğü herhangi bir `LoadWarning` mesajını kaydedin; bunlar bozuk dosyanın hangi bölümlerinin onarıldığını gösterir.

## Markdown ve düz metinde denklemleri LaTeX olarak dışa aktarma

`MarkdownSaveOptions` ve `TxtSaveOptions` aynı `office_math_export_mode` özelliğini sunar. Bunu `LATEX` olarak ayarlamak, motorun Office Math XML'ini LaTeX sözdizimine çevirmesini sağlar. Görselleri tercih ederseniz, enum değerini `IMAGE` olarak değiştirin.

```python
md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.IMAGE  # Alternative
```

İş akışınızdaki renderleme hattına uyan modu seçin.

## Word'ü PDF olarak kaydederken yüzen şekilleri kontrol etme

`export_floating_shapes_as_inline_tag` bayrağı, şekillerin metin akışının bir parçası (`True`) olup olmayacağını ya da ayrı kalıp kalmayacağını (`False`) belirler. Satır içi etiketleme, metin çıkarımını iyileştirir

## Sonraki Öğrenmeniz Gerekenler

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Word'den LaTeX Dışa Aktarma: DOCX'i Markdown'a Dönüştür ve PDF Olarak Kaydet](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)
- [C#'ta Word'ü PDF Olarak Kaydet – Şekil Dışa Aktarımlı DOCX'ten PDF'e Dönüştürme Tam Kılavuzu](/words/english/net/programming-with-pdfsaveoptions/save-word-as-pdf-in-c-full-guide-to-convert-docx-to-pdf-with/)
- [Word'den LaTeX Dışa Aktarma ve DOCX'i Markdown'a Dönüştürme](/words/english/python-net/document-conversion/how-to-export-latex-from-word-and-convert-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}