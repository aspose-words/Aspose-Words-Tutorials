---
date: 2026-01-16
description: Erfahren Sie, wie Sie Rechtschreibfehler in Word mit Aspose.Words für
  Java hervorheben, und entdecken Sie, wie Sie Zeichen pro Zeile festlegen, Ansichtseinstellungen
  anpassen und Stile bereinigen.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Rechtschreibfehler in Word mit Aspose.Words Java hervorheben
url: /de/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Verwendung von Dokumentoptionen und -einstellungen in Aspose.Words für Java

## Einführung in die Verwendung von Dokumentoptionen und -einstellungen in Aspose.Words für Java

In diesem umfassenden Leitfaden lernen Sie **wie man Rechtschreibfehler in Word hervorhebt** mit Aspose.Words für Java und beherrschen gleichzeitig verwandte Einstellungen wie Anzeigeoptionen, Seitenlayout und Stilbereinigung. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst anfangen, die nachstehenden Beispiele helfen Ihnen, robuste, fehlerbewusste Dokumente zu erstellen, die mit allen Word‑Versionen funktionieren.

## Schnelle Antworten
- **Wie kann ich Rechtschreibfehler in Word hervorheben?** Verwenden Sie `setShowSpellingErrors(true)` am `Document`‑Objekt.  
- **Kann ich auch Grammatikfehler anzeigen?** Ja – rufen Sie `setShowGrammaticalErrors(true)` auf.  
- **Welche Methode legt die Zeichen pro Zeile fest?** `getPageSetup().setCharactersPerLine(int)`.  
- **Welche API optimiert für eine bestimmte Word‑Version?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Gibt es eine Möglichkeit, ungenutzte Stile zu bereinigen?** Verwenden Sie `CleanupOptions` mit `setUnusedStyles(true)` und rufen Sie `doc.cleanup(options)` auf.

## Wie man Rechtschreibfehler in Word hervorhebt?

Aspose.Words macht es einfach, die Hervorhebung von Rechtschreibfehlern zu aktivieren. Wenn das Dokument in Microsoft Word geöffnet wird, erscheinen falsch geschriebene Wörter mit der bekannten roten Unterstreichung, sodass Endbenutzer Probleme sofort erkennen.

## Wie man Zeichen pro Zeile festlegt

Die Kontrolle der Anzahl von Zeichen pro Zeile ist für Layouts mit fester Breite (z. B. Code‑Auflistungen oder alte Formulare) unerlässlich. Die Klasse `PageSetup` bietet `setCharactersPerLine(int)`, mit der Sie diesen Wert genau festlegen können.

## Wie man Grammatikfehler anzeigt

Über die Rechtschreibung hinaus können Sie auch die Anzeige von Grammatikfehlern aktivieren. Dies ist nützlich beim Verfassen von Inhalten, die Stilrichtlinien entsprechen müssen, oder beim Erstellen von Korrekturwerkzeugen.

## Optimierung von Dokumenten für Kompatibilität

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

Ein wichtiger Aspekt der Dokumentverwaltung ist die Gewährleistung der Kompatibilität mit verschiedenen Versionen von Microsoft Word. Aspose.Words für Java bietet eine einfache Möglichkeit, Dokumente für bestimmte Word‑Versionen zu optimieren. Im obigen Beispiel optimieren wir ein Dokument für Word 2016, um nahtlose Kompatibilität sicherzustellen.

## Erkennen von Grammatik‑ und Rechtschreibfehlern

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

Genauigkeit ist beim Umgang mit Dokumenten von größter Bedeutung. Aspose.Words für Java ermöglicht es Ihnen, Grammatik‑ und Rechtschreibfehler in Ihren Dokumenten hervorzuheben, wodurch Korrekturlesen und Bearbeiten effizienter werden.

## Bereinigung ungenutzter Stile und Listen

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

Eine effiziente Verwaltung von Dokumentstilen und -listen ist entscheidend für die Konsistenz des Dokuments. Aspose.Words für Java ermöglicht das Bereinigen ungenutzter Stile und Listen, wodurch eine schlanke und organisierte Dokumentstruktur gewährleistet wird.

## Entfernen doppelter Stile

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

