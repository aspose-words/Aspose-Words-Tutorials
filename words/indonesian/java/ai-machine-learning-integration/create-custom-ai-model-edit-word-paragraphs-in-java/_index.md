---
category: general
date: 2026-03-25
description: Buat model AI khusus untuk mengedit dokumen Word – pelajari cara membuat
  teks lebih formal, mengganti teks paragraf, dan menulis ulang paragraf Word menggunakan
  Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: id
og_description: Buat model AI khusus untuk mengedit dokumen Word. Pelajari cara membuat
  teks lebih formal, mengganti teks paragraf, dan menulis ulang paragraf Word menggunakan
  Aspose.Words AI.
og_title: Buat Model AI Kustom – Edit Paragraf Word di Java
tags:
- Aspose.Words
- Java
- AI integration
title: Buat Model AI Kustom – Edit Paragraf Word di Java
url: /id/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Model AI Kustom – Edit Paragraf Word di Java

Pernah membutuhkan **create custom AI model** yang dapat memperhalus sebuah paragraf di dalam file Word? Mungkin Anda memiliki sekumpulan kontrak yang terdengar terlalu santai, dan Anda ingin membuat teks menjadi lebih formal dengan satu baris kode. Kabar baiknya, Anda dapat melakukan hal itu—tanpa layanan eksternal, tanpa SDK berat, hanya Aspose.Words untuk Java dan endpoint yang kompatibel dengan OpenAI.

Dalam tutorial ini kami akan menjelaskan setiap langkah yang diperlukan untuk **create custom AI model**, menghubungkannya ke server LLM lokal, dan kemudian menggunakannya untuk *replace paragraph text* dengan versi yang lebih formal. Pada akhir tutorial Anda akan memiliki program Java yang dapat dijalankan yang **edit paragraph with AI**, menulis ulang paragraf Word, dan menyimpan hasilnya kembali ke disk. Tanpa embel‑embel, hanya solusi praktis yang dapat Anda salin‑tempel ke proyek Anda.

> **Apa yang Anda butuhkan**  
> • Java 17 atau lebih baru (kode dapat dikompilasi dengan versi lebih lama, tetapi 17 adalah pilihan terbaik)  
> • Aspose.Words for Java 23.9 (atau rilis terbaru)  
> • Server LLM yang kompatibel dengan OpenAI yang sedang berjalan (mis., Ollama, LocalAI) yang mendengarkan pada `http://localhost:8000/v1`  
> • Dokumen Word input (`input.docx`) yang ditempatkan di folder yang Anda kontrol  

Jika Anda bertanya-tanya *why bother building a custom model* alih‑alih memanggil OpenAI secara langsung, jawabannya adalah fleksibilitas: Anda mengontrol endpoint, dapat mengganti model tanpa mengubah kode, dan Anda menyimpan kunci API di luar repositori sumber Anda. Mari kita mulai.

---

## Buat Model AI Kustom – Pengaturan dan Konfigurasi

Pertama, kita perlu memberi tahu Aspose.Words di mana LLM kami berada. Kelas `AiModelEndpoint` menyimpan URL dan kunci API opsional. Karena kita menggunakan server lokal, kunci dapat berupa string kosong, tetapi parameter tetap diperlukan.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Pro tip:** Jika Anda pernah beralih ke model yang dihosting (mis., Azure OpenAI), cukup ubah URL dan kunci—tidak ada perubahan kode lain yang diperlukan.

---

## Muat Dokumen Word

