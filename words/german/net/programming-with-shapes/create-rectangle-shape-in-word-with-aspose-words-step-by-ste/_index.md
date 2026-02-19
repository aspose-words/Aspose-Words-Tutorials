---
category: general
date: 2026-02-18
description: Erstellen Sie eine Rechteckform mit Aspose.Words und lernen Sie, wie
  Sie einen Schatten hinzufügen, die Formgröße festlegen und das Word‑Dokument in
  wenigen Minuten speichern.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: de
og_description: Erstellen Sie eine Rechteckform in einer Word‑Datei, lernen Sie, wie
  Sie einen Schatten hinzufügen, die Formgröße festlegen und das Dokument mit Aspose.Words
  in C# speichern.
og_title: Rechteckform in Word erstellen – Vollständiges Aspose.Words‑Tutorial
tags:
- Aspose.Words
- C#
- Word automation
title: Rechteckform in Word mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

produce final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Word mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung

Haben Sie jemals **eine Rechteckform** in einer Word‑Datei erstellen müssen, wussten aber nicht, wo Sie anfangen sollen? Sie sind nicht allein – Entwickler fragen oft: „Wie füge ich einer Form einen Schatten hinzu und halte das Dokument trotzdem editierbar?“ In diesem Tutorial beantworten wir das und zeigen Ihnen außerdem **wie man einen Schatten hinzufügt**, **die Formgröße festlegt** und **das Word‑Dokument speichert**, alles in einem reibungslosen Ablauf.

Wir führen Sie durch alles, was Sie benötigen, von der Initialisierung eines neuen Dokuments (ja, das ist der erste Schritt zu **how to create document**) bis zum Speichern der finalen *.docx* auf der Festplatte. Keine externen Referenzen, nur ein eigenständiges Beispiel, das Sie in Visual Studio kopieren‑und‑einfügen und sofort ausführen können.

---

## Voraussetzungen

- .NET 6+ (oder .NET Framework 4.7+). Aspose.Words funktioniert mit jeder aktuellen .NET‑Runtime.
- Eine gültige Aspose.Words‑Lizenz (oder der kostenlose Evaluierungsschlüssel) – andernfalls sehen Sie ein Wasserzeichen.
- Visual Studio, Rider oder ein beliebiger C#‑Editor Ihrer Wahl.
- Grundkenntnisse in C# – nichts Aufwändiges, nur die Fähigkeit, eine Konsolen‑App auszuführen.

> **Pro‑Tipp:** Wenn Sie einen Mac benutzen, läuft derselbe Code unter .NET 6 mit VS Code – stellen Sie nur sicher, dass Sie das NuGet‑Paket `Aspose.Words` referenzieren.

## Schritt 1: Dokument initialisieren – die Grundlage von **how to create document**

