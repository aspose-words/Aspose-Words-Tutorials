---
category: general
date: 2026-10-13
description: Aspose.Words for Python kullanarak bozuk docx dosyalarını nasıl kurtaracağınızı,
  docx'i markdown’a, docx'i düz metne dönüştürmeyi ve belgeyi markdown olarak kaydetmeyi
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to recover corrupted word file
- convert docx to plain text
- how to save document as markdown
language: tr
lastmod: 2026-10-13
og_description: Aspose.Words for Python ile bozuk docx dosyalarını kurtarın ve docx'i
  markdown, düz metin ve PDF'ye dönüştürün. Bu eksiksiz öğreticiyi izleyin.
og_image_alt: Diagram showing recover corrupted docx workflow from loading to saving
  in multiple formats
og_title: Bozuk docx dosyasını kurtarın ve markdown, düz metin, PDF'ye dönüştürün
  – adım adım rehber
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to recover corrupted docx files, convert docx to markdown,
    convert docx to plain text, and save document as markdown using Aspose.Words for
    Python.
  headline: How to recover corrupted docx and convert it to markdown, plain text,
    and PDF with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document conversion
title: Bozuk docx dosyasını nasıl kurtarır ve Aspose.Words ile markdown, düz metin
  ve PDF'ye dönüştürürsünüz
url: /tr/python/document-conversion/how-to-recover-corrupted-docx-and-convert-it-to-markdown-pla/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bozuk docx dosyalarını kurtarma ve Aspose.Words ile markdown, düz metin ve PDF'ye dönüştürme

Eğer **bozuk docx** dosyalarını **kurtarmanız** gerekiyorsa, bu kılavuz size güvenilir, programatik bir yol gösterir. Python için Aspose.Words kullanarak hasar görmüş bir Word belgesini yükleyebilir, içeriğini çıkarabilir ve ardından **docx'i markdown'a dönüştürebilir**, **docx'i düz metne dönüştürebilir** veya sonucu PDF olarak kaydedebilirsiniz.

Bozuk bir dosyayı kurtarmak genellikle çıkmaz bir yol gibi hissettirir, ancak Aspose.Words'ün kurtarma modu süreci deterministik hâle getirir. Belge yüklendikten sonra, kütüphanenin desteklediği herhangi bir formata, LaTeX denklemleri içeren Markdown, düz‑metin dosyaları ve yüzen şekillerin satır içi etiketlere dönüştüğü PDF'ler dahil olmak üzere dışa aktarabilirsiniz.

Bu öğreticide şunları yapacaksınız:

* Potansiyel olarak bozuk bir `.docx` dosyasını kurtarma modu ile yüklemek.
* Office Math denklemlerini LaTeX olarak koruyarak belgeyi Markdown'a dışa aktarmak.
* Aynı içeriği LaTeX‑formatlı denklemlerle düz metin olarak kaydetmek.
* Yüzen şekilleri satır içi öğeler olarak işaretleyen bir PDF oluşturmak.
* İlk şeklin gölge etkisini ayarlayıp değiştirilmiş dosyayı kaydetmek.

Önkoşullar:

* Python 3.8+ yüklü.
* `aspose-words` paketi (`pip install aspose-words`).
* Bozuk olabilecek bir `.docx` dosyası (ör. `corrupted.docx`).

---

## Aspose.Words ile bozuk docx dosyasını kurtarma

Aspose.Words, bir kurtarma stratejisi belirlemenizi sağlayan bir `LoadOptions` sınıfı sunar. `recovery_mode` değerini `RECOVER` olarak ayarlamak, kütüphaneye yapısal sorunları düzeltmeye çalışmasını ve yüklemeye devam etmesini söyler.

