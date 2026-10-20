---
category: general
date: 2026-03-04
description: Wie man LLM für Document AI konfiguriert und Text in DOCX mit KI ersetzt
  – Schritt‑für‑Schritt‑Anleitung mit vollständigem Java‑Code.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: de
og_description: Wie man LLM für Document AI konfiguriert und Text in DOCX mithilfe
  von KI ersetzt – vollständige Anleitung mit ausführbarem Java‑Code.
og_title: Wie man LLM konfiguriert – Text in DOCX mit KI ersetzen
tags:
- LLM
- Document AI
- Java
- DOCX
title: How to Configure LLM – Replace Text in DOCX with AI
url: /de/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man LLM konfiguriert – Text in DOCX mit KI ersetzen

Haben Sie sich jemals gefragt, **wie man LLM konfiguriert**, damit es für Sie eine Word‑Datei bearbeiten kann? Sie sind nicht der Einzige. Viele Entwickler stoßen an eine Grenze, wenn sie programmatisch einen Ausdruck in einer `.docx` ersetzen müssen, ohne Microsoft Word zu öffnen. Die gute Nachricht? Mit einem lokalen LLM und einem kleinen Document AI‑Wrapper können Sie Text in einer DOCX‑Datei in nur wenigen Zeilen Java austauschen.

In diesem Tutorial gehen wir den gesamten Prozess durch: vom Einrichten der LLM‑Verbindung, über das Laden einer DOCX, bis hin zur Verwendung von **Document AI**, um eine Zielphrase zu ersetzen. Am Ende haben Sie ein eigenständiges, ausführbares Beispiel, das Sie in jedes Maven‑ oder Gradle‑Projekt einbinden können. Keine externen API‑Schlüssel, keine Cloud‑Kosten — nur Ihr eigenes Modell, das unter `http://localhost:8080/v1` lauscht.

> **Schneller Erfolg:** Wenn Sie bereits ein lokales LLM (wie Llama 3 oder Mistral) haben, das einen OpenAI‑kompatiblen Endpunkt bereitstellt, funktioniert der untenstehende Code sofort.

---

![Diagramm zur Konfiguration von LLM für Document AI](/images/configure-llm-diagram.png){: .center-image alt="Diagramm zur Konfiguration von LLM"}

## Was Sie benötigen

- **Java 17** (oder irgendein aktuelles JDK)  
- Ein **lokales LLM**, das einen OpenAI‑ähnlichen `/v1`‑Endpunkt bereitstellt (z. B. Ollama, LMStudio)  
- Die **Document AI Java library** (angenommen `com.example:document-ai:1.2.0` auf Maven Central)  
- Eine Beispiel‑DOCX‑Datei (`input.docx`) in einem bekannten Ordner abgelegt  

Falls Ihnen etwas davon fehlt, starten Sie schnell Ollama:

```bash
ollama serve &
ollama run llama3
```

Damit wird ein Server unter `http://localhost:8080/v1` gestartet, der bereit ist, Anfragen zu akzeptieren.

---

## Wie man LLM für Document AI konfiguriert

Das Erste, was wir tun, ist dem `DocumentAi`‑Client mitzuteilen, wo das Modell zu finden ist und welches Modell verwendet werden soll. Dies ist der **how to configure LLM**‑Schritt, den viele Tutorials übergehen.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Warum das wichtig ist:*  
Das `AiModelConfig`‑Objekt abstrahiert die HTTP‑Details und lässt `DocumentAi` sich auf den Inhalt konzentrieren. Wenn Sie jemals zu einem gehosteten Anbieter wechseln, ändern Sie nur `baseUrl` und `apiKey` — der Rest Ihres Codes bleibt unverändert.

---

## DOCX‑Dokument laden und vorbereiten

Als Nächstes laden wir die Word‑Datei in den Speicher. Die Klasse `Document` verarbeitet sowohl `.docx` als auch `.pdf` im Hintergrund, aber hier interessiert uns nur DOCX.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Pro‑Tipp:* Verwenden Sie während des Debuggens einen absoluten Pfad, um die „Datei nicht gefunden“-Überraschung zu vermeiden. Sobald Sie sicher sind, wechseln Sie zurück zu einem relativen Pfad für Portabilität.

