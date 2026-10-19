---
title: Inserisci una Data Dinamica nell'Intestazione di un Documento Word usando Aspose.Words per .NET
weight: 110
limit:
description: Scopri come aggiungere un campo DATE dinamico all'intestazione primaria di un documento Word con Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Scopri come aggiungere un campo DATE dinamico all'intestazione primaria
    di un documento Word con Aspose.Words per .NET.
  headline: Inserisci una Data Dinamica nell'Intestazione di un Documento Word usando
    Aspose.Words per .NET
  type: TechArticle
- description: Scopri come aggiungere un campo DATE dinamico all'intestazione primaria
    di un documento Word con Aspose.Words per .NET.
  name: Inserisci una Data Dinamica nell'Intestazione di un Documento Word usando
    Aspose.Words per .NET
  steps:
  - name: Crea un nuovo Document e un DocumentBuilder per modificarlo.
    text: Crea un nuovo Document e un DocumentBuilder per modificarlo.
  - name: Sposta il cursore del builder sull'intestazione primaria in modo che le
      inserzioni successive influenzino l'intestazione.
    text: Sposta il cursore del builder sull'intestazione primaria in modo che le
      inserzioni successive influenzino l'intestazione.
  - name: Scrivi l'etichetta statica e inserisci un campo DATE formattato come “MMMM
      d, yyyy” nell'intestazione, creando una data dinamica.
    text: Scrivi l'etichetta statica e inserisci un campo DATE formattato come “MMMM
      d, yyyy” nell'intestazione, creando una data dinamica.
  - name: Torna al corpo principale e aggiungi un paragrafo di esempio, dimostrando
      il contenuto normale del documento accanto all'intestazione.
    text: Torna al corpo principale e aggiungi un paragrafo di esempio, dimostrando
      il contenuto normale del documento accanto all'intestazione.
  - name: Salva il documento in un file .docx.
    text: Salva il documento in un file .docx.
  type: HowTo
- questions:
  - answer: La chiamata `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` posiziona
      il builder sull'intestazione primaria esistente, e `Write`/`InsertField` aggiungono
      semplicemente testo a ciò che è già presente; non eliminano il contenuto esistente.
    question: Cosa succede se il documento ha già un'intestazione primaria – il mio
      codice la sovrascriverà?
  - answer: Sì – modifica il formato dello switch nel codice del campo passato a `InsertField`,
      ad es. `builder.InsertField(\"DATE \\@ \\"yyyy-MM-dd\\\")` produrrà una data
      come 2026-09-22.
    question: Posso cambiare il formato della data usato dal campo DATE, e come?
  - answer: Sostituisci `HeaderFooterType.HeaderPrimary` con `HeaderFooterType.HeaderFirst`
      quando chiami `MoveToHeaderFooter`; il resto del codice funziona allo stesso
      modo.
    question: Se ho bisogno del campo data nell'intestazione della prima pagina invece
      dell'intestazione primaria, cosa devo fare?
  - answer: Il campo è inserito solo con lo switch `\\@`, che indica a Word di visualizzare
      la data corrente ogni volta che il campo viene aggiornato (ad es., all'apertura
      del file o quando premi Ctrl+Alt+F9).
    question: Il campo DATE si aggiorna automaticamente quando il documento viene
      aperto in seguito?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: Aggiungi una Data Dinamica a un'Intestazione Word
og_description: Guida passo‑passo per incorporare un campo data in tempo reale nella tua intestazione Word con Aspose.Words.
og_image_alt: Screenshot che mostra come inserire un campo DATE dinamico nell'intestazione di un documento Word usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci una Data Dinamica nell'Intestazione di un Documento Word usando Aspose.Words per .NET
Questo tutorial dimostra come utilizzare le classi Document e DocumentBuilder in Aspose.Words per .NET per inserire un campo DATE dinamico nell'intestazione primaria di un documento Word. Il campo aggiunto si aggiorna automaticamente alla data corrente ogni volta che il documento viene aperto, garantendo che l'intestazione rifletta sempre la data più recente. Segui il codice passo‑passo per aggiungere il campo e salvare il file aggiornato.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Cosa succede se il documento ha già un'intestazione primaria – il mio codice la sovrascriverà?**  
A: La chiamata `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` posiziona il builder sull'intestazione primaria esistente, e `Write`/`InsertField` aggiungono semplicemente testo a ciò che è già presente; non eliminano il contenuto esistente.

**Q: Posso cambiare il formato della data usato dal campo DATE, e come?**  
A: Sì – modifica il formato dello switch nel codice del campo passato a `InsertField`, ad es. `builder.InsertField(\"DATE \\@ \\"yyyy-MM-dd\\\")` produrrà una data come 2026-09-22.

**Q: Se ho bisogno del campo data nell'intestazione della prima pagina invece dell'intestazione primaria, cosa devo fare?**  
A: Sostituisci `HeaderFooterType.HeaderPrimary` con `HeaderFooterType.HeaderFirst` quando chiami `MoveToHeaderFooter`; il resto del codice funziona allo stesso modo.

**Q: Il campo DATE si aggiorna automaticamente quando il documento viene aperto in seguito?**  
A: Il campo è inserito solo con lo switch `\\@`, che indica a Word di visualizzare la data corrente ogni volta che il campo viene aggiornato (ad es., all'apertura del file o quando premi Ctrl+Alt+F9).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}