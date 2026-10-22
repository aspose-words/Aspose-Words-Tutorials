---
category: general
date: 2026-05-30
description: Registrieren Sie einen Warn‑Callback in Java, um fehlende Schriftarten
  zu verfolgen und das Laden von Dokumenten mit Aspose.Words anzupassen. Erfahren
  Sie die vollständige Schritt‑für‑Schritt‑Lösung.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: de
og_description: Registrieren Sie einen Warnungs‑Callback in Java, um fehlende Schriftarten
  zu verfolgen und das Laden von Dokumenten anzupassen. Vollständige Anleitung mit
  Code und Erklärungen.
og_title: Warn-Callback in Java registrieren – Fehlende Schriftarten verfolgen
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Warn-Callback in Java registrieren – Fehlende Schriftarten verfolgen
url: /de/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Warnungs‑Callback in Java registrieren – Fehlende Schriftarten verfolgen

Haben Sie sich schon einmal gefragt, wie Sie **fehlende Schriftarten** beim Laden eines Word‑Dokuments mit Aspose.Words für Java **verfolgen** können? Vielleicht haben Sie diese stillen Schriftart‑Ersetzungen bemerkt und sich gefragt: „Was ist mit meinem Layout passiert?“ Die gute Nachricht: Sie müssen nicht raten. Durch **Registrieren eines Warnungs‑Callbacks** können Sie jedes Schriftart‑Ersetzungs‑Ereignis im Moment des Lesevorgangs erfassen und zudem **das Laden des Dokuments anpassen**, um es in Ihre Pipeline zu integrieren.

> **Was Sie erhalten:**  
> • Ein vollständiges Java‑Programm mit Aspose.Words  
> • Schritt‑für‑Schritt‑Erklärungen zu jeder Zeile  
> • Tipps zum Umgang mit Sonderfällen wie verschlüsselten Dateien oder großen Stapeln  
> • Einen schnellen Sanity‑Check, den Sie für jede `.docx`‑Datei ausführen können

## Voraussetzungen

Bevor wir starten, stellen Sie sicher, dass Sie Folgendes haben:

- **Java 17** (oder ein aktuelles JDK) installiert und `JAVA_HOME` gesetzt.  
- **Aspose.Words für Java** JAR in Ihrem Klassenpfad. Die neueste Version erhalten Sie aus dem Maven Central‑Repository:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Ein Beispiel‑Word‑Dokument (`input.docx`), von dem Sie vermuten, dass es Schriftarten enthält, die nicht auf Ihrem Rechner installiert sind.  
- Eine IDE oder ein Build‑Tool für die Kommandozeile (Maven/Gradle), mit dem Sie sich auskennen.

Das ist alles. Keine zusätzlichen Schriftarten, keine externen Dienste – nur reines Java und Aspose.Words.

## Warum einen Warnungs‑Callback registrieren?

Betrachten Sie den **Warnungs‑Callback** als Überwachungskamera für Ihren Dokument‑Ladevorgang. Wenn Aspose.Words auf ein fehlendes Glyph stößt, wirft es keine Ausnahme, sondern ersetzt stillschweigend durch eine Ersatzschriftart. Diese stille Ersetzung kann Ihr Layout zerstören, besonders in branding‑kritischen PDFs oder Rechnungen. Durch das Registrieren eines Callbacks können Sie:

1. **Echtzeit‑Einblick erhalten** – jede `FONT_SUBSTITUTION`‑Warnung wird sofort geliefert.  
2. **Protokollieren oder reagieren** – Sie können in eine Datei schreiben, einen Alarm auslösen oder die Schriftart programmgesteuert ersetzen.  
3. **Sauberes Ergebnis bewahren** – zu wissen, welche Schriftarten fehlen, ermöglicht es Ihnen, das Quell‑Dokument vor der Veröffentlichung zu korrigieren.

Kurz gesagt, der Callback verwandelt ein verborgenes Problem in ein sichtbares, wodurch Ihre Dokument‑Pipeline deutlich zuverlässiger wird.

## Schritt 1 – `LoadOptions` erstellen, um das Laden des Dokuments anzupassen

Das Erste, was wir tun, ist die Instanzierung von `LoadOptions`. Dieses Objekt ist das Tor zu allen Anpassungen zur Ladezeit, von der Passwortbehandlung bis zu unserer **Registrierung des Warnungs‑Callbacks**.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

Warum nicht einfach `new Document("file.docx")` aufrufen? Ohne `LoadOptions` verlieren Sie die Möglichkeit, in die Ladevorgänge einzugreifen. `LoadOptions` ist der einzige Ort, an dem Aspose.Words Ihnen erlaubt, das **Laden des Dokuments anzupassen**.

## Schritt 2 – Einen Warnungs‑Callback registrieren, um fehlende Schriftarten zu verfolgen

Jetzt kommt der Star der Show: wir **registrieren einen Warnungs‑Callback**, der `IWarningCallback` implementiert. In der `warning`‑Methode filtern wir nach `WarningType.FONT_SUBSTITUTION` und geben eine hilfreiche Meldung aus.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Ein paar Dinge sind zu beachten:

- **Warum `IWarningCallback`?** – Das ist das Interface, das Aspose.Words für alle Warnungstypen verwendet und Ihnen einen einzigen Einstiegspunkt für zahlreiche mögliche Probleme bietet.  
- **Filtern ist entscheidend** – Ohne die `if`‑Prüfung würden Sie Warnungen zu fehlenden Bildern, veralteten Features usw. sehen, was Ihre Logs verstopft.  
- **Thread‑Sicherheit** – Der Callback läuft im selben Thread, der das Dokument lädt, sodass Sie gemeinsam genutzte Strukturen sicher aktualisieren können, falls Sie Ergebnisse später aggregieren möchten.

