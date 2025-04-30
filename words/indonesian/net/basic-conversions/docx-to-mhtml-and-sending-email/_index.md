---
"description": "Pelajari cara mengonversi DOCX ke MHTML dan mengirim email menggunakan Aspose.Words untuk .NET dalam panduan langkah demi langkah ini. Tingkatkan produktivitas Anda dengan otomatisasi yang mudah."
"linktitle": "Konversi Docx ke Mhtml dan mengirim email"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Konversi Docx ke Mhtml dan mengirim email"
"url": "/id/net/basic-conversions/docx-to-mhtml-and-sending-email/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Konversi Docx ke Mhtml dan mengirim email

## Perkenalan

Di era digital saat ini, mengonversi dokumen dari satu format ke format lain dan mengirimkannya melalui email merupakan tugas yang umum. Artikel ini akan memandu Anda melalui proses mengonversi file DOCX ke format MHTML lalu mengirimkannya sebagai email menggunakan Aspose.Words untuk .NET. Kami akan menguraikan setiap langkah dalam panduan terperinci dan mudah diikuti, memastikan Anda memahami prosesnya dari awal hingga akhir. Mari kita mulai!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:

1. Aspose.Words untuk .NET: Unduh dan instal pustaka Aspose.Words untuk .NET dari [Aspose merilis halaman](https://releases.aspose.com/words/net/).
2. Aspose.Email untuk .NET: Unduh dan instal pustaka Aspose.Email untuk .NET dari [Aspose merilis halaman](https://releases.aspose.com/email/net/).
3. .NET Framework: Pastikan Anda telah menginstal .NET Framework di komputer Anda.
4. Server SMTP: Anda memerlukan akses ke server SMTP untuk mengirim email.

## Mengimpor Ruang Nama

Untuk menggunakan Aspose.Words dan Aspose.Email dalam proyek Anda, Anda perlu mengimpor namespace yang diperlukan. Tambahkan perintah berikut di bagian atas file C# Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Mari kita uraikan prosesnya menjadi beberapa langkah untuk memastikan Anda memahami setiap bagian dengan jelas.

## Langkah 1: Muat Dokumen DOCX

Pertama, Anda perlu memuat dokumen DOCX yang ingin Anda konversi. Gunakan `Document` kelas dari Aspose.Words untuk memuat berkas DOCX Anda.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Langkah 2: Simpan Dokumen sebagai MHTML

Selanjutnya, simpan dokumen yang dimuat sebagai file MHTML. Ini dilakukan dengan menggunakan `Save` metode dari `Document` kelas.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Putar ulang aliran ke awal sehingga Aspose.Email dapat membacanya.
stream.Position = 0;
```

## Langkah 3: Buat Pesan Email

Sekarang, buat pesan email dari aliran MHTML menggunakan Aspose.Email. Anda akan menggunakan `MailMessage` kelas untuk tujuan ini.

```csharp
// Buat pesan email Aspose.Email MIME dari aliran.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Langkah 4: Kirim Email

Terakhir, kirim email menggunakan klien SMTP. Konfigurasikan klien SMTP dengan detail server SMTP Anda dan gunakan `Send` metode untuk mengirim pesan.

```csharp
// Kirim pesan menggunakan Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Kesimpulan

Selamat! Anda telah berhasil mengonversi dokumen DOCX ke MHTML dan mengirimkannya melalui email menggunakan Aspose.Words untuk .NET. Proses ini melibatkan pemuatan dokumen, mengonversinya ke MHTML, membuat pesan email, dan mengirimkannya menggunakan klien SMTP. Dengan langkah-langkah ini, Anda dapat dengan mudah mengotomatiskan konversi dan pengiriman dokumen melalui email di aplikasi Anda.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan metode ini untuk mengonversi format dokumen lain?
Ya, Aspose.Words mendukung berbagai format, dan Anda dapat mengonversi dokumen seperti DOC, DOCX, RTF, dan lainnya ke MHTML.

### Bagaimana cara menambahkan lampiran ke email?
Anda dapat menggunakan `Attachments` milik `MailMessage` kelas untuk menambahkan lampiran ke email Anda.

### Apakah Aspose.Words kompatibel dengan .NET Core?
Ya, Aspose.Words kompatibel dengan .NET Core. Anda juga dapat menggunakannya dalam aplikasi .NET Core.

### Apakah saya memerlukan lisensi untuk Aspose.Words dan Aspose.Email?
Ya, kedua perpustakaan tersebut memerlukan lisensi. Anda bisa mendapatkan lisensi sementara dari [Halaman pembelian Aspose](https://purchase.aspose.com/temporary-license/) untuk tujuan evaluasi.

### Di mana saya dapat menemukan dokumentasi lebih lanjut?
Anda dapat menemukan dokumentasi terperinci untuk Aspose.Words [Di Sini](https://reference.aspose.com/words/net/) dan untuk Aspose.Email [Di Sini](https://reference.aspose.com/email/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}