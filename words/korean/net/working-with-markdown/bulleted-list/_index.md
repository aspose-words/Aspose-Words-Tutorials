---
"description": "이 단계별 가이드를 통해 Aspose.Words for .NET을 사용하여 Word 문서에서 글머리 기호 목록을 만들고 사용자 지정하는 방법을 알아보세요."
"linktitle": "글머리 기호 목록"
"second_title": "Aspose.Words 문서 처리 API"
"title": "글머리 기호 목록"
"url": "/ko/net/working-with-markdown/bulleted-list/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 글머리 기호 목록

## 소개

Aspose.Words for .NET의 세계로 뛰어들 준비가 되셨나요? 오늘은 Word 문서에서 글머리 기호 목록을 만드는 방법을 안내해 드리겠습니다. 아이디어를 정리하거나, 항목을 나열하거나, 문서에 구조를 추가할 때 글머리 기호 목록은 매우 유용합니다. 자, 시작해 볼까요!

## 필수 조건

코딩의 재미에 들어가기 전에, 필요한 모든 것이 있는지 확인해 보겠습니다.

1. Aspose.Words for .NET: Aspose.Words 라이브러리가 설치되어 있는지 확인하세요. 아직 설치되어 있지 않다면 [여기서 다운로드하세요](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio와 같은 AC# 개발 환경.
3. C# 기본 지식: C# 프로그래밍에 대한 기본적인 이해가 있으면 따라가는 데 도움이 됩니다.

## 네임스페이스 가져오기

먼저, 필요한 네임스페이스를 가져오겠습니다. 이는 코드가 원활하게 실행될 수 있도록 준비하는 것과 같습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

이제 이 과정을 쉽고 관리하기 쉬운 단계로 나누어 보겠습니다.

## 1단계: 새 문서 만들기

좋아요, 새 문서를 만들어 볼까요? 여기서 마법 같은 일이 일어날 거예요.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## 2단계: 글머리 기호 목록 형식 적용

다음으로, 글머리 기호 목록 서식을 적용해 보겠습니다. 이는 문서에 글머리 기호 목록을 시작함을 알려줍니다.

```csharp
builder.ListFormat.ApplyBulletDefault();
```

## 3단계: 글머리 기호 목록 사용자 지정

여기서는 글머리 기호 목록을 원하는 대로 설정해 보겠습니다. 이 예제에서는 글머리 기호로 대시(-)를 사용하겠습니다.

```csharp
builder.ListFormat.List.ListLevels[0].NumberFormat = "-";
```

## 4단계: 목록 항목 추가

이제 글머리 기호 목록에 몇 가지 항목을 추가해 보겠습니다. 여기서 창의력을 발휘하여 필요한 콘텐츠를 자유롭게 추가할 수 있습니다.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

## 5단계: 하위 항목 추가

좀 더 흥미롭게 만들기 위해 "항목 2" 아래에 몇 가지 하위 항목을 추가해 보겠습니다. 이렇게 하면 하위 항목을 구성하는 데 도움이 됩니다.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
builder.ListFormat.ListOutdent(); // 메인 목록 레벨로 돌아가기
```

## 결론

자, 이제 완성했습니다! Aspose.Words for .NET을 사용하여 Word 문서에 글머리 기호 목록을 만들었습니다. 간단한 작업이지만 문서 정리에 매우 유용합니다. 간단한 목록이든 복잡한 중첩 목록이든 Aspose.Words가 도와드립니다.

필요에 맞게 다양한 목록 스타일과 형식을 자유롭게 실험해 보세요. 즐거운 코딩 되세요!

## 자주 묻는 질문

### 목록에서 다른 글머리 기호를 사용할 수 있나요?
   예, 글머리 기호를 변경하여 사용자 정의할 수 있습니다. `NumberFormat` 재산.

### 들여쓰기 수준을 더 높이려면 어떻게 해야 하나요?
   사용하세요 `ListIndent` 더 많은 레벨을 추가하는 방법 `ListOutdent` 더 높은 수준으로 돌아가다.

### 글머리 기호 목록과 번호 목록을 섞어서 사용할 수 있나요?
   물론입니다! 다음을 사용하여 글머리 기호와 번호 서식을 전환할 수 있습니다. `ApplyNumberDefault` 그리고 `ApplyBulletDefault` 행동 양식.

### 목록 항목의 텍스트에 스타일을 지정할 수 있나요?
   예, 다음을 사용하여 목록 항목 내의 텍스트에 다양한 스타일, 글꼴 및 서식을 적용할 수 있습니다. `Font` 의 재산 `DocumentBuilder`.

### 여러 열로 구성된 글머리 기호 목록을 어떻게 만들 수 있나요?
   표 서식을 사용하면 각 셀에 별도의 글머리 기호 목록이 포함된 다중 열 목록을 만들 수 있습니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}