Bevor wir etwas zeichnen können, benötigen wir eine leere Leinwand. Aspose.Words nennt dies ein `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Warum das wichtig ist:** Das `Document`‑Objekt repräsentiert die gesamte *.docx*-Datei. Alle Formen, Absätze und Abschnitte, die Sie hinzufügen, werden Kinder dieses Objekts. Mit einem leeren Dokument zu beginnen stellt sicher, dass keine versteckten Stile Ihre Rechteckform beeinträchtigen.

## Schritt 2: Das Rechteck definieren und **Formgröße festlegen**

Ein Rechteck ist einfach ein `Shape` mit `ShapeType.Rectangle`. Wir geben ihm explizite Abmessungen, damit es genau wie beabsichtigt aussieht.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **Was die Zahlen bedeuten:** Aspose.Words verwendet Punkte (1 pt = 1/72 in). Passen Sie die Werte an Ihr Layout an; für eine typische A4‑Seite ist 200 pt eine angenehme Breite.

## Schritt 3: **Wie man einen Schatten hinzufügt** – die Form hervorheben

Schatten geben einen visuellen Hinweis darauf, dass die Form „vom Blatt gehoben“ ist. Die `Shadow`‑Eigenschaft ermöglicht das Anpassen von Farbe, Abstand, Transparenz und Unschärfe.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Warum Transparenz verwenden?** Ein vollständig undurchsichtiger Schatten kann hart wirken. Auf 0,4 zu setzen macht den Effekt dezent und professionell.

## Schritt 4: Das Rechteck positionieren – Inline‑Fluss mit umgebendem Text

Wenn Sie möchten, dass sich die Form wie ein Zeichen in einem Absatz verhält, setzen Sie ihr `WrapType` auf `Inline`. Das sorgt für ein vorhersehbares Layout, besonders wenn das Dokument später bearbeitet wird.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Randfall:** Wenn das Rechteck über Text schweben soll (z. B. ein Wasserzeichen), ändern Sie `WrapType` zu `Square` oder `BehindText`.

## Schritt 5: Die Form in den Dokumentenkörper einfügen

Jetzt platzieren wir das Rechteck tatsächlich in den ersten Absatz. Wenn das Dokument noch keinen Inhalt hat, wird `FirstParagraph` automatisch erstellt.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Tipp:** Sie können auch zuerst einen neuen Absatz erstellen und dann die Form anhängen – nützlich, wenn Sie umgebenden Text benötigen.

## Schritt 6: **Word‑Dokument speichern** – der letzte Schritt

Wenn alles bereit ist, ist das Speichern der Datei ein Einzeiler. Wählen Sie einen beliebigen Pfad; das Beispiel verwendet einen Platzhalter, den Sie durch Ihr eigenes Verzeichnis ersetzen sollten.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Ergebnis:** Öffnen Sie die erzeugte *.docx* in Microsoft Word. Sie sehen ein schwarz‑schattiertes Rechteck, 200 pt breit und 100 pt hoch, das inline mit dem ersten Absatz sitzt.

## Erwartete Ausgabe

Wenn Sie **ShadowShape.docx** öffnen, zeigt das Dokument:

- Ein einzelner Absatz, der eine rechteckige Form enthält.
- Das Rechteck hat einen dezenten schwarzen Schatten, der um 5 pt versetzt ist.
- Die Formgröße entspricht den in Schritt 2 festgelegten Abmessungen.
- Kein zusätzlicher Text erscheint, es sei denn, Sie fügen ihn manuell hinzu.

Wenn die Form nicht erscheint, überprüfen Sie, ob Sie die korrekte Aspose.Words‑Version referenziert haben und ob Ihre Lizenz (oder Testversion) aktiv ist.

## Häufige Fragen & Variationen

| Frage | Antwort |
|----------|--------|
| *Kann ich die Schattenfarbe zu etwas anderem als Schwarz ändern?* | Absolut—setzen Sie `rectangleShape.Shadow.Color = Color.Blue;` oder irgendeine `System.Drawing.Color`. |
| *Was, wenn ich ein größeres Rechteck brauche?* | Passen Sie die Werte `Width` und `Height` an. Denken Sie daran, dass sie in Punkten angegeben sind; 72 pt = 1 in. |
| *Ist es möglich, die Form an einer absoluten Position zu platzieren?* | Ja—verwenden Sie `WrapType = WrapType.Absolute` und setzen Sie die Eigenschaften `Top`/`Left`. |
| *Funktioniert das mit .NET Core?* | Ja. Aspose.Words ist plattformübergreifend; installieren Sie einfach das NuGet‑Paket für .NET Standard. |
| *Kann ich Text in das Rechteck einfügen?* | Nicht direkt; Sie müssten stattdessen eine `TextBox`‑Form einfügen. |

## Vollständiges funktionierendes Beispiel (Kopieren‑Einfügen bereit)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Führen Sie das Programm aus, navigieren Sie zu `C:\Temp\ShadowShape.docx`, und Sie sehen das Rechteck mit einem Schatten genau wie beschrieben.

## Fazit

Sie wissen jetzt, wie man mit Aspose.Words **eine Rechteckform** in einer Word‑Datei erstellt, wie man **die Formgröße festlegt**, **einen Schatten hinzufügt** und schließlich **das Word‑Dokument speichert** mit den Änderungen. Der gesamte Prozess – von **how to create document** bis zum Persistieren des Ergebnisses – passt in ein paar Zeilen C# und lässt sich für komplexere Layouts erweitern.

Bereit für die nächste Herausforderung? Versuchen Sie, das Rechteck durch eine Form mit abgerundeten Ecken zu ersetzen, experimentieren Sie mit verschiedenen Schattenfarben oder betten Sie die Form in eine Tabellenzelle ein. Jede Anpassung festigt die gleichen Kernkonzepte, die wir hier behandelt haben.

Wenn Ihnen diese Anleitung geholfen hat, teilen Sie sie, hinterlassen Sie einen Kommentar mit Ihren eigenen Variationen oder entdecken Sie unsere anderen Tutorials zur Word‑Automatisierung, wie das Einfügen von Bildern oder das Erzeugen von Tabellen mit Aspose.Words. Viel Spaß beim Coden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}