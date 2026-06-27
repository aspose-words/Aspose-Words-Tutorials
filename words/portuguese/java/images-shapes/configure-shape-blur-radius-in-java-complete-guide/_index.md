---
category: general
date: 2026-06-27
description: Aprenda a configurar o raio de desfoque de formas usando Aspose.Words
  para Java. Este tutorial passo a passo também aborda configurações de sombra, transparência
  e como salvar o documento.
draft: false
keywords:
- configure shape blur radius
- Aspose.Words shape shadow
- Java shadow format
- Word document shape manipulation
- set blur radius
language: pt
og_description: Configure o raio de desfoque da forma em um documento Word usando
  Java. Siga este tutorial detalhado para dominar as configurações de sombra de forma
  do Aspose.Words.
og_title: Configure o Raio de Desfoque da Forma no Java – Guia Completo
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  headline: Configure Shape Blur Radius in Java – Complete Guide
  type: TechArticle
- description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  name: Configure Shape Blur Radius in Java – Complete Guide
  steps:
  - name: Understanding the Numbers
    text: '- **Blur radius** (`setBlurRadius`) controls how fuzzy the shadow looks.
      A value of `0` gives a crisp edge, while `10` or higher yields a dreamy glow.
      - **DistanceX / DistanceY** shift the shadow relative to the shape. Positive
      X moves it right; positive Y moves it down. - **Transparency** makes the'
  - name: Targeting a Specific Shape by Name
    text: 'If your document contains many shapes, rely on the shape’s **name** (set
      in Word’s layout options) instead of index:'
  - name: Applying Different Blur Radii
    text: 'You might want a stronger blur for background graphics and a subtle one
      for icons. Loop through all shapes:'
  - name: Compatibility Notes
    text: '- **Units:** Aspose.Words uses points (1 pt = 1/72 inch). If you work with
      millimeters, convert accordingly. - **Version:** The API shown works with Aspose.Words
      for Java 24.9 and later. Older versions may use `setBlurRadius(double)` but
      lack some newer shadow properties.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Configure o Raio de Desfoque da Forma no Java – Guia Completo
url: /pt/java/images-shapes/configure-shape-blur-radius-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configurar o Raio de Desfoque da Forma no Java – Guia Completo

Já precisou **configurar o raio de desfoque da forma** em um documento Word enquanto trabalhava com Java? Você não é o único a ficar coçando a cabeça com isso. Seja aprimorando um relatório corporativo ou adicionando um toque visual sutil a um folheto, dominar essa configuração pode deixar seus documentos muito mais profissionais.

Neste tutorial vamos percorrer todo o processo — desde o carregamento do arquivo `.docx` até o ajuste do desfoque da sombra e, finalmente, a gravação do resultado. Ao longo do caminho, também abordaremos tópicos relacionados como **sombra de forma Aspose.Words**, **formato de sombra Java** e manipulação geral de **formas em documentos Word**. Ao final, você terá um trecho de código pronto‑para‑executar e uma compreensão clara do porquê de cada linha.

## O que Você Vai Aprender

- Como carregar um documento Word com Aspose.Words for Java.  
- Como localizar o primeiro objeto `Shape` dentro do corpo do documento.  
- Os passos exatos para **configurar o raio de desfoque da forma** e outras propriedades de sombra, como distância e transparência.  
- Como persistir as alterações em um novo arquivo `.docx`.  

Nenhuma biblioteca externa além do Aspose.Words é necessária, e o código funciona com Java 8‑plus e qualquer versão recente do Aspose.Words for Java (por exemplo, 24.9). Se você está confortável com a sintaxe básica de Java, estará bem.

---

## Etapa 1: Carregar o Documento Word

Antes de tocar em qualquer forma, você precisa do documento na memória. Aspose.Words faz isso em uma única linha.

```java
// Load the source .docx file
com.aspose.words.Document document = new com.aspose.words.Document("YOUR_DIRECTORY/input.docx");
```

