---
category: general
date: 2026-06-20
description: Wie man in Aspose.Words Java einen Callback festlegt, um fehlende Schriftarten
  zu erkennen und das Laden des Dokuments anzupassen. Erfahren Sie Schritt für Schritt,
  wie Sie Warnungen zur Schriftart‑Substitution behandeln.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: de
og_description: Wie man in Aspose.Words Java einen Callback festlegt, um fehlende
  Schriftarten zu erkennen, Substitutionen zu behandeln und das Laden von Dokumenten
  anzupassen. Vollständige Anleitung mit Code.
og_title: Wie man einen Callback festlegt – Fehlende Schriftarten in Aspose.Words
  Java erkennen
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: Wie man einen Callback in Aspose.Words Java festlegt – Erkennen und Behandeln
  fehlender Schriftarten
url: /de/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man einen Callback in Aspose.Words Java setzt – Fehlende Schriftarten erkennen und behandeln

Haben Sie sich schon einmal gefragt, **wie man einen Callback** in Aspose.Words Java setzt, um fehlende Schriftarten zu entdecken, bevor sie Ihr PDF oder DOCX ruinieren? Sie sind nicht allein. Fehlende‑Schrift‑Warnungen können das Layout stillschweigend beschädigen, und ohne einen geeigneten Warn‑Callback bemerken Sie das Problem vielleicht erst, wenn das fertige Dokument fehlerhaft aussieht.  

In diesem Tutorial führen wir Sie durch ein komplettes, sofort ausführbares Beispiel, das **fehlende Schriftarten erkennt**, **fehlende Schriftarten** elegant behandelt und Ihnen zeigt, wie Sie **das Laden von Dokumenten** mit einem Warn‑Callback **anpassen** können. Am Ende haben Sie eine eigenständige Java‑Klasse, die Sie in jedes Projekt einbinden können – ohne zusätzliche Dokumentationssuche.

## Was Sie benötigen

- Java 8 oder neuer (der Code funktioniert auch mit Java 11+)  
- Aspose.Words für Java Bibliothek (Version 23.9 oder später)  
- Eine DOCX‑Datei, die eine Schriftart referenziert, die Sie nicht installiert haben (z. B. eine firmenspezifische Schrift)  

Wenn Sie Aspose.Words noch nicht zu Ihrem Maven‑Projekt hinzugefügt haben, fügen Sie einfach Folgendes ein:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Das war’s – keine zusätzlichen Plugins, keine nativen Abhängigkeiten.

---

## Schritt 1: Das WarningCallback‑Mechanismus verstehen

Der **Warn‑Callback** ist Aspose.Words’ Art, Sie zu alarmieren, wenn beim Laden oder Speichern eines Dokuments etwas Unerwartetes passiert. Durch die Implementierung von `IWarningCallback` erhalten Sie die volle Kontrolle darüber, was protokolliert, ignoriert oder sogar in eine Ausnahme umgewandelt wird.

> **Warum das wichtig ist:**  
> Wenn eine Schriftart fehlt, ersetzt Aspose sie durch eine Ersatzschrift. Das visuelle Ergebnis kann stark abweichen, besonders bei stark gebrandeten PDFs. Durch das Abfangen von `WarningType.FONT_SUBSTITUTION` können Sie den genauen Schriftartnamen protokollieren, entscheiden, ob Sie abbrechen, oder programmgesteuert Ihre eigene Ersatzschrift setzen.

---

## Schritt 2: Eine LoadOptions‑Instanz erstellen

`LoadOptions` ist der Einstiegspunkt, um das Laden von Dokumenten anzupassen. Sie hängen den Callback an dieses Objekt, bevor Sie die Datei tatsächlich laden.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Zu diesem Zeitpunkt ist `loadOptions` nur ein einfacher Container – es passiert noch nichts. Die eigentliche Magie beginnt, wenn wir den Callback einbinden.

---

## Schritt 3: Den Callback implementieren und anhängen

Unten finden Sie eine kompakte anonyme Klasse, die `IWarningCallback` implementiert. Sie gibt eine freundliche Zeile auf der Konsole aus, sobald eine Schriftart‑Ersetzung stattfindet.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Pro‑Tipp:** Wenn Sie **fehlende Schriftarten** durch eine Ersatzschrift behandeln möchten, können Sie zusätzlich `FontSettings` auf den `LoadOptions` setzen und fehlende Schriftarten einer bekannten Ersatzschrift zuordnen.

---

## Schritt 4: Das Dokument mit Ihren benutzerdefinierten Optionen laden

