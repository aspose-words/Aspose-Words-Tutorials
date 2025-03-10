---
title: Dzielenie dokumentów na strony HTML w Aspose.Words dla Java
linktitle: Dzielenie dokumentów na strony HTML
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Dowiedz się, jak dzielić dokumenty na strony HTML za pomocą Aspose.Words for Java. Postępuj zgodnie z naszym przewodnikiem krok po kroku, aby uzyskać bezproblemową konwersję dokumentów.
weight: 25
url: /pl/java/document-manipulation/splitting-documents-into-html-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dzielenie dokumentów na strony HTML w Aspose.Words dla Java


## Wprowadzenie do dzielenia dokumentów na strony HTML w Aspose.Words dla Java

W tym przewodniku krok po kroku pokażemy, jak dzielić dokumenty na strony HTML za pomocą Aspose.Words dla Java. Aspose.Words to potężne API Java do pracy z dokumentami Microsoft Word, które oferuje rozbudowane funkcje do manipulacji dokumentami, w tym możliwość konwersji dokumentów do różnych formatów, w tym HTML.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że spełnione są następujące wymagania wstępne:

- Java Development Kit (JDK) zainstalowany w Twoim systemie.
-  Biblioteka Aspose.Words dla Java. Możesz ją pobrać z[Tutaj](https://releases.aspose.com/words/java/).

## Krok 1: Importuj niezbędne pakiety

```java
import com.aspose.words.*;
import java.io.*;
import java.util.ArrayList;
```

## Krok 2: Utwórz metodę konwersji Worda do HTML

```java
class WordToHtmlConverter
{
    // Szczegóły implementacji konwersji z formatu Word do formatu HTML.
    // ...
}
```

## Krok 3: Wybierz nagłówki akapitów jako początek tematu

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

## Krok 4: Wstaw podziały sekcji przed akapitami nagłówkowymi

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

## Krok 5: Podziel dokument na tematy

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

## Krok 6: Zapisz każdy temat jako plik HTML

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

## Krok 7: Utwórz spis treści dla tematów

```java
private void saveTableOfContents(ArrayList<Topic> topics) throws Exception
{
    Document tocDoc = new Document(mTocTemplate);
    tocDoc.getMailMerge().setFieldMergingCallback(new HandleTocMergeField());
    tocDoc.getMailMerge().executeWithRegions(new TocMailMergeDataSource(topics));
    tocDoc.save(mDstDir + "contents.html");
}
```

Teraz, gdy opisaliśmy kroki, możesz wdrożyć każdy krok w swoim projekcie Java, aby podzielić dokumenty na strony HTML za pomocą Aspose.Words for Java. Ten proces pozwoli Ci utworzyć ustrukturyzowaną reprezentację HTML Twoich dokumentów, czyniąc je bardziej dostępnymi i przyjaznymi dla użytkownika.

## Wniosek

W tym kompleksowym przewodniku omówiliśmy proces dzielenia dokumentów na strony HTML przy użyciu Aspose.Words for Java. Postępując zgodnie z opisanymi krokami, możesz sprawnie konwertować dokumenty Word do formatu HTML, dzięki czemu Twoja treść będzie bardziej dostępna w sieci.

## Najczęściej zadawane pytania

### Jak zainstalować Aspose.Words dla Java?

 Aby zainstalować Aspose.Words dla Java, możesz pobrać bibliotekę ze strony[Tutaj](https://releases.aspose.com/words/java/) i postępuj zgodnie z instrukcjami instalacji podanymi w dokumentacji.

### Czy mogę dostosować wynik HTML?

 Tak, możesz dostosować wyjście HTML, dostosowując opcje zapisu w`HtmlSaveOptions` Klasa. Pozwala to kontrolować formatowanie i wygląd generowanych plików HTML.

### Jakie wersje programu Microsoft Word są obsługiwane przez Aspose.Words for Java?

Aspose.Words for Java obsługuje szeroki zakres formatów dokumentów Microsoft Word, w tym DOC, DOCX, RTF i inne. Jest kompatybilny z różnymi wersjami Microsoft Word.

### Jak mogę obsługiwać obrazy w przekonwertowanym kodzie HTML?

Aspose.Words for Java może obsługiwać obrazy w przekonwertowanym HTML, zapisując je jako oddzielne pliki w tym samym folderze co plik HTML. Zapewnia to, że obrazy są wyświetlane poprawnie w wyjściu HTML.

### Czy jest dostępna wersja próbna Aspose.Words dla Java?

Tak, możesz poprosić o bezpłatną wersję próbną Aspose.Words for Java na stronie internetowej Aspose, aby ocenić jej funkcje i możliwości przed zakupem licencji.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
