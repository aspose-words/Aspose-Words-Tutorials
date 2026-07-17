---
category: general
date: 2026-07-16
description: Tutorial cmake build x64 menunjukkan cara menggunakan CMake untuk menghasilkan
  solusi Visual Studio 2022 dan membangun proyek VS pada host 64‑bit. Termasuk langkah‑langkah
  mengatur direktori sumber.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: id
lastmod: 2026-07-16
og_description: 'cmake build x64 dijelaskan: pelajari cara mengatur direktori sumber,
  menghasilkan solusi Visual Studio 2022, dan mengompilasi proyek VS pada host 64‑bit.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: Membangun cmake x64 – Panduan Langkah demi Langkah untuk Menghasilkan &
  Membuat Solusi VS 2022
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: cmake build x64 tutorial shows how to use CMake to generate a Visual
    Studio 2022 solution and build a VS project on a 64‑bit host. Includes set source
    directory steps.
  headline: cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects
  type: TechArticle
tags:
- cmake
- visual-studio
- x64
- build-automation
title: cmake build x64 – Panduan Lengkap untuk Menghasilkan dan Membangun Proyek VS 2022
url: /id/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Panduan Lengkap untuk Menghasilkan dan Membuat Proyek VS 2022

Pernah bertanya‑tanya **bagaimana cara menggunakan CMake** untuk menghasilkan solusi Visual Studio 64‑bit tanpa membuat rambut Anda rontok? Anda tidak sendirian. Pada tutorial ini kami akan menelusuri alur kerja **cmake build x64** yang mengatur direktori sumber, menjalankan generator untuk Visual Studio 2022, dan akhirnya membangun proyek VS—semua dengan beberapa perintah Bash yang bersih.

Pada akhir panduan Anda akan memiliki skrip yang dapat direproduksi dan dapat ditempatkan di repositori mana pun, serta pemahaman yang kuat tentang konsep dasarnya sehingga Anda dapat menyesuaikannya sesuai kebutuhan.

---

## Apa yang Akan Anda Pelajari

- **Set source directory** dengan benar sehingga CMake tahu di mana `CMakeLists.txt` Anda berada.  
- **cmake generate visual studio** – memanggil generator Visual Studio 2022 dengan flag host dan arsitektur yang tepat.  
- Melakukan **cmake build x64** pada solusi yang dihasilkan, dengan opsi memilih konfigurasi Release.  
- Memahami jebakan umum ketika Anda mencoba **build vs project** pada mesin 64‑bit.  

Tidak diperlukan keahlian CMake sebelumnya; cukup terminal dan instalasi Visual Studio terbaru.

---

## Prasyarat

| Requirement | Why it matters |
|-------------|----------------|
| CMake ≥ 3.20 | Mendukung flag `-Thost=` dan `-Ax64` yang digunakan untuk build 64‑bit. |
| Visual Studio 2022 (Community, Professional, atau Enterprise) | Generator `Visual Studio 17 2022` mengacu pada versi ini. |
| Shell yang kompatibel Bash (Git Bash, WSL, PowerShell dengan alias `bash`) | Skrip di bawah menggunakan sintaks Bash untuk kejelasan. |
| Pohon sumber yang berisi `CMakeLists.txt` yang valid | CMake tidak dapat menghasilkan solusi tanpa file tersebut. |

Jika ada yang belum terpasang, instal dulu—CMake dari <https://cmake.org/download/> dan VS 2022 dari installer Microsoft.

---

## Langkah 1 – Atur Direktori Sumber dan Build (`set source directory`)

Sebelum memanggil CMake Anda harus memberi tahu **di mana** mencari berkas proyek. Menuliskan jalur secara keras membuat skrip rapuh, jadi kami akan menggunakan variabel lingkungan yang dapat Anda sesuaikan per proyek.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Mengapa ini penting:**  
> CMake memperlakukan *source directory* (`SRC_DIR`) sebagai akar proyek. *Build directory* (`BUILD_DIR`) adalah tempat semua berkas menengah, cache, dan file `.sln` akhir berada. Memisahkannya menghindari pencemaran pohon sumber Anda dan memudahkan pembersihan (`rm -rf "$BUILD_DIR"`).

Anda dapat mengganti `YOUR_DIRECTORY` dengan jalur absolut atau relatif apa pun; pastikan folder tersebut berisi `CMakeLists.txt`.

---

## Langkah 2 – Hasilkan Solusi Visual Studio 2022 (`cmake generate visual studio`)

Sekarang kami meminta CMake untuk menghasilkan solusi VS 2022 yang menargetkan **x64**. Flag kunci adalah:

- `-G "Visual Studio 17 2022"` – memilih generator VS 2022.  
- `-Thost=x64` – memberi tahu CMake bahwa *host* (IDE) berjalan sebagai proses 64‑bit.  
- `-Ax64` – memaksa proyek yang dihasilkan dibangun untuk arsitektur x64.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **Apa yang terjadi di balik layar?**  
> CMake membaca `CMakeLists.txt` dari `$SRC_DIR`, menyelesaikan semua pemanggilan `add_executable()` dan `add_library()`, lalu membuat file `.sln` serta sekumpulan file `.vcxproj` di dalam `$BUILD_DIR`. File proyek tersebut kini siap dibuka di Visual Studio atau dibangun lewat baris perintah.

