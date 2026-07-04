---
category: general
date: 2026-06-20
description: Salve o documento Word usando Aspose.Words em Java enquanto adiciona
  uma forma retangular e aplica uma sombra. Aprenda como inserir a forma passo a passo.
draft: false
keywords:
- save word document
- add rectangle shape
- apply shadow to shape
- how to add shadow
- how to insert shape
language: pt
og_description: Salvar documento Word com Aspose.Words Java. Este guia mostra como
  adicionar uma forma retangular, aplicar uma sombra e inseri‑la em um parágrafo.
og_title: Salvar documento Word – Adicionar forma retangular e sombra em Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  headline: Save Word Document – Add Rectangle Shape & Shadow in Java
  type: TechArticle
- description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  name: Save Word Document – Add Rectangle Shape & Shadow in Java
  steps:
  - name: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
    text: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
  - name: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
    text: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
  - name: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
    text: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the target `Section` or `PageSetup` and insert the shape
      into a paragraph located on that page.
    question: Can I add the shape to a specific page?
  - answer: Absolutely. Aspose.Words abstracts the format, so the same code **saves
      a Word document** whether it’s `.doc` or `.docx`.
    question: Does this work with .doc files?
  - answer: 'Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`. All shadow properties
      remain the same. --- ## Conclusion You now know how to **save a Word document**
      while **adding a rectangle shape**, **applying a shadow**, and **inserting the
      shape** into the first paragraph—all with a handful of clean Ja'
    question: What if I need a different shape, like an ellipse?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word Automation
title: Salvar documento Word – Adicionar forma retangular e sombra em Java
url: /pt/java/images-shapes/save-word-document-add-rectangle-shape-shadow-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvar Documento Word – Adicionar Forma Retangular & Sombra em Java

Já se perguntou como **salvar um documento Word** depois de personalizar seu layout? Você não está sozinho—a maioria dos desenvolvedores encontra esse obstáculo quando precisam enriquecer programaticamente um arquivo DOCX. A boa notícia é que, com Aspose.Words for Java, você pode **salvar um documento Word**, inserir uma forma retangular exatamente onde quiser e ainda dar a essa forma uma sombra sutil.

Neste tutorial percorreremos todo o processo: carregar um arquivo existente, **adicionar uma forma retangular**, configurar sua **sombra**, inserir a forma no primeiro parágrafo e, finalmente, **salvar o documento Word**. Ao final, você terá um programa Java executável que produz um arquivo `shadow.docx` polido—sem necessidade de ajustes manuais.

> **O que você precisará**  
> * Java 17 (ou qualquer JDK recente)  
> * Biblioteca Aspose.Words for Java (Maven/Gradle ou o JAR)  
> * Um arquivo DOCX de entrada (`input.docx`) em uma pasta conhecida  

Se você já tem esses requisitos, vamos começar.

---

## Salvar Documento Word – Exemplo Java Completo

