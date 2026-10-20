---
category: general
date: 2026-03-25
description: Erstellen Sie ein benutzerdefiniertes KI‑Modell zum Bearbeiten von Word‑Dokumenten
  – lernen Sie, wie Sie Text formeller gestalten, Absatztext ersetzen und einen Word‑Absatz
  mit Aspose.Words‑KI umschreiben.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: de
og_description: Erstellen Sie ein benutzerdefiniertes KI‑Modell zum Bearbeiten von
  Word‑Dokumenten. Erfahren Sie, wie Sie Text formeller gestalten, Absatztexte ersetzen
  und einen Word‑Absatz mit Aspose.Words KI neu schreiben.
og_title: Erstelle ein benutzerdefiniertes KI‑Modell – Word‑Absätze in Java bearbeiten
tags:
- Aspose.Words
- Java
- AI integration
title: Eigenes KI‑Modell erstellen – Word‑Absätze in Java bearbeiten
url: /de/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstelle benutzerdefiniertes KI‑Modell – Word‑Absätze in Java bearbeiten

Haben Sie jemals ein **create custom AI model** erstellen müssen, das einen Absatz in einer Word‑Datei verfeinert? Vielleicht haben Sie einen Stapel Verträge, die alle ein wenig zu lässig klingen, und Sie möchten den Text mit einer einzigen Codezeile formeller machen. Die gute Nachricht ist, dass Sie genau das tun können – ohne externe Dienste, ohne schwere SDKs, nur Aspose.Words für Java und einen OpenAI‑kompatiblen Endpunkt.

In diesem Tutorial gehen wir jeden Schritt durch, der nötig ist, um **create custom AI model** zu erstellen, es an einen lokalen LLM‑Server anzubinden und dann zu verwenden, um *replace paragraph text* zu ersetzen durch eine formellere Version. Am Ende haben Sie ein ausführbares Java‑Programm, das **edit paragraph with AI** verwendet, einen Word‑Absatz neu schreibt und das Ergebnis wieder auf die Festplatte speichert. Kein Schnickschnack, nur eine praktische Lösung, die Sie in Ihr eigenes Projekt kopieren‑und‑einfügen können.

> **Was Sie benötigen**  
> • Java 17 oder neuer (der Code kompiliert mit früheren Versionen, aber 17 ist der optimale Punkt)  
> • Aspose.Words for Java 23.9 (oder die neueste Version)  
> • Ein laufender OpenAI‑kompatibler LLM‑Server (z. B. Ollama, LocalAI) der auf `http://localhost:8000/v1` lauscht  
> • Ein Eingabe‑Word‑Dokument (`input.docx`) in einem von Ihnen kontrollierten Ordner  

Falls Sie sich fragen *why bother building a custom model*, warum ein benutzerdefiniertes Modell bauen, anstatt OpenAI direkt aufzurufen, lautet die Antwort Flexibilität: Sie kontrollieren den Endpunkt, können Modelle ohne Codeänderungen austauschen und halten API‑Schlüssel aus Ihrem Quellcode‑Repository fern. Lassen Sie uns eintauchen.

## Erstelle benutzerdefiniertes KI‑Modell – Einrichtung und Konfiguration

Zuerst müssen wir Aspose.Words mitteilen, wo unser LLM läuft. Die Klasse `AiModelEndpoint` enthält die URL und einen optionalen API‑Schlüssel. Da wir einen lokalen Server verwenden, kann der Schlüssel ein leerer String sein, aber der Parameter ist erforderlich.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Profi‑Tipp:** Wenn Sie jemals zu einem gehosteten Modell wechseln (z. B. Azure OpenAI), ändern Sie einfach die URL und den Schlüssel – keine weiteren Code‑Änderungen nötig.

## Word‑Dokument laden

