---
date: 2026-01-03
description: Erfahren Sie, wie Sie Seitenzahlen beim Einfügen eines Inhaltsverzeichnisses
  mit Aspose.Words für Java anpassen. Passen Sie TOC‑Stile an und erstellen Sie mühelos
  Dokumente.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Seitenzahlen anpassen & Inhaltsverzeichnis generieren mit Aspose.Words für
  Java
url: /de/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Seitenzahlen anpassen und Inhaltsverzeichnis in Aspose.Words für Java erzeugen

In diesem Tutorial erfahren Sie, wie Sie **Seitenzahlen anpassen** und **ein Inhaltsverzeichnis** (TOC) mit Aspose.Words für Java **einfügen**. Ein gut strukturiertes TOC erleichtert die Navigation in langen Dokumenten, und das Feintuning der Ausrichtung der Seitenzahlen sorgt für ein professionelles Leseerlebnis. Wir gehen Schritt für Schritt durch das Erstellen eines Dokuments, das Anpassen von TOC‑Stilen und das Ändern von Tabstopps, sodass die Seitenzahlen genau dort erscheinen, wo Sie sie haben möchten.

## Schnellantworten
- **Was bedeutet „Seitenzahlen anpassen“?** Das Ändern der Tabstopps, die die Seitenzahlen in einem TOC ausrichten.  
- **Kann ich ein Inhaltsverzeichnis automatisch einfügen?** Ja – verwenden Sie die Klasse `FieldToc`.  
- **Benötige ich eine Lizenz, um den Code auszuführen?** Eine kostenlose Testversion reicht für die Entwicklung; für den Produktionseinsatz ist eine Lizenz erforderlich.  
- **Welche Aspose‑Version wird unterstützt?** Die Beispiele funktionieren mit der neuesten Aspose.Words‑für‑Java‑Version.  
- **Ist es möglich, TOC‑Stile anzupassen?** Absolut – Sie können Schriftarten, Fettdruck und mehr ändern.

## Was ist ein Inhaltsverzeichnis in Aspose.Words?
Ein TOC ist ein Feld, das das Dokument nach Überschrifts‑Stilen (z. B. Heading 1, Heading 2) durchsucht und eine Liste von Einträgen mit Seitenzahlen erzeugt. Aspose.Words ermöglicht das programmgesteuerte Einfügen dieses Feldes und die vollständige Kontrolle über dessen Erscheinungsbild.

## Warum Seitenzahlen in einem TOC anpassen?
Das Anpassen der Tabstopps gibt Ihnen präzise Kontrolle darüber, wo die Seitenzahlen erscheinen, was wichtig ist für:

- Die Aufrechterhaltung eines sauberen, spalten‑ausgerichteten Layouts.  
- Die Einhaltung von Unternehmens‑Styleguides.  
- Die Verbesserung der Lesbarkeit in gedruckten und digitalen Dokumenten.

## Voraussetzungen
- Aspose.Words für Java ist Ihrem Projekt hinzugefügt (Maven/Gradle).  
- Grundlegende Kenntnisse der Java‑Syntax.

## Schritt‑für‑Schritt‑Anleitung

### Schritt 1: Neues Dokument erstellen
Instanziieren Sie zunächst ein leeres `Document`‑Objekt, das Ihren Inhalt und das TOC aufnehmen wird.

```java
Document doc = new Document();
```

### Schritt 2: TOC‑Stile anpassen
Sie können das Aussehen jeder TOC‑Ebene ändern. In diesem Beispiel machen wir die Einträge der ersten Ebene fett, was häufig verlangt wird.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### Schritt 3: Inhalt zum Dokument hinzufügen
Fügen Sie Überschriften (z. B. `Heading1`, `Heading2`) und reguläre Absätze ein. Das TOC‑Feld wird diese Überschriften später automatisch erkennen. *(Code aus Gründen der Kürze weggelassen – Fokus liegt auf der TOC‑Erstellung.)*

### Schritt 4: TOC‑Feld einfügen
Platzieren Sie das TOC dort, wo Sie es benötigen – typischerweise am Anfang des Dokuments.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### Schritt 5: Dokument speichern
Speichern Sie das Dokument auf dem Datenträger. Sie können jedes unterstützte Format wählen, z. B. DOCX, PDF oder HTML.

```java
doc.save("your_output_path_here");
```

## Tabstopps im TOC anpassen (Seitenzahlen anpassen)
Falls der Standard‑Tabstopp die Seitenzahlen nicht wie gewünscht ausrichtet, können Sie alle TOC‑Absätze durchlaufen und deren Tab‑Positionen ändern.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Jetzt zeigen die TOC‑Einträge die Seitenzahlen exakt dort an, wo Sie sie haben möchten, und verleihen Ihrem Dokument ein professionelles Erscheinungsbild.

## Häufige Probleme & Tipps
- **Überschriften fehlen im TOC:** Stellen Sie sicher, dass Ihre Überschriften integrierte Stile verwenden (`Heading1`, `Heading2` usw.) oder benutzerdefinierte Stile den TOC‑Ebenen zuordnen.  
- **Tabstopp wird nicht angewendet:** Prüfen Sie, ob der Absatz tatsächlich zu einem TOC‑Stil gehört (`TOC_1`‑`TOC_9`).  
- **Performance bei großen Dokumenten:** Rufen Sie `doc.updateFields()` nach dem Einfügen des TOC auf, um die Einträge in einem Durchgang zu aktualisieren.

## Häufig gestellte Fragen

**F: Wie ändere ich das Format der TOC‑Einträge?**  
A: Verwenden Sie `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, wobei *X* die Ebene (1‑9) ist, und passen Sie Schriftart, Farbe oder Absatz‑Einstellungen an.

**F: Wie kann ich weitere Ebenen zu meinem TOC hinzufügen?**  
A: Ändern Sie den `FieldToc`‑Switch `\o "1-3"` (zum Beispiel), um zusätzliche Überschriften‑Ebenen einzubeziehen, und passen Sie anschließend die entsprechenden `TOC_X`‑Stile an.

**F: Kann ich die Tabstopp‑Positionen für bestimmte TOC‑Einträge ändern?**  
A: Ja – durchlaufen Sie die Absätze wie im Abschnitt „Tabstopps anpassen“ gezeigt und ändern Sie jeden Tabstopp einzeln.

**F: Ist es möglich, ein TOC in einer PDF‑Ausgabe zu erzeugen?**  
A: Absolut. Speichern Sie das Dokument als PDF (`doc.save("output.pdf")`) nachdem das TOC erzeugt wurde; das Feld wird automatisch gerendert.

**F: Muss ich `updateFields()` manuell aufrufen?**  
A: Beim Einfügen eines `FieldToc` aktualisiert Aspose.Words das Feld beim Speichern, aber ein Aufruf von `doc.updateFields()` liefert sofortige Ergebnisse zum Debuggen.

## Fazit
Sie haben gelernt, wie Sie **Seitenzahlen anpassen**, **ein Inhaltsverzeichnis einfügen** und **TOC‑Stile anpassen** mit Aspose.Words für Java. Diese Techniken ermöglichen Ihnen die Erstellung sauberer, navigierbarer und professionell formatierter Dokumente, die jedem Veröffentlichungsstandard entsprechen.

---  

**Zuletzt aktualisiert:** 2026-01-03  
**Getestet mit:** Aspose.Words für Java (neueste Version)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}