---
category: general
date: 2026-07-23
description: Dowiedz się, jak dodać Forms2OleControl do pliku DOCX przy użyciu Aspose.Words.
  Ten przewodnik krok po kroku pokazuje wstawianie kontrolki ActiveX CommandButton
  w Javie.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add forms2olecontrol to docx
- insert ActiveX control in DOCX
- Aspose.Words Forms2OleControl example
- embed CommandButton in Word document
- Java DocumentBuilder ActiveX
language: pl
lastmod: 2026-07-23
og_description: Dodaj Forms2OleControl do DOCX od razu. Skorzystaj z tego praktycznego
  przewodnika, aby osadzić przycisk ActiveX CommandButton przy użyciu Aspose.Words
  for Java.
og_image_alt: Screenshot of Java code that adds Forms2OleControl to DOCX using Aspose.Words
og_title: Dodaj Forms2OleControl do DOCX – Pełny samouczek Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  headline: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  name: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  steps:
  - name: Using a Different ActiveX Control
    text: 'If you want a checkbox instead of a button, just change the control type:'
  - name: Embedding Multiple Controls
    text: Call `builder.insertForms2OleControl()` multiple times, moving the cursor
      with `builder.moveTo()` or inserting text between calls. Each call adds a new
      OLE container, so you can build complex forms inside a single DOCX.
  - name: Working with .NET
    text: The same logic applies to C#—the method names are identical (`DocumentBuilder.InsertForms2OleControl()`).
      If you’re on .NET, replace the Java syntax with its C# counterpart, but the
      **embed CommandButton in Word document** concept stays unchanged.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Java
- DOCX
title: Dodaj Forms2OleControl do DOCX – Kompletny przewodnik Aspose.Words
url: /pl/java/using-document-elements/add-forms2olecontrol-to-docx-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj Forms2OleControl do DOCX – Kompletny przewodnik Aspose.Words

Zastanawiałeś się kiedyś, jak **dodać Forms2OleControl do DOCX** bez wyrywania włosów? Nie jesteś jedyny. Niezależnie od tego, czy tworzysz raport oparty na szablonie, czy potrzebujesz klikalnego przycisku w pliku Word, osadzenie kontrolki ActiveX to tajny składnik.

W tym samouczku przeprowadzimy Cię przez konkretny przykład, który **dodaje Forms2OleControl do DOCX** przy użyciu Aspose.Words dla Javy. Zobaczysz pełny kod, zrozumiesz, dlaczego każda linijka ma znaczenie, oraz otrzymasz wskazówki, jak radzić sobie z drobnymi problemami, które często napotykają programiści.

## Czego się nauczysz

- Jak skonfigurować Aspose.Words w projekcie Java  
- Dokładne kroki, aby **wstawić kontrolkę ActiveX w DOCX** (tak, ponownie główne słowo kluczowe)  
- Konfigurowanie właściwości CommandButton, aby zachowywał się jak prawdziwy element UI  
- Zapis dokumentu i weryfikacja, że kontrolka jest naprawdę osadzona  

Nie wymagana jest wcześniejsza znajomość ActiveX, ale podstawowa wiedza o Javie oraz Maven/Gradle ułatwi Ci pracę. Gotowy? Zanurzmy się.

---

## Krok 1: Skonfiguruj Aspose.Words w swoim projekcie

Zanim będziesz mógł **dodać Forms2OleControl do DOCX**, potrzebujesz biblioteki Aspose.Words na classpath. Najłatwiejszy sposób to użycie Maven:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

> **Pro tip:** Jeśli używasz Gradle, odpowiednikiem jest `implementation 'com.aspose:aspose-words:24.9'`.  

Dlaczego to ważne: Aspose.Words udostępnia metodę `DocumentBuilder.insertForms2OleControl()`, której użyjemy, aby **wstawić kontrolkę ActiveX w DOCX**. Bez tej biblioteki kompilator nie będzie wiedział, czym jest `Forms2OleControl`.

## Krok 2: Dodaj Forms2OleControl do DOCX

Teraz przechodzimy do sedna samouczka — tutaj faktycznie **dodajemy Forms2OleControl do DOCX**. Utworzymy nowy dokument, stworzymy `DocumentBuilder` i wywołamy metodę wstawiania.

