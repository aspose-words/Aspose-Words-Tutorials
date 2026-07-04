---
category: general
date: 2026-04-24
description: Pelajari cara menyimpan dokumen Word menggunakan Aspose.Words sambil
  mengatur pengaturan font dan menangani font yang hilang dengan kode Java yang mudah
  diikuti.
draft: false
keywords:
- save word document
- set font settings
- how to set font settings
- aspose words font substitution
- handle missing fonts
language: id
og_description: Simpan dokumen Word dengan Aspose.Words sambil mengatur pengaturan
  font dan menangani font yang hilang. Panduan Java lengkap untuk pengembang.
og_title: Simpan Dokumen Word – Atur Pengaturan Font, Tangani Font yang Hilang
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Simpan Dokumen Word – Atur Pengaturan Font, Tangani Font yang Hilang
url: /id/java/document-loading-and-saving/save-word-document-set-font-settings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan Dokumen Word – Atur Pengaturan Font, Tangani Font yang Hilang

Pernahkah Anda perlu **save Word document** tetapi file sumber menggunakan font yang tidak ada di server Anda? Ini adalah masalah umum yang dapat mengubah alur otomatisasi yang mulus menjadi sakit kepala.  

Kabar baik? Dengan Aspose.Words Anda dapat **set font settings** secara langsung, menangkap peringatan font yang hilang, dan tetap menghasilkan dokumen Word yang tersimpan dengan sempurna. Dalam tutorial ini kami akan membahas contoh Java lengkap yang menunjukkan **how to set font settings**, menangani peringatan *font substitution* yang menakutkan, dan akhirnya **save Word document** tanpa kejutan.

## Apa yang Akan Anda Pelajari

- Cara mengkonfigurasi `LoadOptions` dengan objek `FontSettings` khusus.  
- Cara mendaftarkan callback peringatan yang melaporkan **aspose words font substitution** events.  
- Cara memuat DOCX, membiarkan Aspose menggantikan font yang hilang, dan **save Word document** ke lokasi baru.  
- Tips untuk menangani kasus tepi seperti file terenkripsi atau dokumen dengan font tersemat.  

Tidak diperlukan perpustakaan tambahan selain Aspose.Words, dan kode ini bekerja dengan rilis terbaru 24.x (per April 2026).  

---

![Diagram yang menggambarkan alur kerja menyimpan dokumen Word dengan pengaturan font dan callback peringatan](font-workflow.png "Diagram yang menunjukkan alur kerja menyimpan dokumen Word")

## Simpan Dokumen Word dengan Pengaturan Font Kustom

Langkah pertama adalah memberi tahu Aspose.Words apa yang harus dilakukan ketika tidak dapat menemukan font yang direferensikan oleh dokumen sumber. Di sinilah **set font settings** berperan.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 1: Prepare LoadOptions with a fresh FontSettings instance.
        // -----------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        // By default FontSettings uses system fonts, but we can add folders later.
        loadOptions.setFontSettings(new FontSettings());

        // -----------------------------------------------------------------
        // Step 2: Register a warning callback to catch FONT_SUBSTITUTION alerts.
        // -----------------------------------------------------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about missing‑font warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // -----------------------------------------------------------------
        // Step 3: Load the source document using the configured options.
        // -----------------------------------------------------------------
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // -----------------------------------------------------------------
        // Step 4: Save the processed document – fonts have been substituted.
        // -----------------------------------------------------------------
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Mengapa ini berhasil:**  
- `LoadOptions` memberi tahu Aspose.Words untuk menggunakan `FontSettings` yang disediakan saat mem-parsing file.  
- `IWarningCallback` mencegat setiap pesan **aspose words font substitution**, memberikan Anda log langsung tentang font mana yang hilang.  
- Saat Anda memanggil `document.save(...)`, Aspose secara otomatis menggantikan font yang hilang dengan yang paling cocok dari sistem atau folder yang Anda tambahkan ke `FontSettings`.

### Hasil yang Diharapkan

Menjalankan program mencetak baris seperti:

```
Font substitution: Font 'Calibri' was not found. Substituted with 'Arial'.
Font substitution: Font 'Cambria' was not found. Substituted with 'Times New Roman'.
```

Dan Anda akan mendapatkan `output.docx` yang terlihat persis seperti aslinya—kecuali font yang hilang telah diganti, dan file tersebut berhasil **saved word document** di disk.

## Cara Mengatur Pengaturan Font di Aspose.Words

Jika Anda memerlukan kontrol lebih—misalnya ingin mengarahkan Aspose ke folder font kustom atau menyematkan font cadangan—cukup sesuaikan objek `FontSettings` sebelum menetapkannya ke `LoadOptions`.

```java
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder that contains your private fonts.
fontSettings.setFontsFolder("C:/MyCustomFonts", true);

// Optionally, set a default substitution font (e.g., "Arial").
fontSettings.setDefaultFontName("Arial");

// Attach the configured FontSettings to LoadOptions.
loadOptions.setFontSettings(fontSettings);
```

**Kapan menggunakan ini:**  
- Aplikasi Anda berjalan di kontainer yang hanya menyertakan set minimal font sistem.  
- Anda memiliki font merek perusahaan yang berada di share jaringan yang aman.  
- Anda ingin memastikan bahwa fallback tertentu (seperti “Arial”) selalu digunakan, menghindari substitusi yang tidak terduga.

## Menangani Font yang Hilang – Callback Substitusi Font

Callback peringatan yang kami daftarkan sebelumnya adalah inti dari logika **handle missing fonts**. Anda dapat memperluasnya menjadi:

1. **Collect warnings** ke dalam daftar untuk pelaporan nanti.  
2. **Throw an exception** jika font kritis hilang (mis., font logo).  
3. **Log to a monitoring system** (Splunk, ELK, dll.) untuk jejak audit.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    private final List<String> missingFonts = new ArrayList<>();

    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String msg = "Missing font: " + info.getDescription();
            System.out.println(msg);
            missingFonts.add(msg);
        }
    }

    // Helper to retrieve all missing‑font messages after loading.
    public List<String> getMissingFonts() {
        return missingFonts;
    }
});
```

**Pro tip:** Jika Anda perlu menghentikan operasi ketika font tertentu tidak ada, bandingkan `info.getDescription()` dengan whitelist dan lempar `RuntimeException` ketika tidak cocok.

## Contoh Java Lengkap – Dari Awal hingga Selesai

Menggabungkan semuanya, berikut program mandiri yang dapat Anda salin‑tempel ke IDE Anda. Pastikan Anda memiliki Aspose.Words for Java JAR di classpath.

```java
import com.aspose.words.*;
import java.util.*;

public class SaveWordWithFontHandling {
    public static void main(String[] args) throws Exception {
        // ------------------- Configure FontSettings -------------------
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains any custom fonts you might need.
        fontSettings.setFontsFolder("C:/CustomFonts", true);
        // Ensure a safe fallback.
        fontSettings.setDefaultFontName("Arial");

        // ------------------- Prepare LoadOptions -------------------
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setFontSettings(fontSettings);

        // ------------------- Warning callback (handle missing fonts) -------------------
        loadOptions.setWarningCallback(new IWarningCallback() {
            private final List<String> missing = new ArrayList<>();

            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBstitution) {
                    String msg = "Font substitution: " + info.getDescription();
                    System.out.println(msg);
                    missing.add(msg);
                }
            }

            public List<String> getMissing() {
                return missing;
            }
        });

        // ------------------- Load the source DOCX -------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ------------------- Save the result -------------------
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Run the program, watch the console for any **font

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}