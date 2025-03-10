---
title: Verwenden von Structured Document Tags (SDTs) für strukturierte Daten
linktitle: Verwenden von Structured Document Tags (SDTs) für strukturierte Daten
second_title: Aspose.Words Python-Dokumentenverwaltungs-API
description: Nutzen Sie die Leistungsfähigkeit von Structured Document Tags (SDTs) zum Organisieren von Inhalten. Erfahren Sie, wie Sie Aspose.Words für Python zum Implementieren von SDTs verwenden.
weight: 13
url: /de/python-net/document-combining-and-comparison/document-sdts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Structured Document Tags (SDTs) für strukturierte Daten


## Einführung in strukturierte Dokument-Tags (SDTs)

Strukturierte Dokument-Tags, oft auch als Inhaltssteuerelemente bezeichnet, sind Elemente innerhalb eines Dokuments, die dem darin enthaltenen Inhalt Struktur verleihen. Sie ermöglichen eine einheitliche Formatierung und die programmgesteuerte Bearbeitung von Inhalten. SDTs können verschiedene Arten von Inhalten umfassen, z. B. einfachen Text, Rich Text, Bilder, Kontrollkästchen und mehr.

## Vorteile der Verwendung von SDTs

Die Verwendung von SDTs bietet mehrere Vorteile, darunter:

- Konsistenz: SDTs stellen sicher, dass der Inhalt einem standardisierten Format folgt, und verhindern so Formatierungsinkonsistenzen.
- Automatisierung: Mit SDTs können Sie die Dokumentgenerierung automatisieren und so die Erstellung von Vorlagen und Berichten vereinfachen.
- Datenvalidierung: SDTs können Datenvalidierungsregeln durchsetzen, wodurch Fehler reduziert und die Datenintegrität gewahrt wird.
- Dynamischer Inhalt: SDTs ermöglichen das Einfügen dynamischer Inhalte, die automatisch aktualisiert werden, wie beispielsweise Datums- und Zeitstempel.
- Einfache Zusammenarbeit: Mitarbeiter können sich auf den Inhalt konzentrieren, ohne die Struktur des Dokuments zu ändern.

## Erste Schritte mit Aspose.Words für Python

Bevor wir uns mit der Verwendung von SDTs befassen, beginnen wir mit Aspose.Words für Python. Aspose.Words ist eine leistungsstarke Bibliothek, mit der Entwickler Word-Dokumente programmgesteuert erstellen, ändern und konvertieren können. Führen Sie zunächst die folgenden Schritte aus:

1. Installation: Installieren Sie Aspose.Words für Python mit pip:
   
   ```python
   pip install aspose-words
   ```

2. Importieren der Bibliothek: Importieren Sie die Aspose.Words-Bibliothek in Ihr Python-Skript:

   ```python
   import aspose.words
   ```

3. Laden eines Dokuments: Laden Sie ein vorhandenes Word-Dokument mit Aspose.Words:

   ```python
   doc = aspose.words.Document("sample.docx")
   ```

## Erstellen und Hinzufügen von SDTs zu einem Dokument

Das Hinzufügen von SDTs zu einem Dokument umfasst einige einfache Schritte:

1.  SDT erstellen: Verwenden Sie die`StructuredDocumentTag` Klasse zum Erstellen einer SDT-Instanz.

   ```python
   sdt = aspose.words.StructuredDocumentTag(doc, aspose.words.SdtType.PLAIN_TEXT)
   ```

2. Inhalt festlegen: Legen Sie den Inhalt des SDT fest:

   ```python
   sdt.get_first_child().remove_all_children()
   sdt.get_first_child().append_child(aspose.words.Run(doc, "Structured Content"))
   ```

3. Zum Dokument hinzufügen: Fügen Sie das SDT zur Blockknotensammlung des Dokuments hinzu:

   ```python
   doc.get_first_section().get_body().append_child(sdt)
   ```

## Arbeiten mit SDT-Inhaltssteuerelementen

Mit Inhaltssteuerelementen von SDT können Benutzer mit dem Dokument interagieren. Sehen wir uns einige gängige Inhaltssteuerelemente an:

1. Klartextsteuerung:

   ```python
   sdt = aspose.words.StructuredDocumentTag(doc, aspose.words.SdtType.PLAIN_TEXT)
   sdt.get_first_child().append_child(aspose.words.Run(doc, "Enter your name: "))
   ```