Jetzt laden wir die Quelldatei in den Speicher. `Document` kann `.docx`, `.doc`, `.rtf` und viele andere Formate lesen, aber für dieses Beispiel bleiben wir bei `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Stellen Sie sicher, dass `YOUR_DIRECTORY` auf einen echten Ordner zeigt; andernfalls erhalten Sie eine `FileNotFoundException`. In einer realen Anwendung könnten Sie den Pfad als Befehlszeilenargument übergeben oder aus einer Konfigurationsdatei lesen.

## Initialisiere das benutzerdefinierte KI‑Modell

Wir erstellen ein `AiModel` vom Typ `CUSTOM` und geben ihm den zuvor definierten Endpunkt. Das weist Aspose.Words an, alle KI‑Aufrufe über unseren eigenen Server zu leiten.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Im Hintergrund baut Aspose.Words einen kleinen HTTP‑Client, der mit dem LLM über das standardmäßige OpenAI‑Chat/Completion‑Schema kommuniziert. Deshalb muss der Endpunkt *OpenAI‑compatible* sein.

## Den ersten Absatz abrufen und neu schreiben

Hier wird der Text tatsächlich **make text more formal**. Wir holen den ersten Absatz, senden dessen Rohtext zusammen mit einer Eingabeaufforderung an das Modell und erhalten die bearbeitete Version.

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

Das zweite Argument (`"Make it more formal"`) ist die Anweisung, die wir dem Modell geben. Sie können es durch jede beliebige Direktive ersetzen – **replace paragraph text**, **summarize**, **translate** usw. Die Methode gibt einen einfachen String zurück, den wir später wieder in das Dokument einfügen.

> **Warum das funktioniert:** `editText` sendet ein JSON‑Payload wie `{ \"model\": \"...\", \"messages\": [{ \"role\":\"user\", \"content\":\"<text>\\nMake it more formal\"}] }`. Das LLM sieht den ursprünglichen Absatz und die Anweisung und antwortet mit dem überarbeiteten Text.

## Den ursprünglichen Absatzinhalt ersetzen

Jetzt **replace paragraph text** im Word‑Objektmodell. Wir entfernen alle vorhandenen Runs (die Low‑Level‑Texteinheiten) und fügen einen neuen `Run` ein, der die KI‑generierte Zeichenkette enthält.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Achten Sie darauf, nicht `firstParagraph.setText()` aufzurufen – diese Methode würde jegliche Formatierung entfernen. Die Verwendung von `Run` bewahrt den Stil des Absatzes (Überschrift, Aufzählung usw.), während die eigentlichen Zeichen ausgetauscht werden.

## Das bearbeitete Dokument speichern

Zum Schluss schreiben wir das modifizierte Dokument zurück auf die Festplatte. Sie können die Originaldatei überschreiben oder, wie wir hier, eine neue Kopie erstellen.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Wenn Sie `output.docx` öffnen, sollte der erste Absatz nun deutlich formeller klingen. Wenn das LLM die Anweisung nicht perfekt befolgt hat, können Sie die Eingabeaufforderung anpassen oder eine andere Modellversion ausprobieren.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette Programm – kopieren Sie es in `LlmDemo.java`, passen Sie die Pfade an und führen Sie es mit `javac` + `java` aus.

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Erwartete Ausgabe:** Öffnen Sie `output.docx` und Sie werden den ursprünglichen Absatz transformiert sehen. Zum Beispiel könnte ein lockerer Satz wie „We’ll get the thing done soon.“ zu „We shall complete the task promptly.“ werden. Die genaue Formulierung hängt vom verwendeten Modell ab.

## Häufige Fragen & Sonderfälle

### Was ist, wenn mein Dokument mehrere Abschnitte hat?

Der obige Code berührt nur den *ersten* Absatz des *ersten* Abschnitts. Um **edit paragraph with AI** über die gesamte Datei hinweg anzuwenden, iterieren Sie über `document.getSections()` und dann über jedes `section.getBody().getParagraphs()`. Denken Sie daran, leere Absätze zu überspringen, sonst erhält das LLM einen leeren String und gibt nichts zurück.

### Wie gehe ich mit langen Absätzen um, die Token‑Limits überschreiten?

Die meisten LLMs begrenzen die Eingabe auf etwa 4 000 Token. Wenn ein Absatz ungewöhnlich lang ist, teilen Sie ihn in kleinere Stücke, bevor Sie `editText` aufrufen. Sie können dieselbe `AiModel`‑Instanz wiederverwenden; achten Sie jedoch auf die Rate‑Limits Ihres lokalen Servers.

### Kann ich eine andere Anweisung verwenden, wie „summarize“ oder „translate to French“?

Absolut. Das zweite Argument von `editText` ist frei formulierbar. Für eine Zusammenfassung könnten Sie `"Summarize in one sentence"` übergeben. Für Übersetzungen funktioniert `"Translate to French, keep the tone formal"` ebenso gut. Diese Flexibilität ermöglicht es Ihnen, **replace paragraph text** für viele Szenarien zu nutzen, ohne Code zu ändern.

### Bewahrt das Modell die Absatzformatierung (Schriftarten, Farben)?

Da wir nur den `Run` im selben `Paragraph`‑Objekt ersetzen, bleiben vorhandene Stile (Überschriftenebene, Aufzählung, Einrückung) erhalten. Wenn Sie den Stil selbst ändern müssen, können Sie nach dem Ersetzen `Paragraph.getParagraphFormat()` manipulieren.

### Was ist, wenn mein LLM‑Server HTTPS mit einem selbstsignierten Zertifikat erfordert?

`AiModelEndpoint` akzeptiert eine URL mit `https://`. Wenn das Zertifikat nicht vertrauenswürdig ist, müssen Sie den SSL‑Kontext von Java so konfigurieren, dass er es akzeptiert, oder den Server mit einem gültigen Zertifikat betreiben. Diese Einrichtung liegt außerhalb des Umfangs dieses Tutorials, ist jedoch in den Java‑SSL‑Leitfäden gut dokumentiert.

## Tipps für produktionsreife Integration

| Tip | Why it matters |
|-----|----------------|
| **Endpoint zwischenspeichern** | Das erneute Erstellen von `AiModelEndpoint` bei jeder Anfrage verursacht zusätzlichen Aufwand. |
| **Stapel‑Bearbeitungen** | Wenn Sie viele Absätze haben, senden Sie sie in einer einzigen Anfrage (z. B. JSON‑Array), um die Latenz zu reduzieren. |
| **LLM‑Ausgabe validieren** | Überprüfen Sie stets den zurückgegebenen String auf null oder leere Werte, bevor Sie ihn einfügen. |
| **Eingabeaufforderungen und Antworten protokollieren** | Hilfreich für Debugging und für die Einhaltung von Vorschriften, wenn Sie juristischen Text umschreiben. |
| **Sanfter Rückfall** | Falls das LLM nicht erreichbar ist, greifen Sie auf den Originalabsatz oder eine einfache heuristische Umschreibung zurück. |

## Fazit

Wir haben Ihnen gezeigt, wie Sie **create custom AI model** mit Aspose.Words erstellen, es mit einem OpenAI‑kompatiblen Endpunkt verbinden und dann **edit paragraph with AI** verwenden, um **make text more formal** zu erreichen. Indem Sie die sechs Schritte befolgen – Endpunkt definieren, Dokument laden, Modell initialisieren, 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}