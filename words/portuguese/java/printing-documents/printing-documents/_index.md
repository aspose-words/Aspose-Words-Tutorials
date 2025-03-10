---
title: Imprimindo documentos no Aspose.Words para Java
linktitle: Imprimindo Documentos
second_title: API de processamento de documentos Java Aspose.Words
description: Aprenda a imprimir documentos usando Aspose.Words para Java. Guia passo a passo para impressão perfeita em seus aplicativos Java.
weight: 10
url: /pt/java/printing-documents/printing-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Imprimindo documentos no Aspose.Words para Java


Se você está procurando imprimir documentos usando o Aspose.Words para Java, você está no lugar certo. Neste guia passo a passo, nós o guiaremos pelo processo de impressão de documentos com o Aspose.Words para Java usando o código-fonte fornecido.

## Introdução

Imprimir documentos é uma tarefa comum em muitos aplicativos. O Aspose.Words para Java fornece uma API poderosa para trabalhar com documentos do Word, incluindo a capacidade de imprimi-los. Neste tutorial, guiaremos você pelo processo de impressão de um documento do Word passo a passo.

## Configurando seu ambiente

Antes de mergulharmos no código, certifique-se de ter os seguintes pré-requisitos em vigor:

- Java Development Kit (JDK) instalado
- Biblioteca Aspose.Words para Java baixada e adicionada ao seu projeto

## Carregando o documento

 Para começar, você precisará carregar o documento do Word que deseja imprimir. Substituir`"Your Document Directory"` com o caminho para o seu documento e`"Your Output Directory"` com o diretório de saída desejado.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Criando um trabalho de impressão

Em seguida, criaremos um trabalho de impressão para imprimir nosso documento carregado. O trecho de código abaixo inicializa um trabalho de impressão e define as configurações desejadas da impressora.

```java
// Crie um trabalho de impressão para imprimir nosso documento.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inicialize um conjunto de atributos com o número de páginas no documento.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Passe as configurações da impressora junto com os outros parâmetros para o documento de impressão.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## Imprimindo o documento

Agora que configuramos nosso trabalho de impressão, é hora de imprimir o documento. O seguinte trecho de código associa o documento ao trabalho de impressão e inicia o processo de impressão.

```java
// Passe o documento a ser impresso usando o trabalho de impressão.
pj.setPrintable(awPrintDoc);
pj.print();
```
## Código fonte completo
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Crie um trabalho de impressão para imprimir nosso documento.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inicialize um conjunto de atributos com o número de páginas no documento.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Passe as configurações da impressora junto com os outros parâmetros para o documento de impressão.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// Passe o documento a ser impresso usando o trabalho de impressão.
pj.setPrintable(awPrintDoc);
pj.print();
```
Código fonte do MultipagePrintDocument
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <resumo>
    /// O construtor da classe PrintDocument personalizada.
    // / </resumo>
    public MultipagePrintDocument(Document document, int pagesPerSheet, boolean printPageBorders,
                                  AttributeSet attributes) {
        if (document == null)
            throw new IllegalArgumentException("document");
        mDocument = document;
        mPagesPerSheet = pagesPerSheet;
        mPrintPageBorders = printPageBorders;
        mAttributeSet = attributes;
    }
    public int print(Graphics g, PageFormat pf, int page) {
        //Os índices de início e fim da página, conforme definidos no conjunto de atributos.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Calcule o índice da página que será renderizada em seguida.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Se o índice da página for maior que o intervalo total de páginas, então não há nada
        // mais para renderizar.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Calcule o tamanho de cada espaço reservado para miniatura em pontos.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Calcule o número da primeira página a ser impressa nesta folha de papel.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Selecione o número da última página a ser impressa nesta folha de papel.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Percorrer as páginas selecionadas da página atual armazenada para a página calculada
        // última página.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Calcule os índices de coluna e linha.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Defina a localização da miniatura em coordenadas mundiais (pontos neste caso).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Calcule as posições iniciais esquerda e superior.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // Renderizar a página do documento para o objeto Graphics usando coordenadas calculadas
                // e tamanho do espaço reservado para miniaturas.
                // O valor de retorno útil é a escala na qual a página foi renderizada.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                //Desenhe as bordas da página (a miniatura da página pode ser menor que a miniatura
                // tamanho do espaço reservado).
                if (mPrintPageBorders) {
                    // Obtenha o tamanho real de 100% da página em pontos.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Desenhe a borda ao redor da página dimensionada usando o fator de escala conhecido.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Desenhe a borda ao redor do espaço reservado para miniatura.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Se ocorrer algum erro durante a renderização, não faça nada.
                // Isso desenhará uma página em branco caso haja algum erro durante a renderização.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // Defina o número de colunas e linhas na planilha para o
        // Artigo com orientação paisagística.
        switch (pagesPerSheet) {
            case 16:
                size = new Dimension(4, 4);
                break;
            case 9:
                size = new Dimension(3, 3);
                break;
            case 8:
                size = new Dimension(4, 2);
                break;
            case 6:
                size = new Dimension(3, 2);
                break;
            case 4:
                size = new Dimension(2, 2);
                break;
            case 2:
                size = new Dimension(2, 1);
                break;
            default:
                size = new Dimension(1, 1);
                break;
        }
        // Troque a largura e a altura se o papel estiver na orientação Retrato.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## Conclusão

Parabéns! Você imprimiu com sucesso um documento do Word usando o Aspose.Words para Java. Este guia passo a passo deve ajudar você a integrar a impressão de documentos em seus aplicativos Java perfeitamente.

## Perguntas frequentes

### P1: Posso imprimir páginas específicas de um documento usando o Aspose.Words para Java?

 Sim, você pode especificar o intervalo de páginas ao imprimir um documento. No exemplo de código, usamos`attributes.add(new PageRanges(1, doc.getPageCount()))`para imprimir todas as páginas. Você pode ajustar o intervalo de páginas conforme necessário.

### P2: O Aspose.Words para Java é adequado para impressão em lote?

Absolutamente! O Aspose.Words para Java é bem adequado para tarefas de impressão em lote. Você pode iterar por uma lista de documentos e imprimi-los um por um usando código similar.

### P3: Como posso lidar com erros de impressão ou exceções?

Você deve lidar com quaisquer exceções potenciais que possam ocorrer durante o processo de impressão. Verifique a documentação do Aspose.Words for Java para obter informações sobre como lidar com exceções.

### P4: Posso personalizar ainda mais as configurações de impressão?

Sim, você pode personalizar as configurações de impressão para atender às suas necessidades específicas. Explore a documentação do Aspose.Words for Java para saber mais sobre as opções de impressão disponíveis.

### P5: Onde posso obter mais ajuda e suporte para o Aspose.Words para Java?

 Para obter suporte e assistência adicionais, você pode visitar o[Fórum Aspose.Words para Java](https://forum.aspose.com/).

---

Agora que você aprendeu com sucesso como imprimir documentos usando Aspose.Words para Java, você pode começar a implementar essa funcionalidade em seus aplicativos Java. Boa codificação!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
