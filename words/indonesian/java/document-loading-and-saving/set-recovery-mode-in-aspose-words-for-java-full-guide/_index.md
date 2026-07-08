---
category: general
date: 2026-07-03
description: Atur mode pemulihan untuk memperbaiki file Word yang rusak di Java dan
  tampilkan jumlah halaman setelah memuat. Pelajari langkah demi langkah dengan Aspose.Words.
draft: false
keywords:
- set recovery mode
- display page count
- recover corrupted word
- Aspose.Words Java
- document loading options
language: id
og_description: Atur mode pemulihan di Aspose.Words for Java untuk memulihkan file
  Word yang rusak dan menampilkan jumlah halaman. Ikuti contoh lengkapnya sekarang.
og_title: Mengatur Mode Pemulihan di Aspose.Words untuk Java – Tutorial Lengkap
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  headline: Set Recovery Mode in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  name: Set Recovery Mode in Aspose.Words for Java – Full Guide
  steps:
  - name: Why `RecoveryMode.PARSE`?
    text: '- **PARSE** – Aspose.Words parses whatever fragments it can understand,
      stitching together a partially functional document. Ideal when you need *any*
      content out of a broken file. - **SKIP** – The library skips over corrupted
      sections entirely, which can be faster but may discard more data.'
  - name: 1️⃣ Corrupted Header/Footer Sections
    text: Sometimes only the main body parses while headers and footers are lost.
      If you rely on those for branding, you may need to re‑inject them after recovery.
  - name: 2️⃣ Images That Won’t Load
    text: Embedded images often get stripped out when the zip container (the underlying
      `.docx` format) is damaged. You can catch this by iterating over `doc.getSections()`
      and checking `Section.getBody().getParagraphs()` for `Shape` objects.
  - name: 3️⃣ Large Documents and Memory
    text: Recovering a 200‑page corrupted file can be memory‑intensive. Consider increasing
      the JVM heap size (`-Xmx2g`) when you anticipate huge documents.
  - name: 4️⃣ License Restrictions
    text: The evaluation version caps certain features, but **recovery** is fully
      functional. However, the printed page count may be limited to a few pages in
      the trial. Always test with a licensed build for production.
  - name: Maven `pom.xml` snippet
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> </dependency> ```'
  - name: Java source file `RecoveryModeDemo.java`
    text: '```java import com.aspose.words.*;'
  type: HowTo
- questions:
  - answer: That usually means the file is beyond salvage—perhaps the zip container
      is completely broken. In such cases, you might need a third‑party repair tool
      before handing it to Aspose.Words.
    question: What if `RecoveryMode.PARSE` still throws an exception?
  - answer: 'Absolutely. Implement `IWarningCallback` to capture any warnings Aspose.Words
      emits during the parsing process. This gives you insight into which parts were
      skipped. ```java loadOptions.setWarningCallback(new IWarningCallback() { public
      void warning(WarningInfo info) { System.out.println("Warning: "'
    question: Can I combine `RecoveryMode.PARSE` with custom document loading callbacks?
  - answer: 'No. Aspose.Words works on a copy in memory; the source file remains untouched
      unless you explicitly call `doc.save()`. --- ## ## Wrap‑Up We’ve covered how
      to **set recovery mode** in Aspose.Words for Java, why `PARSE` is generally
      the best choice for salvaging a broken document, and how to **display'
    question: Does changing the recovery mode affect the original file?
  type: FAQPage
tags:
- Java
- Aspose.Words
- Word recovery
title: Mengatur Mode Pemulihan di Aspose.Words untuk Java – Panduan Lengkap
url: /id/java/document-loading-and-saving/set-recovery-mode-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Atur Mode Pemulihan di Aspose.Words untuk Java – Panduan Lengkap

Pernah bertanya-tanya bagaimana cara **set recovery mode** saat memuat file `.docx` yang rusak dengan Aspose.Words? Anda bukan satu-satunya yang kebingungan dengan dokumen Word yang korup dan tidak dapat dibuka. Dalam tutorial ini kami akan membahas tepatnya itu—cara mengonfigurasi library untuk **memulihkan Word yang rusak** dan kemudian **menampilkan jumlah halaman** dari konten yang berhasil dimuat.

Kami akan membahas semuanya mulai dari penyesuaian kecil `LoadOptions` hingga `System.out.println` terakhir yang memberi tahu Anda berapa banyak halaman yang selamat dari misi penyelamatan. Tanpa basa-basi, hanya solusi praktis yang siap disalin‑tempel dan berfungsi dengan rilis terbaru Aspose.Words 23.12.

## Apa yang Akan Anda Pelajari

- Mengapa mode pemulihan penting dan opsi apa yang ditawarkan Aspose.Words.  
- Cara **set recovery mode** secara programatis menggunakan Java.  
- Cara **menampilkan jumlah halaman** setelah dokumen dimuat, mengonfirmasi pemulihan berhasil.  
- Jebakan umum saat menangani file Word yang rusak dan cara menghindarinya.  

Sebelum kita mulai, pastikan Anda memiliki:

1. Lisensi Aspose.Words untuk Java yang valid (atau kunci evaluasi sementara).  
2. Java 17 atau yang lebih baru terpasang di mesin Anda.  
3. File `Corrupted.docx` yang rusak yang ingin Anda uji.  

Sudah ada? Bagus—mari kita mulai.

> **Pro tip:** Bahkan jika Anda menggunakan versi percobaan, fitur pemulihan bekerja persis sama seperti pada build berlisensi.

---

## ## How to Set Recovery Mode with Aspose.Words for Java

Inti solusi berada di kelas `LoadOptions`. Secara default Aspose.Words berusaha sebaik mungkin untuk memuat sebuah dokumen, tetapi ketika file sangat rusak Anda perlu memberi tahu *bagaimana* ia harus berperilaku. Di sinilah **set recovery mode** berperan.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a LoadOptions instance – this object holds all the loading preferences.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose the recovery mode. PARSE attempts to salvage as much as possible,
        //    while SKIP simply skips unreadable parts.
        loadOptions.setRecoveryMode(RecoveryMode.PARSE);

        // 3️⃣ Load the document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 4️⃣ Finally, display the number of pages that were successfully recovered.
        System.out.println("Document loaded, page count = " + doc.getPageCount());
    }
}
```

