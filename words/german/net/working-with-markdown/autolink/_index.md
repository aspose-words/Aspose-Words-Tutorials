---
title: Autolink
linktitle: Autolink
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser ausführlichen Anleitung, wie Sie mit Aspose.Words für .NET Hyperlinks in Word-Dokumente einfügen und anpassen. Verbessern Sie Ihre Dokumente mühelos.
weight: 10
url: /de/net/working-with-markdown/autolink/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Autolink

## Einführung

Um ein ansprechendes, professionelles Dokument zu erstellen, müssen Sie häufig Hyperlinks effektiv einfügen und verwalten können. Egal, ob Sie Links zu Websites, E-Mail-Adressen oder anderen Dokumenten hinzufügen möchten, Aspose.Words für .NET bietet Ihnen eine Reihe robuster Tools, die Ihnen dabei helfen. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET Hyperlinks in Word-Dokumente einfügen und anpassen können. Dabei wird jeder Schritt aufgeschlüsselt, um den Vorgang unkompliziert und leicht zugänglich zu machen.

## Voraussetzungen

Bevor wir uns in die einzelnen Schritte stürzen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

-  Aspose.Words für .NET: Laden Sie die neueste Version herunter und installieren Sie sie von[Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Eine IDE wie Visual Studio.
- .NET Framework: Stellen Sie sicher, dass Sie die entsprechende Version installiert haben.
- Grundkenntnisse in C#: Kenntnisse in der C#-Programmierung sind hilfreich.

## Namespaces importieren

Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importieren. So können Sie nahtlos auf die Funktionen von Aspose.Words zugreifen.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Einrichten Ihres Projekts

Richten Sie zunächst Ihr Projekt in Visual Studio ein. Öffnen Sie Visual Studio und erstellen Sie eine neue Konsolenanwendung. Geben Sie ihr einen relevanten Namen, z. B. „HyperlinkDemo“.

## Schritt 2: Dokument und DocumentBuilder initialisieren

Als nächstes initialisieren Sie ein neues Dokument und ein DocumentBuilder-Objekt. Der DocumentBuilder ist ein praktisches Tool, mit dem Sie verschiedene Elemente in Ihr Word-Dokument einfügen können.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Schritt 3: Einfügen eines Hyperlinks zu einer Website

 Um einen Hyperlink zu einer Website einzufügen, verwenden Sie das`InsertHyperlink` Methode. Sie müssen den Anzeigetext, die URL und einen Booleschen Wert angeben, der angibt, ob der Link als Hyperlink angezeigt werden soll.

```csharp
// Fügen Sie einen Hyperlink zu einer Website ein.
builder.InsertHyperlink("Aspose Website", "https://www.aspose.com", false);
```

Dadurch wird ein anklickbarer Link mit dem Text „Aspose-Website“ eingefügt, der zur Aspose-Startseite weiterleitet.

## Schritt 4: Einfügen eines Hyperlinks zu einer E-Mail-Adresse

 Genauso einfach ist es, einen Link zu einer E-Mail-Adresse einzufügen. Verwenden Sie`InsertHyperlink` Methode, aber mit einem „mailto:“-Präfix in der URL.

```csharp
// Fügen Sie einen Hyperlink zu einer E-Mail-Adresse ein.
builder.InsertHyperlink("Contact Support", "mailto:support@aspose.com", false);
```

 Klicken Sie nun auf "Support kontaktieren". Der Standard-E-Mail-Client wird mit einer neuen E-Mail an`support@aspose.com`.

## Schritt 5: Anpassen des Hyperlink-Erscheinungsbilds

Hyperlinks können an den Stil Ihres Dokuments angepasst werden. Sie können die Schriftfarbe, -größe und andere Attribute mithilfe der`Font` Eigenschaft des DocumentBuilder.

```csharp
builder.Font.Style = doc.Styles[StyleIdentifier.Hyperlink];
builder.InsertHyperlink("Aspose Website", "http://www.aspose.com", false);
```

Dieser Codeausschnitt fügt einen blauen, unterstrichenen Hyperlink ein, der ihn in Ihrem Dokument hervorhebt.

## Abschluss

Das Einfügen und Anpassen von Hyperlinks in Word-Dokumente mit Aspose.Words für .NET ist ein Kinderspiel, wenn Sie die Schritte kennen. Wenn Sie dieser Anleitung folgen, können Sie Ihre Dokumente mit nützlichen Links erweitern und sie interaktiver und professioneller gestalten. Ob es um das Verlinken auf Websites, E-Mail-Adressen oder das Anpassen des Erscheinungsbilds geht, Aspose.Words bietet alle Tools, die Sie benötigen.

## Häufig gestellte Fragen

### Kann ich Hyperlinks zu anderen Dokumenten einfügen?
Ja, Sie können Hyperlinks zu anderen Dokumenten einfügen, indem Sie den Dateipfad als URL angeben.

### Wie entferne ich einen Hyperlink?
 Sie können einen Hyperlink entfernen, indem Sie das`Remove` Methode auf dem Hyperlink-Knoten.

### Kann ich Hyperlinks Tooltips hinzufügen?
 Ja, Sie können Tooltips hinzufügen, indem Sie`ScreenTip`Eigenschaft des Hyperlinks.

### Ist es möglich, Hyperlinks im gesamten Dokument unterschiedlich zu formatieren?
 Ja, Sie können Hyperlinks unterschiedlich formatieren, indem Sie die`Font` Eigenschaften vor dem Einfügen jedes Hyperlinks.

### Wie kann ich einen vorhandenen Hyperlink aktualisieren oder ändern?
Sie können einen vorhandenen Hyperlink aktualisieren, indem Sie über die Dokumentknoten darauf zugreifen und seine Eigenschaften ändern.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