```java
import com.aspose.words.*;

public class ActiveXExample {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2.2: Insert an ActiveX Forms2OleControl (CommandButton)
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Step 2.3: Configure the CommandButton properties
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setName("MyButton");
        commandButton.setCaption("Click Me");

        // Step 2.4: Save the document with the embedded control
        String outPath = "output/ActiveXButton.docx";
        document.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Co się tutaj dzieje?**  

- `new Document()` daje nam czyste płótno. Pomyśl o tym jak o nowej kartce papieru gotowej do **wstawienia kontrolki ActiveX w DOCX**.  
- `builder.insertForms2OleControl()` tworzy niskopoziomowy kontener OLE, który Aspose.Words nazywa *Forms2OleControl*. To jedyne wywołanie API, które faktycznie **dodaje Forms2OleControl do DOCX**.  
- Ustawienie `OleControlType.COMMANDBUTTON` informuje Word, że obiekt OLE ma zachowywać się jak klasyczny CommandButton — dokładnie tak, jak przycisk, który przeciągnąłbyś na formularz w projektancie UI.  
- Na koniec, `document.save(...)` zapisuje plik .docx, utrwalając osadzony ActiveX.

## Krok 3: Skonfiguruj właściwości CommandButton (Dlaczego to ważne)

Same wstawienie kontrolki daje Ci pusty placeholder. Aby była użyteczna, musisz ustawić kilka właściwości:

| Właściwość | Cel | Typowa wartość |
|------------|-----|----------------|
| `setOleControlType` | Definiuje typ kontrolki ActiveX (Button, CheckBox, itp.) | `OleControlType.COMMANDBUTTON` |
| `setName` | Wewnętrzny identyfikator używany przez makra Worda lub skrypty VBA | `"MyButton"` |
| `setCaption` | Tekst wyświetlany na powierzchni przycisku | `"Click Me"` |

Jeśli pominiesz te ustawienia, przycisk pojawi się z ogólną nazwą i bez etykiety — nic, czego użytkownik chciałby kliknąć. Pamiętaj również, że kontrolki ActiveX są **specyficzne dla platformy**; działają tylko na maszynach z systemem Windows, które mają zainstalowane odpowiednie biblioteki COM.

> **Uwaga:** Gdy otworzysz wygenerowany DOCX na platformie nie‑Windows (np. macOS), Word wyświetli obraz zastępczy zamiast rzeczywistego przycisku. Jest to normalne ograniczenie ActiveX, a nie błąd w Twoim kodzie.

## Krok 4: Zapisz i zweryfikuj dokument

Wywołanie `document.save(...)` zapisuje standardowy plik DOCX, który może otworzyć każda nowoczesna wersja Microsoft Word. Po uruchomieniu programu, otwórz `ActiveXButton.docx`:

1. Zlokalizuj przycisk „Click Me” w miejscu, w którym go wstawiłeś.  
2. Kliknij prawym przyciskiem myszy przycisk → **Properties**, aby potwierdzić nazwę i etykietę.  
3. Kliknij przycisk; Word wyświetli prosty komunikat, jeśli dołączyłeś makro (poza zakresem tego przewodnika).  

Jeśli przycisk nie pojawi się, sprawdź ponownie, czy poprawnie użyłeś **przykładu Aspose.Words Forms2OleControl** i czy folder wyjściowy istnieje.  

> **Przypadek brzegowy:** Jeśli potrzebujesz, aby przycisk wywoływał makro, musisz dodać kod VBA do dokumentu po jego zapisaniu. Aspose.Words może wstrzyknąć VBA przy użyciu API `Document.getBuiltInDocumentProperties()`, ale to już temat na osobny samouczek.

## Typowe warianty i pułapki

### Użycie innej kontrolki ActiveX
Jeśli chcesz zamiast przycisku pole wyboru, po prostu zmień typ kontrolki:

```java
commandButton.setOleControlType(OleControlType.CHECKBOX);
commandButton.setCaption("Accept Terms");
```

### Osadzanie wielu kontrolek
Wywołaj `builder.insertForms2OleControl()` wielokrotnie, przesuwając kursor przy pomocy `builder.moveTo()` lub wstawiając tekst pomiędzy wywołaniami. Każde wywołanie dodaje nowy kontener OLE, dzięki czemu możesz budować złożone formularze w jednym pliku DOCX.

### Praca z .NET
Ta sama logika obowiązuje w C# — nazwy metod są identyczne (`DocumentBuilder.InsertForms2OleControl()`). Jeśli pracujesz w .NET, zamień składnię Java na jej odpowiednik w C#, ale koncepcja **osadzenia CommandButton w dokumencie Word** pozostaje niezmieniona.

## Zakończenie

Masz teraz działający, kompleksowy przykład, który **dodaje Forms2OleControl do DOCX** przy użyciu Aspose.Words dla Javy. Tworząc pusty dokument, wstawiając kontrolkę ActiveX, konfigurować jej właściwości i zapisując plik, opanowałeś kluczowe kroki, aby **wstawić kontrolkę ActiveX w DOCX** i możesz rozszerzyć ten wzorzec na inne typy kontrolek.

Co dalej? Spróbuj połączyć tę technikę z funkcją scalania korespondencji Aspose.Words, aby generować spersonalizowane formularze, lub zbadaj dodawanie makr VBA, aby przycisk naprawdę coś robił. Nie ma granic, gdy połączysz **przykład Aspose.Words Forms2OleControl** z własną logiką biznesową.

Miłego kodowania i śmiało zostaw komentarz, jeśli napotkasz jakiekolwiek problemy!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu wraz z krok‑po‑kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak tworzyć pola formularzy i dodawać treść przy użyciu DocumentBuilder w Aspose.Words dla Javy](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Dodawanie zakładek w Wordzie przy użyciu Aspose.Words dla Javy – wstawianie, aktualizacja, usuwanie](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)
- [Jak dodać znak wodny do dokumentów przy użyciu Aspose.Words dla Javy](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}