Jika Anda menjalankan perintah dan melihat daftar panjang pesan konfigurasi yang diakhiri dengan `-- Configuring done` dan `-- Generating done`, maka Anda telah berhasil melakukan langkah **cmake generate visual studio**.

---

## Langkah 3 – Bangun Solusi yang Dihasilkan (`cmake build x64`)

Setelah solusi tersedia, langkah logis berikutnya adalah mengompilasinya. CMake dapat mengendalikan proses build untuk Anda, menyerahkan tugas ke MSBuild di belakang layar.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Mengapa menggunakan `--config Release`?**  
> Proyek Visual Studio mendukung banyak konfigurasi (Debug, Release, RelWithDebInfo, dll.). Menentukan `Release` memastikan binari dioptimalkan untuk produksi dan bahwa file `.exe` atau `.dll` yang dihasilkan berada di dalam folder `Release/` pada pohon build.

Jika Anda menginginkan build Debug, ganti `Release` dengan `Debug`. Perintahnya tetap sama, membuktikan bahwa **how to use CMake** untuk konfigurasi berbeda hanyalah soal mengganti flag ini.

---

## Langkah 4 – Verifikasi Build (`build vs project` sanity check)

Kompilasi yang berhasil harus meninggalkan sebuah executable atau library. Mari pastikan keberadaannya:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Jebakan umum:**  
> - Lupa menjalankan langkah generator setelah mengubah `CMakeLists.txt` akan menyebabkan pemeriksaan ini gagal.  
> - Mencampur toolchain 32‑bit dan 64‑bit dapat menimbulkan error linker; selalu pertahankan konsistensi `-Ax64`.  
> - Jika Anda melihat error “MSB3073”, biasanya berarti langkah post‑build (seperti menyalin resource) gagal—periksa output untuk petunjuk.

---

## Langkah 5 – Bersihkan dan Jalankan Ulang (Iterasi pada `cmake build x64`)

Selama pengembangan Anda sering perlu membangun ulang dari awal. Cara paling bersih adalah menghapus folder build dan memulai lagi:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Tip:**  
> Menambahkan `-DCMAKE_BUILD_TYPE=Release` pada perintah generator bersifat opsional untuk generator multi‑config seperti Visual Studio, namun dapat berguna ketika Anda beralih ke generator single‑config seperti Ninja.

---

## Langkah 6 – Memperluas Skrip (Skenario `cmake generate visual studio` lanjutan)

Bagaimana jika proyek Anda berada di sub‑direktori, atau Anda perlu menyertakan definisi khusus? CMake memungkinkan hal ini dengan argumen `-D`:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Sekarang solusi VS yang dihasilkan akan memiliki makro `MyFeature_ENABLED` terdefinisi, dan target install akan menempatkan berkas di bawah `/opt/myapp`. Ini menunjukkan fleksibilitas **how to use CMake** di luar alur tiga langkah dasar.

---

## Output yang Diharapkan

Saat Anda menjalankan skrip lengkap dari awal hingga akhir, terminal seharusnya menampilkan sesuatu seperti:

```
-- The C compiler identification is MSVC 19.35.31107.0
-- The CXX compiler identification is MSVC 19.35.31107.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
...
-- Configuring done
-- Generating done
-- Build files have been written to: /path/to/Examples/DocsExamples/build
...
[ 50%] Building CXX object CMakeFiles/MyApp.dir/main.cpp.obj
[100%] Linking CXX executable Release/MyApp.exe
✅ Build succeeded! Executable ready at /path/to/Examples/DocsExamples/build/Release/MyApp.exe
```

Jika ada yang tidak beres, CMake akan mengeluarkan pesan error yang menunjuk ke baris bermasalah di `CMakeLists.txt` atau ke komponen SDK yang hilang—sangat membantu untuk debugging cepat.

---

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk melakukan **cmake build x64**: mengatur direktori sumber, memanggil langkah **cmake generate visual studio**, mengompilasi **build vs project** yang dihasilkan, dan memverifikasi output. Skripnya ringkas, portabel, dan siap diintegrasikan ke pipeline CI atau alur kerja pengembangan lokal.

Selanjutnya, Anda dapat menjelajahi:

- Menambahkan eksekusi unit‑test dengan `ctest`.  
- Beralih ke generator Ninja untuk build incremental yang lebih cepat (`-G Ninja`).  
- Menggunakan preset CMake (`CMakePresets.json`) untuk menyimpan flag yang baru saja kita ketik.

Silakan bereksperimen, pecahkan masalah, lalu bangun kembali—karena itulah cara tercepat untuk belajar **how to use CMake** secara efektif. Selamat membangun!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Build Table](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Build Table With Style](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Build Table With Borders](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}