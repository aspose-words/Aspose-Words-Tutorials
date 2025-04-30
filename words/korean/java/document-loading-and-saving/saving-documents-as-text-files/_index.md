---
"description": "Aspose.Words for Java에서 문서를 텍스트 파일로 저장하는 방법을 알아보세요. Java 코드 예제를 통해 단계별 가이드를 따라 해 보세요."
"linktitle": "문서를 텍스트 파일로 저장"
"second_title": "Aspose.Words Java 문서 처리 API"
"title": "Aspose.Words for Java에서 문서를 텍스트 파일로 저장하기"
"url": "/ko/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java에서 문서를 텍스트 파일로 저장하기


## Aspose.Words for Java에서 문서를 텍스트 파일로 저장하는 방법 소개

이 튜토리얼에서는 Aspose.Words for Java 라이브러리를 사용하여 문서를 텍스트 파일로 저장하는 방법을 살펴보겠습니다. Aspose.Words는 Word 문서 작업을 위한 강력한 Java API로, 일반 텍스트를 포함한 다양한 형식으로 문서를 저장할 수 있는 다양한 옵션을 제공합니다. 이를 위한 단계를 설명하고, 그 과정에서 샘플 Java 코드를 제공합니다.

## 필수 조건

시작하기에 앞서 다음과 같은 전제 조건이 충족되었는지 확인하세요.

- 시스템에 Java Development Kit(JDK)가 설치되어 있어야 합니다.
- Aspose.Words for Java 라이브러리가 프로젝트에 통합되었습니다. 다음에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/java/).
- Java 프로그래밍에 대한 기본 지식.

## 1단계: 문서 만들기

문서를 텍스트 파일로 저장하려면 먼저 Aspose.Words를 사용하여 문서를 만들어야 합니다. 다음은 내용이 포함된 문서를 생성하는 간단한 Java 코드 조각입니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

이 코드에서는 새 문서를 만들고 다양한 언어의 텍스트를 포함한 텍스트를 추가합니다.

## 2단계: 텍스트 저장 옵션 정의

다음으로, 문서를 텍스트 파일로 저장하는 방식을 지정하는 텍스트 저장 옵션을 정의해야 합니다. 양방향 마크 추가, 목록 들여쓰기 등 다양한 설정을 구성할 수 있습니다. 두 가지 예를 살펴보겠습니다.

### 예제 1: 비디 마크 추가

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

이 예에서 우리는 다음을 생성합니다. `TxtSaveOptions` 객체를 설정하고 `AddBidiMarks` 재산에 `true` 텍스트 출력에 양방향 표시를 포함합니다.

### 예제 2: 목록 들여쓰기에 탭 문자 사용

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

여기서는 목록 들여쓰기에 탭 문자를 사용하고 카운트를 1로 설정하여 저장 옵션을 구성합니다.

## 3단계: 문서를 텍스트로 저장

이제 텍스트 저장 옵션을 정의했으므로 문서를 텍스트 파일로 저장할 수 있습니다. 다음 코드는 이 작업을 수행하는 방법을 보여줍니다.

```java
doc.save("output.txt", saveOptions);
```

바꾸다 `"output.txt"` 텍스트 파일을 저장하려는 원하는 파일 경로를 입력하세요.

## Aspose.Words for Java에서 문서를 텍스트 파일로 저장하기 위한 전체 소스 코드

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // 3단계 들여쓰기로 목록을 만듭니다.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // 3단계 들여쓰기로 목록을 만듭니다.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## 결론

이 튜토리얼에서는 Aspose.Words for Java에서 문서를 텍스트 파일로 저장하는 방법을 알아보았습니다. 문서를 생성하고, 텍스트 저장 옵션을 정의하고, 문서를 텍스트 형식으로 저장하는 단계를 살펴보았습니다. Aspose.Words는 문서 저장에 있어 광범위한 유연성을 제공하여 특정 요구 사항에 맞게 출력을 조정할 수 있습니다.

## 자주 묻는 질문

### 텍스트 출력에 양방향 마크를 추가하려면 어떻게 해야 하나요?

텍스트 출력에 양방향 표시를 추가하려면 다음을 설정하세요. `AddBidiMarks` 의 속성 `TxtSaveOptions` 에게 `true`. 예를 들어:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### 목록 들여쓰기 문자를 사용자 정의할 수 있나요?

예, 다음을 구성하여 목록 들여쓰기 문자를 사용자 정의할 수 있습니다. `ListIndentation` 의 속성 `TxtSaveOptions`예를 들어, 목록 들여쓰기에 탭 문자를 사용하려면 다음과 같이 하면 됩니다.

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words for Java는 다국어 텍스트를 처리하는 데 적합합니까?

네, Aspose.Words for Java는 다국어 텍스트 처리에 적합합니다. 다양한 언어와 문자 인코딩을 지원하여 여러 언어로 작성된 문서 작업에 매우 유용합니다.

### Aspose.Words for Java에 대한 더 많은 문서와 리소스에 어떻게 접근할 수 있나요?

Aspose.Words for Java에 대한 포괄적인 문서와 리소스는 Aspose 문서 웹사이트에서 찾을 수 있습니다. [Java 문서용 Aspose.Words](https://reference.aspose.com/words/java/).

### Aspose.Words for Java는 어디서 다운로드할 수 있나요?

Aspose 웹사이트에서 Aspose.Words for Java 라이브러리를 다운로드할 수 있습니다. [Java용 Aspose.Words 다운로드](https://releases.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}