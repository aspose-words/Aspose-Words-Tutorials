---
date: 2026-01-03
description: Pelajari cara mengganti teks dengan HTML dalam dokumen Word menggunakan
  Aspose.Words untuk Java. Panduan langkah demi langkah dengan contoh kode, tips mengganti
  teks menggunakan regex di Java, dan lainnya.
linktitle: Finding and Replacing Text
second_title: Aspose.Words Java Document Processing API
title: ganti teks dengan HTML menggunakan Aspose.Words untuk Java
url: /id/java/document-manipulation/finding-and-replacing-text/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ganti teks dengan html di Aspose.Words untuk Java

## Pengantar Menemukan dan Mengganti Teks di Aspose.Words untuk Java

Aspose.Words untuk Java adalah API Java yang kuat yang memungkinkan Anda memanipulasi dokumen Word secara programatis. Salah satu tugas paling umum adalah **ganti teks dengan html**, baik Anda memperbarui placeholder dalam template, menyisipkan konten bergaya, atau melakukan transformasi teks massal. Dalam panduan ini kami akan menjelaskan cara mengganti teks, cara menggunakan regex replace text java, dan bahkan cara mengganti teks di header—semua sambil menjaga kode Anda tetap bersih dan efisien.

## Jawaban Cepat
- **Apa metode utama untuk mengganti teks dengan html?** Gunakan `FindReplaceOptions` dengan callback khusus seperti `ReplaceWithHtmlEvaluator`.  
- **Bisakah saya mengabaikan field saat mengganti?** Ya – atur `options.setIgnoreFields(true)`.  
- **Apakah saya memerlukan lisensi untuk penggunaan produksi?** Lisensi Aspose.Words yang valid diperlukan untuk penyebaran komersial.  
- **Versi Java mana yang didukung?** Aspose.Words untuk Java bekerja dengan Java 8 ke atas.  
- **Apakah regex replace text java didukung?** Tentu – berikan objek `Pattern` ke metode `replace`.

## Apa itu “ganti teks dengan html”?

Mengganti teks dengan HTML berarti menukar placeholder teks biasa dengan markup HTML kaya (tabel, daftar, styling) sambil mempertahankan struktur dokumen Word di sekitarnya. Aspose.Words mem-parsing HTML dan menyisipkan objek Word yang sesuai, memberi Anda kontrol penuh atas tata letak akhir.

## Mengapa menggunakan Aspose.Words untuk tugas ini?

- **Fidelity Word penuh** – perpustakaan menjaga semua format, header, footer, dan perubahan yang dilacak tetap utuh.  
- **Dukungan regex bawaan** – sempurna untuk pola pencarian kompleks (`regex replace text java`).  
- **Kontrol halus** – opsi seperti `IgnoreFields`, `IgnoreDeleted`, dan `UseLegacyOrder` memungkinkan Anda menyesuaikan operasi sesuai kebutuhan.  
- **Lintas‑platform** – bekerja pada sistem operasi apa pun yang menjalankan Java.

## Prasyarat

