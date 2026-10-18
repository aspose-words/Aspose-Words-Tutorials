---
category: general
date: 2026-03-22
description: Speichern Sie ein Word-Dokument und erkennen Sie fehlende Schriftarten
  mit Aspose.Words. Erfahren Sie, wie Sie fehlende Schriftarten verfolgen und Schriftartfehler
  in C# erfassen.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: de
og_description: Word-Dokument speichern und fehlende Schriftarten in C# erkennen.
  Dieser Leitfaden zeigt, wie man fehlende Schriftarten verfolgt und Schriftartfehler
  mithilfe eines Warnungs‑Callbacks erfasst.
og_title: Word-Dokument speichern – Fehlende Schriftarten mit Aspose.Words erkennen
tags:
- Aspose.Words
- C#
- Document Processing
title: Word-Dokument speichern – Fehlende Schriftarten mit Aspose.Words erkennen
url: /de/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word‑Dokument speichern – Fehlende Schriftarten mit Aspose.Words erkennen

Haben Sie schon einmal ein **Word‑Dokument speichern** müssen, waren sich aber nicht sicher, ob einige der darin enthaltenen Schriftarten den Rundweg überleben? Das passiert öfter, als man denkt, besonders wenn Dokumente zwischen Rechnern mit unterschiedlichen Schriftbibliotheken hin‑und her reisen. Die gute Nachricht? Aspose.Words bietet Ihnen eine integrierte Möglichkeit, **fehlende Schriftarten** zu **erkennen**, während Sie das **Word‑Dokument speichern**, sodass Sie sie protokollieren, warnen oder sogar ersetzen können, bevor die Datei auf dem Bildschirm des Benutzers erscheint.

In diesem Tutorial führen wir Sie durch ein komplettes, sofort ausführbares Beispiel, das nicht nur ein Word‑Dokument speichert, sondern auch **fehlende Schriftarten verfolgt** und **Schriftart‑Fehler erfasst** mithilfe eines benutzerdefinierten Warn‑Handlers. Am Ende wissen Sie genau, warum der Warn‑Callback wichtig ist, wie Sie ihn einbinden und wie die Konsolenausgabe aussieht, wenn eine Ersetzung stattfindet. Kein unnötiger Schnickschnack – nur der Code, den Sie jetzt in ein .NET‑Projekt einfügen können.

> **Voraussetzungen**  
> • .NET 6 (oder ein aktuelles .NET Framework) installiert  
> • Visual Studio 2022 oder Ihre bevorzugte IDE  
> • Eine lizenzierte Kopie von **Aspose.Words for .NET** (die kostenlose Testversion reicht zum Ausprobieren)  

Wenn Sie das haben, legen wir los.

---

## Word‑Dokument speichern und fehlende Schriftarten erkennen

Die Grundidee ist einfach: Bevor Sie `Document.Save` aufrufen, weisen Sie `Document.WarningCallback` ein Objekt zu, das `IWarningCallback` implementiert. Aspose.Words ruft dieses Objekt für jede Warnung auf, die es findet, einschließlich **Schriftart‑Ersetzungs‑Warnungen**, die auftreten, wenn das Quell‑Dokument eine Schriftart referenziert, die Ihr System nicht finden kann.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**Was Sie sehen werden:**  
Wenn `input.docx` eine Schriftart referenziert, die nicht installiert ist, gibt die Konsole etwa Folgendes aus:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Diese Zeile sagt Ihnen genau, welche Schriftart fehlte und welche Schriftart Aspose.Words stattdessen verwendet hat – ideal, um **Schriftart‑Fehler** zu **erfassen**, bevor Sie die Datei ausliefern.

---

## Fehlende Schriftarten mit einem Warn‑Callback verfolgen (Schritt‑für‑Schritt)

### 1️⃣ Aspose.Words installieren

Öffnen Sie die NuGet‑Konsole Ihres Projekts und führen Sie aus:

```bash
dotnet add package Aspose.Words
```

Damit wird die neueste stabile Version (derzeit 24.10) heruntergeladen. Die Bibliothek aktuell zu halten, stellt sicher, dass Sie die neuesten **fehlende Schriftarten erkennen**‑Funktionen und Fehlerbehebungen erhalten.

### 2️⃣ Den Warn‑Handler definieren

Warum benötigen wir eine separate Klasse? Die Implementierung von `IWarningCallback` ermöglicht es Ihnen, die gesamte Warnlogik an einer Stelle zu zentralisieren. Sie könnten außerdem in eine Datei protokollieren, Telemetrie senden oder eine Ausnahme werfen, wenn eine fehlende Schriftart für Ihren Workflow ein kritischer Fehler ist.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Pro‑Tipp:** Wenn Sie **fehlende Schriftarten** über viele Dokumente hinweg **verfolgen** müssen, speichern Sie die Meldungen in einer `List<string>` im Handler und stellen Sie sie später für Berichte bereit.

### 3️⃣ Ihr Quell‑Dokument laden

