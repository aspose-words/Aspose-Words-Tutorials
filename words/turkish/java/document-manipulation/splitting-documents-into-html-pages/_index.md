---
title: Aspose.Words for Java'da Belgeleri HTML Sayfalarına Bölme
linktitle: Belgeleri HTML Sayfalarına Bölme
second_title: Aspose.Words Java Belge İşleme API'si
description: Aspose.Words for Java ile belgeleri HTML sayfalarına nasıl böleceğinizi öğrenin. Sorunsuz belge dönüşümü için adım adım kılavuzumuzu izleyin.
weight: 25
url: /tr/java/document-manipulation/splitting-documents-into-html-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java'da Belgeleri HTML Sayfalarına Bölme


## Aspose.Words for Java'da Belgeleri HTML Sayfalarına Bölmeye Giriş

Bu adım adım kılavuzda, Aspose.Words for Java kullanarak belgeleri HTML sayfalarına nasıl böleceğinizi inceleyeceğiz. Aspose.Words, Microsoft Word belgeleriyle çalışmak için güçlü bir Java API'sidir ve belgeleri HTML de dahil olmak üzere çeşitli biçimlere dönüştürme yeteneği de dahil olmak üzere belge düzenleme için kapsamlı özellikler sağlar.

## Ön koşullar

Başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

- Sisteminizde Java Geliştirme Kiti (JDK) yüklü.
-  Aspose.Words for Java kütüphanesi. Buradan indirebilirsiniz[Burada](https://releases.aspose.com/words/java/).

## Adım 1: Gerekli Paketleri İçe Aktarın

```java
import com.aspose.words.*;
import java.io.*;
import java.util.ArrayList;
```

## Adım 2: Word'den HTML'e Dönüştürme Yöntemi Oluşturun

```java
class WordToHtmlConverter
{
    // Word'den HTML'e dönüştürme için uygulama detayları.
    // ...
}
```

## Adım 3: Konu Başlangıcı Olarak Başlık Paragraflarını Seçin

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

## Adım 4: Başlık Paragraflarından Önce Bölüm Sonlarını Ekleyin

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

## Adım 5: Belgeyi Konulara Ayırın

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

## Adım 6: Her Konuyu HTML Dosyası Olarak Kaydedin

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

## Adım 7: Konular için İçindekiler Tablosu Oluşturun

```java
private void saveTableOfContents(ArrayList<Topic> topics) throws Exception
{
    Document tocDoc = new Document(mTocTemplate);
    tocDoc.getMailMerge().setFieldMergingCallback(new HandleTocMergeField());
    tocDoc.getMailMerge().executeWithRegions(new TocMailMergeDataSource(topics));
    tocDoc.save(mDstDir + "contents.html");
}
```

Artık adımları özetlediğimize göre, Aspose.Words for Java kullanarak belgeleri HTML sayfalarına bölmek için her adımı Java projenizde uygulayabilirsiniz. Bu süreç, belgelerinizin yapılandırılmış bir HTML gösterimini oluşturmanıza olanak tanır ve bunları daha erişilebilir ve kullanıcı dostu hale getirir.

## Çözüm

Bu kapsamlı kılavuzda, Aspose.Words for Java kullanarak belgeleri HTML sayfalarına bölme sürecini ele aldık. Belirtilen adımları izleyerek, Word belgelerini HTML biçimine verimli bir şekilde dönüştürebilir ve içeriğinizi web'de daha erişilebilir hale getirebilirsiniz.

## SSS

### Java için Aspose.Words'ü nasıl yüklerim?

 Java için Aspose.Words'ü yüklemek için kütüphaneyi şu adresten indirebilirsiniz:[Burada](https://releases.aspose.com/words/java/) ve dokümanlarda verilen kurulum talimatlarını izleyin.

### HTML çıktısını özelleştirebilir miyim?

 Evet, HTML çıktısını, kaydetme seçeneklerini ayarlayarak özelleştirebilirsiniz.`HtmlSaveOptions` sınıf. Bu, oluşturulan HTML dosyalarının biçimlendirmesini ve görünümünü kontrol etmenizi sağlar.

### Aspose.Words for Java hangi Microsoft Word sürümlerini destekliyor?

Aspose.Words for Java, DOC, DOCX, RTF ve daha fazlası dahil olmak üzere çok çeşitli Microsoft Word belge formatlarını destekler. Microsoft Word'ün çeşitli sürümleriyle uyumludur.

### Dönüştürülen HTML'deki görselleri nasıl işleyebilirim?

Java için Aspose.Words, dönüştürülen HTML'deki resimleri, HTML dosyasıyla aynı klasörde ayrı dosyalar olarak kaydederek işleyebilir. Bu, resimlerin HTML çıktısında doğru şekilde görüntülenmesini sağlar.

### Aspose.Words for Java'nın deneme sürümü mevcut mu?

Evet, lisans satın almadan önce Aspose.Words for Java'nın özelliklerini ve yeteneklerini değerlendirmek için Aspose web sitesinden Aspose.Words for Java'nın ücretsiz deneme sürümünü talep edebilirsiniz.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
