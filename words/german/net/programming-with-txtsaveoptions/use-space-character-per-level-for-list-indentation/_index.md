---
title: Verwenden Sie pro Ebene ein Leerzeichen für die Listeneinrückung
linktitle: Verwenden Sie pro Ebene ein Leerzeichen für die Listeneinrückung
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mehrstufige Listen mit Leerzeicheneinrückungen in Aspose.Words für .NET erstellen. Schritt-für-Schritt-Anleitung zur präzisen Dokumentformatierung.
weight: 10
url: /de/net/programming-with-txtsaveoptions/use-space-character-per-level-for-list-indentation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden Sie pro Ebene ein Leerzeichen für die Listeneinrückung

## Einführung

Beim Formatieren von Dokumenten, insbesondere bei der Arbeit mit Listen, ist Präzision der Schlüssel. In Szenarien, in denen Sie Dokumente mit verschiedenen Einrückungsebenen erstellen müssen, bietet Aspose.Words für .NET leistungsstarke Tools für diese Aufgabe. Eine besonders nützliche Funktion ist das Konfigurieren der Listeneinrückung in Textdateien. In dieser Anleitung erfahren Sie, wie Sie Leerzeichen für die Listeneinrückung verwenden und so sicherstellen, dass Ihr Dokument die gewünschte Struktur und Lesbarkeit beibehält.

## Voraussetzungen

Bevor Sie mit dem Tutorial beginnen, benötigen Sie Folgendes:

-  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Aspose.Words-Bibliothek installiert haben. Wenn Sie sie noch nicht haben, können Sie sie von der[Aspose-Website](https://releases.aspose.com/words/net/).
- Visual Studio: Eine Entwicklungsumgebung zum Schreiben und Testen Ihres Codes.
- Grundlegende Kenntnisse in C#: Wenn Sie mit C# und dem .NET-Framework vertraut sind, können Sie problemlos mit den Schritten weitermachen.

## Namespaces importieren

Um mit Aspose.Words arbeiten zu können, müssen Sie die erforderlichen Namespaces importieren. So können Sie sie in Ihr Projekt einbinden:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Lassen Sie uns den Vorgang zum Erstellen eines Dokuments mit einer mehrstufigen Liste und zum Festlegen von Leerzeichen für die Einrückung aufschlüsseln. 

## Schritt 1: Richten Sie Ihr Dokument ein

 Zuerst müssen Sie ein neues Dokument erstellen und das`DocumentBuilder` Objekt. Mit diesem Objekt können Sie ganz einfach Inhalte hinzufügen und diese nach Bedarf formatieren.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Erstellen Sie das Dokument und fügen Sie Inhalt hinzu
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ersetzen Sie in diesem Snippet`"YOUR DOCUMENTS DIRECTORY"` durch den tatsächlichen Pfad, in dem Sie Ihr Dokument speichern möchten.

## Schritt 2: Erstellen Sie eine Liste mit mehreren Einrückungsebenen

 Mit dem`DocumentBuilder` Instanz können Sie jetzt eine Liste mit verschiedenen Einrückungsebenen erstellen. Verwenden Sie die`ListFormat` -Eigenschaft, um eine Nummerierung anzuwenden und die Listenelemente nach Bedarf einzurücken.

```csharp
// Erstellen Sie eine Liste mit drei Einrückungsebenen
builder.ListFormat.ApplyNumberDefault();
builder.Write("Element 1");
builder.ListFormat.ListIndent();
builder.Write("Element 2");
builder.ListFormat.ListIndent();
builder.Write("Element 3");
```

 In diesem Schritt`ApplyNumberDefault` legt das Listenformat fest und`ListIndent` wird verwendet, um die Einrückungsebene für jedes nachfolgende Listenelement zu erhöhen.

## Schritt 3: Leerzeichen für Einrückung konfigurieren

Nachdem Sie Ihre Liste eingerichtet haben, müssen Sie im nächsten Schritt konfigurieren, wie die Listeneinrückung beim Speichern des Dokuments in einer Textdatei behandelt wird. Sie verwenden`TxtSaveOptions` um anzugeben, dass Leerzeichen zur Einrückung verwendet werden sollen.

```csharp
// Verwenden Sie ein Leerzeichen pro Ebene für die Listeneinrückung
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.ListIndentation.Count = 3;
saveOptions.ListIndentation.Character = ' ';
```

 Hier,`ListIndentation.Count` gibt die Anzahl der Leerzeichen pro Einrückungsebene an und`ListIndentation.Character` legt das tatsächliche Zeichen fest, das für die Einrückung verwendet wird.

## Schritt 4: Speichern Sie das Dokument mit den angegebenen Optionen

Speichern Sie abschließend Ihr Dokument mit den konfigurierten Optionen. Dadurch werden die Einrückungseinstellungen übernommen und Ihre Datei im gewünschten Format gespeichert.

```csharp
// Speichern Sie das Dokument mit den angegebenen Optionen
doc.Save(dataDir + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
```

 Dieser Codeausschnitt speichert das Dokument im angegebenen Pfad in`dataDir` mit dem Dateinamen`"WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt"`. In der gespeicherten Datei wird die Liste entsprechend Ihren Einrückungseinstellungen formatiert sein.

## Abschluss

Wenn Sie diese Schritte befolgen, haben Sie erfolgreich ein Dokument mit mehrstufiger Listeneinrückung erstellt, bei dem Leerzeichen zur Formatierung verwendet werden. Dieser Ansatz stellt sicher, dass Ihre Listen gut strukturiert und leicht zu lesen sind, auch wenn sie als Textdateien gespeichert werden. Aspose.Words für .NET bietet robuste Tools zur Dokumentbearbeitung, und die Beherrschung dieser Funktionen kann Ihre Dokumentverarbeitungs-Workflows erheblich verbessern.

## Häufig gestellte Fragen

### Kann ich zum Einrücken von Listen andere Zeichen als Leerzeichen verwenden?
 Ja, Sie können verschiedene Zeichen für die Listeneinrückung angeben, indem Sie`Character` Immobilien in`TxtSaveOptions`.

### Wie verwende ich in Listen Aufzählungszeichen anstelle von Nummern?
 Verwenden`ListFormat.ApplyBulletDefault()` anstatt`ApplyNumberDefault()` um eine Aufzählungsliste zu erstellen.

### Kann ich die Anzahl der Leerzeichen für Einrückungen dynamisch anpassen?
 Ja, Sie können die`ListIndentation.Count` -Eigenschaft, um die Anzahl der Leerzeichen entsprechend Ihren Anforderungen festzulegen.

### Ist es möglich, die Listeneinrückung nach der Erstellung des Dokuments zu ändern?
Ja, Sie können die Listenformatierung und Einrückungseinstellungen jederzeit ändern, bevor Sie das Dokument speichern.

### Welche anderen Dokumentformate unterstützen Einstellungen für Listeneinrückungen?
Neben Textdateien können Listeneinrückungseinstellungen bei Verwendung von Aspose.Words auch auf andere Formate wie DOCX, PDF und HTML angewendet werden.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
