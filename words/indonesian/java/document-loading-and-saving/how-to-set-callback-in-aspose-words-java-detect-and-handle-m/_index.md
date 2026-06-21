---
category: general
date: 2026-06-20
description: Cara mengatur callback di Aspose.Words Java untuk mendeteksi font yang
  hilang dan menyesuaikan pemuatan dokumen. Pelajari langkah demi langkah penanganan
  peringatan substitusi font.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: id
og_description: cara mengatur callback di Aspose.Words Java untuk mendeteksi font
  yang hilang, menangani substitusi, dan menyesuaikan pemuatan dokumen. panduan lengkap
  dengan kode.
og_title: Cara mengatur callback – Deteksi Font yang Hilang di Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: Cara mengatur callback di Aspose.Words Java – Deteksi dan Tangani Font yang
  Hilang
url: /id/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cara mengatur callback di Aspose.Words Java – Deteksi dan Tangani Font yang Hilang

Pernah bertanya-tanya **cara mengatur callback** di Aspose.Words Java sehingga Anda dapat mendeteksi font yang hilang sebelum merusak PDF atau DOCX Anda? Anda tidak sendirian. Peringatan font yang hilang dapat secara diam-diam merusak tata letak, dan tanpa callback peringatan yang tepat Anda mungkin tidak menyadarinya sampai dokumen akhir terlihat aneh.  

Dalam tutorial ini kami akan membahas contoh lengkap yang siap‑jalan yang **mendeteksi font yang hilang**, **menangani font yang hilang** dengan elegan, dan menunjukkan **cara menyesuaikan pemuatan dokumen** dengan callback peringatan. Pada akhir tutorial Anda akan memiliki kelas Java mandiri yang dapat Anda masukkan ke proyek mana pun—tanpa harus mencari dokumentasi tambahan.

## Apa yang Anda Butuhkan

- Java 8 atau lebih baru (kode ini juga bekerja dengan Java 11+)  
- Perpustakaan Aspose.Words for Java (versi 23.9 atau lebih baru)  
- File DOCX yang merujuk pada font yang tidak Anda miliki (misalnya, font korporat khusus)  

Jika Anda belum menambahkan Aspose.Words ke proyek Maven Anda, cukup sertakan:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Itu saja—tanpa plugin tambahan, tanpa dependensi native.

---

## Langkah 1: Pahami Mekanisme WarningCallback

**Warning callback** adalah cara Aspose.Words memberi tahu Anda ketika sesuatu yang tidak terduga terjadi saat memuat atau menyimpan dokumen. Dengan mengimplementasikan `IWarningCallback` Anda mendapatkan kontrol penuh atas apa yang dicatat, diabaikan, atau bahkan diubah menjadi pengecualian.

> **Mengapa ini penting:**  
> Ketika sebuah font hilang, Aspose menggantinya dengan font fallback. Hasil visualnya dapat sangat berbeda, terutama untuk PDF yang sangat bergantung pada branding. Dengan menangkap `WarningType.FONT_SUBSTITUTION`, Anda dapat mencatat nama font yang tepat, memutuskan apakah harus menghentikan proses, atau mengganti dengan font khusus Anda secara programatis.

---

## Langkah 2: Buat Instance LoadOptions

`LoadOptions` adalah titik masuk untuk menyesuaikan pemuatan dokumen. Anda akan melampirkan callback ke objek ini sebelum benar‑benarnya memuat file.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Pada titik ini `loadOptions` hanyalah wadah biasa—belum ada yang terjadi. Keajaiban sesungguhnya dimulai ketika kita menyambungkan callback.

---

## Langkah 3: Implementasikan dan Lampirkan Callback

Berikut adalah kelas anonim ringkas yang mengimplementasikan `IWarningCallback`. Ia mencetak baris ramah ke konsol setiap kali terjadi substitusi font.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Tips pro:** Jika Anda ingin **menangani font yang hilang** dengan menyediakan pengganti, Anda juga dapat mengatur `FontSettings` pada `LoadOptions` dan memetakan font yang hilang ke fallback yang dikenal.

---

## Langkah 4: Muat Dokumen dengan Opsi Kustom Anda

