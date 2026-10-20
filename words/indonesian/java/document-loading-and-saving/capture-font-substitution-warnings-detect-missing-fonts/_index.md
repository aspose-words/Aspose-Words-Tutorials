---
category: general
date: 2026-04-04
description: Tangkap peringatan substitusi font saat memuat dokumen Word dengan Aspose.Words
  untuk Java dan deteksi font yang hilang secara otomatis. Ikuti panduan langkah demi
  langkah ini.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: id
og_description: Tangkap peringatan substitusi font saat memuat dokumen Word dengan
  Aspose.Words untuk Java dan deteksi font yang hilang dalam beberapa langkah mudah.
og_title: Tangkap Peringatan Substitusi Font – Deteksi Font yang Hilang
tags:
- Aspose.Words
- Java
- Document Processing
title: Tangkap Peringatan Substitusi Font – Deteksi Font yang Hilang
url: /id/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tangkap Peringatan Substitusi Font – Deteksi Font yang Hilang

Pernahkah Anda perlu **menangkap peringatan substitusi font** saat membuka file Word, hanya untuk menemukan bahwa jenis huruf penting tidak ada? Anda tidak sendirian. Dalam banyak alur kerja perusahaan, font yang hilang dapat mengubah laporan yang diformat dengan sempurna menjadi kekacauan, dan satu-satunya petunjuk yang Anda dapatkan adalah peringatan diam yang jarang dilihat oleh pengembang.

Kabar baiknya, Aspose.Words for Java memungkinkan Anda menyisipkan kode ke dalam proses pemuatan dan **mendeteksi font yang hilang** sebelum mereka menimbulkan masalah. Dalam tutorial ini kami akan membimbing Anda melalui contoh lengkap yang dapat dijalankan, yang mencetak setiap peringatan substitusi langsung ke konsol, sehingga Anda dapat memutuskan apakah akan menyematkan font yang tepat, menggantinya, atau memberi tahu pengguna.

Pada akhir panduan ini Anda akan tahu cara:

* Menyiapkan objek `LoadOptions` dengan callback peringatan khusus.
* Menyaring callback sehingga hanya merespons peristiwa substitusi font.
* Memuat file `.docx` apa pun dan melihat peringatannya secara langsung.
* Memperluas solusi untuk mencatat peringatan, melempar pengecualian, atau bahkan meng‑install font yang hilang secara otomatis.

Tidak memerlukan dokumentasi eksternal—hanya beberapa baris Java dan JAR Aspose.Words.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

* Java 8 atau yang lebih baru terpasang (versi LTS terbaru bekerja paling baik).
* Aspose.Words for Java 23.11 atau lebih baru – Anda dapat mengambil artefak Maven atau JAR biasa dari situs web Aspose.
* Dokumen Word yang merujuk pada font yang tidak ada di mesin pengembangan Anda (misalnya, “MyFancyFont”).  
* IDE atau editor teks pilihan Anda – saya menggunakan IntelliJ IDEA, tetapi Eclipse atau VS Code juga dapat digunakan.

Jika ada yang belum Anda kenal, jeda sejenak dan instal dulu; sisanya tutorial mengasumsikan semuanya sudah siap.

---

## Tangkap Peringatan Substitusi Font Menggunakan Aspose.Words

Inti solusi berada pada sebuah instance `LoadOptions`. Dengan menetapkan `IWarningCallback` kita dapat menyela setiap peringatan yang dikeluarkan perpustakaan selama fase pemuatan.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Mengapa ini berhasil:**  
`LoadOptions` memberi tahu Aspose.Words bagaimana memperlakukan file yang masuk. Antarmuka `IWarningCallback` adalah hook yang menerima objek `WarningInfo` untuk *setiap* peringatan. Dengan memeriksa `info.getWarningType()` kita menyaring semua kecuali `SUBSTITUTED_FONT`. Properti `description` berisi pesan yang dapat dibaca manusia seperti “Font 'MyFancyFont' was substituted with 'Arial'”.

### Output konsol yang diharapkan

Jika dokumen sumber merujuk pada font yang tidak terpasang, Anda akan melihat sesuatu seperti:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Jika dokumen hanya menggunakan font yang ada di mesin, callback tetap diam dan Anda hanya akan mendapatkan baris akhir “Document loaded successfully.”.

---

## Deteksi Font yang Hilang dalam Dokumen Anda

