---
category: general
date: 2026-03-27
description: 'Aspose-Schriftartenersetzung leicht gemacht: Erfahren Sie, wie Sie Schriftarteinstellungen
  konfigurieren, Warnungen erfassen und fehlende Schriftarten in Ihren .NET-Anwendungen
  behandeln.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: de
og_description: Meistern Sie die Aspose-Schriftart-Substitution, indem Sie die Schriftarteinstellungen
  konfigurieren und fehlende Schriftarten mit einem Warn‑Callback behandeln. Vollständige
  C#‑Anleitung.
og_title: Aspose-Schriftart-Substitution – Schriftarteinstellungen in C# konfigurieren
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose-Schriftartenersetzung – So konfigurieren Sie Schriftarteinstellungen
  in C#
url: /de/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Vollständige Anleitung zum Konfigurieren von Schriftarteinstellungen

Haben Sie schon einmal ein Dokument gehabt, das plötzlich Ihre benutzerdefinierte Schriftart durch etwas Generisches ersetzt? Das ist **aspose font substitution**, das seine Arbeit tut — fehlende Schriftarten durch die am besten passende ersetzt. Das ist praktisch, aber wenn Sie *genau* wissen müssen, welche Schriftart ausgetauscht wurde, müssen Sie das Warnsystem der Bibliothek nutzen und die Schriftarteinstellungen selbst konfigurieren.

In diesem Tutorial führen wir Sie durch ein praxisnahes Szenario: Laden einer DOCX‑Datei, die eine Schriftart referenziert, die Sie nicht besitzen, das Erfassung des Substitutions‑Ereignisses und das Ausgeben einer freundlichen Meldung in der Konsole. Am Ende sind Sie sicher im **configure font settings**, beim Einrichten eines **Aspose.Words warning callback** und beim Anpassen des Beispiels an jeden Workflow.

> **Was Sie benötigen**  
> • .NET 6+ (oder .NET Framework 4.7.2+)  
> • Aspose.Words für .NET (neueste NuGet)  
> • Eine DOCX, die eine fehlende Schriftart referenziert (wir nennen sie `MissingFont.docx`)  

Lassen Sie uns loslegen.

---

## Schritt 1: Aspose.Words installieren und das Projekt vorbereiten

Bevor wir Code schreiben, stellen Sie sicher, dass das Aspose.Words‑Paket referenziert wird:

```bash
dotnet add package Aspose.Words
```

> **Pro‑Tipp:** Verwenden Sie die neueste stabile Version; Stand März 2026 ist das 23.11.0. Neuere Releases verbessern die Schriftart‑Matching‑Algorithmen und fügen zusätzliche Warnungsarten hinzu.

Erstellen Sie eine neue Konsolen‑App (oder fügen Sie den Code in ein bestehendes Projekt ein) und fügen Sie die üblichen `using`‑Direktiven hinzu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Diese Namespaces geben uns Zugriff auf `Document`, `LoadOptions` und die font‑bezogenen Klassen, die wir benötigen.

---

## Schritt 2: Schriftarteinstellungen mit LoadOptions konfigurieren

Das Herz der **aspose font substitution**‑Steuerung befindet sich in `LoadOptions.FontSettings`. Indem wir ein leeres `FontSettings`‑Objekt übergeben, sagen wir Aspose, dass es seine Standardsuchpfade verwenden und jede Substitution über einen Warn‑Callback melden soll.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Warum nicht einfach die Vorgaben nutzen? Weil das Anbinden eines Warn‑Callbacks (nächster Schritt) nur funktioniert, wenn die Eigenschaft `FontSettings` nicht null ist. Diese kleine Zeile gibt uns einen Hook in den Substitutions‑Prozess, ohne das eigentliche Suchverhalten zu ändern.

---

## Schritt 3: Einen Warn‑Callback anhängen, um Substitutionen zu erfassen

Aspose.Words implementiert das Interface `IWarningCallback`. Immer wenn etwas Bemerkenswertes passiert — wie eine fehlende Schriftart — ruft es unsere `Warning`‑Methode auf. Wir implementieren einen kleinen Handler, der nach `WarningType.FontSubstitution` filtert und die Beschreibung ausgibt.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

Und hier ist der eigentliche Handler:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Warum das wichtig ist** – Ohne den Callback tauscht Aspose Schriftarten stillschweigend aus, und Sie wissen nie, welche verwendet wurde. Der Callback macht den Prozess transparent, was für Compliance‑Berichte oder das Debuggen von Layout‑Problemen unerlässlich ist.

