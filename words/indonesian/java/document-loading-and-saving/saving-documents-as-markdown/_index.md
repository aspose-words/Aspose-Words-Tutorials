---
date: 2026-02-24
description: Pelajari cara mengonversi Word ke Markdown menggunakan Aspose.Words untuk
  Java. Panduan ini mencakup penataan tabel, penanganan gambar, dan cara menyimpan
  dokumen sebagai Markdown.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Konversi Word ke Markdown dengan Aspose.Words untuk Java
url: /id/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mengonversi Word ke Markdown dengan Aspose.Words untuk Java

## Pendahuluan Mengonversi Word ke Markdown dengan Aspose.Words untuk Java

Dalam tutorial langkah‑demi‑langkah ini Anda akan belajar **cara mengonversi Word ke Markdown** menggunakan API Aspose.Words untuk Java yang kuat. Markdown adalah bahasa markup ringan yang banyak digunakan oleh pengembang dan platform konten untuk dokumentasi yang bersih dan mudah dibaca. Pada akhir panduan ini Anda akan dapat mengambil file `.docx` apa pun, mempertahankan tabel, gambar, dan pemformatan, serta mengekspornya sebagai file `.md` yang siap untuk generator situs statis, README GitHub, atau alur kerja apa pun yang mendukung markdown.

## Jawaban Cepat
- **Perpustakaan apa yang saya butuhkan?** Aspose.Words untuk Java (`aspose-words.jar`).
- **Bisakah saya menyesuaikan perataan tabel?** Ya – gunakan `TableContentAlignment` dalam `MarkdownSaveOptions`.
- **Bagaimana gambar ditangani?** Tetapkan folder gambar dengan `setImagesFolder()`; perpustakaan membuat tautan relatif.
- **Apakah saya memerlukan lisensi untuk produksi?** Lisensi komersial diperlukan untuk penggunaan non‑trial.
- **Apakah ini kompatibel dengan Java 17?** Ya, perpustakaan mendukung Java 8 ke atas.

## Apa itu mengonversi Word ke Markdown?

Mengonversi Word ke Markdown berarti mengambil format kaya dari dokumen Microsoft Word dan menerjemahkannya ke dalam sintaks markdown teks biasa. Proses ini mempertahankan judul, daftar, tabel, dan referensi gambar sambil menghilangkan format biner, menjadikan konten dapat dipindahkan dan ramah kontrol versi.

## Mengapa menggunakan Aspose.Words untuk Java untuk menyimpan dokumen sebagai markdown?

* **Fidelity penuh** – tabel, gambar, dan tata letak kompleks dipertahankan.
* **Kontrol halus** – Anda dapat menyesuaikan perataan tabel, jalur gambar, dan lainnya.
* **Tanpa ketergantungan eksternal** – perpustakaan berfungsi langsung tanpa perlu menginstal Office.
* **Lintas platform** – bekerja di Windows, Linux, dan macOS dengan runtime Java apa pun.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

