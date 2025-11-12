---
date: '2025-11-12'
description: Pelajari cara menggunakan LayoutCollector dan LayoutEnumerator Aspose.Words
  untuk Java untuk menentukan rentang halaman, menelusuri entitas tata letak, dan
  memulai kembali penomoran halaman pada bagian berkelanjutan.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- determine page span
- analyze document pagination
- restart page numbering
language: id
title: 'Aspose.Words Java: Panduan LayoutCollector & LayoutEnumerator'
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java: Panduan LayoutCollector & LayoutEnumerator

## Pendahuluan  

Apakah Anda kesulitan **menentukan rentang halaman**, menganalisis pagination, atau memulai kembali penomoran halaman pada dokumen Java yang kompleks? Dengan **Aspose.Words for Java**, Anda dapat menyelesaikan masalah ini dengan cepat menggunakan `LayoutCollector` dan `LayoutEnumerator`. Dalam panduan ini kami akan menunjukkan **cara menggunakan LayoutCollector**, **cara menelusuri LayoutEnumerator**, dan cara mengontrol penomoran halaman pada section berkelanjutan—semua dengan contoh kode langkah‑demi‑langkah yang dapat Anda jalankan hari ini.

Anda akan belajar untuk:

1. Menggunakan `LayoutCollector` untuk **menentukan rentang halaman** dari node apa pun.  
2. **Menelusuri entitas layout** dengan `LayoutEnumerator`.  
3. Menerapkan callback layout untuk rendering dinamis.  
4. **Memulai kembali penomoran halaman** pada section berkelanjutan.  

Mari kita mulai dengan memastikan lingkungan Anda siap.

## Prasyarat  

### Perpustakaan yang Diperlukan  

> **Catatan:** Kode ini bekerja dengan rilis terbaru Aspose.Words for Java (tidak perlu menyebutkan nomor versi).  

**Maven**

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>latest</version>
</dependency>
```

**Gradle**

```gradle
implementation 'com.aspose:aspose-words:latest'
```

### Lingkungan  

- JDK 17 atau lebih baru.  
- IntelliJ IDEA, Eclipse, atau IDE Java lain yang Anda sukai.  

### Pengetahuan  

Pemahaman dasar tentang sintaks Java dan konsep pemrograman berorientasi objek akan membantu Anda mengikuti contoh.

## Menyiapkan Aspose.Words  

Pertama, tambahkan perpustakaan Aspose.Words ke proyek Anda dan terapkan lisensi (atau gunakan versi trial). Potongan kode berikut menunjukkan cara memuat lisensi dan memastikan perpustakaan siap digunakan:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file (skip this line for a trial)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

> **Tip:** Simpan file lisensi di luar kontrol versi untuk melindungi kredensial Anda.

Sekarang kita dapat menyelami dua fitur inti.

## 1. Cara Menggunakan LayoutCollector untuk Analisis Rentang Halaman  

`LayoutCollector` memungkinkan Anda **menentukan rentang halaman** untuk node apa pun dalam dokumen, yang penting untuk analisis pagination.

### Implementasi Langkah‑demi‑Langkah  

1. **Buat Document baru dan instance LayoutCollector.**  
2. **Tambahkan konten yang melintasi beberapa halaman.**  
3. **Segarkan layout dan query metrik rentang halaman.**  

```java
// 1. Initialize Document and LayoutCollector
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);

// 2. Populate the Document with multi‑page content
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);

// 3. Update layout and retrieve page‑span information
layoutCollector.clear();          // Reset any previous state
doc.updatePageLayout();           // Force layout calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected number of pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Penjelasan**

- `DocumentBuilder` menyisipkan teks dan pemisah, menciptakan dokumen yang secara alami melintasi beberapa halaman.  
- `updatePageLayout()` memaksa Aspose.Words menghitung layout, memastikan nomor halaman yang akurat.  
- `getNumPagesSpanned()` mengembalikan total halaman yang dicakup oleh node yang diberikan (di sini seluruh dokumen).

## 2. Cara Menelusuri LayoutEnumerator  

`LayoutEnumerator` menyediakan **tampilan terstruktur dari entitas layout** (halaman, paragraf, run, dll.) dan memungkinkan Anda bergerak maju atau mundur di antara mereka.

### Implementasi Langkah‑demi‑Langkah  

1. Muat dokumen yang sudah ada yang berisi entitas layout.  
2. Buat instance `LayoutEnumerator`.  
3. Pindah ke level halaman, lalu telusuri maju dan mundur menggunakan metode pembantu.

