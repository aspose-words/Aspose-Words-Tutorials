---
"description": "Aspose.Words for .NET을 사용하여 Word 문서를 HTML로 저장할 때 CSS 클래스 이름 접두사를 추가하는 방법을 알아보세요. 단계별 가이드, 코드 조각, FAQ가 포함되어 있습니다."
"linktitle": "CSS 클래스 이름 접두사 추가"
"second_title": "Aspose.Words 문서 처리 API"
"title": "CSS 클래스 이름 접두사 추가"
"url": "/ko/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# CSS 클래스 이름 접두사 추가

## 소개

환영합니다! Aspose.Words for .NET의 세계에 뛰어드셨다면, 정말 멋진 경험을 하실 겁니다. 오늘은 Aspose.Words for .NET을 사용하여 Word 문서를 HTML로 저장할 때 CSS 클래스 이름 접두사를 추가하는 방법을 알아보겠습니다. 이 기능은 HTML 파일에서 클래스 이름 충돌을 방지하고 싶을 때 매우 유용합니다.

## 필수 조건

시작하기에 앞서 다음 사항이 있는지 확인하세요.

- Aspose.Words for .NET: 아직 설치하지 않았다면, [여기서 다운로드하세요](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio 또는 기타 C# IDE.
- Word 문서: 다음 이름의 문서를 사용합니다. `Rendering.docx`프로젝트 디렉토리에 넣으세요.

## 네임스페이스 가져오기

먼저, 필요한 네임스페이스를 C# 프로젝트로 가져왔는지 확인하세요. 코드 파일 맨 위에 다음 내용을 추가하세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

이제 단계별 가이드를 살펴보겠습니다!

## 1단계: 프로젝트 설정

CSS 클래스 이름 접두사를 추가하기 전에 프로젝트를 설정해 보겠습니다.

### 1.1단계: 새 프로젝트 만들기

Visual Studio를 실행하고 새 콘솔 앱 프로젝트를 만듭니다. 다음과 같이 기억하기 쉬운 이름을 지정합니다. `AsposeCssPrefixExample`.

### 1.2단계: .NET용 Aspose.Words 추가

아직 추가하지 않았다면 NuGet을 통해 Aspose.Words for .NET을 프로젝트에 추가하세요. NuGet 패키지 관리자 콘솔을 열고 다음을 실행하세요.

```bash
Install-Package Aspose.Words
```

좋습니다! 이제 코딩을 시작할 준비가 되었습니다.

## 2단계: 문서 로드

가장 먼저 해야 할 일은 HTML로 변환하려는 Word 문서를 로드하는 것입니다.

### 2.1단계: 문서 경로 정의

문서 디렉터리 경로를 설정하세요. 이 튜토리얼에서는 문서가 다음 이름의 폴더에 있다고 가정하겠습니다. `Documents` 프로젝트 디렉토리 내에서.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### 2.2단계: 문서 로드

이제 Aspose.Words를 사용하여 문서를 로드해 보겠습니다.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3단계: HTML 저장 옵션 구성

다음으로, CSS 클래스 이름 접두사를 포함하도록 HTML 저장 옵션을 구성해야 합니다.

### 3.1단계: HTML 저장 옵션 만들기

인스턴스화 `HtmlSaveOptions` 객체를 만들고 CSS 스타일 시트 유형을 설정합니다. `External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### 3.2단계: CSS 클래스 이름 접두사 설정

이제 설정해 보겠습니다. `CssClassNamePrefix` 속성을 원하는 접두사로 변경합니다. 이 예에서는 `"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## 4단계: 문서를 HTML로 저장

마지막으로, 구성된 옵션을 사용하여 문서를 HTML 파일로 저장해 보겠습니다.


출력 HTML 파일 경로를 지정하고 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## 5단계: 출력 확인

프로젝트를 실행한 후 다음으로 이동합니다. `Documents` 폴더. 이름이 지정된 HTML 파일을 찾아야 합니다. `WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`CSS 클래스에 접두사가 있는지 확인하려면 텍스트 편집기나 브라우저에서 이 파일을 엽니다. `pfx_`.

## 결론

자, 이제 완료되었습니다! 다음 단계를 따라 Aspose.Words for .NET을 사용하여 HTML 출력에 CSS 클래스 이름 접두사를 성공적으로 추가했습니다. 이 간단하면서도 강력한 기능은 HTML 문서에서 깔끔하고 충돌 없는 스타일을 유지하는 데 도움이 됩니다.

## 자주 묻는 질문

### 각 저장 작업에 다른 접두사를 사용할 수 있나요?
예, 문서를 저장할 때마다 접두사를 사용자 정의할 수 있습니다. `CssClassNamePrefix` 재산.

### 이 방법은 인라인 CSS를 지원합니까?
그만큼 `CssClassNamePrefix` 속성은 외부 CSS와 함께 작동합니다. 인라인 CSS의 경우 다른 접근 방식이 필요합니다.

### 다른 HTML 저장 옵션을 어떻게 포함할 수 있나요?
다양한 속성을 구성할 수 있습니다. `HtmlSaveOptions` HTML 출력을 사용자 정의하려면 다음을 확인하세요. [선적 서류 비치](https://reference.aspose.com/words/net/) 자세한 내용은.

### HTML을 스트림에 저장할 수 있나요?
물론입니다! 스트림 객체를 스트림에 전달하여 문서를 스트림에 저장할 수 있습니다. `Save` 방법.

### 문제가 발생하면 어떻게 지원을 받을 수 있나요?
당신은에서 지원을 받을 수 있습니다 [Aspose 포럼](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}