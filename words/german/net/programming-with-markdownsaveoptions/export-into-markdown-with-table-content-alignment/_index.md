---
title: Exportieren in Markdown mit Ausrichtung des Tabelleninhalts
linktitle: Exportieren in Markdown mit Ausrichtung des Tabelleninhalts
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie Word-Dokumente mit ausgerichteten Tabellen mithilfe von Aspose.Words für .NET in Markdown exportieren. Folgen Sie unserer Schritt-für-Schritt-Anleitung für perfekte Markdown-Tabellen.
weight: 10
url: /de/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportieren in Markdown mit Ausrichtung des Tabelleninhalts

## Einführung

Hallo! Haben Sie sich schon einmal gefragt, wie Sie Ihr Word-Dokument mit perfekt ausgerichteten Tabellen in das Markdown-Format exportieren können? Egal, ob Sie Entwickler sind, der an Dokumentationen arbeitet, oder einfach jemand, der Markdown liebt, dieser Leitfaden ist für Sie. Wir werden uns eingehend mit der Verwendung von Aspose.Words für .NET befassen, um dies zu erreichen. Sind Sie bereit, Ihre Word-Tabellen in sauber ausgerichtete Markdown-Tabellen umzuwandeln? Dann legen wir los!

## Voraussetzungen

Bevor wir uns in den Code vertiefen, müssen Sie einige Dinge vorbereitet haben:

1.  Aspose.Words für .NET-Bibliothek: Stellen Sie sicher, dass Sie die Aspose.Words für .NET-Bibliothek haben. Sie können sie von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Richten Sie Ihre Entwicklungsumgebung ein. Visual Studio ist eine beliebte Wahl für die .NET-Entwicklung.
3. Grundkenntnisse in C#: Das Verständnis von C# ist wichtig, da wir Code in dieser Sprache schreiben werden.
4. Beispiel-Word-Dokument: Halten Sie ein Word-Dokument bereit, das Sie zum Testen verwenden können.

## Namespaces importieren

Bevor wir mit dem Codieren beginnen, importieren wir die erforderlichen Namespaces. Diese geben uns Zugriff auf die Aspose.Words-Klassen und -Methoden, die wir verwenden werden.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Dokument und DocumentBuilder initialisieren

Als erstes müssen wir ein neues Word-Dokument erstellen und ein`DocumentBuilder` Objekt, um mit dem Erstellen unseres Dokuments zu beginnen.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Erstellen Sie ein neues Dokument.
Document doc = new Document();

// Initialisieren Sie DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Zellen einfügen und Inhalt ausrichten

Als nächstes fügen wir einige Zellen in unser Dokument ein und legen deren Ausrichtung fest. Dies ist wichtig, damit beim Markdown-Export die richtige Ausrichtung erhalten bleibt.

```csharp
// Fügen Sie eine Zelle ein und richten Sie sie rechtsbündig aus.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Fügen Sie eine weitere Zelle ein und richten Sie sie auf die Mitte aus.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Schritt 3: Ausrichtung des Tabelleninhalts für Markdown-Export festlegen

 Jetzt ist es Zeit, die`MarkdownSaveOptions` um die Ausrichtung des Tabelleninhalts in der exportierten Markdown-Datei zu steuern. Wir speichern das Dokument mit verschiedenen Ausrichtungseinstellungen, um zu sehen, wie es funktioniert.

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

// Ausrichtung auf Zentrieren ändern und speichern.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Schritt 4: Automatische Ausrichtung des Tabelleninhalts verwenden

 Der`Auto`Die Ausrichtungsoption übernimmt die Ausrichtung aus dem ersten Absatz in der entsprechenden Tabellenspalte. Dies kann praktisch sein, wenn Sie in einer einzelnen Tabelle gemischte Ausrichtungen haben.

```csharp
// Stellen Sie die Ausrichtung auf „Auto“.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Dokument mit automatischer Ausrichtung speichern.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Abschluss

Und da haben Sie es! Das Exportieren von Word-Dokumenten in Markdown mit ausgerichteten Tabellen mit Aspose.Words für .NET ist ein Kinderspiel, wenn Sie erst einmal wissen, wie es geht. Mit dieser leistungsstarken Bibliothek können Sie die Formatierung und Ausrichtung Ihrer Tabellen ganz einfach steuern und sicherstellen, dass Ihre Markdown-Dokumente genau so aussehen, wie Sie es möchten. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, Word-Dokumente programmgesteuert zu erstellen, zu ändern, zu konvertieren und zu exportieren.

### Kann ich für unterschiedliche Spalten in derselben Tabelle unterschiedliche Ausrichtungen festlegen?
 Ja, mit dem`Auto` Ausrichtungsoption können Sie basierend auf dem ersten Absatz in jeder Spalte unterschiedliche Ausrichtungen haben.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?
 Ja, Aspose.Words für .NET erfordert eine Lizenz für die volle Funktionalität. Sie erhalten eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) zur Auswertung.

### Ist es möglich, mit Aspose.Words andere Dokumentelemente nach Markdown zu exportieren?
Ja, Aspose.Words unterstützt den Export verschiedener Elemente wie Überschriften, Listen und Bilder in das Markdown-Format.

### Wo erhalte ich Unterstützung, wenn Probleme auftreten?
 Unterstützung erhalten Sie vom[Aspose.Words Support Forum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
