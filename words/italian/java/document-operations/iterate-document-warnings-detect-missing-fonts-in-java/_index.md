---
category: general
date: 2026-04-28
description: Iterare gli avvisi del documento in un file Word per rilevare i caratteri
  mancanti, recuperare i nomi dei caratteri mancanti e stampare i dettagli dei caratteri
  mancanti utilizzando Aspose.Words per Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: it
og_description: Itera gli avvisi del documento per trovare i font mancanti, recupera
  i nomi dei font mancanti e stampa i dettagli dei font mancanti con un esempio Java
  completo.
og_title: 'Itera gli avvisi del documento: rileva i font mancanti in Java'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Iterare gli avvisi del documento: rilevare i font mancanti in Java'
url: /it/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Itera gli avvisi del documento – Rileva i font mancanti in Java

Hai mai dovuto **iterare gli avvisi del documento** aprendo un file Word e ti sei chiesto quali font mancano? Non sei l’unico. I font mancanti possono rovinare l’aspetto di un report e, senza un modo per individuarli, potresti distribuire un documento che non assomiglia affatto all’originale.  

In questo tutorial ti mostreremo come **rilevare i font mancanti** caricando un documento Word, iterando i suoi avvisi, recuperando i nomi dei font mancanti e infine stampando le informazioni sui font mancanti—tutto con Aspose.Words per Java.  

Copriamo tutto, dalla prima riga di codice all’output previsto sulla console, così potrai copiare‑incollare una soluzione funzionante nel tuo progetto subito. Nessuna documentazione aggiuntiva necessaria.

## Prerequisiti

- Java 8 o versioni successive installate.  
- Libreria Aspose.Words per Java (l’ultima versione al 2026‑04‑28).  
- Un file Word che potrebbe contenere font non installati sulla tua macchina (ad es., `doc-with-missing-font.docx`).

Se hai già tutto questo, ottimo—sei pronto a **caricare il documento Word** e iniziare a iterare.

## Passo 1 – Carica il documento Word con le opzioni predefinite

Prima di poter **iterare gli avvisi del documento**, il file deve essere caricato in memoria. Aspose.Words ti consente di farlo con una singola chiamata al costruttore. L’uso delle `LoadOptions` predefinite è di solito sufficiente, ma mostreremo la creazione esplicita per chiarezza.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Perché è importante:**  
> Il caricamento del documento fa sì che Aspose.Words esegua la scansione del file alla ricerca di risorse non risolvibili, come i font non installati localmente. Questi problemi vengono memorizzati come **avvisi**, che **itereremo** nel passo successivo.

## Passo 2 – Itera gli avvisi del documento per trovare i problemi di font

Ora arriva il cuore della soluzione: cicliamo tutti gli avvisi che la libreria ha raccolto durante il caricamento. Gli oggetti `WarningInfo` ci dicono cosa è andato storto e possiamo filtrare per `FontSubstitutionWarning` per **rilevare i font mancanti**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Consiglio professionale:** Il controllo `instanceof` garantisce che gestiamo solo gli avvisi relativi ai font, ignorando gli altri, ad esempio problemi di caricamento delle immagini. Questo rende il ciclo efficiente e mantiene l’output focalizzato sui font per i quali devi **recuperare le informazioni sui font mancanti**.

### Output previsto sulla console

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Se il documento non contiene font mancanti, il ciclo termina silenziosamente—nulla da **stampare sui font mancanti**.

## Passo 3 – Perché non limitarsi a catturare un’eccezione?

Potresti chiederti: “Perché non avvolgere la chiamata `new Document(...)` in un try‑catch e cercare un’eccezione?” La risposta è duplice:

1. **Informazioni granulari:** Le eccezioni indicano solo che qualcosa è fallito. Gli avvisi forniscono il nome esatto del font e il fallback scelto da Aspose.Words.  
2. **Problemi non fatali:** I font mancanti sono solitamente non fatali; il documento si carica comunque, ma la fedeltà visiva ne risente. **Iterando gli avvisi del documento**, mantieni la possibilità di elaborare il resto del file.

## Passo 4 – Estendere l’esempio: raccogliere i font mancanti in una lista

A volte hai bisogno dei font mancanti per ulteriori elaborazioni—magari per incorporarli o per avvisare l’utente tramite UI. Ecco una piccola modifica che raccoglie i nomi in un `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Ora disponi di un modo pulito per **recuperare i font mancanti** in modo programmatico, che puoi inviare a un modulo di reportistica o a una procedura guidata di installazione dei font.

## Passo 5 – Considerazioni pratiche

- **Sostituzioni multiple:** Un singolo font mancante può essere sostituito da font diversi in parti diverse del documento. L’elenco degli avvisi conterrà ogni occorrenza, quindi potresti vedere voci duplicate di font mancanti.  
- **Prestazioni:** Il caricamento di documenti molto grandi può generare migliaia di avvisi. Se ti interessano solo i font, filtra subito come mostrato per mantenere il ciclo veloce.  
- **Font cross‑platform:** Su Linux, il font di sostituzione predefinito è spesso *Liberation Sans*. Su Windows, può essere *Arial*. Conoscere il fallback ti aiuta a decidere se è necessario includere font personalizzati nella tua applicazione.

## Passo 6 – Supporto visivo

Di seguito è mostrato uno screenshot dell’output della console (il testo alternativo include la parola chiave principale per la SEO).

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Testo alternativo:* *esempio di iterazione degli avvisi del documento che mostra i nomi dei font mancanti e i dettagli delle sostituzioni.*

## Conclusione

Hai appena imparato come **iterare gli avvisi del documento** in Aspose.Words per Java, **rilevare i font mancanti**, **caricare il documento Word** in modo sicuro, **recuperare le informazioni sui font mancanti** e **stampare i dettagli dei font mancanti** sulla console. Il frammento di codice completo funziona così com’è, e puoi adattarlo per registrare su file, mostrare una finestra di dialogo UI o persino incorporare automaticamente i font mancanti.

Successivamente, potresti voler esplorare come **caricare il documento Word** con font personalizzati (ad es., aggiungendo una cartella di font aziendali) o come incorporare i font mancanti direttamente nel file per preservare il layout su tutte le macchine. Entrambi gli argomenti si basano naturalmente su quanto trattato qui.

Buona programmazione, e che i tuoi PDF abbiano sempre l’aspetto esattamente desiderato!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}