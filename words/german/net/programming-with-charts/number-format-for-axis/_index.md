---
"description": "Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie Diagrammachsenzahlen mit Aspose.Words für .NET formatieren. Verbessern Sie mühelos die Lesbarkeit und Professionalität Ihres Dokuments."
"linktitle": "Zahlenformat für Achsen in einem Diagramm"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Zahlenformat für Achsen in einem Diagramm"
"url": "/de/net/programming-with-charts/number-format-for-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zahlenformat für Achsen in einem Diagramm

## Einführung

Hallo! Haben Sie schon einmal mit Diagrammen in Ihren Dokumenten gearbeitet und sich gewünscht, die Zahlen auf den Achsen professioneller formatieren zu können? Sie haben Glück! In diesem Tutorial zeigen wir Ihnen ausführlich, wie Sie genau das mit Aspose.Words für .NET erreichen können. Mit dieser leistungsstarken Bibliothek können Sie Word-Dokumente kinderleicht bearbeiten. Heute konzentrieren wir uns darauf, die Diagrammachsen mit benutzerdefinierten Zahlenformaten zu optimieren.

## Voraussetzungen

Bevor wir beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen. Hier ist eine kurze Checkliste:

- Aspose.Words für .NET: Stellen Sie sicher, dass es installiert ist. Falls nicht, können Sie [Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- .NET Framework: Stellen Sie sicher, dass Sie ein kompatibles .NET Framework installiert haben.
- Entwicklungsumgebung: Eine IDE wie Visual Studio funktioniert perfekt.
- Grundkenntnisse in C#: Dies wird Ihnen helfen, den Codierungsbeispielen zu folgen.

## Namespaces importieren

Zuerst müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. Das ist wie das Legen des Fundaments vor dem Hausbau. Fügen Sie am Anfang Ihrer Codedatei die folgenden using-Direktiven hinzu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

Lassen Sie uns den Vorgang nun in einfache, leicht verständliche Schritte unterteilen.

## Schritt 1: Einrichten des Dokuments

Überschrift: Initialisieren Sie Ihr Dokument

Zuerst müssen Sie ein neues Dokument und einen Dokumentgenerator erstellen. Stellen Sie sich diesen Schritt so vor, als würden Sie Leinwand und Pinsel vorbereiten, bevor Sie mit Ihrem Meisterwerk beginnen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Hier, `dataDir` ist der Pfad zu Ihrem Dokumentverzeichnis, in dem Sie die endgültige Datei speichern. `Document` Und `DocumentBuilder` sind Klassen von Aspose.Words, die Ihnen beim Erstellen und Bearbeiten von Word-Dokumenten helfen.

## Schritt 2: Einfügen eines Diagramms

Überschrift: Fügen Sie Ihrem Dokument ein Diagramm hinzu

Als Nächstes fügen wir Ihrem Dokument ein Diagramm hinzu. Hier beginnt die Magie. Wir fügen ein Säulendiagramm ein, das als leere Leinwand dient.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

Der `InsertChart` Die Methode fügt ein Diagramm des angegebenen Typs (in diesem Fall „Spalte“) und der angegebenen Dimensionen in das Dokument ein.

## Schritt 3: Anpassen der Diagrammserie

Überschrift: Füllen Sie Ihr Diagramm mit Daten

Jetzt müssen wir unserem Diagramm einige Daten hinzufügen. Dieser Schritt entspricht dem Füllen Ihres Diagramms mit aussagekräftigen Informationen.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

Hier fügen wir eine neue Serie namens "Aspose Series 1" mit fünf Datenpunkten hinzu. Die `Series.Clear` Die Methode stellt sicher, dass alle bereits vorhandenen Daten entfernt werden, bevor unsere neue Serie hinzugefügt wird.

## Schritt 4: Formatieren der Achsenzahlen

Überschrift: Verschönern Sie Ihre Achsenzahlen

Zum Schluss formatieren wir die Zahlen auf der Y-Achse, um sie lesbarer zu machen. Das ist sozusagen der letzte Schliff für Ihr Kunstwerk.

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

Der `FormatCode` Mit dieser Eigenschaft können Sie ein benutzerdefiniertes Format für die Zahlen auf der Achse festlegen. In diesem Beispiel `#,##0` sorgt dafür, dass große Zahlen mit Kommas als Tausendertrennzeichen angezeigt werden.

## Schritt 5: Speichern des Dokuments

Überschrift: Speichern Sie Ihr Meisterwerk

Nachdem alles eingerichtet ist, können Sie Ihr Dokument speichern. Dieser Schritt ist die endgültige Enthüllung Ihrer Arbeit.

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

Hier ist die `Save` Methode speichert das Dokument im angegebenen Pfad mit dem Dateinamen `WorkingWithCharts.NumberFormatForAxis.docx`.

## Abschluss

Und da haben Sie es! Sie haben die Zahlen auf der Y-Achse Ihres Diagramms erfolgreich mit Aspose.Words für .NET formatiert. Das lässt Ihre Diagramme nicht nur professioneller aussehen, sondern verbessert auch die Lesbarkeit. Aspose.Words bietet zahlreiche Funktionen, mit denen Sie programmgesteuert beeindruckende Word-Dokumente erstellen können. Warum also nicht mehr entdecken und sehen, was Sie sonst noch tun können?

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, mit der Entwickler Word-Dokumente programmgesteuert erstellen, bearbeiten und konvertieren können.

### Kann ich neben den Achsenzahlen auch andere Aspekte des Diagramms formatieren?
Absolut! Mit Aspose.Words für .NET können Sie Titel und Beschriftungen formatieren und sogar das Erscheinungsbild des Diagramms anpassen.

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?
Ja, Sie können eine [kostenlose Testversion hier](https://releases.aspose.com/).

### Kann ich Aspose.Words für .NET mit anderen .NET-Sprachen außer C# verwenden?
Ja, Aspose.Words für .NET ist mit jeder .NET-Sprache kompatibel, einschließlich VB.NET und F#.

### Wo finde ich ausführlichere Dokumentation?
Eine ausführliche Dokumentation finden Sie auf der [Aspose.Words für .NET-Dokumentationsseite](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}