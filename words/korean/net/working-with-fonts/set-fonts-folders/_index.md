---
title: 글꼴 폴더 설정
linktitle: 글꼴 폴더 설정
second_title: Aspose.Words 문서 처리 API
description: 이 포괄적인 단계별 가이드로 Aspose.Words for .NET에서 사용자 지정 글꼴 폴더를 설정하는 방법을 알아보세요. 문서 글꼴을 향상시키고자 하는 개발자에게 완벽합니다.
weight: 10
url: /ko/net/working-with-fonts/set-fonts-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 글꼴 폴더 설정

## 소개

안녕하세요! Aspose.Words for .NET에서 사용자 정의 글꼴의 세계로 뛰어들 준비가 되셨나요? 시작해 볼까요. 이 튜토리얼은 사용자 정의 글꼴 폴더를 설정하는 과정을 안내하여 문서가 원하는 대로 보이도록 합니다. 노련한 개발자이든 초보자이든 이 가이드는 모든 단계를 안내합니다. 그럼, 그 글꼴을 멋지게 만들어 볼까요!

## 필수 조건

시작하기에 앞서, 필요한 모든 것이 있는지 확인해 보겠습니다.

-  .NET용 Aspose.Words: 다음을 수행할 수 있습니다.[다운로드](https://releases.aspose.com/words/net/) 아직 하지 않았다면 지금 하세요.
- Visual Studio: 어느 버전이든 작동하지만 최신 버전이 항상 가장 좋습니다.
- 문서: 이 튜토리얼에서는 Word 문서를 사용합니다. 직접 만들거나 기존 문서를 사용할 수 있습니다.
- 사용자 정의 글꼴: 사용자 정의 글꼴을 준비하세요. 이를 사용하여 글꼴 폴더를 설정하는 방법을 보여드리겠습니다.

## 네임스페이스 가져오기

우선, 필요한 네임스페이스를 임포트해 보겠습니다. 이는 Aspose.Words에서 필요한 클래스와 메서드에 액세스하는 데 필수적입니다.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

이러한 네임스페이스를 가져왔으니 이제 사용자 정의 글꼴 폴더를 설정할 준비가 되었습니다.

## 1단계: 문서 디렉토리 정의

 문서 디렉토리 경로를 정의하는 것으로 시작해 보겠습니다. 여기에 Word 문서가 저장됩니다. 우리는 라는 변수를 사용할 것입니다.`dataDir` 이 경로를 저장합니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 바꾸다`"YOUR DOCUMENT DIRECTORY"` 디렉토리로 가는 실제 경로와 함께. 이것은 Aspose.Words가 문서를 어디에서 찾을지 알아야 하기 때문에 중요합니다.

## 2단계: 글꼴 소스 설정

 다음으로, 글꼴 소스를 설정해야 합니다. 여기서 Aspose.Words에 사용자 정의 글꼴을 찾을 위치를 알려줍니다.`FontSettings.DefaultInstance.SetFontsSources` 이를 달성하기 위한 방법.

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

우리가 하는 일은 다음과 같습니다.

- SystemFontSource: Aspose.Words에게 시스템의 기본 글꼴을 사용하도록 알려줍니다.
-  FolderFontSource: 여기서 사용자 정의 글꼴이 들어 있는 폴더를 지정합니다. 바꾸기`"C:\\MyFonts\\"` 사용자 정의 글꼴 디렉토리 경로와 함께.`true` 매개변수는 하위 디렉토리도 포함되어야 함을 나타냅니다.

## 3단계: 문서 로드

이제 글꼴 소스를 설정했으므로 작업하려는 문서를 로드할 시간입니다. 다음을 사용합니다.`Document` Aspose.Words에서 온 수업입니다.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 확인한다`"Rendering.docx"` 는 Word 문서의 이름입니다. 문서에 다른 이름이 있는 경우 이에 따라 업데이트해야 합니다.

## 4단계: 문서를 PDF로 저장

 마지막으로 사용자 정의 글꼴이 실제로 어떻게 작동하는지 보려면 문서를 PDF로 저장해 보겠습니다.`Save` 의 방법`Document` 수업.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

이렇게 하면 사용자 정의 글꼴을 사용하여 지정된 디렉토리에 PDF로 문서가 저장됩니다.

## 결론

이제 다 됐어요! Aspose.Words for .NET에서 사용자 정의 글꼴 폴더를 성공적으로 설정하고 해당 사용자 정의 글꼴을 사용하여 문서를 PDF로 저장했습니다. 꽤 멋지죠? 글꼴을 사용자 정의하면 문서의 모양이 크게 달라질 수 있으며, 이제 그 방법을 정확히 알게 되었습니다. 즐거운 코딩 되세요!

## 자주 묻는 질문

### Aspose.Words for .NET을 어떻게 설치하나요?

 당신은 할 수 있습니다[다운로드](https://releases.aspose.com/words/net/) 웹사이트에서 .NET용 Aspose.Words의 최신 버전을 다운로드하세요.

### 사용자 정의 글꼴 폴더를 여러 개 사용할 수 있나요?

 네, 여러 개를 추가할 수 있습니다.`FolderFontSource` 인스턴스에`SetFontsSources`다양한 디렉토리의 글꼴을 사용하는 방법.

### 시스템 글꼴을 포함해야 합니까?

시스템 글꼴을 포함하는 것은 선택 사항이지만 모든 표준 글꼴을 사용할 수 있도록 하는 것이 좋습니다.

### Aspose.Words는 어떤 파일 형식을 지원하나요?

Aspose.Words는 DOCX, DOC, PDF, TXT, HTML 등 다양한 파일 형식을 지원합니다.

### Aspose.Words에 대한 임시 라이센스를 어떻게 받을 수 있나요?

 당신은 얻을 수 있습니다[임시 면허](https://purchase.aspose.com/temporary-license/) Aspose 웹사이트에 접속하여 Aspose.Words의 모든 기능을 사용해 보세요.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
