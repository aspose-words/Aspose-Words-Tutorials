---
date: 2025-12-24
description: Pelajari cara membuat file teks biasa dari dokumen Word menggunakan Aspose.Words
  untuk Java. Panduan ini menunjukkan cara mengonversi Word ke txt, menggunakan indentasi
  tab, dan menyimpan Word sebagai txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Cara membuat file teks biasa dengan Aspose.Words untuk Java
url: /id/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat file teks biasa dengan Aspose.Words untuk Java

## Pendahuluan tentang Menyimpan Dokumen sebagai File Teks di Aspose.Words untuk Java

Dalam tutorial ini, Anda akan belajar **cara membuat file teks biasa** dari dokumen Word menggunakan pustaka Aspose.Words untuk Java. Baik Anda perlu **mengonversi word ke txt**, mengotomatiskan pembuatan laporan, atau sekadar mengekstrak teks mentah untuk pemrosesan lebih lanjut, panduan ini akan membawa Anda melalui seluruh alur kerja—dari pembuatan dokumen hingga penyesuaian opsi penyimpanan seperti **menggunakan indentasi tab** atau menambahkan tanda bidi. Mari kita mulai!

## Jawaban Cepat
- **Apa kelas utama untuk membuat dokumen?** `Document` dari Aspose.Words.
- **Opsi mana yang menambahkan tanda bidi untuk bahasa kanan‑ke‑kiri?** `TxtSaveOptions.setAddBidiMarks(true)`.
- **Bagaimana cara mengindentasi item daftar dengan tab?** Set `ListIndentation.Character` ke `'\t'`.
- **Apakah saya memerlukan lisensi untuk pengembangan?** Versi percobaan gratis dapat digunakan untuk pengujian; lisensi diperlukan untuk produksi.
- **Bisakah saya menyimpan file dengan nama dan jalur khusus?** Ya—lewatkan jalur lengkap ke `doc.save()`.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:

- Java Development Kit (JDK) terpasang di sistem Anda.  
- Pustaka Aspose.Words untuk Java terintegrasi dalam proyek Anda. Anda dapat mengunduhnya dari [here](https://releases.aspose.com/words/java/).  
- Pengetahuan dasar tentang pemrograman Java.

## Langkah 1: Membuat Dokumen

Untuk **menyimpan word sebagai txt**, pertama-tama kita memerlukan instance `Document`. Berikut adalah contoh potongan kode Java sederhana yang membuat dokumen dan menulis beberapa baris teks multibahasa:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Dalam kode ini kami membuat dokumen baru, menambahkan teks bahasa Inggris, Ibrani, dan Arab, serta mengaktifkan format kanan‑ke‑kiri untuk paragraf Ibrani.

## Langkah 2: Menentukan Opsi Penyimpanan Teks

Selanjutnya, kami mengonfigurasi cara dokumen akan disimpan sebagai file teks biasa. Aspose.Words menyediakan kelas `TxtSaveOptions`, yang memungkinkan Anda mengontrol segala hal mulai dari tanda bidi hingga indentasi daftar.

### Contoh 1: Menambahkan Tanda Bidi (cara menyimpan txt dengan dukungan RTL yang tepat)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Mengatur `AddBidiMarks` ke `true` memastikan bahwa karakter kanan‑ke‑kiri direpresentasikan dengan benar dalam **file teks biasa** yang dihasilkan.

### Contoh 2: Menggunakan Karakter Tab untuk Indentasi Daftar (gunakan indentasi tab)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Di sini kami memberi tahu Aspose.Words untuk menambahkan karakter tab (`'\t'`) sebelum setiap tingkat daftar, sehingga output teks lebih mudah dibaca.

## Langkah 3: Menyimpan Dokumen sebagai Teks

Sekarang opsi penyimpanan sudah siap, Anda dapat menyimpan dokumen sebagai **file teks biasa**:

```java
doc.save("output.txt", saveOptions);
```

Ganti `"output.txt"` dengan jalur lengkap tempat Anda ingin menyimpan file.

## Kode Sumber Lengkap untuk Menyimpan Dokumen sebagai File Teks di Aspose.Words untuk Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Masalah Umum dan Solusinya

| Masalah | Solusi |
|-------|----------|
| **Karakter bidi muncul sebagai teks kacau** | Pastikan `setAddBidiMarks(true)` diaktifkan dan file output dibuka dengan encoding UTF‑8. |
| **Indentasi daftar terlihat salah** | Verifikasi `ListIndentation.Count` dan `Character` telah diatur ke nilai yang diinginkan (tab `'\t'` atau spasi `' '` ). |
| **File tidak dibuat** | Periksa apakah jalur direktori ada dan aplikasi memiliki izin menulis. |

## Pertanyaan yang Sering Diajukan

### Bagaimana cara menambahkan tanda bidi ke output teks?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Bisakah saya menyesuaikan karakter indentasi daftar?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Apakah Aspose.Words untuk Java cocok untuk menangani teks multibahasa?

Ya, Aspose.Words untuk Java mendukung berbagai bahasa dan encoding karakter, menjadikannya ideal untuk mengekstrak dan menyimpan konten multibahasa sebagai teks biasa.

### Bagaimana saya dapat mengakses lebih banyak dokumentasi dan sumber daya untuk Aspose.Words untuk Java?

Anda dapat menemukan dokumentasi dan sumber daya lengkap di halaman Dokumentasi Aspose.Words untuk Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Di mana saya dapat mengunduh Aspose.Words untuk Java?

Anda dapat mengunduh pustaka tersebut dari situs resmi: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### Bagaimana jika saya perlu **mengonversi word ke txt** dalam proses batch?

Bungkus kode di atas dalam sebuah loop yang memuat setiap file `.docx`, menerapkan `TxtSaveOptions` yang sama, dan menyimpan masing‑masing sebagai `.txt`. Pastikan Anda mengelola sumber daya dengan membuang objek `Document` setelah setiap iterasi.

### Apakah API mendukung penyimpanan langsung ke stream alih‑alih file?

Ya, Anda dapat melewatkan `OutputStream` ke `doc.save(outputStream, saveOptions)` untuk pemrosesan dalam memori atau saat mengintegrasikan dengan layanan web.

---

**Terakhir Diperbarui:** 2025-12-24  
**Diuji Dengan:** Aspose.Words for Java 24.12 (latest)  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}