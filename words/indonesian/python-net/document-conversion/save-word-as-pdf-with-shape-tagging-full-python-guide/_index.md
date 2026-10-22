---
category: general
date: 2026-05-30
description: Simpan Word sebagai PDF dengan penandaan bentuk di Python. Konversi docx
  ke PDF, buat PDF dapat diakses, dan pelajari cara menandai bentuk mengambang untuk
  meningkatkan aksesibilitas.
draft: false
keywords:
- save word as pdf
- convert docx to pdf
- convert word document pdf
- make pdf accessible
- how to tag shapes
language: id
og_description: Simpan Word sebagai PDF menggunakan Python dan beri tag pada bentuk
  mengambang untuk aksesibilitas. Pelajari cara mengonversi docx ke PDF dan membuat
  PDF dapat diakses dalam hitungan menit.
og_title: Simpan Word sebagai PDF dengan Penandaan Bentuk – Panduan Python Lengkap
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Save Word as PDF with shape tagging in Python. Convert docx to pdf,
    make pdf accessible, and learn how to tag floating shapes for better accessibility.
  headline: Save Word as PDF with Shape Tagging – Full Python Guide
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for Python via .NET runs on .NET Core, which is cross‑platform.
      Just install the appropriate runtime (`dotnet-sdk-6.0` or later) and the `aspose-words`
      package.
    question: Does this work on Linux?
  - answer: Absolutely. Wrap the `convert_word_to_accessible_pdf` call in a `for`
      loop that iterates over `os.listdir()` and filters for `*.docx`.
    question: Can I batch‑process a folder of .docx files?
  - answer: Iterate over `doc.get_child_nodes(aw.NodeType.SHAPE, True)` and set `shape.title`
      or `shape.alternative_text` before saving.
    question: What if I need to add custom alt text to each shape?
  - answer: 'The inline tagging respects the original layout; however, if you enable
      PDF/A compliance, some visual tweaks (like color profiles) might be applied
      automatically. ## Wrapping Up We’ve just covered how to **save Word as PDF**
      while ensuring that floating shapes are tagged correctly for accessibility.'
    question: Is there a way to keep the original layout exactly the same?
  type: FAQPage
tags:
- Aspose.Words
- PDF conversion
- Python
- Document automation
title: Simpan Word sebagai PDF dengan Penandaan Bentuk – Panduan Python Lengkap
url: /id/python/document-conversion/save-word-as-pdf-with-shape-tagging-full-python-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan Word sebagai PDF dengan Penandaan Bentuk – Panduan Python Lengkap

Pernah bertanya-tanya bagaimana cara **save Word as PDF** sambil menjaga bentuk mengambang tetap dapat diakses? Anda tidak sendirian. Di banyak lingkungan dengan kepatuhan yang ketat, PDF biasa tidak cukup—pembaca layar membutuhkan tag yang tepat, terutama untuk bentuk yang melayang di atas teks.  

Dalam tutorial ini kami akan menelusuri contoh lengkap yang dapat dijalankan yang menunjukkan cara **convert docx to pdf**, mengonfigurasi opsi PDF sehingga outputnya secara visual benar *dan* dapat diakses, serta akhirnya menandai bentuk dengan cara yang tepat. Pada akhir Anda akan memiliki solusi satu‑file yang dapat dimasukkan ke proyek Python mana pun.

## Apa yang Akan Anda Pelajari

- Muat dokumen Word yang berisi bentuk mengambang (gambar, kotak teks, diagram).  
- Gunakan Aspose.Words for Python via .NET untuk **convert Word document pdf** dengan penandaan khusus.  
- Aktifkan mode penandaan *inline* sehingga PDF memenuhi standar aksesibilitas.  
- Verifikasi hasil dan tangani jebakan umum seperti font yang hilang atau gambar berukuran terlalu besar.  

Tidak ada layanan eksternal, tidak ada trik baris perintah yang rumit—hanya kode Python biasa dan beberapa catatan penjelasan.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

| Persyaratan | Alasan |
|-------------|--------|
| Python 3.9+ | Diperlukan oleh paket Aspose .Words for Python via .NET. |
| `aspose-words` NuGet package installed (via `pip install aspose-words`) | Menyediakan namespace `aw` yang digunakan dalam contoh. |
| File `.docx` dengan setidaknya satu bentuk mengambang (misalnya, kotak teks) | Menunjukkan fitur penandaan. |
| Opsional: validator PDF/A‑1a (mis., veraPDF) jika Anda perlu mengesahkan aksesibilitas. | Membantu Anda memastikan PDF benar-benar dapat diakses. |

