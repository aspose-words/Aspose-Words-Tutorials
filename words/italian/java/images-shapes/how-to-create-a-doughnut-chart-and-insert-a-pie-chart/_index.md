---
category: general
date: 2026-10-26
description: Crea un grafico a ciambella e inserisci un grafico a torta in Java con
  codice passo‑passo. Scopri l’intero flusso di lavoro per visualizzazioni di grafici
  flessibili.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: it
lastmod: 2026-10-26
og_description: Crea un grafico a ciambella in Java con questa guida che mostra anche
  come inserire un grafico a torta per visualizzazioni flessibili.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Crea un grafico a ciambella e inserisci un grafico a torta – Guida Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Come creare un grafico a ciambella e inserire un grafico a torta
url: /it/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un grafico a ciambella e inserire un grafico a torta

Se hai bisogno di **creare doughnut chart** in Java, questo tutorial ti guida passo passo. Mostreremo anche come **inserire pie chart** usando la stessa API builder, così potrai passare facilmente tra i diversi stili visivi. Alla fine della guida avrai un programma completo e eseguibile che produce entrambi i tipi di grafico e dimostra le personalizzazioni più comuni.

Il tutorial copre:

* Inizializzare il chart builder fornito dalla libreria scelta.  
* Creare un doughnut chart e configurare la dimensione del buco.  
* Inserire un pie chart ed esplodere una sezione per enfatizzare.  
* Suggerimenti per gestire casi limite come serie mancanti o tipi di grafico non supportati.

Hai bisogno solo di un JDK recente (8 o successivo) e del JAR della libreria di grafici nel tuo classpath. Non sono richiesti servizi esterni.

---

## Prerequisiti

| Elemento | Motivo |
|------|--------|
| Java Development Kit (JDK) 8+ | Necessario per compilare ed eseguire l'esempio. |
| Chart library (e.g., **Aspose.Cells for Java** or **JFreeChart**) | Fornisce `ChartBuilder`, `ChartType` e i metodi di manipolazione delle serie usati nel codice. |
| An IDE or a text editor | Per scrivere ed eseguire il file sorgente Java. |

Assicurati che il JAR della libreria sia aggiunto al percorso di build del tuo progetto. Se usi Maven, aggiungi la dipendenza appropriata; altrimenti, posiziona il JAR nella cartella `libs` e riferiscilo durante la compilazione.

---

## Passo 1: Configurare il chart builder

Il primo passo è creare un'istanza di `ChartBuilder` (o equivalente) che genererà gli oggetti grafico. Questo oggetto funge da factory e contiene il foglio di lavoro o la tela dove verrà posizionato il grafico.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Perché è importante:**  
Il builder collega il grafico a un foglio di lavoro specifico, garantendo che tutti i successivi oggetti grafico condividano la stessa superficie di disegno. Saltare questo passo ti lascerebbe senza una destinazione per gli elementi visivi.

---

## Passo 2: **Creare doughnut chart**

Ora generiamo un doughnut chart con una dimensione definita. La dimensione del buco determina quanto del centro del grafico è vuoto, trasformando un normale pie in un doughnut.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Spiegazione:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` crea l'oggetto grafico e riserva spazio sul foglio di lavoro.  
* `setHoleSize(30)` converte il pie in un doughnut con un centro vuoto del 30 %.  
* `add("{10, 20, 30, 40}", true)` fornisce quattro punti dati; il flag `true` indica alla libreria di trattare i valori come una singola serie.

**Caso limite:** Se il tipo di grafico selezionato non supporta un buco (ad esempio, un grafico a barre), chiamare `getDoughnutChart()` genera un'eccezione. Verifica sempre il tipo di grafico prima di modificare la dimensione del buco.

---

## Passo 3: **Inserire pie chart**

Dopo che il doughnut è pronto, dimostriamo come **inserire pie chart** usando lo stesso builder. Questo passo evidenzia la somiglianza tra i due tipi di grafico e mostra come enfatizzare una sezione.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Spiegazione:**  

* `ChartType.PIE` indica al builder di creare un classico pie chart.  
* `setExplode(10)` sposta la prima sezione del 10 % del raggio, una tecnica comune per evidenziare un punto dati chiave.  

**Suggerimento:** Il metodo `setExplode` funziona solo sulla prima serie di un pie chart. Se hai più serie, devi puntare all'indice corretto.

---

## Passo 4: Salvare la cartella di lavoro

Infine, scrivi la cartella di lavoro su un file così potrai visualizzare i grafici in Excel o in qualsiasi visualizzatore compatibile.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Perché salvare ora:** Persistendo la cartella di lavoro si finalizzano tutte le operazioni di disegno. Tentare di visualizzare il file prima di salvarlo produce un documento vuoto o incompleto.

**Risultato:** Aprendo *DoughnutAndPieChart.xlsx* si vede un doughnut chart con buco del 30 % a sinistra e un pie chart con la prima sezione esplosa a destra.

---

## Passo 5: Variazioni comuni e risoluzione dei problemi

| Situazione | Adeguamento |
|-----------|------------|
| **Different chart dimensions** | Modifica gli argomenti di larghezza e altezza in `insertChart`. |
| **Multiple data series** | Chiama `add` più volte o passa una stringa di array 2‑D. |
| **Dynamic hole size** | Calcola la dimensione del buco in base all'intervallo dei dati, poi chiama `setHoleSize`. |
| **Explode multiple slices** | Itera su `chart.getSeries().get(i).setExplode(percent)` per ogni sezione che desideri spostare. |
| **Library not supporting doughnut** | Usa un pie chart e disegna manualmente un cerchio bianco sovrapposto, anche se è meno preciso. |

**Consiglio professionale:** Chiama sempre `builder.flush()` (se disponibile) dopo aver inserito i grafici quando lavori con cartelle di lavoro grandi. Questo rilascia i buffer interni e previene perdite di memoria.

---

![Codice Java che crea un doughnut chart e inserisce un pie chart](https://example.com/images/doughnut-pie-java.png "esempio di creazione di doughnut chart in Java")

*L'immagine illustra il layout finale della cartella di lavoro con entrambi i grafici affiancati.*

---

## Conclusione

Ora sai come **creare doughnut chart** e **inserire pie chart** in Java usando una fluida API builder. L'esempio completo copre l'inizializzazione, la configurazione delle dimensioni, la definizione del buco, l'esplosione delle sezioni e l'output del file. Da qui puoi esplorare ulteriori personalizzazioni come colori, legende e etichette dati per soddisfare i requisiti del tuo reporting.

**Passi successivi**

* Sperimenta con le funzionalità di **chart customization Java** come riempimenti a gradiente e etichette dati.  
* Integra la generazione dei grafici in un servizio web che restituisce la cartella di lavoro su richiesta.  
* Confronta l'approccio builder con altre librerie (ad esempio, JFreeChart) per scegliere la soluzione più adatta al tuo progetto.

Buon lavoro con i grafici!

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare doughnut chart in un documento Word con Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Salva documento Word dopo aver modificato doughnut chart in Java](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Inserire Pie Chart in Java – Esplodere, Ruotare e Evidenziare le Sezioni](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}