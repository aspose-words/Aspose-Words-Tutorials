---
category: general
date: 2026-07-16
description: cmake build x64 tutorial은 CMake를 사용하여 Visual Studio 2022 솔루션을 생성하고 64비트
  호스트에서 VS 프로젝트를 빌드하는 방법을 보여줍니다. 소스 디렉터리 설정 단계가 포함됩니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: ko
lastmod: 2026-07-16
og_description: 'cmake 빌드 x64 설명: 소스 디렉터리 설정 방법, Visual Studio 2022 솔루션 생성 및 64비트
  호스트에서 VS 프로젝트를 컴파일하는 방법을 배웁니다.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: 'cmake 빌드 x64 – 단계별 가이드: VS 2022 솔루션 생성 및 빌드'
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
title: cmake x64 빌드 – VS 2022 프로젝트 생성 및 빌드 완전 가이드
url: /ko/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – VS 2022 프로젝트 생성 및 빌드 완전 가이드

Ever wondered **how to use CMake** to produce a 64‑bit Visual Studio solution without pulling your hair out? You're not alone. In this tutorial we’ll walk through a **cmake build x64** workflow that sets the source directory, runs the generator for Visual Studio 2022, and finally builds the VS project—all with a few clean Bash commands.

머리카락을 뽑지 않고 64비트 Visual Studio 솔루션을 만들기 위해 **how to use CMake**가 궁금하셨나요? 혼자가 아닙니다. 이 튜토리얼에서는 **cmake build x64** 워크플로우를 살펴보며, 소스 디렉터리를 설정하고 Visual Studio 2022용 생성기를 실행한 뒤, 최종적으로 VS 프로젝트를 빌드합니다—모두 몇 개의 깔끔한 Bash 명령으로 이루어집니다.

By the end of the guide you’ll have a reproducible script that you can drop into any repository, plus a solid grasp of the underlying concepts so you can tweak it for your own needs.

가이드가 끝날 때쯤이면, 어떤 저장소에도 넣을 수 있는 재현 가능한 스크립트를 얻게 되고, 기본 개념을 확실히 이해하여 필요에 맞게 조정할 수 있게 됩니다.

---

## 배울 내용

- **Set source directory**를 올바르게 설정하여 CMake가 `CMakeLists.txt`가 위치한 곳을 알 수 있도록 합니다.  
- **cmake generate visual studio** – 올바른 호스트 및 아키텍처 플래그와 함께 Visual Studio 2022 생성기를 호출합니다.  
- 생성된 솔루션에 대해 **cmake build x64**를 수행하고, 선택적으로 Release 구성으로 빌드합니다.  
- 64비트 머신에서 **build vs project**를 시도할 때 흔히 발생하는 함정을 이해합니다.  

사전 CMake 마법이 필요 없습니다; 터미널과 최신 Visual Studio 설치만 있으면 됩니다.

---

## 사전 요구 사항

| Requirement | Why it matters |
|-------------|----------------|
| CMake ≥ 3.20 | `-Thost=` 및 `-Ax64` 플래그를 사용한 64비트 빌드를 지원합니다. |
| Visual Studio 2022 (Community, Professional, or Enterprise) | 생성기 `Visual Studio 17 2022`가 이 버전을 가리킵니다. |
| A Bash‑compatible shell (Git Bash, WSL, PowerShell with `bash` alias) | 아래 스크립트는 명확성을 위해 Bash 구문을 사용합니다. |
| Source tree containing a valid `CMakeLists.txt` | CMake는 이를 없이 솔루션을 생성할 수 없습니다. |

If any of these are missing, install them first—CMake from <https://cmake.org/download/> and VS 2022 from the Microsoft installer.

이 중 하나라도 없으면 먼저 설치하세요—CMake는 <https://cmake.org/download/>에서, VS 2022는 Microsoft 설치 프로그램에서 설치합니다.

---

## Step 1 – 소스 및 빌드 디렉터리 설정 (`set source directory`)

