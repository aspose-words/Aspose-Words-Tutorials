---
"date": "2025-03-28"
"description": "Pelajari cara mengotomatiskan penandatanganan dokumen menggunakan Aspose.Words untuk Java. Tutorial ini mencakup pengaturan lingkungan, pembuatan data uji, penambahan baris tanda tangan, dan penandatanganan dokumen secara digital."
"title": "Otomatiskan Penandatanganan Dokumen di Java dengan Aspose.Words&#58; Panduan Lengkap"
"url": "/id/java/mail-merge-reporting/aspose-words-java-document-signing-tutorial/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Otomatiskan Penandatanganan Dokumen di Java dengan Aspose.Words: Panduan Lengkap

## Perkenalan

Dalam dunia bisnis yang serba cepat saat ini, manajemen dokumen yang efisien sangatlah penting. Mengotomatiskan pembuatan dan penandatanganan dokumen secara digital dapat menghemat waktu dan meminimalkan kesalahan. Tutorial ini akan memandu Anda menggunakan Aspose.Words untuk Java guna membuat data uji bagi para penanda tangan, menambahkan baris tanda tangan, dan menandatangani dokumen secara digital.

**Apa yang Akan Anda Pelajari:**
- Menyiapkan Aspose.Words dalam proyek Java
- Membuat data penanda tangan uji dengan Java
- Menambahkan baris tanda tangan ke dokumen Word
- Menandatangani dokumen secara digital menggunakan sertifikat digital

Mari mulai dengan mempersiapkan lingkungan pengembangan Anda!

## Prasyarat

Sebelum memulai tutorial, pastikan pengaturan Anda memenuhi persyaratan berikut:

- **Kit Pengembangan Java (JDK):** Versi 8 atau lebih tinggi.
- **Lingkungan Pengembangan Terpadu (IDE):** Seperti IntelliJ IDEA atau Eclipse.
- **Aspose.Words untuk Java:** Pustaka ini dapat disertakan melalui Maven atau Gradle.

### Prasyarat Pengetahuan

Pemahaman dasar tentang pemrograman Java dan keakraban dalam menangani file dan aliran akan bermanfaat. Jika Anda baru mengenal Aspose, jangan khawatir—kami akan membahas hal-hal penting.

## Menyiapkan Aspose.Words

Untuk menggunakan Aspose.Words untuk Java di proyek Anda, ikuti langkah-langkah berikut:

### Ketergantungan Maven

Tambahkan dependensi berikut ke `pom.xml` mengajukan:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Ketergantungan Gradle

Untuk proyek Gradle, sertakan baris ini di `build.gradle` mengajukan:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Akuisisi Lisensi

Aspose menawarkan berbagai pilihan lisensi:

- **Uji Coba Gratis:** Unduh versi uji coba gratis untuk menguji fitur-fiturnya.
- **Lisensi Sementara:** Dapatkan lisensi sementara untuk tujuan evaluasi.
- **Pembelian:** Untuk akses penuh, beli lisensi dari situs web Aspose.

Pastikan proyek Anda dikonfigurasi dengan dependensi yang diperlukan dan lisensi yang dibutuhkan. Pengaturan ini akan memungkinkan Anda memanfaatkan kemampuan manipulasi dokumen Aspose yang canggih dengan mudah.

## Panduan Implementasi

Kami akan membahas setiap fitur langkah demi langkah, dimulai dengan membuat data penanda tangan uji.

### Fitur 1: Membuat Data Uji untuk Penandatangan

#### Ringkasan

Fitur ini menghasilkan daftar penanda tangan dengan ID, nama, posisi, dan gambar yang unik. Fitur ini penting untuk menguji skenario penandatanganan dokumen tanpa menggunakan data sebenarnya.

##### Langkah 1: Siapkan Kelas Java Anda

Buat kelas bernama `SignPersonCreator` dan mengimpor pustaka yang diperlukan:

```java
import java.io.ByteArrayOutputStream;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.UUID;

class DocumentHelper {
    public static byte[] getBytesFromStream(InputStream inputStream) throws IOException {
        int numRead; 
        byte[] buffer = new byte[1024]; 
        ByteArrayOutputStream baos = new ByteArrayOutputStream();

        while ((numRead = inputStream.read(buffer)) != -1) {
            baos.write(buffer, 0, numRead);
        }
        return baos.toByteArray();
    }
}

public class SignPersonCreator {
    private static ArrayList<SignPersonTestClass> gSignPersonList;

    public static void main(String[] args) throws IOException {
        createSignPersonData();
        System.out.println("Test data successfully added!");
    }

    private static void createSignPersonData() throws IOException {
        InputStream inputStream = new FileInputStream(YOUR_DOCUMENT_DIRECTORY + "Logo.jpg");

        gSignPersonList = new ArrayList<>();
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Ron Williams", "Chief Executive Officer",
                DocumentHelper.getBytesFromStream(inputStream)));
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Stephen Morse", "Head of Compliance",
                DocumentHelper.getBytesFromStream(inputStream)));
    }
}
```

