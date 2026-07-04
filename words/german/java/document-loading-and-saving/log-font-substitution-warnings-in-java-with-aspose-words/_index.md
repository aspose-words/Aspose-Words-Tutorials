---
category: general
date: 2026-06-17
description: Protokollieren Sie Schriftart‑Substitutionswarnungen in Java mit Aspose.Words
  – erfassen Sie fehlende Schriftarten beim Laden des Dokuments und halten Sie Ihre
  Ausgabe konsistent.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: de
og_description: Protokollieren Sie Schriftart‑Substitutionswarnungen in Java mit Aspose.Words.
  Erfahren Sie, wie Sie fehlende‑Schriftart‑Warnungen beim Laden von Dokumenten erfassen
  und Ihre PDFs makellos halten.
og_title: Protokollieren von Schriftart-Substitutionswarnungen in Java – Vollständiger
  Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Schriftart‑Substitutionswarnungen in Java mit Aspose.Words protokollieren
url: /de/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Protokollieren von Schriftart‑Substitutionswarnungen in Java – Vollständige Anleitung

Haben Sie sich jemals gefragt, wie man **Schriftart‑Substitutionswarnungen** protokolliert, wenn ein Word‑Dokument eine Schriftart lädt, die Sie auf dem Server nicht haben? Sie sind nicht der Einzige, der sich über fehlende Schriftarten ärgert, die stillschweigend ausgetauscht werden. Die gute Nachricht? Aspose.Words for Java bietet Ihnen eine saubere Möglichkeit, diese Substitutionen sofort beim Laden eines Dokuments abzufangen.

In diesem Tutorial führen wir Sie durch ein praktisches Beispiel, das genau zeigt, wie man einen Warn‑Callback registriert, nach Schriftart‑Substitutions‑Warnungen filtert und sie in die Konsole (oder einen beliebigen Logger Ihrer Wahl) schreibt. Am Ende haben Sie ein wiederverwendbares Snippet, das Sie in jedes Java‑Projekt einbinden können, das **Aspose.Words Java** verwendet.

## Was Sie lernen werden

- Wie man **LoadOptions** konfiguriert, um Warnungen zu erfassen.
- Wie man ein **IWarningCallback** implementiert, das nur auf **font substitution**‑Ereignisse reagiert.
- Wie man ein Dokument sicher lädt und dabei eine klare Prüfspur fehlender Schriftarten beibehält.
- Tipps zum Erweitern der Lösung für dateibasierte Protokolle oder Überwachungssysteme.

### Voraussetzungen

- Java 8 oder neuer (der Code funktioniert auch mit Java 11+).
- Aspose.Words for Java Bibliothek (Version 23.10 oder neuer wird empfohlen).
- Eine Beispiel‑`.docx`‑Datei, die eine Schriftart referenziert, die nicht auf Ihrem Rechner installiert ist (z. B. `MissingFont.docx`).

Es werden keine zusätzlichen Frameworks benötigt – nur reines Java und die Aspose.JARs.

---

## Schritt 1: LoadOptions für Aspose.Words Java konfigurieren

Bevor Sie irgendwelche Warnungen abfangen können, benötigen Sie eine **LoadOptions**‑Instanz. Dieses Objekt teilt Aspose.Words mit, wie es sich beim Parsen der eingehenden Datei verhalten soll.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Warum ist dieser Schritt entscheidend? Ohne ein `LoadOptions`‑Objekt ersetzt die Bibliothek fehlende Schriftarten stillschweigend und Sie sehen keinen Hinweis. Durch das explizite Erstellen eines solchen Objekts öffnen Sie die Tür zu einem benutzerdefinierten **warning callback**, der genau das protokollieren kann, was Sie interessiert.

> **Pro‑Tipp:** Wenn Sie viele Dokumente stapelweise laden, verwenden Sie eine einzelne `LoadOptions`‑Instanz wieder, um unnötigen Objekt‑Overhead zu vermeiden.

---

## Schritt 2: Einen Warning‑Callback für Schriftart‑Substitution implementieren

Aspose.Words liefert das `IWarningCallback`‑Interface. Durch dessen Implementierung können Sie festlegen, was geschehen soll, wenn die Engine ein `WarningInfo` ausgibt. In unserem Fall wollen wir nur auf `WarningType.FONT_SUBSTITUTION` reagieren.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Ein paar Dinge, die Sie beachten sollten:

