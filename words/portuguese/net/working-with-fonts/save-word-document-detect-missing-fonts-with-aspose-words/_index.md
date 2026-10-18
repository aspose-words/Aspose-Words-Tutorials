---
category: general
date: 2026-03-22
description: Salvar documento Word e detectar fontes ausentes usando Aspose.Words.
  Aprenda como rastrear fontes ausentes e capturar erros de fontes em C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: pt
og_description: Salvar documento Word e detectar fontes ausentes em C#. Este guia
  mostra como rastrear fontes ausentes e capturar erros de fonte usando um callback
  de aviso.
og_title: Salvar documento Word – Detectar fontes ausentes com Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Salvar documento Word – Detectar fontes ausentes com Aspose.Words
url: /pt/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvar Documento Word – Detectar Fontes Ausentes com Aspose.Words

Já precisou **salvar documento word** mas não tinha certeza se algumas das fontes internas sobreviveriam à ida e volta? Isso acontece mais vezes do que você imagina, especialmente quando documentos circulam entre máquinas com bibliotecas de fontes diferentes. A boa notícia? Aspose.Words oferece uma forma integrada de **detectar fontes ausentes** enquanto você **salva documento word**, permitindo registrar, avisar ou até substituir as fontes antes que o arquivo chegue à tela do usuário.

Neste tutorial vamos percorrer um exemplo completo, pronto‑para‑executar, que não só salva um documento Word, mas também **rastreia fontes ausentes** e **captura erros de fontes** usando um manipulador de avisos personalizado. Ao final você saberá exatamente por que o callback de aviso é importante, como conectá‑lo e como é a saída do console quando ocorre uma substituição. Sem enrolação — apenas o código que você pode inserir em um projeto .NET agora mesmo.

> **Pré‑requisitos**  
> • .NET 6 (ou qualquer versão recente do .NET Framework) instalado  
> • Visual Studio 2022 ou sua IDE favorita  
> • Uma cópia licenciada do **Aspose.Words for .NET** (a versão de avaliação gratuita funciona para testes)  

Se você tem tudo isso, vamos começar.

---

## Salvar Documento Word e Detectar Fontes Ausentes

A ideia principal é simples: antes de chamar `Document.Save`, atribua um objeto que implemente `IWarningCallback` a `Document.WarningCallback`. Aspose.Words invocará esse objeto para cada aviso que encontrar, incluindo avisos de **substituição de fonte** que ocorrem quando o documento de origem referencia uma fonte que seu sistema não consegue encontrar.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**O que você verá:**  
Se `input.docx` referencia uma fonte que não está instalada, o console imprimirá algo como:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Essa linha informa exatamente qual fonte estava ausente e o que o Aspose.Words usou em seu lugar — perfeito para **capturar erros de fontes** antes de distribuir o arquivo.

## Rastrear Fontes Ausentes com um Callback de Aviso (Passo a Passo)

### 1️⃣ Instalar Aspose.Words

Abra o console NuGet do seu projeto e execute:

```bash
dotnet add package Aspose.Words
```

Isso baixa a versão estável mais recente (atualmente 24.10). Manter a biblioteca atualizada garante que você obtenha os recursos mais recentes de **detectar fontes ausentes** e correções de bugs.

### 2️⃣ Definir o Manipulador de Aviso

Por que precisamos de uma classe separada? Implementar `IWarningCallback` permite centralizar toda a lógica de avisos em um único lugar. Você também pode registrar em um arquivo, enviar telemetria ou lançar uma exceção se uma fonte ausente for um erro crítico para seu fluxo de trabalho.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Dica profissional:** Se precisar **rastrear fontes ausentes** em vários documentos, armazene as mensagens em um `List<string>` dentro do manipulador e exponha‑as posteriormente para relatórios.

### 3️⃣ Carregar Seu Documento Fonte

