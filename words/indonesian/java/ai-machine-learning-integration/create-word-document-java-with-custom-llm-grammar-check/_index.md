---
category: general
date: 2026-05-04
description: Buat dokumen Word Java menggunakan Aspose.Words dan pelajari cara memeriksa
  tata bahasa dengan LLM khusus. Panduan langkah demi langkah untuk pengembang Java.
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: id
og_description: Buat dokumen Word Java dan lihat cara memeriksa tata bahasa menggunakan
  LLM khusus. Tutorial Java lengkap dengan kode yang dapat dijalankan.
og_title: Buat dokumen Word Java dengan Pemeriksaan Tata Bahasa LLM Kustom
tags:
- Java
- Aspose.Words
- LLM
title: Buat dokumen Word Java dengan Pemeriksaan Tata Bahasa LLM Kustom
url: /id/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat word document java dengan Pemeriksaan Tata Bahasa LLM Kustom

Pernah bertanya-tanya bagaimana cara **create word document java** proyek yang juga dapat memeriksa diri mereka sendiri? Anda tidak sendirian—banyak pengembang menginginkan satu alur kerja yang menghasilkan file *.docx* yang halus tanpa harus mengelola banyak alat. Dalam tutorial ini kami akan membahas langkah demi langkah, menunjukkan **how to create docx** file dengan Aspose.Words, menghubungkan LLM yang dihosting secara lokal, dan akhirnya **how to check grammar** secara otomatis. Pada akhir Anda akan memiliki program Java yang berdiri sendiri yang menulis, memvalidasi, dan menyimpan dokumen Word—semua sambil **using custom LLM** endpoint yang Anda kontrol.

## Apa yang Anda Butuhkan

| Prasyarat | Mengapa penting |
|--------------|----------------|
| Java 17+ (or any recent JDK) | Fitur bahasa modern dan dukungan modul yang lebih baik |
| Aspose.Words for Java (latest version) | Pustaka yang memungkinkan Anda **create word document java** file secara programatis |
| A locally hosted LLM server (e.g., Ollama, LMStudio) listening on `http://localhost:11434/api/generate` | Diperlukan untuk langkah **use custom llm** yang mendukung pemeriksaan tata bahasa |
| Maven or Gradle (we’ll use Maven in examples) | Menyederhanakan manajemen dependensi |
| An IDE or text editor (IntelliJ IDEA, VS Code, etc.) | Mempermudah penulisan kode dan debugging |

Jika ada yang terdengar tidak familiar, jangan panik—setiap item gratis atau memiliki edisi komunitas yang berfungsi sempurna untuk tujuan belajar.

## Langkah 1 – Siapkan Proyek Maven Anda

Untuk **create word document java** proyek dengan cepat, mulailah dengan `pom.xml` Maven minimal. File ini mengimpor pustaka Aspose.Words dan klien HTTP apa pun yang Anda pilih (kami akan menggunakan Apache HttpClient).

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-llm-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- replace with the latest -->
        </dependency>

        <!-- Apache HttpClient for calling the LLM endpoint -->
        <dependency>
            <groupId>org.apache.httpcomponents.client5</groupId>
            <artifactId>httpclient5</artifactId>
            <version>5.2</version>
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Jika Anda menggunakan Gradle, dependensi yang sama diletakkan di bawah `implementation` dalam `build.gradle`.

Sekarang jalankan `mvn clean install` untuk mengunduh jar. Setelah build berhasil Anda siap menulis kode Java yang **creates word document java** file.

## Langkah 2 – Tulis Kelas Java yang **Creates word document java**

Berikut adalah file sumber lengkap yang siap dijalankan. Ini mendemonstrasikan alur lengkap: menginisialisasi dokumen kosong, mengonfigurasi endpoint LLM kustom, memanggil pemeriksaan tata bahasa, dan akhirnya menyimpan hasilnya.

