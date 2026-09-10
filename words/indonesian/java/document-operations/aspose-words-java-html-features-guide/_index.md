---
date: '2026-02-06'
description: Pelajari cara memuat HTML VML dengan Aspose.Words untuk Java, mengenkripsi
  file HTML Java, mengatur URI dasar HTML, dan mengonfigurasi opsi kontrol HTML.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: Muat HTML VML menggunakan Aspose.Words untuk Java – Panduan Lengkap
url: /id/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Fitur HTML Komprehensif dengan Aspose.Words untuk Java: Panduan Pengembang

## Pendahuluan

Menavigasi dunia pemrosesan dokumen yang kompleks dapat menjadi menakutkan, terutama saat menangani berbagai fitur HTML. Baik Anda berurusan dengan dukungan Vector Markup Language (VML), dokumen terenkripsi, atau perilaku impor HTML tertentu, **Aspose.Words for Java** menawarkan solusi yang kuat. Dalam panduan ini, Anda akan mempelajari **how to load html vml** secara efisien dan aman, sekaligus mencakup tugas terkait seperti **encrypt html java**, **set html base uri**, dan opsi **configure html control**.

**Apa yang Akan Anda Pelajari:**
- Cara memuat dokumen HTML dengan dukungan VML.
- Teknik menangani HTML halaman tetap dan peringatan.
- Metode mengenkripsi dan memuat dokumen HTML yang dilindungi kata sandi.
- Menggunakan base URI dalam HTML Load Options.
- Mengimpor elemen input HTML sebagai structured document tags atau form fields.
- Mengabaikan elemen `<noscript>` selama pemuatan HTML.
- Mengonfigurasi mode impor blok untuk mengontrol pelestarian struktur HTML.
- Mendukung aturan `@font-face` untuk font yang disesuaikan.

## Jawaban Cepat
- **Apa cara utama untuk mengaktifkan VML saat memuat HTML?** Set `loadOptions.setSupportVml(true)`.
- **Apakah saya dapat memuat file HTML yang dilindungi kata sandi?** Ya, berikan kata sandi ke `HtmlLoadOptions`.
- **Bagaimana cara menyelesaikan jalur gambar relatif?** Gunakan `loadOptions.setBaseUri("your/base/uri")`.
- **Apakah memungkinkan mengimpor `<select>` sebagai form field?** Set `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`.
- **Kelas apa yang menangkap peringatan selama pemuatan?** Implement `IWarningCallback` dan tetapkan ke `loadOptions.setWarningCallback(...)`.

## Prasyarat

Sebelum kita mulai mengimplementasikan berbagai fitur HTML dengan Aspose.Words untuk Java, pastikan lingkungan Anda sudah disiapkan dengan benar:

- **Perpustakaan yang Diperlukan:** Anda memerlukan perpustakaan Aspose.Words versi 25.3 atau lebih baru.
- **Lingkungan Pengembangan:** Panduan ini mengasumsikan Anda menggunakan Maven atau Gradle untuk manajemen dependensi.
- **Basis Pengetahuan:** Pemahaman dasar tentang Java dan familiaritas dengan dokumen HTML akan sangat membantu.

## Menyiapkan Aspose.Words

Untuk mulai bekerja dengan Aspose.Words, pertama-tama Anda perlu menyertakannya dalam proyek Anda. Berikut langkah-langkah menyiapkan perpustakaan menggunakan Maven dan Gradle:

### Maven

Tambahkan dependensi berikut ke file `pom.xml` Anda:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

Sertakan ini dalam file `build.gradle` Anda:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Akuisisi Lisensi

