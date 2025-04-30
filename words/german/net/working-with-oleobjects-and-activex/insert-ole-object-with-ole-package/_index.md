---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET OLE-Objekte in Word-Dokumente einfügen. Folgen Sie unserer detaillierten Schritt-für-Schritt-Anleitung zum nahtlosen Einbetten von Dateien."
"linktitle": "OLE-Objekt mit OLE-Paket in Word einfügen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "OLE-Objekt mit OLE-Paket in Word einfügen"
"url": "/de/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# OLE-Objekt mit OLE-Paket in Word einfügen

## Einführung

Wenn Sie schon immer eine Datei in ein Word-Dokument einbetten wollten, sind Sie hier genau richtig. Ob ZIP-Datei, Excel-Tabelle oder ein anderer Dateityp – das direkte Einbetten in Ihr Word-Dokument kann unglaublich nützlich sein. Stellen Sie sich das wie ein Geheimfach in Ihrem Dokument vor, in dem Sie allerlei Schätze verstecken können. Heute zeigen wir Ihnen, wie das mit Aspose.Words für .NET funktioniert. Bereit, ein Word-Experte zu werden? Los geht’s!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1. Aspose.Words für .NET: Falls noch nicht geschehen, laden Sie es herunter von [Hier](https://releases.aspose.com/words/net/).
2. Eine Entwicklungsumgebung: Visual Studio oder eine andere .NET-Entwicklungsumgebung.
3. Grundlegende Kenntnisse in C#: Sie müssen kein Experte sein, aber Kenntnisse in C# sind hilfreich.
4. Ein Dokumentverzeichnis: Ein Ordner, in dem Sie Dokumente speichern und abrufen können.

## Namespaces importieren

Zuerst müssen wir unsere Namespaces in Ordnung bringen. Sie müssen die folgenden Namespaces in Ihr Projekt einbinden:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Lassen Sie uns dies in mundgerechte Schritte unterteilen, damit es leicht zu befolgen ist.

## Schritt 1: Richten Sie Ihr Dokument ein

Stellen Sie sich vor, Sie sind ein Künstler mit einer leeren Leinwand. Zuerst benötigen wir unsere leere Leinwand, also unser Word-Dokument. So richten Sie es ein:

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Dieser Code initialisiert ein neues Word-Dokument und richtet einen DocumentBuilder ein, den wir zum Einfügen von Inhalten in unser Dokument verwenden.

## Schritt 2: Lesen Sie Ihr OLE-Objekt

Als Nächstes lesen wir die Datei, die Sie einbetten möchten. Stellen Sie sich das so vor, als würden Sie den Schatz aus Ihrem Geheimfach holen:

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

Hier erstellen wir einen Speicherstrom aus dem Byte-Array und verwenden die `InsertOleObject` Methode, um es in das Dokument einzubetten. Wir legen auch den Dateinamen und den Anzeigenamen für das eingebettete Objekt fest.

## Schritt 4: Speichern Sie Ihr Dokument

Zum Schluss speichern wir unser Meisterwerk:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

Dadurch wird das Dokument mit Ihrer eingebetteten Datei im angegebenen Verzeichnis gespeichert.

## Abschluss

Und da haben Sie es! Sie haben mit Aspose.Words für .NET erfolgreich ein OLE-Objekt in ein Word-Dokument eingebettet. Es ist, als würden Sie Ihrem Dokument ein verstecktes Juwel hinzufügen, das jederzeit enthüllt werden kann. Diese Technik kann für eine Vielzahl von Anwendungen, von der technischen Dokumentation bis hin zu dynamischen Berichten, unglaublich nützlich sein. 

## Häufig gestellte Fragen

### Kann ich mit dieser Methode andere Dateitypen einbetten?
Ja, Sie können verschiedene Dateitypen wie Excel-Tabellen, PDFs und Bilder einbetten.

### Benötige ich eine Lizenz für Aspose.Words?
Ja, Sie benötigen eine gültige Lizenz. Sie erhalten eine [vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) zur Auswertung.

### Wie kann ich den Anzeigenamen des OLE-Objekts anpassen?
Sie können die `DisplayName` Eigentum der `OlePackage` um es anzupassen.

### Ist Aspose.Words mit .NET Core kompatibel?
Ja, Aspose.Words unterstützt sowohl .NET Framework als auch .NET Core.

### Kann ich das eingebettete OLE-Objekt im Word-Dokument bearbeiten?
Nein, Sie können das OLE-Objekt nicht direkt in Word bearbeiten. Sie müssen es in der nativen Anwendung öffnen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}