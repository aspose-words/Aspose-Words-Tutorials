---
"description": "이 자세하고 단계별 튜토리얼을 통해 Aspose.Words for .NET을 사용하여 Word 문서에 웹 확장 작업 창을 추가하고 구성하는 방법을 알아보세요."
"linktitle": "웹 확장 작업창 사용"
"second_title": "Aspose.Words 문서 처리 API"
"title": "웹 확장 작업창 사용"
"url": "/ko/net/programming-with-webextension/using-web-extension-task-panes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 웹 확장 작업창 사용

## 소개

Aspose.Words for .NET을 사용하여 Word 문서에서 웹 확장 작업창을 사용하는 방법에 대한 심층적인 튜토리얼에 오신 것을 환영합니다. 대화형 작업창으로 Word 문서를 개선하고 싶으셨다면, 바로 여기가 정답입니다. 이 가이드는 이러한 작업을 원활하게 수행하는 모든 단계를 안내합니다.

## 필수 조건

시작하기에 앞서, 필요한 모든 것이 있는지 확인해 보겠습니다.

- Aspose.Words for .NET: 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/net/).
- .NET 개발 환경: Visual Studio 또는 사용자가 선호하는 다른 IDE.
- C#에 대한 기본 지식: 이를 통해 코드 예제를 따라가는 데 도움이 됩니다.
- Aspose.Words 라이센스: 하나를 구매할 수 있습니다. [여기](https://purchase.aspose.com/buy) 또는 임시 면허를 받으세요 [여기](https://purchase.aspose.com/temporary-license/).

## 네임스페이스 가져오기

코딩을 시작하기 전에 프로젝트에 다음 네임스페이스가 가져왔는지 확인하세요.

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## 단계별 가이드

이제 이 과정을 쉽게 따를 수 있는 단계로 나누어 보겠습니다.

### 1단계: 문서 디렉터리 설정

먼저, 문서 디렉터리 경로를 설정해야 합니다. Word 문서가 저장될 디렉터리입니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

바꾸다 `"YOUR DOCUMENT DIRECTORY"` 문서 폴더의 실제 경로를 사용합니다.

### 2단계: 새 문서 만들기

다음으로 Aspose.Words를 사용하여 새 Word 문서를 만들어 보겠습니다.

```csharp
Document doc = new Document();
```

이 줄은 새 인스턴스를 초기화합니다. `Document` Word 문서를 나타내는 클래스입니다.

### 3단계: 작업 창 추가

이제 문서에 작업창을 추가해 보겠습니다. 작업창은 Word 문서에서 추가 기능과 도구를 제공하는 데 유용합니다.

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

여기서 우리는 새로운 것을 만듭니다 `TaskPane` 객체를 추가하고 문서에 추가합니다. `WebExtensionTaskPanes` 수집.

### 4단계: 작업 창 구성

작업 창을 표시하고 속성을 설정하려면 다음 코드를 사용합니다.

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` 작업창이 나타날 위치를 설정합니다. 이 경우에는 오른쪽에 있습니다.
- `IsVisible` 작업창이 표시되도록 합니다.
- `Width` 작업창의 너비를 설정합니다.

### 5단계: 웹 확장 참조 설정

다음으로, ID, 버전, 스토어 유형 및 스토어를 포함하는 웹 확장 참조를 설정합니다.

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id` 웹 확장 프로그램에 대한 고유 식별자입니다.
- `Version` 확장 프로그램의 버전을 지정합니다.
- `StoreType` 매장의 유형을 나타냅니다(이 경우 OMEX).
- `Store` 매장의 언어/문화 코드를 지정합니다.

### 6단계: 웹 확장 프로그램에 속성 추가

웹 확장 기능에 속성을 추가하여 동작이나 콘텐츠를 정의할 수 있습니다.

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

여기서 우리는 다음과 같은 속성을 추가합니다. `mailchimpCampaign`.

### 7단계: 웹 확장 프로그램 바인딩

마지막으로 웹 확장 프로그램에 바인딩을 추가합니다. 바인딩을 사용하면 확장 프로그램을 문서의 특정 부분에 연결할 수 있습니다.

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` 바인딩의 이름입니다.
- `WebExtensionBindingType.Text` 바인딩이 텍스트 유형임을 나타냅니다.
- `194740422` 는 확장자가 바인딩된 문서 부분의 ID입니다.

### 8단계: 문서 저장

모든 것을 설정한 후 문서를 저장하세요.

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

이 줄은 주어진 파일 이름으로 지정된 디렉토리에 문서를 저장합니다.

### 9단계: 작업창 정보 로드 및 표시

작업 창 정보를 확인하고 표시하려면 문서를 로드하고 작업 창을 반복합니다.

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

이 코드는 문서를 로드하고 콘솔에 각 작업 창의 공급자, 버전 및 카탈로그 식별자를 인쇄합니다.

## 결론

이것으로 끝입니다! Aspose.Words for .NET을 사용하여 Word 문서에 웹 확장 작업창을 성공적으로 추가하고 구성했습니다. 이 강력한 기능은 문서 내에서 직접 추가 기능을 제공하여 Word 문서를 크게 향상시킬 수 있습니다. 

## 자주 묻는 질문

### Word에서 작업창이란 무엇인가요?
작업창은 Word 문서 내에서 추가 도구와 기능을 제공하여 사용자 상호 작용과 생산성을 향상시키는 인터페이스 요소입니다.

### 작업창의 모양을 사용자 지정할 수 있나요?
예, 다음과 같은 속성을 설정하여 작업 창의 모양을 사용자 정의할 수 있습니다. `DockState`, `IsVisible`, 그리고 `Width`.

### 웹 확장 속성이란 무엇인가요?
웹 확장 속성은 웹 확장에 추가하여 동작이나 콘텐츠를 정의할 수 있는 사용자 정의 속성입니다.

### 문서의 일부에 웹 확장 기능을 어떻게 바인딩합니까?
다음을 사용하여 문서의 일부에 웹 확장을 바인딩할 수 있습니다. `WebExtensionBinding` 바인딩 유형과 대상 ID를 지정하는 클래스입니다.

### Aspose.Words for .NET에 대한 자세한 정보는 어디에서 찾을 수 있나요?
자세한 문서를 찾을 수 있습니다 [여기](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}