---
category: general
date: 2026-04-21
description: Salva rapidamente il LaTeX delle equazioni di Office Math usando Aspose.Words
  – scopri anche come salvare il testo semplice di Word ed esportare le equazioni
  di Word in LaTeX in un'unica operazione.
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: it
og_description: salva immediatamente il LaTeX di Office Math; impara a esportare le
  equazioni LaTeX di Word e a convertire il LaTeX matematico di Word con Aspose.Words
  in C#.
og_title: salva office math latex – Esporta le equazioni di Word in LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: salva Office Math LaTeX – Esporta le equazioni di Word in LaTeX in C#
url: /it/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save office math latex – Esporta le equazioni Word in LaTeX con Aspose.Words

Hai mai avuto bisogno di **save office math latex** da un file `.docx` ma non sapevi da dove cominciare? Non sei l'unico, e la buona notizia è che la soluzione è piuttosto semplice. In questa guida percorreremo i passaggi esatti per esportare le equazioni Word in latex (e anche MathML) usando Aspose.Words per .NET, mostrando anche come **save word plain text** insieme alla matematica.

Tratteremo tutto ciò che potresti chiederti: perché scegliere LaTeX rispetto ad altri formati, come configurare il `TxtSaveOptions`, e cosa fare se devi **convert word math latex** in un'altra rappresentazione. Alla fine avrai uno snippet eseguibile che prende un documento Word con oggetti Office Math e genera un file `.txt` pulito contenente equazioni LaTeX (o MathML). Nessun tool esterno, nessun copia‑incolla manuale — solo codice C# pulito che puoi inserire in qualsiasi progetto.

## Prerequisiti

- **Aspose.Words per .NET** (v23.10 o successivo). Il pacchetto NuGet è `Aspose.Words`.
- Un ambiente di sviluppo .NET (Visual Studio, Rider o VS Code con l'estensione C#).
- Un file Word (`.docx`) che contiene almeno un'equazione creata con l'editor Office Math.
- Familiarità di base con la sintassi C# — niente di complicato, solo le consuete istruzioni `using`.

Se hai già spuntato queste caselle, ottimo — immergiamoci.

## Passo 1 – Configura le opzioni **save office math latex**

La prima cosa da fare è dire ad Aspose.Words come vuoi che il contenuto matematico venga renderizzato. La classe `TxtSaveOptions` ha una proprietà `OfficeMathExportMode` che accetta tre valori: `LaTeX`, `MathML` o `Text`. Per il nostro obiettivo principale sceglieremo `LaTeX`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**Perché è importante:** Quando imposti `OfficeMathExportMode` su `LaTeX`, ogni equazione viene trasformata nella sua sorgente LaTeX grezza. Quella sorgente può poi essere compilata con qualsiasi motore LaTeX, fornendoti una tipografia pixel‑perfect senza dover riscrivere le formule.

> **Consiglio:** Se mai avrai bisogno di **convert word equations mathml**, basta scambiare il valore enum con `OfficeMathExportMode.MathML`. Il resto del codice rimane invariato.

## Passo 2 – Carica il documento Word (lo scenario **save word plain text**)

Successivamente, carichiamo il file `.docx` di origine. Questo passaggio è identico sia che tu sia interessato solo all'estrazione del testo semplice sia che voglia anche le equazioni in LaTeX.

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**Cosa sta succedendo?** Il costruttore `Document` legge il file in memoria. Il rapido controllo con `GetChildNodes` ti aiuta a intercettare un caso limite comune — tentare di esportare LaTeX da un file che non contiene equazioni. È una piccola salvaguardia che ti evita un output vuoto e sconcertante in seguito.

## Passo 3 – **save office math latex** in un file di testo semplice

Ora scriviamo finalmente il file. Il metodo `Save` rispetta le `TxtSaveOptions` che abbiamo configurato in precedenza, quindi il `.txt` risultante conterrà sia il testo normale sia gli snippet LaTeX per ogni equazione.

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

Quando apri `Equations.txt` vedrai qualcosa del genere:

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

I blocchi LaTeX sono avvolti automaticamente in `\begin{equation}` … `\end{equation}`, il che li rende pronti per l'inclusione in qualsiasi documento LaTeX.

## Passo 4 – Alternativa: **convert word equations mathml** invece di LaTeX

Se la tua catena di strumenti preferisce MathML (ad esempio, una pagina web che rende le equazioni con MathJax), cambia semplicemente la modalità di esportazione:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

L'output conterrà ora tag MathML in stile XML, come:

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

Questo è il modo rapido per **convert word equations mathml** senza scrivere un parser personalizzato.

## Passo 5 – Bonus: **save word plain text** mantenendo le equazioni separate

A volte vuoi una versione testuale pulita del documento *senza* alcun LaTeX o MathML incorporato. Puoi ottenerlo cambiando la modalità di esportazione in `Text` ed eseguendo un secondo passaggio di salvataggio:

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

Ora hai tre file affiancati:

| File                         | Contenuto                               |
|------------------------------|----------------------------------------|
| `Equations.txt`              | Testo semplice **+** equazioni LaTeX       |
| `EquationsMathML.txt`        | Testo semplice **+** equazioni MathML       |
| `PlainDocument.txt`          | Testo puro, equazioni rimosse               |

Questo schema è utile quando devi inserire il testo semplice in un indice di ricerca mantenendo comunque la matematica originale per la pubblicazione accademica.

## Esempio completo funzionante (pronto per copia‑incolla)

Di seguito trovi il programma completo che puoi compilare ed eseguire così com'è. Dimostra **save office math latex**, **export word equations latex**, **convert word math latex** e **save word plain text** — tutto in un unico script ordinato.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**Risultato atteso:** Dopo l'esecuzione, troverai tre file di testo in `C:\MyDocs`. Apri `Equations.txt` e vedrai i blocchi LaTeX; `EquationsMathML.txt` conterrà MathML; `PlainDocument.txt` sarà privo di qualsiasi markup di equazione.

## Domande comuni e casi limite

- **E se ho bisogno di LaTeX solo per un sottoinsieme di equazioni?**  
  Usa l'API dei nodi `OfficeMath` per iterare su ciascuna equazione, esportala manualmente con `MathConverter` e sostituisci il testo segnaposto dove desideri. Questo approccio ti dà un controllo fine ma aggiunge qualche riga di codice in più.

- **Funziona con .NET Core / .NET 5+?**  
  Assolutamente. Aspose.Words è cross‑platform, quindi lo stesso codice gira su Windows, Linux e macOS purché la versione del runtime corrisponda ai requisiti della libreria.

- **Posso cambiare il wrapper LaTeX (`\begin{equation}`) con qualcos'altro?**  
  Sì. Imposta `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` e poi modifica `txtOptions.MathExportSettings` (disponibile nelle versioni più recenti) per personalizzare i delimitatori.

- **Preoccupazioni di performance per documenti enormi?**  
  La libreria trasmette in streaming l'output, quindi l'uso di memoria rimane contenuto. Tuttavia

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}