---

## Schritt 4: Das Dokument mit den konfigurierten Optionen laden

Jetzt laden wir das Dokument und übergeben die zuvor vorbereiteten `loadOptions`. Wenn die Quelldatei eine Schriftart referenziert, die nicht installiert ist, wird unser Handler ausgelöst.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Ersetzen Sie `YOUR_DIRECTORY` durch den tatsächlichen Pfad, in dem `MissingFont.docx` liegt. Beim Ausführen des Programms sollten Sie eine Ausgabe ähnlich der folgenden sehen:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Diese Zeile sagt Ihnen exakt, welche Schriftart fehlte und welche Ersatzschrift Aspose gewählt hat.

---

## Schritt 5: (Optional) Schriftsuchpfade feinabstimmen

Falls Sie einen privaten Ordner mit Unternehmensschriftarten haben, können Sie Aspose mitteilen, dort zuerst zu suchen, bevor auf Systemschriftarten zurückgegriffen wird. Das ist eine erweiterte Anwendung von **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Durch `recursive: true` wird Aspose auch Unterordner durchsuchen. Jetzt versucht die Bibliothek zuerst Ihre privaten Schriftarten, wodurch die Wahrscheinlichkeit unerwünschter Substitutionen sinkt.

---

## Vollständiges funktionsfähiges Beispiel

Alles zusammengeführt, hier das komplette, sofort ausführbare Programm:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Erwartete Ausgabe** (wenn eine fehlende Schriftart gefunden wird):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Sind alle Schriftarten vorhanden, läuft das Programm still (keine Warnungen) und erzeugt dennoch das PDF.

---

## Häufige Fragen & Sonderfälle

### Was tun, wenn ich die Substitution komplett *verhindern* möchte?

Setzen Sie `FontSettings.SubstitutionSettings` auf `null` oder verwenden Sie `FontSettings.FontSubstitutionSettings`, um das Verhalten zu steuern. Beispiel:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Jetzt wirft Aspose eine Ausnahme, anstatt stillschweigend zu substituieren, die Sie abfangen und behandeln können.

### Funktioniert das mit anderen Dateiformaten (z. B. .doc, .rtf)?

Absolut. Das gleiche `LoadOptions`‑Objekt kann an jeden `Document`‑Konstruktor übergeben werden, der einen Dateipfad akzeptiert. Der Warn‑Callback wird für alle Formate ausgelöst, die Schriftarten verwenden.

### Kann ich den *genauen* Namen der Ersatzschrift erfassen?

Ja. Der String `info.Description` enthält sowohl die fehlende Schriftart als auch die Ersatzschrift. Wenn Sie den Namen programmgesteuert benötigen, können Sie ihn parsen oder das `FontInfo`‑Objekt verwenden (verfügbar in neueren Versionen).

### Wie verhält sich das in einer Multi‑Thread‑Umgebung?

`FontSettings` ist **nicht** thread‑sicher. Erzeugen Sie pro Thread ein separates `LoadOptions` (mit eigenem `FontSettings`) oder schützen Sie den Zugriff mit einem Lock.

---

## Fazit

Wir haben alles behandelt, was Sie benötigen, um **aspose font substitution** und **configure font settings** in einer C#‑Anwendung zu meistern:

1. Aspose.Words installieren und die notwendigen `using`‑Anweisungen hinzufügen.  
2. Ein `LoadOptions`‑Objekt mit einem frischen `FontSettings` erstellen.  
3. Einen benutzerdefinierten `IWarningCallback` anhängen, um Substitutions‑Ereignisse sichtbar zu machen.  
4. Das Dokument laden und den Callback fehlende Schriftarten melden lassen.  
5. (Optional) Den Suchpfad erweitern oder die Substitution komplett deaktivieren.

Mit diesem Muster können Sie fehlende Schriftarten für Compliance protokollieren, Benutzer in einer UI benachrichtigen oder automatisch Ersatzschriftarten einbetten, bevor Sie veröffentlichen. Als nächstes könnten Sie **Aspose.Words font substitution policies** erkunden oder den Workflow in eine größere Dokumenten‑Verarbeitungspipeline integrieren.

Viel Spaß beim Coden und mögen Ihre Dokumente stets mit der richtigen Schriftart gerendert werden!  

---  

![Diagram showing Aspose.Words loading a document, invoking FontSettings, triggering a warning callback, and outputting substitution info](image-placeholder.png "aspose font substitution workflow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}