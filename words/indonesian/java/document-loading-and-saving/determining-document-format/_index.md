---
title: Menentukan Format Dokumen di Aspose.Words untuk Java
linktitle: Menentukan Format Dokumen
second_title: API Pemrosesan Dokumen Java Aspose.Words
description: Pelajari cara mendeteksi format dokumen di Java dengan Aspose.Words. Identifikasi DOC, DOCX, dan lainnya. Atur file secara efisien.
weight: 25
url: /id/java/document-loading-and-saving/determining-document-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menentukan Format Dokumen di Aspose.Words untuk Java


## Pengantar Penentuan Format Dokumen di Aspose.Words untuk Java

Saat bekerja dengan pemrosesan dokumen di Java, sangat penting untuk menentukan format file yang Anda tangani. Aspose.Words untuk Java menyediakan fitur-fitur canggih untuk mengidentifikasi format dokumen, dan kami akan memandu Anda melalui prosesnya.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:

- [Aspose.Words untuk Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) terinstal di sistem Anda
- Pengetahuan dasar tentang pemrograman Java

## Langkah 1: Pengaturan Direktori

Pertama, kita perlu menyiapkan direktori yang diperlukan untuk mengatur berkas-berkas kita secara efektif. Kita akan membuat direktori untuk berbagai jenis dokumen.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Buat direktori jika belum ada.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Kami telah membuat direktori untuk jenis dokumen yang didukung, tidak dikenal, terenkripsi, dan pra-97.

## Langkah 2: Mendeteksi Format Dokumen

Sekarang, mari kita deteksi format dokumen dalam direktori kita. Kita akan menggunakan Aspose.Words untuk Java untuk mencapainya.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Menampilkan jenis dokumen
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Tambahkan kasus untuk format dokumen lain sesuai kebutuhan
    }

    // Menangani dokumen terenkripsi
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Menangani jenis dokumen lainnya
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

Dalam potongan kode ini, kami menelusuri file-file, mendeteksi formatnya, dan mengaturnya ke dalam direktori masing-masing.

## Source Code Lengkap Untuk Menentukan Format Dokumen di Aspose.Words untuk Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Buat direktori jika belum ada.
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
            // Menampilkan jenis dokumen
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

## Kesimpulan

Menentukan format dokumen di Aspose.Words untuk Java sangat penting untuk pemrosesan dokumen yang efisien. Dengan langkah-langkah yang diuraikan dalam panduan ini, Anda dapat mengidentifikasi jenis dokumen dan menanganinya dengan tepat dalam aplikasi Java Anda.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara menginstal Aspose.Words untuk Java?

 Anda dapat mengunduh Aspose.Words untuk Java dari[Di Sini](https://releases.aspose.com/words/java/)dan ikuti petunjuk instalasi yang disediakan.

### Apa saja format dokumen yang didukung?

Aspose.Words untuk Java mendukung berbagai format dokumen, termasuk DOC, DOCX, RTF, HTML, dan banyak lagi. Anda dapat merujuk ke dokumentasi untuk daftar lengkapnya.

### Bagaimana cara mendeteksi dokumen terenkripsi menggunakan Aspose.Words untuk Java?

 Anda dapat menggunakan`FileFormatUtil.detectFileFormat()` metode untuk mendeteksi dokumen terenkripsi, seperti yang ditunjukkan dalam panduan ini.

### Apakah ada batasan saat bekerja dengan format dokumen lama?

Format dokumen lama, seperti MS Word 6 atau Word 95, mungkin memiliki keterbatasan dalam hal fitur dan kompatibilitas dengan aplikasi modern. Pertimbangkan untuk memutakhirkan atau mengonversi dokumen ini bila perlu.

### Bisakah saya mengotomatiskan deteksi format dokumen di aplikasi Java saya?

Ya, Anda dapat mengotomatiskan deteksi format dokumen dengan mengintegrasikan kode yang diberikan ke dalam aplikasi Java Anda. Ini memungkinkan Anda untuk memproses dokumen berdasarkan format yang terdeteksi.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
