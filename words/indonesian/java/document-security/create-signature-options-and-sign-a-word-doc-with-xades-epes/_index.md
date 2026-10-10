---
category: general
date: 2026-10-10
description: Buat opsi tanda tangan dan tanda tangani dokumen Word menggunakan XAdES
  EPES di Java. Pelajari cara menandatangani dokumen Office dengan sertifikat dalam
  beberapa langkah jelas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: id
lastmod: 2026-10-10
og_description: Buat opsi tanda tangan dan tanda tangani dokumen Word menggunakan
  XAdES EPES di Java. Panduan ini menunjukkan cara menandatangani dokumen Office secara
  aman dengan sertifikat.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: Buat opsi tanda tangan dan tandatangani dokumen Word dengan XAdES EPES
schemas:
- author: GroupDocs
  dateModified: '2026-10-10'
  description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  headline: Create signature options and sign a Word doc with XAdES EPES
  type: TechArticle
- description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  name: Create signature options and sign a Word doc with XAdES EPES
  steps:
  - name: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
    text: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
  - name: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
    text: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
  - name: The signature is embedded into the DOCX package, preserving the original
      document layout.
    text: The signature is embedded into the DOCX package, preserving the original
      document layout.
  - name: Open `SignedXades.docx` in Word.
    text: Open `SignedXades.docx` in Word.
  - name: Click **File → Info → View signatures**.
    text: Click **File → Info → View signatures**.
  - name: Word should display a green checkmark indicating a valid digital signature.
    text: Word should display a green checkmark indicating a valid digital signature.
  type: HowTo
tags:
- digital signature
- Java
- XAdES
title: Buat opsi tanda tangan dan tanda tangani dokumen Word dengan XAdES EPES
url: /id/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat opsi tanda tangan dan tanda tangani dokumen Word dengan XAdES EPES

Jika Anda perlu **membuat opsi tanda tangan** untuk file DOCX, panduan ini menunjukkan cara menandatangani dokumen Word menggunakan level XAdES‑EPES di Java. Anda akan mendapatkan contoh lengkap yang dapat dijalankan yang menandatangani dokumen Office dengan sertifikat PFX hanya dalam beberapa baris kode.

Menandatangani dokumen office adalah kebutuhan umum untuk alur kerja hukum, pemrosesan kontrak otomatis, dan pertukaran dokumen yang aman. Dalam tutorial ini Anda akan belajar:

* Cara mengkonfigurasi `SignatureOptions` untuk XAdES‑EPES.
* Cara memanggil `DigitalSignatureUtil.sign` untuk **menandatangani file word doc**.
* Cara menangani jebakan umum seperti pemuatan sertifikat dan kesalahan kata sandi.

> **Prasyarat** – Java 17 atau lebih baru, library GroupDocs.Signature untuk Java (atau library XAdES yang kompatibel), dan file sertifikat `.pfx` yang valid.

---

## Apa yang Anda butuhkan

| Item | Reason |
|------|--------|
| Java 17+ | Fitur bahasa modern dan API keamanan yang lebih baik |
| GroupDocs.Signature for Java (or equivalent) | Menyediakan `SignatureOptions`, `XmlDsigLevel`, dan `DigitalSignatureUtil` |
| A PFX certificate (`.pfx`) | Menyediakan kunci pribadi untuk tanda tangan digital |
| Password for the certificate | Diperlukan untuk membuka kunci pribadi |
| An unsigned DOCX file (`Unsigned.docx`) | Dokumen sumber yang ingin Anda **tandatangani dokumen office** |

Pastikan JAR library berada di classpath Anda:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

---

## Langkah 1: Impor kelas yang diperlukan

Mulailah dengan mengimpor kelas yang menangani tanda tangan dan I/O file.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

Impor ini memberi Anda akses ke API yang digunakan untuk **membuat opsi tanda tangan** dan melakukan operasi penandatanganan sebenarnya.

---

## Langkah 2: Buat opsi tanda tangan

