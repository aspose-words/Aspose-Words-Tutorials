---
category: general
date: 2026-01-11
description: Beschädigtes Dokument in C# mit Aspose.Words wiederherstellen. Erfahren
  Sie, wie Sie den Wiederherstellungsmodus einstellen, ein DOCX mit Wiederherstellung
  laden und den Benutzer bei einem Fehler in wenigen einfachen Schritten auffordern.
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: de
og_description: Beschädigtes Dokument in C# wiederherstellen, indem der Wiederherstellungsmodus
  aktiviert, ein DOCX mit Wiederherstellung geladen und bei einem Fehler der Benutzer
  benachrichtigt wird. Vollständige Schritt‑für‑Schritt‑Anleitung.
og_title: Beschädigtes Dokument in C# wiederherstellen – Schnellleitfaden
tags:
- Aspose.Words
- C#
- Document Recovery
title: Beschädigtes Dokument in C# wiederherstellen – Wiederherstellungsmodus festlegen
  und Benutzer auffordern
url: /de/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Beschädigtes Dokument in C# wiederherstellen – Vollständige Anleitung

Haben Sie schon einmal versucht, ein DOCX zu öffnen, das in Word gut aussieht, aber in Ihrem Code eine Ausnahme auslöst? Wahrscheinlich haben Sie es mit einem **recover corrupted document** Szenario zu tun. Die gute Nachricht ist, dass Aspose.Words Ihnen eine feinkörnige Kontrolle darüber gibt, wie Sie mit diesen lästigen Dateien umgehen – ob Sie sie stillschweigend reparieren, eine Ausnahme werfen oder den Benutzer fragen möchten, was zu tun ist.

In diesem Tutorial führen wir Sie durch alles, was Sie benötigen, um **recover corrupted document** Dateien zu bearbeiten, von der Installation der Bibliothek bis zur Auswahl der richtigen **set recovery mode** Option, **load docx with recovery** und schließlich **prompt user on error**, wenn etwas schiefgeht. Keine Ausschweifungen, nur ein vollständiges, ausführbares Beispiel, das Sie in jedes .NET‑Projekt einbinden können.

> **Schnelle Vorschau:** Am Ende haben Sie eine Konsolenanwendung, die ein möglicherweise beschädigtes `corrupt.docx` lädt, alle Warnungen protokolliert und den Benutzer fragt, ob er fortfahren möchte, wenn die Wiederherstellung fehlschlägt.

## Was Sie benötigen

- **.NET 6.0** oder höher (der Code funktioniert auch mit .NET Framework 4.6+).  
- **Aspose.Words for .NET** – Installation über NuGet (`Install-Package Aspose.Words`).  
- Eine **corrupt DOCX**‑Datei zum Testen (Sie können eine Datei absichtlich beschädigen, indem Sie sie in einem Hex‑Editor öffnen oder die Dateierweiterung umbenennen).  
- Beliebige IDE nach Wahl – Visual Studio, Rider oder sogar VS Code reichen aus.

> *Pro‑Tipp:* Bewahren Sie eine Sicherungskopie der Originaldatei auf. Die Wiederherstellung kann Teile des Dokuments neu schreiben, und Sie möchten die guten Teile nicht verlieren.

## Schritt 1 – Aspose.Words installieren und Namespaces hinzufügen

Zuerst das Wichtigste. Holen Sie sich die Bibliothek von NuGet und bringen Sie die erforderlichen Namespaces in den Gültigkeitsbereich.

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Das ist alles, was Sie für den Rest des Leitfadens benötigen. Der Namespace `Aspose.Words.Loading` enthält die Klasse `LoadOptions`, die der Schlüssel zu **set recovery mode** ist.

## Schritt 2 – Einen Wiederherstellungsmodus wählen (Primary H2 with Keyword)

### Beschädigtes Dokument wiederherstellen – Den richtigen Wiederherstellungsmodus festlegen

Aspose.Words bietet drei Wiederherstellungsverhalten:

| Mode | What Happens | When to Use |
|------|--------------|------------|
| **PromptUser** | Zeigt einen Dialog an (oder Sie können Ihre eigene Eingabeaufforderung implementieren) und versucht, die Datei zu reparieren. | Ideal für interaktive Werkzeuge, bei denen der Benutzer entscheiden kann. |
| **Silent** | Versucht, automatisch zu reparieren, ohne UI. | Gut für Batch‑Jobs oder Dienste. |
| **ThrowException** | Stoppt die Verarbeitung und wirft eine Ausnahme. | Verwenden, wenn Sie eine strenge Validierung wünschen. |

Im Folgenden sehen Sie, wie Sie **set recovery mode** auf `PromptUser` setzen. Wenn Sie eine stille Behandlung bevorzugen, tauschen Sie einfach den Enum‑Wert aus.

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **Warum das wichtig ist:** Durch das explizite **set recovery mode** teilen Sie Aspose.Words mit, wie aggressiv es vorgehen soll. Der Standardwert ist `PromptUser`, aber die explizite Angabe macht Ihre Absicht kristallklar – sowohl für zukünftige Wartende als auch für Suchmaschinen, die den Code durchsuchen.

## Schritt 3 – Das DOCX mit Wiederherstellung laden

Jetzt werden wir **load docx with recovery** mit den gerade konfigurierten `LoadOptions` ausführen. Wenn die Datei beschädigt ist, repariert Aspose.Words sie entweder oder gibt eine Warnung aus, abhängig vom Modus.

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

