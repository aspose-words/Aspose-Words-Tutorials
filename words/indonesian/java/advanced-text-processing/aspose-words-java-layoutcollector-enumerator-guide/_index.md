---
date: '2025-11-12'
description: Pelajari cara menggunakan LayoutCollector dan LayoutEnumerator Aspose.Words
  untuk Java untuk menganalisis paginasi, menelusuri tata letak dokumen, menerapkan
  callback tata letak, dan memulai ulang penomoran halaman pada section berkelanjutan.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: id
title: Analisis Paginasi Java dengan Alat Tata Letak Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Analisis Paginasi Java dengan Alat Layout Aspose.Words

## Introduction  

Jika Anda perlu **menganalisis paginasi** atau **menelusuri layout dokumen** dalam aplikasi Java, Aspose.Words for Java menyediakan dua API kuat: **`LayoutCollector`** dan **`LayoutEnumerator`**. Kelas‑kelas ini memungkinkan Anda mengetahui berapa banyak halaman yang ditempati sebuah node, menjelajahi setiap entitas layout, merespon peristiwa layout, bahkan memulai ulang penomoran halaman pada section berkelanjutan. Dalam panduan ini kami akan membahas setiap fitur langkah demi langkah, menampilkan contoh kode dunia nyata, dan menjelaskan hasil yang diharapkan sehingga Anda dapat langsung mengaplikasikannya.

Anda akan belajar cara:

* **menggunakan LayoutCollector** untuk mendapatkan halaman mulai dan akhir dari node mana pun (use layoutcollector page span)  
* **menelusuri layout dokumen** dengan LayoutEnumerator (traverse document layout)  
* **mengimplementasikan callback layout** untuk merespon peristiwa paginasi (implement layout callback)  
* **memulai ulang penomoran halaman** pada section berkelanjutan (restart page numbering sections)  

Mari kita mulai.

## Prerequisites  

### Required Libraries  

| Build Tool | Dependency |
|------------|------------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **Catatan:** Nomor versi dipertahankan untuk kompatibilitas; kode ini bekerja dengan rilis Aspose.Words for Java terbaru apa pun.

### Environment  

* JDK 8 atau yang lebih baru  
* IDE seperti IntelliJ IDEA atau Eclipse  

### Knowledge  

Pemrograman Java dasar dan pemahaman tentang Maven/Gradle sudah cukup untuk mengikuti contoh‑contoh ini.

## Setting Up Aspose.Words  

Sebelum Anda dapat memanggil API layout apa pun, pustaka harus dilisensikan (atau digunakan dalam mode trial). Potongan kode di bawah ini menunjukkan inisialisasi minimal:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*Kode ini tidak mengubah dokumen apa pun; hanya menyiapkan lingkungan Aspose.*  

Sekarang kita dapat menyelami fitur‑fitur inti.

## Feature 1: Using **LayoutCollector** to Analyze Pagination  

`LayoutCollector` memetakan setiap node dalam `Document` ke halaman‑halaman yang ditempatinya. Ini adalah cara paling dapat diandalkan untuk **use layoutcollector page span** dalam analisis paginasi.

### Step‑by‑step implementation  

1. **Buat dokumen baru dan lampirkan LayoutCollector.**  
2. **Masukkan konten yang memaksa paginasi** (misalnya pemisah halaman, pemisah section).  
3. **Segarkan layout** dengan `updatePageLayout()`.  
4. **Query collector** untuk halaman mulai, halaman akhir, dan total halaman yang dicakup.

#### 1️⃣ Initialize Document and LayoutCollector  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ Populate the Document  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ Update Layout and Retrieve Metrics  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Expected output**

```
Document spans 5 pages.
```

> **Mengapa ini berhasil:** `updatePageLayout()` memaksa Aspose.Words menghitung ulang layout, sehingga `LayoutCollector` dapat melaporkan rentang halaman dengan akurat.

## Feature 2: Traversing Document Layout with **LayoutEnumerator**  

Ketika Anda perlu **traverse document layout** (misalnya untuk rendering khusus atau analisis), `LayoutEnumerator` menyediakan tampilan berbentuk pohon dari halaman, paragraf, baris, dan kata.

### Step‑by‑step implementation  

1. Muat dokumen yang sudah ada yang berisi entitas layout.  
2. Buat instance `LayoutEnumerator`.  
3. Pindah ke entitas root `PAGE`.  
4. Jelajahi layout maju dan mundur menggunakan metode bantu rekursif.

