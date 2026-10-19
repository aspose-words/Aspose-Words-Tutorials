---
category: general
date: 2026-04-04
description: Erfassen Sie Schriftart‑Ersetzungswarnungen beim Laden von Word‑Dokumenten
  mit Aspose.Words für Java und erkennen Sie fehlende Schriftarten automatisch. Folgen
  Sie dieser Schritt‑für‑Schritt‑Anleitung.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: de
og_description: Erfassen Sie Schriftart‑Ersetzungshinweise beim Laden von Word‑Dokumenten
  mit Aspose.Words für Java und erkennen Sie fehlende Schriftarten in wenigen einfachen
  Schritten.
og_title: Erfassung von Schriftart-Substitutionswarnungen – Fehlende Schriftarten
  erkennen
tags:
- Aspose.Words
- Java
- Document Processing
title: Erfasse Schriftart‑Ersetzungshinweise – Fehlende Schriften erkennen
url: /de/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Font‑Substitutionswarnungen erfassen – Fehlende Schriften erkennen

Haben Sie jemals **Font‑Substitutionswarnungen** erfassen müssen, wenn Sie eine Word‑Datei öffnen, nur um festzustellen, dass ein wichtiger Schriftschnitt fehlt? Sie sind nicht allein. In vielen Unternehmens‑Workflows kann eine fehlende Schriftart einen perfekt formatierten Bericht in ein wirres Durcheinander verwandeln, und das einzige Anzeichen ist eine stille Warnung, die die meisten Entwickler nie sehen.

Die gute Nachricht ist, dass Aspose.Words for Java Ihnen ermöglicht, in den Ladevorgang einzugreifen und **fehlende Schriften** zu erkennen, bevor sie später Probleme verursachen. In diesem Tutorial führen wir Sie durch ein vollständiges, ausführbares Beispiel, das jede Substitutionswarnung direkt in die Konsole ausgibt, sodass Sie entscheiden können, ob Sie die richtige Schrift einbetten, sie ersetzen oder den Benutzer benachrichtigen möchten.

Am Ende dieses Leitfadens wissen Sie, wie Sie:

* ein `LoadOptions`‑Objekt mit einem benutzerdefinierten Warn‑Callback einrichten.
* das Callback so filtern, dass es nur auf Font‑Substitutions‑Ereignisse reagiert.
* jede `.docx`‑Datei laden und die Warnungen sofort sehen.
* die Lösung erweitern, um Warnungen zu protokollieren, Ausnahmen zu werfen oder sogar fehlende Schriften automatisch zu installieren.

Keine externe Dokumentation nötig – nur ein paar Zeilen Java und das Aspose.Words‑JAR.

## Voraussetzungen

Bevor wir starten, stellen Sie sicher, dass Sie Folgendes haben:

* Java 8 oder neuer installiert (die neueste LTS‑Version funktioniert am besten).
* Aspose.Words for Java 23.11 oder später – Sie können das Maven‑Artefakt oder das reine JAR von der Aspose‑Website beziehen.
* Ein Word‑Dokument, das eine Schriftart referenziert, die Sie auf Ihrer Entwicklungsmaschine nicht installiert haben (z. B. „MyFancyFont“).  
* Eine IDE oder ein Text‑Editor Ihrer Wahl – ich verwende IntelliJ IDEA, aber Eclipse oder VS Code funktionieren ebenfalls.

Falls Ihnen etwas davon unbekannt ist, pausieren Sie und installieren Sie es zuerst; der Rest des Tutorials geht davon aus, dass alles bereit ist.

---

## Font‑Substitutionswarnungen mit Aspose.Words erfassen

Der Kern der Lösung befindet sich in einer `LoadOptions`‑Instanz. Durch das Zuweisen eines `IWarningCallback` können wir jede Warnung abfangen, die die Bibliothek während der Ladephase ausgibt.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Warum das funktioniert:**  
`LoadOptions` sagt Aspose.Words, wie die eingehende Datei behandelt werden soll. Das `IWarningCallback`‑Interface ist ein Hook, der für *jede* Warnung ein `WarningInfo`‑Objekt erhält. Durch Überprüfung von `info.getWarningType()` filtern wir alles außer `SUBSTITUTED_FONT` heraus. Die Eigenschaft `description` enthält eine menschenlesbare Meldung wie „Font 'MyFancyFont' was substituted with 'Arial'“.

### Erwartete Konsolenausgabe

Wenn das Quell‑Dokument eine Schriftart referenziert, die nicht installiert ist, sehen Sie etwa Folgendes:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Wenn das Dokument nur Schriften verwendet, die auf der Maschine vorhanden sind, bleibt das Callback still und Sie erhalten lediglich die abschließende Zeile „Document loaded successfully.“.

---

## Fehlende Schriften im Dokument erkennen

