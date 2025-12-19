---
date: 2025-12-19
description: Pelajari cara mengekspor HTML dengan Aspose.Words Java, mencakup opsi
  lanjutan untuk menyimpan Word sebagai HTML dan mengonversi Word ke HTML secara efisien.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Cara Mengekspor HTML dengan Aspose.Words Java: Opsi Lanjutan'
url: /id/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengekspor HTML dengan Aspose.Words Java: Opsi Lanjutan

Dalam tutorial ini Anda akan menemukan **cara mengekspor HTML** dari dokumen Word menggunakan Aspose.Words for Java. Baik Anda perlu **menyimpan Word sebagai HTML** untuk publikasi web atau **mengonversi Word ke HTML** untuk pemrosesan lanjutan, opsi penyimpanan lanjutan memberi Anda kontrol detail atas output. Kami akan membahas setiap opsi langkah demi langkah, menjelaskan kapan menggunakannya, dan menunjukkan skenario dunia nyata di mana pengaturan ini membuat perbedaan.

## Jawaban Cepat
- **Apa kelas utama untuk ekspor HTML?** `HtmlSaveOptions`  
- **Apakah font dapat disematkan langsung dalam HTML?** Ya, setel `exportFontsAsBase64` ke `true`.  
- **Bagaimana cara mempertahankan data round‑trip khusus Word?** Aktifkan `exportRoundtripInformation`.  
- **Format apa yang terbaik untuk grafik vektor?** Gunakan `convertMetafilesToSvg` untuk output SVG.  
- **Apakah memungkinkan menghindari bentrok nama kelas CSS?** Ya, gunakan `addCssClassNamePrefix`.

## 1. Pendahuluan
Aspose.Words for Java adalah API yang kuat yang memungkinkan pengembang memanipulasi dokumen Word secara programatis. Panduan ini berfokus pada opsi penyimpanan dokumen HTML lanjutan yang memungkinkan Anda menyesuaikan proses konversi untuk memenuhi kebutuhan web atau integrasi tertentu.

## 2. Mengekspor Informasi Roundtrip
Mempertahankan informasi‑trip memungkinkan Anda mengonversi HTML kembali ke dokumen Word tanpa kehilangan detail tata letak atau pemformatan.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### Kapan digunakan
- Ketika Anda membutuhkan pipeline konversi yang dapat dibalik (HTML → Word → HTML).  
- Ideal untuk skenario penyuntingan kolaboratif di mana struktur Word asli harus dipertahankan.

## 3. Mengekspor Font sebagai Base64
Menyematkan font langsung ke dalam HTML menghilangkan ketergantungan font eksternal dan memastikan kesetiaan visual di semua peramban.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Tips Pro
Gunakan opsi ini ketika lingkungan target memiliki akses terbatas ke sumber daya eksternal (misalnya, buletin email).

## 4. Mengekspor Sumber Daya
Mengontrol cara CSS dan sumber daya font dikeluarkan, serta menentukan folder khusus atau alias URL untuk aset tersebut.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

### Mengapa ini penting
Memisahkan CSS ke dalam file eksternal mengurangi ukuran HTML dan memungkinkan caching untuk pemuatan halaman yang lebih cepat.

## 5. Mengonversi Metafile ke EMF atau WMF
Metafile (misalnya, EMF/WMF) dikonversi ke format yang dapat dirender secara andal oleh peramban.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n                    vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

### Kasus Penggunaan
Pilih EMF/WMF ketika peramban target mendukung format vektor ini dan Anda memerlukan skala tanpa kehilangan kualitas.

## 6. Mengonversi Metafile ke SVG
SVG menyediakan skalabilitas terbaik dan didukung secara luas oleh peramban modern.

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

### Manfaat
File SVG ringan dan menjaga dokumen tetap independen resolusi, sempurna untuk desain web responsif.

