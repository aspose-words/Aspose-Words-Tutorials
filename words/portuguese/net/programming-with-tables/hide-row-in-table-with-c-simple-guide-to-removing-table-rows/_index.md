---
category: general
date: 2026-02-21
description: Ocultar linha em tabela usando C# e Aspose.Words. Aprenda como ocultar
  uma linha, como ocultar linha no Word e remover linha de tabela de forma rápida
  e segura.
draft: false
keywords:
- hide row in table
- how to hide row
- remove row from table
- hide row in word
- hide row c#
language: pt
og_description: Ocultar linha em tabela usando C# e Aspose.Words. Este guia mostra
  como ocultar linha, remover linha de tabela e ocultar linha em documentos Word.
og_title: Ocultar linha em tabela com C# – método rápido e confiável
tags:
- C#
- Aspose.Words
- Word Automation
title: Ocultar linha em tabela com C# – Guia simples para remover linhas de tabela
url: /pt/net/programming-with-tables/hide-row-in-table-with-c-simple-guide-to-removing-table-rows/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ocultar Linha em Tabela – Tutorial Completo em C#

Já precisou **hide row in table** ao gerar um documento Word programaticamente? Você não está sozinho—desenvolvedores perguntam constantemente *como ocultar linha* sem quebrar o layout. A boa notícia? Com algumas linhas de C# e a poderosa biblioteca Aspose.Words, você pode ocultar uma linha, removendo‑a efetivamente da saída final, e manter seu código limpo.

Neste guia vamos percorrer todo o processo: carregar um `.docx`, selecionar a linha exata, definir sua propriedade `Hidden` e salvar o resultado. Ao final você saberá exatamente como hide row in Word, como remover linha de uma tabela se preferir a exclusão, e terá um trecho pronto‑para‑usar que pode ser inserido em qualquer projeto .NET. Nenhuma referência externa necessária—apenas o código e explicações claras.

**O que você receberá**  
- Um passo‑a‑passo da API C#.  
- Código completo e executável (incluindo imports).  
- Dicas para casos de borda como linhas ocultas em células mescladas.  
- Dicas avançadas sobre quando *hide row* vs. *remove row from table*.

