---
"description": "Meistern Sie Dokumentrevisionen mit Aspose.Words für .NET. Lernen Sie, Änderungen mühelos zu verfolgen, zu akzeptieren und abzulehnen. Verbessern Sie Ihre Dokumentenmanagement-Fähigkeiten."
"linktitle": "Überarbeitungen akzeptieren"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Überarbeitungen akzeptieren"
"url": "/de/net/working-with-revisions/accept-revisions/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Überarbeitungen akzeptieren

## Einführung

Haben Sie sich schon einmal in einem Labyrinth von Dokumentrevisionen wiedergefunden und versucht, den Überblick über alle Änderungen verschiedener Beteiligter zu behalten? Mit Aspose.Words für .NET wird die Verwaltung von Revisionen in Word-Dokumenten zum Kinderspiel. Diese leistungsstarke Bibliothek ermöglicht es Entwicklern, Änderungen mühelos zu verfolgen, anzunehmen und abzulehnen und so sicherzustellen, dass Ihre Dokumente geordnet und aktuell bleiben. In diesem Tutorial erfahren Sie Schritt für Schritt, wie Sie Dokumentrevisionen mit Aspose.Words für .NET verwalten – von der Initialisierung des Dokuments bis zur Annahme aller Änderungen.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Visual Studio ist auf Ihrem Computer installiert.
- .NET Framework (vorzugsweise die neueste Version).
- Aspose.Words für .NET-Bibliothek. Sie können es herunterladen [Hier](https://releases.aspose.com/words/net/).
- Grundlegende Kenntnisse der C#-Programmierung.

Lassen Sie uns nun in die Einzelheiten einsteigen und sehen, wie wir Dokumentrevisionen mit Aspose.Words für .NET meistern können.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces für die Arbeit mit Aspose.Words importieren. Fügen Sie oben in Ihrer Codedatei die folgenden using-Direktiven hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
```

Wir unterteilen den Prozess in überschaubare Schritte. Jeder Schritt wird detailliert erklärt, damit Sie jeden Teil des Codes verstehen.

## Schritt 1: Initialisieren des Dokuments

Zunächst müssen wir ein neues Dokument erstellen und einige Absätze hinzufügen. Dies schafft die Grundlage für die Nachverfolgung von Revisionen.

```csharp
// Der Pfad zum Dokumentenverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
Body body = doc.FirstSection.Body;
Paragraph para = body.FirstParagraph;

// Fügen Sie dem ersten Absatz Text hinzu und fügen Sie dann zwei weitere Absätze hinzu.
para.AppendChild(new Run(doc, "Paragraph 1. "));
body.AppendParagraph("Paragraph 2. ");
body.AppendParagraph("Paragraph 3. ");
```

In diesem Schritt haben wir ein neues Dokument erstellt und drei Absätze hinzugefügt. Diese Absätze dienen als Grundlage für unsere Revisionsverfolgung.

## Schritt 2: Beginnen Sie mit der Nachverfolgung von Revisionen

Als Nächstes müssen wir die Revisionsverfolgung aktivieren. Dadurch können wir alle am Dokument vorgenommenen Änderungen erfassen.

```csharp
// Beginnen Sie mit der Nachverfolgung von Revisionen.
doc.StartTrackRevisions("John Doe", DateTime.Now);
```

Durch Anrufen `StartTrackRevisions`ermöglichen wir dem Dokument, alle nachfolgenden Änderungen nachzuverfolgen. Als Parameter werden der Name des Autors und das aktuelle Datum übergeben.

## Schritt 3: Eine Revision hinzufügen

Nachdem die Revisionsverfolgung aktiviert ist, fügen wir einen neuen Absatz hinzu. Dieser Zusatz wird als Revision gekennzeichnet.

```csharp
// Dieser Absatz ist eine Revision und das entsprechende Flag „IsInsertRevision“ ist gesetzt.
para = body.AppendParagraph("Paragraph 4. ");
```

Hier wird ein neuer Absatz („Absatz 4.“) hinzugefügt. Da die Revisionsverfolgung aktiviert ist, wird dieser Absatz als Revision gekennzeichnet.

## Schritt 4: Einen Absatz entfernen

Als Nächstes entfernen wir einen vorhandenen Absatz und beobachten, wie die Überarbeitung verfolgt wird.

```csharp
// Holen Sie sich die Absatzsammlung des Dokuments und entfernen Sie einen Absatz.
ParagraphCollection paragraphs = body.Paragraphs;
para = paragraphs[2];
para.Remove();
```

In diesem Schritt wird der dritte Absatz entfernt. Aufgrund der Revisionsverfolgung wird diese Löschung protokolliert und der Absatz zum Löschen markiert, anstatt sofort aus dem Dokument entfernt zu werden.

## Schritt 5: Alle Revisionen akzeptieren

Akzeptieren wir abschließend alle verfolgten Revisionen und festigen so die Änderungen im Dokument.

```csharp
// Akzeptieren Sie alle Überarbeitungen.
doc.AcceptAllRevisions();
```

Durch Anrufen `AcceptAllRevisions`stellen wir sicher, dass alle Änderungen (Ergänzungen und Löschungen) übernommen und im Dokument angewendet werden. Die Revisionen werden nicht mehr gekennzeichnet und in das Dokument integriert.

## Schritt 6: Beenden Sie die Revisionsverfolgung

### Deaktivieren der Revisionsverfolgung

Zum Abschluss können wir die Revisionsverfolgung deaktivieren, um die Aufzeichnung weiterer Änderungen zu beenden.

```csharp
// Beenden Sie die Verfolgung von Revisionen.
doc.StopTrackRevisions();
```

Dieser Schritt verhindert, dass das Dokument neue Änderungen verfolgt, und behandelt alle nachfolgenden Bearbeitungen als regulären Inhalt.

## Schritt 7: Speichern Sie das Dokument

Speichern Sie abschließend das geänderte Dokument im angegebenen Verzeichnis.

```csharp
// Speichern Sie das Dokument.
doc.Save(dataDir + "WorkingWithRevisions.AcceptRevisions.docx");
```

Durch das Speichern des Dokuments stellen wir sicher, dass alle unsere Änderungen und akzeptierten Überarbeitungen erhalten bleiben.

## Abschluss

Die Verwaltung von Dokumentrevisionen kann eine gewaltige Aufgabe sein, aber mit Aspose.Words für .NET wird sie einfach und effizient. Mit den in dieser Anleitung beschriebenen Schritten können Sie Änderungen in Ihren Word-Dokumenten einfach verfolgen, akzeptieren und ablehnen und so sicherstellen, dass Ihre Dokumente stets aktuell und korrekt sind. Worauf warten Sie also noch? Tauchen Sie ein in die Welt von Aspose.Words und optimieren Sie Ihr Dokumentenmanagement noch heute!

## Häufig gestellte Fragen

### Wie beginne ich mit der Verfolgung von Revisionen in Aspose.Words für .NET?

Sie können die Revisionsverfolgung starten, indem Sie den `StartTrackRevisions` -Methode auf Ihrem Dokumentobjekt und Übergabe des Namens des Autors und des aktuellen Datums.

### Kann ich die Revisionsverfolgung jederzeit beenden?

Ja, Sie können die Revisionsverfolgung beenden, indem Sie den `StopTrackRevisions` Methode für Ihr Dokumentobjekt.

### Wie akzeptiere ich alle Überarbeitungen in einem Dokument?

Um alle Revisionen zu akzeptieren, verwenden Sie die `AcceptAllRevisions` Methode für Ihr Dokumentobjekt.

### Kann ich bestimmte Überarbeitungen ablehnen?

Ja, Sie können bestimmte Revisionen ablehnen, indem Sie zu ihnen navigieren und das `Reject` Verfahren.

### Wo kann ich Aspose.Words für .NET herunterladen?

Sie können Aspose.Words für .NET herunterladen von der [Download-Link](https://releases.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}