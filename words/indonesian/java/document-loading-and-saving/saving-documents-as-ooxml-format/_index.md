---
date: 2025-12-29
description: Pelajari cara mengenkripsi docx dengan kata sandi menggunakan opsi penyimpanan
  Aspose.Words untuk Java. Amankan, optimalkan, dan sesuaikan file OOXML Anda dengan
  mudah.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Cara Mengenkripsi DOCX dengan Kata Sandi Menggunakan Aspose.Words untuk Java
url: /id/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengenkripsi DOCX dengan Kata Sandi Menggunakan Aspose.Words untuk Java

Dalam panduan ini Anda akan menemukan **cara mengenkripsi docx dengan kata sandi** saat menyimpan dokumen dalam format OOXML menggunakan Aspose.Words untuk Java. Baik Anda melindungi laporan rahasia maupun mengamankan draf kontrak, langkah‑langkah di bawah ini menunjukkan secara tepat cara menerapkan perlindungan kata sandi dan menyesuaikan opsi penyimpanan OOXML lainnya.

## Jawaban Cepat
- **Apakah saya dapat mengenkripsi file DOCX dengan kata sandi?** Ya, gunakan `OoxmlSaveOptions.setPassword()` sebelum menyimpan.  
- **Kelas mana yang mengontrol pengaturan penyimpanan OOXML?** `OoxmlSaveOptions` (bagian dari Aspose.Words).  
- **Apakah saya memerlukan lisensi untuk perlindungan kata sandi?** Lisensi Aspose.Words yang valid diperlukan untuk penggunaan produksi.  
- **Bisakah saya menggabungkan enkripsi dengan pengaturan kepatuhan?** Tentu – atur kedua `setPassword` dan `setCompliance` pada instance `OoxmlSaveOptions` yang sama.  
- **Level kompresi apa yang tersedia?** `NORMAL`, `SUPER_FAST`, dan `MAXIMUM` melalui `CompressionLevel`.

## Apa itu “encrypt docx with password”?
Mengenkripsi file DOCX berarti isi file disimpan dalam bentuk terenkripsi dan hanya dapat dibuka setelah memasukkan kata sandi yang benar. Ini melindungi informasi sensitif dari akses tidak sah sekaligus tetap memungkinkan alat Word standar membuka file setelah kata sandi diberikan.

## Mengapa menggunakan opsi penyimpanan Aspose.Words untuk enkripsi?
Aspose.Words menyediakan serangkaian **aspose words save options** yang kaya yang memungkinkan Anda mengontrol tidak hanya enkripsi tetapi juga level kepatuhan, kompresi, dan penanganan karakter warisan — semuanya dari kode Java. Ini menghilangkan kebutuhan akan pemrosesan manual atau alat pihak ketiga.

## Prasyarat
- Java Development Kit (JDK 8 atau lebih tinggi)  
- Perpustakaan Aspose.Words untuk Java yang ditambahkan ke proyek Anda (Maven/Gradle atau JAR)  
- Lisensi Aspose.Words yang valid untuk produksi (opsional untuk evaluasi)

## Menyimpan Dokumen dengan Enkripsi Kata Sandi

Anda dapat mengenkripsi dokumen dengan kata sandi saat menyimpannya dalam format OOXML. Berikut caranya:

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

## Menetapkan Kepatuhan OOXML

Anda dapat menentukan level kepatuhan OOXML saat menyimpan dokumen. Misalnya, Anda dapat mengaturnya ke ISO 29500:2008 (Strict). Berikut caranya:

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

## Menjaga Karakter Kontrol Warisan

Jika dokumen Anda berisi karakter kontrol warisan, Anda dapat memilih untuk mempertahankannya saat menyimpan. Berikut caranya:

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

## Menetapkan Level Kompresi

Anda dapat menyesuaikan level kompresi saat menyimpan dokumen. Misalnya, Anda dapat mengaturnya ke **SUPER_FAST** untuk kompresi minimal. Berikut caranya:

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

Ini adalah beberapa opsi dan pengaturan kunci yang dapat Anda gunakan saat menyimpan dokumen dalam format OOXML menggunakan Aspose.Words untuk Java. Jangan ragu untuk menjelajahi opsi lain dan menyesuaikan proses penyimpanan dokumen Anda sesuai kebutuhan.

## Kode Sumber Lengkap untuk Menyimpan Dokumen sebagai Format OOXML di Aspose.Words untuk Java

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

Dalam panduan komprehensif ini, kami telah mengeksplorasi cara **encrypt docx with password** dan menyesuaikan berbagai opsi penyimpanan OOXML menggunakan Aspose.Words untuk Java. Baik Anda perlu melindungi konten rahasia, memenuhi kepatuhan ISO yang ketat, mempertahankan karakter warisan, atau mengontrol kompresi, perpustakaan ini memberikan kontrol granular melalui API `OoxmlSaveOptions` yang sama.

## Pertanyaan yang Sering Diajukan

**T: Bagaimana cara menghapus perlindungan kata sandi dari dokumen yang diproteksi?**  
J: Buka dokumen dengan kata sandi yang benar, lalu simpan kembali tanpa memanggil `setPassword`. File baru akan tidak diproteksi.

**T: Bisakah saya menetapkan properti khusus saat menyimpan dokumen dalam format OOXML?**  
J: Ya. Gunakan `BuiltInDocumentProperties` atau `CustomDocumentProperties` pada objek `Document` sebelum memanggil `save`.

**T: Apa level kompresi default saat menyimpan dokumen dalam format OOXML?**  
J: Defaultnya adalah `NORMAL`. Anda dapat beralih ke `SUPER_FAST` untuk kecepatan atau `MAXIMUM` untuk ukuran file yang lebih kecil.

**T: Apakah opsi aspose words save options bekerja dengan versi Word yang lebih lama?**  
J: Ya. Dengan menyesuaikan `MsWordVersion` dan pengaturan kepatuhan, Anda dapat menargetkan Word 2007‑2019 dan memastikan kompatibilitas.

**T: Apakah memungkinkan menggabungkan beberapa opsi penyimpanan dalam satu operasi?**  
J: Tentu. Buat satu instance `OoxmlSaveOptions`, atur semua properti yang diinginkan (kata sandi, kepatuhan, kompresi, dll.), dan berikan ke `doc.save()`.

---

**Terakhir Diperbarui:** 2025-12-29  
**Diuji Dengan:** Aspose.Words untuk Java 24.12  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}