```java
// 1. Load the document containing layout entities
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");

// 2. Initialize LayoutEnumerator
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);

// 3. Position the enumerator at the page level
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Forward traversal
traverseLayoutForward(layoutEnumerator, 1);

// Backward traversal
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Catatan:** Metode `traverseLayoutForward` dan `traverseLayoutBackward` adalah pembantu rekursif yang menelusuri pohon layout. Anda dapat menyesuaikannya untuk mengumpulkan informasi seperti bounding box, detail font, atau metadata khusus.

## 3. Cara Menerapkan Callback Layout Halaman  

Terkadang Anda perlu merespons peristiwa layout—misalnya, ketika sebuah section selesai di‑reflow atau ketika konversi ke format lain selesai. Implementasikan antarmuka `IPageLayoutCallback` untuk menerima notifikasi ini.

### Implementasi Langkah‑demi‑Langkah  

1. Tetapkan instance callback pada opsi layout dokumen.  
2. Definisikan logika callback untuk menangani peristiwa `PART_REFLOW_FINISHED` dan `CONVERSION_FINISHED`.  

```java
// 1. Register the callback
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();   // Triggers the callback during layout processing

// 2. Callback implementation
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs args) throws Exception {
        if (args.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            renderPage(args, args.getPageIndex());
        } else if (args.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            System.out.println("Document conversion finished.");
        }
    }

    private void renderPage(PageLayoutCallbackArgs args, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            args.getDocument().save(stream, saveOptions);
        }
    }
}
```

**Penjelasan**

- `notify()` menerima setiap peristiwa layout. Kami menyaring peristiwa yang relevan.  
- Ketika sebuah bagian selesai di‑reflow, `renderPage()` menyimpan halaman tersebut sebagai gambar PNG.  

## 4. Cara Memulai Kembali Penomoran Halaman pada Section Berkelanjutan  

Ketika sebuah dokumen berisi section berkelanjutan, Anda mungkin ingin nomor halaman dimulai kembali hanya pada halaman baru. Aspose.Words memungkinkan Anda mengontrol ini dengan `ContinuousSectionRestart`.

### Implementasi Langkah‑demi‑Langkah  

1. Muat dokumen target.  
2. Atur opsi `ContinuousSectionPageNumberingRestart`.  
3. Segarkan layout untuk menerapkan perubahan.

```java
// 1. Load the multi‑section document
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");

// 2. Configure page‑numbering restart behavior
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);

// 3. Update layout to reflect the new numbering scheme
doc.updatePageLayout();
System.out.println("Page numbering restart configured for continuous sections.");
```

**Penjelasan**

- `FROM_NEW_PAGE_ONLY` memberi tahu Aspose.Words untuk memulai kembali penomoran hanya ketika halaman fisik baru muncul, menjaga alur yang mulus di seluruh section berkelanjutan.

## Aplikasi Praktis  

| Skenario | Fitur yang Digunakan | Manfaat |
|----------|----------------------|---------|
| **Audit pagination dokumen** | `LayoutCollector` | Dengan cepat menemukan section yang melampaui batas halaman. |
| **Render PDF dengan kesetiaan visual tepat** | `LayoutEnumerator` + callbacks | Mengakses detail layout untuk rendering yang presisi. |
| **Otomatisasi penyisipan watermark setelah setiap layout halaman** | Callback layout halaman | Merespons secara instan ketika sebuah halaman selesai di‑layout. |
| **Membuat laporan multi‑section dengan penomoran khusus** | Restart section berkelanjutan | Mempertahankan penomoran halaman profesional tanpa edit manual. |

## Tips Kinerja  

- **Buang node yang tidak terpakai** sebelum memanggil `updatePageLayout()` untuk menjaga penggunaan memori tetap rendah.  
- **Gunakan satu LayoutCollector** untuk banyak query alih‑alih membuatnya berulang kali.  
- **Batasi kedalaman rekursi** pada pembantu penelusuran untuk menghindari stack overflow pada dokumen yang sangat besar.  

## Kesimpulan  

Dengan menguasai **cara menggunakan LayoutCollector**, **cara menelusuri LayoutEnumerator**, dan **cara memulai kembali penomoran halaman**, Anda kini memiliki kotak peralatan yang kuat untuk pemrosesan teks tingkat lanjut dengan Aspose.Words for Java. Teknik‑teknik ini memungkinkan Anda **menentukan rentang halaman**, **menganalisis pagination dokumen**, dan **mengontrol perilaku layout** dengan percaya diri. Terapkan pada laporan, e‑book, atau alur kerja dokumen otomatis apa pun, dan Anda akan melihat peningkatan signifikan dalam akurasi serta produktivitas.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}