O construtor `Document` pode aceitar um caminho de arquivo, um stream ou até bytes brutos. Na maioria dos casos você apontará para um `.docx` que recebeu de um usuário ou de outro sistema.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Se o arquivo for grande, considere usar `LoadOptions` para habilitar carregamento preguiçoso, o que reduz a pressão de memória.

### 4️⃣ Anexar o Callback

Atribua a instância a `doc.WarningCallback`. A partir daí, todo aviso (incluindo substituições de fonte) passará pelo seu manipulador.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Salvar o Documento

Agora você pode chamar `Save` com segurança. O manipulador de avisos executa **sincronamente** durante a operação de salvamento, então você verá a saída imediatamente.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Se preferir salvar em um formato diferente (PDF, HTML, etc.), o mesmo mecanismo de aviso funciona — o Aspose.Words ainda reportará fontes ausentes antes da conversão.

## Capturar Erros de Fonte – Casos Limítrofes Comuns

Embora o fluxo básico cubra a maioria dos cenários, projetos do mundo real frequentemente encontram alguns obstáculos. Abaixo estão algumas variações que você pode encontrar e como lidar com elas.

### Fonte Ausente em Cabeçalho/Rodapé

Cabeçalhos e rodapés são nós separados, mas o sistema de avisos os trata da mesma forma que o texto do corpo. Nenhum código extra é necessário; o callback será disparado para essas fontes também. Apenas certifique-se de carregar o documento completo (o comportamento padrão faz isso).

### Múltiplas Substituições em Um Documento

Se um documento usar várias fontes desconhecidas, o manipulador será chamado uma vez por substituição. Para evitar inundar o console, você pode deduplicar as mensagens:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Transformar Avisos em Exceções

Às vezes, uma fonte ausente é um obstáculo intransponível. Lance uma exceção dentro do manipulador para abortar o salvamento:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Lembre‑se de envolver `doc.Save` em um bloco `try/catch` para tratar a exceção de forma elegante.

## Verificar o Resultado – O Que Esperar

Depois que o salvamento for concluído, abra `output.docx` no Microsoft Word (ou em qualquer visualizador compatível). Você deverá ver o mesmo layout visual do original, mas as fontes substituídas aparecerão como o fallback que você observou no console. Para confirmar, você pode:

1. Abrir **Arquivo → Opções → Avançado → Mostrar conteúdo do documento → Usar qualidade de rascunho** – isso força o Word a revelar quaisquer substituições de fonte ocultas.  
2. Usar a caixa de diálogo **Substituir Fontes** do Word (`Ctrl+Shift+F`) para ver quais fontes estão realmente incorporadas.

Se tudo estiver alinhado, você salvou com sucesso **documento word** enquanto **detectava fontes ausentes** e **capturava erros de fonte**. 🎉

## Exemplo Completo Funcional (Pronto para Copiar e Colar)

Abaixo está o programa completo que você pode inserir em um novo projeto de Aplicativo de Console. Basta substituir `YOUR_DIRECTORY` por um caminho de pasta real na sua máquina.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Saída esperada no console** (exemplo):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

Essa é a história completa — sem etapas ocultas, sem documentos externos que você precise procurar.

## Conclusão

Acabamos de mostrar como **salvar documento word** enquanto detecta ativamente **fontes ausentes**, **rastreia fontes ausentes** e **captura erros de fonte** usando o callback de aviso do Aspose.Words. Ao conectar uma pequena implementação de `IWarningCallback`, você obtém total visibilidade das substituições de fontes no momento do salvamento, permitindo registrar, substituir ou abortar conforme necessário.

Pronto para o próximo desafio? Tente estender o manipulador para gravar avisos em um log JSON estruturado, ou combine‑o com Aspose.PDF para converter o mesmo documento preservando as informações de fonte. Você também pode explorar a incorporação de fontes ausentes diretamente no arquivo de saída — o Aspose.Words suporta incorporação de fontes via `LoadOptions.FontSettings`.

Experimente, ajuste o código para se adequar ao seu pipeline e nos conte como funciona para você. Feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}