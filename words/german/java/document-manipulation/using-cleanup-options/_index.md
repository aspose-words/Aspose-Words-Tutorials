---
date: 2026-01-11
description: Erfahren Sie, wie Sie ein Word‑Dokument mit den Bereinigungsoptionen
  von Aspose.Words für Java säubern, einschließlich des Entfernens leerer Absätze,
  leerer Tabellenzeilen und ungenutzter Felder.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Word-Dokument mit Aspose.Words‑Bereinigungsoptionen bereinigen (Java)
url: /de/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument bereinigen mit Aspose.Words Cleanup-Optionen (Java)

In diesem Tutorial erfahren Sie, wie Sie **Word-Dokumente** mit Aspose.Words für Java bereinigen können. Egal, ob Sie Rechnungen, Verträge oder umfangreiche Seriendruck‑Berichte erstellen, unerwünschte leere Absätze, ungenutzte Felder oder leere Tabellenzeilen können das Endergebnis unprofessionell wirken lassen. Wir gehen jede Bereinigungsoption Schritt für Schritt durch, zeigen Ihnen den genauen Code, den Sie benötigen, und erklären *warum* jede Einstellung wichtig ist, damit Sie jedes Mal ein perfektes Dokument erzeugen.

## Schnelle Antworten
- **Was bedeutet „Word-Dokument bereinigen“?** Entfernen leerer Absätze, ungenutzter Merge‑Regionen, leerer Tabellenzeilen und anderer redundanter Elemente nach einer Seriendruck‑Operation.  
- **Welche Bereinigungsoption entfernt leere Absätze?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **Wie kann ich leere Tabellenzeilen löschen?** Verwenden Sie `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.  
- **Kann ich Felder entfernen, die nie befüllt wurden?** Ja – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` oder `REMOVE_EMPTY_FIELDS`.  
- **Benötige ich eine Lizenz, um diese Beispiele auszuführen?** Eine kostenlose Testversion reicht für die Evaluierung; für den Produktionseinsatz ist eine kommerzielle Lizenz erforderlich.

## Was bedeutet „Word-Dokument bereinigen“ im Kontext von Seriendruck?
Wenn Sie einen Seriendruck ausführen, fügt Aspose.Words Daten in Merge‑Felder und -Regionen ein. Wenn einige Felder `null` oder leere Zeichenketten erhalten, kann das Dokument mit verirrten Absätzen, leeren Tabellen oder Platzhalter‑Regionen enden. Die **Cleanup‑Optionen** entfernen diese Artefakte automatisch und hinterlassen ein sauberes, druckfertiges Dokument.

## Warum Cleanup‑Optionen verwenden?
- **Professionelles Erscheinungsbild:** Keine leeren Zeilen oder verwaisten Tabellen.  
- **Kleinere Dateigröße:** Das Entfernen ungenutzter Elemente reduziert das Dokumentgewicht.  
- **Vereinfachte nachgelagerte Verarbeitung:** Saubere Dokumente lassen sich leichter in PDF, HTML oder andere Formate konvertieren.  
- **Zeitersparnis:** Einzeilige Einstellungen ersetzen manuelle Nachbearbeitungsskripte.

