---
title: 글꼴 대체 활성화 비활성화
linktitle: 글꼴 대체 활성화 비활성화
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서에서 글꼴 대체를 활성화 또는 비활성화하는 방법을 알아보세요. 모든 플랫폼에서 문서가 일관되게 보이도록 하세요.
weight: 10
url: /ko/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 글꼴 대체 활성화 비활성화

## 소개

Word 문서에서 꼼꼼히 선택한 글꼴이 다른 컴퓨터에서 볼 때 바뀌는 상황을 겪어본 적이 있나요? 짜증나죠? 이는 글꼴 대체, 즉 시스템에서 누락된 글꼴을 사용 가능한 글꼴로 대체하는 프로세스로 인해 발생합니다. 하지만 걱정하지 마세요! Aspose.Words for .NET을 사용하면 글꼴 대체를 쉽게 관리하고 제어할 수 있습니다. 이 튜토리얼에서는 Word 문서에서 글꼴 대체를 활성화하거나 비활성화하는 단계를 안내하여 문서가 항상 원하는 대로 보이도록 합니다.

## 필수 조건

다음 단계로 넘어가기 전에 필요한 모든 것이 있는지 확인해 보겠습니다.

-  .NET용 Aspose.Words: 최신 버전 다운로드[여기](https://releases.aspose.com/words/net/).
- Visual Studio: .NET을 지원하는 모든 버전.
- C#에 대한 기본 지식: 이는 코딩 예제를 따라가는 데 도움이 됩니다.

## 네임스페이스 가져오기

시작하려면 프로젝트에 필요한 네임스페이스를 가져왔는지 확인하세요. C# 파일 맨 위에 다음을 추가하세요.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

이제 이 과정을 간단하고 관리하기 쉬운 단계로 나누어 보겠습니다.

## 1단계: 프로젝트 설정

먼저 Visual Studio에서 새 프로젝트를 설정하고 Aspose.Words for .NET 라이브러리에 대한 참조를 추가합니다. 아직 다운로드하지 않았다면 다음에서 다운로드합니다.[Aspose 웹사이트](https://releases.aspose.com/words/net/).

## 2단계: 문서 로드

다음으로, 작업하려는 문서를 로드합니다. 방법은 다음과 같습니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

 바꾸다`"YOUR DOCUMENT DIRECTORY"` 문서 디렉토리의 실제 경로와 함께. 이 코드는 문서를 메모리에 로드하여 조작할 수 있습니다.

## 3단계: 글꼴 설정 구성

 이제 만들어 보겠습니다.`FontSettings` 글꼴 대체 설정을 관리하는 개체:

```csharp
FontSettings fontSettings = new FontSettings();
```

## 4단계: 기본 글꼴 대체 설정

기본 글꼴 대체를 원하는 글꼴로 설정합니다. 원래 글꼴을 사용할 수 없는 경우 이 글꼴이 사용됩니다.

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

이 예에서는 기본 글꼴로 Arial을 사용하고 있습니다.

## 5단계: 글꼴 정보 대체 비활성화

시스템이 누락된 글꼴을 사용 가능한 글꼴로 대체하지 않도록 글꼴 정보 대체를 비활성화하려면 다음 코드를 사용하세요.

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## 6단계: 문서에 글꼴 설정 적용

이제 다음 설정을 문서에 적용하세요.

```csharp
doc.FontSettings = fontSettings;
```

## 7단계: 문서 저장

마지막으로 수정된 문서를 저장합니다. 원하는 형식으로 저장할 수 있습니다. 이 튜토리얼에서는 PDF로 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## 결론

이제 다 됐어요! 다음 단계를 따르면 Aspose.Words for .NET을 사용하여 Word 문서에서 글꼴 대체를 쉽게 제어할 수 있습니다. 이렇게 하면 어디에서 보든 문서가 의도한 모양과 느낌을 유지합니다.

## 자주 묻는 질문

### Arial 이외의 다른 글꼴을 대체해서 사용할 수 있나요?

 물론입니다! 시스템에서 사용 가능한 모든 글꼴을 지정할 수 있습니다. 글꼴 이름을 변경하면 됩니다.`DefaultFontName` 재산.

### 지정된 기본 글꼴을 사용할 수 없는 경우 어떻게 되나요?

기본 글꼴을 사용할 수 없는 경우 Aspose.Words는 시스템 대체 메커니즘을 사용하여 적절한 대체 글꼴을 찾습니다.

### 글꼴 대체를 비활성화한 후 다시 활성화할 수 있나요?

 네, 전환할 수 있습니다.`Enabled` 의 속성`FontInfoSubstitution` 뒤로 돌아가기`true` 글꼴 대체를 다시 활성화하려면 다음을 수행합니다.

### 어떤 글꼴이 대체되는지 확인할 방법이 있나요?

네, Aspose.Words는 글꼴 대체를 기록하고 추적하는 방법을 제공하므로 어떤 글꼴이 대체되는지 확인할 수 있습니다.

### DOCX 외의 다른 문서 형식에도 이 방법을 사용할 수 있나요?

물론입니다! Aspose.Words는 다양한 형식을 지원하며, 이러한 글꼴 설정을 지원되는 모든 형식에 적용할 수 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