- Lingkungan Pengembangan Java (JDK 8+)  
- Perpustakaan Aspose.Words untuk Java – unduh dari [sini](https://releases.aspose.com/words/java/).  
- Dokumen Word contoh (`.docx`) untuk percobaan.

## Menemukan dan Mengganti Teks Sederhana

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Find and replace text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Contoh dasar ini menunjukkan **cara mengganti teks** menggunakan metode `replace`. Ini merupakan fondasi untuk skenario yang lebih maju.

## Menggunakan Ekspresi Reguler (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Use regular expressions for finding and replacing text
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Ekspresi reguler memberi Anda pencocokan pola yang kuat, ideal untuk placeholder dinamis atau batas kata yang kompleks.

## Mengabaikan Teks di Dalam Field (aspose words replace text)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreFields to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Atur `IgnoreFields` untuk menjaga field merge, nomor halaman, atau kode field lainnya tetap tidak tersentuh saat Anda mengganti konten di sekitarnya.

## Mengabaikan Teks di Dalam Revisi Hapus

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreDeleted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Ini mencegah teks yang ditandai untuk dihapus (perubahan yang dilacak) diubah.

## Mengabaikan Teks di Dalam Revisi Sisip

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreInserted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Berguna ketika Anda ingin menjaga teks yang baru disisipkan tetap utuh selama penggantian massal.

## Mengganti Teks dengan HTML

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Save the modified document
doc.save("modified-document.docx");
```

Di sini kami **ganti teks dengan html** dengan menyediakan evaluator khusus yang mem-parsing string HTML dan menyisipkan node Word yang sesuai.

## Mengganti Teks di Header dan Footer (replace text in headers)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the collection of headers and footers
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Choose the header or footer type you want to replace text in (e.g., HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Create a FindReplaceOptions instance and apply it to the footer's range
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Penggantian terarah di dalam header atau footer memastikan branding dokumen Anda tetap konsisten.

## Menampilkan Perubahan untuk Urutan Header dan Footer

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the first section
Section firstPageSection = doc.getFirstSection();

// Create a FindReplaceOptions instance and apply it to the document's range
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Replace text that affects header and footer orders
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Contoh ini mencatat perubahan, membantu Anda mengaudit modifikasi pada urutan header/footer.

## Mengganti Teks dengan Field

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback for fields
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Use options when replacing text
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Menyisipkan field (misalnya field merge) memungkinkan Anda membangun dokumen dinamis yang dapat diisi nanti.

## Mengganti dengan Evaluator

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Use options when replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Evaluator khusus memberi Anda kontrol programatik penuh atas teks pengganti.

## Mengganti dengan Regex (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Use regular expressions for finding and replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Cara singkat untuk melakukan penggantian berbasis pola di seluruh dokumen.

## Mengenali dan Substitusi dalam Pola Pengganti

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with UseSubstitutions set to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Use options when replacing text with a pattern
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Save the modified document
doc.save("modified-document.docx");
```

Aktifkan `UseSubstitutions` untuk merujuk grup penangkap secara langsung dalam string pengganti.

## Mengganti dengan String (replace text word java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Replace text with a string
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Bentuk paling sederhana dari penggantian—sempurna untuk placeholder statis.

## Menggunakan Urutan Legacy

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set UseLegacyOrder to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Use options when replacing text
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Urutan legacy dapat diperlukan saat berurusan dengan dokumen lama yang mengandalkan urutan penelusuran asli.

## Mengganti Teks di dalam Tabel

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get a specific table (e.g., the first table)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Use FindReplaceOptions for replacing text in the table
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Penggantian terarah di dalam tabel mencegah perubahan yang tidak diinginkan di bagian lain dokumen.

## Masalah Umum dan Solusinya

- **HTML tidak dirender dengan benar** – Pastikan HTML Anda terstruktur dengan baik dan menyertakan tag yang diperlukan (mis., `<p>`, `<table>`).  
- **Regex tidak cocok** – Ingat untuk meloloskan karakter khusus dan gunakan `Pattern.CASE_INSENSITIVE` bila diperlukan.  
- **Field terganti secara tidak sengaja** – Atur `options.setIgnoreFields(true)` untuk melindunginya.  
- **Kinerja pada dokumen besar** – Gunakan `UseLegacyOrder` atau proses bagian secara terpisah untuk mengurangi jejak memori.

## Pertanyaan yang Sering Diajukan

**T: Bagaimana cara mengunduh Aspose.Words untuk Java?**  
J: Anda dapat mengunduh Aspose.Words untuk Java dari situs web dengan mengunjungi [tautan ini](https://releases.aspose.com/words/java/).

**T: Bisakah saya menggunakan ekspresi reguler untuk penggantian teks?**  
J: Ya, Anda dapat menggunakan ekspresi reguler untuk penggantian teks di Aspose.Words untuk Java. Ini memungkinkan Anda melakukan operasi temukan dan ganti yang lebih maju dan fleksibel.

**T: Bagaimana cara mengabaikan teks di dalam field selama penggantian?**  
J: Atur properti `IgnoreFields` dari `FindReplaceOptions` menjadi `true`. Ini mengecualikan konten field seperti field merge dari penggantian.

**T: Apakah memungkinkan mengganti teks di dalam header dan footer?**  
J: Tentu saja. Akses header atau footer yang diinginkan melalui `HeaderFooterCollection` dan terapkan metode `replace` dengan opsi yang sesuai.

**T: Apa yang dilakukan opsi `UseLegacyOrder`?**  
J: `UseLegacyOrder` memaksa mesin temukan/ganti menelusuri node dalam urutan asli yang digunakan oleh versi lama Aspose.Words, yang dapat berguna untuk kompatibilitas dengan dokumen legacy.

---

**Terakhir Diperbarui:** 2026-01-03  
**Diuji Dengan:** Aspose.Words untuk Java 24.12  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}