---
date: '2026-01-14'
description: Pelajari cara memulai kembali penomoran halaman dengan Aspose.Words Java
  dan gunakan LayoutCollector untuk mengekstrak data paginasi, memperbarui tata letak
  halaman, serta merender halaman sebagai gambar.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
title: Mulai Ulang Penomoran Halaman dengan Aspose.Words Java – LayoutCollector &
  LayoutEnumerator
url: /id/java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Memulai Ulang Penomoran Halaman dengan Aspose.Words Java – LayoutCollector & LayoutEnumerator

## Pendahuluan

Apakah Anda kesulitan **memulai ulang penomoran halaman** dalam dokumen Java yang besar sekaligus perlu menganalisis paginasi atau menampilkan halaman sebagai gambar? Dengan **Aspose.Words for Java**, Anda dapat memanfaatkan `LayoutCollector` dan `LayoutEnumerator` tidak hanya untuk memulai ulang penomoran halaman tetapi juga **mengekstrak data paginasi**, **memperbarui tata letak halaman**, dan **menampilkan halaman sebagai gambar** untuk pratinjau atau PDF. Panduan ini akan membawa Anda melalui setiap langkah, mulai dari menyiapkan pustaka hingga mengimplementasikan callback yang memberi Anda kontrol penuh atas rendering dokumen.

**Apa yang akan Anda pelajari**
- Cara menggunakan `LayoutCollector` untuk mengekstrak data paginasi dan menentukan rentang halaman.
- Menelusuri tata letak dokumen dengan `LayoutEnumerator`.
- Mengimplementasikan callback tata letak halaman untuk **menampilkan halaman sebagai gambar**.
- **Memulai ulang penomoran halaman** dalam bagian berkelanjutan menggunakan opsi tata letak.
- Tips untuk **memperbarui tata letak halaman** secara efisien.

## Jawaban Cepat
- **Bagaimana cara memulai ulang penomoran halaman dalam dokumen Java?** Gunakan `doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(...)` dan panggil `doc.updatePageLayout()`.
- **Kelas mana yang mengekstrak data paginasi?** `LayoutCollector` menyediakan indeks halaman mulai/akhir untuk setiap node.
- **Bisakah saya menampilkan setiap halaman sebagai gambar?** Ya—implementasikan `IPageLayoutCallback` dan gunakan `ImageSaveOptions`.
- **Apakah saya perlu memanggil update page layout secara manual?** Setelah mengubah opsi tata letak, selalu panggil `doc.updatePageLayout()`.
- **Versi Aspose.Words apa yang diperlukan?** Contoh-contoh ini bekerja dengan Aspose.Words for Java 25.3 (atau lebih baru).

## Apa itu memulai ulang penomoran halaman?

Memulai ulang penomoran halaman memungkinkan Anda memulai urutan penomoran baru di bagian tertentu dari dokumen, yang penting untuk laporan, buku, atau kontrak yang memerlukan penomoran terpisah untuk bab atau lampiran. Aspose.Words menyediakan opsi tata letak yang memungkinkan Anda mengontrol perilaku ini tanpa trik pemisah halaman manual.

## Mengapa menggunakan LayoutCollector dan LayoutEnumerator?

- **LayoutCollector** memberi Anda akses programatik ke detail paginasi, memungkinkan Anda untuk **mengekstrak data paginasi** seperti halaman pertama dan terakhir dari setiap node.
- **LayoutEnumerator** memungkinkan Anda menjelajahi pohon tata letak visual, memudahkan menemukan halaman, paragraf, atau baris untuk rendering atau analisis khusus.
- Bersama-sama mereka menyederhanakan tugas tata letak yang kompleks yang sebaliknya memerlukan konversi PDF yang mahal atau perhitungan manual.

## Prasyarat

### Perpustakaan dan Versi yang Diperlukan
Pastikan Anda memiliki Aspose.Words for Java versi 25.3 (atau lebih baru) terpasang.

**Maven:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Persyaratan Penyiapan Lingkungan
- Java Development Kit (JDK) terpasang.
- IntelliJ IDEA, Eclipse, atau IDE Java pilihan Anda.
- Lisensi Aspose.Words yang valid (versi percobaan gratis dapat digunakan untuk evaluasi).