##### Penjelasan

- **UUID:** Menghasilkan pengenal unik untuk setiap penanda tangan.
- **dapatkanBytesFromStream:** Mengonversi berkas gambar menjadi array byte untuk penyimpanan.

### Fitur 2: Tambahkan Baris Tanda Tangan ke Dokumen

#### Ringkasan

Fitur ini menambahkan baris tanda tangan ke dokumen Anda, mengaitkannya dengan rincian penanda tangan.

##### Langkah 1: Buat Kelas SignatureLineAdder

Terapkan `SignatureLineAdder` kelas sebagai berikut:

```java
import com.aspose.words.*;

class SignatureLineAdder {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        
        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            addSignatureLine(srcDocumentPath, dstDocumentPath, signPersonInfo);
            System.out.println("Signature line added successfully!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void addSignatureLine(final String srcDocumentPath, final String dstDocumentPath,
                                         final SignPersonTestClass signPersonInfo) throws Exception {
        Document document = new Document(srcDocumentPath);
        DocumentBuilder builder = new DocumentBuilder(document);

        SignatureLineOptions signatureLineOptions = new SignatureLineOptions();
        signatureLineOptions.setSigner(signPersonInfo.getName());
        signatureLineOptions.setSignerTitle(signPersonInfo.getPosition());

        SignatureLine signatureLine = builder.insertSignatureLine(signatureLineOptions).getSignatureLine();
        signatureLine.setId(String.valueOf(signPersonInfo.getPersonId()));

        builder.getDocument().save(dstDocumentPath);
    }
}
```

##### Penjelasan

- **Opsi Garis Tanda Tangan:** Mengonfigurasi nama dan jabatan penanda tangan.
- **masukkanSignatureLine:** Menyisipkan baris tanda tangan ke dalam dokumen pada posisi kursor saat ini.

### Fitur 3: Menandatangani Dokumen dengan Sertifikat Digital

#### Ringkasan

Fitur ini menandatangani dokumen secara digital menggunakan sertifikat digital, memastikan keaslian dan integritas.

##### Langkah 1: Buat Kelas DocumentSigner

Terapkan `DocumentSigner` kelas:

```java
import com.aspose.words.*;

class DocumentSigner {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        String certificatePath = YOUR_DOCUMENT_DIRECTORY + "morzal.pfx";
        String certificatePassword = "aw";

        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            signDocument(srcDocumentPath, dstDocumentPath, signPersonInfo, certificatePath, certificatePassword);
            System.out.println("Document successfully signed!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void signDocument(final String srcDocumentPath, final String dstDocumentPath,
                                     final SignPersonTestClass signPersonInfo, final String certificatePath,
                                     final String certificatePassword) throws Exception {
        Document document = new Document(dstDocumentPath);

        CertificateHolder certificateHolder = CertificateHolder.create(certificatePath, certificatePassword);

        SignOptions signOptions = new SignOptions();
        signOptions.setSignatureLineId(String.valueOf(
            signPersonInfo.getPersonId()));

        document.sign(signOptions, certificateHolder);
    }
}
```

##### Penjelasan

- **Pemegang Sertifikat:** Mewakili sertifikat digital yang digunakan untuk penandatanganan.
- **tanda:** Metode yang menandatangani dokumen dengan opsi dan sertifikat yang ditentukan.

## Kesimpulan

Dalam tutorial ini, Anda telah mempelajari cara mengotomatiskan pembuatan dan penandatanganan dokumen di Java menggunakan Aspose.Words. Dengan mengikuti langkah-langkah ini, Anda dapat menyederhanakan proses pengelolaan dokumen, meningkatkan keamanan, dan memastikan integritas data. Untuk eksplorasi lebih lanjut, pertimbangkan untuk mempelajari fitur-fitur Aspose.Words yang lebih canggih.

**Langkah Berikutnya:**
- Jelajahi fitur Aspose.Words tambahan seperti gabungan surat atau pembuatan laporan.
- Lihat dokumentasi Aspose untuk panduan terperinci dan referensi API.
- Bereksperimenlah dengan berbagai format dokumen yang didukung oleh Aspose.Words.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}