---
category: general
date: 2026-03-22
description: Erstellen Sie ein Rechteck‑Shape in C# und fügen Sie dem Shape mit Aspose.Words
  einen Schatten hinzu. Erfahren Sie, wie man einen Schatten hinzufügt, ein Rechteck
  erstellt und Schatteneigenschaften festlegt.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: de
og_description: Erstellen Sie ein Rechteck‑Shape in C# und fügen Sie dem Shape mit
  Aspose.Words einen Schatten hinzu. Schritt‑für‑Schritt‑Anleitung, die erklärt, wie
  man einen Schatten hinzufügt, ein Rechteck erstellt und den Schatten einstellt.
og_title: Rechteckform mit Schatten in C# erstellen – Vollständige Anleitung
tags:
- Aspose.Words
- C#
- Document Automation
title: Rechteckform mit Schatten in C# mit Aspose.Words erstellen
url: /de/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform mit Schatten in C# mit Aspose.Words erstellen

Haben Sie jemals **eine Rechteckform** in einem Word‑Dokument erstellen wollen, waren sich aber nicht sicher, wie Sie ihr einen dezenten Drop‑Shadow geben? Sie sind nicht allein – viele Entwickler stoßen auf dieses Problem, wenn sie das erste Mal mit Dokumenten‑Automatisierung experimentieren. In diesem Leitfaden zeigen wir Ihnen Schritt für Schritt, wie Sie **einem Shape einen Schatten hinzufügen** mit Aspose.Words, und wir beantworten dabei „**how to add shadow**“, „**how to create rectangle**“ und „**how to set shadow**“.

Wir beginnen mit einem leeren `Document`, zeichnen ein Rechteck, aktivieren dessen Schatten, passen Unschärfe, Abstand, Winkel und Farbe an und speichern schließlich die Datei. Am Ende haben Sie eine einsatzbereite `.docx`, die ein grau getöntes Rechteck zeigt, das leicht über der Seite schwebt. Keine Geheimnisse, nur klarer Code, den Sie in jedes .NET‑Projekt kopieren‑und‑einfügen können.

## Voraussetzungen

Bevor wir loslegen, stellen Sie sicher, dass Sie Folgendes haben:

* **Aspose.Words for .NET** (die neueste Version ab März 2026). Sie können es über NuGet mit `Install-Package Aspose.Words` beziehen.
* Eine .NET‑Entwicklungsumgebung – Visual Studio, Rider oder sogar VS Code mit der C#‑Erweiterung funktionieren einwandfrei.
* Grundkenntnisse in C# – nichts Aufwändiges, nur die Fähigkeit, eine Konsolen‑ oder WinForms‑App zu erstellen.

Das war’s. Keine zusätzlichen Bibliotheken, keine versteckten Schritte. Bereit? Dann legen wir los.

## Schritt 1: Ein neues leeres Dokument initialisieren

Um **eine Rechteckform zu erstellen**, benötigen wir zuerst einen Container – ein `Document`‑Objekt –, das die Word‑Datei repräsentiert.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

Die `Document`‑Klasse ist der Einstiegspunkt für alles, was Aspose.Words leistet. Denken Sie an sie als leere Leinwand; ohne sie können Sie keine Shapes, Tabellen oder Texte hinzufügen.

## Schritt 2: Das Rechteck erstellen, das den Schatten tragen wird

Jetzt zeigen wir **how to create rectangle**, indem wir ein `Shape` vom Typ `Rectangle` instanziieren. Wir setzen außerdem seine Größe in Punkten (1 Punkt ≈ 1/72 Zoll).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Warum 200 × 100 Punkte? Das ist eine gute Größe für eine Demo – groß genug, um den Schatten klar zu sehen, aber nicht so riesig, dass es die Seite dominiert. Passen Sie die Werte gern an Ihr Layout an.

## Schritt 3: Schatten aktivieren und das Aussehen konfigurieren

Hier kommt das Herzstück des Tutorials: **how to add shadow** und **how to set shadow**‑Eigenschaften. Aspose.Words stellt jedem Shape ein `Shadow`‑Objekt zur Verfügung, mit dem Sie den Effekt ein‑ bzw. ausschalten und visuelle Parameter anpassen können.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** mildert die Kanten – ein höherer Wert lässt den Schatten diffuser wirken.
* **Distance** verschiebt den Schatten weiter vom Rechteck weg.
* **Angle** bestimmt, aus welcher Richtung das Licht zu kommen scheint; 45° erzeugt einen diagonalen, natürlichen Look.
* **Color** lässt Sie jede `System.Drawing.Color` wählen. Grau ist ein sicherer Standard, aber Sie können auch mutig `Color.Black` oder dezent `Color.LightGray` verwenden.

Pro‑Tipp: Wenn Sie `Enabled = false` setzen, werden alle anderen Schatten‑Einstellungen ignoriert – prüfen Sie also immer dieses Flag.

## Schritt 4: Das Shape in den Dokumentenkörper einfügen

