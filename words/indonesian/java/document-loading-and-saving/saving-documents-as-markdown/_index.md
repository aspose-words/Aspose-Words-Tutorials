---
"description": "Pelajari cara mengonversi dokumen Word ke Markdown dengan Aspose.Words untuk Java. Panduan langkah demi langkah ini mencakup penyelarasan tabel, penanganan gambar, dan banyak lagi."
"linktitle": "Menyimpan Dokumen sebagai Markdown"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Menyimpan Dokumen sebagai Markdown di Aspose.Words untuk Java"
"url": "/id/java/document-loading-and-saving/saving-documents-as-markdown/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menyimpan Dokumen sebagai Markdown di Aspose.Words untuk Java


## Pengantar Menyimpan Dokumen sebagai Markdown di Aspose.Words untuk Java

Dalam panduan langkah demi langkah ini, kami akan menunjukkan cara menyimpan dokumen sebagai Markdown menggunakan Aspose.Words untuk Java. Markdown adalah bahasa markup ringan yang umum digunakan untuk memformat dokumen teks. Dengan Aspose.Words untuk Java, Anda dapat dengan mudah mengonversi dokumen Word Anda ke dalam format Markdown. Kami akan membahas berbagai aspek penyimpanan file Markdown, termasuk penyelarasan konten tabel dan penanganan gambar.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki prasyarat berikut:

- Java Development Kit (JDK) terinstal di sistem Anda.
- Aspose.Words untuk pustaka Java. Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/words/java/).

## Langkah 1: Membuat Dokumen Word

Mari kita mulai dengan membuat dokumen Word yang nantinya akan kita ubah ke format Markdown. Anda dapat menyesuaikan dokumen ini sesuai kebutuhan Anda.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Sisipkan tabel dengan dua sel
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Simpan dokumen sebagai Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

Dalam contoh ini, kita membuat tabel sederhana dengan dua sel dan mengatur perataan paragraf dalam sel-sel ini. Kemudian, kita menyimpan dokumen sebagai Markdown menggunakan `MarkdownSaveOptions`.

## Langkah 2: Sesuaikan Penyelarasan Konten Tabel

Aspose.Words untuk Java memungkinkan Anda menyesuaikan perataan konten tabel saat menyimpan sebagai Markdown. Anda dapat meratakan konten tabel ke kiri, kanan, tengah, atau membiarkannya ditentukan secara otomatis berdasarkan paragraf pertama di setiap kolom tabel.

Berikut cara menyesuaikan perataan konten tabel:

```java
// Atur perataan konten tabel ke kiri
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Atur perataan konten tabel ke kanan
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Atur perataan konten tabel ke tengah
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Atur perataan konten tabel ke otomatis (ditentukan oleh paragraf pertama)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Dengan mengubah `TableContentAlignment` properti, Anda dapat mengontrol bagaimana konten di dalam tabel disejajarkan saat mengonversi ke Markdown.

## Langkah 3: Menangani Gambar

Untuk memasukkan gambar ke dalam dokumen Markdown Anda, Anda perlu menentukan folder tempat gambar tersebut berada. Aspose.Words untuk Java memungkinkan Anda untuk mengatur folder gambar di `MarkdownSaveOptions`.

Berikut cara mengatur folder gambar dan menyimpan dokumen dengan gambar:

```java
// Memuat dokumen yang berisi gambar
Document doc = new Document("document_with_images.docx");

// Mengatur jalur folder gambar
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Simpan dokumen dengan gambar
doc.save("document_with_images.md", saveOptions);
```

Pastikan untuk mengganti `"document_with_images.docx"` dengan jalur ke dokumen Word Anda yang berisi gambar dan `"images_folder/"` dengan jalur sebenarnya ke folder tempat gambar Anda disimpan.

## Kode Sumber Lengkap Untuk Menyimpan Dokumen sebagai Markdown di Aspose.Words untuk Java

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
	// Membuat semua paragraf di dalam tabel menjadi rata.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// Penjajaran dalam kasus ini akan diambil dari paragraf pertama pada kolom tabel yang bersangkutan.
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

## Kesimpulan

Dalam panduan ini, kami telah menjajaki cara menyimpan dokumen sebagai Markdown menggunakan Aspose.Words untuk Java. Kami membahas pembuatan dokumen Word, penyesuaian penyelarasan konten tabel, dan penanganan gambar dalam file Markdown. Kini Anda dapat mengonversi dokumen Word ke format Markdown secara efisien, sehingga cocok untuk berbagai platform penerbitan dan kebutuhan dokumentasi.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara menginstal Aspose.Words untuk Java?

Aspose.Words untuk Java dapat diinstal dengan menyertakan pustaka tersebut dalam proyek Java Anda. Anda dapat mengunduh pustaka tersebut dari [Di Sini](https://releases.aspose.com/words/java/) dan ikuti petunjuk instalasi yang disediakan dalam dokumentasi.

### Bisakah saya mengonversi dokumen Word yang rumit berisi tabel dan gambar ke Markdown?

Ya, Aspose.Words untuk Java mendukung konversi dokumen Word yang kompleks dengan tabel, gambar, dan berbagai elemen pemformatan ke Markdown. Anda dapat menyesuaikan output Markdown sesuai dengan kompleksitas dokumen Anda.

### Bagaimana saya dapat menangani gambar dalam berkas Markdown?

Untuk memasukkan gambar ke dalam file Markdown, atur jalur folder gambar menggunakan `setImagesFolder` metode dalam `MarkdownSaveOptions`Pastikan file gambar disimpan dalam folder yang ditentukan, dan Aspose.Words untuk Java akan menangani referensi gambar sebagaimana mestinya.

### Apakah ada versi uji coba Aspose.Words untuk Java yang tersedia?

Ya, Anda dapat memperoleh versi uji coba Aspose.Words untuk Java dari situs web Aspose. Versi uji coba memungkinkan Anda untuk mengevaluasi kemampuan pustaka sebelum membeli lisensi.

### Di mana saya dapat menemukan lebih banyak contoh dan dokumentasi?

Untuk contoh lebih lanjut, dokumentasi, dan informasi terperinci tentang Aspose.Words untuk Java, silakan kunjungi [dokumentasi](https://reference.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}