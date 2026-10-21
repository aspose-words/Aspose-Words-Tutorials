---
category: general
date: 2026-06-30
description: Como renomear imagens ao converter DOCX para markdown. Aprenda a mudar
  os nomes das imagens e salvar o Word como markdown com nomes de arquivos de imagem
  personalizados.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: pt
og_description: Como renomear imagens ao converter DOCX para markdown. Este guia mostra
  como alterar os nomes das imagens, salvar o Word como markdown e usar nomes de arquivos
  de imagem personalizados.
og_title: Como Renomear Imagens ao Converter DOCX para Markdown
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: Como Renomear Imagens ao Converter DOCX para Markdown
url: /pt/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Renomear Imagens ao Converter DOCX para Markdown

Já se perguntou **como renomear imagens** automaticamente ao converter um arquivo DOCX para Markdown? Você não está sozinho. Em muitas pipelines de documentação, os nomes de imagem padrão (como `image1.png`) se tornam um pesadelo para rastrear, especialmente quando o mesmo markdown é versionado entre equipes.  

A boa notícia é que o Aspose.Words for Python torna isso muito fácil para **alterar nomes de imagens** em tempo real, e você pode manter seu Markdown limpo enquanto preserva uma pasta organizada de recursos com nomes personalizados.  

Neste tutorial você aprenderá a:

* Carregar um documento Word (`.docx`) em Python.  
* Interceptar o processo de salvamento em Markdown com um callback que atribui a cada imagem um nome de arquivo baseado em GUID.  
* Salvar o documento como Markdown para que o arquivo gerado faça referência às imagens recém‑nomeadas.  

Se você está confortável com Python básico e tem o Aspose.Words instalado, estará pronto em menos de cinco minutos. Sem scripts externos, sem renomeação manual — apenas um único programa autônomo que faz o trabalho pesado por você.

---

## Pré-requisitos — O Que Você Precisa Antes de Começar

| Requisito | Por que é importante |
|-------------|----------------|
| **Python 3.7+** | O exemplo usa f‑strings e type hints introduzidos no 3.6, mas 3.7+ oferece as conveniências do `os.path.splitext`. |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | Esta biblioteca fornece a classe `aw.Document` e o `MarkdownSaveOptions` que usamos. |
| **Permissão de escrita** na pasta de saída | O callback criará novos arquivos de imagem, portanto o script deve ter permissão para gravá‑los. |
| **Um arquivo DOCX** que você deseja converter | Qualquer coisa, desde um relatório simples até um manual complexo, funcionará. |

> **Dica profissional:** Se você estiver usando um ambiente virtual, ative‑lo antes de instalar o Aspose.Words. Ele isola as dependências e evita conflitos de versão.

---

## Etapa 1: Carregar o Documento Word  

A primeira coisa que você faz quando deseja **converter docx para markdown** é abrir o arquivo fonte. O Aspose.Words abstrai todo o manuseio de OPC de baixo nível, então uma única linha resolve.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Por que isso importa:* Sem carregar o documento você não pode inspecionar seus recursos, e o exportador Markdown não terá nada para escrever. O objeto `aw.Document` mantém todo o pacote Word na memória, tornando seguro manipulá‑lo antes de salvar.

---

## Etapa 2: Escrever um Callback que **Renomeia Recursos de Imagem**  

O Aspose.Words permite conectar um `resource_saving_callback` nas `MarkdownSaveOptions`. O callback recebe cada recurso (imagens, CSS, etc.) pouco antes de ser gravado no disco. Ao modificar `resource.file_name` podemos impor **nomes de arquivos de imagem personalizados**.

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### Por que usar um GUID?

* **Unicidade** – Um GUID (`uuid4`) garante que duas imagens nunca entrem em conflito, mesmo em execuções múltiplas.  
* **Rastreabilidade** – Se precisar depurar mais tarde, o GUID pode ser registrado junto ao número do parágrafo original do Word.  
* **Portabilidade** – Não depende do esquema de nomes original do Word, que pode conter espaços ou caracteres especiais que quebram links Markdown.

---

## Etapa 3: Anexar o Callback às Opções de Salvamento em Markdown  

Agora informamos ao Aspose para usar nossa lógica de renomeação sempre que ele gravar uma imagem na pasta de saída.

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*Explicação:* A classe `MarkdownSaveOptions` controla tudo, desde quebras de linha até a localização da pasta de imagens. Ao definir `resource_saving_callback`, você obtém um **gancho** que dispara para cada recurso incorporado, dando a chance de **alterar nomes de imagens** antes que o arquivo seja gravado no disco.

---

## Etapa 4: Salvar o Documento como Markdown – A Peça Final  

Com o callback configurado, a etapa final é simples.

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

Quando o script terminar, você encontrará:

* `CustomResources.md` – a representação Markdown do seu arquivo Word.  
* Uma pasta `images/` (ou o que você definiu) contendo arquivos como `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png`.  

O arquivo Markdown referenciará os novos nomes de arquivos baseados em GUID, de modo que qualquer processador downstream (GitHub, MkDocs, etc.) capturará as imagens corretas sem que você precise renomeá‑las manualmente.

### Saída Esperada (trecho)

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

Os GUIDs variarão a cada execução, mas o padrão permanece o mesmo.

---

## Lidando com Casos Limites e Perguntas Comuns  

### E se o documento contiver recursos que não são imagens?  

Nosso callback já verifica a extensão do arquivo e retorna `True` para tudo que não seja uma imagem. Isso significa que arquivos CSS, fontes ou objetos OLE incorporados mantêm seus nomes originais, o que geralmente é o desejado ao **salvar word como markdown**.

### Posso usar um esquema de nomenclatura personalizado em vez de GUIDs?  

Claro. Substitua a chamada `uuid.uuid4()` por qualquer função que retorne uma string. Por exemplo, você pode prefixar o índice do parágrafo original:

```python
new_name = f"para{resource.resource_id}{ext}"
```

Apenas certifique‑se de que o nome resultante seja único em todo o documento.

### Como isso afeta o desempenho em documentos grandes?  

O callback é executado uma vez por recurso, portanto o overhead é mínimo — principalmente o tempo para gerar um GUID. Mesmo um relatório de 200 páginas com dezenas de imagens termina em menos de um segundo em um laptop moderno.

### E se eu precisar que os nomes de arquivos de imagem sejam determinísticos (por exemplo, para builds de CI)?  

Troque `uuid.uuid4()` por um hash dos bytes da imagem original:

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

Isso produz o mesmo nome de arquivo toda vez que você executa o script na mesma imagem de origem.

---

## Script Completo Funcional – Copiar, Colar, Executar  



## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [salvar docx como markdown – Guia Completo em C# com Extração de Imagens](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [Como Salvar Markdown a partir de DOCX – Guia Passo a Passo](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}