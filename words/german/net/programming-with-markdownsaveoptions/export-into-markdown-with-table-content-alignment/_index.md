---
"description": "Erfahren Sie, wie Sie Word-Dokumente mit ausgerichteten Tabellen mit Aspose.Words für .NET in Markdown exportieren. Folgen Sie unserer Schritt-für-Schritt-Anleitung für perfekte Markdown-Tabellen."
"linktitle": "Exportieren in Markdown mit Ausrichtung des Tabelleninhalts"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Exportieren in Markdown mit Ausrichtung des Tabelleninhalts"
"url": "/de/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exportieren in Markdown mit Ausrichtung des Tabelleninhalts

## Einführung

Hallo! Haben Sie sich schon einmal gefragt, wie Sie Ihr Word-Dokument mit perfekt ausgerichteten Tabellen ins Markdown-Format exportieren können? Egal, ob Sie Entwickler an Dokumentationen arbeiten oder einfach nur Markdown lieben – dieser Leitfaden ist genau das Richtige für Sie. Wir zeigen Ihnen die Details der Verwendung von Aspose.Words für .NET, um dies zu erreichen. Sind Sie bereit, Ihre Word-Tabellen in sauber ausgerichtete Markdown-Tabellen umzuwandeln? Los geht‘s!

## Voraussetzungen

Bevor wir uns in den Code vertiefen, müssen Sie einige Dinge eingerichtet haben:

1. Aspose.Words für .NET Bibliothek: Stellen Sie sicher, dass Sie die Aspose.Words für .NET Bibliothek haben. Sie können sie von der [Aspose-Releases-Seite](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Richten Sie Ihre Entwicklungsumgebung ein. Visual Studio ist eine beliebte Wahl für die .NET-Entwicklung.
3. Grundkenntnisse in C#: Das Verständnis von C# ist wichtig, da wir Code in dieser Sprache schreiben werden.
4. Beispiel-Word-Dokument: Halten Sie ein Word-Dokument bereit, das Sie zum Testen verwenden können.

## Namespaces importieren

Bevor wir mit dem Programmieren beginnen, importieren wir die erforderlichen Namespaces. Diese ermöglichen uns den Zugriff auf die von uns verwendeten Aspose.Words-Klassen und -Methoden.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Initialisieren Sie Document und DocumentBuilder

Zuerst müssen wir ein neues Word-Dokument erstellen und initialisieren ein `DocumentBuilder` Objekt, um mit dem Erstellen unseres Dokuments zu beginnen.

```csharp
// Der Pfad zum Dokumentenverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Erstellen Sie ein neues Dokument.
Document doc = new Document();

// Initialisieren Sie DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Zellen einfügen und Inhalt ausrichten

Als Nächstes fügen wir einige Zellen in unser Dokument ein und legen deren Ausrichtung fest. Dies ist entscheidend, damit der Markdown-Export die korrekte Ausrichtung beibehält.

```csharp
// Fügen Sie eine Zelle ein und richten Sie sie rechtsbündig aus.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Fügen Sie eine weitere Zelle ein und richten Sie sie mittig aus.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Schritt 3: Tabelleninhaltsausrichtung für Markdown-Export festlegen

Jetzt ist es Zeit, die `MarkdownSaveOptions` um die Ausrichtung des Tabelleninhalts in der exportierten Markdown-Datei zu steuern. Wir speichern das Dokument mit verschiedenen Ausrichtungseinstellungen, um zu sehen, wie es funktioniert.

```csharp
// Erstellen Sie ein MarkdownSaveOptions-Objekt.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Dokument linksbündig speichern.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Ausrichtung nach rechts ändern und speichern.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Ausrichtung auf Mitte ändern und speichern.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Schritt 4: Automatische Ausrichtung des Tabelleninhalts verwenden

Der `Auto` Die Ausrichtungsoption übernimmt die Ausrichtung des ersten Absatzes in der entsprechenden Tabellenspalte. Dies ist praktisch, wenn in einer Tabelle gemischte Ausrichtungen vorliegen.

```csharp
// Stellen Sie die Ausrichtung auf „Auto“.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Dokument mit automatischer Ausrichtung speichern.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Abschluss

Und fertig! Das Exportieren von Word-Dokumenten in Markdown mit ausgerichteten Tabellen mit Aspose.Words für .NET ist kinderleicht, sobald Sie wissen, wie es geht. Diese leistungsstarke Bibliothek erleichtert die Steuerung der Formatierung und Ausrichtung Ihrer Tabellen und stellt sicher, dass Ihre Markdown-Dokumente genau Ihren Wünschen entsprechen. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, Word-Dokumente programmgesteuert zu erstellen, zu ändern, zu konvertieren und zu exportieren.

### Kann ich für verschiedene Spalten in derselben Tabelle unterschiedliche Ausrichtungen festlegen?
Ja, mit dem `Auto` Ausrichtungsoption können Sie basierend auf dem ersten Absatz in jeder Spalte unterschiedliche Ausrichtungen haben.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?
Ja, Aspose.Words für .NET benötigt eine Lizenz für die volle Funktionalität. Sie erhalten eine [vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) zur Auswertung.

### Ist es möglich, andere Dokumentelemente mit Aspose.Words nach Markdown zu exportieren?
Ja, Aspose.Words unterstützt den Export verschiedener Elemente wie Überschriften, Listen und Bilder in das Markdown-Format.

### Wo erhalte ich Unterstützung, wenn Probleme auftreten?
Unterstützung erhalten Sie von der [Aspose.Words Support Forum](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}