```python
import aspose.words as aw

# Load the document in recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # RECOVER, SKIP, FAIL
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Neden bu çalışır:** Word dosyası kırık bölümler (eksik XML düğümleri, kesilmiş akışlar) içerdiğinde, kurtarma modu mümkün olanı ayrıştırır ve onarılamayan parçaları atar; bu sayede programı durduracak bir istisna oluşmaz.

> **Pro ipucu:** Yalnızca bozuk bölümleri atlamak ve onarım denemek istemiyorsanız `RecoveryMode.SKIP` kullanın. Katı doğrulama için `RecoveryMode.FAIL` herhangi bir sorun olduğunda bir hata fırlatır.

---

## docx'i markdown'a dönüştürme

Belge yüklendikten sonra, onu Markdown olarak kaydedebilirsiniz. `MarkdownSaveOptions` sınıfı, Office Math denklemlerinin nasıl dışa aktarılacağını kontrol etmenizi sağlar. `office_math_export_mode` değerini `LATEX` olarak ayarlamak, denklemlerin LaTeX kodu olarak görünmesini sağlar; bu, bilimsel belgeler için en taşınabilir temsildir.

```python
# Save as Markdown with LaTeX equations
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_options)
```

**Sonuç:** `output.md` orijinal Word dosyasının metin içeriğini, başlıklar, listeler ve tablolar Markdown sözdizimiyle render edilmiş şekilde içerir. Gömülü denklemler `$…$` LaTeX blokları olarak görünür.

> **Sık sorulan soru:** *Bu, DOC dosyalarıyla da çalışır mı?*  
> Evet. Aynı `MarkdownSaveOptions` `.doc` veya `.docx` girdileriyle kullanılabilir çünkü dönüşüm belge tamamen yüklendikten sonra gerçekleşir.

---

## docx'i düz metne dönüştürme

Düz‑metin dışa aktarımı, arama indeksleme veya hızlı ön izlemeler için faydalıdır. `TxtSaveOptions` sınıfı, Markdown seçeneklerine benzer şekilde Office Math için LaTeX formatını korumanıza izin verir; böylece denklemler bir `.txt` dosyasında bile LaTeX biçiminde kalır.

```python
# Save as plain text with LaTeX equations
txt_options = aw.saving.TxtSaveOptions()
txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_options)
```

**Sonuç:** `output.txt` belgenin ham metnini, satır sonlarını koruyarak ve denklemleri LaTeX dizgileri (ör. `\frac{a}{b}`) şeklinde temsil eder.

---

## PDF olarak kaydetme ve satır içi şekiller

PDF'ye dönüştürürken, yüzen şekillerin (metin kutuları, resimler) daha iyi erişilebilirlik veya sonraki işleme için satır içi öğeler gibi davranmasını isteyebilirsiniz. `PdfSaveOptions` sınıfı, bu davranışı zorlayan `export_floating_shapes_as_inline_tag` bayrağını sunar.

```python
# Export to PDF, tagging floating shapes as inline
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_options)
```

**Sonuç:** `output.pdf` orijinal Word dosyasının düzenini yansıtır, ancak herhangi bir yüzen şekil PDF yapısında satır içi bir etiket olarak işaretlenir; bu, birçok PDF ayrıştırıcısı tarafından metin akışının bir parçası olarak kabul edilir.

---

## Şekil gölge etkisini ayarlama (isteğe bağlı)

Bir şeklin görsel yönlerini (ör. bir sunumu güçlendirmek) değiştirmeniz gerekiyorsa, şekil düğümüne doğrudan erişebilir ve gölge özelliklerini değiştirebilirsiniz.

```python
# Locate the first shape in the document
shape = doc.get_child(aw.NodeType.SHAPE, 0, True).as_shape()

# Adjust shadow parameters
shape.shadow.blur = 5.0          # Blur radius
shape.shadow.offset_x = 2.0     # Horizontal offset
shape.shadow.offset_y = 2.0     # Vertical offset

# Save the modified document
doc.save("YOUR_DIRECTORY/shadowed.docx")
```

**Neden gölgeler ayarlanır:** Bulanıklık ve ofseti değiştirmek, bir şeklin sayfadan yükselmiş gibi görünmesini sağlar ve bu da basılı ya da ekranda görüntülenen belgelerin okunabilirliğini artırır.

---

## Tam çalışan örnek

Aşağıda, yukarıda açıklanan tüm adımları içeren tam betik yer almaktadır. Betiği `process_docx.py` olarak kaydedin ve komut satırından çalıştırın.

```python
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Load the potentially corrupted document using recovery mode.
# ------------------------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)

# ------------------------------------------------------------------
# 2. Export to Markdown (with LaTeX equations).
# ------------------------------------------------------------------
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_options)

# ------------------------------------------------------------------
# 3. Export to plain text (also with LaTeX equations).
# ------------------------------------------------------------------
txt_options = aw.saving.TxtSaveOptions()
txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_options)

# ------------------------------------------------------------------
# 4. Export to PDF, tagging floating shapes as inline.
# ------------------------------------------------------------------
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_options)

