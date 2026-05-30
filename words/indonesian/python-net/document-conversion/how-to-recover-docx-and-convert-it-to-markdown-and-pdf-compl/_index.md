---
category: general
date: 2026-05-30
description: Pelajari cara memulihkan docx, mengatur bayangan, dan mengonversi markdown
  docx menjadi markdown dan PDF menggunakan Aspose.Words untuk Python. Kode langkah
  demi langkah disertakan.
draft: false
keywords:
- how to recover docx
- convert docx markdown
- save as markdown
- save as pdf
- how to set shadow
language: id
og_description: Cara memulihkan docx, menetapkan bayangan, dan menyimpan sebagai markdown
  atau pdf dengan Aspose.Words. Panduan lengkap untuk pengembang.
og_title: Cara Memulihkan DOCX dan Mengonversi ke Markdown & PDF – Tutorial Python
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Learn how to recover docx, set shadow, and convert docx markdown to
    both markdown and pdf using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to Recover DOCX and Convert It to Markdown and PDF – Complete Python
    Guide
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document Conversion
title: Cara Memulihkan DOCX dan Mengonversinya ke Markdown serta PDF – Panduan Python
  Lengkap
url: /id/python/document-conversion/how-to-recover-docx-and-convert-it-to-markdown-and-pdf-compl/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Memulihkan DOCX dan Mengonversinya ke Markdown serta PDF – Panduan Python Lengkap

Pernah bertanya-tanya **bagaimana cara memulihkan docx** yang tidak dapat dibuka di Word? Mungkin Anda menerima laporan rusak dari klien, atau pekerjaan batch malam menghasilkan dokumen setengah jadi. Pada saat-saat seperti itu Anda tidak hanya menginginkan tombol “coba lagi”—Anda memerlukan cara yang andal untuk mengekstrak bagian yang baik, menyesuaikan tampilan, dan kemudian mengirimkan hasilnya dalam format yang sebenarnya digunakan pemangku kepentingan Anda.

Itulah yang akan kita lakukan dalam tutorial ini. Kami akan menunjukkan cara memulihkan DOCX, **cara menambahkan bayangan** pada bentuk pertama, kemudian **mengonversi docx ke markdown**, **menyimpan sebagai markdown**, dan akhirnya **menyimpan sebagai pdf**—semua dengan pustaka kuat Aspose.Words untuk Python. Pada akhir tutorial Anda akan memiliki satu skrip yang mengubah file Word yang rusak menjadi output Markdown dan PDF yang bersih, lengkap dengan efek bayangan halus pada grafik apa pun.

> **Tip:** Kode ini bekerja dengan Aspose.Words 22.12 atau yang lebih baru; versi yang lebih lama mungkin tidak mendukung beberapa flag kepatuhan PDF/UA terbaru.

---

## Apa yang Anda Butuhkan

Sebelum kita mulai, pastikan Anda memiliki hal‑hal berikut:

| Persyaratan | Alasan |
|-------------|--------|
| Python 3.8+ | Sintaks modern dan tipe hint |
| paket `aspose-words` (`pip install aspose-words`) | Pustaka inti untuk memuat, mengedit, dan menyimpan |
| File DOCX (bahkan yang rusak) | Dokumen sumber |
| Familiaritas dasar dengan fungsi Python | Agar alur mudah diikuti |

Itu saja—tidak ada DLL tambahan, tidak perlu instalasi Office, dan tidak ada panggilan sistem yang rumit. Aspose.Words menangani semua pekerjaan berat secara internal.

---

## ## Cara Memulihkan DOCX dan Melanjutkan Pengerjaan

Hal pertama yang harus kita lakukan adalah memuat dokumen yang mungkin rusak dalam **mode pemulihan**. Aspose.Words menyediakan kelas `DocumentLoadOptions` di mana Anda dapat mengaktifkan `RecoveryMode`. Ketika diatur ke `RECOVER`, pustaka akan berusaha membangun kembali pohon node internal, hanya membuang bagian yang tidak dapat diperbaiki.

