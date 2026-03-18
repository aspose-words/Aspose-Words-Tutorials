---
category: general
date: 2026-03-17
description: Pelajari tutorial callback peringatan Aspose untuk mendeteksi font yang
  hilang dan melacak font yang hilang dalam dokumen Java dengan contoh lengkap yang
  dapat dijalankan.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: id
og_description: Kuasai tutorial callback peringatan Aspose untuk mendeteksi font yang
  hilang dan melacak font yang hilang dalam alur kerja pemrosesan Word Java Anda.
og_title: Tutorial Callback Peringatan Aspose – Deteksi Font yang Hilang
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Tutorial Callback Peringatan Aspose – Deteksi dan Lacak Font yang Hilang
url: /id/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# tutorial callback peringatan aspose – Deteksi dan Lacak Font yang Hilang

Pernah bertanya-tanya bagaimana cara **mendeteksi font yang hilang** saat mengonversi atau mengedit file Word dengan Aspose.Words? Anda tidak sendirian. Dalam banyak proyek dunia nyata, satu font yang tidak tersedia dapat menyebabkan gangguan tata letak, dan Anda memerlukan cara yang dapat diandalkan untuk **melacak font yang hilang** sebelum mereka menimbulkan masalah di kemudian hari.  

Kabar baiknya? **tutorial callback peringatan aspose** memberikan kait programatik yang bersih yang mencetak peringatan substitusi font tepat saat terjadi. Dalam panduan ini kami akan menuntun Anda menyiapkan callback, memuat dokumen, dan melihat peringatan beraksi—semua dalam Java.

Pada akhir artikel ini Anda akan dapat secara otomatis menemukan font yang hilang, mencatatnya, dan memutuskan apakah akan menyematkan pengganti atau menyesuaikan file sumber Anda. Tidak memerlukan alat eksternal.

## Prasyarat

- **Java 8+** (kode dapat dikompilasi dengan JDK terbaru apa pun)
- **Aspose.Words for Java** versi 23.10 atau lebih baru – unduh dari portal Aspose atau tambahkan dependensi Maven.
- Sebuah contoh DOCX yang sengaja merujuk pada font yang tidak Anda miliki (misalnya “Comic Sans MS” pada mesin Linux).

Itu saja—tanpa pustaka tambahan, tanpa langkah build yang rumit.

## Langkah 1: Daftarkan Callback Peringatan – Inti dari tutorial callback peringatan aspose

Hal pertama yang diajarkan tutorial ini adalah cara melampirkan listener peringatan. Aspose.Words mengeluarkan objek `WarningInfo` untuk setiap masalah yang ditemuinya, dan flag `WarningSource.FONT_SUBSTITUTION` memberi tahu kita tepat kapan sebuah font sedang diganti.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Mengapa ini penting:** Tanpa callback, Aspose secara diam-diam menggantikan font yang hilang, dan Anda tidak pernah tahu glyph mana yang mungkin tampak tidak tepat. Dengan mencatat peringatan, Anda dapat **mendeteksi font yang hilang** lebih awal dan memutuskan apakah akan menyematkan yang benar.

> **Tips pro:** Jika Anda perlu mengumpulkan peringatan untuk pelaporan nanti, simpan mereka dalam `List<WarningInfo>` alih‑alih mencetak langsung.

## Langkah 2: Muat Dokumen – Tempat font yang hilang mungkin bersembunyi

Sekarang kita memuat DOCX yang mungkin merujuk pada font yang tidak ada di mesin. Proses pemuatan memicu callback peringatan jika ada font yang hilang.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Apa yang terjadi di balik layar?** Aspose mem-parsing definisi gaya dokumen, memindai setiap run teks, dan memeriksa repositori font sistem. Ketika tidak menemukan kecocokan yang tepat, ia beralih ke font pengganti dan memicu peringatan yang baru saja kita kaitkan.

## Langkah 3: Simpan Dokumen – Mengeluarkan peringatan