```java
package com.example.wordllmdemo;

import com.aspose.words.*;
import com.aspose.words.ai.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

/**
 * Demonstrates how to create a Word document in Java and run a grammar‑check
 * using a self‑hosted LLM (e.g., Ollama). This example is fully self‑contained
 * and can be executed with a single `java -cp` command after Maven builds.
 */
public class SelfHostedLLMDemo {

    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 2.1 – Create an empty Word document
        // -----------------------------------------------------------------
        Document document = new Document(); // this is the object that will become your .docx

        // Add a simple paragraph so the grammar engine has something to work with
        DocumentBuilder builder = new DocumentBuilder(document);
        builder.writeln("Ths sentence has a typo and a grammer error.");

        // -----------------------------------------------------------------
        // Step 2.2 – Configure the custom LLM endpoint (use custom llm)
        // -----------------------------------------------------------------
        AiEndpoint llmEndpoint = new AiEndpoint();
        llmEndpoint.setBaseUrl("http://localhost:11434/api/generate");
        llmEndpoint.setModel("llama3.1:8b"); // make sure this model is available locally

        // Initialise the Document AI engine with the endpoint we just set up
        DocumentAi documentAi = new DocumentAi(llmEndpoint);

        // -----------------------------------------------------------------
        // Step 2.3 – Run grammar checking (how to check grammar)
        // -----------------------------------------------------------------
        // AiModelType.CUSTOM tells the API to forward the request to our LLM
        documentAi.checkGrammar(document, AiModelType.CUSTOM);

        // -----------------------------------------------------------------
        // Step 2.4 – Save the corrected file
        // -----------------------------------------------------------------
        String outputPath = "output/GrammarChecked.docx";
        // Ensure the directory exists
        Files.createDirectories(Path.of("output"));
        document.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

> **Mengapa ini berhasil:**  
> * `Document` adalah kelas inti Aspose.Words yang merepresentasikan *.docx* dalam memori.  
> * `AiEndpoint` memberi tahu modul AI Aspose ke mana mengirim prompt. Dengan mengarahkannya ke `localhost:11434` kami **use custom llm** alih-alih layanan cloud.  
> * `checkGrammar` dengan `AiModelType.CUSTOM` meneruskan teks dokumen ke LLM, menerima teks yang telah dikoreksi, dan menulis ulang node Word yang mendasarinya.  
> * Akhirnya kami memanggil `save` untuk menulis file ke disk, memberikan Anda file Word yang halus.

### Output yang Diharapkan

Setelah menjalankan `mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` Anda akan melihat:

```
Document saved to output/GrammarChecked.docx
```

Buka `GrammarChecked.docx` yang dihasilkan di Microsoft Word (atau LibreOffice). Kalimat asli *“Ths sentence has a typo and a grammer error.”* kini menjadi *“This sentence has a typo and a grammar error.”* – bukti bahwa langkah **how to check grammar** berhasil.

## Langkah 3 – Cara membuat docx dengan Konten Berbeda (Opsional)

Jika Anda ingin menghasilkan dokumen yang lebih kaya—tabel, gambar, atau teks bergaya—cukup terus gunakan `DocumentBuilder`. Berikut cuplikan singkat yang mendemonstrasikan penambahan heading dan tabel:

```java
// Adding a heading
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Demo Report");

// Adding a 2x2 table
Table table = builder.startTable();
builder.insertCell();
builder.write("Item");
builder.insertCell();
builder.write("Quantity");
builder.endRow();

builder.insertCell();
builder.write("Apples");
builder.insertCell();
builder.write("42");
builder.endRow();
builder.endTable();
```

Anda dapat menempatkan kode ini di mana saja antara blok pembuatan dokumen (Langkah 2.1) dan pemanggilan pemeriksaan tata bahasa (Langkah 2.3). LLM tetap akan menerima seluruh teks, sehingga dapat memperbaiki bagian bahasa alami sambil membiarkan tabel tidak tersentuh.

## Langkah 4 – Menangani Masalah Endpoint (Gunakan Custom LLM dengan Aman)

Saat **using custom llm** endpoint, beberapa masalah umum dapat terjadi:

| Gejala | Penyebab kemungkinan | Perbaikan |
|---------|----------------------|-----------|
| `Connection refused` error | Server LLM tidak berjalan atau port salah | Mulai Ollama (`ollama serve`) dan verifikasi `http://localhost:11434/api/generate` berfungsi dengan `curl`. |
| Response JSON tidak memiliki field `completion` | Nama model tidak cocok | Pastikan model yang Anda set (`llama3.1:8b`) terinstal (`ollama list`). |
| Pemeriksaan tata bahasa mengembalikan teks asli tanpa perubahan | Prompt tidak dikenali oleh LLM | Sesuaikan sistem model |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}