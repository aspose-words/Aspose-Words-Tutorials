---
category: general
date: 2026-02-15
description: Mode pemulihan memungkinkan Anda memuat dokumen dengan pemulihan, memudahkan
  pemulihan dokumen Word yang rusak dan memperbaiki kesalahan pemulihan dokumen Word.
draft: false
keywords:
- set recovery mode
- recover broken word document
- load document with recovery
- recover word document errors
language: id
og_description: Mengatur mode pemulihan adalah kunci untuk memuat dokumen dengan pemulihan,
  memungkinkan Anda memperbaiki kesalahan dokumen Word yang rusak di Java.
og_title: atur mode pemulihan – Pulihkan Dokumen Word yang Rusak dengan Cepat
tags:
- Aspose.Words
- Java
- Document Recovery
title: atur mode pemulihan untuk memperbaiki dokumen Word yang rusak
url: /id/java/document-loading-and-saving/set-recovery-mode-to-recover-broken-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set recovery mode – Cara Memulihkan Dokumen Word Rusak dengan Aspose.Words

Pernah mencoba membuka file Word yang tiba‑tiba menolak untuk dimuat? Anda mungkin sedang melihat *.docx* yang rusak dan bertanya-tanya apakah Anda harus memulai dari awal. Kabar baik? **set recovery mode** di Aspose.Words memberi Anda cara yang elegan untuk *load document with recovery* dan menjaga sebagian besar konten tetap utuh.  

Dalam tutorial ini Anda akan belajar persis cara **set recovery mode**, mengapa opsi *RELAXED* biasanya menjadi pilihan terbaik untuk file yang rusak, dan cara menangani sesekali *recover word document errors* yang masih muncul. Tanpa alat eksternal, hanya Java biasa dan beberapa baris kode.

> **Apa yang akan Anda dapatkan:** contoh lengkap yang dapat dijalankan yang memuat file Word yang rusak, melewati bagian yang tidak dapat dibaca, dan memberi Anda objek `Document` yang dapat digunakan siap untuk pemrosesan lebih lanjut.

## Prasyarat

- **Aspose.Words for Java** (v24.9 atau lebih baru) ditambahkan ke proyek Anda via Maven atau JAR manual.
- Sebuah file **.docx** yang **rusak** yang ingin Anda uji (kami akan menyebutnya `Corrupted.docx`).
- Pengetahuan dasar Java – Anda tidak perlu menjadi ahli pengolah Word, cukup nyaman dengan metode `main`.

Jika Anda kekurangan salah satu dari ini, dapatkan JAR Aspose.Words terbaru dari [official site](https://products.aspose.com/words/java) dan tambahkan ke classpath Anda. Itu saja—tanpa dependensi tambahan.

## Langkah 1: Memahami Mode Pemulihan

| Mode | Behavior | When to use |
|------|----------|------------|
| **RELAXED** | Melewati bagian yang tidak dapat dibaca, menyimpan sisanya. | Sebagian besar file yang rusak – Anda ingin **recover broken word document** tanpa pengecualian. |
| **STRICT** | Melemparkan pengecualian pada setiap kesalahan. | Saat Anda perlu menjamin pemuatan yang sempurna dan bebas error (jarang untuk sumber yang rusak). |

> **Tip profesional:** *RELAXED* adalah default untuk skenario “hanya dapatkan sesuatu kembali”, sementara *STRICT* berguna dalam pipeline otomatis di mana kegagalan harus menghentikan proses.

## Langkah 2: Buat Objek `LoadOptions` dan **set recovery mode**

Di sinilah kata kunci utama muncul dalam kode. Kami secara eksplisit **set recovery mode** pada instance `LoadOptions` sebelum memuat file.

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions and choose a recovery mode.
        // RELAXED will skip unreadable parts, while STRICT throws an exception.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // <-- set recovery mode

        // 2️⃣ Load the potentially corrupted document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 3️⃣ Verify that the document loaded and optionally save a cleaned copy.
        System.out.println("Document loaded successfully. Page count: " + doc.getPageCount());
        doc.save("Recovered.docx");
    }
}
```

**Mengapa ini penting:** Dengan memanggil `setRecoveryMode`, Anda memberi tahu Aspose.Words seberapa agresif ia harus mencoba menyelamatkan file. Tanpa pemanggilan ini, perpustakaan secara default ke *STRICT*, yang akan menghentikan pada tanda pertama masalah—meniadakan tujuan alur kerja *recover broken word document*.

## Langkah 3: Verifikasi Pemuatan – Apakah Kita Benar‑benar **recover broken word document**?

Setelah pemuatan, Anda dapat memeriksa objek `Document`:

```java
// Check if any sections were dropped
int sections = doc.getSections().getCount();
System.out.println("Sections recovered: " + sections);
```

Jika konsol menampilkan jumlah bagian yang wajar, Anda telah berhasil *load document with recovery*. Pada praktiknya, Anda akan melihat bahwa kebanyakan teks, tabel, dan gambar tetap ada, sementara bagian yang rusak hanya menghilang.

## Langkah 4: Tangani **recover word document errors** yang Masih Tersisa dengan Elegan

Bahkan dengan mode *RELAXED*, beberapa kasus tepi masih dapat memunculkan peringatan. Bungkus pemuatan dalam try‑catch untuk menjaga aplikasi tetap hidup:

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    // Continue processing...
} catch (Exception ex) {
    System.err.println("Recovery failed: " + ex.getMessage());
    // Optionally fallback to a backup copy or notify the user.
}
```

