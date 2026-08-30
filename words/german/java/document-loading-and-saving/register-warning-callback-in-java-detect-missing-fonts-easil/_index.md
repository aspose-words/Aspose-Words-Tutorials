---
category: general
date: 2026-07-03
description: Registrieren Sie einen Warnungs-Callback in Java, um fehlende Schriftarten
  beim Verarbeiten von Word‑Dokumenten zu erkennen. Erfahren Sie mehr über die Warnungsbehandlung
  von Aspose.Words und die Erkennung von Schriftart‑Substitutionen.
draft: false
keywords:
- register warning callback
- detect missing fonts
- font substitution warning
- Aspose.Words warning callback
- Java missing font detection
- document font handling
language: de
og_description: Registrieren Sie einen Warnungs‑Callback in Java, um fehlende Schriftarten
  zu erkennen. Dieser Leitfaden zeigt, wie Sie Warnungen bei Schriftart‑Substitution
  mit Aspose.Words erfassen.
og_title: Warnungs‑Callback in Java registrieren – Fehlende Schriftarten erkennen
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  headline: Register warning callback in Java – Detect missing fonts easily
  type: TechArticle
- description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  name: Register warning callback in Java – Detect missing fonts easily
  steps:
  - name: Why this matters
    text: '* **Visibility:** Without a callback, the substitution happens silently,
      and you might ship a document with the wrong appearance. * **Automation:** In
      batch pipelines you can log every missing‑font incident and later feed the list
      to a font‑installation script. * **Compliance:** Some industries (e.g'
  - name: Expected console output
    text: 'Assuming `input.docx` references the font *“Comic Sans MS”* which isn’t
      installed, you’ll see something like:'
  - name: Multiple missing fonts
    text: If a document references several unavailable fonts, the callback will fire
      once per font. You can aggregate the messages into a list if you need a summary
      report later.
  - name: Controlling substitution behavior
    text: 'Sometimes you *do* want to force a particular fallback font. Use `FontSettings`
      before loading the document:'
  - name: Performance considerations
    text: 'Registering a warning callback introduces a tiny overhead—only a few nanoseconds
      per warning. In high‑throughput services (e.g., converting thousands of docs
      per hour) the impact is negligible. However, if you’re processing millions,
      consider disabling warnings after you’ve verified the font set is '
  - name: Cross‑platform notes
    text: The callback works identically on Windows, macOS, and Linux. The only difference
      is the set of fonts available on each OS. If you run the same job on multiple
      agents, you might see different substitution messages. To keep results deterministic,
      ship a **custom font folder** and point Aspose.Words to
  type: HowTo
tags:
- Aspose.Words
- Java
- Fonts
title: Warnungs‑Callback in Java registrieren – Fehlende Schriftarten leicht erkennen
url: /de/java/document-loading-and-saving/register-warning-callback-in-java-detect-missing-fonts-easil/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Warnungs‑Callback in Java registrieren – Fehlende Schriftarten einfach erkennen

Haben Sie sich jemals gefragt, wie man einen **Warnungs‑Callback registriert**, um **fehlende Schriftarten** beim Konvertieren oder Bearbeiten von Word‑Dokumenten zu **erkennen**? Sie sind nicht allein. Fehlende Schriftarten können stillschweigend Layouts beschädigen, einen eleganten Bericht in ein wirres Durcheinander verwandeln, und die meisten Entwickler merken es nicht, bis das endgültige PDF fehlerhaft aussieht.  

In diesem Tutorial gehen wir Schritt für Schritt durch ein vollständiges, sofort ausführbares Beispiel, das Ihnen genau zeigt, wie Sie in das Warnsystem von Aspose.Words for Java einsteigen, diese lästigen Schriftart‑Ersetzungs‑Warnungen abfangen und sie protokollieren oder nach Bedarf reagieren können. Keine vagen „siehe die Docs“ Abkürzungen – nur reiner Copy‑and‑Paste‑Code und die Begründung hinter jeder Zeile.

## Voraussetzungen

Bevor wir starten, stellen Sie sicher, dass Sie Folgendes haben:

* **Java 17** (oder ein aktuelles JDK) installiert und `JAVA_HOME` gesetzt.  
* **Aspose.Words for Java** JAR (von der offiziellen Website herunterladen oder über Maven beziehen).  
* Eine Beispiel‑`.docx`‑Datei, die eine Schriftart referenziert, die **nicht** auf Ihrem Rechner installiert ist – das löst die Warnung aus.  
* Ihre bevorzugte IDE oder ein einfacher Texteditor und Befehlszeilen‑Build‑Tools.

Das war’s. Keine zusätzlichen Frameworks, keine externen Dienste. Bereit? Dann legen wir los.

## Schritt 1: Projekt einrichten und Aspose.Words hinzufügen

Wenn Sie Maven verwenden, fügen Sie die folgende Abhängigkeit zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- use the latest stable version -->
</dependency>
```

Für Gradle fügen Sie das Folgende in `build.gradle` ein:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

Wenn Sie den manuellen Weg bevorzugen, legen Sie einfach die `aspose-words-24.10.jar` in Ihren Klassenpfad.  
**Pro‑Tipp:** Platzieren Sie die JAR-Datei neben Ihrem `src`‑Ordner; das vereinfacht später den `javac`‑Befehl.

## Schritt 2: Dokument laden, das fehlende Schriftarten enthalten könnte

Das Erste, was Sie tun, ist ein `Document`‑Objekt zu erstellen, das auf die Quelldatei zeigt. Dieser Schritt ist unkompliziert, aber hier scannt die Bibliothek die Datei und *möglicherweise* entdeckt fehlende Schriftarten.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // Adjust the path to point at your test document
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – Aspose.Words will start parsing it now
        Document doc = new Document(inputPath);
```

Hier ist `Document` der Einstiegspunkt für alle Aspose.Words‑Operationen. Wenn der Konstruktor ausgeführt wird, analysiert die Bibliothek das XML des Dokuments, löst Schriftarten auf und, falls Schriftarten nicht verfügbar sind, legt sie *eine* Warnung in die Warteschlange, die wir später abfangen können.

## Schritt 3: Warnungs‑Callback registrieren, um Schriftart‑Ersetzungs‑Warnungen abzufangen

Jetzt zum Star der Show: **Warnungs‑Callback registrieren**. Aspose.Words ermöglicht es Ihnen, eine Implementierung des `IWarningCallback`‑Interfaces einzubinden. Jedes Mal, wenn die Engine auf eine Situation stößt, die eine Markierung wert ist – etwa eine fehlende Schriftart – ruft sie Ihre `warning`‑Methode auf.

```java
        // Register the warning callback
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We’re only interested in font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                }
            }
        });
```

### Warum das wichtig ist

* **Sichtbarkeit:** Ohne Callback erfolgt die Ersetzung stillschweigend, und Sie könnten ein Dokument mit falschem Aussehen ausliefern.  
* **Automatisierung:** In Batch‑Pipelines können Sie jeden Vorfall einer fehlenden Schriftart protokollieren und die Liste später an ein Schriftart‑Installations‑Skript übergeben.  
* **Compliance:** Einige Branchen (z. B. Rechtswesen) verlangen den Nachweis, dass die Originalschriftarten verwendet oder ordnungsgemäß ersetzt wurden.

Beachten Sie, dass wir nach `WarningType.FONT_SUBSTITUTION` filtern. Aspose.Words gibt viele Warnungstypen aus – Layout‑Überlauf, veraltete Features usw. – aber wir interessieren uns nur für die, die uns mitteilen, dass eine Schriftart fehlte. Das hält die Konsole sauber und fokussiert auf das Ziel **fehlende Schriftarten erkennen**.

## Schritt 4: Dokument speichern und den Callback auslösen lassen

Wenn Sie schließlich `save` aufrufen, beendet die Engine das verzögerte Laden und löst den Warnungs‑Callback für jede fehlende Schriftart aus, die sie während des Speicher‑Vorgangs entdeckt hat.

```java
        // Save the document – this is where the warning callback gets invoked
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("✅ Document saved to " + outputPath);
    }
}
```

### Erwartete Konsolenausgabe

Angenommen, `input.docx` referenziert die Schriftart *„Comic Sans MS“*, die nicht installiert ist, dann sehen Sie etwa Folgendes:

```
⚠️ Font substituted: Font 'Comic Sans MS' is not available. Substituted with 'Arial'.
✅ Document saved to YOUR_DIRECTORY/output.docx
```

Wenn das Quell‑Dokument bereits nur installierte Schriftarten enthält, erscheint die Warnungszeile einfach nie – das bedeutet, dass **fehlende Schriftarten erkennen** stillschweigend erfolgreich war.

![Konsolenausgabe, die den registrierten Warnungs‑Callback in Aktion zeigt und fehlende Schriftarten erkennt](register-warning-callback-output.png)

*Bild‑Alt‑Text: Konsolenausgabe, die den registrierten Warnungs‑Callback in Aktion zeigt und fehlende Schriftarten erkennt*

## Schritt 5: Umgang mit Sonderfällen und bewährte Praktiken

### Mehrere fehlende Schriftarten

Wenn ein Dokument mehrere nicht verfügbare Schriftarten referenziert, wird der Callback einmal pro Schriftart ausgelöst. Sie können die Meldungen zu einer Liste zusammenfassen, falls Sie später einen Zusammenfassungsbericht benötigen.

```java
List<String> missingFonts = new ArrayList<>();
doc.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        missingFonts.add(info.getDescription());
    }
});
// After saving
if (!missingFonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    missingFonts.forEach(System.out::println);
}
```

### Steuerung des Ersetzungs‑Verhaltens

Manchmal möchten Sie *wirklich* eine bestimmte Ersatzschriftart erzwingen. Verwenden Sie `FontSettings` vor dem Laden des Dokuments:

```java
FontSettings settings = new FontSettings();
settings.setSubstitutionSettings(new FontSubstitutionSettings()
        .addSubstitutes("Comic Sans MS", "Times New Roman"));
doc.setFontSettings(settings);
```

Der Callback wird weiterhin ausgelöst, aber Sie wissen genau, welche Schriftart verwendet wird.

### Leistungs‑Überlegungen

Das Registrieren eines Warnungs‑Callbacks verursacht einen winzigen Overhead – nur ein paar Nanosekunden pro Warnung. In hochdurchsatzfähigen Diensten (z. B. Tausende Dokumente pro Stunde konvertieren) ist die Auswirkung vernachlässigbar. Verarbeiten Sie jedoch Millionen, sollten Sie in Erwägung ziehen, Warnungen zu deaktivieren, nachdem Sie bestätigt haben, dass das Schriftart‑Set vollständig ist:

```java
doc.setWarningCallback(null); // turn off after initial scan
```

### Plattformübergreifende Hinweise

Der Callback funktioniert identisch unter Windows, macOS und Linux. Der einzige Unterschied ist die Menge der auf jedem OS verfügbaren Schriftarten. Wenn Sie denselben Job auf mehreren Agenten ausführen, können unterschiedliche Ersetzungs‑Meldungen auftreten. Um deterministische Ergebnisse zu erhalten, liefern Sie einen **benutzerdefinierten Schriftarten‑Ordner** aus und verweisen Aspose.Words darauf mittels `FontSettings.setFontsFolder("path/to/fonts", true);`.

## Vollständiges, ausführbares Beispiel

Unten finden Sie die gesamte Java‑Klasse, die Sie in `src/main/java/FontWarningDemo.java` kopieren und einfügen können. Sie enthält alle Importe, Fehlerbehandlungen und Kommentare, die Sie benötigen, um sie sofort auszuführen.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Demonstrates how to register a warning callback in Aspose.Words for Java
 * to detect missing fonts during document processing.
 */
public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Paths – adjust to your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // 2️⃣ Load the document (parsing begins here)
        Document doc = new Document(inputPath);

        // 3️⃣ Optional: set a custom font folder if you ship fonts with your app
        // FontSettings fs = new FontSettings();
        // fs.setFontsFolder("fonts", true);
        // doc.setFontSettings(fs);

        // 4️⃣ Register the warning callback to catch missing‑font warnings
        List<String> missingFonts = new ArrayList<>();
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Log to console
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                    // Collect for later reporting
                    missingFonts.add(info.getDescription());
                }
            }
        });

        // 5️⃣ Save the document – triggers the callback
        doc.save(outputPath);
        System.out.println("✅ Document saved to " + outputPath);

        // 6️⃣ Post‑save reporting (if any fonts were missing)
        if (!missingFonts.isEmpty()) {
            System.out.println("\nSummary of missing fonts:");
            missingFonts.forEach(System.out::println);
        } else {
            System.out.println("\nNo missing fonts detected.");
        }
    }
}
```

Kompilieren und ausführen:

```bash
javac -cp "aspose-words-24.10.jar" FontWarningDemo.java
java -cp ".:aspose-words-24.10.jar" FontWarningDemo
```

Sie sollten die Warnungszeilen (falls vorhanden) sehen, gefolgt von der Erfolgsmeldung.

## Fazit

Sie haben gerade **gelernt, wie man einen Warnungs‑Callback** in Java **registriert**, um **fehlende Schriftarten** bei der Arbeit mit Aspose.Words zu **erkennen**. Durch das Einbinden in das Warnsystem der Bibliothek erhalten Sie vollständige Sichtbarkeit auf Schriftart‑Ersetzungs‑Ereignisse, können sie für Compliance protokollieren und bei Bedarf sogar programmgesteuert Schriftarten ersetzen.

Ab hier könnten Sie folgendes erkunden:

* **Fehlende Schriftarten** über einen Stapel von Dateien hinweg mit einer Schleife oder Parallel‑Streams erkennen.  
* Den Callback in ein Logging‑Framework (SLF4J, Log4j) integrieren für produktionsreife Berichte.  
* `FontSettings` verwenden, um eine Unternehmens‑Schriftarten‑Palette durchzusetzen und unerwünschte Ersatzschriften zu vermeiden.

Probieren Sie es aus – tauschen Sie das Eingabedokument aus, testen Sie verschiedene Szenarien mit fehlenden Schriftarten und beobachten Sie, wie der Callback reagiert. Wenn Sie auf Eigenheiten stoßen, hinterlassen Sie unten einen Kommentar; happy coding!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Erfassung von Schriftart‑Ersetzungs‑Warnungen in Java mit Aspose.Words – Komplett‑Leitfaden](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warnungs‑Callback in Word‑Dokument](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose Words Java Callback – benutzerdefinierte Speicherungen](/words/hindi/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}