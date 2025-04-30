---
"date": "2025-03-28"
"description": "Pelajari cara menguasai deteksi daftar, penanganan teks, dan banyak lagi menggunakan Aspose.Words untuk Java. Panduan ini mencakup pendeteksian daftar yang dipisahkan oleh spasi, pemangkasan spasi, penentuan arah dokumen, penonaktifan deteksi penomoran otomatis, dan pengelolaan hyperlink."
"title": "Deteksi Daftar Induk & Penanganan Teks di Java dengan Aspose.Words&#58; Panduan Lengkap"
"url": "/id/java/tables-lists/java-aspose-words-list-detection-text-handling/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Deteksi Daftar Induk & Penanganan Teks di Java dengan Aspose.Words: Panduan Lengkap

## Perkenalan

Bekerja dengan dokumen teks biasa sering kali menghadirkan tantangan dalam mengidentifikasi data terstruktur seperti daftar karena pembatas yang tidak konsisten dan masalah pemformatan. Pustaka Aspose.Words untuk Java menyediakan fitur-fitur yang tangguh untuk mengatasi masalah ini, termasuk mendeteksi penomoran dengan spasi, memangkas spasi, menentukan arah dokumen, menonaktifkan deteksi penomoran otomatis, dan mengelola hyperlink dalam dokumen teks. Tutorial ini memberdayakan Anda untuk memanipulasi data tekstual secara efektif menggunakan Aspose.Words.

**Apa yang Akan Anda Pelajari:**
- Teknik untuk mendeteksi daftar yang dipisahkan oleh spasi
- Metode untuk memangkas spasi yang tidak diinginkan dari konten dokumen
- Pendekatan untuk memastikan arah pembacaan file teks
- Cara menonaktifkan deteksi penomoran otomatis
- Strategi untuk mendeteksi dan mengelola hyperlink dalam dokumen teks biasa

Mari kita tinjau prasyarat yang diperlukan sebelum menerapkan fitur-fitur ini.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

### Pustaka yang dibutuhkan:
- **Aspose.Words untuk Java**: Versi 25.3 atau yang lebih baru.

### Pengaturan Lingkungan:
- Pastikan lingkungan pengembangan Anda mendukung Maven atau Gradle, karena keduanya diperlukan untuk mengelola dependensi.

### Prasyarat Pengetahuan:
- Pemahaman dasar tentang pemrograman Java
- Keakraban dengan sistem build Maven atau Gradle

## Menyiapkan Aspose.Words

Untuk mulai menggunakan Aspose.Words untuk Java dalam proyek Anda, Anda perlu menyertakan dependensi yang diperlukan. Berikut caranya:

**Pakar:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradasi:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Akuisisi Lisensi

Untuk memanfaatkan Aspose.Words sepenuhnya, pertimbangkan untuk mendapatkan lisensi:
- **Uji Coba Gratis**: Tersedia untuk menguji fitur.
- **Lisensi Sementara**: Untuk tujuan evaluasi tanpa batasan.
- **Pembelian**: Lisensi penuh untuk penggunaan berkelanjutan.

Setelah Anda memperoleh lisensi, inisialisasikan dalam aplikasi Anda untuk membuka semua fungsi perpustakaan.

## Panduan Implementasi

Mari kita uraikan setiap fitur dan lihat cara mengimplementasikannya menggunakan Aspose.Words untuk Java.

### Mendeteksi Penomoran dengan Spasi Putih

**Ringkasan:** Fitur ini memungkinkan Anda mengidentifikasi daftar dalam dokumen teks biasa yang menggunakan spasi sebagai pemisah.

#### Langkah 1: Muat Dokumen
```java
import com.aspose.words.*;

final String TEXT_DOC = "Full stop delimiters:\n" +
    // ...
    "3 Fourth list item 3";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDetectNumberingWithWhitespaces(true);
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
```

#### Langkah 2: Validasi Deteksi Daftar
```java
List<Paragraph> paragraphList = Arrays.stream(doc.getFirstSection().getBody().getParagraphs().toArray())
        .filter(Paragraph.class::isInstance)
        .map(Paragraph.class::cast)
        .collect(Collectors.toList());

boolean detectNumberingWithWhitespaces = true;
if (detectNumberingWithWhitespaces) {
    assert doc.getLists().getCount() == 4 : "Expected four lists.";
    boolean foundFourthList = paragraphList.stream()
        .anyMatch(p -> p.getText().contains("Fourth list") && p.isListItem());
    assert foundFourthList : "Expected to find a fourth list item detected as numbered.";
}
```

