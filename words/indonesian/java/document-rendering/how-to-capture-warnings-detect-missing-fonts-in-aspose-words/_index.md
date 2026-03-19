---
category: general
date: 2026-03-19
description: Pelajari cara menangkap peringatan di Aspose.Words untuk Java dan mendeteksi
  font yang hilang. Panduan langkah demi langkah ini juga menunjukkan cara menangani
  font yang hilang dengan elegan.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: id
og_description: Cara menangkap peringatan di Aspose.Words untuk Java, mendeteksi font
  yang hilang, dan menangani font yang hilang dengan contoh kode lengkap.
og_title: Cara Menangkap Peringatan – Mendeteksi Font yang Hilang di Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Cara Menangkap Peringatan – Mendeteksi Font yang Hilang di Aspose.Words
url: /id/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menangkap Peringatan – Mendeteksi Font yang Hilang di Aspose.Words

Pernah bertanya‑tanya **bagaimana cara menangkap peringatan** ketika dokumen Word dimuat dan beberapa font tidak tersedia di mesin? Anda tidak sendirian. Dalam banyak proyek dunia nyata, font yang hilang menyebabkan pergeseran tata letak secara diam‑diam, dan satu‑satunya cara untuk mengetahui apa yang terjadi adalah dengan mendengarkan aliran peringatan yang dikeluarkan oleh Aspose.Words.  

Dalam tutorial ini kami akan membahas contoh lengkap yang siap dijalankan yang **mendeteksi font yang hilang**, menunjukkan **cara mendeteksi font yang hilang** secara programatis, dan bahkan memberikan tip cepat tentang **penanganan font yang hilang** agar output Anda tetap dapat diprediksi.

> **Catatan cepat:** Kode ini bekerja dengan Aspose.Words 23.9 (atau lebih baru) dan memerlukan Java 8+.

---

## Apa yang Anda Butuhkan

- **Aspose.Words for Java** (dependensi Maven/Gradle atau JAR di classpath)  
- File Word (`input.docx`) yang merujuk pada font yang tidak terpasang di sistem Anda (misalnya “Comic Sans MS”)  
- IDE Java atau setup baris perintah sederhana `javac`/`java`  

Tidak ada pustaka lain yang diperlukan—semua yang lain berada di dalam paket Aspose.Words.

---

## Langkah 1 – Siapkan LoadOptions untuk Menangkap Peringatan  

Untuk mulai mendengarkan peringatan, Anda harus membuat instance `LoadOptions`. Objek ini memberi tahu pemuat untuk melacak setiap masalah yang ditemuinya, seperti font yang hilang.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Mengapa ini penting:** Tanpa `LoadOptions` pemuat secara diam‑diam menggantikan font yang hilang dengan font sistem default, dan Anda tidak akan pernah tahu bahwa substitusi terjadi. Mengaktifkan peringatan memberi Anda visibilitas penuh.

---

## Langkah 2 – Muat Dokumen Menggunakan LoadOptions  

Sekarang kita benar‑benar memuat dokumen. `LoadOptions` yang baru saja kita buat diteruskan ke konstruktor, sehingga setiap peringatan yang dihasilkan selama parsing ditangkap.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Tip pro:** Jika Anda memproses banyak file dalam satu batch, gunakan kembali instance `LoadOptions` yang sama untuk menghindari pembuatan objek yang tidak perlu.

---

## Langkah 3 – Iterasi Peringatan yang Ditangkap  

