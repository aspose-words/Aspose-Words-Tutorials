---
date: 2026-01-16
description: Pelajari cara mengonversi inci ke poin, membaca metadata dokumen Java,
  menambahkan properti khusus Java, dan mengatur margin halaman Java dengan Aspose.Words
  untuk Java.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Mengonversi Inci ke Poin – Menggunakan Properti Dokumen di Aspose.Words untuk
  Java
url: /id/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mengonversi Inci ke Poin – Menggunakan Properti Dokumen di Aspose.Words untuk Java

Dalam tutorial ini Anda akan menemukan cara **mengonversi inci ke poin** saat mengatur margin halaman, membaca metadata dokumen Java, menambahkan properti khusus Java, dan bekerja dengan properti dokumen bawaan menggunakan Aspose.Words untuk Java. Baik Anda membuat laporan, faktur, atau dokumen hukum, menguasai teknik ini memberi Anda kontrol detail atas tampilan dan metadata file Word Anda.

## Quick Answers
- **Bagaimana cara mengonversi inci ke poin?** Gunakan `ConvertUtil.inchToPoint(value)` dari Aspose.Words.
- **Apakah saya dapat membaca metadata dokumen di Java?** Ya – panggil `doc.getBuiltInDocumentProperties()` atau `doc.getCustomDocumentProperties()`.
- **Bagaimana cara menambahkan properti khusus di Java?** Gunakan `doc.getCustomDocumentProperties().add(name, value)`.
- **Metode apa yang mengatur margin halaman dalam poin?** `PageSetup.setTopMargin`, `setBottomMargin`, dll., menerima nilai poin.
- **Apakah penautan ke bookmark didukung?** Ya – gunakan `addLinkToContent` pada koleksi properti khusus.

## Pengantar Properti Dokumen

Properti dokumen adalah bagian penting dari setiap file Word. Mereka menyimpan informasi seperti judul, penulis, subjek, kata kunci, dan metadata khusus apa pun yang Anda perlukan untuk pemrosesan lanjutan. Di Aspose.Words untuk Java Anda dapat memanipulasi baik properti dokumen bawaan maupun khusus, dan Anda juga dapat mengontrol detail tata letak seperti margin dengan mengonversi satuan ukuran (mis., **mengonversi inci ke poin**).

## Apa itu “mengonversi inci ke poin”?

Di Word, ukuran tata letak dinyatakan dalam poin (1 poin = 1/72 inci). Mengonversi inci ke poin memungkinkan Anda menentukan margin, indentasi, dan spasi menggunakan satuan imperial yang familiar sementara API bekerja dengan poin secara internal.

## Mengapa mengelola metadata dokumen di Java?

Menyematkan metadata memudahkan pencarian, pengkategorian, dan otomatisasi alur kerja. Misalnya, Anda dapat menandai kontrak dengan flag “Authorized” atau menyimpan nomor revisi untuk jejak audit. Membaca dan menulis informasi ini secara programatik memastikan konsistensi di seluruh batch dokumen yang besar.

## Prasyarat
- Java 17+ (atau JDK yang kompatibel)
- Perpustakaan Aspose.Words untuk Java ditambahkan ke proyek Anda (Maven/Gradle)
- File contoh `.docx` (mis., `Properties.docx`) ditempatkan di direktori yang dapat diakses

## Panduan Langkah‑per‑Langkah

### Mengenumerasi Properti Dokumen Bawaan
Berikut adalah contoh sederhana yang membuka dokumen dan mencetak semua properti bawaan seperti Title, Author, dan Keywords.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Pro tip:** Gunakan potongan kode ini untuk memverifikasi bahwa metadata Anda telah ditulis dengan benar selama langkah‑langkah sebelumnya.

### Menambahkan Properti Dokumen Khusus (add custom properties java)
Properti khusus memungkinkan Anda menyimpan tipe data apa pun yang Anda perlukan—boolean, string, tanggal, angka, dll.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Mengapa ini penting:** Menambahkan flag seperti **Authorized** dapat menggerakkan alur kerja persetujuan lanjutan tanpa mengubah konten dokumen.