Abaixo está o código-fonte completo, pronto‑para‑executar. Copie para sua IDE, ajuste os caminhos e pressione **Run**.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class ShadowShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the existing document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create a rectangle shape (the core of add rectangle shape step)
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);
        rectangle.setHeight(50.0);

        // 3️⃣ Apply shadow to shape – how to add shadow in Aspose.Words
        rectangle.getShadow().setVisible(true);
        rectangle.getShadow().setColor(java.awt.Color.BLACK);
        rectangle.getShadow().setBlurRadius(5.0);
        rectangle.getShadow().setOffsetX(4.0);
        rectangle.getShadow().setOffsetY(4.0);
        rectangle.getShadow().setTransparency(0.3);

        // 4️⃣ Insert shape into the first paragraph – how to insert shape
        Paragraph firstPara = doc.getFirstSection().getBody().getParagraphs().get(0);
        firstPara.appendChild(rectangle);

        // 5️⃣ Save the modified document – the final save word document step
        doc.save("YOUR_DIRECTORY/shadow.docx");
        System.out.println("Document saved successfully as shadow.docx");
    }
}
```

**Resultado esperado:** Após executar o programa, abra `shadow.docx`. Você verá o conteúdo original mais um retângulo preto de 100 × 50 pt com uma sombra suave logo no início do primeiro parágrafo.

---

## Adicionar Forma Retangular a um Documento Word

Por que usar uma forma retangular? Pense nela como um ponto de ancoragem visual—perfeito para chamadas, marcadores de posição ou gráficos simples. No Aspose.Words, a classe `Shape` abstrai todos os objetos de desenho, e `ShapeType.RECTANGLE` fornece uma caixa limpa sem complicações extras.

**Pontos‑chave ao adicionar uma forma retangular**

- **As unidades são pontos** (1 pt = 1/72 in). Ajuste `setWidth`/`setHeight` para se adequar ao seu layout.  
- A forma vive dentro da árvore de nós do documento, portanto pode ser inserida onde um `Paragraph` ou `Run` for permitido.  
- Você pode estilizar o retângulo (preenchimento, cor da linha, etc.) antes de aplicar a sombra.

> **Dica de especialista:** Se precisar de preenchimento transparente, chame `rectangle.getFill().setTransparent(true);`.

---

## Aplicar Sombra à Forma

Sombras dão profundidade. O objeto `Shadow` associado a um `Shape` expõe propriedades que correspondem diretamente às opções da interface do Word.

| Propriedade | O que faz | Valor típico |
|-------------|-----------|--------------|
| `setVisible(true)` | Ativa a sombra | `true` |
| `setColor(Color.BLACK)` | Cor da sombra | `Color.BLACK` |
| `setBlurRadius(5.0)` | Suavidade das bordas | `5.0` |
| `setOffsetX(4.0)` / `setOffsetY(4.0)` | Deslocamento horizontal/vertical | `4.0` cada |
| `setTransparency(0.3)` | Opacidade (0 = opaco, 1 = invisível) | `0.3` |

Quando você se pergunta **como aplicar sombra a uma forma**, a resposta é simplesmente ajustar essas seis propriedades. Experimente—offsets maiores criam a sensação de “elevação”, enquanto um raio de desfoque maior gera um aspecto mais difuso.

> **Erro comum:** Esquecer `setVisible(true)` deixa a forma sem sombra, mesmo que as demais propriedades estejam configuradas.

---

## Como Inserir a Forma em um Parágrafo

Inserir uma forma não é mágica; é apenas manipulação de nós. O método `appendChild` coloca a forma ao final dos nós filhos do parágrafo. Se precisar da forma antes do texto, use `insertBefore` em vez disso.

```java
Paragraph para = doc.getFirstSection().getBody().getParagraphs().get(0);
para.insertBefore(rectangle, para.getFirstChild());
```

Essa pequena mudança responde **como inserir forma** exatamente onde você precisa—antes de quaisquer runs existentes, após um título ou até dentro de uma célula de tabela (basta obter o nó `Cell` apropriado primeiro).

---

## Executando o Código e Verificando a Saída

1. **Compilar** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`  
2. **Executar** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`  
3. **Abrir** `shadow.docx` no Microsoft Word ou LibreOffice. Você deverá ver o retângulo com uma sombra preta suave ancorado no início do primeiro parágrafo.

Se a forma não aparecer, verifique:

- O caminho do arquivo de entrada está correto.  
- Você está usando uma versão recente do Aspose.Words (a API mudou levemente antes da 20.12).  
- O documento realmente possui ao menos um parágrafo (caso contrário `getParagraphs().get(0)` lança `IndexOutOfBoundsException`).

---

## Perguntas Frequentes (FAQ)

**P: Posso adicionar a forma a uma página específica?**  
R: Sim. Recupere a `Section` ou `PageSetup` alvo e insira a forma em um parágrafo localizado naquela página.

**P: Isso funciona com arquivos .doc?**  
R: Absolutamente. O Aspose.Words abstrai o formato, de modo que o mesmo código **salva um documento Word** seja ele `.doc` ou `.docx`.

**P: E se eu precisar de uma forma diferente, como uma elipse?**  
R: Substitua `ShapeType.RECTANGLE` por `ShapeType.ELLIPSE`. Todas as propriedades de sombra permanecem as mesmas.

---

## Conclusão

Agora você sabe como **salvar um documento Word** enquanto **adiciona uma forma retangular**, **aplica uma sombra** e **insere a forma** no primeiro parágrafo—tudo com algumas linhas limpas de Java. Esse padrão escala: troque o tipo de forma, ajuste as configurações de sombra ou posicione a forma em tabelas e cabeçalhos. As possibilidades são tão amplas quanto suas necessidades de automação de documentos.

Pronto para o próximo desafio? Experimente sobrepor múltiplas formas, adicionar texto dentro do retângulo ou gerar um relatório completo com gráficos e marcas d'água. Cada uma dessas tarefas se baseia nos mesmos fundamentos abordados aqui—então você já está um passo à frente.

Feliz codificação, e que sua automação Word esteja livre de bugs e sombras!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Criar Documento Word Java – Adicionar Forma Retangular com Efeito de Sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Como salvar documento como PDF com Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Como salvar Word como PCL com Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pcl-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}