## 7. Menambahkan Awalan Nama Kelas CSS
Cegah bentrok gaya dengan menambahkan awalan pada semua nama kelas CSS yang dihasilkan.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Tips Praktis
Gunakan awalan unik (misalnya, nama proyek Anda) saat menyematkan HTML ke dalam halaman yang ada untuk menghindari konflik CSS.

## 8. Mengekspor URL CID untuk Sumber Daya MHTML
Saat menyimpan sebagai MHTML, Anda dapat mengekspor sumber daya menggunakan URL Content‑ID untuk kompatibilitas email yang lebih baik.

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

### Kapan digunakan
Ideal untuk menghasilkan satu file HTML mandiri yang dapat dilampirkan pada email.

## 9. Menyelesaikan Nama Font
Memastikan bahwa HTML merujuk pada keluarga font yang tepat, meningkatkan konsistensi lintas platform.

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

### Mengapa ini membantu
Jika dokumen asli menggunakan font yang tidak terpasang di mesin klien, opsi ini menggantinya dengan alternatif web‑safe.

## 10. Mengekspor Formulir Input Teks sebagai Teks
Render bidang formulir sebagai teks biasa alih‑alih elemen input HTML interaktif.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// The folder specified needs to exist and should be empty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Set an option to export form fields as plain text, not as HTML input elements.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

### Kasus Penggunaan
Ketika Anda membutuhkan representasi hanya‑baca dari formulir untuk tujuan arsip atau pencetakan.

## Kesalahan Umum & Pemecahan Masalah
| Masalah | Penyebab Umum | Perbaikan |
|-------|---------------|-----|
| Font yang hilang dalam output | `exportFontsAsBase64` tidak diaktifkan | Setel `setExportFontsAsBase64(true)` |
| CSS rusak setelah penyematan | Menggunakan `EXTERNAL` tanpa menyediakan file CSS | Pastikan file CSS ditempatkan pada `resourceFolderAlias` yang ditentukan |
| Ukuran HTML besar | Menyematkan banyak gambar sebagai Base64 | Beralih ke sumber daya gambar eksternal melalui `setExportFontResources(true)` dan konfigurasikan `resourceFolder` |
| SVG tidak terrender di peramban lama | Peramban tidak mendukung SVG | Sediakan PNG cadangan dengan juga mengekspor sebagai EMF/WMF |

## Pertanyaan yang Sering Diajukan

**Q:** Apakah saya dapat menyematkan font sebagai Base64 dan tetap mempertahankan CSS eksternal?  
**A:** Ya. Setel `exportFontsAsBase64(true)` sambil mempertahankan `CssStyleSheetType.EXTERNAL` untuk memisahkan data font dari aturan gaya.

**Q:** Bagaimana cara mengonversi HTML yang ada kembali ke dokumen Word?  
**A:** Muat HTML dengan `Document doc = new Document("input.html");` lalu `doc.save("output.docx");`. Pertahankan data round‑trip menggunakan `exportRoundtripInformation` selama ekspor awal.

**Q:** Apakah ada dampak kinerja saat menggunakan konversi SVG?  
**A:** Mengonversi metafile besar ke SVG dapat meningkatkan waktu pemrosesan, namun HTML yang dihasilkan biasanya lebih kecil dan merender lebih cepat di peramban.

**Q:** Apakah opsi ini juga bekerja dengan Aspose.Words untuk .NET?  
**A:** Konsep yang sama ada di API .NET, meskipun nama metode mungkin sedikit berbeda (misalnya, `HtmlSaveOptions` dibagi di seluruh platform).

**Q:** Opsi mana yang harus saya pilih untuk HTML yang ramah email?  
**A:** Gunakan `SaveFormat.MHTML` dengan `exportCidUrlsForMhtmlResources` untuk menyematkan semua sumber daya langsung di dalam badan email.

---

**Terakhir Diperbarui:** 2025-12-19  
**Diuji Dengan:** Aspose.Words for Java 24.12  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}