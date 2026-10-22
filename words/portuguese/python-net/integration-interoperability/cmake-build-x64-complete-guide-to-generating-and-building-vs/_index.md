---
category: general
date: 2026-07-16
description: O tutorial cmake build x64 mostra como usar o CMake para gerar uma solução
  do Visual Studio 2022 e compilar um projeto VS em um host de 64 bits. Inclui as
  etapas de definição do diretório de origem.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: pt
lastmod: 2026-07-16
og_description: 'Construção cmake x64 explicada: aprenda como definir o diretório
  de origem, gerar uma solução do Visual Studio 2022 e compilar um projeto VS em um
  host de 64 bits.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake build x64 – Guia passo a passo para gerar e compilar soluções VS 2022
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: cmake build x64 tutorial shows how to use CMake to generate a Visual
    Studio 2022 solution and build a VS project on a 64‑bit host. Includes set source
    directory steps.
  headline: cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects
  type: TechArticle
tags:
- cmake
- visual-studio
- x64
- build-automation
title: cmake build x64 – Guia Completo para Gerar e Compilar Projetos VS 2022
url: /pt/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Guia Completo para Gerar e Compilar Projetos VS 2022

Já se perguntou **como usar o CMake** para produzir uma solução Visual Studio de 64 bits sem perder a cabeça? Você não está sozinho. Neste tutorial vamos percorrer um fluxo **cmake build x64** que define o diretório de origem, executa o gerador para Visual Studio 2022 e, por fim, compila o projeto VS — tudo com alguns comandos Bash limpos.

Ao final do guia você terá um script reproduzível que pode ser inserido em qualquer repositório, além de uma compreensão sólida dos conceitos subjacentes para que possa ajustá‑lo às suas necessidades.

---

## O que você aprenderá

- **Definir o diretório de origem** corretamente para que o CMake saiba onde está seu `CMakeLists.txt`.  
- **cmake generate visual studio** – invocar o gerador Visual Studio 2022 com as flags corretas de host e arquitetura.  
- Executar um **cmake build x64** da solução gerada, opcionalmente selecionando a configuração Release.  
- Entender armadilhas comuns ao tentar **build vs project** em uma máquina de 64 bits.  

Nenhum conhecimento avançado de CMake é necessário; apenas um terminal e uma instalação recente do Visual Studio.

---

## Pré‑requisitos

| Requisito | Por que importa |
|-----------|-----------------|
| CMake ≥ 3.20 | Suporta as flags `-Thost=` e `-Ax64` usadas para builds de 64 bits. |
| Visual Studio 2022 (Community, Professional ou Enterprise) | O gerador `Visual Studio 17 2022` aponta para esta versão. |
| Um shell compatível com Bash (Git Bash, WSL, PowerShell com alias `bash`) | O script abaixo usa sintaxe Bash para clareza. |
| Árvore de código contendo um `CMakeLists.txt` válido | O CMake não pode gerar uma solução sem ele. |

Se algum desses itens estiver ausente, instale‑os primeiro — CMake em <https://cmake.org/download/> e VS 2022 pelo instalador da Microsoft.

---

## Etapa 1 – Definir os Diretórios de Origem e Build (`set source directory`)

Antes de chamar o CMake, você precisa dizer **onde** procurar os arquivos do projeto. Codificar caminhos fixos deixa o script frágil, então usaremos variáveis de ambiente que podem ser ajustadas por projeto.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Por que isso importa:**  
> O CMake trata o *diretório de origem* (`SRC_DIR`) como a raiz do projeto. O *diretório de build* (`BUILD_DIR`) é onde ficam todos os arquivos intermediários, caches e o `.sln` final. Mantê‑los separados evita poluir a árvore de código e torna a limpeza trivial (`rm -rf "$BUILD_DIR"`).

Substitua `YOUR_DIRECTORY` por qualquer caminho absoluto ou relativo; apenas certifique‑se de que a pasta contém um `CMakeLists.txt`.

---

## Etapa 2 – Gerar uma Solução Visual Studio 2022 (`cmake generate visual studio`)

Agora pedimos ao CMake que gere uma solução VS 2022 que tem como alvo **x64**. As flags principais são:

- `-G "Visual Studio 17 2022"` – seleciona o gerador VS 2022.  
- `-Thost=x64` – informa ao CMake que o *host* (a IDE) roda como processo de 64 bits.  
- `-Ax64` – força o projeto gerado a compilar para a arquitetura x64.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **O que acontece nos bastidores?**  
> O CMake lê o `CMakeLists.txt` de `$SRC_DIR`, resolve todas as chamadas `add_executable()` e `add_library()`, e então cria um arquivo `.sln` e um conjunto de arquivos `.vcxproj` dentro de `$BUILD_DIR`. Esses arquivos de projeto já podem ser abertos no Visual Studio ou compilados via linha de comando.

