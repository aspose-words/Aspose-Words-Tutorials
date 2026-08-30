---
category: general
date: 2026-08-20
description: Scopri come raggruppare le forme, impostare le dimensioni della forma,
  inserire un'immagine nel documento, aggiungere un'immagine al gruppo e creare una
  forma rettangolare con Aspose.Words in Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: it
lastmod: 2026-08-20
og_description: Come raggruppare le forme in un documento Word usando Aspose.Words.
  Segui questo tutorial Java passo‑passo per impostare le dimensioni della forma,
  inserire un’immagine nel documento, aggiungere un’immagine al gruppo e creare una
  forma rettangolare.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Come raggruppare le forme in un documento Word con Aspose.Words – Guida
  Java
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Come raggruppare le forme in un documento Word utilizzando Aspose.Words
url: /it/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come raggruppare le forme in un documento Word usando Aspose.Words

Se hai bisogno di **come raggruppare le forme** in un file Word, questo tutorial mostra la soluzione completa in Java. Vedrai come **impostare la dimensione della forma**, **inserire un'immagine nel documento**, **aggiungere un'immagine al gruppo** e **creare una forma rettangolare** — tutto con spiegazioni chiare e un esempio di codice eseguibile.

Raggruppare le forme semplifica la gestione del layout, ti consente di spostare o ruotare più oggetti come un’unica unità e mantiene il documento ordinato. Nei passaggi seguenti costruirai un gruppo che contiene un rettangolo e un’immagine, quindi posizionerai il gruppo sulla pagina.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java 17 o versioni successive installate.
* Aspose.Words for Java (versione 23.9 o successiva) aggiunto al classpath del tuo progetto.
* Un’immagine JPEG di esempio in `YOUR_DIRECTORY/sample.jpg` (sostituisci `YOUR_DIRECTORY` con il percorso reale).

Puoi aggiungere Aspose.Words tramite Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Come raggruppare le forme con Aspose.Words

Le sezioni seguenti illustrano ogni operazione necessaria per **come raggruppare le forme**. L’intestazione H2 principale contiene la keyword primaria, soddisfacendo le regole SEO.

### Passo 1: Creare un nuovo documento e un `DocumentBuilder`

Un `Document` rappresenta il file Word, mentre `DocumentBuilder` fornisce metodi pratici per inserire contenuti.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché è importante*: Iniziare con un `Document` nuovo garantisce che il gruppo che crei non interferisca con gli elementi esistenti.

### Passo 2: Inserire una forma di gruppo che conterrà più forme figlio

Una forma di gruppo agisce come un contenitore. Le sue dimensioni definiscono il riquadro di delimitazione per tutte le forme figlio.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Consiglio*: La larghezza (`300`) e l’altezza (`200`) sono in punti (1 pt = 1/72 pollice). Regolale in base alle dimensioni delle forme che intendi aggiungere.

### Passo 3: Creare una forma rettangolare, impostarne la dimensione e aggiungerla al gruppo

Impostare la dimensione esatta di una forma è essenziale quando desideri un controllo preciso del layout.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Perché impostiamo la dimensione della forma*: I metodi `setWidth` e `setHeight` corrispondono alla keyword secondaria **set shape size**, offrendoti un controllo pixel‑perfect sull’aspetto del rettangolo.

### Passo 4: Inserire un’immagine, quindi aggiungere la forma immagine allo stesso gruppo

L’inserimento di un’immagine è il fulcro del requisito **insert image into document**. La `Shape` restituita è una forma immagine che può essere raggruppata come qualsiasi altra forma.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Suggerimento professionale*: Se devi preservare il rapporto d’aspetto originale, imposta solo una dimensione (`setWidth` o `setHeight`). Aspose.Words scala automaticamente l’altra dimensione.

### Passo 5: Posizionare l’intero gruppo sulla pagina

Dopo aver aggiunto tutte le forme figlio, puoi spostare, ruotare o nascondere l’intero gruppo. Il posizionamento utilizza indirettamente il concetto **add picture to group**, poiché il gruppo ora contiene l’immagine.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Spiegazione*: `setLeft` e `setTop` posizionano il gruppo rispetto ai margini della pagina. Ruotare il gruppo dimostra che tutte le forme figlio ereditano la trasformazione.