Dieses Snippet **registriert den Warnungs‑Callback**, und ab diesem Moment wird jedes fehlende‑Schriftart‑Ereignis auf `stdout` ausgegeben. Das ist das Kernstück, um **fehlende Schriftarten zu verfolgen**.

## Schritt 3 – Das Dokument mit den konfigurierten `LoadOptions` laden

Mit dem Callback im Einsatz laden wir nun die Datei. Wenn das Dokument eine Schriftart referenziert, die Sie nicht besitzen, wird der Callback ausgelöst, bevor das Dokument‑Objekt vollständig erstellt ist.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Ersetzen Sie `YOUR_DIRECTORY` durch den tatsächlichen Pfad auf Ihrem Rechner. Der `Document`‑Konstruktor liest die Datei, wendet ggf. ein Passwort an (wenn Sie eines in `loadOptions` gesetzt haben) und löst den Warnungs‑Callback für jede fehlende Schriftart aus. Sie sehen Ausgaben wie:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Diese Zeile beweist, dass Sie **fehlende Schriftarten erfolgreich verfolgen**.

## Schritt 4 – Weiterverarbeitung des Dokuments (optional)

In diesem Stadium können Sie das Dokument nach Belieben manipulieren – Text ersetzen, Bilder einfügen oder sogar programmgesteuert die ersetzten Schriftarten austauschen. Der Callback hat Ihnen bereits eine Liste problematischer Schriftarten geliefert, sodass Sie z. B. eine Ersatzschriftart einbetten könnten:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Sie können diesen Block überspringen, wenn Sie ausschließlich **fehlende Schriftarten verfolgen** möchten. Wichtig ist, dass Sie jetzt die Informationen besitzen, um fundierte Entscheidungen zu treffen.

## Schritt 5 – Das verarbeitete Dokument speichern

Abschließend persistieren wir das Dokument. Sie können das Original überschreiben, an einem neuen Ort speichern oder nach PDF exportieren – alles ohne die zuvor erfassten Warnungsdaten zu verlieren.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Das Ausführen der gesamten Klasse erzeugt Konsolenausgaben für jede fehlende Schriftart und eine neue Datei namens `processed.docx` im selben Ordner.

## Vollständiges funktionierendes Beispiel

Unten finden Sie die komplette Java‑Klasse, die Sie in Ihre IDE kopieren‑und‑einfügen können. Sie enthält alles, was wir besprochen haben, plus eine kleine `main`‑Methode als Wrapper.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Erwartete Ausgabe

Wenn Sie das Programm gegen ein Dokument ausführen, das eine nicht installierte Schriftart verwendet, sehen Sie etwa Folgendes:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Enthält das Dokument **keine fehlenden Schriftarten**, bleibt die Konsole still, bis die abschließende Zeile „Document saved successfully.“ erscheint – genau das erwartete Verhalten einer gut implementierten **Registrierung eines Warnungs‑Callbacks**.

## Profi‑Tipps & häufige Stolperfallen

- **Mehrere Callbacks?** – Aspose.Words erlaubt nur einen Warnungs‑Handler. Wenn Sie sowohl in eine Datei als auch in die Konsole schreiben wollen, implementieren Sie einen zusammengesetzten Callback, der die Warnung an mehrere Ziele weiterleitet.  
- **Große Stapel** – Beim Verarbeiten von Hunderten Dateien sollten Sie eine einzige `LoadOptions`‑Instanz wiederverwenden; das Erzeugen pro Datei verursacht unnötigen Overhead.  
- **Verschlüsselte Dokumente** – Setzen Sie das Passwort in `LoadOptions`, bevor Sie laden, sonst erhalten Sie eine `IncorrectPasswordException`, bevor der Callback überhaupt ausgelöst wird.  
- **Performance** – Der Callback läuft synchron. Wenn Sie in einen Remote‑Service protokollieren, puffern Sie die Meldungen und schreiben sie nach Abschluss des Ladevorgangs, um I/O‑Engpässe zu vermeiden.  
- **Schriftart‑Fallback** – Sie können auch eine eigene `FontSource`‑Sammlung bereitstellen, wenn Sie proprietäre Schriftarten haben, die Aspose.Words vor dem System‑Fallback berücksichtigen soll.

## Fazit

Sie haben gerade gelernt, wie man in Java **einen Warnungs‑Callback registriert**, effektiv **fehlende Schriftarten verfolgt** und das **Laden des Dokuments anpasst** mit Aspose.Words. Die Lösung ist eigenständig, läuft mit einer einzigen `main`‑Methode und gibt Ihnen sofortige Sichtbarkeit auf jede Schriftart‑Ersetzung, die sonst unbemerkt bleiben würde.

Nächste Schritte? Erweitern Sie den Callback, um Warnungen in einer CSV‑Datei für Auditzwecke zu schreiben, oder kombinieren Sie ihn mit einem Batch‑Processor, der fehlende Schriftarten automatisch einbettet. Sie können auch andere Warnungstypen wie `IMAGE_SUBSTITUTION` oder `DEPRECATED_FEATURE` erkunden – das gleiche Muster gilt.

Viel Spaß beim Coden, und mögen Ihre Dokumente stets exakt so rendern, wie Sie es beabsichtigen!

![Diagramm zum Registrieren des Warnungs-Callbacks](register-warning-callback.png "Ablaufdiagramm des Warnungs-Callback‑Registrierens")


## Was sollten Sie als Nächstes lernen?

- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Customize Theme Colors & Fonts in Aspose.Words Java: A Comprehensive Guide](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}