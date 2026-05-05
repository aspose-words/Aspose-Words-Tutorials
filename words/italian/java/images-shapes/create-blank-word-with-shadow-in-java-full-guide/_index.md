---
category: general
date: 2026-05-04
description: Crea un documento Word vuoto in Java e impara a impostare il colore dell'ombra,
  la sfocatura e lo spostamento per le forme – breve tutorial.
draft: false
keywords:
- create blank word
- set shadow color
- how to add shadow
- how to set blur
- how to set offset
language: it
og_description: Crea un documento Word vuoto in Java e impara come impostare il colore
  dell'ombra, la sfocatura e lo spostamento per le forme. Segui questo tutorial passo
  passo.
og_title: Crea una parola vuota con ombra in Java – Guida completa
tags:
- Aspose.Words
- Java
- Document Automation
title: Crea una parola vuota con ombra in Java – Guida completa
url: /it/java/images-shapes/create-blank-word-with-shadow-in-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word vuoto con ombra in Java – Guida completa

Ti è mai capitato di dover **create blank word** da codice e renderli un po' più eleganti? Non sei il solo. In molti progetti di reporting o generazione di template, la prima cosa che si fa è creare un documento Word vuoto, per poi aggiungere una forma con ombra per dare un aspetto più curato.  

In questo tutorial vedremo passo passo come creare un documento Word vuoto usando Aspose.Words per Java, **come aggiungere ombra** a una forma, e i dettagli di **set shadow color**, **how to set blur** e **how to set offset**. Alla fine avrai un file `.docx` pronto all'uso che mostra un rettangolo con un'ombra rossa, leggermente sfocata e semi‑trasparente.

## Cosa ti serve

- **Aspose.Words per Java** (qualsiasi versione recente; il codice funziona con 23.9+)
- JDK 8 o superiore
- Un IDE o un semplice editor di testo più un terminale
- Conoscenze di base di Java—nulla di complicato, solo la capacità di eseguire un metodo `main`

Non è necessaria alcuna configurazione Maven o Gradle aggiuntiva per la demo; basta aggiungere il JAR di Aspose al classpath e sei pronto.

---

![esempio di documento Word vuoto con ombra](image-placeholder.png){: .center alt="esempio di documento Word vuoto con ombra"}

## Crea documento Word vuoto – Inizializzare il Document

Il primo passo è creare un nuovo file Word vuoto. Pensalo come una tela fresca dove potrai successivamente disegnare forme, tabelle o testo.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Perché è importante:** `Document` rappresenta l'intero pacchetto `.docx`. Creandolo con il costruttore di default stai effettivamente **create blank word** – non c'è contenuto, nessuna sezione, solo la struttura del file pronta per essere popolata.

## Come aggiungere ombra a una forma

Ora che abbiamo un documento pulito, inseriamo un rettangolo che conterrà la nostra ombra. È qui che inizia la magia visiva.

```java
        // Step 3: Insert a rectangle shape that will receive a custom shadow
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

> **Consiglio:** La chiamata `insertShape` aggiunge automaticamente la forma al paragrafo corrente, quindi non devi gestire il posizionamento manualmente a meno che non desideri un posizionamento assoluto.

## Impostare il colore dell'ombra – far risaltare l'ombra

Un'ombra senza colore è solo una sfocatura grigia, che può apparire piatta. Impostando il colore dell'ombra puoi allinearla al brand o semplicemente farla risaltare.

```java
        // Step 4a: Make the shadow visible and set its color
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.RED); // set shadow color
```

> **Cosa succede:** `ShadowFormat` controlla ogni aspetto visivo dell'ombra. Abilitare `setVisible(true)` attiva l'effetto, e `setColor` ti permette di scegliere qualsiasi `java.awt.Color`. Nel nostro esempio abbiamo scelto il rosso per dimostrare chiaramente **set shadow color**.

## Come impostare la sfocatura per un effetto delicato

Un'ombra netta e a bordi duri può apparire aggressiva. Aggiungere la sfocatura ammorbidisce i bordi, conferendo un aspetto più naturale.

```java
        // Step 4b: Define how fuzzy the shadow should be
        rectangleShape.getShadowFormat().setBlur(5.0); // how to set blur