**Por que isso importa:**  
Criar um objeto `Document` analisa todo o arquivo, dando acesso a seções, parágrafos, tabelas **e formas**. Pular essa etapa deixaria você sem contexto para aplicar o raio de desfoque.

> **Dica profissional:** Se você estiver lidando com arquivos grandes, considere usar `LoadOptions` para fazer streaming apenas das partes necessárias. Isso pode reduzir drasticamente o uso de memória.

---

## Etapa 2: Recuperar a Forma Alvo

Formas podem estar em qualquer lugar — cabeçalhos, rodapés, tabelas, onde você quiser. Para simplificar, vamos pegar a primeira forma encontrada no corpo principal da primeira seção.

```java
// Navigate to the first shape in the document body
com.aspose.words.Shape shape = (com.aspose.words.Shape) document
        .getFirstSection()
        .getBody()
        .getChild(com.aspose.words.NodeType.SHAPE, 0, true);
```

**Por que isso importa:**  
A chamada `getChild` percorre a árvore de nós em profundidade, retornando a *primeira* forma que corresponde ao `NodeType.SHAPE`. Se seu documento contiver várias formas, você pode ajustar o índice (`0`) ou iterar sobre `document.getChildNodes(NodeType.SHAPE, true)`.

> **Caso de borda:** Se o documento não possuir formas, `shape` será `null` e a linha seguinte lançará um `NullPointerException`. Sempre proteja contra isso em código de produção.

---

## Etapa 3: Configurar a Sombra da Forma – Definir o Raio de Desfoque

Agora vem a estrela do show: ajustar o raio de desfoque. Isso está dentro do objeto `ShadowFormat` associado à forma.

```java
// Access the shadow format of the shape
com.aspose.words.ShadowFormat shadow = shape.getShadowFormat();

// Set the blur radius (in points). Larger values produce a softer edge.
shadow.setBlurRadius(5.0);

// Optional: fine‑tune other shadow attributes
shadow.setDistanceX(3.0);          // Horizontal offset
shadow.setDistanceY(3.0);          // Vertical offset
shadow.setTransparency(0.3);      // 0 = fully opaque, 1 = fully transparent
```

### Entendendo os Valores

- **Raio de desfoque** (`setBlurRadius`) controla o quão difusa a sombra parece. Um valor `0` gera uma borda nítida, enquanto `10` ou superior produz um brilho sonhador.  
- **DistanceX / DistanceY** deslocam a sombra em relação à forma. X positivo move para a direita; Y positivo move para baixo.  
- **Transparency** torna a sombra translúcida. Útil quando você quer um efeito sutil ao invés de um bloco preto sólido.

> **Por que configurar o raio de desfoque?**  
> Em muitos modelos corporativos, um leve desfoque adiciona profundidade sem distrair o leitor. É um ajuste visual pequeno que pode melhorar drasticamente a qualidade percebida.

---

## Etapa 4: Salvar o Documento Modificado

Todo o trabalho pesado está concluído; agora escreva as alterações de volta ao disco.

```java
// Persist the modified document
document.save("YOUR_DIRECTORY/output.docx");
```

**Por que isso importa:**  
Chamar `save` grava todo o documento, incluindo o `ShadowFormat` atualizado. Se você precisar apenas da forma como imagem, pode exportá‑la via `shape.getImageData().save(...)` em vez disso.

---

## Exemplo Completo Funcional

Abaixo está o programa completo e autocontido que você pode copiar‑colar em qualquer IDE Java. Certifique‑se de que o JAR do Aspose.Words for Java esteja no seu classpath.

```java
import com.aspose.words.*;

public class ConfigureShapeBlurRadius {
    public static void main(String[] args) throws Exception {
        // 1. Load the document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Get the first shape (add null‑check for safety)
        Shape shape = (Shape) document.getFirstSection()
                .getBody()
                .getChild(NodeType.SHAPE, 0, true);
        if (shape == null) {
            System.out.println("No shape found in the document.");
            return;
        }

        // 3. Configure shadow – focus on blur radius
        ShadowFormat shadow = shape.getShadowFormat();
        shadow.setBlurRadius(5.0);          // Soft blur
        shadow.setDistanceX(3.0);           // Horizontal offset
        shadow.setDistanceY(3.0);           // Vertical offset
        shadow.setTransparency(0.3);        // Slightly transparent

        // 4. Save the result
        document.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved with configured shape blur radius.");
    }
}
```