```python
import aspose.words as aw

# -------------------------------------------------
# Step 1 – Load the DOCX with recovery enabled
# -------------------------------------------------
load_opts = aw.loading.DocumentLoadOptions()
load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER

# Replace YOUR_DIRECTORY with the real path to your file
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_opts)

print("Document loaded. Nodes recovered:", doc.get_child_nodes(aw.NodeType.ANY, True).get_count())
```

**Mengapa ini penting:** Jika Anda melewatkan pemulihan, konstruktor `Document` akan melemparkan pengecualian begitu menemukan korupsi, menghentikan seluruh alur kerja. Dengan mengaktifkan pemulihan Anda mendapatkan objek `Document` yang dapat digunakan meskipun Word menolak membuka file tersebut.

---

## ## Cara Menambahkan Bayangan pada Bentuk Pertama

Bayangan halus dapat membuat logo atau diagram lebih menonjol, terutama ketika Anda kemudian mengekspor ke PDF/UA di mana aturan aksesibilitas berlaku. Cuplikan kode berikut mengambil node `Shape` pertama dalam dokumen dan mengonfigurasi `ShadowFormat`‑nya.

```python
# -------------------------------------------------
# Step 2 – Find the first shape and apply a shadow
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True).as_shape()
shadow = first_shape.shadow_format

# Enable the shadow and tweak its appearance
shadow.visible = True
shadow.distance = 4          # distance of the shadow from the shape (points)
shadow.blur = 6              # blur radius (points)
shadow.color = aw.Color.gray
shadow.opacity = 0.7         # 70% opacity for a soft look

print("Shadow applied to shape:", first_shape.name)
```

**Kesalahan umum:** Jika dokumen tidak mengandung bentuk apa pun, `get_child` mengembalikan `None` dan skrip akan crash. Sebuah guard clause singkat dapat menyelamatkan Anda:

```python
if first_shape is not None:
    # apply shadow (as above)
else:
    print("No shapes found – skipping shadow step.")
```

---

## ## Mengonversi DOCX ke Markdown (Simpan sebagai Markdown)

Setelah dokumen dalam kondisi baik dan penyesuaian visual diterapkan, mari **mengonversi docx ke markdown**. Aspose.Words dapat menghasilkan Markdown sekaligus menangani persamaan Office Math, yang akan kami ekspor sebagai LaTeX untuk fidelitas maksimum.

```python
# -------------------------------------------------
# Step 3 – Export to Markdown, preserving Math as LaTeX
# -------------------------------------------------
md_options = aw.saving.MarkdownSaveOptions()
md_options.office_math_export_mode = aw.saving.MarkdownOfficeMathExportMode.LATEX

# Again, replace the path with your desired output location
md_path = "YOUR_DIRECTORY/Combined.md"
doc.save(md_path, md_options)

print("Markdown file saved to:", md_path)
```

**Apa yang akan Anda lihat:** File `.md` yang dihasilkan berisi sintaks Markdown standar untuk paragraf, judul, dan daftar, sementara persamaan yang disisipkan muncul sebagai blok LaTeX yang dibungkus dengan `$$ … $$`. Buka di VS Code atau penampil Markdown apa pun untuk memverifikasi.

---

## ## Menyimpan sebagai PDF dengan Aksesibilitas (Simpan sebagai PDF)

Akhirnya, kita akan **menyimpan sebagai pdf** sambil memastikan bentuk mengambang yang kita ubah sebelumnya diekspor sebagai elemen inline‑tag. Ini menjaga tata letak konsisten di semua penampil dan memenuhi kepatuhan PDF/UA 1 untuk aksesibilitas.

```python
# -------------------------------------------------
# Step 4 – Export to PDF/UA with inline‑tagged floating shapes
# -------------------------------------------------
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
pdf_options.compliance = aw.saving.PdfCompliance.PDF_UA_1

pdf_path = "YOUR_DIRECTORY/Combined.pdf"
doc.save(pdf_path, pdf_options)

print("PDF file saved to:", pdf_path)
```

