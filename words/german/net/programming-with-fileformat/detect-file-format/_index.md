---
title: Dokumentdateiformat erkennen
linktitle: Dokumentdateiformat erkennen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser umfassenden Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Dokumentdateiformate erkennen.
weight: 10
url: /de/net/programming-with-fileformat/detect-file-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentdateiformat erkennen

## Einführung

In der heutigen digitalen Welt ist die effiziente Verwaltung verschiedener Dokumentformate von entscheidender Bedeutung. Egal, ob Sie Word, PDF, HTML oder andere Formate verwenden, die Fähigkeit, diese Dateien richtig zu erkennen und zu verarbeiten, kann Ihnen viel Zeit und Mühe sparen. In diesem Tutorial erfahren Sie, wie Sie Dokumentdateiformate mit Aspose.Words für .NET erkennen. Dieser Leitfaden führt Sie durch alles, was Sie wissen müssen, von den Voraussetzungen bis hin zu einer detaillierten Schritt-für-Schritt-Anleitung.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

-  Aspose.Words für .NET: Sie können es herunterladen von[Hier](https://releases.aspose.com/words/net/) . Stellen Sie sicher, dass Sie eine gültige Lizenz haben. Wenn nicht, können Sie eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Jede aktuelle Version funktioniert einwandfrei.
- .NET Framework: Stellen Sie sicher, dass Sie die richtige Version installiert haben.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Lassen Sie uns das Beispiel in mehrere Schritte aufteilen, damit es leichter verständlich ist.

## Schritt 1: Verzeichnisse einrichten

Zuerst müssen wir Verzeichnisse einrichten, in denen die Dateien nach ihrem Format sortiert werden.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Erstellen Sie die Verzeichnisse, falls sie noch nicht vorhanden sind.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Schritt 2: Holen Sie sich die Liste der Dateien

Als Nächstes erhalten wir eine Liste der Dateien aus dem Verzeichnis, ausgenommen beschädigte Dokumente.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Schritt 3: Dateiformate erkennen

Jetzt durchlaufen wir jede Datei und ermitteln ihr Format mit Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Anzeige des Dokumenttyps
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Abschluss

Das Erkennen von Dokumentdateiformaten mit Aspose.Words für .NET ist ein unkomplizierter Vorgang. Indem Sie Ihre Verzeichnisse einrichten, Ihre Dateiliste abrufen und Aspose.Words zum Erkennen von Dateiformaten verwenden, können Sie Ihre Dokumente effizient organisieren und verwalten. Dieser Ansatz spart nicht nur Zeit, sondern stellt auch sicher, dass Sie verschiedene Dokumentformate korrekt verarbeiten.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek für die programmgesteuerte Arbeit mit Word-Dokumenten. Entwickler können damit Dokumente in verschiedenen Formaten erstellen, ändern und konvertieren.

### Kann Aspose.Words verschlüsselte Dokumente erkennen?
Ja, Aspose.Words kann erkennen, ob ein Dokument verschlüsselt ist, und Sie können solche Dokumente entsprechend behandeln.

### Welche Formate kann Aspose.Words erkennen?
Aspose.Words kann eine Vielzahl von Formaten erkennen, darunter DOC, DOCX, RTF, HTML, MHTML, ODT und viele mehr.

### Wie kann ich eine temporäre Lizenz für Aspose.Words erhalten?
 Eine vorläufige Lizenz erhalten Sie bei der[Aspose Kauf](https://purchase.aspose.com/temporary-license/) Seite.

### Wo finde ich die Dokumentation für Aspose.Words?
 Die Dokumentation für Aspose.Words finden Sie[Hier](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