#### 1️⃣ Load Document and Create Enumerator  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

#### 2️⃣ Position on the Page Level  

```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);
```

#### 3️⃣ Forward Traversal (Depth‑First)  

```java
traverseLayoutForward(layoutEnumerator, 1);
```

#### 4️⃣ Backward Traversal  

```java
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Helper methods** (`traverseLayoutForward` / `traverseLayoutBackward`) diimplementasikan secara rekursif untuk mengunjungi setiap entitas anak dan mencetak tipe serta indeks halamannya. Anda dapat menyesuaikannya untuk mengumpulkan statistik, merender grafik, atau mengubah properti layout.

## Feature 3: Implementing **Layout Callbacks**  

Kadang‑kadang Anda perlu merespon saat Aspose.Words selesai menata bagian dokumen. Mengimplementasikan `IPageLayoutCallback` memungkinkan Anda **implement layout callback** seperti menyimpan setiap halaman sebagai gambar.

### Step‑by‑step implementation  

1. Tetapkan instance callback ke `LayoutOptions` dokumen.  
2. Di dalam callback, tangani peristiwa `PART_REFLOW_FINISHED` dan `CONVERSION_FINISHED`.  
3. Render halaman saat ini ke PNG menggunakan `ImageSaveOptions`.

#### 1️⃣ Register the Callback  

```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();                     // Triggers the callback events
```

#### 2️⃣ Callback Class  

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

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }

    // You can add custom logic here for partFinished / conversionFinished
}
```

**What happens:** Setiap kali bagian layout selesai di‑reflow, callback merender halaman tersebut ke file PNG, memberi Anda jejak visual proses paginasi.

## Feature 4: Restarting Page Numbering in **Continuous Sections**  

Ketika dokumen berisi section berkelanjutan, Anda mungkin ingin nomor halaman dimulai ulang hanya pada halaman fisik baru. Hal ini dicapai dengan pengaturan `ContinuousSectionRestart`.

### Step‑by‑step implementation  

1. Muat dokumen target.  
2. Ubah opsi `ContinuousSectionPageNumberingRestart`.  
3. Jalankan kembali `updatePageLayout()` untuk menerapkan perubahan.

#### 1️⃣ Load Document  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

#### 2️⃣ Configure Restart Behavior  

```java
doc.getLayoutOptions()
   .setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();            // Apply the new numbering rule
```

**Result:** Nomor halaman kini akan dimulai ulang hanya ketika halaman fisik baru dimulai, menjaga tampilan yang bersih dan profesional untuk laporan atau buku.

## Practical Applications  

| Scenario | Which API Helps | Benefit |
|----------|----------------|---------|
| **Audit kontrak panjang** | `LayoutCollector` | Dengan cepat menemukan klausul mana yang melintasi beberapa halaman. |
| **Rendering PDF khusus** | `LayoutEnumerator` | Menelusuri pohon layout untuk mengekspor setiap baris sebagai grafik vektor. |
| **Pratinjau dokumen secara langsung** | Layout callbacks | Menghasilkan gambar halaman secara dinamis saat pengguna mengedit konten. |
| **Laporan multi‑section** | Continuous section restart | Menjaga penomoran halaman tetap logis tanpa penyesuaian manual. |

## Performance Tips  

* **Potong node yang tidak terpakai** sebelum memanggil `updatePageLayout()` – lebih sedikit elemen berarti paginasi lebih cepat.  
* **Gunakan kembali satu LayoutCollector** untuk banyak query daripada membuatnya berulang kali.  
* **Batasi kedalaman penelusuran** saat menggunakan LayoutEnumerator jika Anda hanya membutuhkan data tingkat halaman.  
* **Tutup stream** (seperti pada contoh callback) untuk menghindari kebocoran memori pada dokumen besar.

## Conclusion  

Dengan menguasai `LayoutCollector`, `LayoutEnumerator`, callback layout, dan penomoran ulang pada section berkelanjutan, Anda kini memiliki kotak peralatan lengkap untuk **analyze pagination java**, **traverse document layout**, dan **restart page numbering sections**. API‑API ini memungkinkan Anda membangun pipeline pemrosesan teks yang kuat dan berperforma tinggi, menghasilkan hasil profesional setiap saat.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}