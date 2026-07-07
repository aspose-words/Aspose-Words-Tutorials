---
category: general
date: 2026-07-06
description: CMake 프로젝트를 단계별로 빌드합니다. CMake 설정 방법, CMake 빌드 방법, 그리고 신뢰할 수 있는 테스트를 위한
  CTest 실행 방법을 배웁니다.
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: ko
og_description: 명확한 단계로 CMake 프로젝트를 빠르게 빌드하세요. 이 가이드는 CMake를 구성하는 방법, CMake를 빌드하는
  방법, 그리고 CTest를 실행하는 방법을 보여줍니다.
og_title: 'CMake 프로젝트 빌드: 구성, 빌드 및 테스트 가이드'
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Build CMake project step‑by‑step. Learn how to configure CMake, how
    to build CMake, and how to run CTest for reliable testing.
  headline: 'Build CMake Project: Configure, Build & Test'
  type: TechArticle
tags:
- cmake
- ctest
- build-system
title: 'CMake 프로젝트 빌드: 구성, 빌드 및 테스트'
url: /ko/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# CMake 프로젝트 빌드: 구성, 빌드 및 테스트

StackOverflow를 뒤져도 되는 **build CMake project** 방법이 궁금했나요? 당신만 그런 것이 아닙니다. 대부분의 개발자는 간단한 `CMakeLists.txt`에서 재현 가능한 빌드 파이프라인으로 이동하려 할 때 같은 문제에 부딪힙니다.  

이 튜토리얼에서는 전체 과정을 단계별로 살펴봅니다—*CMake 구성 방법*, *CMake 빌드 방법*, 그리고 *CTest 실행 방법*—그래서 어떤 머신에서도 실행할 수 있는 깔끔하고 반복 가능한 빌드를 얻을 수 있습니다. 마지막까지 진행하면 별도의 스크립트 없이도 자신의 저장소에 복사‑붙여넣기 할 수 있는 작동 예제를 얻게 됩니다.

## Prerequisites — 시작하기 전에 필요한 것

시작하기 전에 다음 항목을 확인하세요:

- 최신 CMake 버전 (3.20 이상) – 오래된 버전은 여기서 사용할 플래그를 지원하지 않을 수 있습니다.
- 플랫폼에서 지원하는 C++ 컴파일러 (gcc, clang, MSVC 등).
- `cmake`와 `ctest`에 접근 가능한 터미널 또는 명령 프롬프트.
- (선택) 예제 저장소를 클론하려면 Git이 필요합니다.

위 항목 중 하나라도 없으면 지금 바로 설치하세요. 그렇지 않으면 나중에 “command not found” 오류가 발생합니다.

## Step 1: Configure the CMake Project (Release configuration)

*CMake 구성 방법*을 시작할 때 가장 먼저 해야 할 일은 소스가 어디에 있고 빌드 산출물이 어디에 생성될지를 CMake에 알려주는 것입니다. `-S` 플래그는 소스 디렉터리를 지정하고, `-B`는 별도의 빌드 폴더를 생성하며, `-D CMAKE_BUILD_TYPE=Release`는 최적화된 빌드를 강제합니다.

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**왜 중요한가요:** 소스와 빌드 파일을 분리(`out‑of‑source` 빌드)하면 실수로 소스를 수정하는 일을 방지하고, 나중에 빌드 디렉터리를 쉽게 정리할 수 있습니다. `Release` 플래그는 컴파일러에게 최적화를 활성화하도록 지시하는데, 이는 최종 바이너리를 만들 때 일반적으로 원하는 설정입니다.

> **Pro tip:** 디버깅이 필요하면 `Release`를 `Debug`로 바꾸기만 하면 됩니다. 같은 명령이 작동하며 CMake가 나머지를 처리합니다.

## Step 2: Build the Configured Project

구성 단계에서 필요한 Makefile이나 Visual Studio 프로젝트 파일이 생성되었으니 이제 실제로 코드를 컴파일할 수 있습니다. `--build` 옵션은 기본 빌드 도구(`make`, `ninja`, `MSBuild` 등)를 추상화하므로 동일한 명령을 Linux, macOS, Windows에서 모두 사용할 수 있습니다.

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**내부에서 무슨 일이 일어나나요?** CMake는 이전 단계에서 만든 `CMakeCache.txt`를 읽고, 적절한 빌드 도구를 결정한 뒤 올바른 플래그와 함께 실행합니다. 이것이 *how to build CMake*의 핵심이며, `make`인지 `ninja`인지 기억할 필요 없이 CMake가 대신 처리해 줍니다.

멀티코어 머신에서 빌드 속도를 높이고 싶다면 다음과 같이 옵션을 추가하세요 (`Linux/macOS`에서는 `-- -j$(nproc)`, `Windows`에서는 `-- /m`):

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## Step 3: Run the Example Tests with Detailed Output