Nachdem das Rechteck fertig und sein Schatten konfiguriert ist, müssen wir es ins Dokument einfügen. Der einfachste Weg ist, es an den ersten Absatz der ersten Section anzuhängen.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Enthält Ihr Dokument bereits Text, können Sie ein bestimmtes `Paragraph` oder sogar eine `Table`‑Zelle suchen und das Shape dort einfügen. Die Methode `AppendChild` ist vielseitig – sie funktioniert mit jedem `Node`‑Typ.

## Schritt 5: Das Dokument speichern und das Ergebnis prüfen

Zum Schluss schreiben wir die Datei auf die Festplatte. Ändern Sie den Pfad nach Belieben; der Ordner muss existieren, sonst erhalten Sie eine Ausnahme.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Öffnen Sie das resultierende `ShadowedRectangle.docx` in Microsoft Word (oder LibreOffice) und Sie sollten ein graues Rechteck mit einem klaren, diagonalen Schatten sehen, der nach unten‑rechts verläuft. Wenn der Schatten zu schwach wirkt, erhöhen Sie `BlurRadius` oder `Distance` und führen Sie den Code erneut aus – Experimentieren gehört zum Spaß dazu.

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Beispiel für Rechteckform mit Schatten"}

### Erwartete Ausgabe

* Ein einseitiges Word‑Dokument.
* Ein graues Rechteck von 200 × 100 Punkten, oben‑links auf der Seite positioniert.
* Ein subtiler grauer Schatten, um 8 Pixel versetzt bei einem Winkel von 45°, unscharf gestellt um 5 Pixel.

## Wie man einem Shape Schatten hinzufügt – tieferer Einblick

Vielleicht fragen Sie sich: *„Kann ich den Schatten animieren oder ihn basierend auf Benutzereingaben ändern?“* Während Aspose.Words selbst keine Animationen unterstützt, können Sie die Schatten‑Eigenschaften programmatisch vor dem Speichern anpassen und so mehrere Versionen desselben Dokuments mit unterschiedlichen Looks erzeugen. Zum Beispiel, indem Sie über eine Sammlung von Farben iterieren:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Dieses kleine Snippet demonstriert **how to set shadow** dynamisch – ideal für die Erstellung thematischer Berichte.

## Wie man ein Rechteck erstellt – alternative Shapes

Falls Sie ein abgerundetes Rechteck benötigen, wechseln Sie einfach den `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Oder für ein perfektes Quadrat setzen Sie `Width` gleich `Height`. Die gleichen Schatten‑Eigenschaften gelten, sodass Sie bereits für **how to add shadow** bei jeder gewünschten Form abgedeckt sind.

## Häufige Stolperfallen und Fehlersuche

| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| Schatten erscheint nicht | `Shadow.Enabled` bleibt `false` | `rectangleShape.Shadow.Enabled = true;` setzen |
| Schatten wirkt zu scharf | `BlurRadius` ist 0 | `BlurRadius` auf mindestens 3 erhöhen |
| Beim Speichern wird `FileNotFoundException` geworfen | Zielordner existiert nicht | Ordner zuerst erstellen oder einen gültigen Pfad verwenden |
| Shape ist unsichtbar | Breite/Höhe ist 0 | Sicherstellen, dass beide Dimensionen > 0 sind |

Auf diese Punkte zu achten, spart Ihnen das klassische „Warum wird mein Shape nicht angezeigt?“-Problem.

## Zusammenfassung – Was wir erreicht haben

* **Create rectangle shape** in einem neuen Word‑Dokument mit Aspose.Words.  
* **Add shadow to shape** durch Setzen von `Shadow.Enabled` und Anpassen von Blur, Distance, Angle und Color.  
* Demonstriert **how to add shadow**, **how to create rectangle** und **how to set shadow** in einem sauberen, wiederverwendbaren Code‑Snippet.  
* Ein vollständiges, sofort lauffähiges Beispiel, das Sie in jedes C#‑Projekt einfügen können.

## Was kommt als Nächstes?

Jetzt, wo Sie die Grundlagen beherrschen, können Sie Folgendes erkunden:

* **How to add shadow to images** – dieselbe `Shadow`‑API funktioniert für `ShapeType.Image`.
* **Kombination mehrerer Shapes** – erstellen Sie Flussdiagramme oder Infografiken direkt in Word.
* **Export nach PDF** – rufen Sie `document.Save("output.pdf")` nach dem Hinzufügen der Schatten auf, um eine druckbare Version zu erhalten.

Experimentieren Sie gern mit verschiedenen Farben, Winkeln oder sogar Farbverläufen. Die API ist flexibel genug, um professionelle Dokumente zu erstellen, ohne Word manuell öffnen zu müssen.

---

Viel Spaß beim Coden! Wenn Sie auf Probleme stoßen, hinterlassen Sie einen Kommentar unten oder besuchen Sie die Aspose.Words‑Foren – die Community hilft schnell.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}