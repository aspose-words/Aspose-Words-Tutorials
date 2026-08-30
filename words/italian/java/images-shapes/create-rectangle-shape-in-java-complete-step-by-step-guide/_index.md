---
category: general
date: 2026-07-03
description: Crea una forma rettangolare in Java e impara come aggiungere l'ombra
  alla forma, applicare l'effetto ombra, impostare la trasparenza della forma e creare
  rapidamente un documento vuoto.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: it
og_description: Crea una forma rettangolare in Java con ombra, trasparenza e un documento
  vuoto. Segui questa guida per padroneggiare la gestione delle forme.
og_title: Crea una forma rettangolare in Java – Tutorial completo di programmazione
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Crea una forma rettangolare in Java – Guida completa passo‑a‑passo
url: /it/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea forma rettangolare in Java – Guida completa passo‑passo

Ti sei mai chiesto come **creare una forma rettangolare** in un documento Word usando Java? Non sei l’unico: gli sviluppatori hanno spesso bisogno di un modo rapido per aggiungere grafiche geometriche, poi dare loro un’ombra leggera così il layout risulta più curato. In questo tutorial percorreremo l’intero processo: dalla creazione di un **documento vuoto** all’**aggiunta di ombra alla forma**, **applicazione dell’effetto ombra**, e persino **impostazione della trasparenza della forma** per un aspetto professionale.

Lo snippet di codice qui sotto è un esempio completamente funzionante che puoi copiare‑incollare nel tuo progetto. Nessuna documentazione esterna necessaria—basta seguire i passaggi, capire il “perché”, e genererai rettangoli con ombra in pochi secondi.

## Cosa imparerai

- Come **creare una forma rettangolare** programmaticamente con Aspose.Words per Java.  
- Le chiamate esatte necessarie per **aggiungere ombra alla forma** e configurarne le proprietà visive.  
- Modi per **applicare l’effetto ombra** e regolare parametri come offset, raggio di sfocatura e colore.  
- Tecniche per **impostare la trasparenza della forma** per un aspetto più delicato.  
- Come **creare un documento vuoto**, inserire la forma e salvare il risultato.

> **Pro tip:** Tutte queste azioni vengono eseguite su un’unica istanza `Document`, il che significa che puoi concatenarle senza preoccuparti di I/O intermedio.

## Prerequisiti

Prima di immergerci, assicurati di avere:

- Java 17 (o qualsiasi JDK recente) installato.  
- La libreria Aspose.Words per Java aggiunta al tuo progetto (coordinate Maven: `com.aspose:aspose-words:23.12`).  
- Un IDE Java o un semplice editor di testo—nulla di speciale, solo un luogo dove compilare ed eseguire.

Se ti manca qualcuno di questi, scarica il JDK da Oracle e aggiungi la dipendenza Aspose tramite Maven o Gradle. Una volta fatto, sei pronto a partire.

## Passo 1: **Create blank document** – la tela per tutto

La prima cosa di cui hai bisogno è un oggetto `Document` vuoto. Pensalo come un foglio di carta fresco; senza di esso non c’è dove mettere il tuo rettangolo.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Perché iniziare con un documento vuoto? Perché ogni forma vive all’interno di una `Section`, e un `Document` appena istanziato contiene già una sezione predefinita con un body pronto a ricevere nodi. Saltare questo passo ti costringerebbe a creare manualmente le sezioni in seguito, aggiungendo complessità non necessaria.

## Passo 2: **Create rectangle shape** e definisci le sue dimensioni

Ora che abbiamo una tela, **creiamo la forma rettangolare**. La classe `Shape` accetta il riferimento al documento e un `ShapeType`. Qui scegliamo `RECTANGLE` e impostiamo larghezza/altezza in punti (1 pt ≈ 1/72 inch).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Perché impostare `WrapType.INLINE`? Il wrapping inline fa comportare la forma come un carattere nel paragrafo, garantendo che si muova con il testo circostante. Se ti serve un comportamento flottante, passa a `WrapType.SQUARE` o `WrapType.TOP_BOTTOM`.

## Passo 3: **Apply shadow effect** – dare profondità al rettangolo

Un rettangolo piatto appare… beh, piatto. Aggiungere un’ombra lo fa risaltare. **Applicheremo l’effetto ombra** creando un’istanza `ShadowEffect`, poi regolando le sue proprietà visive.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Analizziamo un po’ il codice:

- **Color** – `Color.getGray(0.5)` restituisce un grigio al 50 %, neutro e adatto alla maggior parte degli sfondi.  
- **OffsetX/Y** – Valori positivi spostano l’ombra a destra e in basso; valori negativi la muoverebbero a sinistra/alto.  
- **BlurRadius** – Valori più alti creano un’ombra più morbida e diffusa.  
- **Transparency** – Varia da `0` (opaco) a `1` (completamente trasparente). Qui abbiamo scelto `0.3` per un effetto delicato.

