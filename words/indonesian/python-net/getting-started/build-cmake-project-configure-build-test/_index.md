---
category: general
date: 2026-07-06
description: Bangun proyek CMake langkah demi langkah. Pelajari cara mengkonfigurasi
  CMake, cara membangun CMake, dan cara menjalankan CTest untuk pengujian yang dapat
  diandalkan.
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: id
og_description: Bangun proyek CMake dengan cepat melalui langkah‑langkah yang jelas.
  Panduan ini menunjukkan cara mengonfigurasi CMake, cara membangun CMake, dan cara
  menjalankan CTest.
og_title: 'Membangun Proyek CMake: Panduan Konfigurasi, Pembangunan, dan Pengujian'
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Build CMake project step‑by‑step. Learn how to configure CMake, how
    to build CMake, and how to run CTest for reliable testing.
  headline: 'Build CMake Project: Configure, Build & Test'
  type: TechArticle
tags:
- cmake
- ctest
- build-system
title: 'Bangun Proyek CMake: Konfigurasi, Bangun & Uji'
url: /id/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Build CMake Project: Configure, Build & Test

Pernah bertanya-tanya bagaimana **membangun proyek CMake** tanpa menghabiskan berjam‑jam mencari di StackOverflow? Anda tidak sendirian. Kebanyakan pengembang mengalami masalah yang sama ketika mencoba beralih dari `CMakeLists.txt` sederhana ke pipeline build yang dapat direproduksi.

Dalam tutorial ini kita akan melewati seluruh proses—*cara mengonfigurasi CMake*, *cara membangun CMake*, dan *cara menjalankan CTest*—sehingga Anda mendapatkan build yang bersih dan dapat diulang yang dapat dijalankan di mesin mana pun. Pada akhir tutorial Anda akan memiliki contoh yang dapat disalin‑tempel ke repositori Anda sendiri, tanpa skrip tambahan.

## Prerequisites — What you need before you start

Sebelum kita mulai, pastikan Anda memiliki:

- Versi CMake terbaru (3.20 atau lebih baru) – rilis yang lebih lama tidak memiliki beberapa flag yang akan kita gunakan.
- Compiler C++ yang didukung oleh platform Anda (gcc, clang, MSVC, dll.).
- Terminal atau command‑prompt dengan akses ke `cmake` dan `ctest`.
- (Opsional) Git untuk meng‑clone repositori contoh jika Anda ingin mengikuti sumber yang tepat.

Jika ada yang belum ada, segera dapatkan sekarang; jika tidak, Anda akan menemui error “command not found” nanti, dan itu tidak menyenangkan.

## Step 1: Configure the CMake Project (Release configuration)

Hal pertama yang Anda lakukan ketika *how to configure CMake* adalah memberi tahu CMake di mana sumber berada dan ke mana artefak build harus diletakkan. Flag `-S` menunjuk ke direktori sumber, `-B` membuat folder build terpisah, dan `-D CMAKE_BUILD_TYPE=Release` memaksa build yang dioptimalkan.

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**Mengapa ini penting:** Memisahkan file sumber dan build (`out‑of‑source` builds) mencegah modifikasi sumber secara tidak sengaja dan memudahkan pembersihan direktori build nanti. Flag `Release` juga memberi tahu compiler untuk mengaktifkan optimisasi, yang biasanya diinginkan untuk binary final.

> **Pro tip:** Jika Anda membutuhkan build Debug untuk pemecahan masalah, cukup ganti `Release` dengan `Debug`. Perintah yang sama tetap berlaku—CMake menangani sisanya.

## Step 2: Build the Configured Project

Setelah langkah konfigurasi menghasilkan semua makefile atau file proyek Visual Studio yang diperlukan, Anda dapat benar‑benar mengompilasi kode. Opsi `--build` menyembunyikan detail alat build yang mendasarinya (`make`, `ninja`, `MSBuild`, dll.), sehingga perintah yang sama bekerja di Linux, macOS, dan Windows.

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**Apa yang terjadi di balik layar?** CMake membaca `CMakeCache.txt` yang dibuat pada langkah sebelumnya, menentukan alat build yang tepat, dan memanggilnya dengan flag yang benar. Inilah inti dari *how to build CMake*—Anda tidak perlu mengingat apakah menggunakan `make` atau `ninja`; CMake yang mengurusnya.

Jika Anda ingin mempercepat proses pada mesin multi‑core, tambahkan `-- -j$(nproc)` (Linux/macOS) atau `-- /m` (Windows) setelah perintah:

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## Step 3: Run the Example Tests with Detailed Output

