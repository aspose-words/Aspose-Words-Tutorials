---
category: general
date: 2026-11-25
description: Aspose.Words kullanarak docx dosyasını pdf olarak kaydetmeyi, docx'i
  pdf'ye dönüştürmeyi ve yüzen şekilleri tek adımda satır içi etiketler olarak dışa
  aktarmayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx as pdf
- convert docx to pdf
- how to export shapes
- convert word to pdf
- aspose docx to pdf
language: tr
lastmod: 2026-11-25
og_description: Aspose.Words kullanarak docx'i pdf olarak kaydedin, docx'i pdf'e dönüştürün
  ve mükemmel PDF çıktısı için şekilleri satır içi etiketler olarak dışa aktarmayı
  öğrenin.
og_image_alt: Screenshot showing a DOCX file being saved as PDF with shapes preserved
og_title: Aspose.Words ile docx'i pdf olarak kaydedin – şekilleri doğru şekilde dışa
  aktar
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to save docx as pdf using Aspose.Words, convert docx to pdf,
    and export floating shapes as inline tags in a single step.
  headline: How to save docx as pdf with Aspose.Words while exporting shapes
  type: TechArticle
- description: Learn how to save docx as pdf using Aspose.Words, convert docx to pdf,
    and export floating shapes as inline tags in a single step.
  name: How to save docx as pdf with Aspose.Words while exporting shapes
  steps:
  - name: Converting multiple DOCX files in a batch
    text: 'When you need to **convert docx to pdf** for many files, wrap the three
      steps in a loop:'
  - name: Dealing with very large documents
    text: For large Word files, consider enabling `pdf_opts.save_format = aw.SaveFormat.PDF`
      (the default) and adjusting `pdf_opts.compliance` if you need PDF/A compliance.
      These options do not affect shape export but improve compatibility with archival
      systems.
  - name: When shapes should remain floating
    text: If a specific document requires floating shapes to stay floating (e.g.,
      a design‑heavy brochure), set the flag to `False`. The PDF will then render
      shapes as separate drawing objects, which may be preferable for precise graphic
      positioning.
  type: HowTo
tags:
- Aspose.Words
- PDF conversion
- Word automation
title: Şekilleri dışa aktarırken Aspose.Words ile docx'i PDF olarak nasıl kaydedilir
url: /tr/python/document-conversion/how-to-save-docx-as-pdf-with-aspose-words-while-exporting-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ile Şekilleri Dışa Aktarırken docx'i pdf olarak kaydetme

Eğer **docx'i pdf olarak kaydetmek** ve her yüzen şekli tam olarak bulunduğu yerde tutmak istiyorsanız, bu kılavuz size tam süreci gösterir. Eğitim sonunda bir Word belgesini PDF dosyasına dönüştürebilecek, şekilleri doğru şekilde dışa aktarabilecek ve her ayarın neden önemli olduğunu anlayacaksınız.

Word dosyalarını PDF'ye dönüştürmek, fatura oluşturma, rapor yayınlama ve belge arşivleme için yaygın bir gereksinimdir. Bu eğitim, **convert docx to pdf** iş akışını kapsar, **how to export shapes** açıklamasıyla şekillerin satır içi görünmesini sağlar ve Aspose.Words kütüphanesini kullanarak **convert word to pdf** işlemini gösterir. Aspose.Words for Python via .NET paketinin dışındaki hiçbir araç gerekmez.

## Önkoşullar

* Python 3.9+ yüklü geliştirme makinenizde.  
* `aspose-words` paketi (`pip install aspose-words` ile kurulabilir).  
* Yüzen şekiller içeren bir DOCX dosyası (ör. metin kutuları, resimler veya SmartArt).  
* Çıktı dizinine yazma izni.  

Bu önkoşulların hepsi serbest formdadır; eğitim Windows, macOS ve Linux'ta çalışır.

## Adım 1: Kaynak belgeyi yükleyin