Objek `SignatureOptions` menyimpan semua konfigurasi yang diperlukan untuk proses penandatanganan, seperti level tanda tangan, tampilan visual, dan pengaturan timestamp.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Membuat instance `SignatureOptions` baru adalah langkah pertama dalam **cara menandatangani docx** karena ia mengisolasi setiap permintaan penandatanganan, mencegah efek samping lintas‑dokumen.

---

## Langkah 3: Tentukan level tanda tangan XAdES EPES

XAdES‑EPES (Explicit Policy-based Electronic Signature) adalah kebijakan yang banyak diterima untuk tanda tangan dokumen Office. Menetapkan level memberi tahu library profil kriptografi mana yang akan digunakan.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

Mengapa XAdES‑EPES? Ia menyematkan kebijakan penandatanganan langsung ke dalam tanda tangan, menjadikan dokumen yang ditandatangani mandiri dan mematuhi banyak regulasi e‑signature.

---

## Langkah 4: Tanda tangani file DOCX

Sekarang panggil `DigitalSignatureUtil.sign`. Metode ini membaca file sumber, menerapkan tanda tangan, dan menulis output yang telah ditandatangani.

```java
// Step 4: Sign the document using the provided certificate
try {
    DigitalSignatureUtil.sign(
        "YOUR_DIRECTORY/Unsigned.docx",   // input file
        "YOUR_DIRECTORY/SignedXades.docx", // output file
        "YOUR_DIRECTORY/mycert.pfx",      // certificate file
        "password",                       // certificate password
        signatureOptions                  // options configured above
    );
    System.out.println("Document signed successfully: SignedXades.docx");
} catch (IOException e) {
    System.err.println("Failed to sign the document: " + e.getMessage());
}
```

**Apa yang terjadi di balik layar?**  
1. Library memuat file `.pfx` dan mengekstrak kunci pribadi menggunakan kata sandi yang diberikan.  
2. Ia membuat struktur XML‑DSig yang sesuai dengan profil XAdES‑EPES.  
3. Tanda tangan disematkan ke dalam paket DOCX, mempertahankan tata letak dokumen asli.  

Jika kata sandi sertifikat salah atau file tidak dapat dibaca, `IOException` akan dilempar, yang harus Anda tangani seperti yang ditunjukkan.

---

## Langkah 5: Verifikasi dokumen yang ditandatangani (opsional)

Setelah menandatangani, Anda mungkin ingin memastikan bahwa tanda tangan ada dan valid. GroupDocs menyediakan API verifikasi, tetapi pemeriksaan manual cepat dapat dilakukan dengan Microsoft Word:

1. Buka `SignedXades.docx` di Word.  
2. Klik **File → Info → View signatures**.  
3. Word akan menampilkan tanda centang hijau yang menunjukkan tanda tangan digital yang valid.

Verifikasi otomatis dengan library terlihat seperti ini:

```java
import com.groupdocs.signature.VerificationResult;

VerificationResult result = DigitalSignatureUtil.verify(
    "YOUR_DIRECTORY/SignedXades.docx",
    signatureOptions
);

if (result.isSuccessful()) {
    System.out.println("Signature verification succeeded.");
} else {
    System.out.println("Signature verification failed: " + result.getErrorMessage());
}
```

Menjalankan langkah verifikasi memberi Anda keyakinan programatik bahwa **menandatangani dokumen office** berhasil.

---

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian, berikut adalah kelas Java mandiri yang dapat Anda salin, tempel, dan jalankan.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import com.groupdocs.signature.VerificationResult;
import java.io.IOException;

/**
 * Demonstrates how to create signature options and sign a DOCX file with XAdES EPES.
 */
public class XadesSignatureDemo {

