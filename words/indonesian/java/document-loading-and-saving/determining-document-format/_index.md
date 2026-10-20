---
date: 2026-02-22
description: Pelajari cara mendeteksi format dokumen Java dengan Aspose.Words dan
  secara otomatis memindahkan file berdasarkan format. Identifikasi DOC, DOCX, dan
  lainnya.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Mendeteksi format dokumen Java menggunakan Aspose.Words untuk Java
url: /id/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# mendeteksi format dokumen java menggunakan Aspose.Words untuk Java

Ketika Anda perlu **mendeteksi format dokumen java** dalam sekumpulan file, kemampuan untuk secara otomatis mengelompokkannya ke folder yang tepat dapat menghemat jam kerja manual. Pada tutorial ini kami akan menunjukkan bagaimana Aspose.Words untuk Java memudahkan identifikasi Word, RTF, HTML, ODT, dan banyak format lainnya, lalu **memindahkan file berdasarkan format** ke direktori yang terorganisir.

## Jawaban Cepat
- **Apa arti “detect document format java”?** Ini adalah proses mengidentifikasi secara programatik format pengolah kata sebuah file (DOC, DOCX, RTF, dll.) menggunakan kode Java.  
- **Perpustakaan mana yang menyediakan kemampuan ini?** Aspose.Words untuk Java menyediakan API `FileFormatUtil.detectFileFormat`.  
- **Apakah utilitas ini juga dapat menangani file terenkripsi?** Ya – flag `FileFormatInfo.isEncrypted()` memberi tahu Anda apakah dokumen dilindungi kata sandi.  
- **Apakah saya memerlukan lisensi untuk penggunaan produksi?** Lisensi komersial Aspose.Words diperlukan untuk penerapan non‑evaluasi.  
- **Apakah memungkinkan memindahkan file secara otomatis setelah deteksi?** Tentu – gabungkan hasil deteksi dengan `FileUtils.copyFile` untuk menyortir file ke folder khusus.

## Apa itu detect document format java?
`detect document format java` mengacu pada penggunaan kode Java untuk memeriksa header biner sebuah file dan menentukan format pengolah kata apa yang dimilikinya (mis., DOC, DOCX, ODT). Aspose.Words membaca file tanpa memuat seluruh dokumen, sehingga operasi ini cepat dan hemat memori.

## Mengapa memindahkan file berdasarkan format?
Mengorganisir dokumen berdasarkan format aslinya menyederhanakan proses selanjutnya:

- **Konversi batch** menjadi mudah ketika semua file DOCX berada dalam satu folder.  
- **Dukungan legacy**: Anda dapat memisahkan file Word pra‑97 untuk penanganan khusus.  
- **Keamanan**: Dokumen terenkripsi dapat dikarantina secara otomatis.  

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

- [Aspose.Words untuk Java](https://releases.aspose.com/words/java/) (unduh versi terbaru)  
- Java Development Kit (JDK) 8 atau yang lebih tinggi terpasang  
- Familiaritas dasar dengan I/O Java dan stream  

## Langkah 1: Siapkan direktori untuk setiap format

Pertama kami membuat struktur folder bersih tempat file yang terdeteksi akan dipindahkan. Ini membuat alur kerja rapi dan memudahkan penambahan kategori format baru di kemudian hari.

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

> **Tips pro:** Gunakan path absolut atau konfigurasikan direktori dasar melalui file properti untuk menghindari hard‑coding path dalam kode produksi.

## Langkah 2: Deteksi format dokumen dan pindahkan file

Inti dari **detect document format java** berada dalam loop di bawah ini. Ia memindai setiap file, menentukan tipenya, dan menyalinnya ke folder yang sesuai.

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

Blok `switch` dapat diperluas untuk mencakup semua format yang Anda perlukan. Setiap kasus mencetak pesan ramah lalu memindahkan file ke folder yang cocok.

## Kode sumber lengkap untuk mendeteksi format dokumen java

Berikut contoh lengkap yang siap dijalankan, menggabungkan penyiapan direktori dan logika deteksi. Salin ke kelas Java, sesuaikan path dasar, dan jalankan terhadap folder berisi dokumen campuran.

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

## Masalah umum dan pemecahan masalah

| Masalah | Mengapa terjadi | Cara memperbaiki |
|-------|----------------|------------|
| **`FileFormatUtil.detectFileFormat` mengembalikan `UNKNOWN`** | File rusak atau menggunakan format non‑Word. | Verifikasi ekstensi file, atau tambahkan fallback untuk memindahkannya ke folder *Unknown* (sudah ada dalam contoh). |
| **File terenkripsi menimbulkan pengecualian** | API mencoba membaca konten sebelum memeriksa enkripsi. | Selalu panggil `info.isEncrypted()` sebelum operasi lain pada dokumen. |
| **Pembuatan direktori gagal di Linux** | Izin tidak cukup atau folder induk tidak ada. | Pastikan proses Java memiliki akses tulis dan path dasar sudah ada. |

## Pertanyaan yang Sering Diajukan

**T: Bagaimana cara menginstal Aspose.Words untuk Java?**  
J: Anda dapat mengunduh Aspose.Words untuk Java dari [sini](https://releases.aspose.com/words/java/) dan mengikuti petunjuk instalasi yang disediakan.

**T: Format dokumen apa saja yang didukung untuk deteksi?**  
J: Aspose.Words dapat mendeteksi DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML, serta format pra‑97 yang lebih lama, dan lainnya.

**T: Apakah kode ini dapat menangani dokumen yang diproteksi kata sandi?**  
J: Ya. Flag `FileFormatInfo.isEncrypted()` mengidentifikasi file terenkripsi, memungkinkan Anda memindahkannya ke folder aman tanpa membuka dokumen.

**T: Apakah ada dampak kinerja saat memindai folder besar?**  
J: Deteksi hanya membaca header file, sehingga bahkan ribuan file diproses dengan cepat. Untuk batch sangat besar, pertimbangkan penggunaan parallel streams.

**T: Bagaimana cara memperluas skrip untuk mengonversi format yang tidak didukung?**  
J: Setelah deteksi, Anda dapat memanggil `Document.save` dengan format output yang diinginkan untuk setiap tipe sumber yang didukung.

## Kesimpulan

Dengan menggunakan **detect document format java** bersama Aspose.Words, Anda memperoleh cara andal untuk secara otomatis menyortir, mengarantina, atau mengonversi file terkait Word. Kode contoh menunjukkan cara membuat hierarki folder bersih, mengidentifikasi format tiap file, dan memindahkannya—menghemat waktu dan mengurangi kesalahan manual.

---

**Terakhir Diperbarui:** 2026-02-22  
**Diuji Dengan:** Aspose.Words untuk Java 24.12 (terbaru)  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}