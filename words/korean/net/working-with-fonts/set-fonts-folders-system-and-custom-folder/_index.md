---
title: 글꼴 폴더 시스템 및 사용자 정의 폴더 설정
linktitle: 글꼴 폴더 시스템 및 사용자 정의 폴더 설정
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서에 시스템 및 사용자 정의 글꼴 폴더를 설정하는 방법을 알아보고, 다양한 환경에서 문서가 올바르게 표시되도록 하세요.
weight: 10
url: /ko/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 글꼴 폴더 시스템 및 사용자 정의 폴더 설정

## 소개

고유한 글꼴 스타일로 문서를 작성하다가 다른 컴퓨터에서는 글꼴이 제대로 표시되지 않는다는 것을 알게 되었다고 상상해 보세요. 답답하시죠? 여기서 글꼴 폴더 구성이 중요한 역할을 합니다. Aspose.Words for .NET을 사용하면 시스템 및 사용자 지정 글꼴 폴더를 정의하여 문서가 항상 의도한 대로 표시되도록 할 수 있습니다. 이를 달성하는 방법을 살펴보겠습니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

-  .NET 라이브러리용 Aspose.Words: 아직 다운로드하지 않았다면 지금 다운로드하세요.[여기](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio와 같은 IDE.
- C#에 대한 기본 지식: C#에 익숙하면 코드 예제를 따라가는 데 도움이 됩니다.

## 네임스페이스 가져오기

먼저 프로젝트에 필요한 네임스페이스를 가져옵니다.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

이제 이 과정을 간단한 단계로 나누어 보겠습니다.

## 1단계: 문서 로드

 시작하려면 Aspose.Words에 Word 문서를 로드합니다.`Document` 객체. 이 문서는 글꼴 폴더를 설정하려는 문서입니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## 2단계: 글꼴 설정 초기화

 새 인스턴스를 만듭니다.`FontSettings`이 개체를 사용하면 글꼴 소스를 관리할 수 있습니다.

```csharp
FontSettings fontSettings = new FontSettings();
```

## 3단계: 시스템 글꼴 소스 검색

기본 시스템 글꼴 소스를 검색합니다. Windows 컴퓨터에서는 일반적으로 "Windows\Fonts"가 포함됩니다.\" 디렉토리.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## 4단계: 사용자 정의 글꼴 폴더 추가

추가 글꼴을 포함하는 사용자 지정 폴더를 추가합니다. 이는 시스템 글꼴 디렉토리에 설치되지 않은 특정 글꼴이 있는 경우에 유용합니다.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## 5단계: 글꼴 소스 업데이트

 글꼴 소스 목록을 다시 배열로 변환하고 설정합니다.`FontSettings` 물체.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## 6단계: 문서에 글꼴 설정 적용

 마지막으로 구성된 것을 적용합니다.`FontSettings` 원하는 형식(예: PDF)으로 문서를 저장하세요.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## 결론

이제 다 됐습니다! 다음 단계를 따르면 Word 문서에서 시스템 글꼴이든 특정 디렉터리에 저장된 사용자 지정 글꼴이든 올바른 글꼴을 사용할 수 있습니다. 이 설정은 다양한 환경에서 문서 모양의 무결성을 유지하는 데 도움이 됩니다.

## 자주 묻는 질문

### 시스템 폴더와 사용자 정의 폴더 모두에 글꼴이 없으면 어떻게 되나요?

Aspose.Words는 누락된 글꼴을 기본 글꼴로 대체하여 문서를 읽기 쉬운 상태로 유지합니다.

### 사용자 정의 글꼴 폴더를 여러 개 추가할 수 있나요?

 예, 생성 프로세스를 반복하여 여러 개의 사용자 정의 글꼴 폴더를 추가할 수 있습니다.`FolderFontSource` 개체를 글꼴 소스 목록에 추가합니다.

### 사용자 정의 글꼴 폴더에 네트워크 경로를 사용할 수 있나요?

 네, 네트워크 경로를 지정할 수 있습니다.`FolderFontSource` 건설자.

### Aspose.Words는 문서를 저장할 때 어떤 파일 형식을 지원하나요?

Aspose.Words는 DOCX, PDF, HTML 등 다양한 형식을 지원합니다.

### 글꼴 대체 알림을 어떻게 처리하나요?

 다음을 사용하여 글꼴 대체 알림을 처리할 수 있습니다.`FontSettings` 수업의`FontSubstitutionWarning`이벤트.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