## Voraussetzungen
- Java-Entwicklungsumgebung (JDK 8+).  
- Aspose.Words für Java‑Bibliothek – herunterladen von [here](https://releases.aspose.com/words/java/).  
- Grundlegende Kenntnisse der Seriendruck‑Konzepte.

## Schritt‑für‑Schritt‑Anleitung

### Schritt 1: Leere Absätze entfernen (Java)
Zunächst zeigen wir, wie man Absätze eliminiert, die keinen sichtbaren Text enthalten. Das ist besonders nützlich, wenn ein Merge‑Feld zu `null` aufgelöst wird.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**Was passiert hier?**  
- `REMOVE_EMPTY_PARAGRAPHS` weist Aspose.Words an, jeden Absatz zu entfernen, der nach dem Merge leer ist.  
- Das Aktivieren von `cleanupParagraphsWithPunctuationMarks` entfernt außerdem Absätze, die ausschließlich aus Satzzeichen bestehen (z. B. „?“).

### Schritt 2: Unzusammengeführte Regionen entfernen
Wenn eine Seriendruck‑Region keine entsprechenden Daten hat, können Sie sie vollständig verwerfen.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**Warum das wichtig ist:**  
- Unbenutzte Regionen hinterlassen oft leere Abschnitte oder verirrte Überschriften. Das Flag `REMOVE_UNUSED_REGIONS` bereinigt sie automatisch.

### Schritt 3: Leere Felder entfernen

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### Schritt 4: Unbenutzte Felder entfernen

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### Schritt 5: Enthaltende Felder entfernen

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### Schritt 6: Leere Tabellenzeilen entfernen

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Häufige Probleme & Fehlersuche
- **Absätze werden nicht entfernt:** Stellen Sie sicher, dass `setCleanupParagraphsWithPunctuationMarks(true)` *nach* dem Setzen der Cleanup‑Option aufgerufen wird.  
- **Leere Tabellenzeilen bleiben bestehen:** Überprüfen Sie, dass die Tabellenzellen tatsächlich leere Zeichenketten (nicht Leerzeichen) enthalten.  
- **Unbenutzte Felder bleiben erhalten:** Prüfen Sie, dass Sie das richtige Enum (`REMOVE_UNUSED_FIELDS`) verwenden und dass die Merge‑Felder nicht versehentlich an anderer Stelle befüllt werden.

## Häufig gestellte Fragen

**Q: Was ist der Unterschied zwischen `REMOVE_EMPTY_FIELDS` und `REMOVE_UNUSED_FIELDS`?**  
A: `REMOVE_EMPTY_FIELDS` löscht Felder, die während des Merges eine leere Zeichenkette oder `null` erhalten, während `REMOVE_UNUSED_FIELDS` Felder entfernt, die vom Merge‑Vorgang überhaupt nie referenziert wurden.

**Q: Kann ich mehrere Cleanup‑Optionen kombinieren?**  
A: Ja. Die Methode `setCleanupOptions` akzeptiert ein bitweises OR von Enum‑Werten, sodass Sie Absätze, Tabellen und Regionen in einem Aufruf bereinigen können.

**Q: Wirkt sich das Aktivieren von `cleanupParagraphsWithPunctuationMarks` auf normalen Text aus?**  
A: Es entfernt nur Absätze, die ausschließlich aus Satzzeichen bestehen (z. B. „?“ oder „---“). Normale Sätze bleiben unverändert.

**Q: Ist es möglich, welche Satzzeichen berücksichtigt werden, anzupassen?**  
A: Die aktuelle API verwendet eine vordefinierte Menge von Satzzeichen. Für ein benutzerdefiniertes Verhalten müssten Sie das Dokument nach dem Merge nachbearbeiten.

**Q: Funktionieren diese Cleanup‑Optionen bei der PDF‑Konvertierung?**  
A: Absolut. Sobald das Word‑Dokument bereinigt ist, können Sie es ohne die unerwünschten Elemente in PDF, HTML oder ein anderes unterstütztes Format konvertieren.

## Fazit
Sie haben nun ein vollständiges Werkzeugset zum **Bereinigen von Word‑Dokumenten** während des Seriendrucks mit Aspose.Words für Java. Durch die Auswahl der passenden `MailMergeCleanupOptions` können Sie automatisch leere Absätze, leere Tabellenzeilen, unbenutzte Felder und mehr entfernen – sodass Sie jedes Mal ein schlankes, produktionsreifes Dokument erhalten.

---

**Zuletzt aktualisiert:** 2026-01-11  
**Getestet mit:** Aspose.Words for Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}