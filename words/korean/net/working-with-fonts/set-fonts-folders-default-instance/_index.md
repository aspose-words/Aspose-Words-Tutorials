---
"description": "이 단계별 튜토리얼을 통해 Aspose.Words for .NET에서 기본 인스턴스의 글꼴 폴더를 설정하는 방법을 알아보세요. Word 문서를 손쉽게 사용자 지정하세요."
"linktitle": "글꼴 폴더 기본 인스턴스 설정"
"second_title": "Aspose.Words 문서 처리 API"
"title": "글꼴 폴더 기본 인스턴스 설정"
"url": "/ko/net/working-with-fonts/set-fonts-folders-default-instance/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 글꼴 폴더 기본 인스턴스 설정

## 소개

안녕하세요, 동료 코더 여러분! .NET에서 Word 문서 작업을 하신다면 글꼴을 제대로 사용하는 것이 얼마나 중요한지 잘 알고 계실 겁니다. 오늘은 Aspose.Words for .NET을 사용하여 기본 인스턴스의 글꼴 폴더를 설정하는 방법을 자세히 알아보겠습니다. 원하는 모든 글꼴을 손쉽게 사용하고, 문서를 원하는 대로 꾸밀 수 있다고 상상해 보세요. 정말 멋지지 않나요? 시작해 볼까요!

## 필수 조건

자세한 내용을 살펴보기 전에 먼저 필요한 모든 것이 있는지 확인해 보겠습니다.
- Aspose.Words for .NET: 라이브러리가 설치되어 있는지 확인하세요. 설치되어 있지 않으면 [여기서 다운로드하세요](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio 또는 기타 .NET 호환 IDE.
- C#에 대한 기본 지식: C# 프로그래밍에 익숙해야 합니다.
- 글꼴 폴더: 사용자 정의 글꼴이 들어 있는 디렉토리입니다.

## 네임스페이스 가져오기

먼저 필요한 네임스페이스를 가져오겠습니다. 이렇게 하면 글꼴 폴더 설정에 필요한 클래스와 메서드에 쉽게 접근할 수 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

이 과정을 간단하고 이해하기 쉬운 단계로 나누어 보겠습니다.

## 1단계: 데이터 디렉터리 정의

모든 위대한 여정은 한 걸음부터 시작되고, 우리의 여정은 문서가 저장될 디렉터리를 정의하는 것에서 시작됩니다. Aspose.Words는 이 디렉터리에서 Word 문서를 찾습니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

여기서 교체하세요 `"YOUR DOCUMENT DIRECTORY"` 문서 디렉터리의 실제 경로를 입력합니다. 이 경로는 원본 문서가 위치하며 출력 결과가 저장되는 위치입니다.

## 2단계: 글꼴 폴더 설정

이제 Aspose.Words에서 사용자 지정 글꼴을 찾을 위치를 지정해 보겠습니다. 이 작업은 다음을 사용하여 글꼴 폴더를 설정하여 수행됩니다. `FontSettings.DefaultInstance.SetFontsFolder` 방법.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

이 줄에서는, `"C:\\MyFonts\\"` 사용자 지정 글꼴 폴더의 경로입니다. 두 번째 매개변수는 `true`, 이 폴더의 글꼴을 재귀적으로 스캔해야 함을 나타냅니다.

## 3단계: 문서 로드

글꼴 폴더가 설정되었으면 다음 단계는 Aspose.Words에 Word 문서를 로드하는 것입니다. 이 작업은 다음을 사용하여 수행됩니다. `Document` 수업.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

여기, `dataDir + "Rendering.docx"` Word 문서의 전체 경로를 나타냅니다. 문서가 지정된 디렉터리에 있는지 확인하세요.

## 4단계: 문서 저장

마지막 단계는 글꼴 폴더를 설정한 후 문서를 저장하는 것입니다. 이렇게 하면 사용자 지정 글꼴이 출력 결과에 올바르게 적용됩니다.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

이 줄은 사용자 지정 글꼴이 적용된 PDF로 문서를 저장합니다. 출력 파일은 원본 문서와 같은 디렉터리에 저장됩니다.

## 결론

자, 이제 완성되었습니다! Aspose.Words for .NET에서 기본 인스턴스의 글꼴 폴더를 설정하는 것은 간단한 단계로 나누어 보면 아주 쉽습니다. 이 가이드를 따라 하면 모든 사용자 지정 글꼴이 적용된 Word 문서가 원하는 대로 정확하게 표시되도록 할 수 있습니다. 지금 바로 사용해 보고 문서를 더욱 빛나게 만들어 보세요!

## 자주 묻는 질문

### 여러 개의 글꼴 폴더를 설정할 수 있나요?
예, 다음을 사용하여 여러 개의 글꼴 폴더를 설정할 수 있습니다. `SetFontsFolders` 폴더 경로 배열을 허용하는 메서드입니다.

### Aspose.Words는 문서 저장을 위해 어떤 파일 형식을 지원합니까?
Aspose.Words는 DOCX, PDF, HTML, EPUB 등 다양한 형식을 지원합니다.

### Aspose.Words에서 온라인 글꼴을 사용할 수 있나요?
아니요, Aspose.Words는 현재 로컬 글꼴 파일만 지원합니다.

### 사용자 지정 글꼴이 저장된 PDF에 포함되어 있는지 어떻게 확인할 수 있나요?
설정하여 `FontSettings` 글꼴을 올바르게 사용하고 사용 가능한지 확인하면 Aspose.Words가 해당 글꼴을 PDF 출력에 포함합니다.

### 지정된 폴더에서 글꼴을 찾을 수 없으면 어떻게 되나요?
지정된 글꼴을 찾을 수 없는 경우 Aspose.Words는 대체 글꼴을 사용합니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}