---

## Text in DOCX mit KI ersetzen

Jetzt kommt der Kern des Tutorials — **how to replace text** in einer DOCX‑Datei mit KI‑Unterstützung. Die Methode `replaceText` sendet den Dokumentinhalt an das LLM, bittet es, die Ersetzung vorzunehmen, und gibt den überarbeiteten Text zurück.

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*Was im Hintergrund passiert?*  
`DocumentAi` serialisiert die DOCX in Klartext, erstellt eine Eingabeaufforderung wie:

> “In dem folgenden Dokument ersetzen Sie jedes Vorkommen von ‘old phrase’ durch ‘new phrase’ und geben nur den aktualisierten Text zurück.”

Das LLM verarbeitet die Anfrage und sendet den modifizierten Inhalt zurück. Dieser Ansatz funktioniert selbst, wenn der Ausdruck über mehrere Runs oder Absätze hinweg reicht — etwas, das bei einfacher Zeichenketten‑Ersetzung häufig übersehen wird.

---

## Überprüfen und Ausgeben des überarbeiteten Textes

Zum Schluss geben wir den KI‑überarbeiteten Text in der Konsole aus. In einer realen Anwendung würden Sie das Ergebnis wahrscheinlich in ein neues DOCX zurückschreiben, aber das Ausdrucken ermöglicht eine schnelle Überprüfung.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Erwartete Ausgabe** (angenommen, das ursprüngliche DOCX enthielt „This is the old phrase we want to change.“):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Wenn Sie die neue Phrase sehen, herzlichen Glückwunsch — **Sie haben gerade gelernt, wie man Document AI verwendet, um eine Phrase mit KI zu ersetzen**.

---

## Vollständiges funktionierendes Beispiel

Wenn wir alles zusammenfügen, erhalten Sie eine komplette, sofort ausführbare Java‑Klasse. Sie können sie gerne in `src/main/java/com/example/ReplaceInDocx.java` kopieren und einfügen.

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### Wie man ausführt

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Stellen Sie sicher, dass der LLM‑Server läuft, bevor Sie das Programm ausführen; andernfalls erhalten Sie einen Verbindungs‑Timeout.

---

## Randfälle & häufige Stolperfallen

| Situation | Worauf zu achten ist | Empfohlene Lösung |
|-----------|----------------------|-------------------|
| **Phrase not found** | Das LLM gibt den ursprünglichen Text unverändert zurück. | Rechtschreibung und Groß‑/Kleinschreibung prüfen; Sie können `ignoreCase:true` zum Prompt hinzufügen, falls Ihr Wrapper das unterstützt. |
| **Large documents (>5 MB)** | Die Prompt‑Größe kann das Token‑Limit des Modells überschreiten. | DOCX in Abschnitte aufteilen, jeden separat verarbeiten und anschließend die Ergebnisse zusammenfügen. |
| **Local LLM returns errors** | Oft verursacht durch einen falschen Modellnamen. | Prüfen Sie, ob der Modellname in der LLM‑UI (`ollama list`) mit `modelConfig.setModelName` übereinstimmt. |
| **Unicode characters get garbled** | Kodierungsprobleme beim Lesen der DOCX. | Stellen Sie sicher, dass Ihre Java‑Runtime UTF‑8 verwendet (fügen Sie `-Dfile.encoding=UTF-8` zu den JVM‑Argumenten hinzu). |

## Nächste Schritte

Jetzt, wo Sie **how to replace text in DOCX** mit KI kennen, möchten Sie vielleicht Folgendes erkunden:

- **How to use Document AI** für komplexere Aufgaben wie Tabellenauszug oder Stil‑Erhaltung.  
- **Replace phrase with AI** in PDFs, indem Sie das Argument des `Document`‑Konstruktors austauschen.  
- **Batch processing**: Durchlaufen Sie ein Verzeichnis von DOCX‑Dateien und wenden Sie dieselbe Ersetzung an.  

Jeder dieser Punkte baut auf derselben `AiModelConfig`‑ und `DocumentAi`‑Basis auf, sodass Sie nicht von Grund auf neu beginnen müssen.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}