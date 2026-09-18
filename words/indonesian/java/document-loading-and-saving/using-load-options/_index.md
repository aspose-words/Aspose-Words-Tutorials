---
date: 2025-12-27
description: Pelajari cara mengatur LoadOptions di Aspose.Words untuk Java, termasuk
  cara menentukan folder sementara, mengatur versi Word, mengonversi metafile ke PNG,
  dan mengonversi shape menjadi matematika untuk pemrosesan dokumen yang fleksibel.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Cara Mengatur LoadOptions di Aspose.Words untuk Java
url: /id/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengatur LoadOptions di Aspose.Words untuk Java

Dalam tutorial ini kami akan membahas **cara mengatur LoadOptions** untuk berbagai skenario dunia nyata saat bekerja dengan Aspose.Words untuk Java. LoadOptions memberi Anda kontrol yang sangat detail atas cara dokumen dibuka—apakah Anda perlu memperbarui field yang kotor, bekerja dengan file terenkripsi, mengonversi shape menjadi Office Math, atau memberi tahu perpustakaan di mana menyimpan data sementara. Pada akhir tutorial Anda akan dapat menyesuaikan perilaku pemuatan agar sesuai dengan kebutuhan aplikasi Anda secara tepat.

## Jawaban Cepat
- **Apa itu LoadOptions?** Objek konfigurasi yang memengaruhi cara Aspose.Words memuat dokumen.  
- **Bisakah saya memperbarui field saat memuat?** Ya—atur `setUpdateDirtyFields(true)`.  
- **Bagaimana cara membuka file yang dilindungi password?** Berikan password ke konstruktor `LoadOptions`.  
- **Apakah memungkinkan mengubah folder sementara?** Gunakan `setTempFolder("path")`.  
- **Metode mana yang mengonversi shape menjadi Office Math?** `setConvertShapeToOfficeMath(true)`.

## Mengapa Menggunakan LoadOptions?
LoadOptions memungkinkan Anda menghindari langkah pemrosesan setelah pemuatan, mengurangi penggunaan memori, dan memastikan dokumen diinterpretasikan persis seperti yang Anda butuhkan. Misalnya, mengonversi metafile ke PNG saat pemuatan mencegah masalah rasterisasi di kemudian hari, dan menentukan versi MS Word membantu mempertahankan kesetiaan tata letak saat berurusan dengan file lama.

## Prasyarat
- Java 17 atau lebih baru  
- Aspose.Words untuk Java (versi terbaru)  
- Lisensi Aspose yang valid untuk penggunaan produksi  

## Panduan Langkah‑per‑Langkah

### Perbarui Field Kotor

Ketika dokumen berisi field yang telah diedit tetapi belum disegarkan, Anda dapat memberi tahu Aspose.Words untuk secara otomatis memperbaruinya selama pemuatan.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*Pemanggilan `setUpdateDirtyFields(true)` memastikan bahwa semua field kotor dihitung ulang segera setelah dokumen dibuka.*

### Muat Dokumen Terenkripsi

Jika file sumber Anda dilindungi password, berikan password saat membuat instance `LoadOptions`. Anda juga dapat mengatur password baru saat menyimpan ke format yang berbeda.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Konversi Shape ke Office Math

Beberapa dokumen lama menyimpan persamaan sebagai shape gambar. Mengaktifkan opsi ini mengonversi shape tersebut menjadi objek Office Math native, yang lebih mudah diedit kemudian.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### Atur Versi MS Word

Menentukan versi Word target membantu perpustakaan memilih aturan rendering yang tepat, terutama saat berurusan dengan format file yang lebih lama.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Gunakan Folder Sementara

Dokumen besar mungkin menghasilkan file sementara (misalnya, saat mengekstrak gambar). Anda dapat mengarahkan file-file ini ke folder pilihan Anda, yang berguna untuk lingkungan sandbox.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Callback Peringatan

Selama pemuatan, Aspose.Words dapat mengeluarkan peringatan (misalnya, fitur yang tidak didukung). Mengimplementasikan callback memungkinkan Anda mencatat atau menanggapi peristiwa tersebut.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Konversi Metafile ke PNG

Metafile seperti WMF dapat dirasterkan menjadi PNG selama pemuatan, memastikan rendering yang konsisten di semua platform.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Kode Sumber Lengkap untuk Bekerja dengan Load Options di Aspose.Words untuk Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		// Prints warnings and their details as they arise during document loading.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Kasus Penggunaan Umum & Tips

- **Pipeline konversi batch** – Gabungkan `setTempFolder` dengan pekerjaan terjadwal untuk memproses ratusan file tanpa mengisi direktori temp sistem.  
- **Migrasi dokumen lama** – Gunakan `setMswVersion` bersama `setConvertShapeToOfficeMath` untuk membawa dokumen teknik lama ke format modern sambil mempertahankan persamaan.  
- **Penanganan dokumen aman** – Padukan `loadEncryptedDocument` dengan `OdtSaveOptions` untuk mengenkripsi ulang file dengan password baru dalam format yang berbeda.  

## Pertanyaan yang Sering Diajukan

**T: Bagaimana saya dapat menangani peringatan selama pemuatan dokumen?**  
J: Implementasikan `IWarningCallback` khusus (seperti pada contoh *Callback Peringatan*) dan daftarkan melalui `loadOptions.setWarningCallback(...)`. Ini memungkinkan Anda mencatat, mengabaikan, atau menghentikan proses berdasarkan tingkat keparahan peringatan.

**T: Bisakah saya mengonversi shape menjadi objek Office Math saat memuat dokumen?**  
J: Ya—panggil `loadOptions.setConvertShapeToOfficeMath(true)` sebelum membuat `Document`. Perpustakaan secara otomatis akan mengganti shape yang kompatibel dengan objek Office Math native.

**T: Bagaimana cara menentukan versi MS Word untuk pemuatan dokumen?**  
J: Gunakan `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (atau nilai enum lain) untuk memberi tahu Aspose.Words aturan rendering versi Word mana yang harus diterapkan.

**T: Apa tujuan metode `setTempFolder` dalam LoadOptions?**  
J: Metode ini mengarahkan semua file sementara yang dihasilkan selama pemuatan (seperti gambar yang diekstrak) ke folder yang Anda kontrol, yang penting untuk lingkungan dengan direktori temp sistem yang terbatas.

**T: Apakah memungkinkan mengonversi metafile seperti WMF ke PNG selama pemuatan?**  
J: Tentu—aktifkan dengan `loadOptions.setConvertMetafilesToPng(true)`. Ini memastikan gambar raster disimpan sebagai PNG, meningkatkan kompatibilitas dengan penampil modern.

## Kesimpulan

Kami telah membahas teknik penting **cara mengatur LoadOptions** di Aspose.Words untuk Java, mulai dari memperbarui field kotor hingga menangani file terenkripsi, mengonversi shape, menentukan versi Word, mengarahkan penyimpanan sementara, dan lainnya. Dengan memanfaatkan opsi-opsi ini Anda dapat membangun pipeline pemrosesan dokumen yang kuat dan berperforma tinggi yang dapat beradaptasi dengan berbagai skenario input.

---

**Terakhir Diperbarui:** 2025-12-27  
**Diuji Dengan:** Aspose.Words untuk Java 24.11  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}