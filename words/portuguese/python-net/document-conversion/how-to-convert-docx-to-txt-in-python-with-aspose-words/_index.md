---
category: general
date: 2026-09-27
description: Converta docx para txt em Python usando Aspose.Words. Aprenda a carregar
  um documento Word, definir a codificação UTF‑8 e exportar o documento Word como
  txt em poucas linhas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- convert docx to txt
- convert word to plain text
- save word as plain text
- export word document txt
- load word document python
language: pt
lastmod: 2026-09-27
og_description: Converta docx para txt em Python com Aspose.Words. Este tutorial mostra
  como carregar um documento Word, configurar a codificação e salvar o Word como texto
  simples.
og_image_alt: Screenshot of Python code that converts a DOCX file to a TXT file
og_title: Converter docx para txt em Python – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Convert docx to txt in Python using Aspose.Words. Learn to load a Word
    document, set UTF‑8 encoding, and export Word document txt in a few lines.
  headline: How to convert docx to txt in Python with Aspose.Words
  type: TechArticle
tags:
- Python
- Aspose.Words
- Document conversion
title: Como converter docx para txt em Python com Aspose.Words
url: /pt/python/document-conversion/how-to-convert-docx-to-txt-in-python-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como converter docx para txt em Python com Aspose.Words

Se você precisa **converter docx para txt** rapidamente, este guia mostra uma solução completa em Python. Você aprenderá como **carregar documento Word python**, configurar a codificação UTF‑8 e **exportar documento Word txt** com apenas algumas linhas de código.

O tutorial cobre tudo o que você precisa para executar a conversão em qualquer plataforma que suporte Python 3. Ao final do artigo, você será capaz de **save word as plain text** de forma confiável, mesmo quando o documento de origem contém caracteres especiais ou símbolos não‑ASCII.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Python 3.8 ou mais recente instalado.
* Uma licença ativa do Aspose.Words for Python (a avaliação gratuita funciona para avaliação).
* O pacote `aspose-words` instalado via `pip install aspose-words`.
* Um arquivo DOCX que você deseja converter (o exemplo usa `input.docx`).

> **Dica profissional:** Mantenha seu arquivo de licença (`Aspose.Words.lic`) na mesma pasta que seu script ou defina o caminho `Aspose.Words.License` explicitamente para evitar marcas d'água do modo de avaliação.

## Instalar Aspose.Words

Execute o comando a seguir no seu terminal ou prompt de comando:

```bash
pip install aspose-words
```

O pacote inclui o namespace `aw` usado em todos os exemplos de código.

## Passo 1 – Carregar o documento Word (converter docx para txt)

A primeira operação é ler o arquivo DOCX em um objeto `aw.Document`. Esta etapa corresponde ao requisito **load word document python**.

