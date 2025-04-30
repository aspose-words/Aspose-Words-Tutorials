---
"description": "Naucz się skutecznie używać przypisów dolnych i końcowych w Aspose.Words for Java. Popraw swoje umiejętności formatowania dokumentów już dziś!"
"linktitle": "Korzystanie z przypisów dolnych i końcowych"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Korzystanie z przypisów dolnych i końcowych w Aspose.Words dla Java"
"url": "/pl/java/using-document-elements/using-footnotes-and-endnotes/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Korzystanie z przypisów dolnych i końcowych w Aspose.Words dla Java


tym samouczku przeprowadzimy Cię przez proces korzystania z przypisów dolnych i końcowych w Aspose.Words for Java. Przypisy dolne i końcowe są niezbędnymi elementami formatowania dokumentów, często używanymi do cytowania, odniesień i dodatkowych informacji. Aspose.Words for Java zapewnia solidną funkcjonalność do bezproblemowej pracy z przypisami dolnymi i końcowymi.

## 1. Wprowadzenie do przypisów dolnych i końcowych

Przypisy dolne i końcowe to adnotacje, które dostarczają informacji uzupełniających lub cytatów w dokumencie. Przypisy dolne pojawiają się na dole strony, podczas gdy przypisy końcowe są zbierane na końcu sekcji lub dokumentu. Są powszechnie używane w pracach naukowych, raportach i dokumentach prawnych w celu odniesienia się do źródeł lub wyjaśnienia treści.

## 2. Konfigurowanie środowiska

Zanim przejdziemy do pracy z przypisami dolnymi i końcowymi, musisz skonfigurować środowisko programistyczne. Upewnij się, że masz zainstalowany i skonfigurowany interfejs API Aspose.Words for Java w swoim projekcie.

## 3. Dodawanie przypisów do dokumentu

Aby dodać przypisy do dokumentu, wykonaj następujące kroki:
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";

public void getFootnoteOptions(){
    Document doc = new Document(dataDir + "Document.docx");
    
    // Określ liczbę kolumn, za pomocą których sformatowany będzie obszar przypisów.
    doc.getFootnoteOptions().setColumns(3);
    doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
}
```

## 4. Modyfikowanie opcji przypisów

Możesz modyfikować opcje przypisów, aby dostosować ich wygląd i zachowanie. Oto jak:
```java
@Test
public void setFootnoteAndEndNotePosition() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    
    doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
    doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
}
```

## 5. Dodawanie przypisów końcowych do dokumentu

Dodawanie przypisów końcowych do dokumentu jest proste. Oto przykład:
```java
@Test
public void setEndnoteOptions() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    DocumentBuilder builder = new DocumentBuilder(doc);
    
    builder.write("Some text");
    builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
    
    EndnoteOptions option = doc.getEndnoteOptions();
    option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
    option.setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
}
```

## 6. Dostosowywanie ustawień przypisów końcowych

Możesz dodatkowo dostosować ustawienia przypisów końcowych tak, aby spełniały wymagania Twojego dokumentu.

## Kompletny kod źródłowy
```java
	string dataDir = "Your Document Directory";
	string outPath = "Your Output Directory";
	public void getFootnoteOptions(){
        Document doc = new Document(dataDir + "Document.docx");
        // Określ liczbę kolumn, za pomocą których sformatowany będzie obszar przypisów.
        doc.getFootnoteOptions().setColumns(3);
        doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
    }
    @Test
    public void setFootnoteAndEndNotePosition() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
        doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
    }
    @Test
    public void setEndnoteOptions() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.write("Some text");
        builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
        EndnoteOptions option = doc.getEndnoteOptions();
        option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
        option.setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
	}
```

## 7. Wnioski

W tym samouczku przyjrzeliśmy się, jak pracować z przypisami dolnymi i końcowymi w Aspose.Words for Java. Te funkcje są nieocenione przy tworzeniu dobrze ustrukturyzowanych dokumentów z odpowiednimi cytowaniami i odniesieniami.

Teraz, gdy wiesz już, jak korzystać z przypisów dolnych i końcowych, możesz udoskonalić formatowanie dokumentu i sprawić, by jego treść wyglądała bardziej profesjonalnie.

### Często zadawane pytania

### 1. Jaka jest różnica między przypisami dolnymi i końcowymi?
Przypisy dolne umieszczane są na dole strony, natomiast przypisy końcowe są umieszczane na końcu sekcji lub dokumentu.

### 2. Jak mogę zmienić położenie przypisów dolnych lub końcowych?
Możesz użyć `setPosition` metoda zmiany położenia przypisów dolnych lub końcowych.

### 3. Czy mogę dostosować formatowanie przypisów dolnych i końcowych?
Tak, możesz dostosować formatowanie przypisów dolnych i końcowych za pomocą Aspose.Words dla Java.

### 4. Czy przypisy dolne i końcowe są istotne w formatowaniu dokumentu?
Tak, przypisy dolne i końcowe są niezbędne do podawania odniesień i dodatkowych informacji w dokumentach.

Możesz swobodnie odkrywać więcej funkcji Aspose.Words dla Java i udoskonalać swoje możliwości tworzenia dokumentów. Miłego kodowania!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}