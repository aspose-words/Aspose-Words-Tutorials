---
category: general
date: 2026-03-06
description: Erstellen Sie ein Rechteck in Word und fügen Sie dem Shape einen Schatten
  mit Aspose.Words hinzu. Erfahren Sie, wie Sie ein Rechteck in Word einfügen und
  wie Sie einem Shape in C# einen Schatten hinzufügen.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: de
og_description: Erstellen Sie eine Rechteckform in Word und fügen Sie der Form einen
  Schatten mit Aspose.Words hinzu. Schritt‑für‑Schritt‑Anleitung, wie man ein Rechteck
  in Word einfügt und wie man der Form einen Schatten hinzufügt.
og_title: Rechteckform mit Schatten in Word mit Aspose.Words erstellen
tags:
- Aspose.Words
- C#
- Word Automation
title: Rechteckform mit Schatten in Word mit Aspose.Words erstellen
url: /de/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen einer Rechteckform mit Schatten in Word mit Aspose.Words

Haben Sie jemals **eine Rechteckform** in einem Word‑Dokument erstellen müssen, waren sich aber nicht sicher, wie Sie ihr ein professionelles Aussehen verleihen? Sie sind nicht allein – die meisten Entwickler stoßen beim ersten Versuch, automatisierten Dokumenten visuelle Akzente zu geben, auf dasselbe Problem. Die gute Nachricht? Mit Aspose.Words für .NET können Sie sowohl **eine Rechteckform erstellen** als auch **einen Form‑Schatten hinzufügen** mit nur wenigen Zeilen C#.

In diesem Tutorial zeigen wir Ihnen genau **wie man ein Rechteck in Word einfügt** und dann **wie man einen Schatten zur Form hinzufügt**, sodass sie vom Blatt „herausspringt“. Am Ende haben Sie ein fertig zu speicherndes `Shadow.docx`, das Sie in Word öffnen und ein grau getöntes Rechteck mit einem weichen Drop‑Shadow sehen können. Keine zusätzlichen Bilddateien, kein manuelles Nachbearbeiten – nur Code.

## Was Sie lernen werden

- Die genauen C#‑Anweisungen, die nötig sind, um **eine Rechteckform** mit Aspose.Words zu **erstellen**.  
- Wie man einen Schatten aktiviert und konfiguriert mithilfe des `Shadow`‑Objekts.  
- Warum jede Eigenschaft wichtig ist (z. B. `Transparency`, `Blur`, `Angle`).  
- Häufige Stolperfallen (Einheiten, Versionskompatibilität) und schnelle Lösungen.  
- Ein vollständiges, copy‑and‑paste‑fertiges Programm, das Sie noch heute ausführen können.

### Voraussetzungen

- .NET 6+ (oder .NET Framework 4.7+).  
- Aspose.Words für .NET 23.10 oder neuer (das NuGet‑Paket heißt `Aspose.Words`).  
- Grundlegende Kenntnisse in C# und Visual Studio (oder einer anderen IDE Ihrer Wahl).  

Wenn Sie das bereits haben, legen wir gleich los.

---

## Schritt 1: Projekt einrichten und Namespaces importieren

Erstellen Sie zunächst eine neue Konsolen‑App (oder verwenden Sie eine bestehende) und fügen Sie das Aspose.Words‑NuGet‑Paket hinzu:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Bringen Sie nun die benötigten Namespaces in Ihre `Program.cs` ein:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Pro‑Tipp:** Wenn Sie .NET 6+ anvisieren, können Sie globale `using`‑Direktiven aktivieren, um diese Zeilen in jeder Datei zu vermeiden.

---

## Schritt 2: **Rechteckform erstellen** in einem leeren Word‑Dokument

Wir beginnen mit einem frischen `Document`‑Objekt und einem `DocumentBuilder`, um es zu manipulieren. Die `InsertShape`‑Methode des Builders ist dort, wo die Magie passiert.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Warum 200 × 100 Punkte? In Word entspricht ein Punkt 1/72 Zoll, sodass das Rechteck etwa 2,8 × 1,4 Zoll groß wird – groß genug, um wahrgenommen zu werden, aber nicht überwältigend. Sie können diese Zahlen an Ihr Layout anpassen; denken Sie nur daran, dass sie in **Punkten**, nicht in Pixeln, gemessen werden.

---

## Schritt 3: **Schatten zur Form hinzufügen** – das Aussehen konfigurieren

