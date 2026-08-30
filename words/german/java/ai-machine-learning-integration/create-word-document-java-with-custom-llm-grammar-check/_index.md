---
category: general
date: 2026-05-04
description: Erstellen Sie ein Word‑Dokument in Java mit Aspose.Words und lernen Sie,
  wie Sie die Grammatik mit einem benutzerdefinierten LLM überprüfen. Schritt‑für‑Schritt‑Anleitung
  für Java‑Entwickler.
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: de
og_description: Erstelle ein Word‑Dokument in Java und sieh dir an, wie man Grammatik
  mit einem benutzerdefinierten LLM prüft. Vollständiges Java‑Tutorial mit ausführbarem
  Code.
og_title: Word-Dokument in Java erstellen mit benutzerdefinierter LLM-Grammatikprüfung
tags:
- Java
- Aspose.Words
- LLM
title: Word-Dokument in Java erstellen mit benutzerdefinierter LLM‑Grammatikprüfung
url: /de/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen von Word-Dokumenten in Java mit benutzerdefinierter LLM‑Grammatikprüfung

Haben Sie sich jemals gefragt, wie man **Word‑Dokument in Java erstellen** Projekte erstellt, die sich selbst Korrektur lesen? Sie sind nicht allein – viele Entwickler wollen eine einzige Pipeline, die eine polierte *.docx*‑Datei ausgibt, ohne mehrere Werkzeuge jonglieren zu müssen. In diesem Tutorial führen wir Sie Schritt für Schritt durch genau das und zeigen Ihnen **wie man docx erstellt** Dateien mit Aspose.Words, wie man ein lokal gehostetes LLM anbinden kann und schließlich **wie man Grammatik prüft** automatisch. Am Ende haben Sie ein eigenständiges Java‑Programm, das ein Word‑Dokument schreibt, validiert und speichert – und das alles, während Sie **benutzerdefiniertes LLM verwenden** Endpunkte selbst steuern.

## Was Sie benötigen

Bevor wir loslegen, stellen Sie sicher, dass Sie Folgendes auf Ihrem Rechner haben:

| Voraussetzung | Warum es wichtig ist |
|--------------|-----------------------|
| Java 17+ (or any recent JDK) | Moderne Sprachfeatures und bessere Modulunterstützung |
| Aspose.Words for Java (latest version) | Die Bibliothek, die es Ihnen ermöglicht, **Word‑Dokument in Java erstellen** Dateien programmgesteuert zu erzeugen |
| A locally hosted LLM server (e.g., Ollama, LMStudio) listening on `http://localhost:11434/api/generate` | Erforderlich für den **benutzerdefiniertes LLM verwenden** Schritt, der die Grammatikprüfung ermöglicht |
| Maven or Gradle (we’ll use Maven in examples) | Vereinfacht das Management von Abhängigkeiten |
| An IDE or text editor (IntelliJ IDEA, VS Code, etc.) | Erleichtert das Schreiben und Debuggen von Code |

Falls Ihnen etwas davon unbekannt vorkommt, keine Panik – jedes Element ist kostenlos oder hat eine Community‑Edition, die sich perfekt für Lernzwecke eignet.

## Schritt 1 – Richten Sie Ihr Maven‑Projekt ein

Um **Word‑Dokument in Java erstellen** Projekte schnell zu starten, beginnen Sie mit einer minimalen Maven‑`pom.xml`. Diese Datei bindet die Aspose.Words‑Bibliothek und einen HTTP‑Client Ihrer Wahl ein (wir verwenden Apache HttpClient).

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-llm-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- replace with the latest -->
        </dependency>

        <!-- Apache HttpClient for calling the LLM endpoint -->
        <dependency>
            <groupId>org.apache.httpcomponents.client5</groupId>
            <artifactId>httpclient5</artifactId>
            <version>5.2</version>
        </dependency>
    </dependencies>
</project>
```

> **Pro Tipp:** Wenn Sie Gradle verwenden, kommen die gleichen Abhängigkeiten unter `implementation` in `build.gradle`.

Führen Sie jetzt `mvn clean install` aus, um die JARs zu holen. Sobald der Build erfolgreich ist, können Sie Java‑Code schreiben, der **Word‑Dokument in Java erstellt** Dateien erzeugt.

## Schritt 2 – Schreiben Sie die Java‑Klasse, die **Word‑Dokument in Java erstellt**

Unten finden Sie die vollständige, sofort ausführbare Quelldatei. Sie demonstriert den gesamten Ablauf: ein leeres Dokument initialisieren, einen benutzerdefinierten LLM‑Endpunkt konfigurieren, die Grammatikprüfung aufrufen und schließlich das Ergebnis speichern.

```java
package com.example.wordllmdemo;

import com.aspose.words.*;
import com.aspose.words.ai.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

