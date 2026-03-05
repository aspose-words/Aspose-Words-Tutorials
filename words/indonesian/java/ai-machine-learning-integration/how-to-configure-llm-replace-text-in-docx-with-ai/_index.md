---
category: general
date: 2026-03-04
description: Cara mengkonfigurasi LLM untuk Document AI dan mengganti teks dalam DOCX
  menggunakan AI – panduan langkah demi langkah dengan kode Java lengkap.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: id
og_description: Cara mengonfigurasi LLM untuk Document AI dan mengganti teks dalam
  DOCX menggunakan AI – panduan lengkap dengan kode Java yang dapat dijalankan.
og_title: Cara Mengonfigurasi LLM – Ganti Teks di DOCX dengan AI
tags:
- LLM
- Document AI
- Java
- DOCX
title: Cara Mengonfigurasi LLM – Ganti Teks di DOCX dengan AI
url: /id/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengonfigurasi LLM – Mengganti Teks di DOCX dengan AI

Pernah bertanya-tanya **how to configure LLM** sehingga dapat mengedit file Word untuk Anda? Anda bukan satu-satunya. Banyak pengembang menemui kendala ketika mereka perlu mengganti frasa secara programatis di dalam `.docx` tanpa membuka Microsoft Word. Kabar baiknya? Dengan LLM lokal dan pembungkus Document AI yang kecil, Anda dapat menukar teks dalam file DOCX hanya dengan beberapa baris Java.

Pada tutorial ini kami akan membahas seluruh proses: mulai dari menghubungkan LLM, memuat DOCX, hingga menggunakan **Document AI** untuk mengganti frasa target. Pada akhir tutorial Anda akan memiliki contoh yang mandiri dan dapat dijalankan yang dapat Anda masukkan ke proyek Maven atau Gradle mana pun. Tanpa kunci API eksternal, tanpa biaya cloud—hanya model Anda sendiri yang mendengarkan pada `http://localhost:8080/v1`.

> **Quick win:** Jika Anda sudah memiliki LLM lokal (seperti Llama 3 atau Mistral) yang mengekspos endpoint kompatibel OpenAI, kode di bawah ini langsung dapat digunakan.

---

![Diagram cara mengonfigurasi LLM untuk Document AI](/images/configure-llm-diagram.png){: .center-image alt="diagram cara mengonfigurasi llm"}

## Apa yang Anda Butuhkan

- **Java 17** (atau JDK terbaru apa pun)  
- Sebuah **local LLM** yang mengekspos endpoint gaya OpenAI `/v1` (mis., Ollama, LMStudio)  
- **Document AI Java library** (asumsikan `com.example:document-ai:1.2.0` di Maven Central)  
- File DOCX contoh (`input.docx`) yang ditempatkan di folder yang diketahui  

Jika Anda belum memiliki salah satu dari ini, jalankan Ollama dengan cepat:

```bash
ollama serve &
ollama run llama3
```

Itu akan memulai server pada `http://localhost:8080/v1` siap menerima permintaan.

---

## Cara Mengonfigurasi LLM untuk Document AI

Hal pertama yang kami lakukan adalah memberi tahu klien `DocumentAi` di mana menemukan model dan model mana yang akan digunakan. Ini adalah langkah **how to configure LLM** yang banyak tutorial lewati.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Mengapa ini penting:*  
Objek `AiModelConfig` menyembunyikan detail HTTP, memungkinkan `DocumentAi` fokus pada konten. Jika Anda pernah beralih ke penyedia yang dihosting, Anda hanya mengubah `baseUrl` dan `apiKey`—sisanya tetap tidak berubah.

---

## Muat dan Siapkan Dokumen DOCX

Selanjutnya kami memuat file Word ke dalam memori. Kelas `Document` menangani baik `.docx` maupun `.pdf` di balik layar, tetapi di sini kami hanya peduli pada DOCX.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Tips profesional:* Gunakan path absolut saat debugging untuk menghindari kejutan “file tidak ditemukan”. Setelah Anda yakin, kembali ke path relatif untuk portabilitas.

---

## Ganti Teks di DOCX Menggunakan AI

Sekarang masuk ke inti tutorial—**how to replace text** dalam file DOCX dengan bantuan AI. Metode `replaceText` mengirimkan isi dokumen ke LLM, meminta LLM melakukan substitusi, dan mengembalikan teks yang telah direvisi.

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*Apa yang terjadi di balik layar?*  
`DocumentAi` men-serialisasi DOCX menjadi teks biasa, membuat prompt seperti:

> “Dalam dokumen berikut, ganti setiap kemunculan ‘old phrase’ dengan ‘new phrase’ dan kembalikan hanya teks yang telah diperbarui.”

LLM memproses permintaan dan mengirim kembali konten yang dimodifikasi. Pendekatan ini bekerja bahkan ketika frasa tersebut melintasi beberapa run atau paragraf—sesuatu yang sering terlewat oleh penggantian string biasa.

---

## Verifikasi dan Output Teks yang Direvisi

Akhirnya kami mencetak teks yang direvisi AI ke konsol. Dalam aplikasi dunia nyata Anda mungkin menulis hasilnya kembali ke DOCX baru, tetapi mencetak memungkinkan Anda memverifikasi dengan cepat.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Output yang diharapkan** (dengan asumsi DOCX asli berisi “This is the old phrase we want to change.”):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Jika Anda melihat frasa baru muncul, selamat—**Anda baru saja belajar cara menggunakan Document AI untuk mengganti frasa dengan AI**.

---

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut kelas Java lengkap yang siap dijalankan. Silakan salin‑tempel ke `src/main/java/com/example/ReplaceInDocx.java`.

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### Cara Menjalankan

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Pastikan server LLM sudah berjalan sebelum Anda menjalankan program; jika tidak, Anda akan mendapatkan timeout koneksi.

---

## Kasus Pinggir & Kesalahan Umum

| Situasi | Hal yang Perlu Diperhatikan | Solusi yang Disarankan |
|-----------|-------------------|---------------|
| **Phrase not found** | LLM mengembalikan teks asli tanpa perubahan. | Periksa kembali ejaan dan sensitivitas huruf; Anda dapat menambahkan `ignoreCase:true` ke prompt jika wrapper Anda mendukungnya. |
| **Large documents (>5 MB)** | Ukuran prompt mungkin melebihi batas token model. | Bagi DOCX menjadi beberapa bagian, proses masing‑masing secara terpisah, lalu gabungkan hasilnya. |
| **Local LLM returns errors** | Sering disebabkan oleh nama model yang tidak cocok. | Verifikasi nama model di UI LLM (`ollama list`) cocok dengan `modelConfig.setModelName`. |
| **Unicode characters get garbled** | Masalah enkoding saat membaca DOCX. | Pastikan runtime Java Anda menggunakan UTF‑8 (tambahkan `-Dfile.encoding=UTF-8` ke argumen JVM). |

---

## Langkah Selanjutnya

Setelah Anda mengetahui **how to replace text in DOCX** dengan AI, Anda mungkin ingin menjelajahi:

- **How to use Document AI** untuk tugas yang lebih kompleks seperti ekstraksi tabel atau pelestarian gaya.  
- **Replace phrase with AI** di PDF dengan mengganti argumen konstruktor `Document`.  
- **Batch processing**: iterasi melalui direktori file DOCX dan terapkan penggantian yang sama.  

Setiap hal ini dibangun di atas fondasi `AiModelConfig` dan `DocumentAi` yang sama, sehingga Anda tidak perlu memulai dari awal

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}