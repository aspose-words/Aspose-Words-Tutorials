---
title: 재시작 목록 번호
linktitle: 재시작 목록 번호
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서에서 목록 번호를 다시 시작하는 방법을 알아보세요. 이 자세한 2000단어 가이드는 설정에서 고급 사용자 지정에 이르기까지 알아야 할 모든 것을 다룹니다.
weight: 10
url: /ko/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 재시작 목록 번호

## 소개

Aspose.Words for .NET을 사용하여 Word 문서에서 목록 조작 기술을 마스터하고 싶으신가요? 글쎄요, 당신은 올바른 곳에 있습니다! 이 튜토리얼에서는 목록 번호 재시작에 대해 자세히 알아보겠습니다. 이 기능은 문서 자동화 기술을 한 단계 업그레이드할 수 있는 멋진 기능입니다. 안전띠를 매고 시작해 봅시다!

## 필수 조건

코드로 넘어가기 전에 먼저 필요한 모든 것이 있는지 확인해 보겠습니다.

1.  Aspose.Words for .NET: Aspose.Words for .NET이 설치되어 있어야 합니다. 아직 설치하지 않았다면 다음을 수행할 수 있습니다.[여기서 다운로드하세요](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio와 같은 적합한 개발 환경이 있는지 확인하세요.
3. C#에 대한 기본 지식: C#에 대한 기본적인 이해가 있으면 튜토리얼을 따라가는 데 도움이 됩니다.

## 네임스페이스 가져오기

우선, 필요한 네임스페이스를 임포트해 보겠습니다. 이는 Aspose.Words 기능에 액세스하는 데 필수적입니다.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

이제 프로세스를 쉽게 따를 수 있는 단계로 나누어 보겠습니다. 목록을 만드는 것부터 번호 매기기를 다시 시작하는 것까지 모든 것을 다루겠습니다.

## 1단계: 문서 및 빌더 설정

목록을 조작하기 전에 문서와 DocumentBuilder가 필요합니다. DocumentBuilder는 문서에 콘텐츠를 추가하는 데 필요한 도구입니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2단계: 첫 번째 목록 만들기 및 사용자 지정

다음으로, 템플릿을 기반으로 목록을 만들고 모양을 사용자 정의합니다. 이 예에서는 괄호가 있는 아라비아 숫자 형식을 사용합니다.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

여기서는 글꼴 색상을 빨간색으로 설정하고 텍스트를 오른쪽에 정렬했습니다.

## 3단계: 첫 번째 목록에 항목 추가

 목록이 준비되면 이제 몇 가지 항목을 추가할 시간입니다. DocumentBuilder의`ListFormat.List` 속성은 텍스트에 목록 형식을 적용하는 데 도움이 됩니다.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## 4단계: 목록 번호 매기기 다시 시작

목록을 재사용하고 번호 매기기를 다시 시작하려면 원래 목록의 사본을 만들어야 합니다. 이렇게 하면 새 목록을 독립적으로 수정할 수 있습니다.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

이 예에서 새로운 목록은 번호 10부터 시작합니다.

## 5단계: 새 목록에 항목 추가

이전과 마찬가지로 새 목록에 항목을 추가합니다. 이는 지정된 번호에서 목록이 다시 시작되는 것을 보여줍니다.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## 6단계: 문서 저장

마지막으로, 지정한 디렉토리에 문서를 저장합니다.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## 결론

Aspose.Words for .NET을 사용하여 Word 문서에서 목록 번호를 다시 시작하는 것은 간단하고 매우 유용합니다. 보고서를 생성하든, 구조화된 문서를 만들든, 그저 목록을 더 잘 제어해야 하든, 이 기술이 당신을 도울 것입니다.

## 자주 묻는 질문

### NumberArabicParenthesis 외에 다른 목록 템플릿을 사용할 수 있나요?

물론입니다! Aspose.Words는 글머리 기호, 문자, 로마 숫자 등 다양한 목록 템플릿을 제공합니다. 귀하의 필요에 가장 잘 맞는 템플릿을 선택할 수 있습니다.

### 목록 수준을 어떻게 변경합니까?

 목록 수준을 수정하여 변경할 수 있습니다.`ListLevels` 속성. 예를 들어,`list1.ListLevels[1]` 목록의 두 번째 수준을 나타냅니다.

### 어떤 번호에서든 번호 매기기를 다시 시작할 수 있나요?

 예, 다음을 사용하여 시작 번호를 정수 값으로 설정할 수 있습니다.`StartAt` 목록 수준의 속성입니다.

### 목록 수준마다 다른 형식을 사용하는 것이 가능합니까?

물론입니다! 각 목록 레벨은 글꼴, 정렬, 번호 매기기 스타일과 같은 자체 서식 설정을 가질 수 있습니다.

### 다시 시작하는 대신 이전 목록에서 번호 매기기를 계속하려면 어떻게 해야 하나요?

번호 매기기를 계속하려면 목록의 사본을 만들 필요가 없습니다. 원래 목록에 항목을 계속 추가하기만 하면 됩니다.



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