    public static void main(String[] args) {
        // Paths – update these to match your environment
        String inputPath = "YOUR_DIRECTORY/Unsigned.docx";
        String outputPath = "YOUR_DIRECTORY/SignedXades.docx";
        String certPath = "YOUR_DIRECTORY/mycert.pfx";
        String certPassword = "password";

        // 1️⃣ Create signature options
        SignatureOptions signatureOptions = new SignatureOptions();

        // 2️⃣ Set XAdES EPES level
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 3️⃣ Sign the document
        try {
            DigitalSignatureUtil.sign(inputPath, outputPath, certPath, certPassword, signatureOptions);
            System.out.println("Document signed successfully: " + outputPath);
        } catch (IOException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // 4️⃣ (Optional) Verify the signature
        VerificationResult verification = DigitalSignatureUtil.verify(outputPath, signatureOptions);
        if (verification.isSuccessful()) {
            System.out.println("Signature verification succeeded.");
        } else {
            System.out.println("Signature verification failed: " + verification.getErrorMessage());
        }
    }
}
```

**Output yang diharapkan**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

Jika ada yang salah, konsol akan menampilkan pesan error yang jelas, membantu Anda memecahkan masalah sertifikat atau jalur file.

---

## Pertanyaan umum dan penanganan kasus tepi

| Question | Answer |
|----------|--------|
| **Apakah saya dapat menggunakan level tanda tangan yang berbeda?** | Ya. Ganti `XmlDsigLevel.XAdES_EPES` dengan `XAdES_BES`, `XAdES_T`, dll., tergantung pada kebutuhan kepatuhan. |
| **Bagaimana jika sertifikat saya disimpan di keystore bukan file .pfx?** | Muat `KeyStore` secara manual, ekstrak `PrivateKey` dan `Certificate`, lalu berikan ke overload `sign` yang menerima objek `KeyStore`. |
| **Bagaimana cara menambahkan gambar tanda tangan yang terlihat?** | Gunakan `signatureOptions.setSignatureImage("path/to/image.png")` sebelum memanggil `sign`. |
| **Apakah proses penandatanganan thread‑safe?** | Metode `DigitalSignatureUtil.sign` bersifat stateless; Anda dapat memanggilnya dengan aman dari banyak thread selama setiap thread menggunakan instance `SignatureOptions` masing‑masing. |
| **Bagaimana jika DOCX berisi tanda tangan yang sudah ada?** | Library akan menambahkan entri paket tanda tangan baru, mempertahankan tanda tangan sebelumnya. Verifikasi bahwa kebijakan penandatanganan mengizinkan beberapa tanda tangan jika diperlukan. |

---

## Tips dan praktik terbaik (E‑E‑A‑T)

* **Tips pro:** Simpan kata sandi sertifikat Anda di vault yang aman (mis., Azure Key Vault) daripada menuliskannya secara hard‑code.  
* **Waspadai:** Pemisah jalur file di Windows (`\`) vs. Unix (`/`). Gunakan `Paths.get(...)` untuk membangun jalur yang independen platform.  
* **Kinerja:** Menandatangani file DOCX besar dapat terbatas oleh I/O; pertimbangkan streaming file input jika Anda memproses banyak dokumen secara batch.  
* **Kepatuhan:** XAdES‑EPES mematuhi regulasi EU eIDAS; verifikasi persyaratan hukum lokal Anda sebelum memilih level tanda tangan.

---

## Kesimpulan

Dalam tutorial ini Anda belajar cara **membuat opsi tanda tangan** dan **menandatangani dokumen Word** dengan level XAdES‑EPES menggunakan Java. Contoh lengkap mencakup pemuatan sertifikat, konfigurasi opsi, pemanggilan penandatanganan, dan verifikasi opsional, memberikan Anda solusi siap pakai untuk **cara menandatangani docx** dalam produksi.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Opsi Muat di Java – Deteksi Font yang Hilang & Cara Memuat DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Menggunakan Opsi Dokumen dan Pengaturan di Aspose.Words untuk Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Cara Membuat Rentang yang Dapat Diedit dalam Dokumen Hanya-Baca Menggunakan Aspose.Words untuk Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}