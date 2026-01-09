---
date: 2026-01-09
description: Pelajari cara mengenkripsi file docx dengan kata sandi dan mengubah tingkat
  kompresi saat menyimpan dokumen dalam format OOXML menggunakan Aspose.Words untuk
  Java.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Enkripsi docx dengan kata sandi – Simpan OOXML dengan Aspose.Words Java
url: /id/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Enkripsi docx dengan password – Simpan OOXML dengan Aspose.Words Java

## Pendahuluan tentang Menyimpan Dokumen dalam Format OOXML di Aspose.Words untuk Java

Dalam panduan ini, Anda akan belajar cara **encrypt docx with password** dan menyimpan dokumen dalam format OOXML menggunakan Aspose.Words untuk Java. OOXML (Office Open XML) adalah format file modern yang digunakan oleh Microsoft Word dan banyak aplikasi perkantoran lainnya. Kami akan membahas opsi-opsi paling umum—perlindungan password, tingkat kepatuhan, pembaruan properti, penanganan karakter legacy, dan **how to change compression level**—sehingga Anda dapat menyesuaikan output sesuai kebutuhan Anda.

## Jawaban Cepat
- **Bagaimana cara melindungi file Word?** Gunakan `OoxmlSaveOptions.setPassword("yourPassword")` sebelum menyimpan.  
- **Tingkat kepatuhan OOXML mana yang harus saya pilih?** ISO 29500 2008 Strict untuk kompatibilitas maksimum dengan versi Office modern.  
- **Apakah saya dapat mempertahankan karakter kontrol legacy?** Ya, aktifkan `setKeepLegacyControlChars(true)`.  
- **Bagaimana cara mengubah tingkat kompresi?** Atur `setCompressionLevel(CompressionLevel.SUPER_FAST)` atau `MAXIMUM` sesuai kebutuhan.  
- **Apakah opsi-opsi ini memengaruhi ukuran file?** Tingkat kompresi dan penanganan karakter legacy dapat secara signifikan mengubah ukuran akhir .docx.

## Apa itu “encrypt docx with password”?
Mengenkripsi file DOCX berarti dokumen disimpan dengan enkripsi AES‑256, memerlukan password untuk membukanya di Word atau penampil kompatibel lainnya. Ini penting untuk melindungi informasi rahasia ketika file dibagikan melalui email, penyimpanan cloud, atau portal intranet.

## Mengapa menggunakan opsi penyimpanan OOXML?
- **Keamanan:** Perlindungan password mencegah akses tidak sah.  
- **Kompatibilitas:** Pengaturan kepatuhan memastikan file berfungsi di berbagai versi Word.  
- **Kinerja:** Menyesuaikan kompresi dapat mempercepat proses penyimpanan atau mengurangi ukuran file.  
- **Preservasi:** Mempertahankan karakter kontrol legacy menjaga kesetiaan saat mengonversi dokumen lama.

## Prasyarat
- Perpustakaan Aspose.Words untuk Java sudah ditambahkan ke proyek Anda (Maven/Gradle atau JAR manual).  
- Java 8 atau lebih tinggi.  
- Dokumen sumber (`.docx` atau `.doc`) yang ingin Anda proses.

## Menyimpan Dokumen dengan Enkripsi Password

Anda dapat mengenkripsi dokumen dengan password saat menyimpannya dalam format OOXML. Berikut cara melakukannya:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

> **Pro tip:** Pilih password yang kuat dan simpan dengan aman; password tidak dapat dipulihkan dari file yang terenkripsi.

## Menetapkan Kepatuhan OOXML

Anda dapat menentukan tingkat kepatuhan OOXML saat menyimpan dokumen. Misalnya, Anda dapat mengaturnya ke ISO 29500:2008 (Strict). Berikut caranya:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## Memperbarui Properti “Last Saved Time”

Anda dapat memilih untuk memperbarui properti “Last Saved Time” dokumen saat menyimpannya. Berikut caranya:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Mempertahankan Karakter Kontrol Legacy

Jika dokumen Anda berisi karakter kontrol legacy, Anda dapat memilih untuk mempertahankannya saat menyimpan. Berikut caranya:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Cara Mengubah Tingkat Kompresi Saat Menyimpan OOXML

Anda dapat menyesuaikan tingkat kompresi saat menyimpan dokumen. Misalnya, Anda dapat mengaturnya ke `SUPER_FAST` untuk kompresi minimal atau `MAXIMUM` untuk ukuran file terkecil. Berikut caranya:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

Berikut beberapa opsi dan pengaturan utama yang dapat Anda gunakan saat menyimpan dokumen dalam format OOXML menggunakan Aspose.Words untuk Java. Jelajahi lebih banyak opsi dan sesuaikan proses penyimpanan dokumen Anda sesuai kebutuhan.

## Kode Sumber Lengkap untuk Menyimpan Dokumen dalam Format OOXML di Aspose.Words untuk Java

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## Kesimpulan

Dalam panduan komprehensif ini, kami telah membahas cara **encrypt docx with password** dan menyimpan dokumen dalam format OOXML menggunakan Aspose.Words untuk Java. Baik Anda perlu melindungi file, memastikan kepatuhan OOXML yang ketat, memperbarui properti dokumen, mempertahankan karakter kontrol legacy, atau **change compression level**, Aspose.Words menyediakan rangkaian alat yang fleksibel untuk memenuhi kebutuhan Anda.

## Pertanyaan yang Sering Diajukan

**Q: Bagaimana cara menghapus perlindungan password dari dokumen yang diproteksi password?**  
A: Buka dokumen dengan password yang benar, lalu simpan tanpa menentukan password di `OoxmlSaveOptions`. Ini akan menghasilkan salinan yang tidak diproteksi.

**Q: Bisakah saya mengatur properti khusus saat menyimpan dokumen dalam format OOXML?**  
A: Ya. Gunakan `BuiltInDocumentProperties` dan `CustomDocumentProperties` pada objek `Document` sebelum memanggil `save()`.

**Q: Apa tingkat kompresi default saat menyimpan dokumen dalam format OOXML?**  
A: Defaultnya adalah `CompressionLevel.NORMAL`. Anda dapat beralih ke `SUPER_FAST` untuk kecepatan atau `MAXIMUM` untuk ukuran file terkecil.

**Q: Apakah mengaktifkan `keepLegacyControlChars` memengaruhi kompatibilitas dengan versi Word modern?**  
A: Word modern dapat membuka file dengan karakter kontrol legacy, tetapi beberapa fitur lama mungkin ditampilkan berbeda. Gunakan opsi ini hanya bila Anda perlu mempertahankan konten asli secara tepat.

**Q: Apakah memungkinkan menggabungkan beberapa opsi penyimpanan (misalnya, password + kompresi) dalam satu panggilan?**  
A: Tentu saja. Konfigurasikan semua properti yang diinginkan pada satu instance `OoxmlSaveOptions` sebelum memberikannya ke `doc.save()`.

---

**Last Updated:** 2026-01-09  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}