İlk işlem, DOCX dosyasını bir `aw.Document` nesnesine yüklemektir. Bu nesne, tüm Word belgesini bellekte temsil eder ve bölümlerine, paragraflarına ve çizim nesnelerine erişim sağlar.

```python
import aspose.words as aw

# Step 1: Load the source document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

**Bu adımın önemi:**  
Dosyanın yüklenmesi, Aspose.Words'un manipüle edebileceği yapılandırılmış bir nesne modeli oluşturur. Bu model olmadan sonraki PDF dönüşümü okunacak bir kaynağa sahip olmaz.

## Adım 2: PDF kaydetme seçeneklerini yapılandırın ve yüzen şekiller için satır içi dışa aktarmayı etkinleştirin

Aspose.Words, çıktıyı PDF olarak ince ayar yapmanızı sağlayan bir `PdfSaveOptions` sınıfı sunar. `export_floating_shapes_as_inline_tag` özelliği, yüzen şekillerin satır içi `<w:wrap>` etiketleri olarak (PDF render'ı bu etiketleri metin akışının bir parçası olarak işler) yoksa ayrı çizim nesneleri olarak render edilip edilmediğini kontrol eder.

```python
# Step 2: Create PDF save options and enable inline export for floating shapes
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True
```

**Bu ayarın önemi:**  
**how to export shapes** doğru şekilde yaptığınızda, bir şeklin kaybolması veya PDF'de beklenmedik bir konuma kayması gibi yaygın sorunu önlersiniz. Bayrağı `True` olarak ayarlamak, render'ı her yüzen şekli satır içi sabitlenmiş gibi ele almasını söyler ve düzen doğruluğunu korur. Bu, çoğu iş belgesi için önerilen yaklaşımdır.

## Adım 3: Belgeyi yapılandırılmış seçeneklerle PDF olarak kaydedin

Belge yüklendi ve kaydetme seçenekleri hazır olduğunda, PDF dosyasını diske yazabilirsiniz.

```python
# Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

**Bu son adım iş akışını tamamlamasının nedeni:**  
`PdfSaveOptions` örneğiyle `doc.save` çağrısı, dönüşüm hattını tetikler. Aspose.Words DOCX yapısını okur, satır içi‑şekil kuralını uygular ve orijinal düzeni yansıtan bir PDF yazar. Bu çağrıdan sonra, `output.pdf` kaynak DOCX ile aynı metin, resim ve şekilleri içerir.

## Beklenen çıktı

- `output.pdf` hedef klasörde görünür.  
- Tüm paragraflar, tablolar ve yüzen şekiller (metin kutuları, resimler, SmartArt) `input.docx`'deki gibi tam konumlarında bulunur.  
- Dosya boyutu, şekil dışa aktarım ayarları yapılmadan bir Word belgesinden oluşturulan standart PDF ile karşılaştırılabilir.  

PDF'yi Adobe Acrobat veya herhangi bir modern görüntüleyicide açarsanız, eksik grafik veya kaymış öğe görmemelisiniz.

## Yaygın varyasyonlar ve uç durumlar

### Bir toplu işlemde birden fazla DOCX dosyasını dönüştürme

Birçok dosya için **convert docx to pdf** yapmanız gerektiğinde, üç adımı bir döngü içinde sarın:

```python
import pathlib

source_dir = pathlib.Path("YOUR_DIRECTORY")
for docx_path in source_dir.glob("*.docx"):
    doc = aw.Document(str(docx_path))
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True
    pdf_path = docx_path.with_suffix(".pdf")
    doc.save(str(pdf_path), pdf_opts)
```

### Çok büyük belgelerle başa çıkma

Büyük Word dosyaları için, `pdf_opts.save_format = aw.SaveFormat.PDF` (varsayılan) etkinleştirmeyi ve PDF/A uyumluluğu gerekiyorsa `pdf_opts.compliance` ayarlamayı düşünün. Bu seçenekler şekil dışa aktarımını etkilemez ancak arşiv sistemleriyle uyumluluğu artırır.

### Şekillerin yüzen kalması gerektiğinde

