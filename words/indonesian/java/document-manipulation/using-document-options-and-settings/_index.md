---
date: 2026-01-16
description: Pelajari cara menyoroti kesalahan ejaan di Word menggunakan Aspose.Words
  untuk Java, dan temukan cara mengatur karakter per baris, menyesuaikan opsi tampilan,
  serta membersihkan gaya.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Sorot Kesalahan Ejaan di Word dengan Aspose.Words Java
url: /id/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menggunakan Opsi Dokumen dan Pengaturan di Aspose.Words untuk Java

## Pendahuluan tentang Menggunakan Opsi Dokumen dan Pengaturan di Aspose.Words untuk Java

Dalam panduan komprehensif ini, Anda akan belajar **cara menyorot kesalahan ejaan di Word** menggunakan Aspose.Words untuk Java sekaligus menguasai pengaturan terkait seperti opsi tampilan, tata letak halaman, dan pembersihan gaya. Baik Anda seorang pengembang berpengalaman maupun yang baru memulai, contoh-contoh di bawah ini akan membantu Anda membuat dokumen yang kuat dan sadar kesalahan yang berfungsi di semua versi Word.

## Jawaban Cepat
- **Bagaimana cara menyorot kesalahan ejaan di Word?** Gunakan `setShowSpellingErrors(true)` pada objek `Document`.  
- **Apakah saya juga dapat menampilkan kesalahan tata bahasa?** Ya—panggil `setShowGrammaticalErrors(true)`.  
- **Metode apa yang mengatur karakter per baris?** `getPageSetup().setCharactersPerLine(int)`.  
- **API mana yang mengoptimalkan untuk versi Word tertentu?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Apakah ada cara untuk membersihkan gaya yang tidak terpakai?** Gunakan `CleanupOptions` dengan `setUnusedStyles(true)` dan panggil `doc.cleanup(options)`.

## Cara Menyorot Kesalahan Ejaan di Word?

Aspose.Words memudahkan mengaktifkan penyorotan kesalahan ejaan. Ketika dokumen dibuka di Microsoft Word, kata yang salah eja akan muncul dengan garis bawah merah yang familiar, membantu pengguna akhir menemukan masalah secara langsung.

## Cara Mengatur Karakter per Baris

Mengontrol jumlah karakter per baris penting untuk tata letak lebar tetap (mis., daftar kode atau formulir lama). Kelas `PageSetup` menyediakan `setCharactersPerLine(int)` yang memungkinkan Anda menentukan nilai ini secara tepat.

## Cara Menampilkan Kesalahan Tata Bahasa

Selain ejaan, Anda juga dapat mengaktifkan tampilan kesalahan tata bahasa. Ini berguna untuk menyusun konten yang harus mengikuti panduan gaya atau untuk membuat alat proofreading.

## Optimizing Documents for Compatibility

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

Salah satu aspek penting dalam manajemen dokumen adalah memastikan kompatibilitas dengan berbagai versi Microsoft Word. Aspose.Words untuk Java menyediakan cara sederhana untuk mengoptimalkan dokumen bagi versi Word tertentu. Pada contoh di atas, kami mengoptimalkan dokumen untuk Word 2016, memastikan kompatibilitas yang mulus.

## Identifying Grammatical and Spelling Errors

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

Ketelitian sangat penting saat menangani dokumen. Aspose.Words untuk Java memungkinkan Anda menyorot kesalahan tata bahasa dan ejaan dalam dokumen, membuat proses proofreading dan penyuntingan lebih efisien.

## Cleaning Up Unused Styles and Lists

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

Mengelola gaya dan daftar dokumen secara efisien penting untuk menjaga konsistensi dokumen. Aspose.Words untuk Java memungkinkan Anda membersihkan gaya dan daftar yang tidak terpakai, memastikan struktur dokumen yang ramping dan terorganisir.

## Removing Duplicate Styles

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

