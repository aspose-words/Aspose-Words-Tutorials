---
category: general
date: 2026-07-16
description: Imposta la dimensione del pulsante programmaticamente in un documento
  Word usando Aspose.Words per Java. Scopri come inserire un pulsante ActiveX, impostare
  la posizione del pulsante e altro.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: it
lastmod: 2026-07-16
og_description: Imposta la dimensione del pulsante in un documento Word usando Java.
  Questa guida passo passo mostra come inserire un pulsante ActiveX, impostare la
  posizione del pulsante e aggiungere il pulsante programmaticamente.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Imposta la dimensione del pulsante in Word con Java – Tutorial completo
  su Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Imposta la dimensione del pulsante in Word con Java – Guida completa ad Aspose.Words
url: /it/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Imposta la Dimensione del Pulsante in Word con Java – Guida Completa a Aspose.Words

Ti sei mai chiesto come **impostare la dimensione del pulsante** all'interno di un file Word senza aprire l'interfaccia utente? Non sei l'unico. Quando devi generare un documento compilato al volo—ad esempio, un pacchetto di onboarding con un pulsante “Submit”—farlo programmaticamente fa risparmiare ore di lavoro manuale.

In questo tutorial percorreremo i passaggi esatti per **inserire un pulsante ActiveX**, regolare le sue dimensioni, posizionarlo correttamente e infine salvare il file. Alla fine sarai in grado di **aggiungere pulsanti** in modo programmatico a qualsiasi documento Word usando Aspose.Words per Java.

## Prerequisiti – Cosa Serve Prima di Iniziare

