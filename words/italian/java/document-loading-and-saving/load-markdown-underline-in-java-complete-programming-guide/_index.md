---
category: general
date: 2026-08-04
description: Carica il sottolineato markdown in Java e conserva la formattazione markdown
  durante il caricamento del markdown nel documento. Segui questo tutorial passo‑passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: it
lastmod: 2026-08-04
og_description: Carica il markdown con sottolineatura in Java e preserva la formattazione
  markdown. Scopri come caricare il markdown in un documento con supporto completo
  alla sottolineatura.
og_image_alt: Diagram showing load markdown underline process
og_title: Carica il markdown sottolineato in Java – guida passo passo
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: Caricare la sottolineatura markdown in Java – guida completa di programmazione
url: /it/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Carica sottolineatura markdown in Java – guida completa di programmazione

Se hai bisogno di **load markdown underline** durante la conversione di un file Markdown in un oggetto `Document`, questa guida ti mostra esattamente come farlo. Imparerai anche come **load markdown into document** senza perdere alcuna formattazione di sottolineatura, garantendo che la formattazione originale del Markdown sia completamente preservata.

Il tutorial copre tutto ciò che devi sapere: le librerie richieste, ogni passaggio di configurazione e come verificare che la formattazione della sottolineatura sia sopravvissuta all'importazione. Alla fine avrai uno snippet di codice riutilizzabile da inserire in qualsiasi progetto Java.

## Prerequisiti

- Java 17 o versioni successive installato (l'esempio utilizza il moderno sistema di moduli)
- L'ultima versione di **GroupDocs.Viewer** (o una libreria compatibile che fornisce `LoadOptions` e `Document`)
- Un file Markdown (`sample.md`) che contiene testo sottolineato, ad esempio `<u>underlined</u>` o la sintassi in stile GitHub `__underlined__`
- Un IDE come IntelliJ IDEA o VS Code, anche se qualsiasi editor di testo funziona

Questi requisiti garantiscono che il codice venga eseguito senza configurazioni aggiuntive.

## Carica sottolineatura markdown – guida passo‑passo

Il processo consiste in tre azioni fondamentali: creare un'istanza di `LoadOptions`, abilitare il rilevamento della sottolineatura e infine caricare il file Markdown con tali opzioni. Ogni passaggio è spiegato di seguito.

### Passo 1: Crea `LoadOptions` per il documento

`LoadOptions` ti consente di personalizzare come la libreria analizza il file sorgente. Creare una nuova istanza ti offre una base pulita per le impostazioni successive.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

L'oggetto `LoadOptions` è il punto di ingresso per tutte le modifiche correlate all'importazione. Lo utilizzerai nel passo successivo per attivare il rilevamento della sottolineatura.

### Passo 2: Abilita il rilevamento della formattazione di sottolineatura durante il caricamento

Per impostazione predefinita il visualizzatore potrebbe ignorare i tag di sottolineatura perché sono meno comuni in Markdown. Abilitare questo flag indica al parser di mantenere intatti gli span di sottolineatura.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

Impostare `setImportUnderlineFormatting(true)` garantisce che qualsiasi tag HTML `<u>` o sintassi di sottolineatura in stile GitHub venga tradotto nel modello `Document` come stile di sottolineatura. Questa è l'azione chiave che fa funzionare **load markdown underline** come previsto.

### Passo 3: Carica il file Markdown usando le opzioni configurate

Ora puoi caricare il file. Passa l'oggetto `loadOptions` al costruttore `Document` affinché il parser rispetti il flag della sottolineatura.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

Al termine del costruttore, `markdownDoc` contiene una rappresentazione completa in memoria della sorgente Markdown, completa di segmenti sottolineati.

### Passo 4: Verifica che la formattazione di sottolineatura sia preservata

Un rapido controllo di coerenza ti aiuta a confermare che **preserve markdown formatting** abbia funzionato. Il frammento seguente stampa il testo di ogni paragrafo e segna i frammenti sottolineati con una tilde (`~`) per la visibilità.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**Output previsto** (supponendo che `sample.md` contenga `This is __underlined__ text`):

```
This is ~underlined~ text
```

Le tilde indicano che lo stile di sottolineatura è sopravvissuto all'importazione, confermando che l'operazione **load markdown into document** ha preservato la formattazione originale.

## Problemi comuni e come evitarli

| Sintomo | Causa | Risoluzione |
|---|---|---|
| La sottolineatura scompare dopo il caricamento | `setImportUnderlineFormatting` lasciato al valore predefinito `false` | Assicurati di chiamare `loadOptions.setImportUnderlineFormatting(true)` prima di creare il `Document`. |
| Solo una parte del testo è sottolineata | Sintassi Markdown mista (ad esempio HTML `<u>` mescolato con `__underline__`) | La libreria supporta entrambi; verifica che il file sorgente utilizzi un marcatore di sottolineatura coerente. |
| Il documento non riesce a caricarsi | Percorso file errato o dipendenze della libreria mancanti | Usa un percorso assoluto o posiziona `sample.md` relativo alla directory di lavoro; includi i JAR di viewer nel classpath. |

**Consiglio professionale:** Se devi anche mantenere gli stili grassetto o corsivo, abilitali con `setImportBoldFormatting(true)` e `setImportItalicFormatting(true)` rispettivamente. Combinando questi flag ottieni un'importazione completamente fedele della maggior parte degli stili Markdown più comuni.

## Esempio completo eseguibile

Di seguito trovi un programma Java autonomo che mette tutto insieme. Copia il codice in un file chiamato `LoadMarkdownUnderlineDemo.java`, regola il percorso del file e eseguilo con `java LoadMarkdownUnderlineDemo`.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

L'esecuzione del programma stampa il contenuto del documento con i marcatori di sottolineatura, dimostrando che la funzionalità **load markdown underline** funziona e che puoi **preserve markdown formatting** lungo l'intera pipeline di importazione.

## Conclusione

Ora sai come **load markdown underline** in Java, come **load markdown into document** mantenendo lo stile originale, e come verificare che la formattazione della sottolineatura sia intatta. Questo approccio funziona con le ultime versioni di GroupDocs.Viewer e può essere esteso per supportare funzionalità Markdown aggiuntive come grassetto, corsivo e tabelle.

Successivamente, esplora argomenti correlati come **preserve markdown formatting for tables**, **render Markdown to PDF**, o **custom styling of imported Markdown elements**. Regola i flag di `LoadOptions` per corrispondere ai requisiti di formattazione esatti della tua applicazione, e avrai un controllo granulare su ogni passaggio di importazione. Buona programmazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Padroneggia le opzioni di caricamento Markdown con Aspose.Words per Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Padroneggia le opzioni di caricamento Markdown Aspose Words Java](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}