Gaya duplikat dapat menyebabkan kebingungan dan inkonsistensi dalam dokumen Anda. Dengan Aspose.Words untuk Java, Anda dapat dengan mudah menghapus gaya duplikat, menjaga kejelasan dan koherensi dokumen.

## Customizing Document Viewing Options

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

Menyesuaikan pengalaman tampilan dokumen Anda sangat penting. Aspose.Words untuk Java memungkinkan Anda mengatur berbagai opsi tampilan, seperti tata letak halaman dan persentase zoom, untuk meningkatkan keterbacaan dokumen.

## Configuring Document Page Setup

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

Pengaturan halaman yang tepat penting untuk pemformatan dokumen. Aspose.Words untuk Java memberi Anda kemampuan untuk mengatur mode tata letak, **karakter per baris**, dan baris per halaman, memastikan dokumen Anda tampak menarik secara visual.

## Setting Editing Languages

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

Bahasa penyuntingan memainkan peran penting dalam pemrosesan dokumen. Dengan Aspose.Words untuk Java, Anda dapat mengatur dan menyesuaikan bahasa penyuntingan sesuai kebutuhan linguistik dokumen Anda.

## Kesimpulan

Dalam panduan ini, kami telah menelusuri berbagai opsi dokumen dan pengaturan yang tersedia di Aspose.Words untuk Java. Mulai dari optimisasi dan tampilan kesalahan hingga pembersihan gaya dan opsi tampilan, perpustakaan yang kuat ini menawarkan kemampuan luas untuk mengelola dan menyesuaikan dokumen Anda.

## FAQ

### Bagaimana cara mengoptimalkan dokumen untuk versi Word tertentu?

Untuk mengoptimalkan dokumen bagi versi Word tertentu, gunakan metode `optimizeFor` dan tentukan versi yang diinginkan. Misalnya, untuk mengoptimalkan bagi Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### Bagaimana cara menyorot kesalahan tata bahasa dan ejaan dalam dokumen?

Anda dapat mengaktifkan tampilan kesalahan tata bahasa dan ejaan dalam dokumen dengan kode berikut:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### Apa tujuan membersihkan gaya dan daftar yang tidak terpakai?

Membersihkan gaya dan daftar yang tidak terpakai membantu menjaga struktur dokumen yang bersih dan terorganisir. Ini menghilangkan kekacauan yang tidak perlu, meningkatkan keterbacaan dan konsistensi dokumen.

### Bagaimana cara menghapus gaya duplikat dari dokumen?

Untuk menghapus gaya duplikat dari dokumen, gunakan metode `cleanup` dengan opsi `duplicateStyle` diatur ke `true`. Berikut contohnya:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### Bagaimana cara menyesuaikan opsi tampilan untuk dokumen?

Anda dapat menyesuaikan opsi tampilan dokumen menggunakan kelas `ViewOptions`. Misalnya, untuk mengatur tipe tampilan ke tata letak halaman dan zoom ke 50%:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Tips Tambahan & Kesalahan Umum
- **Aktifkan pemeriksaan ejaan dan tata bahasa sekaligus** ketika Anda memerlukan proofreading yang komprehensif. Lupa mengatur salah satu flag (`setShowGrammaticalErrors` atau `setShowSpellingErrors`) dapat membuat kesalahan tidak terdeteksi.
- **Saat mengatur karakter per baris**, ingat bahwa nilai tersebut berinteraksi dengan font yang dipilih dan margin halaman. Uji dengan tata letak dokumen sebenarnya untuk menghindari pemutusan baris yang tidak terduga.
- **Operasi pembersihan tidak dapat dibatalkan** pada file asli. Selalu bekerja pada salinan atau gunakan kontrol versi untuk menjaga gaya asli.
- **Preferensi bahasa penyuntingan** memengaruhi perilaku pemeriksaan ejaan. Jika Anda menargetkan dokumen multibahasa, tambahkan semua bahasa yang relevan ke `LanguagePreferences`.

---

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}