- **Java Development Kit (JDK) 8+** – il codice funziona su qualsiasi JDK recente.
- **Aspose.Words for Java** library (scarica l'ultimo JAR dal sito ufficiale).  
- Un **IDE** a tua scelta—IntelliJ IDEA, Eclipse, o anche un semplice editor di testo funziona.
- Familiarità di base con la sintassi Java; non è necessario una conoscenza approfondita dell'automazione di Word.

> *Consiglio professionale:* Mantieni il JAR di Aspose.Words nel classpath del tuo progetto, altrimenti otterrai `ClassNotFoundException` non appena proverai a importare `com.aspose.words.*`.

## Passo 1: Crea un Nuovo Documento Word

La prima cosa che facciamo è creare un documento vuoto e un `DocumentBuilder`. Pensa al builder come a una penna che ci permette di disegnare qualsiasi cosa all'interno del file.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Perché è importante:** L'oggetto `Document` rappresenta l'intero file .docx, mentre il `DocumentBuilder` è il cavallo di battaglia che ci permette di inserire paragrafi, tabelle e—sì—controlli ActiveX.

## Passo 2: Inserisci Pulsante ActiveX – Il Momento “Insert ActiveX Button”

Ora inseriamo effettivamente **un pulsante activex** nel documento. Aspose.Words espone un metodo comodo `insertForms2OleControl` che restituisce un oggetto `Forms2OleControl`.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *Cosa succede dietro le quinte?* `Forms2OleControlType.COMMAND_BUTTON` indica a Word che vogliamo un classico CommandButton, lo stesso tipo che inseriresti dalla scheda Developer nell'interfaccia.

## Passo 3: Imposta Dimensione e Posizione del Pulsante – La Logica Principale “Set Button Size”

Qui è dove la parola chiave principale brilla. Imposteremo **la dimensione del pulsante** e anche **la posizione del pulsante** in modo che il controllo appaia esattamente dove lo desideriamo nella pagina.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Perché dovresti interessartene:** I punti sono l'unità di misura nativa in Word (1 punto = 1/72 di pollice). Modificando `setLeft`, `setTop`, `setWidth` e `setHeight` ottieni un controllo pixel‑perfect—niente più “sembra giusto sul mio schermo ma non sulla stampante”.

> *Errore comune:* Dimenticare di impostare larghezza o altezza lascerà il pulsante alle dimensioni predefinite, che possono essere troppo piccole per fare clic. Specifica sempre entrambi.

## Passo 4: Salva il Documento – “Create Word Document Button” Completato

Infine, scriviamo il file su disco. Il nome suggerisce che stiamo **creando un pulsante in un documento Word** all'interno di un .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Quando apri `CommandButtonDemo.docx` in Microsoft Word, vedrai un pulsante **Submit** posizionato a 100 pt dal bordo sinistro e 150 pt dall'alto, con dimensioni di 80 × 30 pt. Cliccarlo nell'interfaccia attiverà il comportamento predefinito di ActiveX (che potrai collegare successivamente con VBA se necessario).

### Screenshot dell'Uscita Prevista

![Documento Word che mostra il pulsante inserito con la dimensione impostata](https://example.com/images/set-button-size.png "Screenshot di un file Word dove la dimensione del pulsante è stata impostata usando Aspose.Words per Java")

*Testo alternativo:* impostare la dimensione del pulsante in un documento Word usando Java

## Passo 5 (Opzionale): Aggiungi Altri Controlli o Stile al Pulsante

Se hai bisogno di **aggiungere pulsanti** programmaticamente oltre a un singolo pulsante Submit, ripeti semplicemente il blocco di inserimento con nuovi nomi e didascalie. Puoi anche regolare il font, il colore di sfondo, o persino collegare macro VBA in seguito.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Suggerimento:* Mantieni tutte le dimensioni dei pulsanti coerenti per un aspetto professionale. Un modo rapido è memorizzare larghezza/altezza in costanti.

## Domande Frequenti & Casi Limite

### “Posso impostare la dimensione del pulsante usando i centimetri invece dei punti?”

L'API di Word accetta solo punti, ma puoi convertire i centimetri in punti (`points = cm * 28.3465`). Scrivi un piccolo metodo di supporto se preferisci le unità metriche.

### “E se ho bisogno che il pulsante appaia in una pagina specifica?”

Dopo aver inserito il pulsante, puoi spostare il cursore a una pagina specifica usando `builder.moveToPage(pageNumber)`. Inserisci il controllo subito dopo lo spostamento, quindi imposta la sua posizione come mostrato sopra.

### “Funziona con file .doc (Word 97‑2003)?”

Sì—Aspose.Words gestisce automaticamente i formati più vecchi. Basta cambiare l'estensione del file in `doc.save("Demo.doc")`.

## Esempio Completo e Eseguibile

Di seguito trovi l'intero programma che puoi copiare‑incollare in una classe Java e eseguire immediatamente (supponendo che il JAR di Aspose.Words sia nel classpath).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Esegui il programma, apri il `CommandButtonDemo.docx` generato, e vedrai due pulsanti dimensionati ordinatamente pronti per l'interazione.

## Conclusione – Hai Padronato l'Impostazione della Dimensione del Pulsante in Word

Abbiamo appena percorso una soluzione completa, end‑to‑end, per **impostare la dimensione del pulsante** e **impostare la posizione del pulsante** usando Aspose.Words per Java. Seguendo i passaggi puoi **inserire un pulsante activex**, **aggiungere pulsanti** programmaticamente, e infine **creare pulsanti in documenti Word** che si comportano esattamente come desideri.

Cosa fare dopo? Prova a incorporare il pulsante all'interno di una cella di tabella, o allega una macro VBA che valida i campi del modulo prima dell'invio. Lo stesso schema funziona per altri controlli ActiveX come caselle di controllo o caselle combinate—basta sostituire `Forms2OleControlType.COMMAND_BUTTON` con il valore enum appropriato.

Se incontri problemi, lascia un commento qui sotto. Buona programmazione e goditi il potere della creazione automatizzata di documenti Word!

## Cosa Dovresti Imparare Dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come impostare LoadOptions in Aspose.Words per Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Come rimuovere i piè di pagina dai documenti Word usando Aspose.Words per Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java: Guida Completa all'Elaborazione di Documenti Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}