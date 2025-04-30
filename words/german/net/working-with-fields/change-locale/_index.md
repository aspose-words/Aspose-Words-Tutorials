---
"description": "Erfahren Sie in dieser Anleitung, wie Sie das Gebietsschema in Word-Dokumenten mit Aspose.Words für .NET ändern. Ideal für die Betreuung internationaler Kunden und Projekte."
"linktitle": "Gebietsschema ändern"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Gebietsschema ändern"
"url": "/de/net/working-with-fields/change-locale/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Gebietsschema ändern

## Einführung

Die Arbeit mit Word-Dokumenten erfordert oft Fingerspitzengefühl, insbesondere bei unterschiedlichen Gebietsschemata und Kulturen. In diesem Tutorial erfahren Sie, wie Sie das Gebietsschema eines Word-Dokuments mit Aspose.Words für .NET ändern. Egal, ob Sie Dokumente für ein globales Publikum erstellen oder nur die Datumsformate ändern möchten – diese Anleitung hilft Ihnen weiter.

## Voraussetzungen

Bevor wir ins Detail gehen, stellen wir sicher, dass wir alles haben, was wir brauchen:

- Aspose.Words für .NET: Sie können es herunterladen von [Hier](https://releases.aspose.com/words/net/).
- Visual Studio: Jede Version, die .NET Framework unterstützt.
- Grundkenntnisse in C#: Kenntnisse der Grundlagen von C# und .NET helfen Ihnen, den Kurs besser zu verstehen.

Stellen Sie sicher, dass Sie Aspose.Words für .NET installiert haben. Falls nicht, können Sie eine kostenlose Testversion erhalten. [Hier](https://releases.aspose.com/) oder kaufen [Hier](https://purchase.aspose.com/buy).

## Namespaces importieren

Bevor wir mit dem Programmieren beginnen, müssen wir die notwendigen Namespaces importieren. Diese sind wie die Zutaten eines Rezepts und sorgen dafür, dass alles reibungslos funktioniert.

```csharp
using System.Globalization;
using System.Threading;
using Aspose.Words;
using Aspose.Words.Fields;
```

Das Ändern des Gebietsschemas in einem Word-Dokument ist ein unkomplizierter Vorgang. Lassen Sie uns ihn Schritt für Schritt durchgehen.

## Schritt 1: Richten Sie Ihr Dokument ein

Als Erstes richten wir unser Dokument und den Dokument-Generator ein. Das ist, als würden Sie Ihren Arbeitsbereich einrichten, bevor Sie mit dem Kochen beginnen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Ein Seriendruckfeld einfügen

Nun fügen wir ein Seriendruckfeld für das Datum ein. Hier kommt das Gebietsschema ins Spiel.

```csharp
builder.InsertField("MERGEFIELD Date");
```

## Schritt 3: Aktuelle Kultur speichern

Bevor wir das Gebietsschema ändern, müssen wir die aktuelle Kultur speichern. Stellen Sie sich das so vor, als würden Sie Ihre Stelle speichern, bevor Sie mit einem anderen Kapitel fortfahren.

```csharp
CultureInfo currentCulture = Thread.CurrentThread.CurrentCulture;
```

## Schritt 4: Gebietsschema ändern

Als Nächstes ändern wir die aktuelle Kultur des Threads auf Deutsch („de-DE“). Dies entspricht dem Ändern der Spracheinstellungen auf Ihrem Telefon.

```csharp
Thread.CurrentThread.CurrentCulture = new CultureInfo("de-DE");
```

## Schritt 5: Serienbrief ausführen

Nun führen wir den Serienbrief mit dem aktuellen Datum aus. Dadurch wird das neue Gebietsschema auf das Datumsformat angewendet.

```csharp
doc.MailMerge.Execute(new[] { "Date" }, new object[] { DateTime.Now });
```

## Schritt 6: Ursprüngliche Kultur wiederherstellen

Nach der Serienbriefausführung stellen wir die ursprüngliche Kultur wieder her. Dies entspricht dem Zurücksetzen auf Ihre bevorzugte Sprache.

```csharp
Thread.CurrentThread.CurrentCulture = currentCulture;
```

## Schritt 7: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend in Ihrem angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeLocale.docx");
```

Und da haben Sie es! Sie haben das Gebietsschema in Ihrem Word-Dokument mit Aspose.Words für .NET erfolgreich geändert.

## Abschluss

Das Ändern des Gebietsschemas in Word-Dokumenten kann besonders bei internationalen Kunden oder Projekten äußerst nützlich sein. Mit Aspose.Words für .NET wird diese Aufgabe zum Kinderspiel. Befolgen Sie diese Schritte, und Sie können das Gebietsschema mühelos ändern.

## Häufig gestellte Fragen

### Kann ich die Gebietsschemaeinstellung auf eine beliebige Sprache ändern?
Ja, Aspose.Words für .NET unterstützt das Ändern des Gebietsschemas in jede von .NET unterstützte Sprache.

### Wird dies Auswirkungen auf andere Teile meines Dokuments haben?
Das Ändern des Gebietsschemas wirkt sich hauptsächlich auf Datums- und Zahlenformate aus. Anderer Text bleibt unverändert.

### Benötige ich eine spezielle Lizenz, um Aspose.Words für .NET zu verwenden?
Sie können mit einer kostenlosen Testversion beginnen, für die weitere Nutzung müssen Sie jedoch eine Lizenz erwerben [Hier](https://purchase.aspose.com/buy).

### Kann ich zur ursprünglichen Gebietsschemaeinstellung zurückkehren, wenn etwas schief geht?
Ja, indem Sie die ursprüngliche Kultur speichern und später wiederherstellen, können Sie zum ursprünglichen Gebietsschema zurückkehren.

### Wo erhalte ich Unterstützung, wenn Probleme auftreten?
Sie können Unterstützung von der Aspose-Community erhalten [Hier](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}