---
title: Inserir código de barras DataMatrix em documento Word usando Aspose.Words for .NET
weight: 210
limit:
description: Adicione um código de barras DataMatrix a um documento Word programaticamente com Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Adicione um código de barras DataMatrix a um documento Word programaticamente
    com Aspose.Words for .NET.
  headline: Inserir código de barras DataMatrix em documento Word usando Aspose.Words
    for .NET
  type: TechArticle
- description: Adicione um código de barras DataMatrix a um documento Word programaticamente
    com Aspose.Words for .NET.
  name: Inserir código de barras DataMatrix em documento Word usando Aspose.Words
    for .NET
  steps:
  - name: Crie um novo Documento Word vazio e um DocumentBuilder para editá-lo.
    text: Crie um novo Documento Word vazio e um DocumentBuilder para editá-lo.
  - name: Insira um campo DISPLAYBARCODE na posição atual do cursor, o que adiciona
      um marcador de posição de campo ao documento.
    text: Insira um campo DISPLAYBARCODE na posição atual do cursor, o que adiciona
      um marcador de posição de campo ao documento.
  - name: Defina o BarcodeType do campo como DataMatrix e forneça a string de dados
      a ser codificada.
    text: Defina o BarcodeType do campo como DataMatrix e forneça a string de dados
      a ser codificada.
  - name: Opcionalmente, defina as cores de fundo e de primeiro plano do código de
      barras.
    text: Opcionalmente, defina as cores de fundo e de primeiro plano do código de
      barras.
  - name: Chame UpdateFields no documento para renderizar a imagem do código de barras
      dentro do campo.
    text: Chame UpdateFields no documento para renderizar a imagem do código de barras
      dentro do campo.
  - name: Salve o documento em um arquivo .docx.
    text: Salve o documento em um arquivo .docx.
  type: HowTo
- questions:
  - answer: O campo será inserido, mas `document.UpdateFields()` deixará o código
      de barras em branco e Aspose.Words lançará uma `FieldException` indicando um
      tipo de código de barras inválido.
    question: O que acontece se eu atribuir um valor não suportado a `displayBarcodeField.BarcodeType`?
  - answer: '`UpdateFields()` renderiza as imagens dos códigos de barras, portanto
      você pode inserir vários objetos `FieldDisplayBarcode` e chamar `document.UpdateFields()`
      uma única vez ao final para renderizá-los todos.'
    question: Preciso chamar `document.UpdateFields()` após cada inserção de código
      de barras, ou posso atualizar uma única vez após adicionar todos os campos?
  - answer: Ambas as propriedades esperam uma string RGB hexadecimal prefixada com
      `0x` (por exemplo, "0xFF0000" para vermelho); qualquer outro formato será ignorado
      e as cores padrão serão usadas.
    question: Em que formato as strings de cor devem estar para `BackgroundColor`
      e `ForegroundColor`?
  - answer: Sim — basta definir `displayBarcodeField.BarcodeValue` para uma nova string
      e chamar `document.UpdateFields()` novamente para atualizar a imagem renderizada.
    question: Posso alterar o conteúdo do código de barras depois que o campo foi
      inserido?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Inserir um código de barras DataMatrix com Aspose.Words
og_description: Aprenda como adicionar um código de barras DataMatrix a um arquivo Word em apenas algumas linhas de código .NET.
og_image_alt: Guia que mostra como inserir e renderizar um código de barras DataMatrix em um documento Word usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir código de barras DataMatrix em documento Word usando Aspose.Words
Com Aspose.Words for .NET você pode adicionar programaticamente um código de barras DataMatrix a um documento Word. Este tutorial mostra como criar um novo documento, inserir um campo DISPLAYBARCODE, definir seu tipo como DataMatrix e renderizar a imagem do código de barras usando as classes Document e DocumentBuilder. Siga os passos para gerar um código de barras imprimível diretamente dentro do seu arquivo .docx.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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

**Q: O que acontece se eu atribuir um valor não suportado a `displayBarcodeField.BarcodeType`?**  
A: O campo será inserido, mas `document.UpdateFields()` deixará o código de barras em branco e Aspose.Words lançará uma `FieldException` indicando um tipo de código de barras inválido.

**Q: Preciso chamar `document.UpdateFields()` após cada inserção de código de barras, ou posso atualizar uma única vez após adicionar todos os campos?**  
A: `UpdateFields()` renderiza as imagens dos códigos de barras, portanto você pode inserir vários objetos `FieldDisplayBarcode` e chamar `document.UpdateFields()` uma única vez ao final para renderizá-los todos.

**Q: Em que formato as strings de cor devem estar para `BackgroundColor` e `ForegroundColor`?**  
A: Ambas as propriedades esperam uma string RGB hexadecimal prefixada com `0x` (por exemplo, "0xFF0000" para vermelho); qualquer outro formato será ignorado e as cores padrão serão usadas.

**Q: Posso alterar o conteúdo do código de barras depois que o campo foi inserido?**  
A: Sim — basta definir `displayBarcodeField.BarcodeValue` para uma nova string e chamar `document.UpdateFields()` novamente para atualizar a imagem renderizada.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}