Sekarang kami memuat file sumber ke memori. `Document` dapat membaca `.docx`, `.doc`, `.rtf`, dan banyak format lainnya, tetapi untuk contoh ini kami tetap menggunakan `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Pastikan `YOUR_DIRECTORY` mengarah ke folder yang nyata; jika tidak, Anda akan mendapatkan `FileNotFoundException`. Dalam aplikasi dunia nyata, Anda mungkin melewatkan path sebagai argumen baris perintah atau membacanya dari file konfigurasi.

---

## Inisialisasi Model AI Kustom

Kami membuat `AiModel` dengan tipe `CUSTOM` dan memberikannya endpoint yang telah kami definisikan sebelumnya. Ini memberi tahu Aspose.Words untuk mengarahkan semua panggilan AI melalui server kami sendiri.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Di balik layar, Aspose.Words membangun klien HTTP kecil yang berkomunikasi dengan LLM menggunakan skema chat/completion standar OpenAI. Itulah mengapa endpoint harus *OpenAI‑compatible*.

---

## Ambil dan Tulis Ulang Paragraf Pertama

Di sinilah kami benar‑benar **make text more formal**. Kami mengambil paragraf pertama, mengirim teks mentahnya ke model dengan prompt, dan menerima versi yang telah diedit.

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

Argumen kedua (`"Make it more formal"`) adalah instruksi yang kami berikan kepada model. Anda dapat menggantinya dengan perintah apa pun—**replace paragraph text**, **summarize**, **translate**, dll. Metode ini mengembalikan string biasa, yang nanti akan kami sisipkan kembali ke dalam dokumen.

> **Why this works:** `editText` mengirim payload JSON seperti `{ \"model\": \"...\", \"messages\": [{ \"role\":\"user\", \"content\":\"<text>\\nMake it more formal\"}] }`. LLM melihat paragraf asli dan instruksi, kemudian membalas dengan teks yang telah direvisi.

---

## Ganti Konten Paragraf Asli

Sekarang kami **replace paragraph text** di dalam model objek Word. Kami menghapus semua run yang ada (potongan teks tingkat rendah) dan menyisipkan `Run` baru yang berisi string yang dihasilkan AI.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Hati‑hati jangan memanggil `firstParagraph.setText()`—metode itu akan menghapus semua format. Menggunakan `Run` mempertahankan gaya paragraf (heading, bullet, dll.) sambil mengganti karakter sebenarnya.

---

## Simpan Dokumen yang Diedit

Akhirnya, kami menulis dokumen yang telah dimodifikasi kembali ke disk. Anda dapat menimpa file asli atau, seperti yang kami lakukan di sini, membuat salinan baru.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Ketika Anda membuka `output.docx`, Anda akan melihat paragraf pertama kini terdengar jauh lebih formal. Jika LLM tidak mengikuti instruksi dengan sempurna, Anda dapat menyesuaikan prompt atau mencoba versi model yang berbeda.

---

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap—salin ke `LlmDemo.java`, sesuaikan path, dan jalankan dengan `javac` + `java`.

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Expected output:** Buka `output.docx` dan Anda akan melihat paragraf asli telah diubah. Misalnya, kalimat santai seperti “We’ll get the thing done soon.” dapat menjadi “We shall complete the task promptly.” Pilihan kata tepat tergantung pada model yang Anda gunakan.

---

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika dokumen saya memiliki banyak bagian?

Kode di atas hanya memodifikasi paragraf *pertama* dari *bagian pertama*. Untuk **edit paragraph with AI** di seluruh file, lakukan loop melalui `document.getSections()` dan kemudian setiap `section.getBody().getParagraphs()`. Ingat untuk melewatkan paragraf kosong, jika tidak LLM akan menerima string kosong dan tidak mengembalikan apa‑apa.

### Bagaimana cara menangani paragraf besar yang melebihi batas token?

Sebagian besar LLM membatasi input sekitar 4 000 token. Jika sebuah paragraf terlalu panjang, bagi menjadi potongan lebih kecil sebelum memanggil `editText`. Anda dapat menggunakan kembali instance `AiModel` yang sama; hanya perlu memperhatikan batas kecepatan pada server lokal Anda.

### Bisakah saya menggunakan instruksi lain, seperti “summarize” atau “translate to French”?

Tentu saja. Argumen kedua untuk `editText` bersifat bebas. Untuk ringkasan, Anda dapat memberikan `"Summarize in one sentence"`. Untuk terjemahan, `"Translate to French, keep the tone formal"` juga berfungsi. Fleksibilitas ini memungkinkan Anda **replace paragraph text** untuk banyak skenario tanpa mengubah kode apa pun.

### Apakah model mempertahankan gaya paragraf (font, warna)?

Karena kami hanya mengganti `Run` di dalam objek `Paragraph` yang sama, gaya yang ada (tingkat heading, daftar bullet, indentasi) tetap utuh. Jika Anda perlu mengubah gaya itu sendiri, Anda dapat memanipulasi `Paragraph.getParagraphFormat()` setelah penggantian.

### Bagaimana jika server LLM saya memerlukan HTTPS dengan sertifikat self‑signed?

`AiModelEndpoint` menerima URL dengan `https://`. Jika sertifikat tidak dipercaya, Anda harus mengonfigurasi konteks SSL Java untuk mempercayainya, atau menjalankan server dengan sertifikat yang valid. Penyiapan tersebut berada di luar lingkup tutorial ini tetapi terdokumentasi dengan baik dalam panduan SSL Java.

---

## Tips untuk Integrasi Siap Produksi

| Tip | Mengapa penting |
|-----|-----------------|
| **Cache endpoint** | Membuat ulang `AiModelEndpoint` pada setiap permintaan menambah beban. |
| **Batch edits** | Jika Anda memiliki banyak paragraf, kirimkan mereka dalam satu permintaan (mis., array JSON) untuk mengurangi latensi. |
| **Validate LLM output** | Selalu periksa string yang dikembalikan apakah null atau kosong sebelum menyisipkan. |
| **Log prompts and responses** | Bermanfaat untuk debugging dan kepatuhan saat Anda menulis ulang teks legal. |
| **Graceful fallback** | Jika LLM tidak tersedia, kembali ke paragraf asli atau penulisan ulang heuristik sederhana. |

---

## Kesimpulan

Kami telah menunjukkan cara **create custom AI model** dengan Aspose.Words, menghubungkannya ke endpoint yang kompatibel dengan OpenAI, dan kemudian **edit paragraph with AI** untuk **make text more formal**. Dengan mengikuti enam langkah—menentukan endpoint, memuat dokumen, menginisialisasi model,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}