---
category: general
date: 2026-03-19
description: Scopri come catturare gli avvisi in Aspose.Words per Java e rilevare
  i caratteri mancanti. Questa guida passo passo mostra anche come gestire i caratteri
  mancanti in modo elegante.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: it
og_description: Come catturare gli avvisi in Aspose.Words per Java, rilevare i font
  mancanti e gestire i font mancanti con un esempio di codice completo.
og_title: Come catturare gli avvisi – Rilevare i font mancanti in Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Come catturare gli avvisi – Rilevare i font mancanti in Aspose.Words
url: /it/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come catturare gli avvisi – Rilevare i font mancanti in Aspose.Words

Ti sei mai chiesto **come catturare gli avvisi** quando un documento Word viene caricato e alcuni font non sono disponibili sulla macchina? Non sei solo. In molti progetti reali, i font mancanti causano spostamenti di layout silenziosi, e l'unico modo per sapere cosa è successo è ascoltare lo stream di avvisi che Aspose.Words emette.  

In questo tutorial percorreremo un esempio completo, pronto‑all'uso, che **rileva i font mancanti**, ti mostra **come rilevare i font mancanti** programmaticamente, e fornisce anche un suggerimento rapido su **come gestire i font mancanti** affinché il tuo output rimanga prevedibile.

> **Nota rapida:** Il codice funziona con Aspose.Words 23.9 (o versioni successive) e richiede Java 8+.

---

## Cosa ti servirà

- **Aspose.Words for Java** (dipendenza Maven/Gradle o JAR nel classpath)  
- Un file Word (`input.docx`) che fa riferimento a un font non installato sul tuo sistema (ad es., “Comic Sans MS”)  
- Un IDE Java o una semplice configurazione da riga di comando `javac`/`java`  

Non sono richieste altre librerie—tutto il resto è incluso nel pacchetto Aspose.Words.

## Passo 1 – Configura LoadOptions per catturare gli avvisi  

Per iniziare ad ascoltare gli avvisi devi creare un'istanza di `LoadOptions`. Questo oggetto indica al loader di tenere traccia di eventuali problemi riscontrati, come i font mancanti.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Perché è importante:** Senza `LoadOptions` il loader sostituisce silenziosamente i font mancanti con il font di sistema predefinito, e non sapresti mai che è avvenuta una sostituzione. Abilitare gli avvisi ti offre piena visibilità.

## Passo 2 – Carica il documento usando LoadOptions  

Ora carichiamo effettivamente il documento. Il `LoadOptions` appena creato viene passato al costruttore, così tutti gli avvisi generati durante il parsing vengono catturati.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Suggerimento professionale:** Se stai elaborando molti file in batch, riutilizza la stessa istanza di `LoadOptions` per evitare la creazione inutile di oggetti.

## Passo 3 – Itera sugli avvisi catturati  

Aspose.Words memorizza ogni avviso come oggetto `WarningInfo`. Ci interessano solo gli avvisi relativi ai font, quindi filtriamo per `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Spiegazione:**  
- `document.getWarnings()` restituisce un elenco di tutti gli avvisi verificatisi durante il caricamento.  
- `FontSubstitutionWarningInfo` contiene due dati fondamentali: il **font richiesto** (quello richiesto dal DOCX) e il **font effettivo** a cui Aspose.Words è ricaduto.  
- Stampando entrambi, vedi immediatamente quali font mancano e quale sostituzione è avvenuta.

## Passo 4 – (Facoltativo) Gestire i font mancanti programmaticamente  

Catturare gli avvisi è solo metà della storia. Una volta che sai che un font è mancante, potresti voler **gestire i font mancanti** fornendo una sostituzione personalizzata o registrando il problema per una revisione successiva.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Perché farlo?**  
- Garantisce un rendering coerente su tutte le macchine.  
- Previene cambiamenti di layout inaspettati nei PDF o nelle immagini generate successivamente.  

Puoi anche memorizzare i dettagli dell'avviso in un database, inviare un'email al team di contenuti, o persino interrompere il processo se un font critico è mancante.

## Esempio completo funzionante  

Di seguito trovi il programma completo e eseguibile. Sostituisci semplicemente `YOUR_DIRECTORY/input.docx` con il percorso del tuo file di test, aggiungi il JAR di Aspose.Words al tuo classpath e avvia.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Output previsto** (quando “Comic Sans MS” è mancante):

```
Requested: Comic Sans MS → Substituted: Arial
```

Dopo l'esecuzione del codice di fallback opzionale, il `output.docx` salvato verrà renderizzato usando **Arial** ovunque “Comic Sans MS” fosse originariamente referenziato.

## Domande comuni e casi limite  

| Domanda | Risposta |
|----------|--------|
| *Cosa succede se il documento ha più font mancanti?* | Il ciclo emetterà un avviso per ciascuno. Puoi raccoglierli in una `Map<String, String>` per l'elaborazione batch. |
| *Funziona per i PDF generati dal documento?* | Assolutamente. La sostituzione dei font avviene durante la fase di caricamento, quindi qualsiasi esportazione successiva (PDF, HTML, immagine) utilizza i font risolti. |
| *Posso sopprimere gli avvisi invece di catturarli?* | Sì—imposta `loadOptions.setWarningCallback(null);` ma perderai la visibilità sui font mancanti. |
| *L'elenco degli avvisi viene svuotato dopo il salvataggio?* | La raccolta degli avvisi appartiene all'istanza `Document`. Dopo aver chiamato `document.save()`, l'elenco rimane invariato a meno che non venga creato un nuovo `Document`. |
| *E i font personalizzati incorporati nel DOCX?* | I font incorporati sono considerati disponibili; Aspose.Words li utilizzerà anche se non sono installati sul sistema host. |

## Suggerimenti professionali per l'uso in produzione  

- **Cache FontSettings:** Se elabori centinaia di file, crea un unico `FontSettings` con i fallback preferiti e riutilizzalo per evitare overhead.  
- **Log Structured Data:** Invece di usare `System.out` semplice, scrivi gli avvisi in un log JSON—questo rende le analisi successive (ad es., “font più mancanti”) triviali.  
- **Validate Early:** Esegui un rapido “dry‑load” con `LoadOptions` prima di un'elaborazione pesante; interrompi subito se mancano font critici.  
- **Thread Safety:** Gli oggetti `Document` non sono thread‑safe. Mantieni l'elaborazione di ogni file in un proprio thread o usa un `LoadOptions` thread‑local.  

## Conclusione  

Ora sai **come catturare gli avvisi** in Aspose.Words per Java, **rilevare i font mancanti**, e **gestire i font mancanti** con una strategia di fallback pulita. Sfruttando `LoadOptions` e iterando su `document.getWarnings()`, ottieni una piena visibilità sugli eventi di sostituzione dei font, garantendo che i documenti generati appaiano esattamente come previsto in tutti gli ambienti.

Pronto per il passo successivo? Prova a estendere questo modello per **rilevare immagini mancanti**, **tracciare funzionalità non supportate**, o persino **incorporare automaticamente i font mancanti** nel file di output. Lo stesso approccio di cattura degli avvisi funziona per molti altri scenari di elaborazione dei documenti, rendendo il tuo codice robusto e a prova di futuro.

Buon coding, e che i tuoi documenti vengano sempre renderizzati splendidamente!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}