Setelah callback terpasang, muat dokumen. Jika file tersebut merujuk pada font yang tidak Anda miliki, Anda akan melihat peringatan tercetak.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

Saat Anda menjalankan program, konsol mungkin menampilkan:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Baris itu membuktikan bahwa Anda telah berhasil **mendeteksi font yang hilang** dan kini berada dalam posisi untuk **menangani font yang hilang** sesuai keinginan Anda.

---

## Langkah 5: Opsional – Ganti Font yang Hilang dengan Font yang Dikenal

Jika Anda lebih suka secara otomatis mengganti setiap font yang hilang dengan, misalnya, `Times New Roman`, Anda dapat menambahkan objek `FontSettings`:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Sekarang dokumen dimuat, dan setiap referensi ke `MyCustomFont` secara diam-diam diganti dengan `Times New Roman`. Konsol tetap akan memberi tahu apa yang diganti, sehingga Anda tetap terinformasi.

---

## Contoh Lengkap yang Berfungsi

Berikut adalah satu kelas Java yang menggabungkan semua langkah di atas. Salin‑tempel ke IDE Anda, sesuaikan `docPath`, dan jalankan.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Output yang diharapkan**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Sekarang Anda memiliki cara yang dapat direproduksi untuk **mendeteksi font yang hilang**, **menangani font yang hilang**, dan **menyesuaikan pemuatan dokumen**—semua dengan mempelajari **cara mengatur callback** dengan benar.

---

## Pertanyaan yang Sering Diajukan

### Bagaimana jika saya ingin program berhenti memuat ketika sebuah font hilang?

Lempar pengecualian di dalam metode `warning`:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Blok `catch` di bagian bawah akan menangkapnya, dan Anda dapat memutuskan bagaimana mencatat atau memberi peringatan kepada pengguna.

### Apakah ini bekerja untuk PDF yang dihasilkan dari DOCX?

Tentu saja. Callback dipicu selama fase **loading**, yang identik untuk semua format output (`save` ke PDF, DOCX, HTML, dll.). Selama Anda memuat dokumen sumber dengan `LoadOptions` yang sama, Anda akan menangkap font yang hilang sebelum memengaruhi PDF akhir.

### Bisakah saya menangkap tipe peringatan lain (misalnya, konversi gambar)?

Ya—`WarningInfo.getWarningType()` dapat dibandingkan dengan enum lain seperti `WarningType.IMAGE_CONVERSION`. Cukup tambahkan cabang `if` tambahan di dalam callback.

### Apakah ada dampak pada performa?

Sangat kecil. Callback dijalankan secara sinkron selama proses loading, dan pemeriksaan tambahan bersifat ringan. Jika Anda memuat ribuan dokumen, Anda mungkin ingin menonaktifkan peringatan di produksi dengan mengatur `loadOptions.setWarningCallback(null);`.

---

## Gambaran Visual

![how to set callback example in Aspose.Words Java](https://example.com/images/callback-diagram.png "how to set callback")

*Diagram ini menggambarkan alur: `LoadOptions` → `IWarningCallback` → Pemuatan dokumen → Penanganan substitusi font.*

---

## Penutup

Kami telah membahas **cara mengatur callback** di Aspose.Words Java, mendemonstrasikan **deteksi font yang hilang**, menunjukkan cara praktis **menangani font yang hilang**, dan menjelaskan **penyesuaian pemuatan dokumen** dengan `LoadOptions`.  

Dengan pengetahuan ini, Anda kini dapat melindungi alur kerja dokumen Anda dari pertukaran font yang diam‑diam, menjaga konsistensi branding, dan memberi pengguna umpan balik yang jelas ketika sesuatu tidak beres.

### Apa Selanjutnya?

- Jelajahi **tabel substitusi font** untuk pemetaan massal banyak font yang hilang.  
- Gabungkan callback ini dengan **validasi dokumen** untuk menegakkan panduan gaya.  
- Coba **custom warning callbacks** yang menulis ke file log atau sistem pemantauan alih‑alih `System.out`.  

Silakan bereksperimen, dan beri tahu kami bagaimana Anda menyesuaikan callback untuk proyek Anda sendiri. Selamat coding!

---


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}