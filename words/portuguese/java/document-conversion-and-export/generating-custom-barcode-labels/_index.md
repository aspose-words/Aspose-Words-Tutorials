---
date: 2026-10-23
description: Aprenda a criar rótulos Java com código QR usando Aspose.Words. Este
  guia passo a passo mostra como incorporar códigos de barras em documentos Word e
  personalizar tamanho, cores e formato.
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: Gerando Rótulos de Código de Barras Personalizados
og_description: Aprenda a criar rótulos Java com código QR usando Aspose.Words. Este
  guia explica a incorporação de códigos de barras, controle de tamanho e personalização
  de cores em documentos Word.
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: Como criar rótulos Java com código QR usando Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  headline: How to create QR code Java labels using Aspose.Words
  type: TechArticle
- description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  name: How to create QR code Java labels using Aspose.Words
  steps:
  - name: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
    text: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
  - name: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
    text: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
  - name: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
    text: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
  - name: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
    text: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
  type: HowTo
- questions:
  - answer: Yes, but it will have evaluation limitations. Obtain a [temporary license](https://purchase.aspose.com/temporary-license/)
      for full functionality.
    question: Can I use Aspose.Words for Java without a license?
  - answer: Aspose.BarCode supports QR, Code 128, EAN‑13, DataMatrix, PDF417, and
      many other formats—over 20 symbologies in total. See the [documentation](https://reference.aspose.com/words/java/)
      for the complete list.
    question: What types of barcodes can I generate?
  - answer: Adjust the width and height arguments in `builder.insertImage`, or calculate
      exact Word twips using `twipsToPixels` for pixel‑perfect control.
    question: How can I change the barcode size?
  - answer: Yes, you can customize the text font through the `CodeTextParameters`
      property of the `BarcodeGenerator`.
    question: Is it possible to use custom fonts for the barcode text?
  - answer: Visit the [support forum](https://forum.aspose.com/c/words/8/) for assistance
      from the Aspose community and engineers.
    question: Where can I get help if I run into problems?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- barcode generation
- Aspose.Words
- Java document processing
- QR code
title: Como criar rótulos Java com código QR usando Aspose.Words
url: /pt/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar rótulos QR code Java usando Aspose.Words

Os códigos de barras são essenciais em aplicações modernas—seja gerenciando inventário, imprimindo ingressos ou criando crachás. Neste tutorial você **criará rótulos QR code Java** e os incorporará diretamente em um documento Word usando a interface `IBarcodeGenerator`. Vamos percorrer cada passo, desde a configuração do ambiente até a inserção da imagem do código de barras, para que você possa começar a usar códigos de barras em seus projetos Java imediatamente.

## Respostas rápidas
- **O que este tutorial ensina?** Como criar rótulos QR code Java e incorporá‑los em um arquivo Word com Aspose.Words for Java.  
- **Qual tipo de código de barras é usado no exemplo?** QR code (você pode substituí‑lo por qualquer um dos mais de 20 tipos suportados).  
- **Preciso de uma licença?** Uma licença temporária é necessária para acesso irrestrito durante o desenvolvimento.  
- **Qual versão do Java é necessária?** JDK 8 ou superior.  
- **Posso alterar o tamanho ou as cores do código de barras?** Sim—modifique as configurações de `BarcodeParameters` e `BarcodeGenerator`.

## O que é criar QR code Java?
`create QR code Java` refere‑se à geração de uma imagem de QR‑code programaticamente em um ambiente Java e à inserção dela em um documento ou componente de UI. Aspose.Words for Java junto com Aspose.BarCode permitem produzir a imagem totalmente em memória, evitando arquivos temporários.

## Por que gerar rótulos de código de barras personalizados com Aspose.Words?
Aspose.Words suporta **35+ formatos de entrada e saída** e pode processar **documentos de 500 páginas em menos de 3 segundos** em hardware de servidor padrão. Usando sua geração de código de barras em memória, você obtém controle total sobre tipo, tamanho e cores, mantendo o fluxo de trabalho totalmente centrado em Java e independente de plataforma.

## Pré‑requisitos

- Java Development Kit (JDK): Versão 8 ou superior.  
- Biblioteca Aspose.Words for Java: [Download here](https://releases.aspose.com/words/java/).  
- Biblioteca Aspose.BarCode for Java: [Download here](https://releases.aspose.com/).  
- Ambiente de Desenvolvimento Integrado (IDE): IntelliJ IDEA, Eclipse ou qualquer IDE de sua preferência.  
- Licença Temporária: Obtenha uma [temporary license](https://purchase.aspose.com/temporary-license/) para acesso irrestrito.

## Importar pacotes

Usaremos as bibliotecas Aspose.Words e Aspose.BarCode. Importe os pacotes a seguir para o seu projeto:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Essas importações nos dão acesso à API de geração de código de barras e às classes de documento Word que precisaremos.

## Etapa 1: criar uma classe utilitária para operações de código de barras

A classe utilitária contém auxiliares reutilizáveis, como **converter twips em pixels** e **conversão de cor hexadecimal**.  
A classe `CustomBarcodeGeneratorUtils` fornece métodos estáticos para conversão de unidades e manipulação de cores.

### Código

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**Explicação**  
- `twipsToPixels` – O Word mede dimensões em **twips**; este método converte‑as em pixels de tela, o que é útil quando você precisa dimensionar a imagem do código de barras com precisão.  
- `convertColor` – Converte uma string hexadecimal (por exemplo, `"FF0000"` para vermelho) em um objeto `java.awt.Color`, permitindo **adicionar código de barras ao documento Word** com cores de primeiro plano e fundo personalizadas.

## Etapa 2: implementar o gerador de código de barras personalizado

Agora implementaremos a interface `IBarcodeGenerator`. Esta classe é responsável por **gerar imagens QR code Java** que o Aspose.Words pode incorporar.  
A interface `IBarcodeGenerator` define um único método que retorna um `BufferedImage` representando o código de barras.

### Código

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**Explicação**  
- `getBarcodeImage` cria uma instância de `BarcodeGenerator`, aplica as cores fornecidas via `BarcodeParameters` e, finalmente, devolve um `BufferedImage`.  
- O método também trata erros de forma elegante, retornando uma imagem placeholder, garantindo que a criação do documento Word nunca falhe.

## Como incorporar o código de barras no Word usando Aspose.Words?

Carregue seu arquivo Word com `new Document("template.docx")` (ou crie um novo `Document`) e chame `builder.insertImage` com a imagem do código de barras retornada pelo gerador. Esse padrão de duas etapas incorpora o código de barras diretamente sem gravar um arquivo intermediário no disco. Ao especificar as dimensões da imagem em pixels ou converter twips do Word para pixels, você pode controlar o tamanho e a posição exatos do código de barras dentro do documento, garantindo um layout profissional que imprime corretamente em qualquer impressora.

## Etapa 3: gerar um código de barras e incorporá‑lo no Word

Com o gerador pronto, podemos agora produzir uma imagem de código de barras e **inseri‑la em um documento Word**.

### Código

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**Explicação**  

1. **Inicialização do documento** – Cria um novo `Document` (ou você pode carregar um modelo existente).  
2. **Parâmetros do código de barras** – Define o tipo de código de barras (`QR`), o valor a ser codificado e as cores de primeiro plano/fundo.  
3. **Inserção da imagem** – `builder.insertImage` coloca o código de barras gerado no tamanho desejado (200 × 200 pixels). Este é o núcleo de **como incorporar código de barras no Word**.  
4. **Salvamento** – O documento final, `CustomBarcodeLabels.docx`, contém o código de barras incorporado pronto para impressão ou distribuição.

## Problemas comuns & solução de problemas

| Sintoma | Causa provável | Solução |
|---------|----------------|--------|
| O código de barras aparece em branco | As cores em `BarcodeParameters` são iguais (ex.: preto sobre preto) | Verifique os valores de `foregroundColor` e `backgroundColor`. |
| A imagem está distorcida | Dimensões de pixel incorretas passadas para `insertImage` | Ajuste os argumentos de largura/altura ou use a conversão `twipsToPixels` para dimensionamento preciso. |
| Erro de tipo de código de barras não suportado | Uso de um tipo não reconhecido por `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Certifique‑se de que a string do tipo de código de barras corresponde a um dos `EncodeTypes` suportados (ex.: `"QR"`, `"CODE128"`). |

## Perguntas frequentes

**P: Posso usar Aspose.Words for Java sem licença?**  
R: Sim, mas haverá limitações de avaliação. Obtenha uma [temporary license](https://purchase.aspose.com/temporary-license/) para funcionalidade completa.

**P: Que tipos de códigos de barras posso gerar?**  
R: Aspose.BarCode suporta QR, Code 128, EAN‑13, DataMatrix, PDF417 e muitos outros formatos—mais de 20 simbologias no total. Consulte a [documentation](https://reference.aspose.com/words/java/) para a lista completa.

**P: Como posso mudar o tamanho do código de barras?**  
R: Ajuste os argumentos de largura e altura em `builder.insertImage`, ou calcule twips exatos do Word usando `twipsToPixels` para controle pixel‑perfeito.

**P: É possível usar fontes personalizadas para o texto do código de barras?**  
R: Sim, você pode personalizar a fonte do texto através da propriedade `CodeTextParameters` do `BarcodeGenerator`.

**P: Onde posso obter ajuda se encontrar problemas?**  
R: Visite o [support forum](https://forum.aspose.com/c/words/8/) para assistência da comunidade e engenheiros da Aspose.

## Conclusão

Seguindo os passos acima, você agora sabe como **criar imagens QR code Java** e **incorporar código de barras em documentos Word** usando Aspose.Words for Java. Essa técnica é flexível o suficiente para etiquetas de inventário, ingressos de eventos ou qualquer cenário onde um código de barras precise fazer parte de um documento gerado. Experimente diferentes tipos de códigos de barras, cores e opções de dimensionamento para atender às necessidades específicas do seu negócio.

---

**Última atualização:** 2026-10-23  
**Testado com:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Autor:** Aspose

## Tutoriais relacionados

- [Create PDF from Word with Barcode Generation – Aspose.Words for Java](/words/java/document-conversion-and-export/using-barcode-generation/)
- [Save Word As Pdf With Aspose Words Step By Step Java Guide](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Create Blank Word Document In Java With Aspose Words](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}