### Menghapus Properti Khusus
Jika sebuah properti tidak lagi diperlukan, Anda dapat menghapusnya dengan bersih.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Mengonfigurasi Tautan ke Konten (penautan bookmark)
Anda dapat membuat bookmark dan kemudian menambahkan properti khusus yang mengarah ke bookmark tersebut, memungkinkan referensi silang dinamis.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Mengonversi Antara Satuan Ukuran (set page margins java)
Di sinilah kata kunci utama bersinar. Kami mengatur margin dalam inci, lalu **mengonversi inci ke poin** menggunakan `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Catatan:** `ConvertUtil` juga menyediakan `pointToInch`, `mmToPoint`, dll., untuk penanganan tata letak yang fleksibel.

### Menggunakan Karakter Kontrol (read document metadata java)
Karakter kontrol membantu Anda membersihkan aliran teks. Contoh ini menggantikan carriage‑return (`\r`) dengan urutan pemisah baris Windows (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Masalah Umum & Solusinya
| Masalah | Penyebab | Solusi |
|-------|-------|-----|
| Margin terlihat salah setelah konversi | Menggunakan satuan yang salah (mis., cm bukan inci) | Pastikan Anda memanggil `ConvertUtil.inchToPoint` untuk nilai inci |
| Properti khusus tidak muncul | Properti ditambahkan setelah menyimpan dokumen | Panggil `doc.save(...)` setelah menambahkan properti |
| Tautan bookmark rusak | Typo nama bookmark | Pastikan nama bookmark cocok persis di `addLinkToContent` |

## FAQ

### Bagaimana cara mengakses properti dokumen bawaan?
Untuk mengakses properti dokumen bawaan di Aspose.Words untuk Java, Anda dapat menggunakan metode `getBuiltInDocumentProperties` pada objek `Document`. Metode ini mengembalikan koleksi properti bawaan yang dapat Anda iterasi.

### Bisakah saya menambahkan properti dokumen khusus ke sebuah dokumen?
Ya, Anda dapat menambahkan properti dokumen khusus ke sebuah dokumen menggunakan koleksi `CustomDocumentProperties`. Anda dapat mendefinisikan properti khusus dengan berbagai tipe data, termasuk string, boolean, tanggal, dan nilai numerik.

### Bagaimana cara menghapus properti dokumen khusus tertentu?
Untuk menghapus properti dokumen khusus tertentu, Anda dapat menggunakan metode `remove` pada koleksi `CustomDocumentProperties`, dengan memberikan nama properti yang ingin dihapus sebagai parameter.

### Apa tujuan menautkan ke konten dalam dokumen?
Menautkan ke konten dalam dokumen memungkinkan Anda membuat referensi dinamis ke bagian tertentu dari dokumen. Ini dapat berguna untuk membuat dokumen interaktif atau referensi silang antar bagian.

### Bagaimana cara mengonversi antara satuan ukuran yang berbeda di Aspose.Words untuk Java?
Anda dapat mengonversi antara satuan ukuran yang berbeda di Aspose.Words untuk Java dengan menggunakan kelas `ConvertUtil`. Kelas ini menyediakan metode untuk mengonversi satuan seperti inci ke poin, poin ke sentimeter, dan lainnya.

## Pertanyaan yang Sering Diajukan

**Q: Bagaimana cara membaca metadata dokumen Java tanpa memuat seluruh file?**  
A: Gunakan `DocumentInfo` untuk mengambil properti inti tanpa memuat seluruh konten dokumen.

**Q: Bisakah saya mengatur margin halaman Java secara programatik untuk dokumen yang ada?**  
A: Ya—buka dokumen, ubah margin `PageSetup` (konversi inci ke poin jika diperlukan), dan simpan.

**Q: Apakah memungkinkan mengekspor properti khusus ke metadata PDF?**  
A: Saat menyimpan ke PDF, Aspose.Words secara otomatis memetakan properti dokumen khusus ke metadata khusus PDF.

**Q: Apakah karakter kontrol memengaruhi konversi PDF?**  
A: Mereka dipertahankan selama konversi; namun, Anda mungkin ingin menormalkan akhir baris untuk konsistensi.

**Q: Versi Aspose.Words mana yang diperlukan untuk `ConvertUtil`?**  
A: `ConvertUtil` telah tersedia sejak Aspose.Words 16.5; versi terbaru mana pun mendukungnya.

## Kesimpulan

Dengan menguasai **mengonversi inci ke poin**, membaca metadata dokumen Java, dan menambahkan properti khusus Java, Anda memperoleh kontrol penuh atas tata letak visual serta data tersembunyi dari file Word Anda. Kemampuan ini memungkinkan Anda membangun alur kerja dokumen otomatis, menegakkan kepatuhan, dan membuat laporan berformat kaya—semua dengan Aspose.Words untuk Java.

---

**Terakhir Diperbarui:** 2026-01-16  
**Diuji Dengan:** Aspose.Words for Java 24.11  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}