---
title: Vložte Comment do konkrétního odstavce ve Word dokumentu pomocí Aspose.Words pro .NET
weight: 210
limit:
description: Podrobný návod krok za krokem, jak přidat komentář autora do vybraného odstavce ve Word dokumentu a uložit jej jako DOCX pomocí Aspose.Words pro .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Podrobný návod krok za krokem, jak přidat komentář autora do vybraného
    odstavce ve Word dokumentu a uložit jej jako DOCX pomocí Aspose.Words pro .NET.
  headline: Vložte Comment do konkrétního odstavce ve Word dokumentu pomocí Aspose.Words
    pro .NET
  type: TechArticle
- description: Podrobný návod krok za krokem, jak přidat komentář autora do vybraného
    odstavce ve Word dokumentu a uložit jej jako DOCX pomocí Aspose.Words pro .NET.
  name: Vložte Comment do konkrétního odstavce ve Word dokumentu pomocí Aspose.Words
    pro .NET
  steps:
  - name: Vytvořte novou instanci třídy Document a DocumentBuilder, abyste mohli začít
      sestavovat soubor Word.
    text: Vytvořte novou instanci třídy Document a DocumentBuilder, abyste mohli začít
      sestavovat soubor Word.
  - name: Použijte DocumentBuilder.Writeln k přidání tří samostatných odstavců textu
      do dokumentu.
    text: Použijte DocumentBuilder.Writeln k přidání tří samostatných odstavců textu
      do dokumentu.
  - name: Bezpečně načtěte druhý odstavec, přičemž v případě, že dokument obsahuje
      méně než dva odstavce, použijte první.
    text: Bezpečně načtěte druhý odstavec, přičemž v případě, že dokument obsahuje
      méně než dva odstavce, použijte první.
  - name: Vytvořte Comment s údaji o autorovi, nastavte jeho text a připojte jej k
      vybranému odstavci.
    text: Vytvořte Comment s údaji o autorovi, nastavte jeho text a připojte jej k
      vybranému odstavci.
  - name: Uložte upravený dokument jako soubor DOCX s názvem 'sample.docx' do aktuální
      složky.
    text: Uložte upravený dokument jako soubor DOCX s názvem 'sample.docx' do aktuální
      složky.
  type: HowTo
- questions:
  - answer: '`if` blok přejde na první odstavec (`paraList[0]`), když je `paraList.Count`
      menší než 2, takže komentář bude připojen k tomuto jedinému odstavci místo chybějícího
      druhého.'
    question: Co kód udělá, pokud dokument obsahuje pouze jeden odstavec?
  - answer: Jsou předány konstruktoru `Comment` jako druhý a třetí argument – `new
      Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – kde \"Jordan\" je jméno
      autora a \"JH\" jsou iniciály.
    question: Jak jsou v tomto příkladu nastaveny jméno autora komentáře a iniciály?
  - answer: V tomto úryvku je komentář spojen s celým `Paragraph` pomocí `AppendChild`,
      ale pro komentování rozsahu textu byste museli vytvořit `CommentRangeStart`
      a `CommentRangeEnd` kolem požadovaných uzlů `Run` a poté mezi ně vložit uzel
      `Comment`.
    question: Mohu připojit komentář k určitému úseku textu místo celého odstavce?
  - answer: '`AppendChild` přidá uzel `Comment` do kolekce podřízených uzlů odstavce
      a Aspose.Words automaticky vygeneruje požadované značky začátku/konce komentáře
      při uložení dokumentu.'
    question: Musím ručně vkládat značky komentáře, nebo to zařídí `AppendChild`?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Vložte komentář do odstavce ve Wordu
og_description: Přidejte komentář autora do konkrétního odstavce a exportujte soubor jako DOCX pomocí Aspose.Words.
og_image_alt: Průvodce ukazující, jak přidat komentář k odstavci ve Word dokumentu pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložte Comment do konkrétního odstavce ve Word dokumentu pomocí Aspose.Words pro .NET
S Aspose.Words pro .NET můžete programově přidávat komentáře do souborů Word. Tento tutoriál vás provede vytvořením nového dokumentu, vložením tří odstavců, nalezením druhého odstavce a připojením komentáře, který obsahuje informace o autorovi a datu. Nakonec je dokument uložen jako soubor DOCX s zachováním komentáře.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Co kód udělá, pokud dokument obsahuje pouze jeden odstavec?**  
A: `if` blok přejde na první odstavec (`paraList[0]`), když je `paraList.Count` menší než 2, takže komentář bude připojen k tomuto jedinému odstavci místo chybějícího druhého.

**Q: Jak jsou v tomto příkladu nastaveny jméno autora komentáře a iniciály?**  
A: Jsou předány konstruktoru `Comment` jako druhý a třetí argument – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – kde \"Jordan\" je jméno autora a \"JH\" jsou iniciály.

**Q: Mohu připojit komentář k určitému úseku textu místo celého odstavce?**  
A: V tomto úryvku je komentář spojen s celým `Paragraph` pomocí `AppendChild`, ale pro komentování rozsahu textu byste museli vytvořit `CommentRangeStart` a `CommentRangeEnd` kolem požadovaných uzlů `Run` a poté mezi ně vložit uzel `Comment`.

**Q: Musím ručně vkládat značky komentáře, nebo to zařídí `AppendChild`?**  
A: `AppendChild` přidá uzel `Comment` do kolekce podřízených uzlů odstavce a Aspose.Words automaticky vygeneruje požadované značky začátku/konce komentáře při uložení dokumentu.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}