Before you call CMake you need to tell it **where** to look for the project files. Hard‑coding paths makes the script brittle, so we’ll use environment variables that you can adjust per‑project.

CMake를 호출하기 전에 프로젝트 파일을 찾을 **위치**를 알려줘야 합니다. 경로를 하드코딩하면 스크립트가 깨지기 쉬우므로, 프로젝트별로 조정 가능한 환경 변수를 사용할 것입니다.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **왜 중요한가:**  
> CMake는 *source directory* (`SRC_DIR`)를 프로젝트의 루트로 간주합니다. *build directory* (`BUILD_DIR`)는 모든 중간 파일, 캐시 및 최종 `.sln` 파일이 위치하는 곳입니다. 이들을 분리하면 소스 트리가 오염되는 것을 방지하고, 정리(`rm -rf "$BUILD_DIR"`)가 간단해집니다.

`YOUR_DIRECTORY`를 절대 경로나 상대 경로로 교체할 수 있습니다; 해당 폴더에 `CMakeLists.txt`가 포함되어 있는지 확인하세요.

---

## Step 2 – Visual Studio 2022 솔루션 생성 (`cmake generate visual studio`)

Now we ask CMake to spit out a VS 2022 solution that targets **x64**. The key flags are:

이제 CMake에 **x64**를 타깃으로 하는 VS 2022 솔루션을 생성하도록 요청합니다. 주요 플래그는 다음과 같습니다:

- `-G "Visual Studio 17 2022"` – VS 2022 생성기를 선택합니다.  
- `-Thost=x64` – CMake에 *host* (IDE)가 64비트 프로세스로 실행된다고 알립니다.  
- `-Ax64` – 생성된 프로젝트가 x64 아키텍처용으로 빌드되도록 강제합니다.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **내부에서 무슨 일이 일어나나요?**  
> CMake는 `$SRC_DIR`에서 `CMakeLists.txt`를 읽고, 모든 `add_executable()` 및 `add_library()` 호출을 해석한 뒤, `$BUILD_DIR` 안에 `.sln` 파일과 여러 `.vcxproj` 파일을 생성합니다. 이제 이 프로젝트 파일들은 Visual Studio에서 열거나 명령줄에서 빌드할 준비가 되었습니다.

명령을 실행했을 때 `-- Configuring done` 및 `-- Generating done`으로 끝나는 긴 설정 메시지 목록이 표시되면, **cmake generate visual studio** 단계가 성공적으로 수행된 것입니다.

---

## Step 3 – 생성된 솔루션 빌드 (`cmake build x64`)

With the solution in place, the next logical step is to compile it. CMake can drive the build for you, delegating to MSBuild behind the scenes.

솔루션이 준비되면, 다음 논리적인 단계는 이를 컴파일하는 것입니다. CMake가 빌드를 담당하고, 내부적으로 MSBuild에 위임합니다.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **왜 `--config Release`를 사용하나요?**  
> Visual Studio 프로젝트는 여러 구성(Debug, Release, RelWithDebInfo 등)을 지원합니다. `Release`를 지정하면 바이너리가 프로덕션용으로 최적화되고, 생성된 `.exe` 또는 `.dll`이 빌드 트리 내 `Release/` 디렉터리에 위치하게 됩니다.

디버그 빌드를 원한다면 `Release`를 `Debug`로 바꾸세요. 명령은 동일하게 동작하며, 다른 구성에 대한 **how to use CMake**는 이 플래그를 교체하는 것뿐임을 보여줍니다.

---

## Step 4 – 빌드 검증 (`build vs project` sanity check)

A successful compilation should leave you with an executable or library. Let’s confirm it exists:

성공적인 컴파일은 실행 파일이나 라이브러리를 남깁니다. 존재하는지 확인해 봅시다:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **일반적인 함정:**  
> - `CMakeLists.txt`를 변경한 후에 생성기 단계를 실행하지 않으면 이 검사가 실패합니다.  
> - 32비트와 64비트 툴체인을 혼용하면 링커 오류가 발생할 수 있으니 항상 `-Ax64`를 일관되게 사용하세요.  
> - “MSB3073” 오류가 표시되면 보통 포스트‑빌드 단계(예: 리소스 복사)가 실패했음을 의미합니다—출력을 확인하여 단서를 찾으세요.