# ------------------------------------------------------------------
# 5. Optional: modify the first shape's shadow and save a new DOCX.
# ------------------------------------------------------------------
shape = doc.get_child(aw.NodeType.SHAPE, 0, True).as_shape()
shape.shadow.blur = 5.0
shape.shadow.offset_x = 2.0
shape.shadow.offset_y = 2.0
doc.save("YOUR_DIRECTORY/shadowed.docx")
```

**Beklenen çıktı dosyaları**

| Dosya                | Açıklama                                                |
|----------------------|--------------------------------------------------------|
| `output.md`          | LaTeX denklemleri içeren Markdown sürümü.              |
| `output.txt`         | Düz metin sürümü, denklemler LaTeX sözdiziminde.       |
| `output.pdf`         | Yüzen şekillerin satır içi etiket olarak işaretlendiği PDF. |
| `shadowed.docx`      | İlk şeklin gölgesi değiştirilmiş orijinal belge.       |

Betik çalıştırın ve her dosyanın `YOUR_DIRECTORY` içinde göründüğünden emin olun. Markdown dosyasını LaTeX destekleyen bir görüntüleyicide (ör. VS Code + Markdown ön izleme uzantısı) açarak denklemlerin doğru şekilde render edildiğini kontrol edin.

---

## Sık sorulan sorular

**Aspose olmadan bozuk Word dosyasını nasıl kurtarabilirim?**  
Microsoft Word'ün yerleşik “Aç ve Onar” özelliğini deneyebilirsiniz, ancak bu sınırlı kontrol sunar ve programatik dışa aktarım sağlamaz. Aspose.Words deterministik kurtarma sunar ve sonraki dönüşümleri otomatikleştirmenize izin verir.

**DOCX'i markdown'a resimleri kaybetmeden dönüştürebilir miyim?**  
`MarkdownSaveOptions` kullanıldığında, resimler `.md` dosyasının yanındaki bir alt klasöre ayrı dosyalar olarak kaydedilir. Markdown, görsel düzeni koruyan göreceli yollarla bu resim dosyalarına referans verir.

**Belge birleştirilmiş hücreli bir tablo içeriyorsa ne olur?**  
Aspose.Words, birleştirilmiş hücreleri hem Markdown hem de düz metin dönüşümünde korur. Markdown'ta birleştirilmiş hücreler uygun boru (`|`) ayırıcılarıyla normal hücrelere dönüşür; düz metinde ise boşluklu sütunlar olarak görünür.

**LaTeX dışa aktarma modu eski Aspose.Words sürümleriyle uyumlu mu?**  
LaTeX dışa aktarma, 22.10 sürümünde tanıtıldı. Daha eski bir sürüm kullanıyorsanız, bu özellik mevcut olmayacak ve denklemler MathML'e geri düşecektir.

---

## Sonraki adımlar

Artık **bozuk docx dosyasını kurtarmayı**, **docx'i markdown'a dönüştürmeyi**, **docx'i düz metne dönüştürmeyi** ve **belgeyi markdown olarak kaydetmeyi** bildiğinize göre iş akışını genişletebilirsiniz:

* **Toplu işleme** – bozuk dosyalar klasörünü dolaşarak tek bir çalıştırmada tüm hedef formatları üretin.
* **Bulut dağıtımı** – betiği bir Azure Function veya AWS Lambda içinde paketleyerek talep üzerine dönüşüm sağlayan bir web servisi oluşturun.
* **Ek format desteği** – ek dışa aktarma yetenekleri için `HtmlSaveOptions`, `EpubSaveOptions` veya `MhtmlSaveOptions` keşfedin.

Aspose.Words tarafından sunulan seçeneklerle görüntü işleme, font gömme veya PDF güvenlik ayarlarını ince ayar yapın. Kütüphanenin kapsamlı API'si, kurtarmadan yayınlamaya hazır varlıklara kadar tam bir belge‑işleme hattı oluşturmanıza olanak tanır.

---


## Bir Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanıza ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım‑adım açıklamalarla tam çalışan kod örnekleri içerir.

- [Word'den LaTeX Dışa Aktarma – DOCX'i Markdown'a Dönüştürme](/words/english/python-net/document-conversion/how-to-export-latex-from-word-convert-docx-to-markdown/)
- [Aspose.Words ile Word'u Markdown Olarak Kaydet – DOCX'i Dönüştürme ve Görselleri Çıkarma Tam Kılavuzu](/words/english/net/programming-with-markdownsaveoptions/save-word-as-markdown-complete-guide-to-convert-docx-and-ext/)
- [docx'i kurtarma – kurtarma modunu ayarla ve bozuk Word dosyalarını aç](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}