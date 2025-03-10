---
title: Seitenverhältnis gesperrt
linktitle: Seitenverhältnis gesperrt
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie das Seitenverhältnis von Formen in Word-Dokumenten mit Aspose.Words für .NET sperren. Folgen Sie dieser Schritt-für-Schritt-Anleitung, um die Proportionen Ihrer Bilder und Formen beizubehalten.
weight: 10
url: /de/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Seitenverhältnis gesperrt

## Einführung

Haben Sie sich schon einmal gefragt, wie Sie die perfekten Proportionen von Bildern und Formen in Ihren Word-Dokumenten beibehalten können? Manchmal müssen Sie sicherstellen, dass Ihre Bilder und Formen bei Größenänderungen nicht verzerrt werden. Hier ist es praktisch, das Seitenverhältnis zu sperren. In diesem Tutorial erfahren Sie, wie Sie das Seitenverhältnis für Formen in Word-Dokumenten mit Aspose.Words für .NET festlegen. Wir unterteilen es in leicht verständliche Schritte, damit Sie diese Fähigkeiten sicher auf Ihre Projekte anwenden können.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, gehen wir noch einmal durch, was Sie für den Einstieg benötigen:

- Aspose.Words für .NET-Bibliothek: Sie müssen Aspose.Words für .NET installiert haben. Wenn Sie dies noch nicht getan haben, können Sie[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Stellen Sie sicher, dass Sie eine .NET-Entwicklungsumgebung eingerichtet haben. Visual Studio ist eine beliebte Wahl.
- Grundkenntnisse in C#: Einige Kenntnisse der C#-Programmierung sind hilfreich.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces. Diese Namespaces geben uns Zugriff auf die Klassen und Methoden, die wir zum Arbeiten mit Word-Dokumenten und -Formen benötigen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

 Bevor wir mit der Bearbeitung von Formen beginnen, müssen wir ein Verzeichnis einrichten, in dem unsere Dokumente gespeichert werden. Der Einfachheit halber verwenden wir einen Platzhalter`YOUR DOCUMENT DIRECTORY`. Ersetzen Sie dies durch den tatsächlichen Pfad zu Ihrem Dokumentverzeichnis.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Neues Dokument erstellen

Als Nächstes erstellen wir mit Aspose.Words ein neues Word-Dokument. Dieses Dokument dient uns als Leinwand zum Hinzufügen von Formen und Bildern.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Hier erstellen wir eine Instanz des`Document` Klasse und verwenden Sie eine`DocumentBuilder` um uns beim Erstellen des Dokumentinhalts zu helfen.

## Schritt 3: Ein Bild einfügen

 Fügen wir nun ein Bild in unser Dokument ein. Wir verwenden das`InsertImage` Methode der`DocumentBuilder`Klasse. Stellen Sie sicher, dass Sie ein Bild in Ihrem angegebenen Verzeichnis haben.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

 Ersetzen`dataDir + "Transparent background logo.png"` durch den Pfad zu Ihrer Bilddatei.

## Schritt 4: Seitenverhältnis sperren

Sobald das Bild eingefügt ist, können wir sein Seitenverhältnis sperren. Durch das Sperren des Seitenverhältnisses wird sichergestellt, dass die Proportionen des Bildes beim Ändern der Größe konstant bleiben.

```csharp
shape.AspectRatioLocked = true;
```

 Einstellung`AspectRatioLocked` Zu`true` stellt sicher, dass das Bild sein ursprüngliches Seitenverhältnis beibehält.

## Schritt 5: Speichern Sie das Dokument

Zum Schluss speichern wir das Dokument im angegebenen Verzeichnis. Dabei werden alle Änderungen, die wir vorgenommen haben, in die Dokumentdatei geschrieben.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Abschluss

Herzlichen Glückwunsch! Sie haben erfolgreich gelernt, wie Sie das Seitenverhältnis für Formen in Word-Dokumenten mit Aspose.Words für .NET festlegen. Indem Sie diese Schritte befolgen, können Sie sicherstellen, dass Ihre Bilder und Formen ihre Proportionen beibehalten, sodass Ihre Dokumente professionell und elegant aussehen. Experimentieren Sie ruhig mit verschiedenen Bildern und Formen, um zu sehen, wie die Funktion zum Sperren des Seitenverhältnisses in verschiedenen Szenarien funktioniert.

## Häufig gestellte Fragen

### Kann ich das Seitenverhältnis nach der Sperrung entsperren?
Ja, Sie können das Seitenverhältnis entsperren, indem Sie`shape.AspectRatioLocked = false`.

### Was passiert, wenn ich die Größe eines Bildes mit einem gesperrten Seitenverhältnis ändere?
Die Größe des Bildes wird proportional angepasst, wobei das ursprüngliche Breite-Höhe-Verhältnis erhalten bleibt.

### Kann ich dies außer auf Bilder auch auf andere Formen anwenden?
Auf jeden Fall! Die Funktion zum Sperren des Seitenverhältnisses kann auf jede beliebige Form angewendet werden, einschließlich Rechtecke, Kreise und mehr.

### Ist Aspose.Words für .NET mit .NET Core kompatibel?
Ja, Aspose.Words für .NET unterstützt sowohl .NET Framework als auch .NET Core.

### Wo finde ich weitere Dokumentation zu Aspose.Words für .NET?
 Eine ausführliche Dokumentation finden Sie[Hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
