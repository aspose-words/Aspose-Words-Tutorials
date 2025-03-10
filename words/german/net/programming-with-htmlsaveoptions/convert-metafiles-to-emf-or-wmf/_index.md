---
title: Metadateien in EMF oder WMF konvertieren
linktitle: Metadateien in EMF oder WMF konvertieren
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Schritt-für-Schritt-Anleitung zum Konvertieren von Metadateien in die Formate EMF oder WMF bei der Konvertierung eines Dokuments in HTML mit Aspose.Words für .NET.
weight: 10
url: /de/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Metadateien in EMF oder WMF konvertieren

## Einführung

Willkommen zu einem weiteren tiefen Einblick in die Welt von Aspose.Words für .NET. Heute widmen wir uns einem tollen Trick: der Konvertierung von SVG-Bildern in die Formate EMF oder WMF in Ihren Word-Dokumenten. Das mag ein wenig technisch klingen, aber keine Sorge. Am Ende dieses Tutorials sind Sie ein Profi darin. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst mit Aspose.Words für .NET beginnen, dieser Leitfaden führt Sie Schritt für Schritt durch alles, was Sie wissen müssen.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass wir alles eingerichtet haben. Folgendes benötigen Sie:

1.  Aspose.Words für .NET-Bibliothek: Stellen Sie sicher, dass Sie die neueste Version haben. Wenn Sie sie nicht haben, können Sie sie hier herunterladen:[Hier](https://releases.aspose.com/words/net/).
2. .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem Computer installiert ist.
3. Entwicklungsumgebung: Eine IDE wie Visual Studio wird Ihnen das Leben leichter machen.
4. Grundkenntnisse in C#: Sie müssen kein Experte sein, aber ein grundlegendes Verständnis ist hilfreich.

Alles dabei? Super! Dann legen wir los.

## Namespaces importieren

Als Erstes müssen wir die erforderlichen Namespaces importieren. Dies ist wichtig, da es unserem Programm mitteilt, wo es die Klassen und Methoden findet, die wir verwenden werden.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Diese Namespaces decken alles ab, von grundlegenden Systemfunktionen bis hin zur spezifischen Aspose.Words-Funktionalität, die wir für dieses Tutorial benötigen.

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Beginnen wir mit der Definition des Pfads zu Ihrem Dokumentverzeichnis. Hier wird Ihr Word-Dokument gespeichert, nachdem wir die Metadateien konvertiert haben.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem Sie Ihr Dokument speichern möchten.

## Schritt 2: Erstellen Sie den HTML-String mit SVG

Als nächstes benötigen wir einen HTML-String, der das SVG-Bild enthält, das wir konvertieren möchten. Hier ist ein einfaches Beispiel:

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' width='500' height='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

Dieser HTML-Ausschnitt enthält ein einfaches SVG mit dem Text „Hallo Welt!“.

## Schritt 3: HTML mit der Option ConvertSvgToEmf laden

 Nun verwenden wir die`HtmlLoadOptions` um anzugeben, wie wir mit den SVG-Bildern im HTML umgehen wollen. Einstellung`ConvertSvgToEmf` Zu`true` stellt sicher, dass SVG-Bilder in das EMF-Format konvertiert werden.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

 Dieser Codeausschnitt erstellt eine neue`Document` Objekt, indem Sie die HTML-Zeichenfolge mit den angegebenen Ladeoptionen darin laden.

## Schritt 4: HtmlSaveOptions für das Metadateiformat festlegen

 Um das Dokument im richtigen Metadateiformat zu speichern, verwenden wir`HtmlSaveOptions` . Hier setzen wir`MetafileFormat` Zu`HtmlMetafileFormat.Png` , aber Sie können dies ändern in`Emf` oder`Wmf` abhängig von Ihren Bedürfnissen.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## Schritt 5: Speichern Sie das Dokument

Abschließend speichern wir das Dokument mit den angegebenen Speicheroptionen.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

Dadurch wird das Dokument mit dem wie definiert konvertierten Metadateiformat im angegebenen Verzeichnis gespeichert.

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, haben Sie SVG-Bilder mit Aspose.Words für .NET erfolgreich in die Formate EMF oder WMF in Ihren Word-Dokumenten konvertiert. Diese Methode ist praktisch, um die Kompatibilität sicherzustellen und die visuelle Integrität Ihrer Dokumente auf verschiedenen Plattformen aufrechtzuerhalten. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Kann ich mit dieser Methode andere Bildformate konvertieren?
Ja, Sie können verschiedene Bildformate konvertieren, indem Sie die Lade- und Speicheroptionen entsprechend anpassen.

### Ist es notwendig, eine bestimmte .NET Framework-Version zu verwenden?
Aspose.Words für .NET unterstützt mehrere Versionen des .NET Frameworks, aber für optimale Kompatibilität und Funktionen ist es immer eine gute Idee, die neueste Version zu verwenden.

### Was ist der Vorteil der Konvertierung von SVG in EMF oder WMF?
Durch die Konvertierung von SVG in EMF oder WMF wird sichergestellt, dass Vektorgrafiken in Umgebungen, die SVG möglicherweise nicht vollständig unterstützen, erhalten bleiben und korrekt gerendert werden.

### Kann ich diesen Vorgang für mehrere Dokumente automatisieren?
Auf jeden Fall! Sie können mehrere HTML-Dateien durchlaufen und dabei denselben Prozess anwenden, um die Konvertierung für die Stapelverarbeitung zu automatisieren.

### Wo finde ich weitere Ressourcen und Support für Aspose.Words für .NET?
 Eine ausführliche Dokumentation finden Sie[Hier](https://reference.aspose.com/words/net/) und erhalten Sie Unterstützung von der Aspose-Community[Hier](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
