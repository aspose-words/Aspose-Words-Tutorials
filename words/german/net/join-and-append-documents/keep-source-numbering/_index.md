---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET Dokumente unter Beibehaltung der Formatierung importieren. Schritt-für-Schritt-Anleitung mit Codebeispielen."
"linktitle": "Quellennummerierung beibehalten"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Quellennummerierung beibehalten"
"url": "/de/net/join-and-append-documents/keep-source-numbering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Quellennummerierung beibehalten

## Einführung

Bei der Arbeit mit Aspose.Words für .NET kann der Import von Dokumenten von einer Quelle in eine andere unter Beibehaltung der Formatierung effizient mithilfe der `NodeImporter` Klasse. Dieses Tutorial führt Sie Schritt für Schritt durch den Prozess.

## Voraussetzungen

Stellen Sie vor dem Start sicher, dass Sie über Folgendes verfügen:
- Visual Studio ist auf Ihrem Computer installiert.
- Aspose.Words für .NET installiert. Falls nicht, laden Sie es herunter von [Hier](https://releases.aspose.com/words/net/).
- Grundkenntnisse in C#- und .NET-Programmierung.

## Namespaces importieren

Fügen Sie zunächst die erforderlichen Namespaces in Ihr Projekt ein:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## Schritt 1: Richten Sie Ihr Projekt ein

Beginnen Sie, indem Sie in Visual Studio ein neues C#-Projekt erstellen und Aspose.Words über den NuGet-Paket-Manager installieren.

## Schritt 2: Dokumente initialisieren
Erstellen Sie Instanzen der Quelle (`srcDoc`) und Ziel (`dstDoc`) Dokumente.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Schritt 3: Importoptionen konfigurieren
Richten Sie Importoptionen ein, um die Quellformatierung, einschließlich nummerierter Absätze, beizubehalten.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## Schritt 4: Absätze importieren
Durchlaufen Sie Absätze im Quelldokument und importieren Sie sie in das Zieldokument.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## Schritt 5: Speichern Sie das Dokument
Speichern Sie das zusammengeführte Dokument am gewünschten Speicherort.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## Abschluss

Zusammenfassend lässt sich sagen, dass die Verwendung von Aspose.Words für .NET zum Importieren von Dokumenten unter Beibehaltung der Formatierung unkompliziert ist mit dem `NodeImporter` Klasse. Diese Methode stellt sicher, dass Ihre Dokumente ihr ursprüngliches Aussehen und ihre Struktur nahtlos beibehalten.

## Häufig gestellte Fragen

### Kann ich Dokumente mit unterschiedlichen Formatierungsstilen importieren?
Ja, die `NodeImporter` Klasse unterstützt den Import von Dokumenten mit unterschiedlichen Formatierungsstilen.

### Was ist, wenn meine Dokumente komplexe Tabellen und Bilder enthalten?
Aspose.Words für .NET verarbeitet komplexe Strukturen wie Tabellen und Bilder während Importvorgängen.

### Ist Aspose.Words mit allen Versionen von .NET kompatibel?
Aspose.Words unterstützt .NET Framework- und .NET Core-Versionen für eine nahtlose Integration.

### Wie gehe ich mit Fehlern beim Dokumentenimport um?
Verwenden Sie Try-Catch-Blöcke, um Ausnahmen zu behandeln, die während des Importvorgangs auftreten können.

### Wo finde ich ausführlichere Dokumentation zu Aspose.Words für .NET?
Besuchen Sie die [Dokumentation](https://reference.aspose.com/words/net/) für umfassende Anleitungen und API-Referenzen.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}