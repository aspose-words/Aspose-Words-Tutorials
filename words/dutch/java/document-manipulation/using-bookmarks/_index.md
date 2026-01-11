---
date: 2026-01-11
description: Leer hoe u bladwijzers kunt tonen en verbergen en bladwijzers in Java
  kunt maken met Aspose.Words for Java voor efficiënte documentnavigatie en -manipulatie.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Bladwijzers tonen en verbergen met Aspose.Words voor Java
url: /nl/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bladwijzers weergeven/verbergen met Aspose.Words voor Java

## Introductie tot het gebruik van bladwijzers in Aspose.Words voor Java

Bladwijzers zijn een krachtige functie in Aspose.Words voor Java die je in staat stelt om **create bookmark java** te maken, naar specifieke inhoud te navigeren, en zelfs **show hide bookmarks** te gebruiken wanneer je verschillende documentversies moet genereren. In deze stap‑voor‑stap‑gids lopen we door het maken, benaderen, bijwerken, kopiëren en schakelen van de zichtbaarheid van bladwijzers, zodat je volledige controle hebt over documentmanipulatie.

## Quick Answers
- **Wat is het primaire doel van bladwijzers?** Om specifieke delen van een document te markeren en later op te halen.  
- **Kan ik bladwijzer‑markeringen verbergen in de uiteindelijke output?** Ja—gebruik de show/hide‑API om hun zichtbaarheid te schakelen.  
- **Hoe maak ik een bladwijzer binnen een tabelcel?** Start en eindig de bladwijzer met `DocumentBuilder` terwijl de cursor zich binnen de cel bevindt.  
- **Is het mogelijk om gemarkeerde tekst naar een ander document te kopiëren?** Absoluut—gebruik `NodeImporter` om opmaak te behouden.  
- **Welke versie van Aspose.Words is vereist?** Elke recente release; de code werkt met de nieuwste 2026‑build.

## Wat is “show hide bookmarks”?

De **show hide bookmarks**‑functie stelt je in staat om programmatisch de bladwijzer‑scheidingstekens in het opgeslagen document weer te geven of te verbergen. Dit is handig wanneer je schone output voor eindgebruikers wilt genereren, terwijl je toch bladwijzergegevens behoudt voor interne verwerking.

## Waarom bladwijzers gebruiken in Java‑documentautomatisering?

- **Efficiënte navigatie** – Spring direct naar secties zonder het hele bestand te doorzoeken.  
- **Dynamische inhoudsgeneratie** – Voeg tekst in, vervang of verwijder tekst gekoppeld aan een bladwijzer.  
- **Conditionele zichtbaarheid** – Toon of verberg bladwijzer‑markeringen op basis van gebruikersvoorkeuren of outputformaat.  
- **Herbruikbaarheid** – Kopieer gemarkeerde fragmenten tussen documenten terwijl je stijlen behoudt.

## Prerequisites
- Java Development Kit (JDK) 8 of hoger.  
- Aspose.Words for Java‑bibliotheek toegevoegd aan je project (Maven/Gradle of JAR).  
- Basiskennis van de klassen `Document` en `DocumentBuilder`.

## Step‑by‑Step Guide

### Stap 1: Een bladwijzer maken (create bookmark java)

Om een bladwijzer toe te voegen, start je deze, schrijf je de inhoud, en eindig je vervolgens. Dit voorbeeld maakt een eenvoudige bladwijzer met de naam **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Stap 2: Bladwijzers benaderen (access bookmarks java)

Bladwijzers kunnen worden opgehaald op basis van hun nul‑gebaseerde index of op naam. De onderstaande code toont beide benaderingen.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Stap 3: Bladwijzergegevens bijwerken (update bookmark text)

Je kunt een bladwijzer hernoemen of de tekstinhoud vervangen. Dit is handig wanneer het onderliggende document verandert.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Stap 4: Werken met gemarkeerde tekst (copy bookmarked text)

Het kopiëren van een gemarkeerd fragment naar een ander document terwijl je de oorspronkelijke opmaak behoudt, is eenvoudig met `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Stap 5: Bladwijzers weergeven en verbergen (show hide bookmarks)

De volgende code laat zien hoe je de markeringen van een bladwijzer in het opgeslagen bestand kunt verbergen. Geef `false` door om te verbergen, `true` om weer te geven.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Stap 6: Rij‑bladwijzers ontknopen (bookmark table cell)

Wanneer bladwijzers zich over tabelrijen uitstrekken, kunnen ze verward raken. De onderstaande hulpprogramma‑methoden ontknopen ze en stellen je in staat om een specifieke rij te verwijderen op basis van zijn bladwijzer.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Veelvoorkomende problemen en oplossingen

| Issue | Oplossing |
|-------|-----------|
| **Bookmark not found** | Controleer of de bladwijzernaam exact overeenkomt (hoofdlettergevoelig) en dat het document is opgeslagen na het aanmaken. |
| **Copied text loses formatting** | Gebruik `ImportFormatMode.KEEP_SOURCE_FORMATTING` met `NodeImporter` zoals getoond in Stap 4. |
| **Show/hide does not affect output** | Zorg ervoor dat je `showHideBookmarkedContent` **voordat** je het document opslaat aanroept. |
| **Bookmark inside a table cell is ignored** | Plaats de start/eind‑aanroepen terwijl de builder‑cursor zich binnen de doelcel bevindt. |

## Veelgestelde vragen

**V: Hoe maak ik een bladwijzer in een tabelcel?**  
A: Gebruik `DocumentBuilder` om de cursor naar de gewenste cel te verplaatsen, en roep vervolgens `startBookmark` en `endBookmark` aan rond de celinhoud.

**V: Kan ik een bladwijzer naar een ander document kopiëren?**  
A: Ja—gebruik de `NodeImporter`‑klasse (zie Stap 4) om het gemarkeerde knooppunt te importeren terwijl je de oorspronkelijke opmaak behoudt.

**V: Hoe kan ik een rij verwijderen op basis van zijn bladwijzer?**  
A: Zoek eerst de rij die de bladwijzer bevat, en roep vervolgens `remove` aan op het rijnode (zoals gedemonstreerd in Stap 6).

**V: Wat zijn enkele veelvoorkomende gebruikssituaties voor bladwijzers?**  
A: Het genereren van een inhoudsopgave, het extraheren van specifieke secties voor rapportage, en het automatiseren van documentassemblage op basis van gebruikersselecties.

**V: Waar kan ik meer informatie vinden over Aspose.Words voor Java?**  
A: Voor gedetailleerde documentatie en downloads, bezoek [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Laatst bijgewerkt:** 2026-01-11  
**Getest met:** Aspose.Words for Java 24.11 (2026)  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}