Jetzt, wo der Callback verkabelt ist, laden Sie das Dokument. Wenn die Datei eine Schriftart referenziert, die Sie nicht besitzen, wird die Warnung ausgegeben.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

Wenn Sie das Programm ausführen, könnte die Konsole Folgendes anzeigen:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Diese Zeile beweist, dass Sie **fehlende Schriftarten erfolgreich erkannt** haben und nun in der Lage sind, **fehlende Schriftarten** nach Belieben zu **behandeln**.

---

## Schritt 5: Optional – Fehlende Schriftarten durch eine bekannte Schrift ersetzen

Wenn Sie fehlende Schriftarten automatisch durch z. B. `Times New Roman` ersetzen möchten, können Sie ein `FontSettings`‑Objekt hinzufügen:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Jetzt wird das Dokument geladen, und jede Referenz zu `MyCustomFont` wird stillschweigend durch `Times New Roman` ausgetauscht. Die Konsole gibt weiterhin aus, was ersetzt wurde, sodass Sie im Bilde bleiben.

---

## Vollständiges funktionierendes Beispiel

Unten finden Sie eine einzelne Java‑Klasse, die alle oben genannten Schritte kombiniert. Kopieren Sie sie in Ihre IDE, passen Sie `docPath` an und führen Sie sie aus.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Erwartete Ausgabe**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Sie haben nun eine reproduzierbare Methode, um **fehlende Schriftarten zu erkennen**, **fehlende Schriftarten zu behandeln** und **das Laden von Dokumenten** zu **customizen** – alles, indem Sie **wie man einen Callback setzt** korrekt anwenden.

---

## Häufig gestellte Fragen

### Was, wenn das Programm beim Fehlen einer Schriftart das Laden abbrechen soll?

Werfen Sie innerhalb der `warning`‑Methode eine Ausnahme:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Der `catch`‑Block unten fängt sie ab, und Sie können entscheiden, wie Sie protokollieren oder den Benutzer alarmieren.

### Funktioniert das auch für PDFs, die aus DOCX erzeugt wurden?

Absolut. Der Callback wird während der **Lade‑Phase** ausgelöst, die für alle Ausgabeformate identisch ist (`save` nach PDF, DOCX, HTML usw.). Solange Sie das Quell‑Dokument mit denselben `LoadOptions` laden, fangen Sie fehlende Schriftarten, bevor sie das finale PDF beeinflussen.

### Kann ich andere Warnungstypen erfassen (z. B. Bildkonvertierung)?

Ja – `WarningInfo.getWarningType()` lässt sich mit anderen Enums wie `WarningType.IMAGE_CONVERSION` vergleichen. Fügen Sie einfach weitere `if`‑Zweige im Callback hinzu.

### Gibt es Performance‑Einbußen?

Vernachlässigbar. Der Callback läuft synchron während des Ladens, und die zusätzlichen Prüfungen sind leichtgewichtig. Laden Sie tausende Dokumente, möchten Sie vielleicht Warnungen in der Produktion deaktivieren, indem Sie `loadOptions.setWarningCallback(null);` setzen.

---

## Visuelle Übersicht

![Beispiel für das Setzen eines Callbacks in Aspose.Words Java](https://example.com/images/callback-diagram.png "Beispiel für das Setzen eines Callbacks in Aspose.Words Java")

*Das Diagramm veranschaulicht den Ablauf: `LoadOptions` → `IWarningCallback` → Dokumenten‑Laden → Behandlung von Schriftart‑Ersetzungen.*

---

## Zusammenfassung

Wir haben **wie man einen Callback** in Aspose.Words Java setzt, **fehlende Schriftarten erkennt**, praktische Wege gezeigt, **fehlende Schriftarten zu behandeln**, und erklärt, wie man das **Laden von Dokumenten** mit `LoadOptions` **anpasst**.  

Mit diesem Wissen können Sie Ihre Dokumenten‑Pipelines vor stillen Schriftart‑Ersetzungen schützen, das Branding intakt halten und Ihren Benutzern klare Rückmeldungen geben, wenn etwas schiefgeht.

### Was kommt als Nächstes?

- Erkunden Sie **Schriftart‑Ersetzungstabellen** für die Massenzuordnung vieler fehlender Schriftarten.  
- Kombinieren Sie diesen Callback mit **Dokumenten‑Validierung**, um Style‑Guidelines durchzusetzen.  
- Probieren Sie **benutzerdefinierte Warn‑Callbacks** aus, die in eine Log‑Datei oder ein Monitoring‑System schreiben statt `System.out`.  

Experimentieren Sie gern und teilen Sie uns mit, wie Sie den Callback für Ihre eigenen Projekte angepasst haben. Viel Spaß beim Coden!

---

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}