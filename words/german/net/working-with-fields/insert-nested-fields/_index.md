---
title: Verschachtelte Felder einfügen
linktitle: Verschachtelte Felder einfügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in unserer Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET verschachtelte Felder in Word-Dokumente einfügen. Perfekt für Entwickler, die die Dokumenterstellung automatisieren möchten.
weight: 10
url: /de/net/working-with-fields/insert-nested-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verschachtelte Felder einfügen

## Einführung

Mussten Sie schon einmal verschachtelte Felder programmgesteuert in Ihre Word-Dokumente einfügen? Vielleicht möchten Sie bedingt unterschiedliche Texte basierend auf der Seitenzahl anzeigen? Nun, Sie haben Glück! Dieses Tutorial führt Sie durch den Prozess des Einfügens verschachtelter Felder mit Aspose.Words für .NET. Lassen Sie uns eintauchen!

## Voraussetzungen

Bevor wir beginnen, benötigen Sie einige Dinge:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek Aspose.Words für .NET haben. Sie können sie hier herunterladen:[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine IDE wie Visual Studio.
3. Grundkenntnisse in C#: Verständnis der Programmiersprache C#.

## Namespaces importieren

Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importieren. Diese Namespaces enthalten Klassen, die Sie für die Interaktion mit Aspose.Words benötigen.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.HeaderFooter;
```

## Schritt 1: Initialisieren Sie das Dokument

Der erste Schritt besteht darin, ein neues Dokument und ein DocumentBuilder-Objekt zu erstellen. Die DocumentBuilder-Klasse hilft beim Erstellen und Ändern von Word-Dokumenten.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Erstellen Sie das Dokument und den DocumentBuilder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Seitenumbrüche einfügen

Als nächstes fügen wir ein paar Seitenumbrüche in das Dokument ein. So können wir die verschachtelten Felder wirkungsvoll demonstrieren.

```csharp
// Seitenumbrüche einfügen.
for (int i = 0; i < 5; i++)
{
    builder.InsertBreak(BreakType.PageBreak);
}
```

## Schritt 3: Zur Fußzeile wechseln

Nachdem wir Seitenumbrüche eingefügt haben, müssen wir zur Fußzeile des Dokuments wechseln. Hier fügen wir unser verschachteltes Feld ein.

```csharp
// Zur Fußzeile verschieben.
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);
```

## Schritt 4: Verschachteltes Feld einfügen

Fügen wir nun das verschachtelte Feld ein. Wir verwenden das WENN-Feld, um Text basierend auf der aktuellen Seitenzahl bedingt anzuzeigen.

```csharp
// Verschachteltes Feld einfügen.
Field field = builder.InsertField(@"IF ");
builder.MoveTo(field.Separator);
builder.InsertField("PAGE");
builder.Write(" <> ");
builder.InsertField("NUMPAGES");
builder.Write(" \"See next page\" \"Last page\" ");
```

In diesem Schritt fügen wir zuerst das IF-Feld ein, wechseln zu seinem Trennzeichen und fügen dann die Felder PAGE und NUMPAGES ein. Das IF-Feld prüft, ob die aktuelle Seitenzahl (PAGE) nicht der Gesamtseitenzahl (NUMPAGES) entspricht. Wenn dies zutrifft, wird „Siehe nächste Seite“ angezeigt, andernfalls „Letzte Seite“.

## Schritt 5: Aktualisieren Sie das Feld

Abschließend aktualisieren wir das Feld, um sicherzustellen, dass der richtige Text angezeigt wird.

```csharp
// Aktualisieren Sie das Feld.
field.Update();
```

## Schritt 6: Speichern Sie das Dokument

Der letzte Schritt besteht darin, das Dokument in dem von Ihnen angegebenen Verzeichnis zu speichern.

```csharp
doc.Save(dataDir + "InsertNestedFields.docx");
```

## Abschluss

Und da haben Sie es! Sie haben erfolgreich verschachtelte Felder mit Aspose.Words für .NET in ein Word-Dokument eingefügt. Diese leistungsstarke Bibliothek macht es unglaublich einfach, Word-Dokumente programmgesteuert zu bearbeiten. Egal, ob Sie Berichte erstellen, Vorlagen erstellen oder Dokument-Workflows automatisieren, Aspose.Words bietet alles.

## Häufig gestellte Fragen

### Was ist ein verschachteltes Feld in Word-Dokumenten?
Ein verschachteltes Feld ist ein Feld, das andere Felder enthält. Es ermöglicht komplexere und bedingtere Inhalte in Dokumenten.

### Kann ich innerhalb des WENN-Felds andere Felder verwenden?
Ja, Sie können verschiedene Felder wie DATUM, ZEIT und AUTOR in das WENN-Feld verschachteln, um dynamische Inhalte zu erstellen.

### Ist Aspose.Words für .NET kostenlos?
 Aspose.Words für .NET ist eine kommerzielle Bibliothek, aber Sie können eine[Kostenlose Testversion](https://releases.aspose.com/) um es auszuprobieren.

### Kann ich Aspose.Words mit anderen .NET-Sprachen verwenden?
Ja, Aspose.Words unterstützt alle .NET-Sprachen, einschließlich VB.NET und F#.

### Wo finde ich weitere Dokumentation zu Aspose.Words für .NET?
 Eine ausführliche Dokumentation finden Sie[Hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
