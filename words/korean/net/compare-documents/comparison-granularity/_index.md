---
"description": "Aspose.Words for .NET의 Word 문서 기능인 '세분성 비교'를 통해 문서를 문자별로 비교하고 변경 사항을 보고할 수 있습니다."
"linktitle": "Word 문서의 비교 세분성"
"second_title": "Aspose.Words 문서 처리 API"
"title": "Word 문서의 비교 세분성"
"url": "/ko/net/compare-documents/comparison-granularity/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서의 비교 세분성

다음은 Aspose.Words for .NET의 Word 문서에서 세분성 비교 기능을 사용하는 아래의 C# 소스 코드를 설명하는 단계별 가이드입니다.

## 1단계: 소개

Aspose.Words for .NET의 세분성 비교 기능을 사용하면 문자 단위로 문서를 비교할 수 있습니다. 즉, 각 문자를 비교하고 변경 사항을 그에 따라 보고합니다.

## 2단계: 환경 설정

시작하기 전에 Aspose.Words for .NET을 사용할 수 있도록 개발 환경을 설정해야 합니다. Aspose.Words 라이브러리가 설치되어 있고 코드를 삽입할 적절한 C# 프로젝트가 있는지 확인하세요.

## 3단계: 필요한 어셈블리 추가

Aspose.Words for .NET의 세분성 비교 기능을 사용하려면 프로젝트에 필요한 어셈블리를 추가해야 합니다. 프로젝트에 Aspose.Words에 대한 참조가 제대로 되어 있는지 확인하세요.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## 4단계: 문서 만들기

이 단계에서는 DocumentBuilder 클래스를 사용하여 두 개의 문서를 만듭니다. 이 문서들은 비교에 사용됩니다.

```csharp
// 문서 A를 만듭니다.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// 문서 B를 만듭니다.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## 5단계: 비교 옵션 구성

이 단계에서는 비교 옵션을 구성하여 비교 단위를 지정합니다. 여기서는 문자 단위 단위를 사용합니다.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## 6단계: 문서 비교

이제 Document 클래스의 Compare 메서드를 사용하여 문서를 비교해 보겠습니다. 변경 사항은 문서 A에 저장됩니다.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

그만큼 `Compare` 이 방법은 문서 A와 문서 B를 비교하고 문서 A에 변경 사항을 저장합니다. 참조를 위해 작성자 이름과 비교 날짜를 지정할 수 있습니다.

## 결론

이 글에서는 Aspose.Words for .NET의 세분성 비교 기능을 살펴보았습니다. 이 기능을 사용하면 문자 단위로 문서를 비교하고 변경 사항을 보고할 수 있습니다. 이러한 지식을 활용하여 프로젝트에서 세부적인 문서 비교를 수행할 수 있습니다.

### Aspose.Words for .NET을 사용한 비교 세분성에 대한 샘플 소스 코드

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## 결론

이 튜토리얼에서는 Aspose.Words for .NET의 비교 세분성 기능을 살펴보았습니다. 이 기능을 사용하면 문서를 비교할 때 세부 수준을 지정할 수 있습니다. 다양한 세분성 수준을 선택하여 특정 요구 사항에 따라 문자, 단어 또는 블록 단위로 세부적인 비교를 수행할 수 있습니다. Aspose.Words for .NET은 유연하고 강력한 문서 비교 기능을 제공하여 다양한 세분성 수준의 문서에서 차이점을 쉽게 파악할 수 있도록 합니다.

### 자주 묻는 질문

#### 질문: Aspose.Words for .NET에서 비교 세분성을 사용하는 목적은 무엇입니까?

A: Aspose.Words for .NET의 비교 세분성을 사용하면 문서를 비교할 때 세부 수준을 지정할 수 있습니다. 이 기능을 사용하면 문자 수준, 단어 수준 또는 블록 수준 등 다양한 수준에서 문서를 비교할 수 있습니다. 각 세분성 수준은 비교 결과에 각기 다른 세부 수준을 제공합니다.

#### 질문: Aspose.Words for .NET에서 비교 세분성을 어떻게 사용하나요?

답변: Aspose.Words for .NET에서 비교 세분성을 사용하려면 다음 단계를 따르세요.
1. Aspose.Words 라이브러리로 개발 환경을 설정하세요.
2. Aspose.Words를 참조하여 프로젝트에 필요한 어셈블리를 추가합니다.
3. 다음을 사용하여 비교하려는 문서를 만듭니다. `DocumentBuilder` 수업.
4. 비교 옵션을 구성하려면 다음을 생성하세요. `CompareOptions` 객체 및 설정 `Granularity` 원하는 수준으로 속성을 (예: `Granularity.CharLevel` (문자 수준 비교용).
5. 사용하세요 `Compare` 한 문서에 대해 메서드를 사용하고 다른 문서에 전달합니다. `CompareOptions` 객체를 매개변수로 사용합니다. 이 메서드는 지정된 세분성을 기준으로 문서를 비교하고 첫 번째 문서에 변경 사항을 저장합니다.

#### 질문: Aspose.Words for .NET에서 사용 가능한 비교 세분성 수준은 무엇입니까?

A: Aspose.Words for .NET은 세 가지 수준의 비교 세분성을 제공합니다.
- `Granularity.CharLevel`: 문자 수준에서 문서를 비교합니다.
- `Granularity.WordLevel`: 단어 수준에서 문서를 비교합니다.
- `Granularity.BlockLevel`: 블록 수준에서 문서를 비교합니다.

#### 질문: 문자 수준의 세분성을 적용한 비교 결과를 어떻게 해석할 수 있나요?

A: 문자 단위 세분성을 사용하면 비교 대상 문서의 각 문자에 대한 차이점을 분석합니다. 비교 결과에는 추가, 삭제, 수정을 포함한 개별 문자 단위의 변경 사항이 표시됩니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}