Aspose.Words menyimpan setiap peringatan sebagai objek `WarningInfo`. Kami hanya peduli pada peringatan yang terkait dengan font, sehingga kami menyaring `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Penjelasan:**  
- `document.getWarnings()` mengembalikan daftar semua peringatan yang terjadi selama pemuatan.  
- `FontSubstitutionWarningInfo` berisi dua data penting: **font yang diminta** (yang diminta oleh DOCX) dan **font yang sebenarnya** yang digunakan oleh Aspose.Words sebagai fallback.  
- Dengan mencetak keduanya, Anda langsung melihat font mana yang hilang dan substitusi apa yang terjadi.

---

## Langkah 4 – (Opsional) Tangani Font yang Hilang Secara Programatis  

Menangkap peringatan hanya setengah cerita. Setelah Anda mengetahui sebuah font hilang, Anda mungkin ingin **menangani font yang hilang** dengan menyediakan substitusi khusus atau dengan mencatat masalah tersebut untuk ditinjau nanti.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Mengapa melakukan ini?**  
- Menjamin rendering yang konsisten di semua mesin.  
- Mencegah perubahan tata letak yang tidak terduga pada PDF atau gambar yang dihasilkan kemudian.  

Anda juga dapat menyimpan detail peringatan ke basis data, mengirim email ke tim konten, atau bahkan menghentikan proses jika font penting hilang.

---

## Contoh Lengkap yang Berfungsi  

Berikut adalah program lengkap yang dapat dijalankan. Cukup ganti `YOUR_DIRECTORY/input.docx` dengan path ke file uji Anda, tambahkan JAR Aspose.Words ke classpath, dan jalankan.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Output yang diharapkan** (ketika “Comic Sans MS” tidak ada):

```
Requested: Comic Sans MS → Substituted: Arial
```

Setelah kode fallback opsional dijalankan, `output.docx` yang disimpan akan dirender menggunakan **Arial** di mana pun “Comic Sans MS” awalnya direferensikan.

---

## Pertanyaan Umum & Kasus Tepi  

| Pertanyaan | Jawaban |
|------------|---------|
| *Bagaimana jika dokumen memiliki beberapa font yang hilang?* | Loop akan menghasilkan peringatan untuk masing‑masing. Anda dapat mengumpulkannya dalam `Map<String, String>` untuk pemrosesan batch. |
| *Apakah ini bekerja untuk PDF yang dihasilkan dari dokumen?* | Tentu saja. Substitusi font terjadi selama fase pemuatan, sehingga ekspor selanjutnya (PDF, HTML, gambar) menggunakan font yang sudah diselesaikan. |
| *Bisakah saya menekan peringatan alih‑alih menangkapnya?* | Ya—atur `loadOptions.setWarningCallback(null);` tetapi Anda akan kehilangan visibilitas terhadap font yang hilang. |
| *Apakah daftar peringatan dibersihkan setelah menyimpan?* | Koleksi peringatan merupakan milik instance `Document`. Setelah Anda memanggil `document.save()`, daftar tetap tidak berubah kecuali Anda membuat `Document` baru. |
| *Bagaimana dengan font khusus yang disematkan dalam DOCX?* | Font yang disematkan dianggap tersedia; Aspose.Words akan menggunakannya meskipun tidak terpasang di sistem host. |

---

## Tips Pro untuk Penggunaan Produksi  

- **Cache FontSettings:** Jika Anda memproses ratusan file, buat satu `FontSettings` dengan fallback pilihan Anda dan gunakan kembali untuk menghindari beban tambahan.  
- **Log Data Terstruktur:** Alih‑alih `System.out` biasa, tulis peringatan ke log JSON—ini memudahkan analitik downstream (misalnya “font yang paling sering hilang”) secara sederhana.  
- **Validasi Dini:** Jalankan “dry‑load” cepat dengan `LoadOptions` sebelum pemrosesan berat; hentikan lebih awal jika font penting hilang.  
- **Keamanan Thread:** Objek `Document` tidak thread‑safe. Jaga pemrosesan tiap file di thread masing‑masing atau gunakan `LoadOptions` thread‑local.  

---

## Kesimpulan  

Anda kini tahu **cara menangkap peringatan** di Aspose.Words untuk Java, **mendeteksi font yang hilang**, dan **menangani font yang hilang** dengan strategi fallback yang bersih. Dengan memanfaatkan `LoadOptions` dan mengiterasi `document.getWarnings()`, Anda memperoleh wawasan penuh tentang peristiwa substitusi font, memastikan dokumen yang dihasilkan terlihat persis seperti yang diharapkan di semua lingkungan.

Siap untuk langkah selanjutnya? Cobalah memperluas pola ini untuk **mendeteksi gambar yang hilang**, **melacak fitur yang tidak didukung**, atau bahkan **menyematkan secara otomatis font yang hilang** ke dalam file output. Pendekatan penangkapan peringatan yang sama bekerja untuk banyak skenario pemrosesan dokumen lainnya, menjadikan kode Anda kuat dan siap masa depan.

Selamat coding, semoga dokumen Anda selalu dirender dengan indah!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}