```

> **Perché la sfocatura è importante:** Il valore di `setBlur` è misurato in punti. Un valore di `5.0` crea una diffusione leggera; aumentalo per un'ombra più soffusa, diminuiscilo per un contorno più nitido.

## Come impostare l'offset – posizionare l'ombra

Gli offset determinano dove l'ombra cade rispetto alla forma. Pensali come spostamenti X‑ e Y‑.

```java
        // Step 4c: Position the shadow horizontally and vertically
        rectangleShape.getShadowFormat().setOffsetX(8.0); // how to set offset (horizontal)
        rectangleShape.getShadowFormat().setOffsetY(8.0); // how to set offset (vertical)
```

> **Spiegazione dell'offset:** Un X positivo sposta l'ombra a destra, un Y positivo la sposta verso il basso. Gioca con numeri negativi se vuoi che l'ombra appaia sul lato opposto.

## Regolare la trasparenza

Se desideri che l'ombra sia meno dominante, regola la sua trasparenza. Questo passaggio non è un requisito di parola chiave ma completa il controllo visivo.

```java
        // Optional: Make the shadow semi‑transparent (30 % transparent)
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

## Salvare il documento – vedere il risultato

Infine, scrivi il documento su disco. Otterrai un `.docx` che potrai aprire in Word, LibreOffice o qualsiasi visualizzatore che supporti il formato.

```java
        // Step 5: Save the document with the shaped shadow
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

> **Cosa dovresti vedere:** Apri `ShadowShape.docx`. Una singola pagina mostrerà un rettangolo di 150 × 80 pt con un'ombra rossa, leggermente sfocata, spostata di 8 pt verso il basso e a destra. L'ombra è al 30 % trasparente, quindi il rettangolo rimane chiaramente visibile.

---

## Domande frequenti e casi particolari

### E se avessi bisogno di una forma diversa?

Sostituisci `ShapeType.RECTANGLE` con qualsiasi altro valore enum (`ELLIPSE`, `CLOUD`, `CALLOUT`, ecc.). Le impostazioni dell'ombra funzionano identicamente su tutte le forme.

### Posso applicare la stessa ombra a più forme senza ripetere il codice?

Assolutamente. Crea un metodo di supporto:

```java
private static void applyShadow(Shape shape, java.awt.Color color,
                                double blur, double offsetX, double offsetY,
                                double transparency) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(color);
    shape.getShadowFormat().setBlur(blur);
    shape.getShadowFormat().setOffsetX(offsetX);
    shape.getShadowFormat().setOffsetY(offsetY);
    shape.getShadowFormat().setTransparency(transparency);
}
```

Poi chiama `applyShadow(rectangleShape, Color.RED, 5.0, 8.0, 8.0, 0.3);` per qualsiasi forma.

### Funziona con versioni più vecchie di Aspose?

L'API `ShadowFormat` è stabile dalla versione 19.8, quindi dovresti essere a posto con la maggior parte delle release recenti. Se usi una build molto vecchia, controlla il Javadoc di `ShadowFormat` per verificare i nomi dei metodi.

### Come esportare in PDF mantenendo l'ombra?

Basta chiamare `document.save("output.pdf");` dopo aver creato la forma. Aspose.Words rende correttamente le ombre in PDF, preservando sfocatura e trasparenza.

---

## Riepilogo – create blank word con ombra personalizzata

Abbiamo iniziato con **create blank word** usando `new Document()`, poi inserito un rettangolo, **set shadow color**, imparato **how to add shadow**, regolato **how to set blur** e infine aggiustato **how to set offset** per posizionarla perfettamente. Il codice completo e eseguibile è nello snippet sopra, e il file risultante dimostra chiaramente l'effetto.

---

## Qual è il prossimo passo?

- **Sperimenta altre proprietà dell'ombra** come `ShadowFormat.setStyle(ShadowStyle.OUTER)` per stili visivi diversi.
- **Combina più forme**, ognuna con la propria ombra, per costruire diagrammi complessi.
- **Aggiungi testo all'interno della forma** usando `builder.insertHtml("<b>Hello</b>")` prima di inserire la forma, poi applica la stessa logica dell'ombra.
- **Esplora altre opzioni di formattazione** come lo stile della linea, il colore di riempimento o i riempimenti a gradiente—Aspose.Words offre un'API ricca per tutti questi casi.

Sentiti libero di modificare il raggio di sfocatura, gli offset o i colori finché l'ombra non si adatta perfettamente al linguaggio di design del tuo documento. Buona programmazione, e che i tuoi file Word generati siano sempre un po' più raffinati!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}