Akhirnya, kita menyimpan dokumen. Operasi penyimpanan juga mengevaluasi ulang font, sehingga peringatan yang belum muncul saat pemuatan akan muncul sekarang.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Saat Anda menjalankan program, Anda akan melihat output konsol serupa dengan:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Output tersebut membuktikan bahwa **tutorial callback peringatan aspose** berfungsi, dan Anda telah berhasil **mendeteksi font yang hilang** serta kini **melacak font yang hilang** melalui log.

## Cara Mendeteksi Font yang Hilang dalam Dokumen Word – Lebih dari Dasar

Pendekatan callback sangat cocok untuk eksekusi satu kali, tetapi kadang Anda memerlukan utilitas yang dapat dipakai ulang. Berikut pembungkus singkat yang dapat Anda masukkan ke proyek mana pun:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Panggil seperti:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Sekarang Anda memiliki metode **detect missing fonts** yang dapat dipakai kembali dan mengembalikan daftar yang dapat Anda alirkan ke pipeline CI atau UI.

## Melacak Font yang Hilang dengan Aspose.Words – Pelaporan untuk Tim

Dalam tim yang lebih besar, Anda mungkin ingin menghasilkan laporan CSV semua font yang hilang di banyak dokumen. Gabungkan utilitas sebelumnya dengan iterasi file sederhana:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

Menjalankan skrip ini akan memberi Anda CSV **track missing fonts** yang dapat dilihat setiap pengembang sebelum meng‑commit dokumen ke produksi.

## Kesalahan Umum & Cara Menghindarinya

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Callback tidak dipicu** | Anda lupa mengatur callback **sebelum** memuat dokumen. | Letakkan `Document.setWarningCallback` di bagian paling atas `main`. |
| **Hanya peringatan pertama yang muncul** | Aspose menyimpan cache peringatan per instance `Document`. | Gunakan objek `Document` baru untuk setiap file, atau reset callback di antara run. |
| **Nama font salah di log** | Deskripsi mengandung teks tambahan (“Font … not found”). | Hapus menggunakan regex seperti yang ditunjukkan pada contoh CSV. |
| **Penurunan performa pada batch besar** | Callback dijalankan pada setiap run teks, yang dapat mahal. | Batasi pemeriksaan ke langkah pre‑flight; lewati penyimpanan jika hanya perlu deteksi. |

## Hasil yang Diharapkan & Verifikasi

1. **Output konsol** – Anda harus melihat setidaknya satu baris “Font substitution warning” untuk setiap font yang hilang.  
2. **Laporan CSV** – Setelah skrip bulk selesai, buka `missing-fonts-report.csv` dan verifikasi setiap baris mencantumkan nama dokumen serta font yang tepatnya hilang.  
3. **Dokumen yang disimpan** – DOCX output akan dirender menggunakan font pengganti, tetapi tata letak visual mungkin berbeda dari aslinya.

Jika salah satu langkah tidak berperilaku seperti yang dijelaskan, periksa kembali bahwa JAR Aspose.Words berada di classpath Anda dan bahwa `input.docx` memang merujuk pada font yang tidak ada di OS Anda.

## Kesimpulan

Anda baru saja menyelesaikan **tutorial callback peringatan aspose** yang menunjukkan cara **mendeteksi font yang hilang** dan **melacak font yang hilang** dalam aplikasi Java. Dengan mendaftarkan listener peringatan, memuat dokumen, dan secara opsional mengekspor temuan, Anda memperoleh visibilitas penuh terhadap masalah terkait font sebelum mereka muncul di produksi.

Selanjutnya, Anda dapat menjelajahi:

- Menyematkan font yang hilang langsung dengan `LoadOptions.setFontSubstitution`.
- Menggunakan kelas `FontSettings` untuk memetakan font yang hilang ke pengganti tertentu.
- Mengintegrasikan laporan CSV ke pipeline CI/CD untuk menolak build ketika font yang tidak terdokumentasi muncul.

Cobalah, sesuaikan callback dengan kerangka logging Anda, dan saksikan alur kerja dokumen Anda menjadi jauh lebih kuat. Selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}