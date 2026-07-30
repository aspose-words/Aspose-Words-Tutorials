---
date: 2025-12-20
description: Pelajari cara mengatur file berdasarkan tipe dan mendeteksi format dokumen
  di Java dengan Aspose.Words. Mendukung DOC, DOCX, RTF, dan lainnya.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Mengatur File Berdasarkan Tipe Menggunakan Aspose.Words untuk Java
url: /id/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mengatur File Berdasarkan Tipe Menggunakan Aspose.Words untuk Java

Saat Anda perlu **mengatur file berdasarkan tipe** dalam aplikasi Java, langkah pertama adalah secara andal menentukan format setiap dokumen. Aspose.Words untuk Java mempermudah hal ini, memungkinkan Anda mendeteksi DOC, DOCX, RTF, HTML, ODT, dan banyak format lainnya – bahkan file yang terenkripsi atau tidak dikenal. Dalam panduan ini kami akan menjelaskan cara menyiapkan folder, mendeteksi format file, dan secara otomatis menyortir file Anda.

## Jawaban Cepat
- **Apa arti “mengatur file berdasarkan tipe”?** Artinya secara otomatis memindahkan dokumen ke dalam folder berdasarkan format yang terdeteksi (misalnya, DOCX, PDF, RTF).  
- **Perpustakaan mana yang membantu mendeteksi format file di Java?** Aspose.Words untuk Java menyediakan `FileFormatUtil.detectFileFormat()`.  
- **Apakah API dapat mengidentifikasi tipe file yang tidak dikenal?** Ya – API mengembalikan `LoadFormat.UNKNOWN` untuk file yang tidak didukung atau tidak dapat dikenali.  
- **Apakah deteksi dokumen terenkripsi didukung?** Tentu; flag `FileFormatInfo.isEncrypted()` memberi tahu Anda jika file dilindungi kata sandi.  
- **Apakah saya memerlukan lisensi untuk penggunaan produksi?** Lisensi Aspose.Words yang valid diperlukan untuk penyebaran komersial.

## Pendahuluan: Mengatur File Berdasarkan Tipe dengan Aspose.Words untuk Java

Saat bekerja dengan pemrosesan dokumen di Java, sangat penting untuk menentukan format file yang Anda tangani. Aspose.Words untuk Java menyediakan fitur kuat untuk **detect file format java**, dan kami akan memandu Anda melalui proses mengatur file secara efisien.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) terpasang di sistem Anda
- Pengetahuan dasar tentang pemrograman Java

## Langkah 1: Penyiapan Direktori

Pertama, kita perlu menyiapkan direktori yang diperlukan untuk mengatur file kita secara efektif. Kami akan membuat direktori untuk berbagai tipe dokumen.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Kami telah membuat direktori untuk tipe dokumen yang didukung, tidak dikenal, terenkripsi, dan pra‑97.

## Langkah 2: Mendeteksi Format Dokumen

Sekarang, mari kita deteksi format dokumen di dalam direktori kita. Kami akan menggunakan Aspose.Words untuk Java untuk mencapainya.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

Dalam potongan kode ini kami mengiterasi file, **detect file format java**, dan mengatur mereka ke folder yang sesuai.

## Kode Sumber Lengkap untuk Menentukan Format Dokumen di Aspose.Words untuk Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Display the document type
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## Cara Mendeteksi Format File Java

Metode `FileFormatUtil.detectFileFormat()` memeriksa header file dan mengembalikan objek `FileFormatInfo`. Objek ini memberi tahu Anda **load format**, apakah file terenkripsi, dan metadata berguna lainnya. Dengan informasi ini Anda dapat secara programatis **identify unknown file types** dan memutuskan cara memproses masing‑masing.

## Mengidentifikasi Tipe File yang Tidak Dikenal

Ketika API mengembalikan `LoadFormat.UNKNOWN`, file tersebut mungkin rusak atau menggunakan format yang tidak didukung oleh Aspose.Words. Dalam contoh kode kami, file‑file tersebut dipindahkan ke folder **Unknown** sehingga Anda dapat meninjaunya nanti.

## Masalah Umum dan Solusinya

| Issue | Reason | Fix |
|-------|--------|-----|
| File selalu ditempatkan di folder *Supported* | `FileFormatUtil` tidak dapat membaca header (misalnya, file kosong) | Pastikan Anda memberikan jalur file yang benar dan file tidak berukuran nol byte. |
| File terenkripsi menghasilkan pengecualian | Mencoba membaca tanpa menangani enkripsi | Gunakan pemeriksaan `info.isEncrypted()` sebelum pemrosesan lebih lanjut, seperti yang ditunjukkan dalam kode. |
| Dokumen Word pra‑97 tidak terdeteksi | Format lama memerlukan kasus `DOC_PRE_WORD_60` | Pertahankan blok `case LoadFormat.DOC_PRE_WORD_60` untuk mengarahkan mereka ke folder *Pre97*. |

## Pertanyaan yang Sering Diajukan

### Bagaimana cara menginstal Aspose.Words untuk Java?

Anda dapat mengunduh Aspose.Words untuk Java dari [sini](https://releases.aspose.com/words/java/) dan mengikuti petunjuk instalasi yang disediakan.

### Apa saja format dokumen yang didukung?

Aspose.Words untuk Java mendukung berbagai format dokumen, termasuk DOC, DOCX, RTF, HTML, ODT, dan lainnya. Lihat dokumentasi resmi untuk daftar lengkap.

### Bagaimana cara mendeteksi dokumen terenkripsi menggunakan Aspose.Words untuk Java?

Gunakan metode `FileFormatUtil.detectFileFormat()`; flag `FileFormatInfo.isEncrypted()` yang dikembalikan menunjukkan enkripsi, seperti yang ditunjukkan dalam panduan ini.

### Apakah ada batasan saat bekerja dengan format dokumen lama?

Format lama seperti MS Word 6 atau Word 95 mungkin tidak memiliki fitur modern dan dapat mengalami masalah kompatibilitas. Pertimbangkan untuk mengonversinya ke format yang lebih baru bila memungkinkan.

### Bisakah saya mengotomatisasi deteksi format dokumen dalam aplikasi Java saya?

Ya, sisipkan kode yang disediakan ke dalam pipeline pemrosesan aplikasi Anda. Ini memungkinkan penyortiran dan penanganan otomatis berdasarkan format yang terdeteksi.

**Last Updated:** 2025-12-20  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}