Belirli bir belgenin yüzen şekilleri yüzen tutması gerekiyorsa (ör. tasarım ağırlıklı bir broşür), bayrağı `False` olarak ayarlayın. PDF daha sonra şekilleri ayrı çizim nesneleri olarak render eder; bu, kesin grafik konumlandırması için tercih edilebilir.

## Pro ipuçları

- **Pro tip:** PDF'yi hedef görüntüleyicide (ör. Chrome, Edge, Acrobat) her zaman test edin çünkü bazı görüntüleyiciler satır içi etiketleri biraz farklı yorumlayabilir.  
- **Watch out for:** Eski VML çizim formatlarını kullanan belgeler; Aspose.Words VML'yi otomatik olarak modern çizim nesnelerine dönüştürür, ancak karmaşık VML ek temizlik gerektirebilir.  
- **Performance tip:** Birçok dosya işlenirken tek bir `PdfSaveOptions` örneğini yeniden kullanarak nesne tahsis yükünü azaltın.

## Tam, çalıştırılabilir örnek

Aşağıda, `docx_to_pdf.py` adlı bir dosyaya kopyalayıp yapıştırabileceğiniz tam betik bulunmaktadır. `YOUR_DIRECTORY` ifadesini makinenizdeki gerçek yol ile değiştirin.

```python
import aspose.words as aw
import pathlib

def convert_docx_to_pdf(input_path: pathlib.Path, output_path: pathlib.Path):
    """
    Loads a DOCX file, configures PDF save options to export floating shapes as inline tags,
    and writes the result to a PDF file.
    """
    # Load the DOCX document
    doc = aw.Document(str(input_path))

    # Configure PDF options – export floating shapes as inline tags
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True

    # Save the PDF
    doc.save(str(output_path), pdf_opts)

if __name__ == "__main__":
    base_dir = pathlib.Path("YOUR_DIRECTORY")
    input_file = base_dir / "input.docx"
    output_file = base_dir / "output.pdf"

    convert_docx_to_pdf(input_file, output_file)
    print(f"Conversion complete: {output_file}")
```

`python docx_to_pdf.py` çalıştırmak, tüm şekiller korunmuş `output.pdf` üretir. Betik, **aspose docx to pdf** yeteneğini temiz ve yeniden kullanılabilir bir fonksiyon içinde gösterir.

## Sonuç

Artık Aspose.Words kullanarak **docx'i pdf olarak kaydetmeyi**, şekil dışa aktarımını kontrol ederken **docx'i pdf'e dönüştürmeyi** ve `export_floating_shapes_as_inline_tag` bayrağının güvenilir düzen korumasının anahtarı olduğunu biliyorsunuz. Bu yaklaşım **convert word to pdf** senaryosu için çalışır, toplu işlemeyi destekler ve belge başına şekil işleme ayarlarını esnek bir şekilde yapmanıza olanak tanır.

Sonra, **PDF'lere filigran ekleme**, **PDF çıktısını sıkıştırma** veya **DOCX'i HTML veya EPUB gibi diğer formatlara dönüştürme** gibi ilgili konuları keşfedin. Bu özelliklerin her biri, burada kullandığınız aynı `aw.Document` nesne modeline dayanır, böylece otomasyon hattınızı güvenle genişletebilirsiniz.

Kodlamaktan keyif alın ve sorunsuz PDF sonuçlarının tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki eğitimler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Aspose.Words ile Python'da docx'i pdf olarak kaydetme](/words/english/python-net/document-conversion/how-to-save-docx-as-pdf-with-aspose-words-in-python/)
- [C#'ta Word'ü PDF olarak kaydetme – Şekil Dışa Aktarımlı DOCX'ten PDF'e Tam Rehber](/words/english/net/programming-with-pdfsaveoptions/save-word-as-pdf-in-c-full-guide-to-convert-docx-to-pdf-with/)
- [Aspose.Words kullanarak docx'i pdf olarak kaydetme ve eksik fontları tespit etme](/words/english/net/working-with-fonts/save-docx-as-pdf-detect-missing-fonts-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}