Se você executar o comando e vir uma longa lista de mensagens de configuração terminando com `-- Configuring done` e `-- Generating done`, você concluiu com sucesso a etapa **cmake generate visual studio**.

---

## Etapa 3 – Compilar a Solução Gerada (`cmake build x64`)

Com a solução pronta, o próximo passo lógico é compilá‑la. O CMake pode conduzir a compilação para você, delegando ao MSBuild nos bastidores.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Por que usar `--config Release`?**  
> Projetos Visual Studio suportam múltiplas configurações (Debug, Release, RelWithDebInfo, etc.). Especificar `Release` garante que os binários sejam otimizados para produção e que o `.exe` ou `.dll` resultante fique em `Release/` dentro da árvore de build.

Se preferir uma build Debug, substitua `Release` por `Debug`. O comando funciona da mesma forma, provando que **how to use CMake** para diferentes configurações é apenas uma questão de trocar essa flag.

---

## Etapa 4 – Verificar a Compilação (`build vs project` sanity check)

Uma compilação bem‑sucedida deve deixar você com um executável ou biblioteca. Vamos confirmar que ele existe:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Armadi­lhos comuns:**  
> - Esquecer de executar a etapa do gerador após mudar o `CMakeLists.txt` fará esse teste falhar.  
> - Misturar toolchains de 32 bits e 64 bits pode gerar erros de linker; mantenha sempre `-Ax64` consistente.  
> - Se aparecerem erros “MSB3073”, geralmente significa que uma etapa pós‑build (como copiar recursos) falhou — inspecione a saída para pistas.

---

## Etapa 5 – Limpar e Reexecutar (Iterando em um `cmake build x64`)

Durante o desenvolvimento você frequentemente precisará recompilar do zero. A forma mais limpa é excluir a pasta de build e começar novamente:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Dica:**  
> Adicionar `-DCMAKE_BUILD_TYPE=Release` ao comando do gerador é opcional para geradores multi‑config como o Visual Studio, mas pode ser útil quando você troca para um gerador de configuração única como o Ninja.

---

## Etapa 6 – Estendendo o Script (Cenários avançados `cmake generate visual studio`)

E se seu projeto estiver em um sub‑diretório, ou se precisar passar definições personalizadas? O CMake permite isso com argumentos `-D`:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Agora a solução VS gerada terá a macro `MyFeature_ENABLED` definida, e o alvo de instalação colocará arquivos em `/opt/myapp`. Isso demonstra a flexibilidade de **how to use CMake** além do fluxo básico de três passos.

---

## Saída Esperada

Ao executar o script completo do início ao fim, o terminal deve exibir algo como:

```
-- The C compiler identification is MSVC 19.35.31107.0
-- The CXX compiler identification is MSVC 19.35.31107.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
...
-- Configuring done
-- Generating done
-- Build files have been written to: /path/to/Examples/DocsExamples/build
...
[ 50%] Building CXX object CMakeFiles/MyApp.dir/main.cpp.obj
[100%] Linking CXX executable Release/MyApp.exe
✅ Build succeeded! Executable ready at /path/to/Examples/DocsExamples/build/Release/MyApp.exe
```

Se algo der errado, o CMake emitirá mensagens de erro apontando para a linha problemática no `CMakeLists.txt` ou para componentes SDK ausentes — perfeito para depuração rápida.

---

## Conclusão

Cobremos tudo que você precisa para realizar um **cmake build x64**: definir o diretório de origem, invocar a etapa **cmake generate visual studio**, compilar o **build vs project** resultante e verificar a saída. O script é compacto, portátil e pronto para integração em pipelines CI ou fluxos de desenvolvimento locais.

Próximos passos sugeridos:

- Adicionar execução de testes unitários com `ctest`.  
- Trocar para o gerador Ninja para builds incrementais mais rápidas (`-G Ninja`).  
- Usar presets do CMake (`CMakePresets.json`) para armazenar as flags que acabamos de digitar.

Sinta‑se à vontade para experimentar, quebrar coisas e então recompilar — afinal, essa é a maneira mais rápida de aprender **how to use CMake** efetivamente. Boa compilação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Build Table](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Build Table With Style](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Build Table With Borders](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}