2. Kontrollkästchen:

   ```python
   sdt = aspose.words.StructuredDocumentTag(doc, aspose.words.SdtType.CHECKBOX)
   sdt.checkbox = True
   sdt.get_first_child().append_child(aspose.words.Run(doc, "Check to agree: "))
   ```

## Programmgesteuertes Navigieren und Bearbeiten von SDTs

Durch die programmgesteuerte Navigation und Bearbeitung von SDTs ist eine dynamische Dokumenterstellung möglich. So können Sie dies erreichen:

1. Zugriff auf SDTs:

   ```python
   sdt_collection = doc.get_child_nodes(aspose.words.NodeType.STRUCTURED_DOCUMENT_TAG, True)
   ```

2. Aktualisieren von SDT-Inhalten:

   ```python
   for sdt in sdt_collection:
       if sdt.sdt_type == aspose.words.SdtType.PLAIN_TEXT:
           sdt.get_first_child().remove_all_children()
           sdt.get_first_child().append_child(aspose.words.Run(doc, "New Content"))
   ```

## Nutzung von SDTs zur Dokumentenautomatisierung

SDTs können für Szenarien zur Dokumentenautomatisierung genutzt werden. Sie können beispielsweise Rechnungsvorlagen mit SDTs für variable Felder wie Kundennamen, Beträge und Daten erstellen. Anschließend füllen Sie diese Felder programmgesteuert basierend auf Daten aus einer Datenbank aus.

## Anpassen des Erscheinungsbilds und Verhaltens von SDT

SDTs bieten verschiedene Anpassungsoptionen, z. B. das Ändern von Schriftarten, Farben und Verhalten. Sie können beispielsweise Platzhaltertext festlegen, um Benutzer beim Ausfüllen von SDTs zu unterstützen.

## Fortgeschrittene Techniken mit SDTs

Fortgeschrittene Techniken umfassen verschachtelte SDTs, benutzerdefinierte XML-Datenbindung und die Verarbeitung von mit SDTs verknüpften Ereignissen. Diese Techniken ermöglichen komplexe Dokumentstrukturen und ein interaktiveres Benutzererlebnis.

## Bewährte Methoden für die Verwendung von SDTs

Befolgen Sie bei der Verwendung von SDTs die folgenden Best Practices:

- Verwenden Sie SDTs konsistent für ähnliche Inhalte in mehreren Dokumenten.
- Planen Sie die Struktur Ihres Dokuments und Ihrer SDTs vor der Implementierung.
- Testen Sie das Dokument gründlich, insbesondere wenn Sie die Inhaltsauffüllung automatisieren.

## Fallstudie: Erstellen einer dynamischen Berichtsvorlage

Betrachten wir eine Fallstudie, in der wir mithilfe von SDTs eine dynamische Berichtsvorlage erstellen. Wir erstellen Platzhalter für einen Berichtstitel, einen Autorennamen und Inhalt. Anschließend füllen wir diese Platzhalter programmgesteuert mit relevanten Daten.

## Abschluss

Strukturierte Dokument-Tags bieten eine effektive Möglichkeit, strukturierte Daten in Dokumenten zu verwalten. Durch die Nutzung von Aspose.Words für Python können Entwickler problemlos dynamische und automatisierte Dokumentlösungen erstellen. SDTs ermöglichen Benutzern die Interaktion mit Dokumenten unter Wahrung von Konsistenz und Integrität.

## Häufig gestellte Fragen

### Wie greife ich auf den Inhalt eines SDT zu?

 Um auf den Inhalt eines SDT zuzugreifen, können Sie den`get_text()`Methode des Inhaltssteuerelements des SDT. Dadurch wird der im SDT enthaltene Text abgerufen.

### Kann ich SDTs in Excel- oder PowerPoint-Dokumenten verwenden?

Nein, SDTs sind spezifisch für Word-Dokumente und nicht in Excel oder PowerPoint verfügbar.

### Sind SDTs mit älteren Versionen von Microsoft Word kompatibel?

SDTs sind mit Microsoft Word 2010 und späteren Versionen kompatibel. In früheren Versionen funktionieren sie möglicherweise nicht wie vorgesehen.

### Kann ich benutzerdefinierte SDT-Typen erstellen?

Microsoft Word unterstützt derzeit einen vordefinierten Satz von SDT-Typen. Benutzerdefinierte SDT-Typen können nicht erstellt werden.

### Wie kann ich ein SDT aus einem Dokument entfernen?

Sie können ein SDT aus einem Dokument entfernen, indem Sie das SDT auswählen und die Taste „Entf“ drücken oder die entsprechende Methode in der Aspose.Words-API verwenden.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