Pengujian adalah tempat di mana semuanya diuji. CMake menyertakan `ctest`, driver tes yang dapat menemukan dan menjalankan tes apa pun yang ditambahkan melalui `add_test()` di `CMakeLists.txt` Anda. Untuk mengeksekusi tes dan melihat output verbose, gunakan helper `-E chdir` untuk berpindah ke direktori build terlebih dahulu:

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**Mengapa menggunakan `--verbose`?** Ia mencetak baris perintah tiap tes, kode keluar, dan output apa pun yang ditulis tes tersebut. Ini penting ketika Anda belajar *how to run CTest* karena memperlihatkan secara tepat apa yang terjadi di belakang layar.

Output tipikal terlihat seperti ini:

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

Jika sebuah tes gagal, log verbose akan menyertakan perintah yang gagal dan pesan error apa pun, sehingga proses debugging menjadi jauh lebih cepat.

## Step 4: Automate the Whole Workflow (Optional)

Untuk banyak proyek Anda akan menginginkan satu baris perintah yang mengonfigurasi, membangun, dan menguji sekaligus. Anda dapat mencapainya dengan skrip Bash (atau PowerShell) sederhana:

```bash
#!/usr/bin/env bash
SRC=YOUR_DIRECTORY/Examples/DocsExamples
BUILD=$SRC/build

# 1️⃣ Configure
cmake -S "$SRC" -B "$BUILD" -D CMAKE_BUILD_TYPE=Release

# 2️⃣ Build
cmake --build "$BUILD" -- -j$(nproc)

# 3️⃣ Test
cmake -E chdir "$BUILD" ctest --verbose
```

Simpan sebagai `run_all.sh`, beri hak eksekusi (`chmod +x run_all.sh`), dan Anda memiliki pipeline **cmake build and test** yang dapat direproduksi dan dapat dimasukkan ke sistem CI apa pun (GitHub Actions, GitLab CI, Azure Pipelines, sebut saja).

## Edge Cases & Common Pitfalls

| Situation | What to Watch For | Fix |
|-----------|-------------------|-----|
| **Missing compiler** | CMake aborts with “No CMAKE_CXX_COMPILER could be found.” | Install a compiler (`sudo apt install build-essential` on Ubuntu, `xcode-select --install` on macOS). |
| **Out‑of‑source folder already exists** | CMake may refuse to reconfigure if the folder contains stale files. | Delete the `build` directory (`rm -rf build`) or run `cmake --fresh` (CMake 3.24+). |
| **CTest cannot find tests** | `add_test()` was never called or the test executable failed to compile. | Verify that `add_test(NAME MyTest COMMAND MyTestExe)` appears in `CMakeLists.txt` and that the target builds. |
| **Parallel builds race on custom commands** | Some custom commands are not marked as `DEPENDS`, leading to nondeterministic failures. | Add proper `add_custom_command(... DEPENDS ...)` entries. |

Memahami nuansa ini membuat perbedaan antara build yang tidak stabil dan pipeline CI yang kokoh.

## Visual Overview (Alt text includes primary keyword)

![Diagram showing the flow of configuring, building, and testing a CMake project](/images/cmake-workflow.png "Build CMake Project workflow diagram")

## Recap – What You’ve Learned

Kami memulai dengan pertanyaan inti: *how to build CMake project* dari nol. Pada akhir tutorial Anda kini tahu cara **mengonfigurasi CMake** dengan build out‑of‑source yang bersih, **membangun CMake** menggunakan flag universal `--build`, dan **menjalankan CTest** dengan output verbose untuk memverifikasi semuanya berjalan. Anda juga memiliki skrip siap pakai yang menggabungkan ketiga langkah tersebut, memberi Anda alur kerja **cmake build and test** yang lengkap.

## What’s Next?

- **Add coverage reporting** – integrate `gcov` or `llvm-cov` and let CTest publish the results.
- **Cross‑compilation** – explore `-DCMAKE_TOOLCHAIN_FILE` for building on embedded devices.
- **Package creation** – use `cpack` to bundle your binaries for distribution.
- **CI integration** – copy the script into a GitHub Actions workflow and watch the automation run on every pull request.

Silakan bereksperimen dengan tipe build yang berbeda, tambahkan lebih banyak tes, atau ganti sumber contoh dengan proyek Anda sendiri. Pola yang kami bahas hari ini berlaku untuk basis kode apa pun yang berbasis CMake, baik itu utilitas kecil atau sistem multi‑module yang besar.

Selamat membangun, semoga build CMake Anda selalu dapat direproduksi!


## What Should You Learn Next?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [How to Export LaTeX from Word – Step‑by‑Step Guide](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [How to Display Aspose.Words Version in Python and .NET&#58; A Step-by-Step Guide](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}