---
date: 2025-12-20
description: Pelajari cara memuat HTML dan mengonversi HTML ke DOCX dengan Aspose.Words
  untuk Java. Panduan langkah demi langkah menunjukkan cara menyimpan file DOCX dan
  menggunakan tag dokumen terstruktur.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Cara Memuat HTML dan Menyimpan sebagai DOCX menggunakan Aspose.Words untuk
  Java
url: /id/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Memuat HTML dan Menyimpan sebagai DOCX menggunakan Aspose.Words untuk Java

## Pendahuluan tentang Memuat dan Menyimpan Dokumen HTML dengan Aspose.Words untuk Java

Dalam artikel ini, kita akan menjelajahi **cara memuat html** dan menyimpannya sebagai file DOCX menggunakan pustaka Aspose.Words untuk Java. Aspose.Words adalah API yang kuat yang memungkinkan Anda memanipulasi dokumen Word secara programatis, dan mencakup dukungan yang kuat untuk impor/ekspor HTML. Kami akan memandu seluruh proses, mulai dari menyiapkan opsi pemuatan hingga menyimpan hasilnya sebagai dokumen Word.

## Jawaban Cepat
- **Apa kelas utama untuk memuat HTML?** `Document` bersama dengan `HtmlLoadOptions`.
- **Opsi mana yang mengaktifkan Structured Document Tags?** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **Bisakah saya mengonversi HTML ke DOCX dalam satu langkah?** Ya – muat HTML dan panggil `doc.save(...".docx")`.
- **Apakah saya memerlukan lisensi untuk pengembangan?** Versi percobaan gratis dapat digunakan untuk pengujian; lisensi komersial diperlukan untuk produksi.
- **Versi Java apa yang dibutuhkan?** Java 8 atau yang lebih tinggi didukung.

## Apa itu “cara memuat html” dalam konteks Aspose.Words?

Memuat HTML berarti membaca string atau file HTML dan mengubahnya menjadi objek `Document` Aspose.Words. Objek ini kemudian dapat diedit, diformat, atau disimpan ke format apa pun yang didukung oleh API, seperti DOCX, PDF, atau RTF.

## Mengapa menggunakan Aspose.Words untuk konversi HTML‑ke‑DOCX?

- **Mempertahankan tata letak** – tabel, daftar, dan gambar tetap utuh.
- **Mendukung Structured Document Tags** – ideal untuk membuat kontrol konten di Word.
- **Tidak memerlukan Microsoft Office** – bekerja di server atau lingkungan cloud apa pun.
- **Kinerja tinggi** – memproses file HTML besar dengan cepat.

## Prasyarat

1. **Pustaka Aspose.Words untuk Java** – unduh dari [here](https://releases.aspose.com/words/java/).
2. **Lingkungan Pengembangan Java** – JDK 8+ terpasang dan dikonfigurasi.
3. **Familiaritas dasar dengan Java I/O** – kami akan menggunakan `ByteArrayInputStream` untuk memasukkan string HTML.

## Cara Memuat Dokumen HTML

Berikut adalah contoh singkat yang menunjukkan cara memuat potongan HTML sambil mengaktifkan fitur **structured document tag**.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**Penjelasan**

- Kami membuat string `HTML` yang berisi kontrol `<select>` sederhana.
- `HtmlLoadOptions` memungkinkan kami menentukan cara HTML harus diinterpretasikan. Menetapkan tipe kontrol yang diinginkan ke `STRUCTURED_DOCUMENT_TAG` memberi tahu Aspose.Words untuk mengonversi kontrol formulir HTML menjadi kontrol konten Word.
- Konstruktor `Document` membaca HTML dari `ByteArrayInputStream` menggunakan enkoding UTF‑8.

## Cara Menyimpan sebagai DOCX (Mengonversi HTML ke DOCX)

Setelah HTML dimuat ke dalam `Document`, menyimpannya sebagai file DOCX menjadi sederhana:

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

Ganti `"Your Directory Path"` dengan folder sebenarnya tempat Anda ingin file output muncul.

## Kode Sumber Lengkap untuk Memuat dan Menyimpan Dokumen HTML

Berikut adalah contoh lengkap yang siap dijalankan yang menggabungkan langkah memuat dan menyimpan. Silakan salin‑tempel ke IDE Anda.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## Kesalahan Umum & Tips

| Masalah | Mengapa Terjadi | Cara Memperbaiki |
|---------|----------------|------------------|
| **Font hilang** | HTML merujuk pada font yang tidak terpasang di server. | Sematkan font dalam DOCX menggunakan `FontSettings` atau pastikan font yang diperlukan tersedia. |
| **Gambar tidak ditampilkan** | Path gambar relatif tidak dapat diselesaikan. | Gunakan URL absolut atau muat gambar ke dalam `MemoryStream` dan atur `HtmlLoadOptions.setImageSavingCallback`. |
| **Tipe kontrol tidak dikonversi** | `setPreferredControlType` tidak disetel atau disetel ke enum yang salah. | Pastikan Anda menggunakan `HtmlControlType.STRUCTURED_DOCUMENT_TAG`. |
| **Masalah enkoding** | String HTML dienkode dengan charset yang berbeda. | Selalu gunakan `StandardCharsets.UTF_8` saat mengonversi string menjadi byte. |

## Pertanyaan yang Sering Diajukan

### Bagaimana cara menginstal Aspose.Words untuk Java?

Aspose.Words untuk Java dapat diunduh dari [here](https://releases.aspose.com/words/java/). Ikuti panduan instalasi di halaman unduhan untuk menambahkan file JAR ke classpath proyek Anda.

### Bisakah saya memuat dokumen HTML kompleks menggunakan Aspose.Words?

Ya, Aspose.Words untuk Java dapat menangani HTML kompleks, termasuk tabel bersarang, styling CSS, dan elemen interaktif tanpa JavaScript. Sesuaikan `HtmlLoadOptions` (mis., `setLoadImages` atau `setCssStyleSheetFileName`) untuk menyempurnakan proses impor.

### Format dokumen lain apa yang didukung oleh Aspose.Words?

Aspose.Words mendukung DOC, DOCX, RTF, HTML, PDF, EPUB, XPS, dan banyak lagi. API menyediakan penyimpanan satu baris ke semua format tersebut.

### Apakah Aspose.Words cocok untuk otomasi dokumen tingkat perusahaan?

Tentu saja. Ini digunakan oleh perusahaan besar untuk pembuatan laporan otomatis, konversi dokumen massal, dan pemrosesan dokumen sisi server tanpa ketergantungan Microsoft Office.

### Di mana saya dapat menemukan dokumentasi dan contoh lebih lanjut untuk Aspose.Words untuk Java?

Anda dapat menjelajahi referensi API lengkap dan tutorial tambahan di situs dokumentasi Aspose.Words untuk Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Terakhir Diperbarui:** 2025-12-20  
**Diuji Dengan:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}