### Prasyarat Pengetahuan
Pengetahuan dasar pemrograman Java sudah cukup.

## Menyiapkan Aspose.Words
Pertama, integrasikan pustaka Aspose.Words ke dalam proyek Anda. Anda dapat memperoleh lisensi percobaan gratis [di sini](https://releases.aspose.com/words/java/) atau menggunakan lisensi sementara untuk pengujian.

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Set up the license (if available)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

Dengan pustaka siap, kita dapat menyelami fitur inti.

## Panduan Implementasi

### Fitur 1: Menggunakan LayoutCollector untuk Analisis Rentang Halaman
Fitur `LayoutCollector` memungkinkan Anda menentukan bagaimana node tersebar di halaman, yang merupakan dasar untuk **mengekstrak data paginasi**.

#### Ikhtisar
Dengan memanfaatkan `LayoutCollector`, Anda dapat mengambil indeks halaman mulai dan akhir dari setiap node serta menghitung total halaman yang ditempati.

#### Langkah-Langkah Implementasi

**1. Inisialisasi Document dan LayoutCollector**
```java
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

**2. Isi Document**
Di sini, kami akan menambahkan konten yang melintasi beberapa halaman:
```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

**3. Perbarui Layout dan Dapatkan Metrik**
```java
layoutCollector.clear();
doc.updatePageLayout();

assert layoutCollector.getNumPagesSpanned(doc) == 5;
```

#### Penjelasan
- **`DocumentBuilder`** menyisipkan teks serta pemisah halaman/bagian.
- **`updatePageLayout()`** menghitung ulang informasi tata letak sehingga data paginasi akurat.

### Fitur 2: Menelusuri dengan LayoutEnumerator
`LayoutEnumerator` memungkinkan penelusuran efisien melalui pohon tata letak visual.

#### Ikhtisar
Anda dapat menjelajahi halaman, paragraf, baris, dan entitas tata letak lainnya, yang berguna untuk rendering khusus atau diagnostik.

#### Langkah-Langkah Implementasi

**1. Inisialisasi Document dan LayoutEnumerator**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

**2. Menelusuri Maju dan Mundur**
```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Traverse forward
traverseLayoutForward(layoutEnumerator, 1);

// Traverse backward
traverseLayoutBackward(layoutEnumerator, 1);
```

#### Penjelasan
- **`moveParent()`** memindahkan enumerator ke entitas induk (dalam hal ini, tingkat halaman).
- Metode penelusuran rekursif memungkinkan Anda menjelajahi seluruh hierarki tata letak.

### Fitur 3: Callback Tata Letak Halaman
Implementasikan callback untuk memantau peristiwa tata letak dan **menampilkan halaman sebagai gambar** bila diperlukan.

#### Ikhtisar
Antarmuka `IPageLayoutCallback` memberi tahu Anda ketika bagian dokumen selesai di‑reflow atau ketika konversi selesai.

#### Langkah-Langkah Implementasi

**1. Atur Callback**
```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();
```

**2. Implementasikan Metode Callback**
```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream("YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }
}
```

#### Penjelasan
- **`notify()`** bereaksi terhadap peristiwa tata letak.
- **`ImageSaveOptions`** bersama dengan `PageSet` memungkinkan Anda **menampilkan halaman sebagai gambar** (PNG dalam contoh ini).

### Fitur 4: Memulai Ulang Penomoran Halaman dalam Bagian Berkelanjutan
Kontrol penomoran halaman ketika Anda memiliki beberapa bagian yang mengalir secara kontinu.

#### Ikhtisar
Dengan mengatur opsi `ContinuousSectionRestart`, Anda dapat memutuskan apakah nomor halaman dimulai ulang pada halaman baru atau berlanjut tanpa gangguan.

#### Langkah-Langkah Implementasi

**1. Muat Document**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

**2. Konfigurasikan Opsi Penomoran Halaman**
```java
doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();
```

#### Penjelasan
- **`setContinuousSectionPageNumberingRestart()`** memberi tahu Aspose.Words cara menangani penomoran dalam bagian berkelanjutan.
- Setelah mengubah opsi, **perbarui tata letak halaman** untuk menerapkan perubahan.

## Aplikasi Praktis
1. **Analisis Paginasi Dokumen** – Gunakan `LayoutCollector` untuk mengaudit bagaimana konten tersebar di halaman dan sesuaikan margin atau pemisah sesuai kebutuhan.
2. **Rendering PDF** – Gabungkan `LayoutEnumerator` dengan callback untuk menghasilkan gambar halaman berkualitas tinggi sebelum konversi PDF.
3. **Pembaruan Dokumen Dinamis** – Tanggapi peristiwa tata letak (mis., setelah tabel diperluas) dan secara otomatis render ulang halaman yang terpengaruh.
4. **Laporan Multi‑Bagian** – Terapkan **restart penomoran halaman** untuk memberi setiap bab skema penomoran sendiri sambil mempertahankan aliran kontinu.

## Pertimbangan Kinerja
- Hapus bagian yang tidak terpakai atau konten tersembunyi sebelum memanggil `updatePageLayout()` untuk menjaga proses tetap cepat.
- Gunakan API streaming untuk dokumen besar agar tidak memuat seluruh file ke memori.
- Batasi kedalaman penelusuran rekursif di `LayoutEnumerator` jika Anda hanya memerlukan informasi tingkat halaman.

## Masalah Umum dan Solusinya
| Masalah | Penyebab | Solusi |
|-------|-------|-----|
| `layoutCollector.getNumPagesSpanned()` returns 0 | Layout belum diperbarui | Panggil `doc.updatePageLayout()` sebelum melakukan query |
| Gambar tidak dihasilkan dalam callback | Konfigurasi `ImageSaveOptions` tidak ada | Pastikan `saveOptions.setPageSet(new PageSet(pageIndex))` telah diatur |
| Nomor halaman tidak restart | Nilai `ContinuousSectionRestart` salah | Gunakan `ContinuousSectionRestart.FROM_NEW_PAGE_ONLY` untuk restart yang sesungguhnya |

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya mengekstrak nomor halaman tepat dari paragraf tertentu?**  
A: Ya—gunakan `LayoutCollector` untuk mendapatkan halaman mulai dari node paragraf dan kemudian panggil `doc.updatePageLayout()` untuk memastikan data terkini.

**Q: Apakah `update page layout` memengaruhi konten dokumen?**  
A: Tidak. Itu hanya menghitung ulang informasi tata letak; teks dan pemformatan sebenarnya tetap tidak berubah.

**Q: Bagaimana cara menampilkan semua halaman dokumen besar sebagai gambar secara efisien?**  
A: Implementasikan `IPageLayoutCallback` dan proses setiap halaman secara berurutan, opsional menggunakan multi‑threading untuk penyimpanan I/O‑bound.

**Q: Apakah memungkinkan untuk memulai ulang penomoran hanya untuk bagian tertentu?**  
A: Ya—terapkan `setContinuousSectionPageNumberingRestart` pada opsi tata letak bagian spesifik sebelum memanggil `updatePageLayout()`.

**Q: Versi Aspose.Words mana yang memperkenalkan `LayoutCollector`?**  
A: `LayoutCollector` telah tersedia sejak rilis awal 2020; contoh-contoh menggunakan versi 25.3.

## Kesimpulan
Dengan menguasai **restart penomoran halaman**, `LayoutCollector`, dan `LayoutEnumerator`, Anda kini memiliki toolkit yang kuat untuk pemrosesan teks tingkat lanjut di Aspose.Words for Java. Baik Anda perlu **mengekstrak data paginasi**, **menampilkan halaman sebagai gambar**, atau sekadar mengontrol penomoran halaman antar bagian, API ini memberi Anda kontrol yang tepat dan programatik sambil menjaga kinerja tetap tinggi.

---

**Terakhir Diperbarui:** 2026-01-14  
**Diuji Dengan:** Aspose.Words for Java 25.3  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}