Aspose.Words memerlukan lisensi untuk fungsionalitas penuh. Anda dapat memperoleh percobaan gratis, meminta lisensi sementara, atau membeli lisensi permanen. Kunjungi [halaman pembelian](https://purchase.aspose.com/buy) untuk detail lebih lanjut.

Untuk menginisialisasi Aspose.Words dalam proyek Java Anda, pastikan lisensi telah disiapkan dengan benar:

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## Panduan Implementasi

Kami akan membagi implementasi menjadi beberapa bagian berdasarkan fitur yang ingin kami terapkan.

### Cara memuat html vml dengan Aspose.Words

**Gambaran Umum:**  
Memuat dokumen HTML dengan dukungan VML memungkinkan rendering vektor yang beragam seperti diagram dan bentuk. Ini adalah langkah inti untuk kata kunci utama **load html vml**.

#### Langkah‑per‑Langkah

1. **Siapkan Load Options**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **Muat Dokumen**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **Verifikasi Tipe Gambar**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### Memuat HTML Tetap dan Menangani Peringatan

**Gambaran Umum:**  
Memuat dokumen HTML halaman tetap dapat menghasilkan peringatan yang perlu dikelola untuk pemrosesan yang akurat.

#### Langkah‑per‑Langkah

1. **Definisikan Warning Callback**

```java
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import java.util.ArrayList;

private static class ListDocumentWarnings implements IWarningCallback {
    private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

    public void warning(WarningInfo info) { 
        mWarnings.add(info); 
    }

    public ArrayList<WarningInfo> warnings() { return mWarnings; }
}
```

2. **Konfigurasikan Load Options**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **Muat Dokumen dan Periksa Peringatan**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### Enkripsi Dokumen HTML

**Gambaran Umum:**  
Mengenkripsi dokumen HTML dengan kata sandi memastikan akses yang aman, yang penting untuk informasi sensitif—ini menangani skenario **encrypt html java**.

#### Langkah‑per‑Langkah

1. **Siapkan Opsi Tanda Tangan Digital**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;

CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
SignOptions signOptions = new SignOptions();
signOptions.setComments("Comment");
signOptions.setSignTime(new Date());
signOptions.setDecryptionPassword("docPassword");
```

2. **Tandatangani dan Enkripsi Dokumen**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **Muat Dokumen yang Dienkripsi**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### Base URI untuk HTML Load Options

**Gambaran Umum:**  
Menentukan **set html base uri** membantu menyelesaikan URI relatif, terutama saat menangani gambar atau sumber daya tertaut lainnya.

#### Langkah‑per‑Langkah

1. **Konfigurasikan Load Options dengan Base URI**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **Muat Dokumen dan Verifikasi Gambar**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### Impor HTML Select sebagai Structured Document Tag

**Gambaran Umum:**  
Untuk mengatur perilaku **configure html control**, Anda dapat mengimpor elemen `<select>` sebagai Structured Document Tags, memberi Anda kontrol lebih halus atas form field di dalam dokumen Word.

#### Langkah‑per‑Langkah

1. **Setel Tipe Kontrol yang Diinginkan**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **Muat Dokumen dan Verifikasi Struktur**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.StructuredDocumentTag;

Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (!sdt.getTagName().equals("Select")) {
    throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
}
```

## Masalah Umum dan Solusinya

| Masalah | Alasan | Solusi |
|-------|--------|-----|
| Grafik VML tidak muncul | `supportVml` flag dibiarkan default (`false`) | Pastikan `loadOptions.setSupportVml(true)` sebelum memuat. |
| Gambar tidak muncul setelah dimuat | Jalur relatif tidak dapat diselesaikan | Gunakan **set html base uri** (`loadOptions.setBaseUri(...)`) untuk mengarahkan ke folder yang tepat. |
| HTML yang dilindungi kata sandi menghasilkan pengecualian | Kata sandi tidak diberikan | Berikan kata sandi ke `new HtmlLoadOptions("yourPassword")`. |
| Kontrol form muncul sebagai teks biasa | `HtmlControlType` salah | Set `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` atau `FormField` sesuai kebutuhan. |
| Peringatan tak terduga | Elemen HTML tidak ditangani | Implementasikan `IWarningCallback` untuk menangkap dan meninjau peringatan. |

## Pertanyaan yang Sering Diajukan

**T: Bisakah saya memuat file HTML yang berisi VML dan grafik SVG modern?**  
J: Ya. Aktifkan VML dengan `setSupportVml(true)`; SVG ditangani secara otomatis oleh Aspose.Words.

**T: Bagaimana cara mengenkripsi dokumen HTML tanpa menggunakan sertifikat digital?**  
J: Gunakan konstruktor `HtmlLoadOptions` yang menerima kata sandi dan simpan dokumen dengan `Document.save(..., SaveFormat.HTML)` setelah menetapkan kata sandi.

**T: Apa yang terjadi jika base URI mengarah ke folder yang tidak ada?**  
J: Aspose.Words akan melempar `FileNotFoundException` untuk sumber daya yang hilang. Verifikasi jalur sebelum memuat.

**T: Apakah memungkinkan mengubah tipe kontrol default untuk semua elemen form HTML?**  
J: Ya. Gunakan `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` untuk menerapkannya secara global.

**T: Apakah warning callback bersifat thread‑safe?**  
J: Implementasi callback harus thread‑safe jika Anda berencana memuat dokumen secara bersamaan. Gunakan koleksi yang disinkronkan atau penyimpanan thread‑local.

---

**Terakhir Diperbarui:** 2026-02-06  
**Diuji Dengan:** Aspose.Words for Java 25.3  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}