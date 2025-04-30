---
"description": "Zoptymalizuj zarządzanie dokumentami za pomocą Aspose.Words dla Java. Naucz się pracować z właściwościami dokumentu, dodawać niestandardowe metadane i nie tylko w tym kompleksowym samouczku."
"linktitle": "Korzystanie z właściwości dokumentu"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Korzystanie z właściwości dokumentu w Aspose.Words dla Java"
"url": "/pl/java/document-manipulation/using-document-properties/"
"weight": 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Korzystanie z właściwości dokumentu w Aspose.Words dla Java


## Wprowadzenie do właściwości dokumentu

Właściwości dokumentu są istotną częścią każdego dokumentu. Dostarczają dodatkowych informacji o samym dokumencie, takich jak tytuł, autor, temat, słowa kluczowe i inne. W Aspose.Words for Java możesz manipulować zarówno wbudowanymi, jak i niestandardowymi właściwościami dokumentu.

## Wyliczanie właściwości dokumentu

### Właściwości wbudowane

Aby pobrać i pracować z wbudowanymi właściwościami dokumentu, możesz użyć następującego fragmentu kodu:

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

Ten kod wyświetli nazwę dokumentu i wbudowane właściwości, w tym właściwości takie jak „Tytuł”, „Autor” i „Słowa kluczowe”.

### Właściwości niestandardowe

Aby pracować z niestandardowymi właściwościami dokumentu, możesz użyć następującego fragmentu kodu:

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

Ten fragment kodu pokazuje, jak dodać niestandardowe właściwości dokumentu, takie jak wartość logiczna, ciąg, data, numer wersji i wartość liczbowa.

## Usuwanie właściwości dokumentu

Aby usunąć określone właściwości dokumentu, możesz użyć następującego kodu:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Ten kod usuwa z dokumentu niestandardową właściwość „Data autoryzacji”.

## Konfigurowanie łącza do treści

W niektórych przypadkach możesz chcieć utworzyć linki w swoim dokumencie. Oto jak możesz to zrobić:

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Dodaj właściwość powiązaną z treścią.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Ten fragment kodu pokazuje, jak utworzyć zakładkę w dokumencie i dodać niestandardową właściwość dokumentu zawierającą odnośnik do tej zakładki.

## Konwersja między jednostkami miary

W Aspose.Words for Java możesz łatwo konwertować jednostki miary. Oto przykład, jak to zrobić:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Ustaw marginesy w calach.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Ten fragment kodu ustawia różne marginesy i odległości w calach, zamieniając je na punkty.

## Korzystanie ze znaków kontrolnych

Znaki kontrolne mogą być przydatne w przypadku tekstu. Oto jak zastąpić znak kontrolny w tekście:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Zamień znak kontrolny „\r” na „\r\n”.
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

W tym przykładzie zastępujemy znak powrotu karetki (`\r`) z powrotem karetki i następującym po nim znakiem nowej linii (`\r\n`).

## Wniosek

Właściwości dokumentu odgrywają znaczącą rolę w efektywnym zarządzaniu i organizowaniu dokumentów w Aspose.Words for Java. Niezależnie od tego, czy pracujesz z wbudowanymi właściwościami, właściwościami niestandardowymi, czy używasz znaków kontrolnych, masz do dyspozycji szereg narzędzi, które ulepszą Twoje możliwości zarządzania dokumentami.

## Najczęściej zadawane pytania

### Jak uzyskać dostęp do wbudowanych właściwości dokumentu?

Aby uzyskać dostęp do wbudowanych właściwości dokumentu w Aspose.Words dla Java, możesz użyć `getBuiltInDocumentProperties` metoda na `Document` obiekt. Ta metoda zwraca kolekcję wbudowanych właściwości, po których można iterować.

### Czy mogę dodać do dokumentu niestandardowe właściwości?

Tak, możesz dodać niestandardowe właściwości dokumentu do dokumentu za pomocą `CustomDocumentProperties` kolekcja. Możesz zdefiniować niestandardowe właściwości z różnymi typami danych, w tym ciągami, wartościami logicznymi, datami i wartościami liczbowymi.

### Jak mogę usunąć określoną niestandardową właściwość dokumentu?

Aby usunąć określoną niestandardową właściwość dokumentu, możesz użyć `remove` metoda na `CustomDocumentProperties` kolekcji, przekazując jako parametr nazwę właściwości, którą chcesz usunąć.

### Jaki jest cel linkowania do treści w dokumencie?

Łączenie z treścią w dokumencie umożliwia tworzenie dynamicznych odniesień do określonych części dokumentu. Może to być przydatne do tworzenia interaktywnych dokumentów lub odniesień krzyżowych między sekcjami.

### W jaki sposób mogę konwertować różne jednostki miary w Aspose.Words dla Java?

W Aspose.Words for Java możesz konwertować różne jednostki miary za pomocą `ConvertUtil` Klasa. Dostarcza metod konwersji jednostek, takich jak cale na punkty, punkty na centymetry i inne.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}