Der `Document`‑Konstruktor übernimmt die schwere Arbeit. Im **PromptUser**‑Modus sehen Sie eine Konsolenaufforderung (oder eine benutzerdefinierte UI, wenn Sie sich in die `LoadOptions`‑Ereignisse einklinken), die fragt, ob fortgefahren werden soll. Im **Silent**‑Modus versucht die Methode ihr Bestes und fährt fort.

## Schritt 4 – Warnungen prüfen und den Benutzer auffordern

Aspose.Words protokolliert alle auftretenden Probleme in der `Warnings`‑Sammlung. Lassen Sie uns darüber iterieren und dem Benutzer die Möglichkeit geben, zu entscheiden, was als Nächstes zu tun ist.

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

Das obige Snippet **prompt user on error** auf konsolenfreundliche Weise. Wenn Sie eine Windows‑Forms‑ oder WPF‑App erstellen, ersetzen Sie `Console.ReadLine` durch eine `MessageBox` oder einen benutzerdefinierten Dialog.

## Schritt 5 – Mit dem wiederhergestellten Dokument arbeiten

An diesem Punkt befindet sich das Dokument im Speicher, so gut wie möglich von Aspose.Words repariert. Sie können nun den Inhalt lesen, eine saubere Kopie speichern oder jede gewünschte Manipulation durchführen.

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

Das Ausführen des vollständigen Programms mit einer beschädigten Datei erzeugt eine Konsolenausgabe, die etwa wie folgt aussieht:

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

Wenn die Datei tatsächlich in Ordnung war, sehen Sie „Document loaded without any warnings.“ und die saubere Kopie ist identisch mit der Quelle.

## Vollständiges funktionierendes Beispiel

Hier ist das gesamte Programm an einem Ort. Kopieren Sie es in ein neues Konsolenprojekt und drücken Sie **F5**.

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

Führen Sie es aus, beschädigen Sie eine Testdatei und beobachten Sie die Wiederherstellung in Aktion. 🎉

## Randfälle & Variationen

| Szenario | Was zu ändern | Warum |
|----------|----------------|-----|
| **Batch-Verarbeitung** (keine Benutzerinteraktion) | Setze `RecoveryMode = RecoveryMode.Silent` und entferne die Konsolenaufforderung. | Hält die Pipeline automatisch am Laufen. |
| **Strenge Validierung** (schnelles Scheitern) | Verwende `RecoveryMode.ThrowException`. Umhülle den Ladevorgang in ein try/catch und protokolliere die Ausnahme. | Garantiert, dass Sie nie mit einer teilweise reparierten Datei arbeiten. |
| **Benutzerdefinierte UI** (WinForms/WPF) | Abonniere `LoadOptions.LoadingProgress` oder nutze `Document.LoadOptions`‑Ereignisse, um einen Dialog anzuzeigen. | Bietet ein reichhaltigeres Erlebnis als die Konsole. |
| **Große Dokumente** (Speicherbeschränkungen) | Lade mit `LoadOptions.LoadFormat = LoadFormat.Docx` und erwäge `Document.SaveOptions`, um die Ausgabe zu streamen. | Verhindert OutOfMemory‑Ausnahmen. |

## Praktische Tipps (E‑E‑A‑T‑Signale)

- **Immer eine Sicherungskopie behalten** bevor Sie die Wiederherstellung versuchen; der Vorgang kann Teile der Datei überschreiben.  
- **Warnungen protokollieren** in einer Datei zur späteren Analyse; sie geben oft Aufschluss über die Ursache (z. B. fehlende Teile, beschädigtes XML).  
- **Mit verschiedenen Beschädigungsarten testen** – Datei kürzen, XML‑Tags beschädigen oder die ZIP‑Struktur ändern, um zu sehen, wie sich jeder Modus verhält.  
- **Aspose.Words regelmäßig aktualisieren**; neuere Versionen verbessern die Wiederherstellungsalgorithmen und fügen neue Warnungstypen hinzu.  
- **Mit Validierung kombinieren** – nach der Wiederherstellung führen Sie schnell `document.UpdateFields()` und `document.Save()` aus, um sicherzustellen, dass das Dokument voll funktionsfähig ist.

## Fazit

Sie wissen jetzt, wie Sie **recover corrupted document** Dateien in C# durch **set recovery mode**, **load docx with recovery** und **prompt user on error** wiederherstellen, wenn etwas schiefgeht. Das vollständige Beispiel demonstriert einen sauberen End‑zu‑End‑Ablauf, der in Konsolen‑Apps, Diensten oder UI‑Projekten funktioniert.

Nächste Schritte? Versuchen Sie, die Konsolenaufforderung durch einen modalen Dialog in einer WinForms‑App zu ersetzen, experimentieren Sie mit dem **Silent**‑Modus für Hintergrundjobs oder integrieren Sie die Wiederherstellungslogik in einen ASP.NET‑Datei‑Upload‑Endpunkt, sodass Benutzer beschädigte DOCX‑Dateien hochladen und sofort eine reparierte Version erhalten.

Viel Spaß beim Programmieren und möge Ihre Dokumente ganz bleiben!  

---

![Recover corrupted document example](/images/recover-corrupted-document.png "recover corrupted document")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}