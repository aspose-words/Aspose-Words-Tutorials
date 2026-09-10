---
"date": "2025-03-29"
"description": "Pelajari cara mengoptimalkan penyimpanan dokumen dengan Aspose.Words untuk Python menggunakan format alur XAML dan callback progres. Tingkatkan efisiensi dalam mengelola dokumen."
"title": "Mengoptimalkan Penyimpanan Dokumen dalam Alur XAML dan Panggilan Balik Aspose.Words Python"
"url": "/id/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---
{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
# Cara Mengoptimalkan Penyimpanan Dokumen di Python Menggunakan Aspose.Words: Alur XAML dan Panggilan Balik Kemajuan

## Perkenalan

Apakah Anda ingin mengelola konversi dokumen secara efisien menggunakan Python? Kesulitan menangani gambar dan melacak kemajuan selama penyimpanan dokumen? Tutorial ini memandu Anda mengoptimalkan penyimpanan dokumen dengan Aspose.Words untuk Python, dengan fokus pada dua fitur hebat: `XamlFlowSaveOptions` dengan Panggilan Balik Kemajuan Penyimpanan Folder Gambar dan Dokumen.

Panduan komprehensif ini sempurna bagi pengembang yang ingin meningkatkan alur kerja pemrosesan dokumen mereka menggunakan pustaka Aspose.Words.

**Apa yang Akan Anda Pelajari:**
- Cara menyimpan dokumen dalam format alur XAML sambil mengelola sumber daya gambar.
- Menerapkan panggilan balik kemajuan selama penyimpanan dokumen untuk mencegah operasi yang lama.
- Menyiapkan dan mengonfigurasi Aspose.Words untuk Python di lingkungan pengembangan Anda.
- Aplikasi nyata dari fitur-fitur ini dalam sistem manajemen dokumen.

Mari selami prasyaratnya sebelum memulai coding!

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:

### Pustaka dan Versi yang Diperlukan
- **Aspose.Words untuk Python**Pastikan Anda memiliki versi 23.3 atau yang lebih baru.
- **Ular piton**: Versi 3.6 atau lebih tinggi direkomendasikan.

### Persyaratan Pengaturan Lingkungan
- Editor kode seperti VSCode atau PyCharm.
- Pengetahuan dasar tentang pemrograman Python.

### Prasyarat Pengetahuan
- Keakraban dengan konsep pemrosesan dokumen.
- Pemahaman tentang penanganan berkas dan manajemen direktori dalam Python.

## Menyiapkan Aspose.Words untuk Python

Untuk mulai menggunakan Aspose.Words, Anda perlu menginstalnya melalui pip. Buka terminal atau command prompt dan jalankan:

```bash
pip install aspose-words
```

### Langkah-langkah Memperoleh Lisensi
1. **Uji Coba Gratis**: Akses lisensi sementara [Di Sini](https://purchase.aspose.com/temporary-license/) untuk tujuan pengujian.
2. **Pembelian**:Untuk penggunaan jangka panjang, beli lisensi [Di Sini](https://purchase.aspose.com/buy).
3. **Inisialisasi dan Pengaturan Dasar**:
   - Muat dokumen Anda menggunakan `aw.Document()`.
   - Konfigurasikan pilihan penyimpanan sesuai kebutuhan.

## Panduan Implementasi

Bagian ini akan memandu Anda menerapkan dua fitur utama tutorial ini: XamlFlowSaveOptions dengan Folder Gambar, dan Panggilan Balik Kemajuan Penyimpanan Dokumen.

### Fitur 1: XamlFlowSaveOptions dengan Folder Gambar

#### Ringkasan
Fitur ini memungkinkan Anda menyimpan dokumen dalam format alur XAML sambil menentukan folder gambar dan alias. Fitur ini ideal untuk mengelola dokumen besar dengan gambar tertanam secara efisien.

#### Langkah-langkah Implementasi

##### Langkah 1: Impor Pustaka yang Diperlukan
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### Langkah 2: Tentukan Kelas Panggilan Balik ImageUriPrinter
Kelas ini menghitung dan mengalihkan aliran gambar ke folder alias yang ditentukan selama konversi.

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # tipe: Daftar[str]

        def image_saving(self, args: aw.saving.ImageSavingArgs):
            self.resources.append(args.image_file_name)
            with open(f"{self.images_folder_alias}/{args.image_file_name}", "wb") as image_stream:
                args.image_stream = image_stream
            args.keep_image_stream_open = False

    def test_image_folder(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Rendering.docx")
        callback = self.ImageUriPrinter(YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias")

        options = aw.saving.XamlFlowSaveOptions()
        options.images_folder = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolder"
        options.images_folder_alias = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias"
        options.image_saving_callback = callback

        os.makedirs(options.images_folder_alias, exist_ok=True)
        
        doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.image_folder.xaml", options)

        for resource in callback.resources:
            print(f"{callback.images_folder_alias}/{resource}")
```
**Opsi Konfigurasi Utama:**
- `images_folder`: Menentukan direktori tempat gambar disimpan.
- `images_folder_alias`: Menetapkan jalur alias yang digunakan selama konversi dokumen.

##### Tips Pemecahan Masalah
- Pastikan semua direktori ada sebelum menjalankan kode untuk menghindari kesalahan file tidak ditemukan.
- Periksa izin menulis di direktori keluaran Anda.

### Fitur 2: Panggilan Balik Kemajuan Penyimpanan Dokumen

#### Ringkasan
Fitur ini mengelola proses penyimpanan dengan menggunakan panggilan balik progres, yang memungkinkan Anda membatalkan operasi penyimpanan yang berjalan lama.

#### Langkah-langkah Implementasi

##### Langkah 1: Tentukan Kelas SavingProgressCallback
Kelas memantau durasi penyimpanan dokumen dan membatalkan jika melampaui batas waktu yang ditentukan.

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # Durasi maksimum yang diizinkan dalam detik.

        def notify(self, args: aw.saving.DocumentSavingArgs):
            canceled_at = datetime.now()
            elapsed_seconds = (canceled_at - self.saving_started_at).total_seconds()
            if elapsed_seconds > self.max_duration:
                raise OperationCanceledException(f"estimated_progress = {args.estimated_progress}; canceled_at = {canceled_at}")

    def test_progress_callback(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        parameters = [
            (aw.SaveFormat.XAML_FLOW, "xamlflow"),
            (aw.SaveFormat.XAML_FLOW_PACK, "xamlflowpack"),
        ]

        for save_format, ext in parameters:
            doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Big document.docx")
            save_options = aw.saving.XamlFlowSaveOptions(save_format)
            save_options.progress_callback = self.SavingProgressCallback()

            try:
                doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.progress_callback.{ext}", save_options)
            except OperationCanceledException as e:
                print(e)
```
**Opsi Konfigurasi Utama:**
- `save_format`: Pilih antara XAML_FLOW dan XAML_FLOW_PACK.
- `progress_callback`: Memantau kemajuan penyimpanan untuk menangani operasi yang panjang.

##### Tips Pemecahan Masalah
- Menyesuaikan `max_duration` berdasarkan ukuran dan kompleksitas dokumen.
- Tangani pengecualian dengan baik untuk memberikan pesan kesalahan yang informatif.

## Aplikasi Praktis

Berikut ini beberapa kasus penggunaan nyata untuk fitur-fitur ini:
1. **Sistem Manajemen Dokumen**: Kelola dokumen besar dengan gambar tertanam secara efisien dengan menentukan folder gambar, meningkatkan kinerja dan pengorganisasian.
2. **Alat Pelaporan Otomatis**: Gunakan panggilan balik kemajuan untuk memastikan laporan dibuat dalam jangka waktu yang dapat diterima, sehingga meningkatkan pengalaman pengguna.
3. **Jaringan Distribusi Konten**:Memperlancar konversi dokumen untuk distribusi web sambil mengelola sumber daya secara efektif.

## Pertimbangan Kinerja

Untuk mengoptimalkan kinerja saat menggunakan Aspose.Words dengan Python:
- **Manajemen Memori**: Pantau penggunaan sumber daya dan kelola memori secara efisien dengan membuang objek setelah digunakan.
- **Operasi I/O File**: Minimalkan operasi baca/tulis file untuk meningkatkan kecepatan.
- **Pemrosesan Batch**: Memproses dokumen secara berkelompok jika memungkinkan untuk mengurangi biaya overhead.

## Kesimpulan

Dalam tutorial ini, kami menjajaki cara mengoptimalkan penyimpanan dokumen dengan Aspose.Words untuk Python menggunakan XAML Flow dan callback progres. Dengan menerapkan fitur-fitur ini, Anda dapat meningkatkan efisiensi alur kerja pemrosesan dokumen, mengelola sumber daya secara efektif, dan memastikan operasi yang tepat waktu.
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}