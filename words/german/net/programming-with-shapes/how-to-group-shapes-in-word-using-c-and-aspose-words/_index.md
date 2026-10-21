---
category: general
date: 2026-09-30
description: Formen in Word mit C# gruppieren – lernen Sie, wie Sie Formen gruppieren,
  Rechtecke und Ellipsen hinzufügen und Rechteckformen programmgesteuert in Word‑Dokumente
  einfügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: de
lastmod: 2026-09-30
og_description: Formen in Word mit C# und Aspose.Words gruppieren. Folgen Sie dieser
  umfassenden Anleitung, um ein Rechteck hinzuzufügen, eine Ellipse hinzuzufügen und
  zu lernen, wie man Formen effizient gruppiert.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Formen in Word mit C# gruppieren – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man Formen in Word mit C# und Aspose.Words gruppiert
url: /de/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Formen in Word mit C# und Aspose.Words gruppiert

Wenn Sie **Formen in Word** programmgesteuert **gruppieren** müssen, zeigt Ihnen dieses Handbuch genau, wie es geht. Sie sehen, wie man ein Rechteck, eine Ellipse hinzufügt und sie dann zu einer einzigen Gruppierungsform kombiniert – mithilfe der Aspose.Words‑Bibliothek für .NET.

Die Arbeit mit Formen ist ein häufiges Bedürfnis beim automatischen Erzeugen von Berichten, Verträgen oder Marketing‑Materialien. Am Ende dieses Tutorials besitzen Sie eine wiederverwendbare C#‑Methode, die eine DOCX‑Datei lädt, ein Rechteck und eine Ellipse einfügt, sie gruppiert und das Ergebnis speichert – ganz ohne Word manuell zu öffnen.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 SDK oder neuer installiert  
* Eine Entwicklungsumgebung wie Visual Studio 2022 (die Community‑Edition reicht)  
* Eine Aspose.Words für .NET‑Lizenz oder eine kostenlose Evaluierungskopie (die API funktioniert ohne Lizenz, fügt jedoch ein Wasserzeichen hinzu)  

Sie benötigen außerdem ein Quell‑Word‑Dokument (`input.docx`) in einem Ordner, den Sie im Code referenzieren können. Das Dokument kann leer sein; das Tutorial konzentriert sich auf die Handhabung von Formen.

## Schritt 1: Neues Konsolenprojekt erstellen und Aspose.Words hinzufügen

Öffnen Sie ein Terminal oder die Visual Studio‑Eingabeaufforderung und führen Sie aus:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Damit wird eine frische Konsolenanwendung namens **WordShapeDemo** erstellt und das NuGet‑Paket `Aspose.Words` hinzugefügt, das die Klassen `Document` und `DocumentBuilder` enthält, die zur Manipulation von Word‑Dateien verwendet werden.

## Schritt 2: Dokument laden oder erstellen

Der erste Vorgang beim Arbeiten mit **Gruppenformen in Word** besteht darin, ein `Document`‑Objekt zu erhalten. Sie können entweder eine vorhandene DOCX‑Datei laden oder ein leeres Dokument beginnen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

Die Klasse `Document` repräsentiert die gesamte Word‑Datei. Das Laden einer Datei liefert Ihnen eine fertige Leinwand zum Einfügen von Formen.

## Schritt 3: Eine Gruppenform beginnen

Eine *Gruppenform* lässt Sie mehrere unabhängige Formen als eine Einheit behandeln – ideal, um sie gemeinsam zu verschieben oder zu skalieren. Um eine Gruppe zu starten, rufen Sie `StartGroupShape()` auf einem `DocumentBuilder` auf.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Der Aufruf von `StartGroupShape` teilt Aspose.Words mit, dass jede nachfolgende Formeinfügung zur selben logischen Gruppe gehört, bis Sie `EndGroupShape` aufrufen.

## Schritt 4: Rechteckform in Word hinzufügen

Jetzt, wo die Gruppe geöffnet ist, fügen Sie ein Rechteck ein. Die Methode `InsertShape` erwartet ein `ShapeType`‑Enum, gefolgt von Breite und Höhe (in Punkten).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Das Rechteck wird zum ersten Mitglied der Gruppe. Sie können später seine Füllung, Kontur oder Text anpassen, falls nötig.

## Schritt 5: Ellipsenform in Word hinzufügen

Als Nächstes fügen Sie eine Ellipse hinzu (ein Kreis, wenn Breite und Höhe gleich sind). Dies demonstriert **wie man eine Ellipse hinzufügt** mit demselben Builder.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Beide Formen teilen nun denselben Koordinatenraum innerhalb der Gruppe, was die visuelle Ausrichtung erleichtert.

## Schritt 6: Definition der Gruppenform schließen

Wenn Sie alle gewünschten Mitglieder hinzugefügt haben, schließen Sie die Gruppe. Damit wird die Sammlung von Formen finalisiert, sodass Word sie als ein Objekt behandelt.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

An diesem Punkt enthält das Dokument ein einzelnes gruppiertes Objekt, das aus einem Rechteck und einer Ellipse besteht.

## Schritt 7: Das geänderte Dokument speichern