Jika Anda belum pernah menggunakan Aspose.Words sebelumnya, anggaplah sebagai “pisau Swiss” untuk manipulasi dokumen—jauh lebih kuat daripada pustaka `python-docx` bawaan, terutama ketika Anda memerlukan output PDF dengan kontrol yang sangat detail.

## Langkah 1: Instal dan Impor Aspose.Words

Pertama-tama—instal pustaka dan impor kelas yang diperlukan. Langkah ini singkat, tetapi melewatkannya akan membuat Anda melihat `ImportError` nanti.

```bash
pip install aspose-words
```

```python
# Step 1: Import the Aspose.Words namespace
import aspose.words as aw
```

> **Pro tip:** Jika Anda bekerja dalam lingkungan virtual, aktifkan dulu sebelum menjalankan perintah `pip`. Dengan begitu Anda menjaga ketergantungan proyek tetap rapi.

## Langkah 2: Muat Dokumen Word yang Berisi Bentuk Mengambang

Sekarang kita benar‑benarnya membuka file sumber. Konstruktor `Document` menerima path atau stream, sehingga Anda dapat memberikannya apa saja mulai dari file lokal hingga objek S3.

```python
# Step 2: Load the source .docx
input_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(input_path)
```

> **Mengapa ini penting:** Memuat dokumen memberi kami akses ke pohon node internalnya, di mana bentuk mengambang direpresentasikan sebagai objek `Shape`. Jika file tidak ada, Aspose akan mengeluarkan `FileNotFoundError`, yang dapat Anda tangkap dan tangani dengan elegan.

## Langkah 3: Konfigurasikan Opsi Penyimpanan PDF untuk Penandaan Bentuk yang Dapat Diakses

Berikut inti tutorial. Secara default Aspose.Words menyimpan bentuk mengambang sebagai tag *block‑level*, yang banyak teknologi bantu anggap sebagai elemen terpisah, bukan urutan bacaan. Menetapkan `export_floating_shapes_as_inline_tag` ke `True` memaksa bentuk ditandai *inline*, mempertahankan urutan bacaan dan meningkatkan pengalaman pembaca layar.

```python
# Step 3: Create PDF save options and enable inline shape tagging
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True   # True → inline (accessible) tagging
```

> **Cara kerjanya:** Ketika `export_floating_shapes_as_inline_tag` bernilai `True`, Aspose menyisipkan tag `<Figure>` di sekitar setiap bentuk dan menempatkannya dalam alur dokumen. Ini adalah pendekatan yang direkomendasikan untuk **make pdf accessible** compliance, terutama di bawah Pedoman WCAG 2.1 Guideline 1.3.1.

### Penyesuaian Opsional

| Opsi | Deskripsi | Nilai Umum |
|------|-----------|------------|
| `pdf_opts.compliance` | Menetapkan tingkat kepatuhan PDF/A (mis., PDF/A‑1a). | `aw.saving.PdfCompliance.PDF_A_1A` |
| `pdf_opts.embed_full_fonts` | Menyematkan semua font yang digunakan untuk menghindari substitusi. | `True` |
| `pdf_opts.save_format` | Memaksa format output (berguna jika Anda nanti beralih ke XPS). | `aw.SaveFormat.PDF` |

Anda dapat menggabungkan pengaturan ini jika proyek Anda memiliki persyaratan yang lebih ketat.

## Langkah 4: Simpan Dokumen sebagai PDF Menggunakan Opsi yang Dikonfigurasi

Akhirnya, kami menulis file output. Metode `save` menerima path tujuan dan objek opsi yang baru saja kami konfigurasikan.

```python
# Step 4: Save the document as a PDF with the accessible tagging options
output_path = "YOUR_DIRECTORY/output.pdf"
doc.save(output_path, pdf_opts)
print(f"✅ PDF saved to {output_path}")
```

Itu saja—operasi **convert word document pdf** Anda selesai. PDF yang dihasilkan akan memiliki bentuk mengambang yang ditandai inline, membuatnya jauh lebih ramah bagi teknologi bantu.

## Memverifikasi PDF yang Dapat Diakses

Jika Anda ingin memastikan bahwa PDF benar‑benar memenuhi standar aksesibilitas, buka di Adobe Acrobat Pro dan periksa panel **Tags**. Anda harus melihat entri seperti:

```
/Figure
  /Alt (optional alt text you may have set)
  /Para
```

Atau, jalankan validator baris perintah:

```bash
verapdf --format text output.pdf
```

Jika validator mengembalikan “No errors,” Anda telah berhasil **make pdf accessible**.

## Kasus Edge Umum & Cara Menanganinya

