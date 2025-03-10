---
title: Word 파일에서 Active XControl 속성 읽기
linktitle: Word 파일에서 Active XControl 속성 읽기
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 파일에서 ActiveX 컨트롤 속성을 읽는 방법을 단계별 가이드로 알아보세요. 문서 자동화 기술을 향상시키세요.
weight: 10
url: /ko/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 파일에서 Active XControl 속성 읽기

## 소개

오늘날의 디지털 시대에 자동화는 생산성을 향상시키는 데 중요합니다. ActiveX 컨트롤이 포함된 Word 문서로 작업하는 경우 다양한 목적으로 해당 속성을 읽어야 할 수 있습니다. 체크박스 및 버튼과 같은 ActiveX 컨트롤은 중요한 데이터를 보관할 수 있습니다. Aspose.Words for .NET을 사용하면 이 데이터를 효율적으로 추출하고 프로그래밍 방식으로 조작할 수 있습니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1.  Aspose.Words for .NET 라이브러리: 여기에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
2. Visual Studio 또는 C# IDE: 코드를 작성하고 실행합니다.
3. ActiveX 컨트롤이 있는 Word 문서: 예: "ActiveX controls.docx".
4. C#에 대한 기본 지식: 이 내용을 따라가려면 C# 프로그래밍에 대한 지식이 필요합니다.

## 네임스페이스 가져오기

먼저, Aspose.Words for .NET 작업에 필요한 네임스페이스를 가져와 보겠습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## 1단계: Word 문서 로드

시작하려면 ActiveX 컨트롤이 포함된 Word 문서를 로드해야 합니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## 2단계: 속성을 보관하기 위한 문자열 초기화

다음으로, ActiveX 컨트롤의 속성을 저장하기 위해 빈 문자열을 초기화합니다.

```csharp
string properties = "";
```

## 3단계: 문서의 모양 반복

ActiveX 컨트롤을 찾으려면 문서의 모든 모양을 반복해야 합니다.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // ActiveX 컨트롤을 처리합니다
    }
}
```

## 4단계: ActiveX 컨트롤에서 속성 추출

루프 내에서 컨트롤이 Forms2OleControl인지 확인합니다. 그렇다면 캐스팅하고 속성을 추출합니다.

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## 5단계: ActiveX 컨트롤 총 수 계산

모든 모양을 반복한 후, 발견된 ActiveX 컨트롤의 총 개수를 세어보세요.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## 6단계: 속성 표시

마지막으로 추출된 속성을 콘솔에 출력합니다.

```csharp
Console.WriteLine("\n" + properties);
```

## 결론

이제 Aspose.Words for .NET을 사용하여 Word 문서에서 ActiveX 컨트롤 속성을 읽는 방법을 성공적으로 배웠습니다. 이 튜토리얼에서는 문서 로드, 셰이프 반복, ActiveX 컨트롤에서 속성 추출을 다루었습니다. 이러한 단계를 따르면 Word 문서에서 중요한 데이터 추출을 자동화하여 워크플로 효율성을 높일 수 있습니다.

## 자주 묻는 질문

### Word 문서의 ActiveX 컨트롤이란 무엇입니까?
ActiveX 컨트롤은 체크박스, 단추, 텍스트 필드와 같이 Word 문서에 포함된 대화형 개체로, 양식을 만들고 작업을 자동화하는 데 사용됩니다.

### Aspose.Words for .NET을 사용하여 ActiveX 컨트롤의 속성을 수정할 수 있습니까?
네, Aspose.Words for .NET을 사용하면 ActiveX 컨트롤의 속성을 프로그래밍 방식으로 수정할 수 있습니다.

### Aspose.Words for .NET은 무료로 사용할 수 있나요?
 Aspose.Words for .NET은 무료 평가판을 제공하지만 계속 사용하려면 라이선스를 구매해야 합니다. 무료 평가판을 받을 수 있습니다.[여기](https://releases.aspose.com/).

### C# 외의 다른 .NET 언어에서도 Aspose.Words for .NET을 사용할 수 있나요?
네, Aspose.Words for .NET은 VB.NET 및 F#을 포함한 모든 .NET 언어와 함께 사용할 수 있습니다.

### .NET용 Aspose.Words에 대한 추가 문서는 어디에서 찾을 수 있나요?
 자세한 문서를 찾을 수 있습니다[여기](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
