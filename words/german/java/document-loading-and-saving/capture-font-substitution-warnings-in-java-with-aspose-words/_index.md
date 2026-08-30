---
category: general
date: 2026-06-27
description: Erfahren Sie, wie Sie Schriftart‑Ersetzungshinweise in Java mit Aspose.Words
  erfassen können. Dieses Schritt‑für‑Schritt‑Tutorial behandelt außerdem Warn‑Callbacks
  und die Verwendung von LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: de
og_description: Erfassen Sie Schriftart‑Substitutionswarnungen in Java mit Aspose.Words.
  Folgen Sie dieser Anleitung, um Warnungs‑Callbacks einzurichten, LoadOptions zu
  verwenden und fehlende Schriftarten zu behandeln.
og_title: Erfassung von Schriftart‑Substitutionswarnungen in Java – Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Erfassung von Schriftart-Substitutionswarnungen in Java mit Aspose.Words –
  Vollständiger Leitfaden
url: /de/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Font-Substitutionswarnungen in Java mit Aspose.Words erfassen – Vollständige Anleitung

Haben Sie jemals **Font-Substitutionswarnungen** erfassen müssen, während Sie ein DOCX laden, das exotische Schriftarten verwendet? Sie sind nicht allein. In vielen realen Projekten – denken Sie an automatisierte Berichtsgeneratoren oder Stapel‑Dokumentenkonverter – führen fehlende Schriftarten zu stillen Substitutionen, die die Layout‑Treue ruinieren.  

Glücklicherweise bietet Aspose.Words eine saubere Möglichkeit, diese Warnungen zu beobachten. In diesem Tutorial gehen wir die Konfiguration von **LoadOptions**, das Einbinden eines **Aspose.Words warning callback** und das Ausgeben jeder *Font‑Substitution*-Meldung in die Konsole durch. Am Ende wissen Sie genau, wann eine Schriftart ausgetauscht wurde und wie Sie programmgesteuert reagieren können.

> **Was Sie erhalten:** ein vollständig ausführbares Java‑Snippet, eine Erklärung, *warum* jedes Bauteil wichtig ist, und Tipps zum Umgang mit Sonderfällen wie benutzerdefinierten Schriftarten‑Verzeichnissen.

## Voraussetzungen & Was Sie benötigen

Bevor wir starten, stellen Sie sicher, dass Sie Folgendes haben:

- Java 8 oder neuer installiert (der Code funktioniert auch mit Java 11+).
- Das aktuelle Aspose.Words for Java JAR (Download von der offiziellen Seite oder Maven Central).
- Eine DOCX‑Datei, die Schriftarten referenziert, die nicht auf Ihrem Rechner installiert sind (z. B. ein *font‑rich.docx*, das Sie im Aspose‑Demo‑Set finden).
- Eine ordentliche IDE (IntelliJ IDEA, Eclipse oder sogar VS Code mit Java‑Erweiterungen).

Keine externen Bibliotheken außer Aspose.Words sind erforderlich, und das Beispiel läuft in einer einfachen `main`‑Methode.

## Schritt 1: LoadOptions einrichten – Einstiegspunkt für benutzerdefiniertes Laden

`LoadOptions` ist Aspose.Words’ Konfigurations‑Bag, das der Bibliothek sagt, *wie* ein Dokument gelesen werden soll. Standardmäßig substituiert sie fehlende Schriftarten still, aber Sie können dieses Verhalten mit einem Warn‑Callback ändern.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Warum das wichtig ist:** Ohne `LoadOptions` lädt das Dokument stillschweigend, und Sie verlieren die Sichtbarkeit auf fehlende Schriftarten. Durch das Erzeugen einer Instanz erhalten Sie einen Hook für das Warnsystem.

## Schritt 2: Einen Warnungs‑Callback definieren, um *Font-Substitutionswarnungen* zu erfassen

