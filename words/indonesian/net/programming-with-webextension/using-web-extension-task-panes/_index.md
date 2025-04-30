---
"description": "Pelajari cara menambahkan dan mengonfigurasi Panel Tugas Ekstensi Web dalam dokumen Word menggunakan Aspose.Words untuk .NET dalam tutorial langkah demi langkah terperinci ini."
"linktitle": "Menggunakan Panel Tugas Ekstensi Web"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Menggunakan Panel Tugas Ekstensi Web"
"url": "/id/net/programming-with-webextension/using-web-extension-task-panes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menggunakan Panel Tugas Ekstensi Web

## Perkenalan

Selamat datang di tutorial mendalam tentang penggunaan Panel Tugas Ekstensi Web dalam dokumen Word menggunakan Aspose.Words untuk .NET. Jika Anda ingin menyempurnakan dokumen Word dengan panel tugas interaktif, Anda berada di tempat yang tepat. Panduan ini akan memandu Anda melalui setiap langkah untuk mencapainya dengan lancar.

## Prasyarat

Sebelum kita mulai, mari pastikan Anda memiliki semua yang Anda butuhkan:

- Aspose.Words untuk .NET: Anda dapat mengunduhnya [Di Sini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan .NET: Visual Studio atau IDE lain yang Anda sukai.
- Pengetahuan Dasar C#: Ini akan membantu Anda mengikuti contoh kode.
- Lisensi untuk Aspose.Words: Anda dapat membeli satu [Di Sini](https://purchase.aspose.com/buy) atau dapatkan lisensi sementara [Di Sini](https://purchase.aspose.com/temporary-license/).

## Mengimpor Ruang Nama

Sebelum kita mulai membuat kode, pastikan Anda telah mengimpor namespace berikut ke proyek Anda:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## Panduan Langkah demi Langkah

Sekarang, mari kita uraikan prosesnya menjadi langkah-langkah yang mudah diikuti.

### Langkah 1: Menyiapkan Direktori Dokumen Anda

Pertama-tama, kita perlu mengatur jalur ke direktori dokumen Anda. Di sinilah dokumen Word Anda akan disimpan.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Mengganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke folder dokumen Anda.

### Langkah 2: Membuat Dokumen Baru

Selanjutnya, kita akan membuat dokumen Word baru menggunakan Aspose.Words.

```csharp
Document doc = new Document();
```

Baris ini menginisialisasi instance baru dari `Document` kelas, yang mewakili dokumen Word.

### Langkah 3: Menambahkan Panel Tugas

Sekarang, kita akan menambahkan Task Pane ke dokumen kita. Task Pane berguna untuk menyediakan fungsi dan alat tambahan dalam dokumen Word.

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

Di sini, kita membuat yang baru `TaskPane` objek dan menambahkannya ke dokumen `WebExtensionTaskPanes` koleksi.

### Langkah 4: Mengonfigurasi Panel Tugas

Untuk membuat Panel Tugas kita terlihat dan mengatur propertinya, kita menggunakan kode berikut:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` mengatur tempat Task Pane akan muncul. Dalam kasus ini, Task Pane berada di sebelah kanan.
- `IsVisible` memastikan Panel Tugas terlihat.
- `Width` mengatur lebar Panel Tugas.

### Langkah 5: Menyiapkan Referensi Ekstensi Web

Berikutnya, kami menyiapkan Referensi Ekstensi Web yang menyertakan ID, versi, jenis penyimpanan, dan penyimpanan.

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id` adalah pengenal unik untuk ekstensi web.
- `Version` menentukan versi ekstensi.
- `StoreType` menunjukkan jenis toko (dalam hal ini, OMEX).
- `Store` menentukan kode bahasa/budaya toko.

### Langkah 6: Menambahkan Properti ke Ekstensi Web

Anda dapat menambahkan properti ke ekstensi web Anda untuk menentukan perilaku atau kontennya.

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

Di sini, kami menambahkan properti bernama `mailchimpCampaign`.

### Langkah 7: Mengikat Ekstensi Web

Terakhir, kami menambahkan binding ke ekstensi web kami. Binding memungkinkan Anda untuk menautkan ekstensi ke bagian tertentu dari dokumen.

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` adalah nama pengikatannya.
- `WebExtensionBindingType.Text` menunjukkan bahwa pengikatan tersebut berjenis teks.
- `194740422` adalah ID bagian dokumen yang ditautkan dengan ekstensi tersebut.

### Langkah 8: Menyimpan Dokumen

Setelah mengatur semuanya, simpan dokumen Anda.

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

Baris ini menyimpan dokumen ke direktori yang ditentukan dengan nama berkas yang diberikan.

### Langkah 9: Memuat dan Menampilkan Informasi Panel Tugas

Untuk memverifikasi dan menampilkan informasi panel tugas, kami memuat dokumen dan mengulangi panel tugas.

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

Kode ini memuat dokumen dan mencetak penyedia, versi, dan pengenal katalog setiap panel tugas di konsol.

## Kesimpulan

Selesai! Anda telah berhasil menambahkan dan mengonfigurasi Panel Tugas Ekstensi Web dalam dokumen Word menggunakan Aspose.Words untuk .NET. Fitur hebat ini dapat menyempurnakan dokumen Word Anda secara signifikan dengan menyediakan fungsionalitas tambahan langsung di dalam dokumen. 

## Pertanyaan yang Sering Diajukan

### Apa itu Panel Tugas di Word?
Panel Tugas adalah elemen antarmuka yang menyediakan alat dan fungsi tambahan dalam dokumen Word, yang meningkatkan interaksi pengguna dan produktivitas.

### Bisakah saya menyesuaikan tampilan Task Pane?
Ya, Anda dapat menyesuaikan tampilan Task Pane dengan mengatur properti seperti `DockState`Bahasa Indonesia: `IsVisible`, Dan `Width`.

### Apa itu Properti Ekstensi Web?
Properti Ekstensi Web adalah properti khusus yang dapat Anda tambahkan ke ekstensi web untuk menentukan perilaku atau kontennya.

### Bagaimana cara mengikat Ekstensi Web ke bagian dokumen?
Anda dapat mengikat Ekstensi Web ke bagian dokumen menggunakan `WebExtensionBinding` kelas, yang menentukan jenis pengikatan dan ID target.

### Di mana saya dapat menemukan informasi lebih lanjut tentang Aspose.Words untuk .NET?
Anda dapat menemukan dokumentasi terperinci [Di Sini](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}