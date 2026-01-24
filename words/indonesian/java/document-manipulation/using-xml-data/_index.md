---
date: 2026-01-24
description: Pelajari cara menggabungkan data XML dengan Aspose.Words untuk Java,
  mengotomatiskan pembuatan dokumen Java, dan menggunakan sintaks Mustache untuk dokumen
  dinamis.
linktitle: Using XML Data
second_title: Aspose.Words Java Document Processing API
title: Cara Menggabungkan XML di Aspose.Words untuk Java
url: /id/java/document-manipulation/using-xml-data/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menggabungkan XML di Aspose.Words untuk Java

Dalam panduan komprehensif ini Anda akan menemukan **cara menggabungkan XML** menggunakan Aspose.Words untuk Java. Kami akan membahas skenario mail‑merge dasar dan bersarang, menunjukkan **cara menggunakan sintaks Mustache**, dan menjelaskan **cara mengotomatiskan pembuatan dokumen Java**‑style. Pada akhir panduan Anda akan dapat menghasilkan dokumen Word yang dipersonalisasi langsung dari sumber XML dengan hanya beberapa baris kode.

## Jawaban Cepat
- **Kelas utama untuk mail merge apa?** `Document` dan properti `MailMerge`‑nya.  
- **Apakah saya dapat menggabungkan tabel XML bersarang?** Ya – gunakan `executeWithRegions` untuk data hierarkis.  
- **Apakah sintaks Mustache didukung?** Aktifkan dengan `setUseNonMergeFields(true)`.  
- **Apakah saya memerlukan lisensi untuk produksi?** Lisensi komersial Aspose.Words diperlukan.  
- **Versi Java mana yang kompatibel?** Java 8+ dan versi selanjutnya didukung sepenuhnya.

## Apa Itu XML Mail Merge di Aspose.Words?
XML mail merge memungkinkan Anda mengikat dataset berbasis XML ke placeholder dalam templat Word. Mesin akan mengganti setiap placeholder dengan nilai node XML yang bersesuaian, menghasilkan dokumen selesai tanpa penyuntingan manual.

## Mengapa Menggunakan Aspose.Words untuk Pembuatan Dokumen Berbasis XML?
- **Mengotomatiskan pembuatan dokumen Java** tanpa ketergantungan Microsoft Office.  
- **Mendukung hierarki kompleks** – tabel bersarang, bagian berulang, dan konten bersyarat.  
- **Sintaks Mustache** memberi Anda placeholder non‑merge‑field yang fleksibel untuk templating lanjutan.  
- **Lintas platform** – berfungsi di Windows, Linux, dan macOS.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal‑hal berikut:

