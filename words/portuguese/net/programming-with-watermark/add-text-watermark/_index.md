---
title: Adicionar Marca d'Água de Texto Diagonal Vermelha a Documentos Word Usando Aspose.Words para .NET
weight: 110
limit:
description: Aplicar automaticamente uma marca d'água de texto diagonal vermelha a cada arquivo Word gerado em um lote usando Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aplicar automaticamente uma marca d'água de texto diagonal vermelha
    a cada arquivo Word gerado em um lote usando Aspose.Words para .NET.
  headline: Adicionar Marca d'Água de Texto Diagonal Vermelha a Documentos Word Usando
    Aspose.Words para .NET
  type: TechArticle
- description: Aplicar automaticamente uma marca d'água de texto diagonal vermelha
    a cada arquivo Word gerado em um lote usando Aspose.Words para .NET.
  name: Adicionar Marca d'Água de Texto Diagonal Vermelha a Documentos Word Usando
    Aspose.Words para .NET
  steps:
  - name: Crie a pasta "GeneratedReports" onde os arquivos de saída serão salvos.
    text: Crie a pasta "GeneratedReports" onde os arquivos de saída serão salvos.
  - name: Inicie um loop que gerará três documentos separados.
    text: Inicie um loop que gerará três documentos separados.
  - name: Crie um novo objeto de documento Word vazio.
    text: Crie um novo objeto de documento Word vazio.
  - name: Use DocumentBuilder para escrever uma linha de título e uma descrição no
      documento.
    text: Use DocumentBuilder para escrever uma linha de título e uma descrição no
      documento.
  - name: Defina a aparência da marca d'água, incluindo fonte, tamanho, cor e layout
      diagonal.
    text: Defina a aparência da marca d'água, incluindo fonte, tamanho, cor e layout
      diagonal.
  - name: Aplique a marca d'água diagonal vermelha configurada com o texto "PROTECTED"
      ao documento.
    text: Aplique a marca d'água diagonal vermelha configurada com o texto "PROTECTED"
      ao documento.
  - name: Salve o documento com marca d'água na pasta "GeneratedReports" com um nome
      de arquivo exclusivo.
    text: Salve o documento com marca d'água na pasta "GeneratedReports" com um nome
      de arquivo exclusivo.
  - name: Feche o loop após processar o documento atual.
    text: Feche o loop após processar o documento atual.
  type: HowTo
- questions:
  - answer: IsSemitrasparent determina se a marca d'água é renderizada com opacidade
      parcial; defini‑la como **true** torna o texto semitransparente, de modo que
      o conteúdo subjacente permaneça mais legível.
    question: O que a opção **IsSemitrasparent** controla e que efeito tem ao defini-la
      como **true**?
  - answer: Sim—defina a propriedade **Layout** como **WatermarkLayout.Horizontal**
      em **TextWatermarkOptions** antes de chamar **document.Watermark.SetText**.
    question: Posso mudar a orientação da marca d'água para horizontal em vez de diagonal?
  - answer: O trecho cria uma nova instância de **Document**, mas você pode abrir
      qualquer arquivo existente (por exemplo, `new Document("Existing.docx")`) e
      então chamar **document.Watermark.SetText** para aplicar a mesma marca d'água.
    question: Este código adicionará uma marca d'água a um arquivo Word existente
      ou apenas a documentos recém‑criados?
  - answer: Atribua uma cor personalizada com **Color.FromArgb(red, green, blue)**
      à propriedade **Color** de **TextWatermarkOptions**, por exemplo, `Color = Color.FromArgb(128,
      0, 128)` para roxo.
    question: Como posso usar uma cor RGB personalizada para a marca d'água em vez
      do **Color.Red** predefinido?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Adicionar uma Marca d'Água de Texto Diagonal Vermelha a Documentos Word
og_description: Veja como aplicar automaticamente uma marca d'água diagonal vermelha a cada documento Word em um lote com Aspose.Words.
og_image_alt: Guia que mostra como adicionar uma marca d'água de texto diagonal vermelha a documentos Word usando Aspose.Words para .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Adicionar Marca d'Água de Texto Diagonal Vermelha a Documentos Word Usando Aspose.Words para .NET
Este tutorial demonstra como incorporar automaticamente uma marca d'água de texto diagonal vermelha em cada documento Word criado durante a geração de relatórios em lote. Usando as classes Document e DocumentBuilder do Aspose.Words para .NET, a marca d'água é aplicada programaticamente à medida que os arquivos são produzidos, garantindo que cada documento carregue a mesma identidade visual ou aviso de confidencialidade sem esforço manual.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: O que a opção **IsSemitrasparent** controla e que efeito tem ao defini-la como **true**?**  
A: IsSemitrasparent determina se a marca d'água é renderizada com opacidade parcial; defini‑la como **true** torna o texto semitransparente, de modo que o conteúdo subjacente permaneça mais legível.

**Q: Posso mudar a orientação da marca d'água para horizontal em vez de diagonal?**  
A: Sim—defina a propriedade **Layout** como **WatermarkLayout.Horizontal** em **TextWatermarkOptions** antes de chamar **document.Watermark.SetText**.

**Q: Este código adicionará uma marca d'água a um arquivo Word existente ou apenas a documentos recém‑criados?**  
A: O trecho cria uma nova instância de **Document**, mas você pode abrir qualquer arquivo existente (por exemplo, `new Document("Existing.docx")`) e então chamar **document.Watermark.SetText** para aplicar a mesma marca d'água.

**Q: Como posso usar uma cor RGB personalizada para a marca d'água em vez do **Color.Red** predefinido?**  
A: Atribua uma cor personalizada com **Color.FromArgb(red, green, blue)** à propriedade **Color** de **TextWatermarkOptions**, por exemplo, `Color = Color.FromArgb(128, 0, 128)` para roxo.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}