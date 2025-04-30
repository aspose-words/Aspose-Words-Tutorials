---
"description": "Erfahren Sie, wie Sie in Aspose.Words für .NET mehrstufige Listen mit Leerzeicheneinrückung erstellen. Schritt-für-Schritt-Anleitung zur präzisen Dokumentformatierung."
"linktitle": "Leerzeichen pro Ebene für Listeneinrückung verwenden"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Leerzeichen pro Ebene für Listeneinrückung verwenden"
"url": "/de/net/programming-with-txtsaveoptions/use-space-character-per-level-for-list-indentation/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Leerzeichen pro Ebene für Listeneinrückung verwenden

## Einführung

Bei der Dokumentformatierung, insbesondere bei der Arbeit mit Listen, ist Präzision entscheidend. Für die Erstellung von Dokumenten mit unterschiedlichen Einrückungsebenen bietet Aspose.Words für .NET leistungsstarke Tools. Besonders hilfreich ist die Konfiguration von Listeneinrückungen in Textdateien. Diese Anleitung erklärt Ihnen, wie Sie Leerzeichen für Listeneinrückungen verwenden und so die gewünschte Struktur und Lesbarkeit Ihres Dokuments gewährleisten.

## Voraussetzungen

Bevor Sie mit dem Tutorial beginnen, benötigen Sie Folgendes:

- Aspose.Words für .NET: Stellen Sie sicher, dass die Aspose.Words-Bibliothek installiert ist. Falls Sie sie noch nicht haben, können Sie sie von der [Aspose-Website](https://releases.aspose.com/words/net/).
- Visual Studio: Eine Entwicklungsumgebung zum Schreiben und Testen Ihres Codes.
- Grundlegende Kenntnisse in C#: Wenn Sie mit C# und dem .NET-Framework vertraut sind, können Sie problemlos weitermachen.

## Namespaces importieren

Um mit Aspose.Words arbeiten zu können, müssen Sie die erforderlichen Namespaces importieren. So können Sie sie in Ihr Projekt einbinden:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Lassen Sie uns den Vorgang zum Erstellen eines Dokuments mit einer mehrstufigen Liste und zum Festlegen von Leerzeichen für die Einrückung aufschlüsseln. 

## Schritt 1: Richten Sie Ihr Dokument ein

Zuerst müssen Sie ein neues Dokument erstellen und das `DocumentBuilder` Objekt. Mit diesem Objekt können Sie ganz einfach Inhalte hinzufügen und nach Bedarf formatieren.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Erstellen Sie das Dokument und fügen Sie Inhalte hinzu
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ersetzen Sie in diesem Snippet `"YOUR DOCUMENTS DIRECTORY"` durch den tatsächlichen Pfad, in dem Sie Ihr Dokument speichern möchten.

## Schritt 2: Erstellen Sie eine Liste mit mehreren Einrückungsebenen

Mit dem `DocumentBuilder` Beispielsweise können Sie jetzt eine Liste mit verschiedenen Einrückungsebenen erstellen. Verwenden Sie die `ListFormat` -Eigenschaft, um eine Nummerierung anzuwenden und die Listenelemente nach Bedarf einzurücken.

```csharp
// Erstellen Sie eine Liste mit drei Einrückungsebenen
builder.ListFormat.ApplyNumberDefault();
builder.Write("Element 1");
builder.ListFormat.ListIndent();
builder.Write("Element 2");
builder.ListFormat.ListIndent();
builder.Write("Element 3");
```

In diesem Schritt `ApplyNumberDefault` legt das Listenformat fest und `ListIndent` wird verwendet, um die Einrückungsebene für jedes nachfolgende Listenelement zu erhöhen.

## Schritt 3: Leerzeichen für Einrückung konfigurieren

Nachdem Sie Ihre Liste eingerichtet haben, konfigurieren Sie im nächsten Schritt, wie die Listeneinrückung beim Speichern des Dokuments in einer Textdatei behandelt wird. Sie verwenden `TxtSaveOptions` um anzugeben, dass Leerzeichen zur Einrückung verwendet werden sollen.

```csharp
// Verwenden Sie ein Leerzeichen pro Ebene für die Listeneinrückung
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.ListIndentation.Count = 3;
saveOptions.ListIndentation.Character = ' ';
```

Hier, `ListIndentation.Count` gibt die Anzahl der Leerzeichen pro Einrückungsebene an und `ListIndentation.Character` legt das tatsächliche Zeichen fest, das für die Einrückung verwendet wird.

## Schritt 4: Speichern Sie das Dokument mit den angegebenen Optionen

Speichern Sie Ihr Dokument abschließend mit den konfigurierten Optionen. Dadurch werden die Einrückungseinstellungen übernommen und Ihre Datei im gewünschten Format gespeichert.

```csharp
// Speichern Sie das Dokument mit den angegebenen Optionen
doc.Save(dataDir + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
```

Dieser Codeausschnitt speichert das Dokument im angegebenen Pfad in `dataDir` mit dem Dateinamen `"WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt"`. In der gespeicherten Datei wird die Liste entsprechend Ihren Einrückungseinstellungen formatiert.

## Abschluss

Mit diesen Schritten haben Sie erfolgreich ein Dokument mit mehrstufiger Listeneinrückung und Leerzeichen zur Formatierung erstellt. Dieser Ansatz stellt sicher, dass Ihre Listen gut strukturiert und leicht lesbar sind, auch wenn sie als Textdateien gespeichert werden. Aspose.Words für .NET bietet robuste Tools zur Dokumentbearbeitung. Die Beherrschung dieser Funktionen kann Ihre Dokumentverarbeitungsabläufe erheblich verbessern.

## Häufig gestellte Fragen

### Kann ich für die Listeneinrückung andere Zeichen als Leerzeichen verwenden?
Ja, Sie können verschiedene Zeichen für die Listeneinrückung angeben, indem Sie die `Character` Eigentum in `TxtSaveOptions`.

### Wie verwende ich Aufzählungszeichen anstelle von Zahlen in Listen?
Verwenden `ListFormat.ApplyBulletDefault()` anstatt `ApplyNumberDefault()` um eine Aufzählungsliste zu erstellen.

### Kann ich die Anzahl der Leerzeichen für die Einrückung dynamisch anpassen?
Ja, Sie können die `ListIndentation.Count` Eigenschaft, um die Anzahl der Leerzeichen entsprechend Ihren Anforderungen festzulegen.

### Ist es möglich, die Listeneinrückung nach der Erstellung des Dokuments zu ändern?
Ja, Sie können die Listenformatierung und Einrückungseinstellungen jederzeit ändern, bevor Sie das Dokument speichern.

### Welche anderen Dokumentformate unterstützen Einstellungen für Listeneinrückungen?
Neben Textdateien können bei Verwendung von Aspose.Words Einstellungen für Listeneinrückungen auch auf andere Formate wie DOCX, PDF und HTML angewendet werden.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}