## Passo 4: **Add shadow to shape** – collegare l’effetto

Creare l’effetto non basta; dobbiamo **aggiungere l’ombra alla forma** assegnando l’oggetto `ShadowEffect` al rettangolo.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

In background, questa chiamata aggiorna il markup OpenXML sottostante (`<w:shdw>`) che Word utilizza per renderizzare le ombre. Se ispezioni il `.docx` salvato, vedrai un elemento `<w:effect>` popolato con i parametri impostati.

## Passo 5: **Set shape transparency** – opzionale ma spesso utile

A volte vuoi che il rettangolo stesso sia semi‑trasparente, lasciando trasparire il testo di sfondo. La classe `Shape` espone `setFillColor` e `setFillTransparency`. Ecco un esempio rapido che rende il rettangolo al 40 % trasparente:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Perché potresti farlo? Immagina una filigrana o un evidenziatore dove il contenuto sottostante deve rimanere leggibile. Regola il valore di trasparenza in base al tuo linguaggio di design.

## Passo 6: Inserisci la forma nel documento

Abbiamo costruito il rettangolo, aggiunto l’ombra e (facoltativamente) impostato la trasparenza. L’ultimo passo è **aggiungere la forma alla prima sezione del documento**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Aggiungere la forma al body la posiziona alla fine del primo paragrafo. Se ti serve un punto di inserimento specifico, recupera il `Paragraph` target e usa `insertBefore` o `insertAfter`.

## Passo 7: Salva il documento – vedi il risultato

Tutto questo lavoro culmina in una singola chiamata `save`. Scegli un percorso che abbia senso per il tuo ambiente.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Apri il risultato `ShadowShape.docx` in Microsoft Word o LibreOffice, e vedrai un rettangolo nitido con una leggera ombra grigia, leggermente trasparente se hai mantenuto il passo opzionale. L’aspetto corrisponde ai parametri definiti programmaticamente.

---

![crea forma rettangolare con ombra in un documento Word](https://example.com/images/rectangle-shadow.png "crea forma rettangolare con ombra")

*Testo alternativo immagine:* **crea forma rettangolare con ombra** – rappresentazione visiva del risultato finale.

## Domande frequenti & casi particolari

### E se volessi un colore d’ombra diverso?

Basta modificare la chiamata `setColor`:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Ricorda che ombre troppo vivide possono apparire poco professionali; tonalità sobrie funzionano di solito meglio.

### Posso applicare la stessa ombra a più forme?

Sì. Crea un’istanza `ShadowEffect`, configurala, poi riutilizzala:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Evita di mutare il `ShadowEffect` dopo averlo associato ad altre forme, a meno che tu non intenda aggiornare tutte contemporaneamente.

### Come cambio dinamicamente il raggio di sfocatura dell’ombra?

Esporre uno slider UI che mappa a `setBlurRadius`. Valori tra `2` e `12` sono tipici; numeri più alti producono un “bagliore” anziché un’ombra netta.

### E se la forma deve fluttuare anziché essere inline?

Cambia il tipo di wrapping:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Le forme flottanti offrono più libertà di layout ma richiedono logica di posizionamento aggiuntiva.

## Esempio completo funzionante

Di seguito trovi il programma completo, pronto per il copy‑paste, che incorpora tutti i passaggi discussi. Eseguilo come una normale applicazione Java.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Output atteso:** Quando apri `ShadowShape.docx`, vedrai un rettangolo bianco, 200 × 100 pt, centrato nel primo paragrafo, con un’ombra grigia media spostata di 5 pt, sfocata con raggio 8, e al 30 % di trasparenza. Il rettangolo stesso è al 40 % di trasparenza, permettendo al testo sottostante di intravedersi.

## Conclusioni

Abbiamo appena **creato una forma rettangolare** da zero, **aggiunto ombra alla forma**, **applicato l’effetto ombra**, e persino **impostato la trasparenza della forma**—tutto mentre **creavamo un documento vuoto** come base. L’approccio è lineare, si basa sull’API fluida di Aspose.Words, e può essere esteso a cerchi, stelle o poligoni personalizzati.

Qual è il prossimo passo nella tua roadmap? Prova a sostituire `ShapeType.RECTANGLE` con `ShapeType.OVAL` per generare cerchi con ombra, o sperimenta riempimenti a gradiente per

## Cosa dovresti imparare dopo?


I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci alternativi nei tuoi progetti.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}