Sie fragen sich vielleicht: *„Ist eine Substitutionswarnung dasselbe wie eine fehlende Schrift?“* In den meisten Fällen ja – Aspose.Words ersetzt eine fehlende Schriftart durch eine Ersatzschrift und meldet dies über `SUBSTITUTED_FONT`. Es gibt jedoch Randfälle, in denen die Schriftart vorhanden ist, aber der exakte Stil (fett‑kursiv, bestimmte OpenType‑Features) fehlt, was zu einer subtilen Substitution führt.

Um absolut sicherzugehen, dass Sie jede Lücke erfasst haben, können Sie das Warn‑Callback mit einer Inspektion nach dem Laden kombinieren:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Pro‑Tipp:** Wenn Sie noch Runs finden, die auf die fehlende Schriftart verweisen, können Sie sie sofort ersetzen:

```java
font.setName("Arial"); // fallback
```

Damit stellen Sie ein konsistentes visuelles Ergebnis sicher, selbst wenn die ursprüngliche Warnung unterdrückt wurde.

---

## Häufige Fallstricke & wie man sie vermeidet

| Fallstrick | Warum das passiert | Lösung |
|------------|--------------------|--------|
| **Vergessen, das Callback zu setzen** | `LoadOptions` verwendet standardmäßig ein No‑Op‑Callback, sodass Warnungen verschwinden. | Immer `loadOptions.setWarningCallback(...)` vor dem Laden aufrufen. |
| **Falschen Warnungstyp verwenden** | `WarningType.SUBSTITUTED_FONT` ist das einzige Enum, das fehlende Schriften signalisiert. | Genau auf `WarningType.SUBSTITUTED_FONT` filtern; andere Typen (z. B. `UNKNOWN_FILE_FORMAT`) sind nicht relevant. |
| **Hartkodierte Dateipfade** | Funktioniert lokal, bricht aber in CI/CD‑Pipelines. | Einen relativen Pfad verwenden oder den Dateistandort als Befehlszeilenargument übergeben. |
| **Unicode‑Schriften ignorieren** | Einige fehlende Schriften betreffen nur bestimmte Zeichen. | Mit einem Dokument testen, das den vollen Zeichensatz enthält, den Sie unterstützen wollen. |
| **Ausführen auf einem headless Server ohne Schrift‑Konfiguration** | Der Server hat möglicherweise keine Ersatzschriften, was zu unerwarteten Substitutionen führt. | Ein minimales Set gängiger Schriften (Arial, Times New Roman) auf dem Server installieren. |

---

## Lösung erweitern

Jetzt, da Sie **Font‑Substitutionswarnungen erfassen** können, möchten Sie vielleicht:

* **Warnungen in eine Datei protokollieren** – `System.out.println` durch einen Logger wie SLF4J ersetzen.
* **Eine Ausnahme werfen** – nützlich in automatisierten Pipelines, wo eine fehlende Schrift den Build fehlschlagen lassen sollte:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Fehlende Schriften automatisch installieren** – zur Laufzeit die benötigte TTF/OTF herunterladen und sie der Java‑`GraphicsEnvironment` hinzufügen. Das ist ein fortgeschritteneres Szenario, aber durchaus machbar.

---

## Diagramm (optional)

![Capture font substitution warnings flow diagram showing LoadOptions → WarningCallback → Console output](capture-font-substitution-warnings-diagram.png)

*Alt-Text:* “Flussdiagramm zur Erfassung von Font‑Substitutionswarnungen, das zeigt, wie Aspose.Words fehlende‑Schrift‑Warnungen an einen benutzerdefinierten Callback weiterleitet.”

---

## Fazit

Wir haben gerade gezeigt, wie man **Font‑Substitutionswarnungen erfasst** und **fehlende Schriften** erkennt, wenn Word‑Dokumente mit Aspose.Words for Java geladen werden. Durch das Konfigurieren eines `LoadOptions`‑Objekts und das Implementieren eines kleinen `IWarningCallback` erhalten Sie vollständige Transparenz über den Schrift‑Fallback‑Prozess, sodass Sie Warnungen protokollieren, ersetzen oder bei fehlenden Schriftarten abbrechen können.

Kurz gesagt: Callback setzen, nach `SUBSTITUTED_FONT` filtern, Dokument laden und die Ausgabe nach den Bedürfnissen Ihrer Anwendung verarbeiten. Von hier aus können Sie zu Logging‑Frameworks, CI‑Checks oder sogar automatischer Schrift‑Bereitstellung übergehen.

Möchten Sie weitergehen? Probieren Sie:

* **Schriften direkt in das gespeicherte Dokument einbetten** (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` mit `FontEmbeddingMode.EMBED_ALL`).
* **Ein PDF generieren** nach dem Beheben der Schriften, um sicherzustellen, dass das Endergebnis exakt wie gewünscht aussieht.
* **Einen gesamten Ordner** von Dokumenten auf fehlende Schriften scannen und einen Zusammenfassungsbericht erstellen.

Das war's für jetzt – happy coding, und möge Ihr Dokument stets mit der richtigen Schriftart gerendert werden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}