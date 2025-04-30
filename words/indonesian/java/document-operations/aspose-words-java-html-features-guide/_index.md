---
"date": "2025-03-28"
"description": "Pelajari cara memanfaatkan Aspose.Words untuk Java untuk menguasai pemrosesan dokumen, termasuk dukungan VML, enkripsi, opsi impor HTML, dan banyak lagi."
"title": "Panduan Lengkap Fitur HTML dan Penanganan Dokumen Aspose.Words untuk Java"
"url": "/id/java/document-operations/aspose-words-java-html-features-guide/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Fitur HTML Komprehensif dengan Aspose.Words untuk Java: Panduan Pengembang

## Perkenalan

Menjelajahi dunia pemrosesan dokumen yang rumit bisa jadi menakutkan, terutama saat menangani berbagai fitur HTML. Baik Anda berurusan dengan dukungan Vector Markup Language (VML), dokumen terenkripsi, atau perilaku impor HTML tertentu, **Aspose.Words untuk Java** menawarkan solusi yang tangguh. Dalam panduan ini, kami akan membahas cara menerapkan fungsi-fungsi ini dengan lancar menggunakan Aspose.Words, yang akan meningkatkan kemampuan pemrosesan dokumen Anda.

**Apa yang Akan Anda Pelajari:**
- Cara memuat dokumen HTML dengan dukungan VML.
- Teknik untuk menangani HTML halaman tetap dan peringatan.
- Metode untuk mengenkripsi dan memuat dokumen HTML yang dilindungi kata sandi.
- Memanfaatkan URI dasar dalam Opsi Muat HTML.
- Mengimpor elemen input HTML sebagai tag dokumen terstruktur atau bidang formulir.
- Mengabaikan `<noscript>` elemen selama pemuatan HTML.
- Mengonfigurasi mode impor blok untuk mengendalikan pelestarian struktur HTML.
- Mendukung `@font-face` aturan untuk font yang disesuaikan.

Dengan wawasan ini, Anda akan siap untuk menangani berbagai tugas pemrosesan HTML. Mari kita bahas prasyarat dan pengaturannya terlebih dahulu!

## Prasyarat

Sebelum kita mulai mengimplementasikan berbagai fitur HTML dengan Aspose.Words untuk Java, pastikan lingkungan Anda telah disiapkan dengan benar:

- **Pustaka yang dibutuhkan:** Anda memerlukan pustaka Aspose.Words versi 25.3 atau yang lebih baru.
- **Lingkungan Pengembangan:** Panduan ini mengasumsikan Anda menggunakan Maven atau Gradle untuk manajemen ketergantungan.
- **Basis Pengetahuan:** Pemahaman dasar tentang Java dan keakraban dengan dokumen HTML akan bermanfaat.

## Menyiapkan Aspose.Words

Untuk mulai bekerja dengan Aspose.Words, pertama-tama Anda perlu memasukkannya ke dalam proyek Anda. Berikut adalah langkah-langkah untuk menyiapkan pustaka menggunakan Maven dan Gradle:

### Pakar

Tambahkan dependensi berikut ke `pom.xml` mengajukan:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Bahasa Inggris Gradle

Sertakan ini di dalam `build.gradle` mengajukan:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Akuisisi Lisensi

Aspose.Words memerlukan lisensi untuk fungsionalitas penuh. Anda dapat memperoleh uji coba gratis, meminta lisensi sementara, atau membeli lisensi permanen. Kunjungi [halaman pembelian](https://purchase.aspose.com/buy) untuk lebih jelasnya.

Untuk menginisialisasi Aspose.Words di proyek Java Anda, pastikan Anda telah mengatur lisensi dengan benar:

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

### Mendukung VML dalam Dokumen HTML

**Ringkasan:**
Memuat dokumen HTML dengan atau tanpa dukungan VML memungkinkan rendering grafis vektor yang serbaguna. Fitur ini penting saat menangani dokumen yang menyertakan elemen grafis seperti bagan dan bentuk.

#### Implementasi Langkah demi Langkah:

1. **Siapkan Opsi Muatan**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.HtmlLoadOptions;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   loadOptions.setSupportVml(true); // Aktifkan dukungan VML
   ```

2. **Muat Dokumen**
   
   ```java
   Document doc = new Document("path/to/VML conditional.htm", loadOptions);
   ```

3. **Verifikasi Jenis Gambar**
   
   Pastikan jenis gambar sesuai dengan harapan Anda:
   
   ```java
   import com.aspose.words.NodeType;
   import com.aspose.words.Shape;

   Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
   String expectedImageType = "JPG"; // Sesuaikan berdasarkan logika aktual

   if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
       throw new AssertionError("Unexpected image type loaded.");
   }
   ```

### Muat HTML Tetap dan Tangani Peringatan

**Ringkasan:**
Memuat dokumen HTML halaman tetap dapat menghasilkan peringatan yang perlu dikelola untuk pemrosesan yang akurat.

#### Implementasi Langkah demi Langkah:

1. **Definisikan Panggilan Balik Peringatan**
   
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

2. **Konfigurasikan Opsi Muatan**
   
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

**Ringkasan:**
Mengenkripsi dokumen HTML dengan kata sandi memastikan akses aman, yang penting untuk informasi sensitif.

#### Implementasi Langkah demi Langkah:

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

3. **Muat Dokumen Terenkripsi**
   
   ```java
   import com.aspose.words.Document;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
   Document doc = new Document(outputFileName, loadOptions);

   if (!doc.getText().trim().equals("Test encrypted document.")) {
       throw new AssertionError("Unexpected document text.");
   }
   ```

### URI Dasar untuk Opsi Pemuatan HTML

**Ringkasan:**
Menentukan URI dasar membantu menyelesaikan URI relatif, terutama saat menangani gambar atau sumber daya tertaut lainnya.

#### Implementasi Langkah demi Langkah:

1. **Konfigurasikan Opsi Muat dengan URI Dasar**
   
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

### Impor HTML Pilih sebagai Tag Dokumen Terstruktur

**Ringkasan:**
Pengimporan `<select>` elemen sebagai tag dokumen terstruktur memungkinkan kontrol dan pemformatan yang lebih baik dalam dokumen Word.

#### Implementasi Langkah demi Langkah:

1. **Tetapkan Jenis Kontrol Pilihan**
   
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

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}