---
title: Vertikaler Anker
linktitle: Vertikaler Anker
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET vertikale Ankerpositionen für Textfelder in Word-Dokumenten festlegen. Einfache Schritt-für-Schritt-Anleitung enthalten.
weight: 10
url: /de/net/programming-with-shapes/vertical-anchor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vertikaler Anker

## Einführung

Mussten Sie schon einmal genau steuern, wo Text in einem Textfeld in einem Word-Dokument angezeigt wird? Vielleicht möchten Sie, dass Ihr Text oben, in der Mitte oder unten im Textfeld verankert wird? Wenn ja, sind Sie hier richtig! In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET den vertikalen Anker von Textfeldern in Word-Dokumenten festlegen. Stellen Sie sich die vertikale Verankerung als Zauberstab vor, der Ihren Text genau dort positioniert, wo Sie ihn in seinem Container haben möchten. Bereit, loszulegen? Dann legen wir los!

## Voraussetzungen

Bevor wir uns mit den Einzelheiten der vertikalen Verankerung befassen, müssen Sie einige Dinge vorbereitet haben:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek Aspose.Words für .NET installiert haben. Wenn Sie sie noch nicht haben, können Sie[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Visual Studio: Dieses Tutorial setzt voraus, dass Sie Visual Studio oder eine andere .NET-IDE zum Codieren verwenden.
3. Grundkenntnisse in C#: Wenn Sie mit C# und .NET vertraut sind, können Sie problemlos mitmachen.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihren C#-Code importieren. Hier teilen Sie Ihrer Anwendung mit, wo sie die Klassen und Methoden finden kann, die Sie verwenden möchten. So geht's:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Diese Namespaces stellen die Klassen bereit, die Sie zum Arbeiten mit Dokumenten und Formen benötigen.

## Schritt 1: Initialisieren Sie das Dokument

Als Erstes müssen Sie ein neues Word-Dokument erstellen. Stellen Sie sich das so vor, als würden Sie Ihre Leinwand einrichten, bevor Sie mit dem Malen beginnen.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Hier,`Document` ist Ihre leere Leinwand und`DocumentBuilder` ist Ihr Pinsel, mit dem Sie Formen und Text hinzufügen können.

## Schritt 2: Einfügen einer TextBox-Form

Fügen wir nun unserem Dokument ein Textfeld hinzu. Hier wird Ihr Text gespeichert. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

 In diesem Beispiel`ShapeType.TextBox` gibt die gewünschte Form an und`200, 200` sind die Breite und Höhe des Textfelds in Punkten.

## Schritt 3: Den vertikalen Anker setzen

Und hier geschieht die Magie! Sie können die vertikale Ausrichtung des Textes innerhalb des Textfelds festlegen. Dadurch wird bestimmt, ob der Text oben, in der Mitte oder unten im Textfeld verankert wird.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

 In diesem Fall,`TextBoxAnchor.Bottom`sorgt dafür, dass der Text am unteren Rand des Textfelds verankert wird. Wenn Sie ihn zentriert oder oben ausgerichtet haben möchten, verwenden Sie`TextBoxAnchor.Center` oder`TextBoxAnchor.Top`, jeweils.

## Schritt 4: Text zum Textfeld hinzufügen

Jetzt ist es an der Zeit, Ihrem Textfeld Inhalt hinzuzufügen. Betrachten Sie es als das Ausfüllen Ihrer Leinwand mit den letzten Feinheiten.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

 Hier,`MoveTo` sorgt dafür, dass der Text in das Textfeld eingefügt wird, und`Write` fügt den eigentlichen Text hinzu.

## Schritt 5: Speichern Sie das Dokument

Der letzte Schritt besteht darin, Ihr Dokument zu speichern. Das ist, als würde man sein fertiges Gemälde in einen Rahmen stecken.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Abschluss

Und da haben Sie es! Sie haben gerade gelernt, wie Sie die vertikale Ausrichtung von Text in einem Textfeld in einem Word-Dokument mit Aspose.Words für .NET steuern. Egal, ob Sie Text oben, in der Mitte oder unten verankern, diese Funktion gibt Ihnen präzise Kontrolle über das Layout Ihres Dokuments. Wenn Sie also das nächste Mal die Textplatzierung Ihres Dokuments optimieren müssen, wissen Sie genau, was zu tun ist!

## Häufig gestellte Fragen

### Was ist vertikale Verankerung in einem Word-Dokument?
Die vertikale Verankerung steuert die Position des Textes innerhalb eines Textfelds, beispielsweise die Ausrichtung oben, mittig oder unten.

### Kann ich außer Textfeldern auch andere Formen verwenden?
Ja, Sie können die vertikale Verankerung mit anderen Formen verwenden, der häufigste Anwendungsfall sind jedoch Textfelder.

### Wie ändere ich den Ankerpunkt, nachdem ich das Textfeld erstellt habe?
 Sie können den Ankerpunkt ändern, indem Sie den`VerticalAnchor` -Eigenschaft des Textfeld-Formobjekts.

### Ist es möglich, Text in der Mitte des Textfelds zu verankern?
 Absolut! Verwenden Sie einfach`TextBoxAnchor.Center` um den Text vertikal im Textfeld zu zentrieren.

### Wo finde ich weitere Informationen zu Aspose.Words für .NET?
 Schauen Sie sich die[Aspose.Words-Dokumentation](https://reference.aspose.com/words/net/) für weitere Details und Anleitungen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
