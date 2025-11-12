---
date: '2025-11-12'
description: Lär dig hur du infogar kontrolltecken, hanterar radbrytningar och lägger
  till sid- eller kolumnbrytningar i Java med Aspose.Words för exakt dokumentformatering.
keywords:
- Aspose.Words control characters
- Java document formatting with Aspose.Words
- inserting control characters in Java
- insert control characters java
- manage carriage returns
- add page break aspose
- insert non‑breaking space
- create multi‑column layout
language: sv
title: Infoga kontrolltecken i Java med Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

We need to translate the content to Swedish, preserving markdown, code blocks placeholders unchanged, keep technical terms, URLs, file paths, variable names, function names unchanged. Also keep the custom Hugo shortcodes like {{< blocks/... >}} unchanged. Also note rule 6: "For Swedish, ensure proper RTL formatting if needed" Swedish is LTR, so ignore.

We need to translate all visible text, headings, table contents, bullet points, etc. Keep code block placeholders like ```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
``` unchanged.

We must not translate URLs, file paths, variable names, function names. Those are inside code blocks placeholders, not actual code. So fine.

We need to translate the markdown content.

Let's go through line by line.

Start:

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insert Control Characters in Java with Aspose.Words

Translate to Swedish: "Infoga kontrolltecken i Java med Aspose.Words"

## Introduction

"Introduktion"

Do you need pixel‑perfect control over line breaks, tabs, or page divisions when generating invoices, reports, or newsletters?  

Translate: "Behöver du pixel‑perfekt kontroll över radbrytningar, tabbar eller sidindelningar när du genererar fakturor, rapporter eller nyhetsbrev?"  

Control characters are the invisible building blocks that let you shape document layout programmatically.  

"Kontrolltecken är de osynliga byggstenarna som låter dig forma dokumentlayout programatiskt."

In this tutorial you’ll learn how to **insert**, **verify**, and **manage** control characters such as carriage returns, non‑breaking spaces, and column breaks using the Aspose.Words for Java API.

" I den här handledningen kommer du att lära dig hur du **infogar**, **verifierar** och **hanterar** kontrolltecken såsom vagnretur, icke‑brytande mellanslag och kolumnbrytningar med Aspose.Words for Java API."

**What you’ll achieve:** -> "**Vad du kommer att uppnå:**"

1. Insert and validate carriage returns, line feeds, and page breaks.  

"Infoga och validera vagnretur, radmatningar och sidbrytningar."

2. Add spaces, tabs, non‑breaking spaces, and column breaks to create multi‑column layouts.  

"Lägg till mellanslag, tabbar, icke‑brytande mellanslag och kolumnbrytningar för att skapa flerkolumnslayouter."

3. Apply best‑practice performance tips for large‑scale document automation.  

"Tillämpa bästa praxis för prestanda vid storskalig dokumentautomatisering."

## Prerequisites

"Förutsättningar"

Before we start, make sure you have the following ready:

"Innan vi börjar, se till att du har följande redo:"

Table:

| Requirement | Details |
|-------------|----------|
| **Aspose.Words for Java** | Version 25.3 or newer (the API remains stable across later releases). |
| **JDK** | Java 8 + (Java 11 or 17 recommended). |
| **IDE** | IntelliJ IDEA, Eclipse, or any Java‑compatible editor. |
| **Build tool** | Maven **or** Gradle for dependency management. |
| **License** | A temporary or purchased Aspose.Words license file. |

Translate each cell.

Requirement -> "Krav"

Details -> "Detaljer"

Row 1: **Aspose.Words for Java** stays same. Details: "Version 25.3 eller nyare (API:et förblir stabilt i senare versioner)."

Row 2: **JDK** same. Details: "Java 8 + (Java 11 eller 17 rekommenderas)."

Row 3: **IDE** same. Details: "IntelliJ IDEA, Eclipse eller någon Java‑kompatibel editor."

Row 4: **Build tool** same. Details: "Maven **eller** Gradle för beroendehantering."

Row 5: **License** same. Details: "En temporär eller köpt Aspose.Words-licensfil."

### Quick Environment Checklist

"### Snabbchecklista för miljön"

1. Maven **or** Gradle installed.  

"Maven **eller** Gradle installerat."

2. License file accessible (e.g., `src/main/resources/aspose.words.lic`).  

"Licensfil åtkomlig (t.ex. `src/main/resources/aspose.words.lic`)."

3. Project compiled without errors.  

"Projektet kompilerat utan fel."

## Setting Up Aspose.Words

"## Konfigurera Aspose.Words"

We’ll first add the library to the project, then load the license. Choose the build system that matches your workflow.

