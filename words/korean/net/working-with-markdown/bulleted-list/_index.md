---
title: 글머리 기호 목록
linktitle: 글머리 기호 목록
second_title: Aspose.Words 문서 처리 API
description: 이 단계별 가이드를 통해 Aspose.Words for .NET을 사용하여 Word 문서에서 글머리 기호 목록을 만들고 사용자 지정하는 방법을 알아보세요.
weight: 10
url: /ko/net/working-with-markdown/bulleted-list/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 글머리 기호 목록

## 소개

Aspose.Words for .NET의 세계로 뛰어들 준비가 되셨나요? 오늘은 Word 문서에서 요점 목록을 만드는 방법을 알아보겠습니다. 아이디어를 정리하든, 항목을 나열하든, 문서에 약간의 구조를 추가하든, 요점 목록은 매우 편리합니다. 그럼 시작해 볼까요!

## 필수 조건

코딩의 재미에 들어가기 전에 먼저 필요한 모든 것이 있는지 확인해 보겠습니다.

1.  .NET용 Aspose.Words: Aspose.Words 라이브러리가 설치되어 있는지 확인하세요. 아직 설치되어 있지 않으면 다음을 수행할 수 있습니다.[여기서 다운로드하세요](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio와 같은 AC# 개발 환경.
3. 기본 C# 지식: C# 프로그래밍에 대한 기본적인 이해가 따라가는 데 도움이 됩니다.

## 네임스페이스 가져오기

우선, 필요한 네임스페이스를 임포트해 보겠습니다. 이것은 코드가 원활하게 실행될 수 있는 무대를 마련하는 것과 같습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

이제 이 과정을 쉽고 관리하기 쉬운 단계로 나누어 보겠습니다.

## 1단계: 새 문서 만들기

좋습니다. 새 문서를 만드는 것으로 시작해 봅시다. 여기서 모든 마법이 일어날 것입니다.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## 2단계: 글머리 기호 목록 형식 적용

다음으로, 글머리 기호 목록 형식을 적용합니다. 이는 문서에 글머리 기호 목록을 시작하려고 한다는 것을 알려줍니다.

```csharp
builder.ListFormat.ApplyBulletDefault();
```

## 3단계: 글머리 기호 목록 사용자 지정

여기서, 우리는 우리의 취향에 맞게 글머리 기호 목록을 사용자 정의할 것입니다. 이 예에서, 우리는 글머리 기호로 대시(-)를 사용할 것입니다.

```csharp
builder.ListFormat.List.ListLevels[0].NumberFormat = "-";
```

## 4단계: 목록 항목 추가

이제, 우리의 글머리 기호 목록에 몇 가지 항목을 추가해 보겠습니다. 여기서 창의력을 발휘하고 필요한 모든 콘텐츠를 추가할 수 있습니다.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

## 5단계: 하위 항목 추가

더 흥미로운 것을 만들기 위해 "항목 2" 아래에 몇 가지 하위 항목을 추가해 보겠습니다. 이것은 하위 포인트를 구성하는 데 도움이 됩니다.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
builder.ListFormat.ListOutdent(); // 메인 목록 레벨로 돌아가기
```

## 결론

이제 다 됐습니다! Aspose.Words for .NET을 사용하여 Word 문서에 글머리 기호 목록을 만들었습니다. 간단한 프로세스이지만 문서를 구성하는 데 매우 강력합니다. 간단한 목록을 만들든 복잡한 중첩 목록을 만들든 Aspose.Words가 처리해 드립니다.

다양한 목록 스타일과 형식을 실험해 보세요. 여러분의 필요에 맞게요. 즐거운 코딩 되세요!

## 자주 묻는 질문

### 목록에서 다른 글머리 기호를 사용할 수 있나요?
    예, 글머리 기호를 변경하여 사용자 정의할 수 있습니다.`NumberFormat` 재산.

### 들여쓰기 수준을 더 높이려면 어떻게 해야 하나요?
    사용하세요`ListIndent` 더 많은 레벨을 추가하는 방법`ListOutdent` 더 높은 수준으로 돌아가다.

### 글머리 기호 목록과 번호 목록을 혼합할 수 있나요?
   물론입니다! 다음을 사용하여 글머리 기호와 숫자 형식 사이를 전환할 수 있습니다.`ApplyNumberDefault` 그리고`ApplyBulletDefault` 행동 양식.

### 목록 항목의 텍스트에 스타일을 지정할 수 있나요?
    예, 다음을 사용하여 목록 항목 내의 텍스트에 다양한 스타일, 글꼴 및 서식을 적용할 수 있습니다.`Font` 의 속성`DocumentBuilder`.

### 여러 열로 구성된 요점 목록을 어떻게 만들 수 있나요?
   표 서식을 사용하면 각 셀에 별도의 글머리 기호 목록이 포함된 다중 열 목록을 만들 수 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