1. **Filtering** – Die `if`‑Anweisung stellt sicher, dass wir nicht relevante Warnungen (wie Layout‑Probleme) ignorieren und das Protokoll übersichtlich bleibt.
2. **Thread‑Sicherheit** – Der Callback wird im selben Thread ausgeführt, der das Dokument lädt, sodass für einfache Konsolenausgaben keine zusätzliche Synchronisation nötig ist. Schreiben Sie in einen gemeinsamen Logger, stellen Sie sicher, dass er thread‑sicher ist.
3. **Erweiterbarkeit** – Möchten Sie in eine Datei schreiben? Ersetzen Sie `System.out.println` durch `java.util.logging.Logger` oder ein Drittanbieter‑Logging‑Framework.

---

## Schritt 3: Das Dokument mit den konfigurierten Optionen laden

Jetzt, wo der Callback eingerichtet ist, laden Sie Ihre Word‑Datei. In dem Moment, in dem Aspose.Words das Dokument parst, löst jede fehlende Schriftart den oben definierten Callback aus.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Wenn die Quelldatei eine Schriftart referenziert, die nicht installiert ist, sehen Sie eine Ausgabe ähnlich wie:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Diese Zeile ist die **log font substitution warnings**, nach der Sie gesucht haben. Sie können nun darauf reagieren – z. B. einen Benutzer benachrichtigen, zu einem Ersatz‑Stylesheet wechseln oder einfach aus Compliance‑Gründen ein Protokoll führen.

---

## Schritt 4: Weiter mit der normalen Verarbeitung

Nach dem Laden verhält sich das Dokument wie jedes andere `Document`‑Objekt. Sie können problemlos Abschnitte inspizieren, Text extrahieren oder in PDF konvertieren. Das Protokollieren der Warnungen geschieht automatisch während des Ladevorgangs, sodass kein zusätzlicher Code nötig ist.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

Die Konsole zeigt nun sowohl die Schriftart‑Substitutionswarnung (falls vorhanden) **als auch** die Abschnittszahl, was bestätigt, dass das Dokument voll funktionsfähig ist.

---

## Erweiterte Tipps & Sonderfälle

### Protokollierung in eine Datei statt in die Konsole

Wenn Sie ein dauerhaftes Protokoll bevorzugen, ersetzen Sie den Aufruf `System.out.println` durch einen `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Denken Sie daran, `IOException` in Produktionscode korrekt zu behandeln.

### Mehrere Dokumente in einer Schleife erfassen

Beim Verarbeiten eines Ordners mit Dokumenten können Sie denselben Callback wiederverwenden:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Da der Callback an `loadOptions` angehängt ist, protokolliert jede Iteration automatisch alle Schriftart‑Substitutions‑Ereignisse.

### Umgang mit eingebetteten Schriftarten

Aspose.Words kann fehlende Schriftarten einbetten, wenn Sie dies aktivieren:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Selbst wenn das Einbetten aktiviert ist, wird der Warning‑Callback weiterhin ausgelöst, sodass Sie sehen, welche Schriftart ersetzt wurde.

---

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, sofort ausführbare Programm. Kopieren Sie es in eine Klasse namens `FontSubstitutionDiagnostics.java`, passen Sie den Dateipfad an und führen Sie es aus.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Erwartete Ausgabe** (unter der Annahme, dass das Quell‑Dokument eine fehlende Schriftart referenziert):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

Sowohl die Konsole als auch `font_substitution_log.txt` enthalten die Warnung, wodurch Sie eine zuverlässige Prüfspur erhalten.

---

## Fazit

Wir haben Ihnen gerade gezeigt, wie Sie **Schriftart‑Substitutionswarnungen** in Java mit Aspose.Words **protokollieren**. Durch das Konfigurieren von `LoadOptions`, das Einbinden eines `IWarningCallback` und das Laden des Dokuments erhalten Sie vollständige Sicht auf alle fehlenden‑Schriftart‑Ereignisse, die sonst unbemerkt bleiben könnten. Ab hier können Sie:

- Warnungen an einen zentralen Logging‑Dienst weiterleiten.
- Alarme für Qualitätssicherungs‑Pipelines auslösen.
- Diese Technik mit anderen **document loading**‑Strategien kombinieren, z. B. PDF‑Konvertierung oder Seriendruck.

Fühlen Sie sich frei zu experimentieren – ersetzen Sie den Konsolen‑Logger durch SLF4J, fügen Sie Zeitstempel hinzu oder senden Sie Alarme an ein Monitoring‑Dashboard. Das Grundmuster bleibt gleich, und Sie haben nun eine solide Grundlage für ein robustes Schriftart‑Handling in jedem Java‑basierten Dokument‑Workflow.

Haben Sie eine Variante, die Sie teilen möchten? Vielleicht haben Sie das mit Spring Boot oder einer Cloud‑Funktion integriert. Hinterlassen Sie unten einen Kommentar, und lassen Sie uns die Diskussion fortsetzen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}