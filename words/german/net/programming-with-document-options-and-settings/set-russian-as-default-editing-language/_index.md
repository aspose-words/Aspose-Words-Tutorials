---
title: Russisch als Standardbearbeitungssprache festlegen
linktitle: Russisch als Standardbearbeitungssprache festlegen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Russisch als Standardbearbeitungssprache in Word-Dokumenten festlegen. Folgen Sie unserer Schritt-für-Schritt-Anleitung für detaillierte Anweisungen.
weight: 10
url: /de/net/programming-with-document-options-and-settings/set-russian-as-default-editing-language/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Russisch als Standardbearbeitungssprache festlegen

## Einführung

In der heutigen mehrsprachigen Welt ist es oft notwendig, Ihre Dokumente anzupassen, um den Sprachpräferenzen verschiedener Zielgruppen gerecht zu werden. Das Festlegen einer Standardbearbeitungssprache in einem Word-Dokument ist eine solche Anpassung. Wenn Sie Aspose.Words für .NET verwenden, führt Sie dieses Tutorial durch das Festlegen von Russisch als Standardbearbeitungssprache in Ihren Word-Dokumenten. 

Diese Schritt-für-Schritt-Anleitung stellt sicher, dass Sie jeden Teil des Prozesses verstehen, vom Einrichten Ihrer Umgebung bis zum Überprüfen der Spracheinstellungen in Ihrem Dokument.

## Voraussetzungen

Bevor Sie mit dem Programmieren beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:

1.  Aspose.Words für .NET: Sie benötigen die Bibliothek Aspose.Words für .NET. Sie können sie von der[Aspose-Veröffentlichungen](https://releases.aspose.com/words/net/) Seite.
2. Entwicklungsumgebung: Zum Codieren und Ausführen von .NET-Anwendungen wird eine IDE wie Visual Studio empfohlen.
3. Grundkenntnisse in C#: Um diesem Tutorial folgen zu können, ist es wichtig, dass Sie die Programmiersprache C# und das .NET-Framework verstehen.

## Namespaces importieren

Bevor wir ins Detail gehen, stellen Sie sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importieren. Diese Namespaces bieten Zugriff auf die Klassen und Methoden, die zum Bearbeiten von Word-Dokumenten erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

## Schritt 1: Einrichten von LoadOptions

 Zuerst müssen wir die`LoadOptions` um die Standardbearbeitungssprache auf Russisch einzustellen. Dieser Schritt beinhaltet das Erstellen einer Instanz von`LoadOptions` und die Einstellung`LanguagePreferences.DefaultEditingLanguage` Eigentum.

### LoadOptions-Instanz erstellen

```csharp
LoadOptions loadOptions = new LoadOptions();
```

### Standardbearbeitungssprache auf Russisch einstellen

```csharp
loadOptions.LanguagePreferences.DefaultEditingLanguage = EditingLanguage.Russian;
```

 In diesem Schritt erstellen Sie eine Instanz von`LoadOptions` und setzen Sie seine`DefaultEditingLanguage`Eigentum an`EditingLanguage.Russian`. Dadurch wird Aspose.Words angewiesen, Russisch als Standardbearbeitungssprache zu behandeln, wenn ein Dokument mit diesen Optionen geladen wird.

## Schritt 2: Laden Sie das Dokument

 Als nächstes müssen wir das Word-Dokument mit dem`LoadOptions` im vorherigen Schritt konfiguriert. Dazu müssen Sie den Pfad zu Ihrem Dokument angeben und die`LoadOptions` Instanz an die`Document` Konstruktor.

### Dokumentpfad angeben

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

### Dokument mit LoadOptions laden

```csharp
Document doc = new Document(dataDir + "No default editing language.docx", loadOptions);
```

 In diesem Schritt geben Sie den Verzeichnispfad an, in dem sich Ihr Dokument befindet und laden das Dokument mit dem`Document` Konstruktor. Der`LoadOptions` Stellen Sie sicher, dass Russisch als Standardbearbeitungssprache eingestellt ist.

## Schritt 3: Überprüfen der Standardbearbeitungssprache

 Nach dem Laden des Dokuments ist es wichtig zu überprüfen, ob die Standardbearbeitungssprache auf Russisch eingestellt ist. Dazu müssen Sie die`LocaleId` des Standardschriftstils des Dokuments.

### Holen Sie sich die LocaleId der Standardschriftart

```csharp
int localeId = doc.Styles.DefaultFont.LocaleId;
```

### Überprüfen Sie, ob die LocaleId mit der russischen Sprache übereinstimmt

```csharp
Console.WriteLine(
    localeId == (int)EditingLanguage.Russian
        ? "The document either has no any language set in defaults or it was set to Russian originally."
        : "The document default language was set to another than Russian language originally, so it is not overridden.");
```

 In diesem Schritt rufen Sie die`LocaleId` des Standardschriftstils und vergleichen Sie ihn mit dem`EditingLanguage.Russian` Kennung. Die Ausgabenachricht gibt an, ob die Standardsprache auf Russisch eingestellt ist oder nicht.

## Abschluss

 Das Festlegen von Russisch als Standardbearbeitungssprache in einem Word-Dokument mit Aspose.Words für .NET ist mit den richtigen Schritten unkompliziert. Durch die Konfiguration`LoadOptions`Laden des Dokuments und Überprüfen der Spracheinstellungen können Sie sicherstellen, dass Ihr Dokument den sprachlichen Anforderungen Ihres Publikums entspricht. 

Dieses Handbuch bietet einen klaren und detaillierten Prozess, der Ihnen dabei hilft, diese Anpassung effizient durchzuführen.

## FAQs

### Was ist Aspose.Words für .NET?

Aspose.Words für .NET ist eine leistungsstarke Bibliothek für die programmgesteuerte Arbeit mit Word-Dokumenten innerhalb von .NET-Anwendungen. Sie ermöglicht die Erstellung, Bearbeitung und Konvertierung von Dokumenten.

### Wie lade ich Aspose.Words für .NET herunter?

 Sie können Aspose.Words für .NET herunterladen von der[Aspose-Veröffentlichungen](https://releases.aspose.com/words/net/) Seite.

###  Was ist`LoadOptions` used for?

`LoadOptions` wird verwendet, um verschiedene Optionen zum Laden eines Dokuments anzugeben, beispielsweise zum Festlegen der Standardbearbeitungssprache.

### Kann ich andere Sprachen als Standardbearbeitungssprache festlegen?

 Ja, Sie können jede von Aspose.Words unterstützte Sprache einstellen, indem Sie die entsprechende`EditingLanguage` Wert auf`DefaultEditingLanguage`.

### Wie kann ich Support für Aspose.Words für .NET erhalten?

 Unterstützung erhalten Sie vom[Aspose-Unterstützung](https://forum.aspose.com/c/words/8) Forum, wo Sie Fragen stellen und Hilfe von der Community und den Aspose-Entwicklern erhalten können.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