**Mengapa PDF/UA?** PDF/UA (Universal Accessibility) menambahkan tag yang dapat diinterpretasikan pembaca layar, menjadikan dokumen Anda lebih ramah bagi pengguna dengan disabilitas. Flag `export_floating_shapes_as_inline_tag` juga mencegah bentuk terlepas dari teks di sekitarnya, yang biasanya menjadi sumber pergeseran tata letak.

---

## ## Skrip Lengkap – Solusi Satu‑Pintu

Menggabungkan semuanya, berikut skrip siap‑jalankan yang mencakup **cara memulihkan docx**, **cara menambahkan bayangan**, **mengonversi docx ke markdown**, **menyimpan sebagai markdown**, dan **menyimpan sebagai pdf**. Salin, tempel, dan sesuaikan jalur file agar cocok dengan lingkungan Anda.

```python
import aspose.words as aw

def recover_and_convert(input_path: str, output_dir: str):
    # ---------- Load with recovery ----------
    load_opts = aw.loading.DocumentLoadOptions()
    load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    doc = aw.Document(input_path, load_opts)
    print(f"Loaded '{input_path}'. Node count:", doc.get_child_nodes(aw.NodeType.ANY, True).get_count())

    # ---------- Apply shadow to first shape ----------
    first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if first_shape is not None:
        shape = first_shape.as_shape()
        shadow = shape.shadow_format
        shadow.visible = True
        shadow.distance = 4
        shadow.blur = 6
        shadow.color = aw.Color.gray
        shadow.opacity = 0.7
        print(f"Shadow set on shape '{shape.name}'.")
    else:
        print("No shapes detected – shadow step skipped.")

    # ---------- Save as Markdown ----------
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.office_math_export_mode = aw.saving.MarkdownOfficeMathExportMode.LATEX
    md_path = f"{output_dir}/Combined.md"
    doc.save(md_path, md_options)
    print("Markdown saved at:", md_path)

    # ---------- Save as PDF/UA ----------
    pdf_options = aw.saving.PdfSaveOptions()
    pdf_options.export_floating_shapes_as_inline_tag = True
    pdf_options.compliance = aw.saving.PdfCompliance.PDF_UA_1
    pdf_path = f"{output_dir}/Combined.pdf"
    doc.save(pdf_path, pdf_options)
    print("PDF saved at:", pdf_path)

# Example usage – replace with your actual paths
if __name__ == "__main__":
    recover_and_convert("YOUR_DIRECTORY/input.docx", "YOUR_DIRECTORY")
```

Jalankan skrip dengan `python recover_and_convert.py`. Jika semuanya berjalan lancar Anda akan mendapatkan dua file di `YOUR_DIRECTORY`:

* **Combined.md** – Markdown bersih, LaTeX untuk persamaan apa pun, dan gambar yang telah ditambahkan bayangan sebagai tag gambar biasa.
* **Combined.pdf** – PDF/UA‑compliant, dengan bayangan pada bentuk pertama terjaga dan bentuk mengambang tetap inline.

---

## ## Output yang Diharapkan & Verifikasi

| File | Hal yang Perlu Diperiksa |
|------|--------------------------|
| `Combined.md` | Heading Markdown standar (`#`, `##`), daftar bullet, dan setiap persamaan ditampilkan sebagai `$$ … $$`. Buka di penampil Markdown untuk melihat formatnya. |
| `Combined.pdf` | Tag aksesibilitas (gunakan “Read Out Loud” di Adobe Acrobat untuk menguji), bentuk pertama harus menampilkan bayangan abu‑abu tipis, dan tata letak harus menyerupai DOCX asli sebanyak mungkin. |

Jika PDF terbuka tanpa error dan Markdown dirender dengan benar, Anda telah berhasil **memulihkan DOCX**, menerapkan penyesuaian visual, dan mengekspor

## Apa yang Harus Anda Pelajari Selanjutnya?

- [how to recover docx with Aspose.Words – step by step](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Save docx as pdf with Aspose.Words – Complete C# Guide](/words/english/net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}