---
date: 2025-12-22
description: Pelajari cara mengekspor markdown dengan mengonversi dokumen Word ke
  Markdown menggunakan Aspose.Words untuk Java. Panduan langkah demi langkah ini mencakup
  penyelarasan tabel, penanganan gambar, dan lainnya.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Cara Mengekspor Markdown dengan Aspose.Words untuk Java
url: /id/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengekspor Markdown dengan Aspose.Words untuk Java

## Pengantar Mengekspor Markdown di Aspose.Words untuk Java

Dalam tutorial langkah‑demi‑langkah ini, **Anda akan belajar cara mengekspor markdown** dari dokumen Word menggunakan Aspose.Words untuk Java. Markdown adalah bahasa markup ringan yang sempurna untuk dokumentasi, generator situs statis, dan banyak platform penerbitan. Pada akhir panduan ini Anda akan dapat **mengonversi Word ke markdown**, menyesuaikan perataan tabel, dan **menangani gambar dalam markdown** dengan mudah.

## Jawaban Cepat
- **Kelas utama untuk menyimpan sebagai Markdown?** `MarkdownSaveOptions`
- **Apakah gambar dapat disematkan secara otomatis?** Ya – atur folder gambar melalui `setImagesFolder`.
- **Bagaimana cara mengontrol perataan tabel?** Gunakan `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **Apa persyaratan minimum?** JDK 8+ dan perpustakaan Aspose.Words untuk Java.
- **Apakah tersedia versi percobaan?** Ya, unduh dari situs web Aspose.

## Apa itu “cara mengekspor markdown”?
Mengekspor markdown berarti mengambil dokumen Word berformat teks kaya (`.docx`) dan menghasilkan file `.md` teks biasa yang mempertahankan heading, tabel, dan gambar dalam sintaks Markdown.

## Mengapa menggunakan Aspose.Words untuk Java untuk mengonversi docx dengan gambar?
Aspose.Words menangani tata letak kompleks, gambar yang disematkan, dan struktur tabel tanpa kehilangan fidelitas. Ia juga memberi Anda kontrol halus atas output Markdown, seperti perataan tabel dan manajemen folder gambar.

## Prasyarat

- Java Development Kit (JDK) terpasang di sistem Anda.
- Perpustakaan Aspose.Words untuk Java. Anda dapat mengunduhnya dari [sini](https://releases.aspose.com/words/java/).

## Langkah 1: Buat dokumen Word sederhana

Pertama, kita akan membuat dokumen kecil yang berisi tabel. Ini akan memungkinkan kami mendemonstrasikan **menyesuaikan perataan tabel** nanti.

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

Dalam potongan kode di atas kami:

1. Membuat `Document` baru.
2. Menggunakan `DocumentBuilder` untuk menyisipkan tabel dua‑sel.
3. Menerapkan perataan paragraf **kanan** dan **tengah** di dalam masing‑masing sel.
4. Menyimpan file sebagai Markdown menggunakan `MarkdownSaveOptions`.

## Langkah 2: Sesuaikan perataan konten tabel

Aspose.Words memungkinkan Anda menentukan bagaimana sel tabel dirender dalam Markdown akhir. Anda dapat memaksa perataan kiri, kanan, tengah, atau membiarkan perpustakaan memutuskan secara otomatis berdasarkan paragraf pertama di setiap kolom.

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

Dengan mengubah properti `TableContentAlignment` Anda mengontrol **penyesuaian perataan tabel** untuk output Markdown.

## Langkah 3: Menangani gambar saat mengekspor ke markdown

Ketika dokumen berisi gambar, Anda ingin gambar‑gambar tersebut muncul dengan benar dalam file `.md` yang dihasilkan. Atur folder tempat Aspose.Words harus mengekstrak gambar.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Ganti `"document_with_images.docx"` dengan jalur ke file sumber Anda dan `"images_folder/"` dengan lokasi tempat Anda ingin menyimpan gambar. Markdown yang dihasilkan akan berisi tautan gambar yang mengarah ke folder ini, memungkinkan Anda **menangani gambar dalam markdown** secara mulus.

## Kode Sumber Lengkap untuk Menyimpan Dokumen sebagai Markdown di Aspose.Words untuk Java

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

| Masalah | Solusi |
|---------|--------|
| Gambar tidak muncul di file `.md` | Pastikan `setImagesFolder` mengarah ke direktori yang dapat ditulisi dan folder tersebut direferensikan dengan benar dalam Markdown yang dihasilkan. |
| Perataan tabel terlihat tidak tepat | Gunakan `TableContentAlignment.AUTO` agar Aspose.Words menentukan perataan terbaik berdasarkan paragraf pertama setiap kolom. |
| File output kosong | Pastikan objek `Document` memang berisi konten sebelum memanggil `save`. |

## Pertanyaan yang Sering Diajukan

**Q: Bagaimana cara menginstal Aspose.Words untuk Java?**  
A: Aspose.Words untuk Java dapat diinstal dengan menyertakan perpustakaan dalam proyek Java Anda. Anda dapat mengunduh perpustakaan dari [sini](https://releases.aspose.com/words/java/) dan mengikuti petunjuk instalasi yang disediakan dalam dokumentasi.

**Q: Apakah saya dapat mengonversi dokumen Word kompleks dengan tabel dan gambar ke Markdown?**  
A: Ya, Aspose.Words untuk Java mendukung konversi dokumen Word kompleks dengan tabel, gambar, dan berbagai elemen format ke Markdown. Anda dapat menyesuaikan output Markdown sesuai dengan kompleksitas dokumen Anda.

**Q: Bagaimana cara menangani gambar dalam file Markdown?**  
A: Atur jalur folder gambar menggunakan metode `setImagesFolder` pada `MarkdownSaveOptions`. Pastikan file gambar disimpan di folder yang ditentukan; Aspose.Words akan menghasilkan tautan gambar Markdown yang sesuai.

**Q: Apakah ada versi percobaan Aspose.Words untuk Java?**  
A: Ya, Anda dapat memperoleh versi percobaan Aspose.Words untuk Java dari situs web Aspose. Versi percobaan memungkinkan Anda mengevaluasi kemampuan perpustakaan sebelum membeli lisensi.

**Q: Di mana saya dapat menemukan contoh dan dokumentasi lebih lanjut?**  
A: Untuk contoh lebih banyak, dokumentasi, dan informasi detail tentang Aspose.Words untuk Java, silakan kunjungi [dokumentasi](https://reference.aspose.com/words/java/).

---

**Terakhir Diperbarui:** 2025-12-22  
**Diuji Dengan:** Aspose.Words untuk Java 24.12 (terbaru pada saat penulisan)  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}