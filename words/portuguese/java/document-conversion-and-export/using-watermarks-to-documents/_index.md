---
date: 2026-02-19
description: Aprenda a criar um documento com marca d'água usando Aspose.Words para
  Java e a adicionar marca d'água de imagem em Java para documentos com aparência
  profissional.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Criar documento com marca d'água usando Aspose.Words para Java
url: /pt/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

 With:** Aspose.Words for Java 24.12 (latest) -> "**Testado com:** Aspose.Words for Java 24.12 (latest)"

**Author:** Aspose -> "**Autor:** Aspose"

Make sure markdown bold formatting preserved.

Now produce final content with all sections.

Check we didn't translate any code blocks placeholders.

Make sure we keep shortcodes at start and end.

Let's craft final output.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento com marca d'água usando Aspose.Words for Java

Neste tutorial você **criará documento com marca d'água** usando a API Aspose.Words for Java. Marcas d'água—sejam texto ou imagens—ajudam a rotular um arquivo como confidencial, rascunho ou aprovado, e podem ser aplicadas programaticamente a qualquer documento Word. Vamos percorrer a configuração da biblioteca, a adição de marcas d'água de texto e de imagem, a personalização de sua aparência e até a remoção delas quando não forem mais necessárias.

## Respostas rápidas
- **O que uma marca d'água faz?** Ela sobrepõe texto ou uma imagem em cada página para transmitir status ou branding.  
- **Qual biblioteca adiciona marcas d'água em Java?** Aspose.Words for Java fornece suporte integrado a marcas d'água.  
- **Posso adicionar uma marca d'água de imagem?** Sim—use a classe `Shape` e a abordagem `add image watermark java`.  
- **A marca d'água é semitransparente?** Você pode controlar a opacidade via `setSemitransparent` para marcas d'água de texto.  
- **Preciso de licença?** Um teste gratuito funciona para testes; uma licença comercial é necessária para produção.

## O que é uma marca d'água e por que usá‑la?

Uma marca d'água é uma sobreposição sutil—textual ou gráfica—adicionada a cada página de um documento. É comumente usada para indicar **confidencialidade**, **status de rascunho** ou **branding** sem alterar o conteúdo subjacente. Adicionar marcas d'água programaticamente garante consistência em grandes lotes de arquivos e economiza tempo comparado à edição manual.

## Configurando Aspose.Words for Java

Antes de começar a adicionar marcas d'água, certifique‑se de que a biblioteca está pronta no seu projeto:

1. Baixe Aspose.Words for Java de [aqui](https://releases.aspose.com/words/java/).  
2. Adicione o JAR baixado (ou a dependência Maven/Gradle) ao classpath do seu projeto.  
3. Importe as classes necessárias no seu arquivo fonte Java:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Agora que a biblioteca está configurada, vamos mergulhar no código real da marca d'água.

## Como adicionar uma marca d'água de texto

Marcas d'água de texto são ideais para rotular um documento como “CONFIDENTIAL” ou “DRAFT”. O trecho a seguir mostra uma forma limpa de **criar documento com marca d'água** usando `TextWatermarkOptions`.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

### Personalizando a marca d'água de texto
- **Família e tamanho da fonte** – altere `setFontFamily` e `setFontSize`.  
- **Cor** – use qualquer `java.awt.Color`.  
- **Layout** – escolha `HORIZONTAL`, `DIAGONAL`, etc.  
- **Transparência** – ative `setSemitransparent(true)` para um aspecto mais claro.

## Como adicionar uma marca d'água de imagem (add image watermark java)

Marcas d'água de imagem são perfeitas para logotipos ou gráficos personalizados. Abaixo está o exemplo **add image watermark java** que insere um PNG no centro de cada página.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

### Dicas para marcas d'água de imagem
- **Redimensionar** usando `setWidth` / `setHeight` para ajustar à página.  
- **Posição** pode ser centralizada ou alinhada a qualquer margem usando `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Transparência** pode ser aplicada ajustando o canal alfa da imagem antes de carregá‑la.

## Como remover marcas d'água

Quando um documento não precisa mais de uma marca d'água, você pode excluí‑la programaticamente. O código abaixo itera por todas as formas e remove quaisquer que contenham “Watermark” no nome.

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Armadilhas comuns e solução de problemas

- **Marca d'água ausente após salvar** – garanta que você chame `doc.save()` após definir a marca d'água.  
- **Imagem não aparece** – verifique se o caminho da imagem está correto e se o arquivo está em um formato suportado (PNG, JPEG, BMP).  
- **Transparência não aplicada** – `setSemitransparent(true)` funciona apenas para marcas d'água de texto; para imagens, edite o canal alfa do PNG.  
- **Múltiplas seções** – se seu documento tem várias seções, adicione a marca d'água ao corpo de cada seção ou use `doc.getWatermark().setText(...)` que aplica globalmente.

## Perguntas Frequentes

**Q: Como posso mudar a fonte de uma marca d'água de texto?**  
A: Modifique a propriedade `setFontFamily` em `TextWatermarkOptions`, por exemplo, `options.setFontFamily("Times New Roman");`.

**Q: Posso adicionar múltiplas marcas d'água a um único documento?**  
A: Sim. Crie múltiplos objetos `Shape` (para imagens) ou chame `doc.getWatermark().setText(...)` com opções diferentes para cada marca d'água.

**Q: É possível girar uma marca d'água?**  
A: Para marcas d'água de imagem, defina a rotação no objeto `Shape` com `watermark.setRotation(angle)`. Para marcas d'água de texto, use a propriedade `setLayout` (por exemplo, `WatermarkLayout.DIAGONAL`).

**Q: Como posso tornar uma marca d'água semitransparente?**  
A: Defina `options.setSemitransparent(true)` em `TextWatermarkOptions`. Para imagens, ajuste a opacidade da imagem antes de carregá‑la.

**Q: Posso adicionar marcas d'água a seções específicas de um documento?**  
A: Sim. Itere através de `doc.getSections()` e adicione a marca d'água apenas nas seções desejadas.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Última atualização:** 2026-02-19  
**Testado com:** Aspose.Words for Java 24.12 (latest)  
**Autor:** Aspose