> **Pré‑requisito:** Visual Studio (ou qualquer IDE C#) e o pacote NuGet Aspose.Words for .NET (versão 23.9 ou superior). Se você é novo no Aspose.Words, a biblioteca é uma solução totalmente gerenciada—não requer instalação do Office.

---

## Ocultar Linha em Tabela – Implementação Passo a Passo

Abaixo está o exemplo completo e autocontido. Ele demonstra a tarefa **principal**—*hide row in table*—e também mostra como você poderia *remove row from table* caso decida excluir a linha.

![Exemplo de ocultar linha em tabela](hide-row-in-table.png "Captura de tela mostrando uma tabela Word com a terceira linha oculta")

### 1. Carregar o Documento Fonte  

Primeiro, precisamos trazer o arquivo Word para a memória. A classe `Document` representa o arquivo inteiro.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyDocs\input.docx");
```

*Por que isso importa:* Carregar o documento lhe dá acesso a seções, corpos e tabelas. Sem essa etapa você não pode manipular linhas.

### 2. Localizar a Tabela Desejada  

Para simplificar, pegamos a primeira tabela na primeira seção, mas você pode buscar por índice, nome ou até conteúdo.

```csharp
// Step 2: Get the first table in the document body
Table table = doc.FirstSection.Body.Tables[0];
```

> **Dica:** Se o seu documento possui várias tabelas, itere `doc.GetChildNodes(NodeType.Table, true)` e escolha a que precisar.

### 3. Escolher a Linha que Você Quer Ocultar  

Aqui selecionamos a terceira linha (índice base‑zero `2`). Você também pode usar `Rows.Count` para verificar se o índice existe.

```csharp
// Step 3: Choose the row you want to hide (third row, index 2)
Row rowToHide = table.Rows[2];
```

*Por que isso importa:* Selecionar a linha correta é o núcleo de **how to hide row**. Errar o índice ocultará o conteúdo errado.

### 4. Ocultar a Linha Selecionada  

Definir `Hidden = true` indica ao Aspose.Words que a linha deve ser omitida ao salvar o documento. A linha ainda existe no modelo de objetos, podendo ser revelada depois, se necessário.

```csharp
// Step 4: Hide the selected row – it will be omitted from the output
rowToHide.Hidden = true;
```

> **Pro dica:** Se você realmente quiser *remove row from table* em vez de ocultar, chame `table.Rows.Remove(rowToHide);`. Ocultar preserva metadados da linha, o que pode ser útil para formatação condicional.

### 5. Salvar o Documento Atualizado  

Por fim, grave as alterações no disco.

```csharp
// Step 5: Save the document with the hidden row applied
doc.Save(@"C:\MyDocs\output.docx");
```

Ao abrir `output.docx` no Word, a terceira linha ficará invisível—exatamente o que **hide row in word** significa na prática.

---

## Como Ocultar Linha – Variações Comuns & Casos de Borda

### Ocultar Várias Linhas  

Se precisar ocultar várias linhas, percorra a coleção:

```csharp
int[] rowsToHide = { 1, 3, 5 }; // zero‑based indexes
foreach (int i in rowsToHide)
{
    table.Rows[i].Hidden = true;
}
```

### Lidando com Células Mescladas  

Uma linha oculta que contém uma célula mesclada verticalmente pode gerar avisos de layout. A abordagem segura é dividir a mesclagem antes de ocultar:

```csharp
Cell mergedCell = rowToHide.Cells[0];
if (mergedCell.CellFormat.VerticalMerge != CellMerge.None)
{
    // Break the merge to avoid Word warnings
    mergedCell.CellFormat.VerticalMerge = CellMerge.None;
}
rowToHide.Hidden = true;
```

### Compatibilidade com Versões Antigas do Word  

Aspose.Words grava o atributo `w:hideMark`, que é compreendido pelo Word 2007+ e LibreOffice. Se você mira o Word 97‑2003 (`.doc`), a linha oculta ainda será omitida, mas tabelas complexas podem ser renderizadas de forma diferente. Prefira `.docx` para resultados previsíveis.

### Quando *Hide Row* vs. *Remove Row from Table*  

- **Hide Row** – Mantém a linha para possível desocultação, preserva a altura da linha para cálculos de quebra de página.  
- **Remove Row** – Reduz o tamanho do arquivo, exclui permanentemente os dados. Use `table.Rows.Remove(row)` se tiver certeza de que a linha não será mais necessária.

---

## Dicas Avançadas & Armadilhas

- **Pro dica:** Sempre verifique `table.Rows.Count` antes de acessar um índice para evitar `ArgumentOutOfRangeException`.  
- **Fique atento a:** Linhas ocultas ainda participam dos cálculos da tabela, como altura total. Se notar espaçamento inesperado, considere definir `row.Height = 0` após ocultar.  
- **Desempenho:** Ocultar linhas é barato; remover linhas dispara um relayout de toda a tabela, o que pode ser mais lento em documentos muito grandes.  
- **Teste:** Abra o arquivo salvo no Word e use **Reveal Formatting** (`Shift+F1`) para confirmar que a flag `Hidden` da linha está definida.

---

## Exemplo Completo Funcionando (Pronto para Copiar e Colar)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;

class HideRowInTableDemo
{
    static void Main()
    {
        // Load the source document (ensure the path exists)
        Document doc = new Document(@"C:\MyDocs\input.docx");

        // Get the first table – adapt if you have multiple tables
        Table table = doc.FirstSection.Body.Tables[0];

        // Verify we have at least three rows
        if (table.Rows.Count < 3)
        {
            Console.WriteLine("The table doesn't have a third row to hide.");
            return;
        }

        // Choose the third row (index 2) and hide it
        Row rowToHide = table.Rows[2];
        rowToHide.Hidden = true; // This hides the row in the output document

        // Save the modified document
        doc.Save(@"C:\MyDocs\output.docx");
        Console.WriteLine("Row hidden successfully. Check output.docx.");
    }
}
```

**Resultado esperado:** Abra `output.docx` e você verá a tabela sem a terceira linha, enquanto o restante do conteúdo permanece intacto. A linha oculta ainda faz parte do modelo do documento, podendo ser tornada visível novamente definindo `row.Hidden = false`.

---

## Conclusão

Acabamos de cobrir **how to hide row** em uma tabela Word usando C#. Carregando o documento, localizando a tabela, escolhendo a linha alvo, marcando‑a como oculta e salvando, você realiza uma operação limpa de *hide row in table* sem excluir dados. O mesmo padrão permite *remove row from table* caso precise de uma alteração permanente, e as dicas extras ajudam a evitar armadilhas comuns ao trabalhar com células mescladas ou versões antigas do Word.

Pronto para o próximo desafio? Experimente combinar esta técnica com lógica condicional—oculte linhas com base na entrada do usuário, ou gere relatórios dinâmicos onde certas seções desaparecem automaticamente. Você também pode explorar **hide row in word** para cabeçalhos, rodapés ou até seções inteiras.

Tem perguntas sobre *hide row c#* ou precisa de ajuda para integrar isso em um fluxo maior? Deixe um comentário abaixo ou confira nossos tutoriais relacionados sobre **manipulação de tabelas no Word com Aspose.Words**. Boa codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}