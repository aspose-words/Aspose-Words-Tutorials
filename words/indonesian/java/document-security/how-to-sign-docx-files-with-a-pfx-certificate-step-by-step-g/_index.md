---
category: general
date: 2026-08-14
description: Pelajari cara menandatangani file docx menggunakan sertifikat PFX. Tutorial
  ini mencakup pengaturan PFX untuk menandatangani dokumen, opsi XAdES‑EPES, dan kode
  Java lengkap.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign docx
- sign document pfx
language: id
lastmod: 2026-08-14
og_description: Cara menandatangani file docx menggunakan sertifikat PFX. Ikuti panduan
  ini untuk menyiapkan penandatanganan dokumen PFX, menerapkan XAdES‑EPES, dan menghasilkan
  DOCX yang ditandatangani dengan Java.
og_image_alt: Screenshot showing how to sign docx with a PFX certificate in Java
og_title: Cara menandatangani file docx dengan sertifikat PFX – panduan lengkap
schemas:
- author: GroupDocs
  dateModified: '2026-08-14'
  description: Learn how to sign docx files using a PFX certificate. This tutorial
    covers sign document pfx setup, XAdES‑EPES options, and full Java code.
  headline: How to sign docx files with a PFX certificate – step‑by‑step guide
  type: TechArticle
- description: Learn how to sign docx files using a PFX certificate. This tutorial
    covers sign document pfx setup, XAdES‑EPES options, and full Java code.
  name: How to sign docx files with a PFX certificate – step‑by‑step guide
  steps:
  - name: Load the PFX certificate holder
    text: The signing SDK needs a wrapper that knows where the PFX file lives and
      what password protects it. The `CertificateHolder` class encapsulates this information.
  - name: Sign the document with default XML‑DSIG settings
    text: 'The first signature demonstrates the simplest scenario: a standard XML‑DSIG
      envelope. This is useful when you only need a basic integrity check.'
  - name: Configure XAdES‑EPES signature options
    text: XAdES‑EPES (Extended Advanced Electronic Signature – Explicit Policy‑Based
      Electronic Signature) adds policy information and stronger non‑repudiation guarantees.
      To use it, you must create a `SignatureOptions` instance and set the desired
      level.
  - name: Sign the document with XAdES‑EPES
    text: Now we apply the options created in the previous step. The overload of `sign`
      that accepts a `SignatureOptions` object lets you inject the policy.
  - name: Full runnable example
    text: Combine the pieces into a single `main` method so you can execute the workflow
      with one command.
  type: HowTo
tags:
- docx signing
- pfx certificate
- java
- digital signature
title: Cara menandatangani file docx dengan sertifikat PFX – panduan langkah demi
  langkah
url: /id/java/document-security/how-to-sign-docx-files-with-a-pfx-certificate-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menandatangani file docx dengan sertifikat PFX – panduan langkah demi langkah

Jika Anda perlu **how to sign docx** file secara programatis, panduan ini menunjukkan langkah‑langkah yang tepat. Anda akan belajar cara **sign document pfx** file, mengonfigurasi XAdES‑EPES, dan menghasilkan output DOCX yang dapat diverifikasi—semua dalam plain Java.

Menandatangani file DOCX adalah kebutuhan umum untuk otomatisasi kontrak, kepatuhan hukum, dan pertukaran dokumen yang aman. Pada akhir tutorial ini Anda akan memiliki contoh lengkap yang dapat dijalankan yang menandatangani dokumen Word input dua kali—sekali dengan pengaturan XML‑DSIG default dan sekali lagi dengan level XAdES‑EPES yang lebih kuat.

## Prasyarat