Anda mungkin bertanya, *“Apakah peringatan substitusi sama dengan font yang hilang?”* Dalam kebanyakan kasus, ya—Aspose.Words menggantikan font yang hilang dengan fallback dan melaporkannya melalui `SUBSTITUTED_FONT`. Namun, ada kasus tepi di mana font memang ada tetapi gaya tepatnya (bold‑italic, fitur OpenType tertentu) tidak, sehingga terjadi substitusi halus.

Untuk memastikan Anda menangkap setiap celah, Anda dapat menggabungkan callback peringatan dengan inspeksi setelah pemuatan:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Pro tip:** Jika Anda menemukan run yang masih merujuk pada font yang hilang, Anda dapat menggantinya secara langsung:

```java
font.setName("Arial"); // fallback
```

Dengan cara ini Anda menjamin hasil visual yang konsisten, bahkan jika peringatan asli ditekan.

---

## Kesalahan Umum & Cara Menghindarinya

| Kesalahan | Mengapa Terjadi | Solusi |
|-----------|----------------|--------|
| **Lupa menetapkan callback** | `LoadOptions` secara default menggunakan callback kosong, sehingga peringatan tidak muncul. | Selalu panggil `loadOptions.setWarningCallback(...)` sebelum memuat. |
| **Menggunakan tipe peringatan yang salah** | `WarningType.SUBSTITUTED_FONT` adalah satu‑satunya enum yang menandakan font yang hilang. | Filter pada `WarningType.SUBSTITUTED_FONT` *tepat*; tipe lain (misalnya `UNKNOWN_FILE_FORMAT`) tidak terkait. |
| **Hard‑coding jalur file** | Berfungsi secara lokal tetapi gagal pada pipeline CI/CD. | Gunakan jalur relatif atau terima lokasi file sebagai argumen baris perintah. |
| **Mengabaikan font Unicode** | Beberapa font yang hilang hanya menjadi masalah untuk karakter tertentu. | Uji dengan dokumen yang berisi seluruh set karakter yang Anda harapkan dukung. |
| **Menjalankan di server tanpa konfigurasi font** | Server mungkin tidak memiliki font fallback, menyebabkan substitusi tak terduga. | Instal set minimal font umum (Arial, Times New Roman) di server. |

---

## Memperluas Solusi

Sekarang Anda dapat **menangkap peringatan substitusi font**, Anda mungkin ingin:

* **Mencatat peringatan ke file** – ganti `System.out.println` dengan logger seperti SLF4J.
* **Melempar pengecualian** – berguna dalam pipeline otomatis di mana font yang hilang harus membuat build gagal:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Meng‑install font yang hilang secara otomatis** – unduh TTF/OTF yang diperlukan pada runtime dan tambahkan ke `GraphicsEnvironment` Java. Itu skenario yang lebih maju, tetapi sepenuhnya memungkinkan.

---

## Diagram (opsional)

![Capture font substitution warnings flow diagram showing LoadOptions → WarningCallback → Console output](capture-font-substitution-warnings-diagram.png)

*Alt text:* “Diagram alur penangkapan peringatan substitusi font yang menggambarkan bagaimana Aspose.Words mengarahkan peringatan font yang hilang ke callback khusus.”

---

## Kesimpulan

Kami baru saja membahas cara **menangkap peringatan substitusi font** dan **mendeteksi font yang hilang** saat memuat dokumen Word dengan Aspose.Words for Java. Dengan mengonfigurasi objek `LoadOptions` dan mengimplementasikan `IWarningCallback` yang kecil, Anda memperoleh visibilitas penuh ke proses fallback font, memungkinkan Anda mencatat, mengganti, atau menghentikan proses ketika jenis huruf tidak tersedia.

Singkatnya: setel callback, filter untuk `SUBSTITUTED_FONT`, muat dokumen, dan tangani output sesuai kebutuhan aplikasi Anda. Dari sini Anda dapat memperluas ke kerangka kerja logging, pemeriksaan CI, atau bahkan penyediaan font otomatis.

Ingin melangkah lebih jauh? Coba:

* **Menyematkan font** langsung ke dalam dokumen yang disimpan (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` dengan `FontEmbeddingMode.EMBED_ALL`).
* **Menghasilkan PDF** setelah memperbaiki font, memastikan output akhir terlihat persis seperti yang diharapkan.
* **Memindai seluruh folder** dokumen untuk font yang hilang dan menghasilkan laporan ringkasan.

Itu saja untuk saat ini—selamat coding, dan semoga dokumen Anda selalu ditampilkan dengan jenis huruf yang tepat!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}