**Saída esperada:**  
Executar o programa produz um novo `output.docx` onde a primeira forma agora possui uma sombra suave, semi‑transparente, com raio de desfoque de `5` pontos. Abra o arquivo no Word, selecione a forma e, em **Formato da Forma → Efeitos de Sombra → Opções de Sombra**, você verá os valores que definiu refletidos na interface.

---

## Manipulando Múltiplas Formas & Cenários Avançados

### Alvo de uma Forma Específica por Nome

Se seu documento contém muitas formas, baseie‑se no **nome** da forma (definido nas opções de layout do Word) em vez do índice:

```java
Shape target = (Shape) document.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getName().equals("MyLogo"))
        .findFirst()
        .orElse(null);
```

### Aplicando Raios de Desfoque Diferentes

Talvez você queira um desfoque mais forte para gráficos de fundo e um sutil para ícones. Percorra todas as formas:

```java
for (Node node : document.getChildNodes(NodeType.SHAPE, true)) {
    Shape s = (Shape) node;
    ShadowFormat sf = s.getShadowFormat();
    sf.setBlurRadius(s.getName().contains("Background") ? 10.0 : 3.0);
}
```

### Notas de Compatibilidade

- **Unidades:** Aspose.Words usa pontos (1 pt = 1/72 polegada). Se você trabalha com milímetros, converta adequadamente.  
- **Versão:** A API mostrada funciona com Aspose.Words for Java 24.9 ou posterior. Versões mais antigas podem usar `setBlurRadius(double)`, mas carecem de algumas propriedades de sombra mais recentes.

---

## Armadilhas Comuns & Como Evitá‑las

| Armadilha | Por que Acontece | Solução |
|-----------|------------------|---------|
| `NullPointerException` em `shape` | O documento não tem formas ou o índice está fora do intervalo | Adicione uma verificação de null antes de acessar `ShadowFormat`. |
| Sombra não visível no Word | A cor da sombra padrão é transparente ou os valores de distância a deslocam para fora da página | Defina uma `ShadowColor` visível (`shadow.setColor(Color.BLACK)`) e mantenha `DistanceX/Y` modestos. |
| Raio de desfoque permanece inalterado | Uso de uma versão antiga do Aspose.Words que ignora a propriedade | Atualize para a biblioteca mais recente; a propriedade foi introduzida na versão 20.5. |
| Desempenho lento em documentos enormes | Re‑salvar o documento inteiro após cada modificação de forma | Agrupe todas as alterações e chame `save` apenas uma vez. |

---

## Conclusão

Agora você sabe **como configurar o raio de desfoque da forma** em um documento Word usando Java e Aspose.Words. Desde o carregamento do arquivo, captura da `Shape` correta, ajuste do `ShadowFormat`, até a persistência das alterações — cada passo foi coberto com explicações e dicas práticas.

A técnica não se limita a uma única forma; você pode escalá‑la para documentos inteiros, aplicar diferentes níveis de desfoque ou combiná‑la com outros atributos de sombra, como **transparência da sombra Java**. Os próximos passos lógicos são explorar **definir raio de desfoque** para imagens, experimentar **formato de sombra Java** em gráficos, ou aprofundar‑se em **manipulação de formas em documentos Word** para geração dinâmica de relatórios.

Tem um cenário que não foi abordado aqui? Deixe um comentário ou consulte a documentação do Aspose.Words for Java para efeitos de sombra mais avançados. Feliz codificação!

---

<img src="configure-shape-blur-radius.png" alt="Configurar raio de desfoque da forma usando exemplo Aspose.Words Java" style="max-width:100%;">

---


## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}