*Parameter dan Metode:*
- `setDetectNumberingWithWhitespaces(true)`: Mengonfigurasi parser untuk mengenali daftar dengan pemisah spasi.
- `doc.getLists().getCount()`: Mengambil jumlah daftar yang terdeteksi dalam dokumen.

### Pangkas Spasi Awal dan Akhir

**Ringkasan:** Fitur ini memangkas spasi yang tidak diperlukan di awal atau akhir baris dalam dokumen teks biasa, memastikan format teks yang bersih.

#### Langkah 1: Konfigurasikan Opsi Muat
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

String textDoc = "      Line 1 \n" +
    // ...
    " Line 3       ";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);

Document doc = new Document(new ByteArrayInputStream(textDoc.getBytes(StandardCharsets.US_ASCII)), loadOptions);
```

#### Langkah 2: Verifikasi Pemangkasan
```java
ParagraphCollection paragraphs = doc.getFirstSection().getBody().getParagraphs();
for (int i = 0; i < paragraphs.getCount(); i++) {
    Paragraph paragraph = paragraphs.get(i);
    String text = paragraph.getText();
    assert !text.startsWith(" ") : "Expected no leading spaces.";
    assert !text.endsWith(" ") : "Expected no trailing spaces.";
}
```

*Konfigurasi Utama:*
- `setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM)`: Memotong spasi dari awal baris.
- `setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM)`: Menghapus spasi di akhir baris.

### Deteksi Arah Dokumen

**Ringkasan:** Tentukan apakah suatu dokumen harus dibaca dari kanan ke kiri (RTL), seperti untuk teks Ibrani atau Arab.

#### Langkah 1: Atur Deteksi Otomatis
```java
TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDocumentDirection(DocumentDirection.AUTO);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Hebrew text.txt", loadOptions);

boolean isBidi = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat().isBidi();
assert isBidi : "Expected Hebrew text to be right-to-left.";
```

### Nonaktifkan Deteksi Penomoran Otomatis

**Ringkasan:** Cegah perpustakaan mendeteksi dan memformat item daftar secara otomatis.

#### Langkah 1: Konfigurasikan Opsi Muat
```java
TxtLoadOptions options = new TxtLoadOptions();
options.setAutoNumberingDetection(false);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Number detection.txt", options);

int listItemsCount = 0;
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true)) {
    if (paragraph.isListItem())
        listItemsCount++;
}
assert listItemsCount == 0 : "Expected no detected list items.";
```

### Mendeteksi Hyperlink dalam Teks

**Ringkasan:** Identifikasi dan kelola hyperlink dalam dokumen teks biasa.

#### Langkah 1: Atur Opsi Deteksi
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

final String INPUT_TEXT = "Some links in TXT:\n" +
    // ...
    "https://docs.aspose.com/words/net/";

try (ByteArrayInputStream stream = new ByteArrayInputStream(INPUT_TEXT.getBytes(StandardCharsets.US_ASCII))) {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    loadOptions.setDetectHyperlinks(true);
    Document doc = new Document(stream, loadOptions);

    String[] expectedLinks = {"https://www.aspose.com/", "https://docs.aspose.com/words/net/"};
    for (int i = 0; i < doc.getRange().getFields().getCount(); i++) {
        String result = doc.getRange().getFields().get(i).getResult().trim();
        assert result.equals(expectedLinks[i]) : "Expected hyperlink does not match.";
    }
}
```

## Aplikasi Praktis

1. **Sistem Manajemen Konten (CMS):** Format secara otomatis konten yang dibuat pengguna ke dalam daftar terstruktur.
2. **Alat Ekstraksi Data:** Gunakan deteksi daftar untuk mengatur data tidak terstruktur untuk analisis.
3. **Alur Pemrosesan Teks:** Meningkatkan praproses dokumen dengan memangkas spasi dan mendeteksi arah teks.

## Pertimbangan Kinerja

Untuk mengoptimalkan kinerja:
- Memuat dokumen dengan operasi minimal, dengan fokus pada fitur-fitur yang diperlukan.
- Kelola penggunaan memori dengan memproses dokumen besar dalam potongan-potongan jika memungkinkan.

## Kesimpulan

Dengan memanfaatkan Aspose.Words untuk Java, Anda dapat mengelola data tekstual dalam dokumen teks biasa secara efisien. Dari mendeteksi daftar yang dipisahkan oleh spasi hingga menangani arah teks dan hyperlink, alat-alat canggih ini memungkinkan manipulasi dokumen yang kuat. Untuk eksplorasi lebih lanjut, lihat [Dokumentasi Aspose.Words](https://reference.aspose.com/words/java/) atau coba uji coba gratis.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}