- Java Development Kit (JDK) terinstal di sistem Anda.
- Perpustakaan Aspose.Words untuk Java. Anda dapat mengunduhnya dari [here](https://releases.aspose.com/words/java/).

## Panduan Langkah‑demi‑Langkah

### Langkah 1: Buat dokumen Word yang akan dikonversi

Pertama, kami membuat dokumen Word sederhana yang berisi tabel dua‑sel. Contoh ini menunjukkan bagaimana perataan paragraf di dalam sel tabel dipertahankan ketika kami kemudian **menyimpan dokumen sebagai markdown**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

### Langkah 2: Sesuaikan perataan konten tabel

Aspose.Words untuk Java memungkinkan Anda mengontrol bagaimana sel tabel disejajarkan dalam markdown yang dihasilkan. Gunakan properti `TableContentAlignment` untuk mengatur **penyesuaian perataan tabel** ke kiri, kanan, tengah, atau biarkan perpustakaan memutuskan secara otomatis berdasarkan paragraf pertama di setiap kolom.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Dengan mengubah pengaturan ini Anda dapat **mengekspor tabel word ke markdown** dengan perataan yang tepat yang Anda butuhkan untuk mesin rendering selanjutnya.

### Langkah 3: Tangani gambar selama konversi

Ketika dokumen Word sumber Anda berisi gambar, Anda harus memberi tahu Aspose.Words di mana menempatkan file gambar yang diekspor. Metode `setImagesFolder` pada `MarkdownSaveOptions` menentukan folder yang akan menyimpan aset gambar, dan markdown akan berisi tautan relatif ke file tersebut.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Ganti `"document_with_images.docx"` dengan jalur ke file sumber Anda dan `"images_folder/"` dengan folder output yang diinginkan untuk gambar.

### Kode sumber lengkap untuk semua skenario

Di bawah ini adalah contoh terintegrasi yang menunjukkan cara **menyetel perataan tabel otomatis**, **menyesuaikan perataan**, dan **menetapkan folder gambar** dalam satu metode. Potongan kode ini mencerminkan kode tutorial asli dan berfungsi tanpa perubahan.

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Masalah Umum dan Solusinya

| Masalah | Penyebab | Solusi |
|-------|--------|-----|
| Gambar muncul sebagai tautan rusak | `setImagesFolder` tidak diatur atau jalur folder tidak tepat | Verifikasi bahwa jalur folder sudah benar dan folder dapat ditulisi |
| Perataan tabel terlihat tidak tepat | Nilai `TableContentAlignment` salah | Gunakan `TableContentAlignment.AUTO` agar paragraf pertama yang menentukan, atau secara eksplisit atur LEFT/RIGHT/CENTER |
| File output kosong | Opsi penyimpanan tidak diberikan ke `doc.save()` | Pastikan Anda memberikan instance `MarkdownSaveOptions` ke metode `save` |
| Fitur Word tidak didukung (mis., SmartArt) | Markdown tidak dapat merepresentasikan beberapa objek kompleks | Konversi elemen tersebut menjadi gambar sebelum menyimpan, atau sederhanakan dokumen sumber |

## Pertanyaan yang Sering Diajukan

**T: Bagaimana cara menginstal Aspose.Words untuk Java?**  
J: Aspose.Words untuk Java dapat diinstal dengan menyertakan perpustakaan dalam proyek Java Anda. Anda dapat mengunduh perpustakaan dari [here](https://releases.aspose.com/words/java/) dan mengikuti petunjuk instalasi yang disediakan dalam dokumentasi.

**T: Bisakah saya mengonversi dokumen Word kompleks dengan tabel dan gambar ke Markdown?**  
J: Ya, Aspose.Words untuk Java mendukung konversi dokumen Word kompleks dengan tabel, gambar, dan berbagai elemen pemformatan ke Markdown. Anda dapat menyesuaikan output Markdown sesuai dengan kompleksitas dokumen Anda.

**T: Bagaimana saya dapat menangani gambar dalam file Markdown?**  
J: Untuk menyertakan gambar dalam file Markdown, tetapkan jalur folder gambar menggunakan metode `setImagesFolder` dalam `MarkdownSaveOptions`. Pastikan file gambar disimpan di folder yang ditentukan, dan Aspose.Words untuk Java akan menangani referensi gambar secara tepat.

**T: Apakah ada versi percobaan Aspose.Words untuk Java yang tersedia?**  
J: Ya, Anda dapat memperoleh versi percobaan Aspose.Words untuk Java dari situs web Aspose. Versi percobaan memungkinkan Anda mengevaluasi kemampuan perpustakaan sebelum membeli lisensi.

**T: Di mana saya dapat menemukan contoh dan dokumentasi lebih lanjut?**  
J: Untuk contoh lebih lanjut, dokumentasi, dan informasi detail tentang Aspose.Words untuk Java, silakan kunjungi [documentation](https://reference.aspose.com/words/java/).

## Kesimpulan

Dalam panduan ini kami membahas semua yang Anda perlukan untuk **mengonversi word ke markdown** menggunakan Aspose.Words untuk Java: membuat dokumen sumber, **menyesuaikan perataan tabel**, dan menangani gambar dengan konfigurasi folder yang tepat. Dengan teknik ini Anda dapat mengekspor konten Word ke markdown secara andal untuk blog, situs dokumentasi, atau platform apa pun yang menggunakan markdown.

---

**Terakhir Diperbarui:** 2026-02-24  
**Diuji Dengan:** Aspose.Words for Java 24.12 (terbaru pada saat penulisan)  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}