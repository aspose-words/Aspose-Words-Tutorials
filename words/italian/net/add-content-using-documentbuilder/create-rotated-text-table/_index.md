---
title: Creare una tabella con testo ruotato in un documento Word utilizzando Aspose.Words per .NET
weight: 110
limit:
description: Impara a creare una tabella Word con larghezze di colonna fisse, testo ruotato, altezze di riga precise e celle popolate usando Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Impara a creare una tabella Word con larghezze di colonna fisse, testo
    ruotato, altezze di riga precise e celle popolate usando Aspose.Words per .NET.
  headline: Creare una tabella con testo ruotato in un documento Word utilizzando
    Aspose.Words per .NET
  type: TechArticle
- description: Impara a creare una tabella Word con larghezze di colonna fisse, testo
    ruotato, altezze di riga precise e celle popolate usando Aspose.Words per .NET.
  name: Creare una tabella con testo ruotato in un documento Word utilizzando Aspose.Words
    per .NET
  steps:
  - name: Istanziare un nuovo Document e un DocumentBuilder che verranno utilizzati
      per costruire la tabella.
    text: Istanziare un nuovo Document e un DocumentBuilder che verranno utilizzati
      per costruire la tabella.
  - name: Avviare una nuova tabella, inserire la prima cella e fissare le larghezze
      delle colonne in modo che non si adattino automaticamente.
    text: Avviare una nuova tabella, inserire la prima cella e fissare le larghezze
      delle colonne in modo che non si adattino automaticamente.
  - name: Allineare verticalmente al centro il contenuto nella cella corrente e scrivere
      il testo della prima cella della prima riga.
    text: Allineare verticalmente al centro il contenuto nella cella corrente e scrivere
      il testo della prima cella della prima riga.
  - name: Inserire la seconda cella della prima riga e scrivere il suo testo.
    text: Inserire la seconda cella della prima riga e scrivere il suo testo.
  - name: Chiudere la prima riga, finalizzandone il layout.
    text: Chiudere la prima riga, finalizzandone il layout.
  - name: Avviare la prima cella della seconda riga, impostare l'altezza della riga
      a esattamente 100 punti, ruotare il testo verso l'alto e scrivere il testo della
      cella.
    text: Avviare la prima cella della seconda riga, impostare l'altezza della riga
      a esattamente 100 punti, ruotare il testo verso l'alto e scrivere il testo della
      cella.
  - name: Inserire la seconda cella della seconda riga, ruotare il suo testo verso
      il basso e scrivere il testo della cella.
    text: Inserire la seconda cella della seconda riga, ruotare il suo testo verso
      il basso e scrivere il testo della cella.
  - name: Chiudere la seconda riga, completando la seconda linea della tabella.
    text: Chiudere la seconda riga, completando la seconda linea della tabella.
  - name: Terminare la costruzione della tabella, sigillando la struttura della tabella.
    text: Terminare la costruzione della tabella, sigillando la struttura della tabella.
  - name: Salvare il documento completato in un file .docx.
    text: Salvare il documento completato in un file .docx.
  type: HowTo
- questions:
  - answer: Dopo aver fissato le larghezze delle colonne, assegna una larghezza a
      ciascuna cella usando `builder.CellFormat.Width = <valueInPoints>;` prima di
      inserire la cella successiva; la tabella manterrà quelle larghezze esatte.
    question: Come posso impostare larghezze di colonna specifiche dopo aver chiamato
      `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?
  - answer: '`builder.CellFormat.VerticalAlignment` è un''impostazione a livello di
      cella, quindi è necessario impostarla nuovamente per le celle della seconda
      riga (ad esempio, `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`)
      prima di scrivere il loro contenuto.'
    question: Perché l'allineamento verticale influisce solo sulla prima riga e non
      sulla seconda?
  - answer: Sì—imposta `builder.RowFormat.Height` e `builder.RowFormat.HeightRule
      = HeightRule.Exactly` prima di ogni chiamata a `builder.EndRow();`; la riga
      successiva può avere un valore di altezza diverso.
    question: Posso assegnare a ogni riga un'altezza esatta diversa e, in tal caso,
      come?
  - answer: Reimposta l'orientamento assegnando `builder.CellFormat.Orientation =
      TextOrientation.Horizontal;` prima di scrivere nella cella successiva.
    question: Come posso ripristinare l'orientamento del testo al valore predefinito
      dopo aver usato `TextOrientation.Upward` o `Downward`?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Creare una tabella con testo ruotato in Word con Aspose.Words
og_description: Codice passo‑passo per costruire una tabella a larghezza fissa con testo ruotato verticalmente e altezze di riga esatte.
og_image_alt: Screenshot che mostra un documento Word con una tabella che ha larghezze di colonna fisse, testo ruotato nelle celle e altezze di riga definite, creata usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Creare una tabella con testo ruotato in un documento Word utilizzando Aspose.Words per .NET
Questo tutorial mostra come generare un documento Word e aggiungere una tabella le cui colonne hanno larghezze fisse, le righe hanno altezze esatte e il testo delle celle è ruotato verticalmente. Imparerai a impostare l'allineamento verticale, applicare l'orientamento del testo, riempire ogni cella con contenuto e infine salvare il documento—tutto con Aspose.Words per .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Come posso impostare larghezze di colonna specifiche dopo aver chiamato `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?**  
A: Dopo aver fissato le larghezze delle colonne, assegna una larghezza a ciascuna cella usando `builder.CellFormat.Width = <valueInPoints>;` prima di inserire la cella successiva; la tabella manterrà quelle larghezze esatte.

**Q: Perché l'allineamento verticale influisce solo sulla prima riga e non sulla seconda?**  
A: `builder.CellFormat.VerticalAlignment` è un'impostazione a livello di cella, quindi è necessario impostarla nuovamente per le celle della seconda riga (ad esempio, `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) prima di scrivere il loro contenuto.

**Q: Posso assegnare a ogni riga un'altezza esatta diversa e, in tal caso, come?**  
A: Sì—imposta `builder.RowFormat.Height` e `builder.RowFormat.HeightRule = HeightRule.Exactly` prima di ogni chiamata a `builder.EndRow();`; la riga successiva può avere un valore di altezza diverso.

**Q: Come posso ripristinare l'orientamento del testo al valore predefinito dopo aver usato `TextOrientation.Upward` o `Downward`?**  
A: Reimposta l'orientamento assegnando `builder.CellFormat.Orientation = TextOrientation.Horizontal;` prima di scrivere nella cella successiva.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}