"Vi lägger först till biblioteket i projektet, sedan laddar vi licensen. Välj det byggsystem som passar ditt arbetsflöde."

### Maven Dependency

"### Maven‑beroende"

Add the following snippet to your `pom.xml` inside `<dependencies>`:

"Lägg till följande kodsnutt i din `pom.xml` inom `<dependencies>`:"

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
``` stays.

### Gradle Dependency

"### Gradle‑beroende"

Insert this line into the `dependencies` block of `build.gradle`:

"Sätt in den här raden i `dependencies`‑blocket i `build.gradle`:"

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### License Initialization (Java code)

"### Licensinitiering (Java‑kod)"

```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **Note:** Replace `"path/to/aspose.words.lic"` with the actual path to your license file.

"> **Obs:** Ersätt `"path/to/aspose.words.lic"` med den faktiska sökvägen till din licensfil."

## Feature 1: Handle Carriage Returns and Page Breaks

"## Funktion 1: Hantera vagnretur och sidbrytningar"

Carriage returns (`ControlChar.CR`) and page breaks (`ControlChar.PAGE_BREAK`) are essential when you need the output text to reflect the visual layout of a document.

"Vagnretur (`ControlChar.CR`) och sidbrytningar (`ControlChar.PAGE_BREAK`) är viktiga när du vill att utdata‑texten ska spegla dokumentets visuella layout."

### Step‑by‑Step Implementation

"### Steg‑för‑steg‑implementering"

1. **Create a new Document and DocumentBuilder.**  

"**Skapa ett nytt Document och DocumentBuilder.**"

2. **Write two paragraphs.**  

"**Skriv två stycken.**"

3. **Verify that the generated text contains the expected control characters.**  

"**Verifiera att den genererade texten innehåller de förväntade kontrolltecknen.**"

4. **Trim the text and re‑check the result.**  

"**Trimma texten och kontrollera resultatet igen.**"

#### 1. Create a Document

"#### 1. Skapa ett Document"

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. Insert Paragraphs

"#### 2. Infoga stycken"

```java
builder.writeln("Hello world!");
builder.writeln("Hello again!");
```

#### 3. Verify Control Characters

"#### 3. Verifiera kontrolltecken"

```java
String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
        MessageFormat.format("Hello again!{0}", ControlChar.CR) +
        ControlChar.PAGE_BREAK;
assert doc.getText().equals(expectedTextWithCR) :
        "Text does not match expected value with control characters.";
```

#### 4. Trim and Check Text

"#### 4. Trimma och kontrollera text"

```java
String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
assert doc.getText().trim().equals(expectedTrimmedText) :
        "Trimmed text does not match expected value.";
```

**Result:** The `doc.getText()` string now contains explicit CR and page‑break symbols, guaranteeing that downstream systems (e.g., plain‑text exporters) preserve the layout.

"**Resultat:** Strängen `doc.getText()` innehåller nu explicita CR‑ och sidbrytningssymboler, vilket garanterar att efterföljande system (t.ex. ren‑text‑exportörer) bevarar layouten."

## Feature 2: Insert Various Control Characters

"## Funktion 2: Infoga olika kontrolltecken"

Beyond carriage returns, Aspose.Words offers constants for spaces, tabs, line feeds, paragraph breaks, and column breaks. This section shows how to embed each one.

"Utöver vagnretur erbjuder Aspose.Words konstanter för mellanslag, tabbar, radmatningar, styckebrytningar och kolumnbrytningar. Denna sektion visar hur du bäddar in var och en."

### Step‑by‑Step Implementation

"### Steg‑för‑steg‑implementering"

1. **Initialize a fresh DocumentBuilder.**  

"**Initiera en ny DocumentBuilder.**"

2. **Write examples for space, non‑breaking space, and tab characters.**  

"**Skriv exempel för mellanslag, icke‑brytande mellanslag och tab‑tecken.**"

3. **Add line feeds, paragraph breaks, and section breaks, then validate node counts.**  

"**Lägg till radmatningar, styckebrytningar och sektionsbrytningar, och validera sedan nodantalet.**"

4. **Create a two‑column layout and insert a column break.**  

"**Skapa en två‑kolumns layout och infoga en kolumnbrytning.**"

#### 1. Initialize DocumentBuilder

"#### 1. Initiera DocumentBuilder"

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. Insert Space‑Related Characters

"#### 2. Infoga mellanslagsrelaterade tecken"

- **Space (`ControlChar.SPACE_CHAR`)**  
```java
builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
```
- **Non‑Breaking Space (`ControlChar.NON_BREAKING_SPACE`)**  
```java
builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
```
- **Tab (`ControlChar.TAB`)**  
```java
builder.write("Before tab." + ControlChar.TAB + "After tab.");
```