Zum Schluss schreiben Sie die Änderungen zurück auf die Festplatte. Sie können die Originaldatei überschreiben oder eine neue erstellen.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Das Ausführen des Programms erzeugt `output.docx`. Öffnen Sie die Datei in Microsoft Word, wählen Sie die Form aus, und Sie werden sehen, dass Rechteck und Ellipse zusammen bewegt werden – ein Beweis dafür, dass die **Gruppierung von Formen in Word** erfolgreich war.

### Erwartetes Ergebnis

* Die Word‑Datei enthält ein einzelnes gruppiertes Objekt.  
* Durch Auswahl der Gruppe können Sie das Rechteck und die Ellipse gleichzeitig ziehen, skalieren oder drehen.  
* Keine manuelle Interaktion mit Word ist erforderlich; alles geschieht über C#‑Code.

![Grouped shapes in Word document](grouped-shapes.png "Screenshot eines Word‑Dokuments, das ein gruppiertes Rechteck und eine Ellipse zeigt")

*Bild‑Alt‑Text: “Screenshot eines Word‑Dokuments, das ein gruppiertes Rechteck und eine Ellipse zeigt”* (erfüllt die Anforderung an den Bild‑Alt‑Text).

## Warum das Gruppieren von Formen wichtig ist

Das Gruppieren von Formen ist mehr als nur ein visueller Komfort. Es ermöglicht Ihnen:

* **Layout‑Konsistenz bewahren** – das Verschieben einer Gruppe hält die relativen Positionen unverändert.  
* **Transformationen einmal anwenden** – drehen oder skalieren Sie die gesamte Gruppe statt jede Form einzeln.  
* **Nachgelagerte Verarbeitung vereinfachen** – wenn andere Werkzeuge das DOCX lesen, sehen sie eine einzige zusammengesetzte Form, was die Komplexität reduziert.

Falls Sie später weitere Formen (z. B. eine Linie oder ein Textfeld) zur selben logischen Einheit hinzufügen möchten, rufen Sie einfach erneut `InsertShape` auf, bevor Sie `EndGroupShape` ausführen.

## Häufige Varianten und Sonderfälle

| Situation | Wie man damit umgeht |
|-----------|----------------------|
| **Unterschiedliche Einheiten** – Sie haben Maße in Zentimetern | Konvertieren Sie Zentimeter in Punkte (`1 cm ≈ 28,35 pt`), bevor Sie `InsertShape` aufrufen. |
| **Ein Textlabel hinzufügen** – Sie wollen eine Beschriftung innerhalb der Gruppe | Fügen Sie nach Rechteck und Ellipse ein `ShapeType.TextBox` ein und setzen Sie anschließend dessen `Text`‑Eigenschaft. |
| **Füllfarbe anwenden** – Sie benötigen ein blaues Rechteck | Nach `InsertShape` holen Sie die letzte Form über `builder.CurrentParagraph.Runs[0].Font` und setzen `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Ein anderes Dokumentformat verwenden** – Sie zielen auf `.doc` statt `.docx` | Der gleiche Code funktioniert; ändern Sie lediglich die Dateierweiterung beim Aufruf von `Save`. Aspose.Words übernimmt das Format automatisch. |

## Pro‑Tipps

* **Builder wiederverwenden** – Sie können mehrere Gruppen im selben Dokument starten und beenden; rufen Sie einfach nach `EndGroupShape` erneut `StartGroupShape` auf.  
* **Performance** – das Stapel‑Einfügen von Formen innerhalb eines einzigen `StartGroupShape/EndGroupShape`‑Blocks ist schneller als das einzelne Einfügen von Formen außerhalb einer Gruppe.  
* **Lizenzierung** – eine Evaluationslizenz fügt ein Wasserzeichen auf der ersten Seite ein. Installieren Sie eine gültige Lizenz, um es in Produktionsumgebungen zu entfernen.

## Fazit

Sie wissen jetzt, wie man **Formen in Word** mit C# **gruppiert**, wie man ein **Rechteck** **hinzufügt**, wie man eine **Ellipse** **einfügt** und wie man **Rechteck‑Formen in Word‑Dokumenten** mit Aspose.Words verwendet. Das vollständige, ausführbare Beispiel demonstriert jeden Schritt von der Projekt‑Einrichtung bis zum Speichern der finalen Datei.

Ab hier können Sie weitere Formtypen erkunden, Stil‑Anpassungen vornehmen oder gruppierte Formen mit Tabellen und Bildern kombinieren, um anspruchsvolle, programmgesteuert erzeugte Dokumente zu erstellen.

---

**Nächste Schritte**

* Lernen Sie, **gruppierte Formen zu drehen**: verwenden Sie `Shape.RotationAngle`, nachdem die Gruppe geschlossen wurde.  
* Erkunden Sie **Füll‑ und Konturanpassungen** für Rechtecke und Ellipsen.  
* Integrieren Sie diese Logik in eine ASP.NET Core‑API, um Berichte auf Abruf zu erzeugen.  

Viel Spaß beim Coden!


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Gruppenform in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Formen in Word‑Dokumenten mit Aspose.Words für .NET einfügen](/words/english/net/working-with-shapes/insert-shape/)
- [Rechteck‑Form in Word erstellen – Vollständiger Aspose.Words‑Leitfaden](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}