- Java 17 atau lebih baru (kode menggunakan sintaks modern `var` untuk singkat)
- Maven atau Gradle untuk mengelola dependensi
- File **PFX** (PKCS #12) yang valid yang berisi kunci pribadi dan rantai sertifikatnya
- Perpustakaan GroupDocs.Signature untuk Java (atau SDK penandatanganan yang kompatibel). Contoh menggunakan koordinat Maven `com.groupdocs:groupdocs-signature:23.5`.

Jika Anda belum memiliki file PFX, Anda dapat membuatnya dengan OpenSSL:

```bash
openssl pkcs12 -export -out mycert.pfx -inkey private.key -in certificate.crt -certfile ca_bundle.crt
```

> **Pro tip:** Lindungi PFX dengan kata sandi yang kuat dan simpan di luar kontrol sumber.

## Cara menandatangani docx menggunakan sertifikat PFX

Alur kerja inti terdiri dari empat langkah logis:

1. Muat file PFX ke dalam `CertificateHolder`.
2. Tanda tangani DOCX dengan profil XML‑DSIG default.
3. Tentukan opsi XAdES‑EPES.
4. Tanda tangani kembali DOCX menggunakan opsi tersebut.

Setiap langkah dijelaskan di bawah, dan kode sumber lengkap mengikuti penjelasan.

### Langkah 1: Muat pemegang sertifikat PFX

SDK penandatanganan membutuhkan pembungkus yang mengetahui lokasi file PFX dan kata sandi yang melindunginya. Kelas `CertificateHolder` mengenkapsulasi informasi ini.

```java
import com.groupdocs.signature.options.sign.SignatureOptions;
import com.groupdocs.signature.utils.DigitalSignatureUtil;
import com.groupdocs.signature.options.enumerations.SignatureType;
import com.groupdocs.signature.options.enumerations.XmlDsigLevel;
import com.groupdocs.signature.certificate.CertificateHolder;

public class DocxSigner {
    // Path to the PFX file and its password
    private static final String PFX_PATH = "YOUR_DIRECTORY/mycert.pfx";
    private static final String PFX_PASSWORD = "password";

    // Helper method to create a CertificateHolder
    private static CertificateHolder loadCertificate() {
        // The CertificateHolder reads the PFX file and prepares the private key for signing
        return new CertificateHolder(PFX_PATH, PFX_PASSWORD);
    }
}
```

**Why this matters:** SDK tidak dapat mengakses kunci pribadi secara langsung; harus dimuat melalui kontainer yang aman. Menggunakan `CertificateHolder` juga mengabstraksi penanganan keystore spesifik platform.

### Langkah 2: Tanda tangani dokumen dengan pengaturan XML‑DSIG default

Tanda tangan pertama menunjukkan skenario paling sederhana: sebuah envelope XML‑DSIG standar. Ini berguna ketika Anda hanya membutuhkan pemeriksaan integritas dasar.

```java
public static void signWithDefaultXmlDsig(CertificateHolder cert) throws Exception {
    String inputPath = "YOUR_DIRECTORY/input.docx";
    String outputPath = "YOUR_DIRECTORY/signed.docx";

    // The static sign method performs the actual signing operation.
    DigitalSignatureUtil.sign(
        inputPath,
        outputPath,
        cert,
        SignatureType.XML_DSIG   // Use the XML‑DSIG profile
    );

    System.out.println("Document signed with default XML‑DSIG: " + outputPath);
}
```

**Explanation:** `DigitalSignatureUtil.sign` mengabstraksi manipulasi XML tingkat rendah. Konstanta `SignatureType.XML_DSIG` memberi tahu perpustakaan untuk menghasilkan tanda tangan digital XML standar yang mematuhi spesifikasi W3C.

### Langkah 3: Konfigurasikan opsi tanda tangan XAdES‑EPES

XAdES‑EPES (Extended Advanced Electronic Signature – Explicit Policy‑Based Electronic Signature) menambahkan informasi kebijakan dan jaminan non‑repudiation yang lebih kuat. Untuk menggunakannya, Anda harus membuat instance `SignatureOptions` dan menetapkan level yang diinginkan.

```java
private static SignatureOptions createXadesEpesOptions() {
    SignatureOptions options = new SignatureOptions();
    // XAdES‑EPES is the most commonly required level for regulated environments
    options.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);
    return options;
}
```

**Why XAdES‑EPES?** Banyak kerangka hukum (mis., eIDAS di UE) mengharuskan tanda tangan yang menyertakan kebijakan penandatanganan. Level EPES memenuhi persyaratan tersebut tanpa beban penuh tanda tangan XAdES‑T (bertanda waktu).

### Langkah 4: Tanda tangani dokumen dengan XAdES‑EPES

Sekarang kami menerapkan opsi yang dibuat pada langkah sebelumnya. Overload `sign` yang menerima objek `SignatureOptions` memungkinkan Anda menyuntikkan kebijakan.

```java
public static void signWithXadesEpes(CertificateHolder cert, SignatureOptions options) throws Exception {
    String inputPath = "YOUR_DIRECTORY/input.docx";
    String outputPath = "YOUR_DIRECTORY/signed_epes.docx";

    DigitalSignatureUtil.sign(
        inputPath,
        outputPath,
        cert,
        SignatureType.XML_DSIG, // Still XML‑DSIG, but with XAdES‑EPES policy
        options                 // Pass the configured options
    );

    System.out.println("Document signed with XAdES‑EPES: " + outputPath);
}
```

### Contoh lengkap yang dapat dijalankan

Gabungkan bagian-bagian menjadi satu metode `main` sehingga Anda dapat mengeksekusi alur kerja dengan satu perintah.

```java
public class DocxSigner {
    private static final String PFX_PATH = "YOUR_DIRECTORY/mycert.pfx";
    private static final String PFX_PASSWORD = "password";

    public static void main(String[] args) {
        try {
            // Load the certificate holder (sign document pfx)
            CertificateHolder cert = new CertificateHolder(PFX_PATH, PFX_PASSWORD);

            // 1️⃣ Default XML‑DSIG signature
            signWithDefaultXmlDsig(cert);

            // 2️⃣ XAdES‑EPES signature
            SignatureOptions xadesOptions = createXadesEpesOptions();
            signWithXadesEpes(cert, xadesOptions);

            System.out.println("Both signatures created successfully.");
        } catch (Exception e) {
            System.err.println("Signing failed: " + e.getMessage());
            e.printStackTrace();
        }
    }

    // --- Methods from previous sections (omitted for brevity) ---
    // signWithDefaultXmlDsig, createXadesEpesOptions, signWithXadesEpes
}
```

**Output yang diharapkan**

```
Document signed with default XML‑DSIG: YOUR_DIRECTORY/signed.docx
Document signed with XAdES‑EPES: YOUR_DIRECTORY/signed_epes.docx
Both signatures created successfully.
```

Buka `signed.docx` atau `signed_epes.docx` di Microsoft Word → **File → Info → View Signatures** untuk memverifikasi bahwa tanda tangan digital muncul dan dipercaya (asalkan rantai sertifikat terpasang di mesin).

## Pertanyaan umum dan kasus tepi

| Question | Answer |
|----------|--------|
| *Bagaimana jika kata sandi PFX salah?* | SDK melempar `InvalidKeyException`. Validasi kata sandi sebelum memanggil `sign`. |
| *Apakah saya dapat menandatangani DOCX yang sama beberapa kali?* | Ya. Setiap pemanggilan menambahkan elemen `<Signature>` baru. Perhatikan bahwa ukuran file akan bertambah dengan setiap tanda tangan. |
| *Apakah saya perlu menambahkan sertifikat ke Windows Trusted Store?* | Tidak untuk verifikasi dalam Word, tetapi validator eksternal (mis., Adobe Acrobat) mungkin memerlukan rantai tersebut dipercaya. |
| *Bagaimana menandatangani DOCX yang sudah berisi tanda tangan?* | SDK secara otomatis menambahkan elemen tanda tangan baru; tidak diperlukan kode tambahan. |
| *Bagaimana jika saya membutuhkan timestamp (XAdES‑T)?* | Ganti `XmlDsigLevel.XADES_EPES` dengan `XmlDsigLevel.XADES_T` dan sediakan URL TSA di `SignatureOptions`. |

## Praktik terbaik untuk menandatangani DOCX dengan sertifikat PFX

- **Store the PFX securely** – gunakan vault atau variabel lingkungan untuk kata sandi.
- **Validate the certificate chain** sebelum menandatangani untuk menghindari kegagalan kepercayaan di kemudian hari.
- **Prefer XAdES‑EPES** untuk industri yang diatur; gunakan XML‑DSIG biasa hanya ketika kompatibilitas menjadi masalah.
- **Log the signing operation** (nama file, timestamp, penandatangan) untuk jejak audit.
- **Test verification** pada berbagai platform (Word, LibreOffice, validator online) untuk memastikan interoperabilitas.

## Kesimpulan

Dalam tutorial ini Anda belajar **how to sign docx** file menggunakan sertifikat **sign document pfx**, cara mengonfigurasi XAdES‑EPES, dan cara menghasilkan dua tanda tangan yang dapat diverifikasi dengan satu program Java. Contoh lengkap dapat disalin ke proyek Maven atau Gradle mana pun, disesuaikan dengan jalur input yang berbeda, dan diperluas dengan timestamp atau kebijakan tanda tangan khusus.

Selanjutnya, jelajahi topik terkait seperti **sign PDF with a PFX certificate**, **embed visible signature images**, atau **automate batch signing of multiple Word documents**. Ekstensi ini dibangun di atas konsep yang sama yang disajikan di sini dan lebih memperkuat alur kerja keamanan dokumen Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang dibangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Sign Word Document](/words/english/net/programming-with-digital-signatures/sign-document/)
- [Sign Document](/words/hindi/net/programming-with-digital-signatures/sign-document/)
- [Sign Document](/words/spanish/net/programming-with-digital-signatures/sign-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}