#### 3. Line, Paragraph, and Section Breaks

"#### 3. Rad‑, stycke‑ och sektionsbrytningar"

```java
// Verify initial paragraph count is 1
Assert.assertEquals(1, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a line feed (creates a new paragraph)
builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");
Assert.assertEquals(2, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a paragraph break
builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
Assert.assertEquals(3, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a section break (still one Section object, but a break marker)
builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
assert doc.getSections().getCount() == 1 :
        "Section count mismatch after section break.";
```

#### 4. Column Break in a Multi‑Column Layout

"#### 4. Kolumnbrytning i en flerkolumnslayout"

```java
// Add a second section to host two columns
doc.appendChild(new Section(doc));
builder.moveToSection(1);
builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);

// Insert a column break between the two columns
builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
```

**Result:** The document now contains a two‑column page where text flows automatically from the first column to the second after the `COLUMN_BREAK`.

"**Resultat:** Dokumentet innehåller nu en två‑kolumnssida där texten flödar automatiskt från den första kolumnen till den andra efter `COLUMN_BREAK`."

## Practical Applications

"## Praktiska tillämpningar"

| Scenario | How Control Characters Help |
|----------|-----------------------------|
| **Invoice Generation** | Use `PAGE_BREAK` to start a new page for each invoice batch. |
| **Financial Report** | Align figures with `TAB` and keep headings together using `NON_BREAKING_SPACE`. |
| **Newsletter Layout** | Create side‑by‑side articles with `COLUMN_BREAK` in a multi‑column section. |
| **CMS Content Export** | Preserve line structure when converting rich text to plain text via `LINE_FEED`. |
| **Automated Templates** | Dynamically insert `PARAGRAPH_BREAK` or `SECTION_BREAK` based on user input. |

Translate:

Scenario -> "Scenario" maybe "Scenario" can be "Scenario" or "Användningsfall". Keep as "Scenario". How Control Characters Help -> "Hur kontrolltecken hjälper". Let's translate.

Rows:

**Invoice Generation** -> "**Fakturagenerering**" | Use `PAGE_BREAK` to start a new page for each invoice batch. -> "Använd `PAGE_BREAK` för att starta en ny sida för varje fakturabatch."

**Financial Report** -> "**Finansiell rapport**" | Align figures with `TAB` and keep headings together using `NON_BREAKING_SPACE`. -> "Justera siffror med `TAB` och håll rubriker ihop med `NON_BREAKING_SPACE`."

**Newsletter Layout** -> "**Nyhetsbrevslayout**" | Create side‑by‑side articles with `COLUMN_BREAK` in a multi‑column section. -> "Skapa sida‑vid‑sida-artiklar med `COLUMN_BREAK` i en flerkolumnssektion."

**CMS Content Export** -> "**CMS‑innehållsexport**" | Preserve line structure when converting rich text to plain text via `LINE_FEED`. -> "Bevara radstruktur när du konverterar rik text till ren text via `LINE_FEED`."

**Automated Templates** -> "**Automatiserade mallar**" | Dynamically insert `PARAGRAPH_BREAK` or `SECTION_BREAK` based on user input. -> "Infoga dynamiskt `PARAGRAPH_BREAK` eller `SECTION_BREAK` baserat på användarens inmatning."

## Performance Considerations

"## Prestandaöverväganden"

* **Batch Inserts:** Group multiple `write` calls into a single operation to reduce internal reflows.  

"* **Batch‑infogningar:** Gruppera flera `write`‑anrop till en enda operation för att minska interna omflöden."

* **Avoid Frequent Node Traversal:** Cache `NodeCollection` results when you need to count paragraphs repeatedly.  

"* **Undvik frekvent nodtraversering:** Cacha `NodeCollection`‑resultat när du behöver räkna stycken upprepade gånger."

* **Profile Large Docs:** Use Java profilers (e.g., VisualVM) to identify hotspots in text manipulation loops.  

"* **Profilera stora dokument:** Använd Java‑profilerare (t.ex. VisualVM) för att identifiera flaskhalsar i textmanipuleringsloopar."

## Conclusion

"## Slutsats"

You now have a concrete, step‑by‑step method for **inserting**, **validating**, and **optimizing** control characters in Java documents using Aspose.Words. These techniques empower you to produce professional‑grade invoices, reports, and multi‑column publications programmatically.

"Du har nu en konkret, steg‑för‑steg‑metod för att **infoga**, **validera** och **