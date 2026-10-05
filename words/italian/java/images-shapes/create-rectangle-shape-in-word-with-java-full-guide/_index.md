---
category: general
date: 2026-02-10
description: Crea una forma rettangolare in un documento Word usando Aspose.Words
  per Java. Scopri come impostare il colore dell'ombra, come aggiungere l'ombra e
  come creare un documento Word programmaticamente.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: it
og_description: Crea una forma rettangolare in un documento Word usando Aspose.Words
  per Java. Segui questo tutorial passo‑passo per impostare il colore dell'ombra,
  aggiungere l'ombra e creare il documento Word.
og_title: Crea una forma rettangolare in Word con Java – Guida completa
tags:
- Aspose.Words
- Java
- Document Automation
title: Crea una forma rettangolare in Word con Java – Guida completa
url: /it/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea una forma rettangolare in Word con Java – Guida completa

Ti è mai capitato di dover **creare una forma rettangolare** in un documento Word ma non sapevi da dove cominciare? Non sei il solo—molti sviluppatori si trovano di fronte a questo ostacolo quando provano per la prima volta a disegnare graficamente in Word in modo programmatico. La buona notizia? Con Aspose.Words per Java puoi inserire un rettangolo in una pagina, aggiungere un’ombra gradevole e salvare il file in pochi secondi. In questo tutorial vedremo passo passo **come aggiungere l’ombra**, **impostare il colore dell’ombra** e **creare un documento Word** da zero.  

Copriamo tutto ciò di cui hai bisogno: le librerie richieste, ogni riga di codice, perché alcune impostazioni sono importanti e qualche trucco che potresti non trovare nella documentazione ufficiale. Alla fine avrai un esempio pronto all’uso che crea una forma rettangolare con un’ombra grigia morbida, salvata come *Shadow.docx*.

## Prerequisiti – Cosa ti serve prima di iniziare

Prima di immergerci nel codice, assicurati di avere quanto segue:

| Requisito | Motivo |
|-----------|--------|
| Java Development Kit (JDK) 8 o superiore | Aspose.Words funziona su qualsiasi JDK moderno. |
| Maven o Gradle (opzionale) | Semplifica l’aggiunta della dipendenza Aspose.Words. |
| Licenza Aspose.Words per Java (o una prova gratuita) | La libreria è commerciale; una versione di prova è sufficiente per i test. |
| Un IDE (IntelliJ IDEA, Eclipse, VS Code, ecc.) | Ti aiuta a eseguire e fare debug dell’esempio rapidamente. |

Se hai già un progetto Java, aggiungi semplicemente la coordinata Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Nessuna configurazione complessa oltre a questo—basta un semplice metodo `public static void main`.