/**
 * Demonstrates how to create a Word document in Java and run a grammar‑check
 * using a self‑hosted LLM (e.g., Ollama). This example is fully self‑contained
 * and can be executed with a single `java -cp` command after Maven builds.
 */
public class SelfHostedLLMDemo {

    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 2.1 – Create an empty Word document
        // -----------------------------------------------------------------
        Document document = new Document(); // this is the object that will become your .docx

        // Add a simple paragraph so the grammar engine has something to work with
        DocumentBuilder builder = new DocumentBuilder(document);
        builder.writeln("Ths sentence has a typo and a grammer error.");

        // -----------------------------------------------------------------
        // Step 2.2 – Configure the custom LLM endpoint (use custom llm)
        // -----------------------------------------------------------------
        AiEndpoint llmEndpoint = new AiEndpoint();
        llmEndpoint.setBaseUrl("http://localhost:11434/api/generate");
        llmEndpoint.setModel("llama3.1:8b"); // make sure this model is available locally

        // Initialise the Document AI engine with the endpoint we just set up
        DocumentAi documentAi = new DocumentAi(llmEndpoint);

        // -----------------------------------------------------------------
        // Step 2.3 – Run grammar checking (how to check grammar)
        // -----------------------------------------------------------------
        // AiModelType.CUSTOM tells the API to forward the request to our LLM
        documentAi.checkGrammar(document, AiModelType.CUSTOM);

        // -----------------------------------------------------------------
        // Step 2.4 – Save the corrected file
        // -----------------------------------------------------------------
        String outputPath = "output/GrammarChecked.docx";
        // Ensure the directory exists
        Files.createDirectories(Path.of("output"));
        document.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

> **Warum das funktioniert:**  
> * `Document` ist die Kernklasse von Aspose.Words, die ein *.docx* im Speicher repräsentiert.  
> * `AiEndpoint` teilt dem AI‑Modul von Aspose mit, wohin die Eingabe gesendet werden soll. Indem wir es auf `localhost:11434` zeigen, **verwenden wir benutzerdefiniertes LLM** statt eines Cloud‑Dienstes.  
> * `checkGrammar` mit `AiModelType.CUSTOM` leitet den Text des Dokuments an das LLM weiter, erhält korrigierten Text und überschreibt die zugrunde liegenden Word‑Knoten.  
> * Schließlich rufen wir `save` auf, um die Datei auf die Festplatte zu schreiben und erhalten ein poliertes Word‑Dokument.

### Erwartete Ausgabe

Nach dem Ausführen von `mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` sollten Sie sehen:

```
Document saved to output/GrammarChecked.docx
```

Öffnen Sie die resultierende `GrammarChecked.docx` in Microsoft Word (oder LibreOffice). Der ursprüngliche Satz *„Ths sentence has a typo and a grammer error.“* wird nun zu *„This sentence has a typo and a grammar error.“* – ein Beweis dafür, dass der **wie man Grammatik prüft** Schritt erfolgreich war.

## Schritt 3 – Wie man docx mit unterschiedlichem Inhalt erstellt (Optional)

Wenn Sie reichhaltigere Dokumente erzeugen möchten – Tabellen, Bilder oder formatierter Text – verwenden Sie weiterhin `DocumentBuilder`. Hier ein kurzer Ausschnitt, der das Hinzufügen einer Überschrift und einer Tabelle demonstriert:

```java
// Adding a heading
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Demo Report");

// Adding a 2x2 table
Table table = builder.startTable();
builder.insertCell();
builder.write("Item");
builder.insertCell();
builder.write("Quantity");
builder.endRow();

builder.insertCell();
builder.write("Apples");
builder.insertCell();
builder.write("42");
builder.endRow();
builder.endTable();
```

Sie können diesen Code beliebig zwischen dem Dokument‑Erstellungs‑Block (Schritt 2.1) und dem Grammatik‑Check‑Aufruf (Schritt 2.3) einfügen. Das LLM erhält weiterhin den gesamten Text, sodass es natürliche Sprachteile korrigieren kann, während Tabellen unverändert bleiben.

## Schritt 4 – Umgang mit Endpunkt‑Problemen (Benutzerdefiniertes LLM sicher verwenden)

Bei **benutzerdefiniertes LLM verwenden** Endpunkten treten häufig einige Stolpersteine auf:

| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| `Connection refused` Fehler | LLM‑Server läuft nicht oder falscher Port | Starten Sie Ollama (`ollama serve`) und prüfen Sie, ob `http://localhost:11434/api/generate` mit `curl` funktioniert. |
| Antwort‑JSON fehlt das Feld `completion` | Modellname stimmt nicht überein | Stellen Sie sicher, dass das von Ihnen gesetzte Modell (`llama3.1:8b`) installiert ist (`ollama list`). |
| Grammatikprüfung gibt den Originaltext unverändert zurück | Prompt wird vom LLM nicht erkannt | Passen Sie das System des Modells an |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}