테스트는 실제 동작을 검증하는 단계입니다. CMake는 `ctest`라는 테스트 드라이버를 제공하며, `add_test()`로 `CMakeLists.txt`에 추가된 모든 테스트를 자동으로 발견하고 실행합니다. 상세 출력을 보려면 먼저 빌드 디렉터리로 이동하는 `-E chdir` 헬퍼를 사용합니다:

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**왜 `--verbose`를 사용하나요?** 각 테스트의 명령줄, 종료 코드, 그리고 테스트 자체가 출력하는 모든 내용을 보여줍니다. 이는 *how to run CTest*를 배우는 데 필수적이며, 실제로 어떤 일이 일어나고 있는지 정확히 확인할 수 있게 해 줍니다.

Typical output looks like this:

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

테스트가 실패하면 상세 로그에 실패한 명령과 오류 메시지가 포함되어 디버깅이 훨씬 빨라집니다.

## Step 4: Automate the Whole Workflow (Optional)

많은 프로젝트에서는 한 줄 명령으로 구성, 빌드, 테스트를 한 번에 실행하고 싶습니다. 간단한 Bash(또는 PowerShell) 스크립트로 이를 구현할 수 있습니다:

```bash
#!/usr/bin/env bash
SRC=YOUR_DIRECTORY/Examples/DocsExamples
BUILD=$SRC/build

# 1️⃣ Configure
cmake -S "$SRC" -B "$BUILD" -D CMAKE_BUILD_TYPE=Release

# 2️⃣ Build
cmake --build "$BUILD" -- -j$(nproc)

# 3️⃣ Test
cmake -E chdir "$BUILD" ctest --verbose
```

`run_all.sh`라는 파일로 저장하고 실행 권한을 부여하세요 (`chmod +x run_all.sh`). 이제 어떤 CI 시스템(GitHub Actions, GitLab CI, Azure Pipelines 등)에도 넣을 수 있는 재현 가능한 **cmake build and test** 파이프라인이 완성됩니다.

## Edge Cases & Common Pitfalls

| Situation | What to Watch For | Fix |
|-----------|-------------------|-----|
| **Missing compiler** | CMake aborts with “No CMAKE_CXX_COMPILER could be found.” | Install a compiler (`sudo apt install build-essential` on Ubuntu, `xcode-select --install` on macOS). |
| **Out‑of‑source folder already exists** | CMake may refuse to reconfigure if the folder contains stale files. | Delete the `build` directory (`rm -rf build`) or run `cmake --fresh` (CMake 3.24+). |
| **CTest cannot find tests** | `add_test()` was never called or the test executable failed to compile. | Verify that `add_test(NAME MyTest COMMAND MyTestExe)` appears in `CMakeLists.txt` and that the target builds. |
| **Parallel builds race on custom commands** | Some custom commands are not marked as `DEPENDS`, leading to nondeterministic failures. | Add proper `add_custom_command(... DEPENDS ...)` entries. |

이러한 미묘한 차이를 이해하면 불안정한 빌드와 견고한 CI 파이프라인 사이의 차이를 만들 수 있습니다.

## Visual Overview (Alt text includes primary keyword)

![CMake 프로젝트의 구성, 빌드 및 테스트 흐름을 보여주는 다이어그램](/images/cmake-workflow.png "Build CMake Project workflow diagram")

## Recap – What You’ve Learned

우리는 *how to build CMake project*라는 핵심 질문에서 시작했습니다. 이제 **CMake를 깨끗한 out‑of‑source 빌드**로 구성하고, **CMake를 universal `--build` 플래그**로 빌드하며, **CTest를 verbose 출력**으로 실행해 모든 것이 정상인지 확인하는 방법을 알게 되었습니다. 또한 세 단계를 하나로 묶은 스크립트를 확보했으니, 완전한 **cmake build and test** 워크플로우를 바로 사용할 수 있습니다.

## What’s Next?

- **커버리지 보고** – `gcov` 또는 `llvm-cov`를 통합하고 CTest가 결과를 게시하도록 합니다.
- **크로스‑컴파일** – 임베디드 디바이스용 빌드를 위해 `-DCMAKE_TOOLCHAIN_FILE`을 탐색합니다.
- **패키지 생성** – `cpack`을 사용해 바이너리를 배포용으로 번들링합니다.
- **CI 통합** – 스크립트를 GitHub Actions 워크플로우에 복사하고 모든 Pull Request에서 자동화가 실행되는 모습을 확인합니다.

빌드 타입을 바꾸거나 테스트를 추가하고, 예제 소스를 자신의 프로젝트로 교체해 보세요. 오늘 다룬 패턴은 작은 유틸리티든 대규모 멀티‑모듈 시스템이든 모든 CMake 기반 코드베이스에 적용할 수 있습니다.

Happy building, and may your CMake builds always be reproducible!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하여 밀접하게 관련된 주제를 다룹니다. 각 리소스는 완전한 동작 코드 예제와 단계별 설명을 제공해 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 도와줍니다.

- [How to Export LaTeX from Word – Step‑by‑Step Guide](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [How to Display Aspose.Words Version in Python and .NET&#58; A Step-by-Step Guide](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}