### Mengapa `RecoveryMode.PARSE`?

- **PARSE** – Aspose.Words mem-parsing fragmen apa pun yang dapat dipahami, menyatukan dokumen yang sebagian berfungsi. Ideal ketika Anda membutuhkan *setiap* konten dari file yang rusak.  
- **SKIP** – Library melewati bagian yang rusak sepenuhnya, yang dapat lebih cepat tetapi mungkin membuang lebih banyak data.  

Dalam kebanyakan skenario dunia nyata, **PARSE** adalah pilihan yang lebih aman karena memaksimalkan jumlah teks, gambar, dan format yang dapat dipulihkan.

---

## ## Display Page Count After Recovery

Setelah dokumen dimuat, langkah logis berikutnya adalah memverifikasi keberhasilan operasi. Metrik paling sederhana namun paling informatif adalah jumlah halaman. Metode `Document.getPageCount()` melakukan tepat itu.

```java
int pages = doc.getPageCount();
System.out.println("Document loaded, page count = " + pages);
```

Jika file tidak dapat dibaca sama sekali, Aspose.Words akan melemparkan pengecualian *sebelum* Anda mencapai baris ini. Ketika Anda melihat jumlah halaman `0` atau angka yang sangat rendah, biasanya berarti mode pemulihan harus membuang bagian besar dari file asli.

**Output yang diharapkan (contoh):**

```
Document loaded, page count = 12
```

Itu memberi tahu Anda bahwa library berhasil merekonstruksi dua belas halaman dari sumber yang rusak—cukup solid untuk sebuah `.docx` yang rusak.

---

## ## Edge Cases & Common Pitfalls

### 1️⃣ Bagian Header/Footer yang Rusak
Kadang hanya badan utama yang ter‑parsing sementara header dan footer hilang. Jika Anda mengandalkan mereka untuk branding, Anda mungkin perlu menyuntikkan kembali setelah pemulihan.

### 2️⃣ Gambar yang Tidak Dapat Dimuat
Gambar yang disematkan sering dihapus ketika kontainer zip (format `.docx` yang mendasarinya) rusak. Anda dapat mendeteksinya dengan mengiterasi `doc.getSections()` dan memeriksa `Section.getBody().getParagraphs()` untuk objek `Shape`.

```java
for (Section sec : doc.getSections()) {
    for (Paragraph para : sec.getBody().getParagraphs()) {
        for (Node node : para.getChildNodes(NodeType.SHAPE, true)) {
            Shape shape = (Shape) node;
            System.out.println("Found image: " + shape.getName());
        }
    }
}
```

Jika loop tidak mencetak apa pun, kemungkinan mode pemulihan melewatkan gambar.

### 3️⃣ Dokumen Besar dan Memori
Memulihkan file rusak berukuran 200 halaman dapat memakan banyak memori. Pertimbangkan meningkatkan ukuran heap JVM (`-Xmx2g`) ketika Anda mengantisipasi dokumen besar.