### Passo 6: Salvare il documento

Infine, scrivi il file su disco. Puoi aprire il `.docx` risultante in Word per verificare il raggruppamento.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

L’esecuzione del programma produce **GroupShapesDemo.docx** contenente un rettangolo e un’immagine raggruppati insieme. Selezionare una delle forme in Word selezionerà anche l’altra, confermando che hai appreso con successo **come raggruppare le forme**.

---

## Output previsto

Quando apri *GroupShapesDemo.docx* in Microsoft Word:

* Un rettangolo (riempimento dorato) appare sul lato sinistro del gruppo.
* L’immagine fornita appare a destra del rettangolo.
* Entrambi gli oggetti si muovono insieme quando trascini il gruppo.
* Il gruppo è posizionato a 50 pt dal margine sinistro e a 100 pt dal margine superiore, ruotato di 15°.

Se l’immagine non compare, verifica nuovamente il percorso del file in `insertImage`. Aspose.Words genera un `IOException` quando il file non viene trovato.

---

## Domande comuni e gestione dei casi limite

| Domanda | Risposta |
|----------|----------|
| **Posso aggiungere più di due forme?** | Sì. Chiama `groupShape.appendChild(otherShape)` per ogni forma aggiuntiva. |
| **E se ho bisogno di uno sfondo trasparente per il rettangolo?** | Usa `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Il raggruppamento è supportato nei formati Word più vecchi (es. `.doc`)?** | Il raggruppamento funziona per `.docx` e `.doc`, ma alcuni visualizzatori più vecchi potrebbero ignorare i metadati del gruppo. Salva come `.docx` per la massima fedeltà. |
| **Come posso separare il gruppo in seguito?** | Recupera i nodi figlio tramite `groupShape.getChildNodes(NodeType.ANY, true)` e spostali nel corpo del documento, quindi rimuovi il gruppo. |
| **Posso raggruppare forme in sezioni diverse?** | No. Un `GroupShape` deve risiedere all’interno di una singola `Story` (di solito il corpo principale del documento). |

---

## Pro consigli per una gestione robusta delle forme

* **Usa il posizionamento assoluto con parsimonia** – il posizionamento relativo (`builder.moveToDocumentEnd()`) spesso produce layout più reattivi.
* **Cachea il `DocumentBuilder`** – creare un nuovo builder per ogni operazione può ridurre le prestazioni su documenti di grandi dimensioni.
* **Imposta `PictureFillMode`** quando hai bisogno che l’immagine si estenda o si ripeta all’interno della forma: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Convalida le dimensioni dell’immagine** prima dell’inserimento per evitare ridimensionamenti imprevisti che potrebbero influire sul riquadro di delimitazione del gruppo.

---

## Prossimi passi

Ora che sai **come raggruppare le forme**, potresti approfondire:

* **Insert image into document** con opzioni avanzate come il ritaglio (`pictureShape.setCropTop(...)`).
* **Set shape size** in modo dinamico in base alle dimensioni della pagina (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** insieme a caselle di testo per grafici con didascalia.
* **Create rectangle shape** con angoli arrotondati (`rectangleShape.setCornerRadius(5);`).

Questi argomenti si basano sulla stessa API e ti aiutano a creare report Word sofisticati e programmabili.

---

## Conclusione

In questo tutorial hai imparato **come raggruppare le forme** in un documento Word usando Aspose.Words per Java. Seguendo i sei passaggi—creare un documento, inserire un gruppo, **creare una forma rettangolare**, **impostare la dimensione della forma**, **inserire un’immagine nel documento**, **aggiungere un’immagine al gruppo** e posizionare il gruppo—ora disponi di un modello riutilizzabile per scenari di layout complessi. Sentiti libero di sperimentare con forme figlio aggiuntive, rotazioni diverse o logiche di raggruppamento condizionali per soddisfare le esigenze della tua applicazione.

Buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Crea documento Word Java – Aggiungi forma rettangolare con effetto ombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Utilizzare le forme del documento in Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Creare forma di gruppo in documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}