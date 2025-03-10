---
title: Opsi Penyimpanan Dokumen HTML Lanjutan dengan Aspose.Words Java
linktitle: Menyimpan Dokumen HTML dengan
second_title: API Pemrosesan Dokumen Java Aspose.Words
description: Dalam tutorial ini, kami telah membahas berbagai opsi penyimpanan dokumen HTML tingkat lanjut dengan Aspose.Words untuk Java. Opsi-opsi ini memberdayakan Anda untuk membuat HTML berkualitas tinggi
weight: 16
url: /id/java/document-loading-and-saving/advance-html-documents-saving-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Opsi Penyimpanan Dokumen HTML Lanjutan dengan Aspose.Words Java


Dalam tutorial ini, kita akan menjelajahi opsi penyimpanan dokumen HTML tingkat lanjut yang disediakan oleh Aspose.Words untuk Java. Aspose.Words adalah API Java yang hebat untuk bekerja dengan dokumen Word, dan menawarkan berbagai fitur untuk manipulasi dan konversi dokumen.

## 1. Pendahuluan
Aspose.Words untuk Java memungkinkan Anda bekerja dengan dokumen Word secara terprogram. Dalam tutorial ini, kami akan fokus pada opsi penyimpanan dokumen HTML tingkat lanjut, yang memungkinkan Anda mengontrol bagaimana dokumen Word diubah menjadi HTML.

## 2. Ekspor Informasi Perjalanan Pulang Pergi
 Itu`exportRoundtripInformation` Metode ini memungkinkan Anda mengekspor dokumen Word ke HTML sambil mempertahankan informasi perjalanan pulang pergi. Informasi ini dapat berguna saat Anda ingin mengonversi HTML kembali ke format Word tanpa kehilangan detail khusus dokumen apa pun.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Ekspor Font sebagai Base64
 Dengan`exportFontsAsBase64` Dengan metode ini, Anda dapat mengekspor font yang digunakan dalam dokumen sebagai data berkode Base64 dalam HTML. Ini memastikan bahwa representasi HTML mempertahankan gaya font yang sama seperti dokumen Word asli.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Ekspor Sumber Daya
 Itu`exportResources` Metode ini memungkinkan Anda menentukan jenis style sheet CSS dan mengekspor sumber daya font. Anda juga dapat mengatur folder sumber daya dan alias untuk sumber daya dalam HTML.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://contoh.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

## 5. Konversi Metafile ke EMF atau WMF
 Itu`convertMetafilesToEmfOrWmf`Metode ini memungkinkan Anda mengonversi metafile dalam dokumen ke dalam format EMF atau WMF, memastikan kompatibilitas dan kelancaran pemrosesan dalam HTML.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Titik merah\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Konversi Metafile ke SVG
 Gunakan`convertMetafilesToSvg` metode untuk mengonversi metafile ke format SVG. Format ini ideal untuk menampilkan grafik vektor dalam dokumen HTML.

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

## 7. Tambahkan Awalan Nama Kelas CSS
 Dengan`addCssClassNamePrefix` metode ini, Anda dapat menambahkan awalan ke nama kelas CSS dalam HTML yang diekspor. Ini membantu mencegah konflik dengan gaya yang ada.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Ekspor URL CID untuk Sumber Daya MHTML
 Itu`exportCidUrlsForMhtmlResources` Metode ini digunakan saat menyimpan dokumen dalam format MHTML. Metode ini memungkinkan ekspor URL Content-ID untuk sumber daya.

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

## 9. Mengatasi Nama Font
 Itu`resolveFontNames` Metode ini membantu mengatasi nama font saat menyimpan dokumen dalam format HTML, memastikan rendering yang konsisten di berbagai platform.

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

## 10. Ekspor Bidang Formulir Input Teks sebagai Teks
 Itu`exportTextInputFormFieldAsText`metode mengekspor bidang formulir sebagai teks biasa dalam HTML, membuatnya mudah dibaca dan diedit.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// Folder yang ditentukan harus ada dan harus kosong.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Tetapkan opsi untuk mengekspor bidang formulir sebagai teks biasa, bukan sebagai elemen input HTML.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Kesimpulan
Dalam tutorial ini, kami menjelajahi opsi penyimpanan dokumen HTML tingkat lanjut yang disediakan oleh Aspose.Words untuk Java. Opsi ini memberi Anda kendali yang lebih rinci atas proses konversi, yang memungkinkan Anda membuat dokumen HTML yang sangat mirip dengan dokumen Word asli.

## Pertanyaan yang Sering Diajukan
Berikut ini beberapa pertanyaan yang sering diajukan tentang penggunaan Aspose.Words untuk pilihan penyimpanan dokumen Java dan HTML:

### Q1: Bagaimana cara mengonversi kembali HTML ke format Word menggunakan Aspose.Words untuk Java?
 Untuk mengonversi HTML kembali ke format Word, Anda dapat menggunakan API Aspose.Words`load` metode untuk memuat dokumen HTML dan kemudian menyimpannya dalam format Word.

### Q2: Dapatkah saya menyesuaikan gaya CSS saat mengekspor ke HTML?
Ya, Anda dapat menyesuaikan gaya CSS dengan memodifikasi stylesheet yang digunakan dalam HTML atau dengan menggunakan`addCssClassNamePrefix` metode untuk menambahkan awalan ke nama kelas CSS.

### Q3: Apakah ada cara untuk mengoptimalkan keluaran HTML untuk tampilan web?
Ya, Anda dapat mengoptimalkan keluaran HTML untuk tampilan web dengan mengonfigurasi opsi seperti mengekspor font sebagai Base64 dan mengonversi metafile ke SVG.

### Q4: Apakah ada batasan saat mengonversi dokumen Word yang rumit ke HTML?
Sementara Aspose.Words untuk Java menyediakan kemampuan konversi yang hebat, dokumen Word yang rumit dengan tata letak yang rumit mungkin memerlukan pasca-pemrosesan tambahan untuk mencapai keluaran HTML yang diinginkan.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
