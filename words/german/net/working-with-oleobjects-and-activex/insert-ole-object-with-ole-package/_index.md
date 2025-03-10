---
title: OLE-Objekt mit OLE-Paket in Word einfügen
linktitle: OLE-Objekt mit OLE-Paket in Word einfügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET OLE-Objekte in Word-Dokumente einfügen. Folgen Sie unserer detaillierten Schritt-für-Schritt-Anleitung, um Dateien nahtlos einzubetten.
weight: 10
url: /de/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# OLE-Objekt mit OLE-Paket in Word einfügen

## Einführung

Wenn Sie schon einmal eine Datei in ein Word-Dokument einbetten wollten, sind Sie hier richtig. Egal, ob es sich um eine ZIP-Datei, eine Excel-Tabelle oder einen anderen Dateityp handelt, das direkte Einbetten in Ihr Word-Dokument kann unglaublich nützlich sein. Stellen Sie es sich so vor, als hätten Sie ein Geheimfach in Ihrem Dokument, in dem Sie alle möglichen Schätze verstecken können. Und heute zeigen wir Ihnen, wie Sie dies mit Aspose.Words für .NET tun können. Sind Sie bereit, ein Word-Zauberer zu werden? Tauchen wir ein!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1. Aspose.Words für .NET: Falls noch nicht geschehen, laden Sie es herunter von[Hier](https://releases.aspose.com/words/net/).
2. Eine Entwicklungsumgebung: Visual Studio oder eine andere .NET-Entwicklungsumgebung.
3. Grundlegende Kenntnisse in C#: Sie müssen kein Experte sein, aber Kenntnisse in C# sind hilfreich.
4. Ein Dokumentverzeichnis: Ein Ordner, in dem Sie Dokumente speichern und abrufen können.

## Namespaces importieren

Das Wichtigste zuerst: Bringen wir unsere Namespaces in Ordnung. Sie müssen die folgenden Namespaces in Ihr Projekt aufnehmen:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Lassen Sie uns dies in mundgerechte Schritte aufteilen, damit es leicht nachvollziehbar ist.

## Schritt 1: Richten Sie Ihr Dokument ein

Stellen Sie sich vor, Sie sind ein Künstler mit einer leeren Leinwand. Zuerst brauchen wir unsere leere Leinwand, also unser Word-Dokument. So richten Sie es ein:

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Dieser Code initialisiert ein neues Word-Dokument und richtet einen DocumentBuilder ein, den wir zum Einfügen von Inhalten in unser Dokument verwenden.

## Schritt 2: Lesen Sie Ihr altes Objekt

Als nächstes lesen wir die Datei, die Sie einbetten möchten. Stellen Sie sich das so vor, als würden Sie den Schatz aufheben, den Sie in Ihrem Geheimfach verstecken möchten:

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

Diese Zeile liest alle Bytes aus Ihrer ZIP-Datei und speichert sie in einem Byte-Array.

## Schritt 3: Einfügen des Ole-Objekts

Jetzt kommt der magische Teil. Wir werden die Datei in unser Word-Dokument einbetten:

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

 Hier erzeugen wir einen Speicherstrom aus dem Byte-Array und verwenden die`InsertOleObject` Methode, um es in das Dokument einzubetten. Wir legen auch den Dateinamen und den Anzeigenamen für das eingebettete Objekt fest.

## Schritt 4: Speichern Sie Ihr Dokument

Zum Schluss speichern wir unser Meisterwerk:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

Dadurch wird das Dokument mit Ihrer eingebetteten Datei im angegebenen Verzeichnis gespeichert.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich ein OLE-Objekt in ein Word-Dokument eingebettet, indem Sie Aspose.Words für .NET verwenden. Es ist, als würden Sie Ihrem Dokument ein verstecktes Juwel hinzufügen, das jederzeit enthüllt werden kann. Diese Technik kann für eine Vielzahl von Anwendungen unglaublich nützlich sein, von der technischen Dokumentation bis hin zu dynamischen Berichten. 

## Häufig gestellte Fragen

### Kann ich mit dieser Methode andere Dateitypen einbetten?
Ja, Sie können verschiedene Dateitypen wie Excel-Tabellen, PDFs und Bilder einbetten.

### Benötige ich eine Lizenz für Aspose.Words?
 Ja, Sie benötigen eine gültige Lizenz. Sie erhalten eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) zur Auswertung.

### Wie kann ich den Anzeigenamen des OLE-Objekts anpassen?
 Sie können die`DisplayName` Eigentum der`OlePackage` um es anzupassen.

### Ist Aspose.Words mit .NET Core kompatibel?
Ja, Aspose.Words unterstützt sowohl .NET Framework als auch .NET Core.

### Kann ich das eingebettete OLE-Objekt im Word-Dokument bearbeiten?
Nein, Sie können das OLE-Objekt nicht direkt in Word bearbeiten. Sie müssen es in der nativen Anwendung öffnen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
