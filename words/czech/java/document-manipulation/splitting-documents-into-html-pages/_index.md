---
"description": "Naučte se, jak rozdělit dokumenty na HTML stránky pomocí Aspose.Words pro Javu. Postupujte podle našeho podrobného návodu pro bezproblémovou konverzi dokumentů."
"linktitle": "Rozdělení dokumentů na HTML stránky"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Rozdělení dokumentů na HTML stránky v Aspose.Words pro Javu"
"url": "/cs/java/document-manipulation/splitting-documents-into-html-pages/"
"weight": 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rozdělení dokumentů na HTML stránky v Aspose.Words pro Javu


## Úvod do dělení dokumentů na HTML stránky v Aspose.Words pro Javu

V tomto podrobném návodu se podíváme na to, jak rozdělit dokumenty na HTML stránky pomocí Aspose.Words pro Javu. Aspose.Words je výkonné Java API pro práci s dokumenty Microsoft Word, které poskytuje rozsáhlé funkce pro manipulaci s dokumenty, včetně možnosti převodu dokumentů do různých formátů, včetně HTML.

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

- Na vašem systému nainstalovaná sada pro vývoj Java (JDK).
- Knihovna Aspose.Words pro Javu. Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/java/).

## Krok 1: Importujte potřebné balíčky

```java
import com.aspose.words.*;
import java.io.*;
import java.util.ArrayList;
```

## Krok 2: Vytvořte metodu pro převod Wordu do HTML

```java
class WordToHtmlConverter
{
    // Podrobnosti implementace pro převod Wordu do HTML.
    // ...
}
```

## Krok 3: Vyberte nadpisy odstavců jako začátek tématu

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

## Krok 4: Vložení zalomení oddílů před nadpisy odstavců

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

## Krok 5: Rozdělte dokument na témata

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

## Krok 6: Uložte každé téma jako soubor HTML

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

## Krok 7: Vytvořte obsah pro témata

```java
private void saveTableOfContents(ArrayList<Topic> topics) throws Exception
{
    Document tocDoc = new Document(mTocTemplate);
    tocDoc.getMailMerge().setFieldMergingCallback(new HandleTocMergeField());
    tocDoc.getMailMerge().executeWithRegions(new TocMailMergeDataSource(topics));
    tocDoc.save(mDstDir + "contents.html");
}
```

Nyní, když jsme si nastínili jednotlivé kroky, můžete každý krok implementovat ve svém projektu Java a rozdělit dokumenty na HTML stránky pomocí Aspose.Words pro Javu. Tento proces vám umožní vytvořit strukturovanou HTML reprezentaci vašich dokumentů, díky čemuž budou přístupnější a uživatelsky přívětivější.

## Závěr

V této komplexní příručce jsme se zabývali procesem rozdělení dokumentů na HTML stránky pomocí Aspose.Words pro Javu. Dodržováním uvedených kroků můžete efektivně převádět dokumenty Wordu do formátu HTML, čímž zpřístupníte svůj obsah na webu.

## Často kladené otázky

### Jak nainstaluji Aspose.Words pro Javu?

Chcete-li nainstalovat Aspose.Words pro Javu, můžete si stáhnout knihovnu z [zde](https://releases.aspose.com/words/java/) a postupujte podle pokynů k instalaci uvedených v dokumentaci.

### Mohu si přizpůsobit HTML výstup?

Ano, HTML výstup si můžete přizpůsobit úpravou možností ukládání v `HtmlSaveOptions` třída. To vám umožňuje ovládat formátování a vzhled generovaných HTML souborů.

### Jaké verze aplikace Microsoft Word podporuje Aspose.Words pro Javu?

Aspose.Words pro Javu podporuje širokou škálu formátů dokumentů Microsoft Word, včetně DOC, DOCX, RTF a dalších. Je kompatibilní s různými verzemi Microsoft Wordu.

### Jak mohu zpracovat obrázky v převedeném HTML?

Aspose.Words pro Javu dokáže zpracovat obrázky v převedeném HTML tak, že je uloží jako samostatné soubory do stejné složky jako soubor HTML. Tím je zajištěno, že se obrázky ve výstupu HTML zobrazí správně.

### Je k dispozici zkušební verze Aspose.Words pro Javu?

Ano, můžete si na webových stránkách Aspose vyžádat bezplatnou zkušební verzi Aspose.Words pro Javu, abyste si před zakoupením licence mohli vyzkoušet její funkce a možnosti.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}