**Kapan ini terjadi?** Jika file begitu rusak sehingga bahkan parser yang relaxed tidak dapat mengidentifikasi struktur dokumen yang valid, Aspose.Words tetap akan melempar pengecualian. Pada momen langka tersebut, Anda mungkin perlu meminta pengguna menyediakan salinan lain.

## Langkah 5: Simpan File yang Dipulihkan (Opsional)

Sebagian besar pengembang menginginkan versi bersih untuk diserahkan ke sistem hilir. Pemanggilan `save` di bawah menulis `.docx` baru yang tidak lagi berisi fragmen yang rusak.

```java
doc.save("Recovered.docx");
System.out.println("Recovered file saved as Recovered.docx");
```

Sekarang Anda memiliki **recover broken word document** yang dapat dibuka di Microsoft Word, Google Docs, atau penampil lainnya—tanpa dialog error.

## Gambaran Visual (Gambar)

![Diagram yang menunjukkan alur set recovery mode – dari file yang rusak ke dokumen yang dipulihkan](https://example.com/images/recovery-flow.png "diagram alur set recovery mode")

*Teks alt secara eksplisit berisi kata kunci utama, membantu mesin pencari dan pembaca layar.*

## Pertanyaan Umum & Kasus Tepi

| Question | Answer |
|----------|--------|
| *Bagaimana jika saya perlu menyimpan bagian yang rusak untuk analisis forensik?* | Gunakan `LoadOptions.setRecoverMode(LoadOptions.RecoveryMode.STRICT)` dan tangkap pengecualian. Pesan pengecualian berisi detail tentang bagian yang bermasalah. |
| *Apakah saya dapat beralih antara RELAXED dan STRICT saat runtime?* | Tentu saja—cukup buat instance `LoadOptions` baru dengan mode yang diinginkan sebelum setiap pemuatan. |
| *Apakah ini bekerja dengan file .doc lama?* | Ya. `LoadOptions` yang sama berlaku untuk format `.doc` dan `.docx`. |
| *Apakah ada penalti kinerja?* | Minimal. Overhead parsing tambahan dapat diabaikan dibandingkan biaya pemuatan dokumen penuh. |

## Contoh Lengkap yang Dapat Dijalankan (Siap Salin‑Tempel)

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) {
        try {
            // Step 1 – configure recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // set recovery mode

            // Step 2 – load the corrupted file
            Document doc = new Document("Corrupted.docx", loadOptions);

            // Step 3 – optional verification
            System.out.println("Loaded! Pages: " + doc.getPageCount());

            // Step 4 – save a clean copy
            doc.save("Recovered.docx");
            System.out.println("Saved recovered document as Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
        }
    }
}
```

Jalankan program, arahkan ke file yang rusak, dan perhatikan outputnya. Jika semuanya berjalan lancar, Anda akan melihat jumlah halaman tercetak dan `Recovered.docx` baru muncul di samping sumber Anda.

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk **set recovery mode** di Aspose.Words, mulai dari memilih enum `RecoveryMode` yang tepat hingga menangani beberapa *recover word document errors* yang mungkin masih muncul. Dengan mengikuti langkah‑langkah di atas, Anda dapat secara andal **load document with recovery**, mempertahankan bagian baik dari file yang rusak, dan menghasilkan versi bersih yang siap untuk pemrosesan hilir apa pun.

Siap untuk tantangan berikutnya? Cobalah menggabungkan **set recovery mode** dengan API **pembersihan dokumen** Aspose.Words—menghapus paragraf tersembunyi, memperbaiki tautan yang rusak, atau bahkan mengonversi file yang dipulihkan ke PDF dalam satu langkah. Kemungkinannya tak terbatas, dan kini Anda memiliki fondasi kuat untuk menangani file Word yang rusak secara langsung.

Selamat coding, semoga dokumen Anda tetap sehat!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}