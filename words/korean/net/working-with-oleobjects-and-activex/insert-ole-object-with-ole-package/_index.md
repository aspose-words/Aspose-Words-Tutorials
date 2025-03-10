---
title: OLE 패키지로 Word에 OLE 개체 삽입
linktitle: OLE 패키지로 Word에 OLE 개체 삽입
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서에 OLE 개체를 삽입하는 방법을 알아보세요. 자세한 단계별 가이드를 따라 파일을 매끄럽게 임베드하세요.
weight: 10
url: /ko/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# OLE 패키지로 Word에 OLE 개체 삽입

## 소개

Word 문서에 파일을 임베드하고 싶었던 적이 있다면, 당신은 올바른 곳에 있습니다. ZIP 파일이든, Excel 시트이든, 다른 파일 유형이든, Word 문서에 직접 임베드하는 것은 엄청나게 유용할 수 있습니다. 문서에 온갖 보물을 숨길 수 있는 비밀 보관소가 있다고 생각해 보세요. 그리고 오늘은 Aspose.Words for .NET을 사용하여 이를 수행하는 방법을 살펴보겠습니다. Word 마법사가 될 준비가 되셨나요? 시작해 볼까요!

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1. .NET용 Aspose.Words: 아직 다운로드하지 않았다면 여기에서 다운로드하세요.[여기](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio 또는 기타 .NET 개발 환경.
3. C#에 대한 기본적인 이해: 전문가가 될 필요는 없지만, C#를 다루는 방법을 알고 있으면 도움이 됩니다.
4. 문서 디렉토리: 문서를 저장하고 검색할 수 있는 폴더입니다.

## 네임스페이스 가져오기

우선, 네임스페이스를 정리합시다. 프로젝트에 다음 네임스페이스를 포함해야 합니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

따라하기 쉽도록 작은 단계로 나누어 설명해 보겠습니다.

## 1단계: 문서 설정

빈 캔버스를 가진 예술가라고 상상해 보세요. 먼저, 빈 캔버스가 필요한데, 그것은 Word 문서입니다. 설정하는 방법은 다음과 같습니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

이 코드는 새 Word 문서를 초기화하고 문서에 내용을 삽입하는 데 사용할 DocumentBuilder를 설정합니다.

## 2단계: Ole 객체 읽기

다음으로, 임베드하려는 파일을 읽어봅시다. 이것을 비밀 보관함에 숨기고 싶은 보물을 집어드는 것으로 생각해보세요.

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

이 줄은 ZIP 파일에서 모든 바이트를 읽어 바이트 배열에 저장합니다.

## 3단계: Ole 개체 삽입

이제 마법의 부분이 옵니다. 파일을 Word 문서에 임베드합니다.

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

 여기서 우리는 바이트 배열에서 메모리 스트림을 생성하고 사용합니다.`InsertOleObject` 문서에 임베드하는 방법입니다. 또한 임베드된 객체에 대한 파일 이름과 표시 이름도 설정합니다.

## 4단계: 문서 저장

마지막으로, 우리의 걸작을 저장해 보겠습니다.

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

이렇게 하면 지정된 디렉토리에 내장된 파일이 있는 문서가 저장됩니다.

## 결론

이제 Aspose.Words for .NET을 사용하여 Word 문서에 OLE 개체를 성공적으로 임베드했습니다. 언제든지 공개할 수 있는 문서 내부에 숨겨진 보석을 추가하는 것과 같습니다. 이 기술은 기술 문서에서 동적 보고서에 이르기까지 다양한 애플리케이션에 매우 유용할 수 있습니다. 

## 자주 묻는 질문

### 이 방법을 사용하여 다른 파일 형식을 내장할 수 있나요?
네, Excel 시트, PDF, 이미지 등 다양한 파일 유형을 포함할 수 있습니다.

### Aspose.Words를 사용하려면 라이센스가 필요한가요?
 네, 유효한 면허가 필요합니다.[임시 면허](https://purchase.aspose.com/temporary-license/) 평가를 위해서.

### OLE 개체의 표시 이름을 사용자 지정하려면 어떻게 해야 하나요?
 설정할 수 있습니다`DisplayName` 의 속성`OlePackage` 사용자 정의하려면 다음을 클릭하세요.

### Aspose.Words는 .NET Core와 호환됩니까?
네, Aspose.Words는 .NET Framework와 .NET Core를 모두 지원합니다.

### Word 문서 내에서 포함된 OLE 개체를 편집할 수 있나요?
아니요, Word에서 OLE 개체를 직접 편집할 수 없습니다. 네이티브 응용 프로그램에서 열어야 합니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
