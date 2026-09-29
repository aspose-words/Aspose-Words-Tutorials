---
title: Criar uma Marca d'Água de Texto Diagonal com Fonte Personalizada em um Documento Word usando Aspose.Words para .NET
weight: 210
limit:
description: Código passo a passo para adicionar uma marca d'água de texto diagonal com fonte personalizada a um .docx do Word usando Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Código passo a passo para adicionar uma marca d'água de texto diagonal
    com fonte personalizada a um .docx do Word usando Aspose.Words para .NET.
  headline: Criar uma Marca d'Água de Texto Diagonal com Fonte Personalizada em um
    Documento Word usando Aspose.Words para .NET
  type: TechArticle
- description: Código passo a passo para adicionar uma marca d'água de texto diagonal
    com fonte personalizada a um .docx do Word usando Aspose.Words para .NET.
  name: Criar uma Marca d'Água de Texto Diagonal com Fonte Personalizada em um Documento
    Word usando Aspose.Words para .NET
  steps:
  - name: Crie uma nova instância vazia de documento Word chamada `document`.
    text: Crie uma nova instância vazia de documento Word chamada `document`.
  - name: Configure `watermarkSettings` com fonte Arial 48 pt cinza, layout diagonal
      e renderização opaca.
    text: Configure `watermarkSettings` com fonte Arial 48 pt cinza, layout diagonal
      e renderização opaca.
  - name: Aplique a marca d'água de texto "Private" ao `document` usando as configurações
      definidas anteriormente.
    text: Aplique a marca d'água de texto "Private" ao `document` usando as configurações
      definidas anteriormente.
  - name: Defina o caminho do arquivo onde o documento com marca d'água será salvo.
    text: Defina o caminho do arquivo onde o documento com marca d'água será salvo.
  - name: Salve o `document` modificado no caminho especificado como um arquivo .docx.
    text: Salve o `document` modificado no caminho especificado como um arquivo .docx.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` determina se a marca d''água é renderizada com opacidade
      parcial; definir como `false` torna a marca d''água totalmente opaca, enquanto
      `true` aplica um efeito semitransparente padrão.'
    question: O que controla a flag **IsSemitrasparent** em `TextWatermarkOptions`?
  - answer: Sim—defina a propriedade `Layout` como `WatermarkLayout.Horizontal` (ou
      outro valor de enum) antes de chamar `document.Watermark.SetText`.
    question: Posso mudar a orientação da marca d'água para horizontal em vez de diagonal?
  - answer: O Word usará sua fonte padrão para a marca d'água, portanto o texto ainda
      aparecerá, mas pode ter uma aparência diferente do estilo pretendido.
    question: O que acontece se a `FontFamily` especificada (por exemplo, "Arial")
      não estiver instalada na máquina de destino?
  - answer: Carregue o arquivo existente com `Document document = new Document(\"Existing.docx\");`
      depois configure `TextWatermarkOptions` e chame `document.Watermark.SetText`
      conforme mostrado.
    question: É possível adicionar uma marca d'água a um arquivo `.docx` existente
      em vez de criar um novo?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Adicionar uma Marca d'Água de Texto Diagonal com Fonte Personalizada
og_description: Aprenda a inserir uma marca d'água de texto inclinado com sua própria fonte em um arquivo Word em minutos.
og_image_alt: Guia que mostra como adicionar uma marca d'água de texto diagonal com fonte personalizada a um documento Word usando Aspose.Words para .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Criar uma Marca d'Água de Texto Diagonal com Fonte Personalizada em um Documento Word usando Aspose.Words para .NET
Este tutorial orienta você na criação de um novo documento Word, na configuração de uma marca d'água de texto diagonal com as configurações de fonte escolhidas, na aplicação dela via a API Document.Watermark.SetText e na gravação do resultado como um arquivo .docx. Ao final, você terá um documento profissionalmente marcado que exibe sua marca ou propriedade. O código passo a passo está pronto para ser copiado em qualquer projeto .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: O que controla a flag **IsSemitrasparent** em `TextWatermarkOptions`?**  
A: `IsSemitrasparent` determina se a marca d'água é renderizada com opacidade parcial; definir como `false` torna a marca d'água totalmente opaca, enquanto `true` aplica um efeito semitransparente padrão.

**Q: Posso mudar a orientação da marca d'água para horizontal em vez de diagonal?**  
A: Sim—defina a propriedade `Layout` como `WatermarkLayout.Horizontal` (ou outro valor de enum) antes de chamar `document.Watermark.SetText`.

**Q: O que acontece se a `FontFamily` especificada (por exemplo, "Arial") não estiver instalada na máquina de destino?**  
A: O Word usará sua fonte padrão para a marca d'água, portanto o texto ainda aparecerá, mas pode ter uma aparência diferente do estilo pretendido.

**Q: É possível adicionar uma marca d'água a um arquivo `.docx` existente em vez de criar um novo?**  
A: Carregue o arquivo existente com `Document document = new Document(\"Existing.docx\");` depois configure `TextWatermarkOptions` e chame `document.Watermark.SetText` conforme mostrado.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}