Der `Document`‑Konstruktor kann einen Dateipfad, einen Stream oder sogar rohe Bytes akzeptieren. In den meisten Fällen geben Sie ihm eine `.docx`, die Sie von einem Benutzer oder einem anderen System erhalten haben.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Ist die Datei groß, sollten Sie `LoadOptions` verwenden, um Lazy Loading zu aktivieren – das reduziert den Speicherverbrauch.

### 4️⃣ Den Callback anhängen

Weisen Sie die Instanz `doc.WarningCallback` zu. Ab diesem Moment wird jede Warnung (einschließlich Schriftart‑Ersetzungen) über Ihren Handler geleitet.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Das Dokument speichern

Jetzt können Sie sicher `Save` aufrufen. Der Warn‑Handler wird **synchron** während des Speicher‑Vorgangs ausgeführt, sodass Sie die Ausgabe sofort sehen.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Möchten Sie in ein anderes Format (PDF, HTML usw.) speichern, funktioniert derselbe Warn‑Mechanismus – Aspose.Words meldet weiterhin fehlende Schriftarten vor der Konvertierung.

---

## Schriftart‑Fehler erfassen – Häufige Sonderfälle

Der Basis‑Ablauf deckt die meisten Szenarien ab, aber reale Projekte stoßen häufig auf ein paar Stolpersteine. Nachfolgend einige Varianten, denen Sie begegnen können, und wie Sie sie handhaben.

### Fehlende Schriftart in Kopf‑/Fußzeile

Kopf‑ und Fußzeilen sind separate Knoten, aber das Warnsystem behandelt sie wie Fließtext. Es ist kein zusätzlicher Code nötig; der Callback wird auch für diese Schriftarten ausgelöst. Stellen Sie nur sicher, dass Sie das gesamte Dokument laden (Standardverhalten tut das).

### Mehrere Ersetzungen in einem Dokument

Verwendet ein Dokument mehrere unbekannte Schriftarten, wird der Handler einmal pro Ersetzung aufgerufen. Um ein Überfluten der Konsole zu vermeiden, können Sie Meldungen deduplizieren:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Warnungen in Ausnahmen umwandeln

Manchmal ist eine fehlende Schriftart ein Deal‑Breaker. Werfen Sie innerhalb des Handlers eine Ausnahme, um das Speichern abzubrechen:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Denken Sie daran, `doc.Save` in einen `try/catch`‑Block zu packen, um die Ausnahme elegant zu behandeln.

---

## Ergebnis prüfen – Was Sie erwarten können

Nach Abschluss des Speichervorgangs öffnen Sie `output.docx` in Microsoft Word (oder einem kompatiblen Viewer). Das Layout sollte dem Original entsprechen, wobei die ersetzten Schriftarten als die in der Konsole beobachteten Fallback‑Schriftarten erscheinen. Zum Nachprüfen können Sie:

1. **Datei → Optionen → Erweitert → Dokumentinhalt anzeigen → Entwurfsqualität verwenden** öffnen – das zwingt Word, versteckte Schriftart‑Ersetzungen sichtbar zu machen.  
2. Das **Schriftarten ersetzen**‑Dialogfeld von Word (`Strg+Shift+F`) nutzen, um zu sehen, welche Schriftarten tatsächlich eingebettet sind.

Wenn alles passt, haben Sie erfolgreich ein **Word‑Dokument gespeichert**, **fehlende Schriftarten erkannt** und **Schriftart‑Fehler erfasst**. 🎉

---

## Vollständiges Beispiel (Einfaches Kopieren & Einfügen)

Unten finden Sie das komplette Programm, das Sie in ein neues Konsolen‑App‑Projekt einfügen können. Ersetzen Sie `YOUR_DIRECTORY` durch einen echten Ordnerpfad auf Ihrem Rechner.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Erwartete Konsolenausgabe** (Beispiel):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

Das war’s – keine versteckten Schritte, keine externen Dokumente, die Sie suchen müssen.

---

## Fazit

Wir haben Ihnen gezeigt, wie Sie ein **Word‑Dokument speichern** und gleichzeitig **fehlende Schriftarten erkennen**, **fehlende Schriftarten verfolgen** und **Schriftart‑Fehler erfassen** können, indem Sie den Warn‑Callback von Aspose.Words nutzen. Durch das Einbinden einer kleinen `IWarningCallback`‑Implementierung erhalten Sie volle Transparenz über Schriftart‑Ersetzungen zur Speicherzeit und können protokollieren, ersetzen oder abbrechen, je nach Bedarf.

Bereit für die nächste Herausforderung? Versuchen Sie, den Handler so zu erweitern, dass Warnungen in ein strukturiertes JSON‑Log geschrieben werden, oder kombinieren Sie ihn mit Aspose.PDF, um dasselbe Dokument zu konvertieren und dabei Schriftinformationen zu bewahren. Sie können auch das Einbetten fehlender Schriftarten direkt in die Ausgabedatei erkunden – Aspose.Words unterstützt das Einbetten von Schriftarten über `LoadOptions.FontSettings`.

Probieren Sie es aus, passen Sie den Code an Ihre Pipeline an und lassen Sie uns wissen, wie es bei Ihnen funktioniert. Viel Spaß beim Coden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}