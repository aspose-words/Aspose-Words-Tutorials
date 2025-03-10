---
title: Präfix für CSS-Klassennamen hinzufügen
linktitle: Präfix für CSS-Klassennamen hinzufügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie beim Speichern von Word-Dokumenten als HTML mit Aspose.Words für .NET ein CSS-Klassennamenpräfix hinzufügen. Schritt-für-Schritt-Anleitung, Codeausschnitte und FAQs enthalten.
weight: 10
url: /de/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Präfix für CSS-Klassennamen hinzufügen

## Einführung

Willkommen! Wenn Sie in die Welt von Aspose.Words für .NET eintauchen, erwartet Sie ein Leckerbissen. Heute werden wir untersuchen, wie Sie beim Speichern eines Word-Dokuments als HTML mit Aspose.Words für .NET ein CSS-Klassennamenpräfix hinzufügen. Diese Funktion ist äußerst praktisch, wenn Sie Klassennamenkonflikte in Ihren HTML-Dateien vermeiden möchten.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

-  Aspose.Words für .NET: Wenn Sie es noch nicht installiert haben,[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Visual Studio oder eine andere C#-IDE.
-  Ein Word-Dokument: Wir verwenden ein Dokument namens`Rendering.docx`. Platzieren Sie es in Ihrem Projektverzeichnis.

## Namespaces importieren

Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr C#-Projekt importiert haben. Fügen Sie diese oben in Ihrer Codedatei hinzu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Lassen Sie uns nun in die Schritt-für-Schritt-Anleitung eintauchen!

## Schritt 1: Richten Sie Ihr Projekt ein

Bevor wir mit dem Hinzufügen eines CSS-Klassennamenpräfixes beginnen können, richten wir unser Projekt ein.

### Schritt 1.1: Neues Projekt erstellen

 Starten Sie Visual Studio und erstellen Sie ein neues Konsolen-App-Projekt. Geben Sie ihm einen einprägsamen Namen wie`AsposeCssPrefixExample`.

### Schritt 1.2: Aspose.Words für .NET hinzufügen

Wenn Sie dies noch nicht getan haben, fügen Sie Aspose.Words für .NET über NuGet zu Ihrem Projekt hinzu. Öffnen Sie einfach die NuGet Package Manager-Konsole und führen Sie Folgendes aus:

```bash
Install-Package Aspose.Words
```

Großartig! Jetzt können wir mit dem Codieren beginnen.

## Schritt 2: Laden Sie Ihr Dokument

Als Erstes müssen wir das Word-Dokument laden, das wir in HTML konvertieren möchten.

### Schritt 2.1: Dokumentpfad festlegen

 Richten Sie den Pfad zu Ihrem Dokumentverzeichnis ein. Für dieses Tutorial nehmen wir an, dass sich Ihr Dokument in einem Ordner namens`Documents` in Ihrem Projektverzeichnis.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Schritt 2.2: Laden Sie das Dokument

Laden wir nun das Dokument mit Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Schritt 3: HTML-Speicheroptionen konfigurieren

Als Nächstes müssen wir die HTML-Speicheroptionen so konfigurieren, dass sie ein CSS-Klassennamenpräfix enthalten.

### Schritt 3.1: HTML-Speicheroptionen erstellen

 Instanziieren Sie den`HtmlSaveOptions` Objekt und setzen Sie den CSS-Stylesheet-Typ auf`External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Schritt 3.2: CSS-Klassennamenpräfix festlegen

 Nun setzen wir die`CssClassNamePrefix` Eigenschaft auf das gewünschte Präfix. Für dieses Beispiel verwenden wir`"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Schritt 4: Speichern Sie das Dokument als HTML

Abschließend speichern wir das Dokument mit unseren konfigurierten Optionen als HTML-Datei.


Geben Sie den Pfad zur HTML-Ausgabedatei an und speichern Sie das Dokument.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Schritt 5: Überprüfen der Ausgabe

 Navigieren Sie nach dem Ausführen Ihres Projekts zu Ihrem`Documents` Ordner. Sie sollten eine HTML-Datei mit dem Namen finden`WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html` Öffnen Sie diese Datei in einem Texteditor oder Browser, um zu überprüfen, ob die CSS-Klassen das Präfix haben`pfx_`.

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, haben Sie Ihrer HTML-Ausgabe mithilfe von Aspose.Words für .NET erfolgreich ein CSS-Klassennamenpräfix hinzugefügt. Diese einfache, aber leistungsstarke Funktion kann Ihnen dabei helfen, saubere und konfliktfreie Stile in Ihren HTML-Dokumenten beizubehalten.

## Häufig gestellte Fragen

### Kann ich für jeden Speichervorgang ein anderes Präfix verwenden?
 Ja, Sie können das Präfix bei jedem Speichern eines Dokuments anpassen, indem Sie das`CssClassNamePrefix` Eigentum.

### Unterstützt diese Methode Inline-CSS?
 Der`CssClassNamePrefix`-Eigenschaft funktioniert mit externem CSS. Für Inline-CSS benötigen Sie einen anderen Ansatz.

### Wie kann ich andere HTML-Speicheroptionen einbinden?
 Sie können verschiedene Eigenschaften von`HtmlSaveOptions` um Ihre HTML-Ausgabe anzupassen. Überprüfen Sie die[Dokumentation](https://reference.aspose.com/words/net/) für weitere Details.

### Ist es möglich, das HTML in einem Stream zu speichern?
 Absolut! Sie können das Dokument in einem Stream speichern, indem Sie das Stream-Objekt an den`Save` Verfahren.

### Wie erhalte ich Unterstützung, wenn Probleme auftreten?
 Unterstützung erhalten Sie vom[Aspose-Forum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
