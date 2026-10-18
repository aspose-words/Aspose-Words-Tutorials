---
title: Sesuaikan Garis Kisi Sumbu X pada Diagram Kolom Menggunakan Aspose.Words for .NET
weight: 610
limit:
description: Pelajari cara menambahkan dan menyesuaikan warna garis kisi utama sumbu X pada diagram kolom Word dengan Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, column chart, customize x axis gridlines, word chart gridlines, primary x axis gridlines, chart formatting .NET]
url: /net/programming-with-charts/customize-x-axis-gridlines/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Pelajari cara menambahkan dan menyesuaikan warna garis kisi utama sumbu
    X pada diagram kolom Word dengan Aspose.Words for .NET.
  headline: Sesuaikan Garis Kisi Sumbu X pada Diagram Kolom Menggunakan Aspose.Words
    for .NET
  type: TechArticle
- description: Pelajari cara menambahkan dan menyesuaikan warna garis kisi utama sumbu
    X pada diagram kolom Word dengan Aspose.Words for .NET.
  name: Sesuaikan Garis Kisi Sumbu X pada Diagram Kolom Menggunakan Aspose.Words for
    .NET
  steps:
  - name: Buat dokumen Word baru dan DocumentBuilder untuk mengeditnya.
    text: Buat dokumen Word baru dan DocumentBuilder untuk mengeditnya.
  - name: Sisipkan diagram kolom berukuran 432×252 ke dalam dokumen dan dapatkan objek
      Chart-nya.
    text: Sisipkan diagram kolom berukuran 432×252 ke dalam dokumen dan dapatkan objek
      Chart-nya.
  - name: Hapus seri default dan tambahkan seri khusus dengan tiga grup dan nilai.
    text: Hapus seri default dan tambahkan seri khusus dengan tiga grup dan nilai.
  - name: Dapatkan referensi ke sumbu horizontal (X) utama chart.
    text: Dapatkan referensi ke sumbu horizontal (X) utama chart.
  - name: Aktifkan tampilan garis kisi utama pada sumbu X utama.
    text: Aktifkan tampilan garis kisi utama pada sumbu X utama.
  - name: Atur warna garis kisi menjadi biru dan ketebalannya menjadi 2 poin.
    text: Atur warna garis kisi menjadi biru dan ketebalannya menjadi 2 poin.
  - name: Simpan dokumen ke file .docx.
    text: Simpan dokumen ke file .docx.
  type: HowTo
- questions:
  - answer: 'Setel properti sumbu yang sama ke false: `horizontalAxis.HasMajorGridlines
      = false;` mengubah visibilitas garis kisi utama sumbu X.'
    question: Bagaimana cara menyembunyikan kembali garis kisi utama setelah mengaktifkannya?
  - answer: Tidak, pengaturan `Format.Stroke` hanya berlaku pada sumbu yang Anda ubah;
      untuk menata garis kisi sumbu Y Anda harus menyesuaikan `chart.AxisY.Format.Stroke`
      secara terpisah.
    question: Apakah mengubah `horizontalAxis.Format.Stroke.Color` juga akan memengaruhi
      garis kisi sumbu Y?
  - answer: Gunakan `horizontalAxis.Format.Stroke.Weight` dan berikan nilai double
      (misalnya `0.5`) untuk membuat garis kisi menjadi lebih tipis.
    question: Properti mana yang mengontrol ketebalan garis kisi utama sumbu X?
  - answer: Ya, atur `horizontalAxis.Format.Stroke.DashStyle` ke nilai enum `DashStyle`
      seperti `DashStyle.Dash` atau `DashStyle.Dot`.
    question: Bisakah saya mengubah pola dash pada garis kisi utama sumbu X?
  type: FAQPage
images:
- /net/programming-with-charts/customize-x-axis-gridlines/og-image.png
og_title: Gaya Garis Kisi Sumbu X pada Diagram Kolom Word
og_description: Aktifkan dan sesuaikan warna garis kisi utama sumbu X pada chart Word dengan Aspose.Words for .NET.
og_image_alt: Panduan yang menampilkan dokumen Word dengan diagram kolom di mana garis kisi utama sumbu X utama disorot dengan warna khusus menggunakan Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sesuaikan Garis Kisi Sumbu X pada Diagram Kolom Menggunakan Aspose.Words
Dalam tutorial ini Anda akan belajar cara membuat dokumen Word, menyisipkan diagram kolom, mengganti data defaultnya, dan kemudian mengaktifkan garis kisi utama pada sumbu X utama. Anda juga akan melihat cara mengubah warna garis kisi agar sesuai dengan desain Anda. Ikuti kode langkah‑demi‑langkah untuk mendapatkan kontrol yang tepat atas visibilitas dan penataan garis kisi sumbu X.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/customize-x-axis-gridlines" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Bagaimana cara menyembunyikan kembali garis kisi utama setelah mengaktifkannya?**  
A: Setel properti sumbu yang sama ke false: `horizontalAxis.HasMajorGridlines = false;` mengubah visibilitas garis kisi utama sumbu X.

**Q: Apakah mengubah `horizontalAxis.Format.Stroke.Color` juga akan memengaruhi garis kisi sumbu Y?**  
A: Tidak, pengaturan `Format.Stroke` hanya berlaku pada sumbu yang Anda ubah; untuk menata garis kisi sumbu Y Anda harus menyesuaikan `chart.AxisY.Format.Stroke` secara terpisah.

**Q: Properti mana yang mengontrol ketebalan garis kisi utama sumbu X?**  
A: Gunakan `horizontalAxis.Format.Stroke.Weight` dan berikan nilai double (misalnya `0.5`) untuk membuat garis kisi menjadi lebih tipis.

**Q: Bisakah saya mengubah pola dash pada garis kisi utama sumbu X?**  
A: Ya, atur `horizontalAxis.Format.Stroke.DashStyle` ke nilai enum `DashStyle` seperti `DashStyle.Dash` atau `DashStyle.Dot`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}