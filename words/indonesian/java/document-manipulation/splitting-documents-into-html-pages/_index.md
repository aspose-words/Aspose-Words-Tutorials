---
title: Membagi Dokumen menjadi Halaman HTML di Aspose.Words untuk Java
linktitle: Membagi Dokumen menjadi Halaman HTML
second_title: API Pemrosesan Dokumen Java Aspose.Words
description: Pelajari cara membagi dokumen menjadi halaman HTML dengan Aspose.Words untuk Java. Ikuti panduan langkah demi langkah kami untuk konversi dokumen yang lancar.
weight: 25
url: /id/java/document-manipulation/splitting-documents-into-html-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membagi Dokumen menjadi Halaman HTML di Aspose.Words untuk Java


## Pengantar Membagi Dokumen ke dalam Halaman HTML di Aspose.Words untuk Java

Dalam panduan langkah demi langkah ini, kita akan menjelajahi cara membagi dokumen menjadi halaman HTML menggunakan Aspose.Words untuk Java. Aspose.Words adalah API Java yang hebat untuk bekerja dengan dokumen Microsoft Word, dan menyediakan fitur yang luas untuk manipulasi dokumen, termasuk kemampuan untuk mengonversi dokumen ke dalam berbagai format, termasuk HTML.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:

- Java Development Kit (JDK) terinstal di sistem Anda.
-  Aspose.Words untuk pustaka Java. Anda dapat mengunduhnya dari[Di Sini](https://releases.aspose.com/words/java/).

## Langkah 1: Impor Paket yang Diperlukan

```java
import com.aspose.words.*;
import java.io.*;
import java.util.ArrayList;
```

## Langkah 2: Buat Metode untuk Konversi Word ke HTML

```java
class WordToHtmlConverter
{
    // Detail implementasi untuk konversi Word ke HTML.
    // ...
}
```

## Langkah 3: Pilih Paragraf Judul sebagai Awal Topik

```java
private ArrayList<Paragraph> selectTopicStarts()
{
    NodeCollection paras = mDoc.getChildNodes(NodeType.PARAGRAPH, true);
    ArrayList<Paragraph> topicStartParas = new ArrayList<Paragraph>();
    for (Paragraph para : (Iterable<Paragraph>) paras)
    {
        int style = para.getParagraphFormat().getStyleIdentifier();
        if (style == StyleIdentifier.HEADING_1)
            topicStartParas.add(para);
    }
    return topicStartParas;
}
```

## Langkah 4: Masukkan Hentian Bagian Sebelum Judul Paragraf

```java
private void insertSectionBreaks(ArrayList<Paragraph> topicStartParas)
{
    DocumentBuilder builder = new DocumentBuilder(mDoc);
    for (Paragraph para : topicStartParas)
    {
        Section section = para.getParentSection();
        if (para != section.getBody().getFirstParagraph())
        {
            builder.moveTo(para.getFirstChild());
            builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
            section.getBody().getLastParagraph().remove();
        }
    }
}
```

## Langkah 5: Membagi Dokumen menjadi Topik

```java
private ArrayList<Topic> saveHtmlTopics() throws Exception
{
    ArrayList<Topic> topics = new ArrayList<Topic>();
    for (int sectionIdx = 0; sectionIdx < mDoc.getSections().getCount(); sectionIdx++)
    {
        Section section = mDoc.getSections().get(sectionIdx);
        String paraText = section.getBody().getFirstParagraph().getText();
        String fileName = makeTopicFileName(paraText);
        if ("".equals(fileName))
            fileName = "UNTITLED SECTION " + sectionIdx;
        fileName = mDstDir + fileName + ".html";
        String title = makeTopicTitle(paraText);
        if ("".equals(title))
            title = "UNTITLED SECTION " + sectionIdx;
        Topic topic = new Topic(title, fileName);
        topics.add(topic);
        saveHtmlTopic(section, topic);
    }
    return topics;
}
```

## Langkah 6: Simpan Setiap Topik sebagai File HTML

```java
private void saveHtmlTopic(Section section, Topic topic) throws Exception
{
    Document dummyDoc = new Document();
    dummyDoc.removeAllChildren();
    dummyDoc.appendChild(dummyDoc.importNode(section, true, ImportFormatMode.KEEP_SOURCE_FORMATTING));
    dummyDoc.getBuiltInDocumentProperties().setTitle(topic.getTitle());
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    {
        saveOptions.setPrettyFormat(true);
        saveOptions.setAllowNegativeIndent(true);
        saveOptions.setExportHeadersFootersMode(ExportHeadersFootersMode.NONE);
    }
    dummyDoc.save(topic.getFileName(), saveOptions);
}
```

## Langkah 7: Buat Daftar Isi untuk Topik

```java
private void saveTableOfContents(ArrayList<Topic> topics) throws Exception
{
    Document tocDoc = new Document(mTocTemplate);
    tocDoc.getMailMerge().setFieldMergingCallback(new HandleTocMergeField());
    tocDoc.getMailMerge().executeWithRegions(new TocMailMergeDataSource(topics));
    tocDoc.save(mDstDir + "contents.html");
}
```

Setelah kami menguraikan langkah-langkahnya, Anda dapat menerapkan setiap langkah dalam proyek Java Anda untuk membagi dokumen menjadi halaman HTML menggunakan Aspose.Words untuk Java. Proses ini akan memungkinkan Anda membuat representasi HTML terstruktur dari dokumen Anda, sehingga lebih mudah diakses dan ramah pengguna.

## Kesimpulan

Dalam panduan lengkap ini, kami telah membahas proses pemisahan dokumen menjadi halaman HTML menggunakan Aspose.Words untuk Java. Dengan mengikuti langkah-langkah yang diuraikan, Anda dapat mengonversi dokumen Word ke dalam format HTML secara efisien, sehingga konten Anda lebih mudah diakses di web.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara menginstal Aspose.Words untuk Java?

 Untuk menginstal Aspose.Words untuk Java, Anda dapat mengunduh pustaka dari[Di Sini](https://releases.aspose.com/words/java/) dan ikuti petunjuk instalasi yang disediakan dalam dokumentasi.

### Bisakah saya menyesuaikan keluaran HTML?

 Ya, Anda dapat menyesuaikan output HTML dengan menyesuaikan opsi penyimpanan di`HtmlSaveOptions` kelas. Ini memungkinkan Anda untuk mengontrol format dan tampilan file HTML yang dihasilkan.

### Versi Microsoft Word apa yang didukung oleh Aspose.Words untuk Java?

Aspose.Words untuk Java mendukung berbagai format dokumen Microsoft Word, termasuk DOC, DOCX, RTF, dan banyak lagi. Aplikasi ini kompatibel dengan berbagai versi Microsoft Word.

### Bagaimana saya dapat menangani gambar dalam HTML yang dikonversi?

Aspose.Words untuk Java dapat menangani gambar dalam HTML yang dikonversi dengan menyimpannya sebagai file terpisah dalam folder yang sama dengan file HTML. Ini memastikan bahwa gambar ditampilkan dengan benar dalam keluaran HTML.

### Apakah ada versi uji coba Aspose.Words untuk Java yang tersedia?

Ya, Anda dapat meminta versi uji coba gratis Aspose.Words untuk Java dari situs web Aspose untuk mengevaluasi fitur dan kemampuannya sebelum membeli lisensi.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