Doppelte Stile können zu Verwirrung und Inkonsistenz in Ihren Dokumenten führen. Mit Aspose.Words für Java können Sie doppelte Stile einfach entfernen und so Klarheit und Kohärenz des Dokuments bewahren.

## Anpassen von Anzeigeoptionen für Dokumente

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

Die Anpassung der Anzeige Ihrer Dokumente ist entscheidend. Aspose.Words für Java ermöglicht das Festlegen verschiedener Anzeigeoptionen, wie Seitenlayout und Zoom‑Prozentsatz, um die Lesbarkeit des Dokuments zu verbessern.

## Konfigurieren der Seiteneinrichtung des Dokuments

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

Eine präzise Seiteneinrichtung ist für die Dokumentformatierung entscheidend. Aspose.Words für Java ermöglicht das Festlegen von Layout‑Modi, **Zeichen pro Zeile** und Zeilen pro Seite, sodass Ihre Dokumente optisch ansprechend sind.

## Festlegen von Bearbeitungssprachen

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

Bearbeitungssprachen spielen eine wichtige Rolle bei der Dokumentverarbeitung. Mit Aspose.Words für Java können Sie Bearbeitungssprachen festlegen und anpassen, um den sprachlichen Anforderungen Ihres Dokuments gerecht zu werden.

## Fazit

In diesem Leitfaden haben wir die verschiedenen Dokumentoptionen und -einstellungen von Aspose.Words für Java untersucht. Von Optimierung und Fehlermeldungen bis hin zu Stilbereinigung und Anzeigeoptionen bietet diese leistungsstarke Bibliothek umfangreiche Möglichkeiten zur Verwaltung und Anpassung Ihrer Dokumente.

## Häufig gestellte Fragen

### Wie optimiere ich ein Dokument für eine bestimmte Word‑Version?

Um ein Dokument für eine bestimmte Word‑Version zu optimieren, verwenden Sie die Methode `optimizeFor` und geben die gewünschte Version an. Zum Beispiel, um für Word 2016 zu optimieren:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### Wie kann ich Grammatik‑ und Rechtschreibfehler in einem Dokument hervorheben?

Sie können die Anzeige von Grammatik‑ und Rechtschreibfehlern in einem Dokument mit folgendem Code aktivieren:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### Welchen Zweck hat das Bereinigen ungenutzter Stile und Listen?

Das Bereinigen ungenutzter Stile und Listen trägt dazu bei, eine saubere und organisierte Dokumentstruktur zu erhalten. Es entfernt unnötigen Ballast und verbessert die Lesbarkeit und Konsistenz des Dokuments.

### Wie kann ich doppelte Stile aus einem Dokument entfernen?

Um doppelte Stile aus einem Dokument zu entfernen, verwenden Sie die Methode `cleanup` mit der Option `duplicateStyle`, die auf `true` gesetzt ist. Hier ein Beispiel:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### Wie passe ich die Anzeigeoptionen für ein Dokument an?

Sie können die Anzeigeoptionen eines Dokuments mit der Klasse `ViewOptions` anpassen. Zum Beispiel, um den Ansichtstyp auf Seitenlayout zu setzen und den Zoom auf 50 % zu stellen:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Zusätzliche Tipps & häufige Fallstricke

- **Aktivieren Sie sowohl Rechtschreib- als auch Grammatikprüfungen**, wenn Sie ein umfassendes Korrekturlesen benötigen. Das Vergessen einer der Optionen (`setShowGrammaticalErrors` oder `setShowSpellingErrors`) kann dazu führen, dass Fehler übersehen werden.
- **Beim Festlegen von Zeichen pro Zeile** sollten Sie beachten, dass der Wert mit der gewählten Schriftart und den Seitenrändern interagiert. Testen Sie das Layout mit dem tatsächlichen Dokument, um unerwartete Zeilenumbrüche zu vermeiden.
- **Bereinigungs‑Operationen sind auf der Originaldatei unwiderruflich**. Arbeiten Sie stets mit einer Kopie oder verwenden Sie Versionskontrolle, um das ursprüngliche Styling zu erhalten.
- **Einstellungen der Bearbeitungssprache** beeinflussen das Verhalten der Rechtschreibprüfung. Wenn Sie mehrsprachige Dokumente ansprechen, fügen Sie alle relevanten Sprachen zu `LanguagePreferences` hinzu.

---

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}