- [Aspose.Words for Java](https://products.aspose.com/words/java/) terpasang (versi terbaru).  
- File XML contoh untuk pelanggan, pesanan, dan vendor (tutorial ini menggunakan `Mail merge data - Customers.xml`, `Orders.xml`, dan `Vendors.xml`).  
- Dokumen templat Word yang berisi field merge (misalnya `Registration complete.docx`, `Invoice.docx`, `Vendor.docx`).  

## Cara Menggabungkan XML – Mail Merge Dasar

Mail merge dasar mengambil satu tabel XML ke dalam templat Word. Ikuti langkah‑langkah berikut:

1. Muat file XML ke dalam `DataSet`.  
2. Buka dokumen Word tujuan.  
3. Jalankan merge menggunakan nama tabel.  
4. Simpan dokumen yang sudah digabung.

```java
DataSet customersDs = new DataSet();
customersDs.readXml("Your Directory Path" + "Mail merge data - Customers.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Registration complete.docx");
doc.getMailMerge().execute(customersDs.getTables().get("Customer"));
doc.save("Your Directory Path" + "BasicMailMerge.docx");
```

**Tips profesional:** Pertahankan struktur XML Anda datar untuk merge sederhana – setiap tabel harus langsung dipetakan ke sekumpulan field merge.

## Cara Menggabungkan XML – Mail Merge Bersarang

Ketika XML Anda berisi hubungan induk‑anak (misalnya pesanan dengan item baris), Anda memerlukan merge bersarang. Metode `executeWithRegions` memproses setiap region secara rekursif.

1. Muat XML hierarkis ke dalam `DataSet`.  
2. Nonaktifkan pemangkasan spasi putih jika Anda memerlukan format yang tepat.  
3. Panggil `executeWithRegions` untuk menangani semua tabel bersarang.  
4. Simpan hasilnya.

```java
DataSet pizzaDs = new DataSet();
pizzaDs.readXml("Your Directory Path" + "Mail merge data - Orders.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Invoice.docx");
doc.getMailMerge().setTrimWhitespaces(false);
doc.getMailMerge().executeWithRegions(pizzaDs);
doc.save("Your Directory Path" + "NestedMailMerge.docx");
```

**Kesalahan umum:** Lupa mengatur `setTrimWhitespaces(false)` dapat menyebabkan spasi yang tidak diinginkan dalam dokumen akhir, terutama untuk bidang mata uang atau numerik.

## Cara Menggunakan Sintaks Mustache dengan DataSet

Sintaks Mustache memungkinkan Anda menyisipkan placeholder non‑merge‑field (misalnya `{{CustomerName}}`) di dalam templat. Aktifkan dan jalankan merge berbasis region.

1. Muat XML vendor.  
2. Aktifkan dukungan Mustache dengan `setUseNonMergeFields(true)`.  
3. Jalankan merge dengan region.  
4. Simpan outputnya.

```java
DataSet ds = new DataSet();
ds.readXml("Your Directory Path" + "Mail merge data - Vendors.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Vendor.docx");
doc.getMailMerge().setUseNonMergeFields(true);
doc.getMailMerge().executeWithRegions(ds);
doc.save("Your Directory Path" + "MustacheSyntaxUsingDataSet.docx");
```

**Mengapa menggunakan Mustache?** Sintaks ini menyediakan cara bersih dan bahasa‑agnostik untuk merujuk data, membuat templat Anda lebih mudah dibaca dan dipelihara, terutama ketika **menghasilkan dokumen berbasis XML** dalam alur kerja.

## Masalah Umum dan Solusinya

| Masalah | Solusi |
|-------|----------|
| Node XML tidak cocok dengan field merge | Pastikan nama elemen XML persis sama dengan nama field merge (case‑sensitive). |
| Spasi putih muncul di sekitar nilai yang digabung | Gunakan `doc.getMailMerge().setTrimWhitespaces(false)` untuk mempertahankan spasi asli. |
| Tabel bersarang diabaikan | Pastikan region tabel induk didefinisikan dalam templat (misalnya `{{#Orders}} … {{/Orders}}`). |
| Placeholder Mustache tidak diganti | Panggil `setUseNonMergeFields(true)` sebelum mengeksekusi merge. |

## FAQ

### Bagaimana cara menyiapkan data XML saya untuk mail merge?

Pastikan XML Anda mengikuti struktur tabel di mana setiap elemen `<TableName>` berisi baris (`<Row>`) dan kolom yang sesuai dengan field merge di templat Word Anda.

### Bisakah saya menyesuaikan perilaku pemangkasan nilai mail merge?

Ya. Gunakan `doc.getMailMerge().setTrimWhitespaces(false)` untuk mempertahankan spasi awal/akhir persis seperti yang muncul di XML.

### Apa itu sintaks Mustache, dan kapan harus saya gunakan?

Sintaks Mustache (`{{FieldName}}`) memungkinkan placeholder fleksibel yang tidak terbatas pada field merge tradisional. Aktifkan dengan `setUseNonMergeFields(true)` ketika Anda memerlukan templat yang lebih bersih atau ingin memisahkan logika data dari kode field Word.

### Bagaimana cara mengotomatiskan proyek pembuatan dokumen Java dengan pendekatan ini?

Integrasikan potongan kode di atas ke dalam lapisan layanan Anda, baca XML dari basis data atau API, dan panggil rutin merge setiap kali dokumen baru diperlukan (misalnya pembuatan faktur, kontrak).

### Apakah lisensi komersial diperlukan untuk penggunaan produksi?

Ya, Aspose.Words memerlukan lisensi yang valid untuk penyebaran produksi. Lisensi sementara gratis tersedia untuk evaluasi.

---

**Terakhir Diperbarui:** 2026-01-24  
**Diuji Dengan:** Aspose.Words for Java (rilis terbaru)  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}