---

## Step 5 – 정리 및 재실행 (`cmake build x64` 반복)

During development you’ll often need to rebuild from scratch. The cleanest way is to delete the build folder and start over:

개발 중에는 종종 처음부터 다시 빌드해야 할 필요가 있습니다. 가장 깔끔한 방법은 빌드 폴더를 삭제하고 다시 시작하는 것입니다:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **팁:**  
> Visual Studio와 같은 다중 구성 생성기에서는 `-DCMAKE_BUILD_TYPE=Release`를 생성기 명령에 추가하는 것이 선택 사항이지만, Ninja와 같은 단일 구성 생성기로 전환할 때는 유용할 수 있습니다.

---

## Step 6 – 스크립트 확장 (고급 `cmake generate visual studio` 시나리오)

What if your project lives in a sub‑directory, or you need to pass custom definitions? CMake lets you do that with `-D` arguments:

프로젝트가 하위 디렉터리에 있거나 사용자 정의 정의를 전달해야 한다면 어떻게 할까요? CMake는 `-D` 인자를 사용해 이를 가능하게 합니다:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Now the generated VS solution will have the `MyFeature_ENABLED` macro defined, and the install target will place files under `/opt/myapp`. This demonstrates the flexibility of **how to use CMake** beyond the basic three‑step flow.

이제 생성된 VS 솔루션에는 `MyFeature_ENABLED` 매크로가 정의되고, 설치 대상은 파일을 `/opt/myapp` 아래에 배치합니다. 이는 기본 3단계 흐름을 넘어 **how to use CMake**의 유연성을 보여줍니다.

---

## 예상 출력

When you run the full script from start to finish, the terminal should display something like:

전체 스크립트를 처음부터 끝까지 실행하면 터미널에 다음과 같은 내용이 표시됩니다:

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

If anything goes wrong, CMake will emit error messages that point to the offending line in `CMakeLists.txt` or to missing SDK components—perfect for quick debugging.

문제가 발생하면 CMake는 `CMakeLists.txt`의 오류가 있는 라인이나 누락된 SDK 구성 요소를 가리키는 오류 메시지를 출력합니다—빠른 디버깅에 최적입니다.

---

## 결론

We’ve covered everything you need to perform a **cmake build x64**: setting the source directory, invoking the **cmake generate visual studio** step, compiling the resulting **build vs project**, and verifying the output. The script is compact, portable, and ready for integration into CI pipelines or local development workflows.

우리는 **cmake build x64**를 수행하는 데 필요한 모든 것을 다루었습니다: 소스 디렉터리 설정, **cmake generate visual studio** 단계 호출, 결과 **build vs project** 컴파일, 그리고 출력 검증. 이 스크립트는 간결하고 이식 가능하며 CI 파이프라인이나 로컬 개발 워크플로에 통합할 준비가 되어 있습니다.

Next, you might explore:

- `ctest`를 사용한 단위 테스트 실행 추가.  
- 더 빠른 증분 빌드를 위해 Ninja 생성기로 전환 (`-G Ninja`).  
- 방금 입력한 플래그를 저장하기 위해 CMake 프리셋(`CMakePresets.json`) 사용.

Feel free to experiment, break things, and then rebuild—after all, that’s the fastest way to learn how to use CMake effectively. Happy building!

자유롭게 실험하고, 문제를 일으키고, 다시 빌드하세요—결국 이것이 CMake를 효과적으로 사용하는 가장 빠른 방법입니다. 즐거운 빌딩 되세요!

## 다음에 배울 내용은?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 자체 프로젝트에서 대체 구현 방식을 탐색하도록 돕습니다.

- [테이블 빌드](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [스타일이 적용된 테이블 빌드](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [테두리가 있는 테이블 빌드](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}