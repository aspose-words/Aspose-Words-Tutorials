---
category: general
date: 2026-10-16
description: Crea un documento Word vuoto con Java e impara come aggiungere un pulsante
  ActiveX, impostarne la didascalia e regolare le sue dimensioni usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: it
lastmod: 2026-10-16
og_description: Crea un documento Word vuoto con Java, quindi aggiungi un pulsante
  ActiveX, imposta la sua didascalia e definisci le sue dimensioni usando Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Crea un documento Word vuoto e incorpora un pulsante ActiveX – Guida Java
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Crea un documento Word vuoto e aggiungi un pulsante ActiveX (Java)
url: /it/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto e aggiungi un pulsante ActiveX (Java)

Se hai bisogno di **creare un documento Word vuoto** programmaticamente, questa guida ti mostra come farlo con Java e Aspose.Words. Imparerai anche come **aggiungere un pulsante ActiveX**, **impostare la didascalia del pulsante** e **impostare le dimensioni del pulsante** in modo che il controllo appaia esattamente come ti aspetti.

Questo tutorial copre:

* Inizializzare un file Word vuoto con Aspose.Words per Java.  
* Inserire un controllo ActiveX `CommandButton`.  
* Configurare la didascalia e le dimensioni del pulsante.  
* Salvare il file `.docx` finale.

Dovresti avere conoscenze di base di Java e una versione recente della libreria Aspose.Words per Java (il codice funziona con la 23.9 e successive). Non sono richieste dipendenze aggiuntive.

![Crea un documento Word vuoto con un pulsante ActiveX](/images/activex-button-example.png){: .align-center alt="Crea un documento Word vuoto con un pulsante ActiveX"}

## Crea un documento Word vuoto con Aspose.Words

Il primo passo è istanziare un oggetto `Document` vuoto. Questo oggetto rappresenta l'intero file Word in memoria e fornisce la classe `DocumentBuilder` per la modifica.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Perché è importante:**  
Creare un documento vuoto ti fornisce una tela pulita, evitando stili o sezioni nascosti che potrebbero interferire con i calcoli di layout successivi.

## Aggiungi un pulsante ActiveX al documento

Aspose.Words ti consente di incorporare controlli ActiveX legacy tramite la classe `Forms2OleControl`. Il codice seguente inserisce un controllo `CommandButton` nella posizione corrente del cursore.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Suggerimento:**  
Il valore `setOleClassName` `"Forms.CommandButton.1"` è il ProgID per il pulsante standard di Microsoft Forms. Usare un ProgID diverso (ad es., `"Forms.CheckBox.1"`) inserirebbe un tipo di controllo differente.

## Imposta la didascalia del pulsante

Una didascalia è il testo che appare sulla superficie del pulsante. Puoi cambiarla in qualsiasi momento prima di salvare il documento.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Perché ti serve:**  
Gli utenti comprendono un controllo solo quando il suo scopo è chiaro. Impostare una didascalia significativa migliora l'usabilità, soprattutto quando il documento viene aperto in Word su Windows.

## Imposta le dimensioni del pulsante

Posizione e dimensione sono specificate in punti (1 punto = 1/72 di pollice). Regola i valori per adattarli al tuo layout.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Varianti comuni:**

| Scenario | Regolazione |
|----------|------------|
| Pulsante più grande per schermi touch | Aumenta `setWidth` e `setHeight` proporzionalmente |
| Pulsante centrato nella pagina | Calcola `left = (pageWidth - width) / 2` |
| Più pulsanti in una colonna | Incrementa `setTop` per ogni nuovo pulsante |

## Salva il documento contenente il pulsante ActiveX

Infine, scrivi il documento su disco. Il formato `.docx` preserva il controllo ActiveX per le versioni Windows di Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Risultato atteso:**  
Aprendo `ActiveXCommandButton.docx` in Word (Windows) si visualizza una pagina vuota con un pulsante cliccabile etichettato **Click Me** posizionato a 100 pt dal margine sinistro e 200 pt dal margine superiore.

## Esempio completo, eseguibile

Copia l'intera classe qui sotto nel tuo IDE, aggiungi il JAR di Aspose.Words per Java al classpath del progetto e eseguilo.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Eseguendo il programma viene generato `ActiveXCommandButton.docx` nella directory di lavoro. Aprilo con Microsoft Word (Windows) per verificare che il pulsante appaia esattamente come configurato.

## Perché questo approccio è consigliato

* **Semplicità:** Viene utilizzata solo l'API core di Aspose.Words; non è necessario alcun interop COM o librerie aggiuntive.  
* **Portabilità:** Il codice funziona su qualsiasi piattaforma che supporta Java, sebbene il controllo ActiveX funzioni solo sulle versioni Windows di Word.  
* **Manutenibilità:** Tutte le proprietà (didascalia, dimensioni, posizione) sono impostate tramite metodi chiari e auto‑documentanti, rendendo le future modifiche semplici.

## Problemi comuni e come evitarli

| Problema | Risoluzione |
|----------|------------|
| Il pulsante non appare in Word su macOS o Linux | I controlli ActiveX sono solo per Windows. Usa un controllo diverso (ad es., un content control) per documenti multipiattaforma. |
| La didascalia è troncata | Assicurati che la larghezza del pulsante sia sufficiente per il testo; aumenta `setWidth` o usa una didascalia più breve. |
| Il pulsante si sovrappone ad altri contenuti | Regola i valori `setTop` e `setLeft`, oppure inserisci un nuovo paragrafo prima del controllo per dargli spazio proprio. |

## Prossimi passi

Ora che puoi **creare un documento Word vuoto**, **aggiungere un pulsante ActiveX**, **impostare la didascalia del pulsante** e **impostare le dimensioni del pulsante**, potresti esplorare:

* Aggiungere codice di gestione eventi tramite macro VBA (richiede l'incorporamento di un modulo macro).  
* Inserire più controlli in un layout a tabella per documenti simili a moduli.  
* Utilizzare le API **FormField** di Aspose.Words per soluzioni di modulo multipiattaforma.

Sperimenta con diverse dimensioni, posizioni e didascalie per adattarle al tuo design specifico del documento. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word Java – Aggiungi forma rettangolare con effetto ombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aggiungi una filigrana a un documento usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}