![create rectangle shape example](https://example.com/rectangle-shadow.png "crea una forma rettangolare con ombra in Word")

*Testo alternativo immagine: esempio di forma rettangolare che mostra un rettangolo ciano con un’ombra grigia.*

## Passo 1 – Crea un nuovo documento Word

La prima cosa da fare è avviare un documento vuoto. Pensalo come aprire un nuovo file Word su cui dipingerai in seguito.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Perché iniziare con un `Document` vuoto? Perché Aspose.Words tratta la classe `Document` come la tela per tutte le operazioni successive—aggiunta di paragrafi, tabelle o forme. Se salti questo passaggio otterrai un `NullPointerException` non appena proverai a inserire qualcosa.

## Passo 2 – Configura un DocumentBuilder

Un `DocumentBuilder` è la tua penna amichevole che scrive nel `Document`. È il modo consigliato per aggiungere contenuti perché gestisce automaticamente la posizione del cursore.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Ti potresti chiedere: “Perché non manipolare direttamente il documento?” La risposta: il builder astrae i dettagli a basso livello come la gestione delle sezioni, rendendo il codice più pulito e meno soggetto a errori.

## Passo 3 – Inserisci la forma rettangolare

Ora arriva la parte divertente—**come creare una forma**. Inseriremo un rettangolo di 100 × 50 punti e gli daremo un riempimento ciano così da poterlo vedere.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Alcune note:

* `ShapeType.RECTANGLE` indica ad Aspose che vogliamo un rettangolo; puoi sostituirlo con `OVAL`, `LINE`, ecc.
* Le dimensioni sono espresse in punti (1 pt ≈ 1/72 in). Regolale per adattarle al tuo layout.
* Senza un colore di riempimento la forma sarebbe invisibile su una pagina bianca—da qui il ciano.

## Passo 4 – Aggiungi un’ombra e **imposta il colore dell’ombra**

Qui rispondiamo alla parte **come aggiungere l’ombra** del puzzle. L’oggetto `ShadowFormat` controlla ogni aspetto visivo dell’ombra, dal colore al raggio di sfocatura.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Perché questi valori specifici?

* **Visibilità** – Senza `setVisible(true)` le altre impostazioni vengono ignorate.
* **Colore** – Il grigio è una scelta neutra che funziona sia su sfondi chiari che scuri. Sentiti libero di sostituire `java.awt.Color.GRAY` con qualsiasi `java.awt.Color` preferisci.
* **Raggio di sfocatura** – Un valore di `5.0` produce una sfumatura delicata; valori più alti rendono l’ombra più diffusa.
* **OffsetX/Y** – Gli offset spostano l’ombra verso destra e verso il basso, simulando una fonte luminosa dall’alto‑sinistra.
* **Trasparenza** – Un’ombra semi‑trasparente si integra meglio con la pagina, soprattutto in stampa.

Se desideri un aspetto più netto, riduci il raggio di sfocatura a `0` e aumenta l’offset. Sperimentare è consigliato—le ombre sono altamente visive e le impostazioni giuste dipendono dal design del tuo documento.

## Passo 5 – Salva il documento

Infine, persisti tutto in un file `.docx`. Puoi scegliere qualsiasi percorso ti piaccia; assicurati solo che la cartella esista.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Quando apri *Shadow.docx* in Microsoft Word, vedrai un rettangolo ciano con una leggera ombra grigia spostata di 4 pt verso destra e verso il basso. Questo è l’intero flusso di lavoro **crea documento Word**.

### Risultato atteso

| Elemento | Aspetto |
|----------|---------|
| Rettangolo | Riempimento ciano, dimensioni 100 × 50 pt |
| Ombra | Grigia, 30 % trasparente, sfocatura 5 pt, offset (4, 4) |
| File | `Shadow.docx` salvato nel percorso fornito |

Se la forma non appare, verifica che il colore di riempimento non sia uguale allo sfondo della pagina e che l’ombra sia impostata come visibile.

## Consigli professionali & errori comuni

* **Consiglio pro:** Usa `rectangle.setStrokeColor(java.awt.Color.BLACK);` se desideri un bordo attorno alla forma. Il rettangolo risalta di più su una pagina stampata.
* **Attenzione a:** Salvare in una cartella di sola lettura genererà un `IOException`. Scegli una posizione scrivibile o modifica i permessi del file.
* **Caso limite:** Se ti serve un riempimento trasparente (senza colore), chiama `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`. La forma proietterà comunque un’ombra, utile per grafiche in stile filigrana.
* **Nota sulle prestazioni:** Aggiungere centinaia di forme in un ciclo può aumentare l’uso di memoria. Chiama `document.save` una sola volta dopo aver inserito tutte le forme.

## Esempio completo funzionante

Di seguito trovi l’intero programma che puoi copiare‑incollare in una classe Java chiamata `ShadowDemo`. Compila ed esegui così com’è (a patto che il JAR di Aspose.Words sia nel classpath).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Esegui il programma, apri il *Shadow.docx* risultante e vedrai il rettangolo con la sua ombra esattamente come descritto.

## E se ti servono più forme?

Ti potresti chiedere, “Posso **creare una forma rettangolare** più volte o usare altre forme?” Assolutamente sì. Basta iterare il codice di inserimento e regolare le coordinate con `builder.moveTo` o `builder.insertParagraph`. Le stesse impostazioni di ombra possono essere riutilizzate estraendole in un metodo di supporto:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Chiama `applyStandardShadow(rectangle);` dopo ogni inserimento di forma per mantenere il codice DRY (Don’t Repeat Yourself).

## Prossimi passi – Oltre le basi

Ora che sai **come aggiungere l’ombra**, considera di approfondire questi argomenti correlati:

* **Come impostare il colore dell’ombra** per i run di testo – dona ai titoli un leggero rilievo.
* **Crea documento Word** con tabelle e immagini – combina forme con altri contenuti.
* **Come creare animazioni di forma** usando le funzionalità integrate di Word

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}