### 4️⃣ Pembatasan Lisensi
Versi evaluasi membatasi beberapa fitur, tetapi **pemulihan** berfungsi penuh. Namun, jumlah halaman yang dicetak mungkin dibatasi hanya beberapa halaman dalam versi percobaan. Selalu uji dengan build berlisensi untuk produksi.

---

## ## Full End‑to‑End Example (Runnable)

Berikut adalah program mandiri yang dapat Anda masukkan ke dalam proyek Maven atau Gradle apa pun. Program ini menyertakan deklarasi dependensi yang diperlukan untuk Aspose.Words 23.12.

### Potongan `pom.xml` Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### File sumber Java `RecoveryModeDemo.java`

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) {
        try {
            // Initialize load options
            LoadOptions loadOptions = new LoadOptions();

            // Set recovery mode to PARSE – this is the key step to recover corrupted Word files.
            loadOptions.setRecoveryMode(RecoveryMode.PARSE);

            // Load the possibly damaged document
            Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

            // Display the page count to confirm how much content was recovered.
            System.out.println("Document loaded, page count = " + doc.getPageCount());

            // (Optional) Save the recovered document for further inspection.
            doc.save("YOUR_DIRECTORY/Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Apa yang dilakukan kode ini:**

1. **Mengatur mode pemulihan** – inti dari tutorial kami.  
2. Memuat file yang rusak menggunakan `LoadOptions` yang dikonfigurasi.  
3. **Menampilkan jumlah halaman**, memberikan umpan balik langsung.  
4. Menyimpan versi yang telah dibersihkan (`Recovered.docx`) sehingga Anda dapat membukanya di Word nanti.

Jalankan program dengan:

```bash
javac -cp "path/to/aspose-words-23.12.jar" RecoveryModeDemo.java
java -cp ".:path/to/aspose-words-23.12.jar" RecoveryModeDemo
```

Anda akan melihat jumlah halaman tercetak di konsol, mengonfirmasi pemulihan berhasil.

---

## ## Visual Overview (Image)

![diagram alur set recovery mode](https://example.com/images/recovery-mode-flow.png "Diagram yang menggambarkan cara kerja set recovery mode di Aspose.Words untuk Java")

*Teks alt mencakup kata kunci utama **set recovery mode** untuk memenuhi SEO.*

---

## ## Frequently Asked Questions

**Q: Bagaimana jika `RecoveryMode.PARSE` masih melempar pengecualian?**  
A: Itu biasanya berarti file tidak dapat diselamatkan—mungkin kontainer zipnya benar‑benar rusak. Dalam kasus seperti itu, Anda mungkin memerlukan alat perbaikan pihak ketiga sebelum menyerahkannya ke Aspose.Words.

**Q: Bisakah saya menggabungkan `RecoveryMode.PARSE` dengan callback pemuatan dokumen khusus?**  
A: Tentu saja. Implementasikan `IWarningCallback` untuk menangkap peringatan apa pun yang dikeluarkan Aspose.Words selama proses parsing. Ini memberi Anda wawasan tentang bagian mana yang dilewati.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    public void warning(WarningInfo info) {
        System.out.println("Warning: " + info.getDescription());
    }
});
```

**Q: Apakah mengubah mode pemulihan memengaruhi file asli?**  
A: Tidak. Aspose.Words bekerja pada salinan di memori; file sumber tetap tidak tersentuh kecuali Anda secara eksplisit memanggil `doc.save()`.

---

## ## Wrap‑Up

Kami telah membahas cara **set recovery mode** di Aspose.Words untuk Java, mengapa `PARSE` umumnya pilihan terbaik untuk menyelamatkan dokumen yang rusak, dan cara **menampilkan jumlah halaman** untuk memverifikasi hasilnya. Dengan mengikuti contoh lengkap, Anda kini memiliki solusi siap‑jalankan yang dapat **memulihkan Word yang rusak** dan memberi Anda umpan balik langsung tentang keberhasilan operasi.

Langkah selanjutnya? Coba ganti ke `RecoveryMode.SKIP` untuk melihat perbedaannya, bereksperimen dengan file multi‑section besar, atau integrasikan logika ini ke dalam layanan web yang secara otomatis memperbaiki dokumen yang diunggah pengguna. Pola yang sama berlaku untuk PDF (menggunakan Aspose.PDF) dan bahkan untuk pemulihan teks biasa dengan library lain—ingat saja ide intinya: konfigurasikan loader, lakukan pemulihan, lalu validasi dengan metrik sederhana seperti jumlah halaman.

Selamat coding, semoga dokumen Anda tetap utuh!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara Mengatur LoadOptions di Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words Java: Panduan Komprehensif untuk Pemrosesan Dokumen Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Menggabungkan Beberapa File Word dengan Aspose.Words untuk Java](/words/english/java/document-manipulation/cloning-and-combining-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}