Aspose.Words leitet Warn‑Events über das `IWarningCallback`‑Interface weiter. Implementieren Sie es inline (oder als separate Klasse) und filtern Sie nach `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Erklärung:**  
- `info.getWarningType()` gibt Ihnen die Kategorie der Warnung an.  
- `WarningType.FONT_SUBSTITUTION` ist der Enum‑Wert, der uns interessiert.  
- `info.getDescription()` enthält eine menschenlesbare Meldung, z. B. *„Font 'Comic Sans MS' not found, substituted with 'Arial'.“*  

Durch das Ausgeben der Beschreibung **erfassen Sie Font‑Substitutionswarnungen** in Echtzeit.

## Schritt 3: Das Dokument mit den konfigurierten LoadOptions laden

Jetzt, wo der Callback eingerichtet ist, laden Sie Ihr DOCX. Der Warn‑Callback wird automatisch während des Parsens ausgelöst.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Ersetzen Sie `YOUR_DIRECTORY` durch den tatsächlichen Pfad zu Ihrer Testdatei. Wenn der `Document`‑Konstruktor ausgeführt wird, löst jede fehlende Schriftart den zuvor definierten Callback aus, und Sie sehen die Substitutionsmeldungen in der Konsole.

## Schritt 4: Das geladene Dokument überprüfen (optional aber hilfreich)

Nach dem Laden möchten Sie vielleicht die Integrität des Dokuments bestätigen – Seitenzahl, Textextraktion usw. Dieser Schritt ist nicht zwingend nötig, um Warnungen zu erfassen, hilft Ihnen aber, die Auswirkungen von Substitutionen zu sehen.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Wurde eine Schriftart substituiert, kann das Layout leicht verschoben werden; das Prüfen der Seitenzahl kann solche Änderungen aufdecken.

## Schritt 5: Fortgeschritten – Substituierte Schriftarten programmgesteuert behandeln

Manchmal wollen Sie die Warnung nicht nur protokollieren – Sie müssen vielleicht eine Ersatzschrift einbetten oder das Styling anpassen. Nachfolgend ein kurzer Ansatz, den Sie übernehmen können.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Indem Sie Aspose.Words auf einen Ordner zeigen, der die Original‑Schriftarten enthält, können Sie die Substitution *vollständig verhindern*. Fehlt der Ordner, erfasst der Warn‑Callback das Ereignis weiterhin und gibt Ihnen eine Ausweichstrategie.

## Vollständiges funktionierendes Beispiel

Alles zusammengeführt, hier das komplette, sofort ausführbare Programm:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Erwartete Konsolenausgabe** (wenn eine fehlende Schriftart gefunden wird):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Sind alle Schriftarten vorhanden, bleibt der Callback still – es wird nichts ausgegeben, was genau das erwartete Verhalten ist.

## Häufige Fallstricke & Pro‑Tipps

| Problem | Warum es passiert | Lösung |
|---------|-------------------|--------|
| **Callback never fires** | Sie haben vergessen, den Callback an `LoadOptions` anzuhängen **oder** den Standard‑Konstruktor von `Document` ohne `loadOptions` verwendet. | Rufen Sie immer `loadOptions.setWarningCallback(...)` **und** verwenden Sie die Überladung `new Document(path, loadOptions)`. |
| **Too many warnings clutter the log** | Große Dokumente mit vielen fehlenden Schriftarten erzeugen für jede Substitution eine Warnung. | Filtern Sie weiter, indem Sie `info.getDescription()` auf bestimmte Schriftartnamen prüfen, oder sammeln Sie Warnungen in einer Liste für die spätere Verarbeitung. |
| **Substituted fonts affect layout** | Die Ersatzschrift kann andere Metriken (Größe, Abstand) haben. | Stellen Sie einen benutzerdefinierten Schriftarten‑Ordner bereit (siehe Schritt 5) oder passen Sie den Dokumentstil nach dem Laden an. |
| **Running on a headless server** | Der Standard‑Fallback für Schriftarten kann System‑Schriftarten benötigen, die auf dem Server nicht installiert sind. | Liefern Sie die benötigten Schriftarten mit Ihrer Anwendung und verweisen Sie `FontSettings` auf diesen Ordner. |

## Häufig gestellte Fragen

**Q: funktioniert das auch mit PDF oder anderen Formaten?**  
A: Ja. Der Warn‑Callback ist formatunabhängig; er wird für jeden Dokumenttyp ausgelöst, den Aspose.Words lädt (DOC, DOCX, RTF, HTML usw.). Der einzige Unterschied ist die Menge der möglichen Warnungen.

**Q: kann ich andere Warnungsarten erfassen, z. B. *image resolution*‑Warnungen?**  
A: Absolut. Untersuchen Sie im `warning`‑Methodenkörper `info.getWarningType()` auf andere Enum‑Werte wie `WarningType.IMAGE_RESOLUTION` und behandeln Sie sie entsprechend.

**Q: was, wenn ich nach dem Laden die Liste der substituierten Schriftarten benötige?**  
A: Speichern Sie jede `info.getDescription()` in einer `List<String>` innerhalb des Callbacks. Nach dem Laden haben Sie eine Sammlung, die Sie protokollieren, an einen Monitoring‑Service senden oder für einen Schriftarten‑Download‑Prozess nutzen können.

## Fazit

Sie wissen jetzt **wie Sie Font‑Substitutionswarnungen** in Java mit Aspose.Words erfassen, warum jedes Bauteil wichtig ist und wie Sie die Lösung für reale Szenarien erweitern können. Durch die Nutzung von `LoadOptions`, einem `Aspose.Words warning callback` und optionalen `FontSettings` erhalten Sie vollständige Sichtbarkeit auf fehlende Schriftarten und können Ihre Dokument‑Konvertierungs‑Pipelines zuverlässig halten.

Bereit für den nächsten Schritt? Ersetzen Sie `System.out.println` durch einen Logger wie SLF4J oder integrieren Sie die Warnliste in eine UI, die Nutzer warnt, bevor sie einen Batch‑Konvertierungsvorgang abschließen. Sie können zudem den **Aspose.Words warning callback** für weitere Warnungsarten erkunden, etwa *unsupported features* oder *high‑resolution image*‑Warnungen.  

Viel Spaß beim Coden, und mögen Ihre PDFs nie wieder unerwartete Schriftart‑Austausche erleben! 

![Screenshot, der die Konsolenausgabe der erfassten Font-Substitutionswarnungen zeigt](image-placeholder.png "Font-Substitutionswarnungen erfassen")


## Was Sie als Nächstes lernen sollten


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Font-Substitutionswarnungen in Aspose.Words aktivieren – Vollständige Anleitung](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Wie man LoadOptions in Aspose.Words für Java festlegt](/words/english/java/document-loading-and-saving/using-load-options/)
- [Wie man PDF-Dokumente mit Aspose.Words für Java erstellt | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}