Jetzt, wo wir ein Rechteck haben, geben wir ihm einen dezenten grauen Schatten. Das `Shadow`‑Objekt gehört zur `Shape` und stellt mehrere praktische Eigenschaften bereit.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Was jede Eigenschaft bewirkt

| Eigenschaft | Wirkung | Typische Werte |
|-------------|---------|----------------|
| **Enabled** | Schaltet den Schatten ein/aus | `true` oder `false` |
| **Color** | Grundfarbe des Schattens | Beliebiges `System.Drawing.Color` |
| **Transparency** | Opazität (0 = undurchsichtig, 1 = unsichtbar) | 0.0 – 1.0 |
| **Blur** | Weichheit der Kante | 0 – 10 (höher = weicher) |
| **Distance** | Abstand zwischen Form und Schatten | 0 – 20 Punkte |
| **Angle** | Richtung, aus der das Licht zu kommen scheint | 0 – 360 Grad |
| **Size** | Skalierung des Schattens relativ zur Form | 0 – 200 % |

> **Warum diese Einstellungen?**  
> Durch Feineinstellung des Schattens können Sie Unternehmens‑Branding‑Richtlinien entsprechen (z. B. ein subtiler Transparenzwert von 20 % für ein professionelles Aussehen), ohne externe Bildbearbeitungsprogramme zu verwenden.

---

## Schritt 4: Dokument speichern und Ergebnis prüfen

Zum Schluss schreiben wir die Datei auf die Festplatte. Sie können jeden gewünschten Ordner wählen; ersetzen Sie einfach `YOUR_DIRECTORY` durch einen echten Pfad.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Öffnen Sie `Shadow.docx` in Microsoft Word und Sie sollten ein graues Rechteck mit einem sanften Drop‑Shadow sehen, das im 45°‑Winkel versetzt ist. Dieser visuelle Hinweis lässt die Form „gehoben“ vom Blatt wirken – genau das, was Sie von einem professionellen Bericht oder einer Rechnung erwarten.

---

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette Programm, das Sie in `Program.cs` einfügen können. Es fehlen keine Teile; es kompiliert und läuft sofort.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Erwartete Ausgabe

- **Datei:** `Shadow.docx` im Ausführungsordner des Projekts.  
- **Visuell:** Ein einzelnes Rechteck, zentriert auf der Seite, standardmäßig weiß gefüllt, mit einem grauen Schatten, der 4 Punkte nach unten‑rechts versetzt und leicht verschwommen ist für ein natürliches Aussehen.

---

## Häufige Fragen & Sonderfälle

### 1. Was, wenn ich eine andere Einheit benötige (z. B. Zentimeter)?

Aspose.Words arbeitet mit Punkten, aber Sie können Zentimeter mit der einfachen Formel in Punkte umrechnen:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Funktioniert das mit älteren Aspose.Words‑Versionen?

Die `Shadow`‑API wurde in Version 14.0 eingeführt. Wenn Sie eine ältere Version verwenden, müssen Sie über NuGet ein Upgrade durchführen. Der Rest des Codes (Erstellung von Formen) ist seit vielen Jahren stabil, sodass Sie keine Breaking Changes erwarten.

### 3. Kann ich einem anderen Formtyp (z. B. Kreisen) einen Schatten hinzufügen?

Absolut – jedes `Shape`‑Objekt verfügt über eine `Shadow`‑Eigenschaft. Ersetzen Sie einfach `ShapeType.Rectangle` durch `ShapeType.Ellipse` oder `ShapeType.Cloud` und wenden Sie dieselben Schatten‑Einstellungen an.

### 4. Was, wenn ich einen farbigen Schatten brauche (z. B. blau für eine Marke)?

Ersetzen Sie `Color.Gray` durch jede gewünschte `Color`:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Achten Sie darauf, `Transparency` anzupassen, damit die Farbe nicht zu dominant wird.

---

## 🎨 Visuelle Zusammenfassung

![create rectangle shape with shadow in Word using Aspose.Words](image-placeholder.png "create rectangle shape with shadow in Word using Aspose.Words")

*Alt‑Text: create rectangle shape with shadow in Word using Aspose.Words*

Der Screenshot (Platzhalter) zeigt das Enddokument – nur das Rechteck und sein weicher grauer Schatten.

---

## Fazit

Sie wissen jetzt, wie Sie **eine Rechteckform** in einer Word‑Datei **erstellen**, **einen Form‑Schatten hinzufügen** und jeden visuellen Aspekt mit Aspose.Words für .NET feinjustieren. Das kurze Programm, das wir gebaut haben, deckt den gesamten Workflow ab – von

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}