| Situasi | Apa yang Mungkin Salah | Solusi yang Disarankan |
|---------|------------------------|------------------------|
| **Dokumen berisi banyak gambar resolusi tinggi** | Ukuran PDF membengkak, kinerja menurun. | Setel `pdf_opts.jpeg_quality = 80` atau turunkan resolusi gambar dengan `doc.get_child_nodes(aw.NodeType.SHAPE, True)` sebelum menyimpan. |
| **Font yang hilang di server** | Teks muncul dengan font cadangan, merusak tata letak. | Aktifkan `pdf_opts.embed_full_fonts = True` dan pastikan font yang diperlukan terpasang di OS host. |
| **Bentuk tidak memiliki teks alt** | Alat aksesibilitas membaca “Figure” tanpa deskripsi. | Iterasi bentuk dan tetapkan `shape.title = "Description"` sebelum menyimpan. |
| **Dokumen besar (>100 MB)** | Kesalahan out‑of‑memory pada runtime 32‑bit. | Gunakan `PdfSaveOptions.memory_usage_setting = aw.saving.MemoryUsageSetting.LOW` untuk men-stream konten. |
| **Anda membutuhkan PDF/A‑2b bukan PDF/A‑1a** | Ketidaksesuaian kepatuhan. | Setel `pdf_opts.compliance = aw.saving.PdfCompliance.PDF_A_2B`. |

Menangani skenario ini lebih awal menyelamatkan Anda dari harus mengulang konversi nanti.

## Contoh Kerja Lengkap

Berikut skrip lengkap yang dapat Anda salin‑tempel ke file bernama `convert_to_accessible_pdf.py`. Ganti `YOUR_DIRECTORY` dengan jalur folder yang sebenarnya.

```python
import aspose.words as aw

def convert_word_to_accessible_pdf(input_docx: str, output_pdf: str) -> None:
    """
    Loads a Word document, configures PDF save options to tag floating shapes inline,
    and saves the result as an accessible PDF.
    """
    # Load the .docx file
    doc = aw.Document(input_docx)

    # Configure PDF options for accessible shape tagging
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True   # Inline tagging for accessibility
    pdf_opts.compliance = aw.saving.PdfCompliance.PDF_A_1A  # Optional: enforce PDF/A‑1a
    pdf_opts.embed_full_fonts = True                       # Ensure fonts are embedded

    # Save the PDF
    doc.save(output_pdf, pdf_opts)
    print(f"✅ Successfully saved accessible PDF to: {output_pdf}")

if __name__ == "__main__":
    # Adjust these paths as needed
    INPUT_PATH = "YOUR_DIRECTORY/input.docx"
    OUTPUT_PATH = "YOUR_DIRECTORY/output.pdf"

    convert_word_to_accessible_pdf(INPUT_PATH, OUTPUT_PATH)
```

Menjalankan skrip:

```bash
python convert_to_accessible_pdf.py
```

Anda akan melihat pesan konfirmasi, dan `output.pdf` akan berisi bentuk yang ditandai inline siap untuk pembaca layar.

## Pertanyaan yang Sering Diajukan

**Q: Apakah ini bekerja di Linux?**  
A: Ya. Aspose.Words for Python via .NET berjalan di .NET Core, yang lintas‑platform. Cukup instal runtime yang sesuai (`dotnet-sdk-6.0` atau lebih baru) dan paket `aspose-words`.

**Q: Bisakah saya memproses batch folder .docx?**  
A: Tentu saja. Bungkus pemanggilan `convert_word_to_accessible_pdf` dalam loop `for` yang mengiterasi `os.listdir()` dan menyaring `*.docx`.

**Q: Bagaimana jika saya perlu menambahkan teks alt khusus ke setiap bentuk?**  
A: Iterasi `doc.get_child_nodes(aw.NodeType.SHAPE, True)` dan setel `shape.title` atau `shape.alternative_text` sebelum menyimpan.

**Q: Apakah ada cara untuk menjaga tata letak asli persis sama?**  
A: Penandaan inline menghormati tata letak asli; namun, jika Anda mengaktifkan kepatuhan PDF/A, beberapa penyesuaian visual (seperti profil warna) mungkin diterapkan secara otomatis.

## Menyimpulkan

Kami baru saja membahas cara **save Word as PDF** sambil memastikan bahwa bentuk mengambang ditandai dengan benar untuk aksesibilitas. Langkah‑langkahnya—muat, konfigurasikan, simpan—


## Apa yang Harus Anda Pelajari Selanjutnya?

- [Buat PDF Aksesibel dari Word – Konversi ke PDF/UA](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-word-convert-to-pdf-ua/)
- [Simpan Word sebagai PDF dengan Aspose.Words – Panduan C# Lengkap](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}