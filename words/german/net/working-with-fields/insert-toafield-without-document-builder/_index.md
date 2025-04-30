---
"description": "Erfahren Sie, wie Sie ein TOA-Feld ohne Dokumentgenerator in Aspose.Words für .NET einfügen. Folgen Sie unserer Schritt-für-Schritt-Anleitung zur effizienten Verwaltung juristischer Zitate."
"linktitle": "TOA-Feld ohne Document Builder einfügen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "TOA-Feld ohne Document Builder einfügen"
"url": "/de/net/working-with-fields/insert-toafield-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# TOA-Feld ohne Document Builder einfügen

## Einführung

Das Erstellen eines Tabellenfelds (TOA) in einem Word-Dokument kann sich wie das Zusammensetzen eines komplexen Puzzles anfühlen. Mithilfe von Aspose.Words für .NET wird der Vorgang jedoch reibungslos und unkompliziert. In diesem Artikel führen wir Sie durch die Schritte zum Einfügen eines TOA-Felds ohne Verwendung eines Dokumentgenerators und erleichtern Ihnen so die Verwaltung Ihrer Zitate und Rechtsverweise in Ihren Word-Dokumenten.

## Voraussetzungen

Bevor wir uns in das Tutorial stürzen, wollen wir uns mit den wichtigsten Dingen befassen, die Sie benötigen:

- Aspose.Words für .NET: Stellen Sie sicher, dass Sie die neueste Version installiert haben. Sie können sie von der [Aspose-Website](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Eine .NET-kompatible IDE wie Visual Studio.
- Grundlegende C#-Kenntnisse: Das Verständnis der grundlegenden C#-Syntax und -Konzepte ist hilfreich.
- Beispiel-Word-Dokument: Erstellen Sie ein Beispieldokument oder halten Sie ein solches bereit, in das Sie das TOA-Feld einfügen möchten.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces aus der Aspose.Words-Bibliothek importieren. Dadurch haben Sie Zugriff auf alle für die Dokumentbearbeitung erforderlichen Klassen und Methoden.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Wir unterteilen den Prozess in einfache, leicht verständliche Schritte. Wir führen Sie durch jeden Schritt und erklären, was jeder Codeteil bewirkt und wie er zur Erstellung des TOA-Felds beiträgt.

## Schritt 1: Initialisieren des Dokuments

Zuerst müssen Sie eine Instanz des `Document` Klasse. Dieses Objekt stellt das Word-Dokument dar, an dem Sie arbeiten.

```csharp
// Der Pfad zum Dokumentenverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Dieser Code initialisiert ein neues Word-Dokument. Stellen Sie sich das so vor, als würde eine leere Leinwand erstellt, der Sie Ihren Inhalt hinzufügen.

## Schritt 2: Erstellen und Konfigurieren des TA-Felds

Als Nächstes fügen wir ein TA-Feld (Table of Authorities) hinzu. Dieses Feld markiert die Einträge, die im TOA erscheinen.

```csharp
Paragraph para = new Paragraph(doc);

// Wir möchten TA- und TOA-Felder wie folgt einfügen:
// { TA \c 1 \l "Wert 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Hier ist eine Aufschlüsselung:
- Absatz para = neuer Absatz(doc);: Erstellt einen neuen Absatz innerhalb des Dokuments.
- FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: Fügt dem Absatz ein TA-Feld hinzu. Der `FieldType.FieldTOAEntry` gibt an, dass dies ein TOA-Eingabefeld ist.
- fieldTA.EntryCategory = "1";: Legt die Eintragskategorie fest. Dies ist nützlich, um verschiedene Arten von Einträgen zu kategorisieren.
- fieldTA.LongCitation = "Wert 0";: Gibt den langen Zitattext an. Dieser Text wird im TOA angezeigt.
- doc.FirstSection.Body.AppendChild(para);: Fügt den Absatz mit dem TA-Feld an den Hauptteil des Dokuments an.

## Schritt 3: Hinzufügen des TOA-Felds

Nun fügen wir das eigentliche TOA-Feld ein, das alle TA-Einträge in einer Tabelle zusammenfasst.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

In diesem Schritt:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Fügt dem Absatz ein TOA-Feld hinzu.
- fieldToa.EntryCategory = "1";: Filtert die Einträge, um nur diejenigen einzuschließen, die mit der Kategorie "1" markiert sind.

## Schritt 4: Aktualisieren Sie das TOA-Feld

Nachdem Sie das TOA-Feld eingefügt haben, müssen Sie es aktualisieren, um sicherzustellen, dass es die neuesten Einträge widerspiegelt.

```csharp
fieldToa.Update();
```

Dieser Befehl aktualisiert das TOA-Feld und stellt sicher, dass alle markierten Einträge korrekt in der Tabelle angezeigt werden.

## Schritt 5: Speichern Sie das Dokument

Speichern Sie abschließend Ihr Dokument mit dem neu hinzugefügten TOA-Feld.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

Diese Codezeile speichert das Dokument im angegebenen Verzeichnis. Ersetzen Sie `"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem Sie Ihre Datei speichern möchten.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich ein TOA-Feld zu einem Word-Dokument hinzugefügt, ohne einen Dokumentgenerator zu verwenden. Mit diesen Schritten können Sie Zitate effizient verwalten und umfassende Rechtsgrundlagenverzeichnisse in Ihren juristischen Dokumenten erstellen. Aspose.Words für .NET macht diesen Prozess reibungslos und effizient und bietet Ihnen die Werkzeuge, um komplexe Dokumentaufgaben mühelos zu bewältigen.

## Häufig gestellte Fragen

### Kann ich mehrere TA-Felder mit unterschiedlichen Kategorien hinzufügen?
Ja, Sie können mehrere TA-Felder mit unterschiedlichen Kategorien hinzufügen, indem Sie die `EntryCategory` Eigentum entsprechend.

### Wie kann ich das Erscheinungsbild des TOA anpassen?
Sie können das Erscheinungsbild des TOA anpassen, indem Sie die Eigenschaften des TOA-Felds ändern, beispielsweise die Eintragsformatierung und die Kategoriebezeichnungen.

### Ist es möglich, das TOA-Feld automatisch zu aktualisieren?
Sie können das TOA-Feld zwar manuell aktualisieren, indem Sie `Update` Methode: Aspose.Words unterstützt derzeit keine automatischen Updates bei Dokumentänderungen.

### Kann ich TA-Felder programmgesteuert in bestimmten Teilen des Dokuments hinzufügen?
Ja, Sie können TA-Felder an bestimmten Stellen hinzufügen, indem Sie sie in die gewünschten Absätze oder Abschnitte einfügen.

### Wie verarbeite ich mehrere TOA-Felder in einem einzelnen Dokument?
Sie können mehrere TOA-Felder verwalten, indem Sie unterschiedliche `EntryCategory` Werte und Sicherstellen, dass jedes TOA-Feld Einträge basierend auf seiner Kategorie filtert.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}