```python
import aspose.words as aw

# Load the source DOCX file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Por que isso importa*: Carregar o documento cria uma representação em memória que o Aspose.Words pode manipular, independentemente do formato original do arquivo.

## Passo 2 – Configurar opções de salvamento TXT (converter word para texto simples)

O Aspose.Words fornece `TxtSaveOptions` para controlar como a saída de texto simples é gerada. Definir a propriedade `encoding` como `"utf-8"` garante que todos os caracteres Unicode sejam preservados.

```python
# Create TXT save options and set UTF‑8 encoding
txt_options = aw.saving.TxtSaveOptions()
txt_options.encoding = "utf-8"
```

*Por que isso importa*: Sem uma codificação explícita, a página de código padrão do sistema pode substituir caracteres não‑ASCII por pontos de interrogação. UTF‑8 é a escolha mais segura para documentos multilíngues.

## Passo 3 – Salvar o documento como texto simples (save word as plain text)

Agora escreva o documento em um arquivo `.txt` usando as opções definidas acima.

```python
# Export the document to a plain‑text file
output_path = "YOUR_DIRECTORY/out.txt"
doc.save(output_path, txt_options)
print(f"Document exported successfully to {output_path}")
```

O arquivo resultante `out.txt` contém apenas o conteúdo textual de `input.docx`, com quebras de linha que correspondem à estrutura original dos parágrafos.

### Saída esperada

Se `input.docx` contém a frase:

> **“Hello, world! Привет мир!”**

o `out.txt` gerado exibirá:

```
Hello, world! Привет мир!
```

Todos os caracteres permanecem intactos porque a codificação UTF‑8 foi aplicada.

## Tratamento de casos de borda comuns

| Situação | Abordagem recomendada |
|-----------|----------------------|
| **Documento contém tabelas** | Aspose.Words achata as células da tabela em texto simples separado por tabulações. Se precisar de um delimitador personalizado, defina `txt_options.table_cell_separator` adequadamente. |
| **Arquivos grandes (≥ 100 MB)** | Transmita o documento para evitar alto consumo de memória: use `doc.save(output_stream, txt_options)` onde `output_stream` é um objeto de arquivo aberto em modo binário. |
| **Fontes ausentes** | Instale as fontes necessárias na máquina host ou incorpore‑as no DOCX antes da conversão. Fontes ausentes afetam apenas a renderização visual, não a extração de texto simples. |
| **DOCX protegido por senha** | Forneça a senha ao carregar: `doc = aw.Document("secure.docx", aw.LoadOptions(password="MySecret"))`. |

## Script completo – pronto para executar

Salve o código a seguir como `convert_docx_to_txt.py` e execute‑o com `python convert_docx_to_txt.py`.

```python
import aspose.words as aw
import os

def convert_docx_to_txt(input_path: str, output_path: str, encoding: str = "utf-8") -> None:
    """
    Converts a DOCX file to a TXT file using Aspose.Words.

    Args:
        input_path: Path to the source .docx file.
        output_path: Desired path for the resulting .txt file.
        encoding: Text encoding for the output file (default UTF‑8).
    """
    if not os.path.isfile(input_path):
        raise FileNotFoundError(f"Input file not found: {input_path}")

    # Load the Word document (load word document python)
    document = aw.Document(input_path)

    # Configure TXT save options (convert word to plain text)
    txt_options = aw.saving.TxtSaveOptions()
    txt_options.encoding = encoding

    # Save as plain‑text (save word as plain text)
    document.save(output_path, txt_options)
    print(f"Conversion complete: {output_path}")

if __name__ == "__main__":
    INPUT_FILE = "YOUR_DIRECTORY/input.docx"
    OUTPUT_FILE = "YOUR_DIRECTORY/out.txt"
    convert_docx_to_txt(INPUT_FILE, OUTPUT_FILE)
```

Executar o script imprime uma linha de confirmação e cria `out.txt` no diretório especificado.

## Verificar o resultado

Após a execução, abra `out.txt` em qualquer editor de texto (por exemplo, VS Code, Notepad++) e confirme que o conteúdo corresponde ao texto original do DOCX. Se você vir caracteres corrompidos, verifique novamente se `txt_options.encoding` está definido como `"utf-8"`.

## Próximos passos e tópicos relacionados

* **Convert docx to pdf** – use `aw.saving.PdfSaveOptions` para saída PDF de alta fidelidade.
* **Extract images from a Word document** – explore `aw.NodeType.SHAPE` e a classe `Shape`.
* **Batch conversion** – iterate over a folder of DOCX files and call `convert_docx_to_txt` for each entry.
* **Advanced encoding** – experiment with `txt_options.add_bidi_marks` ao lidar com scripts da direita para a esquerda.

Ao dominar as etapas acima, você pode **export word document txt** em qualquer pipeline de automação, seja construindo uma ferramenta de linha de comando, integrando com um serviço web ou processando documentos na nuvem.

---

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Converter docx para txt – Guia completo para salvar Word como texto simples](/words/english/net/programming-with-txtsaveoptions/convert-docx-to-txt-complete-guide-to-saving-word-as-plain-t/)
- [Aspose.Words – Salvar docx como txt e Exportar equações Word como LaTeX – Guia completo](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [Tutorial Word para PDF: Converter DOCX para PDF com Aspose.Words](/words/english/net/basic-conversions/word-to-pdf-tutorial-convert-docx-to-pdf-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}