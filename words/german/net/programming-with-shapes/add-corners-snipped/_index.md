---
title: Abgeschnittene Ecken hinzufügen
linktitle: Abgeschnittene Ecken hinzufügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Ihren Word-Dokumenten eine Form mit abgeschnittenen Ecken hinzufügen. Diese Schritt-für-Schritt-Anleitung stellt sicher, dass Sie Ihre Dokumente problemlos verbessern können.
weight: 10
url: /de/net/programming-with-shapes/add-corners-snipped/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Abgeschnittene Ecken hinzufügen

## Einführung

Das Hinzufügen benutzerdefinierter Formen zu Ihren Word-Dokumenten kann eine unterhaltsame und optisch ansprechende Möglichkeit sein, wichtige Informationen hervorzuheben oder Ihren Inhalten etwas Flair zu verleihen. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET „Corners Snipped“-Formen in Ihre Word-Dokumente einfügen können. Diese Anleitung führt Sie durch jeden Schritt und stellt sicher, dass Sie diese Formen mühelos hinzufügen und Ihre Dokumente wie ein Profi anpassen können.

## Voraussetzungen

Bevor wir uns in den Code stürzen, stellen wir sicher, dass Sie alles haben, was Sie zum Starten brauchen:

1.  Aspose.Words für .NET: Wenn Sie es noch nicht getan haben, laden Sie die neueste Version von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Richten Sie Ihre Entwicklungsumgebung ein. Visual Studio ist eine beliebte Wahl, Sie können jedoch jede IDE verwenden, die .NET unterstützt.
3.  Lizenz: Wenn Sie nur experimentieren, können Sie eine[Kostenlose Testversion](https://releases.aspose.com/) oder erhalten Sie eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) um die volle Funktionalität freizuschalten.
4. Grundlegende Kenntnisse in C#: Wenn Sie mit der C#-Programmierung vertraut sind, können Sie den Beispielen leichter folgen.

## Namespaces importieren

Bevor wir mit Aspose.Words für .NET arbeiten können, müssen wir die erforderlichen Namespaces importieren. Fügen Sie diese oben in Ihrer C#-Datei hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Lassen Sie uns nun den Vorgang des Hinzufügens einer Form mit abgeschnittenen Ecken in mehrere Schritte unterteilen. Befolgen Sie diese Schritte genau, um sicherzustellen, dass alles reibungslos funktioniert.

## Schritt 1: Initialisieren Sie das Dokument und den DocumentBuilder

 Als erstes müssen wir ein neues Dokument erstellen und ein`DocumentBuilder` Objekt. Dieser Builder hilft uns, unserem Dokument Inhalt hinzuzufügen.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 In diesem Schritt haben wir unser Dokument und unseren Builder eingerichtet. Denken Sie an die`DocumentBuilder` als Ihr digitaler Stift, bereit zum Schreiben und Zeichnen in Ihrem Word-Dokument.

## Schritt 2: Fügen Sie die abgeschnittene Form für die Ecken ein

 Als nächstes verwenden wir die`DocumentBuilder` um eine Form mit abgeschnittenen Ecken einzufügen. Dieser Formtyp ist in Aspose.Words vordefiniert und kann einfach mit einer einzigen Codezeile eingefügt werden.

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

Hier geben wir den Formtyp und seine Abmessungen (50 x 50) an. Stellen Sie sich vor, Sie kleben einen kleinen, perfekt zugeschnittenen Eckaufkleber auf Ihr Dokument. 

## Schritt 3: Definieren Sie Speicheroptionen mit Compliance

Bevor wir unser Dokument speichern, müssen wir die Speicheroptionen definieren, um sicherzustellen, dass unser Dokument bestimmten Standards entspricht. Wir verwenden die`OoxmlSaveOptions` Klasse dafür.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

Diese Speicheroptionen stellen sicher, dass unser Dokument dem Standard ISO/IEC 29500:2008 entspricht, was für die Kompatibilität und Langlebigkeit des Dokuments von entscheidender Bedeutung ist.

## Schritt 4: Speichern Sie das Dokument

Abschließend speichern wir unser Dokument mit den zuvor definierten Speicheroptionen im angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

Und schon enthält Ihr Dokument eine benutzerdefinierte Form „Abgeschnittene Ecken“, die mit den erforderlichen Kompatibilitätsoptionen gespeichert wurde.

## Abschluss

Da haben Sie es! Das Hinzufügen benutzerdefinierter Formen zu Ihren Word-Dokumenten mit Aspose.Words für .NET ist unkompliziert und kann die visuelle Attraktivität Ihrer Dokumente erheblich steigern. Indem Sie diese Schritte befolgen, können Sie ganz einfach eine Form mit abgeschnittenen Ecken einfügen und sicherstellen, dass Ihr Dokument den erforderlichen Standards entspricht. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Kann ich die Größe der Form „Abgeschnittene Ecken“ anpassen?
Ja, Sie können die Größe anpassen, indem Sie die Abmessungen im`InsertShape` Verfahren.

### Ist es möglich, andere Arten von Formen hinzuzufügen?
 Absolut! Aspose.Words unterstützt verschiedene Formen. Ändern Sie einfach die`ShapeType` in die gewünschte Form.

### Benötige ich eine Lizenz, um Aspose.Words zu verwenden?
Sie können zwar eine kostenlose Testversion oder eine temporäre Lizenz verwenden, für die uneingeschränkte Nutzung ist jedoch eine Volllizenz erforderlich.

### Wie kann ich die Formen noch weiter stylen?
Sie können zusätzliche Eigenschaften und Methoden von Aspose.Words verwenden, um das Erscheinungsbild und Verhalten von Formen anzupassen.

### Ist Aspose.Words mit anderen Formaten kompatibel?
Ja, Aspose.Words unterstützt mehrere Dokumentformate, darunter DOCX, PDF, HTML und mehr.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
