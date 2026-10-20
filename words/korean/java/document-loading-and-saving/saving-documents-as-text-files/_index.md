---
date: 2025-12-24
description: Aspose.Words for Java를 사용하여 Word 문서에서 일반 텍스트 파일을 만드는 방법을 배웁니다. 이 가이드는
  Word를 txt로 변환하고, 탭 들여쓰기를 사용하며, Word를 txt로 저장하는 방법을 보여줍니다.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java를 사용하여 일반 텍스트 파일 만들기
url: /ko/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 사용하여 일반 텍스트 파일 만들기

## Aspose.Words for Java에서 문서를 텍스트 파일로 저장하기 소개

이 튜토리얼에서는 Aspose.Words for Java 라이브러리를 사용하여 Word 문서에서 **일반 텍스트 파일을 만드는 방법**을 배웁니다. **word를 txt로 변환**이 필요하든, 보고서 생성을 자동화하든, 혹은 원시 텍스트를 추출해 추가 처리하든, 이 가이드는 문서 생성부터 **탭 들여쓰기 사용** 또는 bidi 마크 추가와 같은 저장 옵션 세부 조정까지 전체 워크플로를 안내합니다. 시작해봅시다!

## 빠른 답변
- **문서를 생성하는 기본 클래스는?** Aspose.Words의 `Document`.
- **우측에서 좌측 언어용 bidi 마크를 추가하는 옵션은?** `TxtSaveOptions.setAddBidiMarks(true)`.
- **탭으로 리스트 항목을 들여쓰기하려면?** `ListIndentation.Character`를 `'\t'`로 설정.
- **개발에 라이선스가 필요합니까?** 테스트용 무료 체험판으로 가능하지만, 프로덕션에서는 라이선스가 필요합니다.
- **파일을 사용자 지정 이름과 경로로 저장할 수 있나요?** 예—전체 경로를 `doc.save()`에 전달하면 됩니다.

## 전제 조건

시작하기 전에 다음 전제 조건을 확인하세요:

- 시스템에 Java Development Kit (JDK)가 설치되어 있어야 합니다.  
- 프로젝트에 Aspose.Words for Java 라이브러리가 통합되어 있어야 합니다. 라이브러리는 [여기](https://releases.aspose.com/words/java/)에서 다운로드할 수 있습니다.  
- Java 프로그래밍에 대한 기본 지식이 필요합니다.

## 1단계: 문서 만들기

**word를 txt로 저장**하려면 먼저 `Document` 인스턴스를 생성해야 합니다. 아래는 다국어 텍스트 몇 줄을 작성하는 간단한 Java 코드 스니펫입니다:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

이 코드는 새 문서를 만들고, 영어, 히브리어, 아랍어 텍스트를 추가한 뒤 히브리어 단락에 우측‑좌측 서식을 활성화합니다.

## 2단계: 텍스트 저장 옵션 정의

다음으로 문서를 일반 텍스트 파일로 저장하는 방식을 구성합니다. Aspose.Words는 `TxtSaveOptions` 클래스를 제공하며, 이를 통해 bidi 마크부터 리스트 들여쓰기까지 모든 옵션을 제어할 수 있습니다.

### 예제 1: Bidi 마크 추가 (RTL 지원이 올바른 txt 저장)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

`AddBidiMarks`를 `true`로 설정하면 우측‑좌측 문자가 **일반 텍스트 파일**에 올바르게 표시됩니다.

### 예제 2: 리스트 들여쓰기에 탭 문자 사용 (탭 들여쓰기)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

여기서는 각 리스트 레벨 앞에 탭 문자(`'\t'`)를 추가하도록 Aspose.Words에 지시하여 텍스트 출력이 더 읽기 쉽도록 합니다.

## 3단계: 문서를 텍스트로 저장

이제 저장 옵션이 준비되었으니 **일반 텍스트 파일**로 문서를 저장할 수 있습니다:

```java
doc.save("output.txt", saveOptions);
```

`"output.txt"`를 파일을 저장하고자 하는 전체 경로로 교체하세요.

## Aspose.Words for Java에서 텍스트 파일 저장을 위한 전체 소스 코드

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
        // Create a list with three levels of indentation.
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
        // Create a list with three levels of indentation.
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

## 일반적인 문제와 해결책

| Issue | Solution |
|-------|----------|
| **Bidi 문자들이 깨져 보임** | `setAddBidiMarks(true)`가 활성화되어 있는지 확인하고, 출력 파일을 UTF‑8 인코딩으로 열어야 합니다. |
| **리스트 들여쓰기가 잘못 표시됨** | `ListIndentation.Count`와 `Character`가 원하는 값(탭 `'\t'` 또는 공백 `' '` )으로 설정되어 있는지 확인하세요. |
| **파일이 생성되지 않음** | 디렉터리 경로가 존재하고 애플리케이션에 쓰기 권한이 있는지 확인합니다. |

## 자주 묻는 질문

### 텍스트 출력에 bidi 마크를 어떻게 추가하나요?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### 리스트 들여쓰기 문자를 사용자 지정할 수 있나요?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words for Java가 다국어 텍스트 처리를 지원하나요?

예, Aspose.Words for Java는 다양한 언어와 문자 인코딩을 지원하므로 다국어 콘텐츠를 일반 텍스트로 추출하고 저장하는 데 적합합니다.

### Aspose.Words for Java에 대한 추가 문서와 리소스는 어디서 찾을 수 있나요?

다음 페이지에서 포괄적인 문서와 리소스를 확인할 수 있습니다: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Aspose.Words for Java를 어디서 다운로드하나요?

공식 사이트에서 라이브러리를 다운로드할 수 있습니다: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### 배치 프로세스에서 **word를 txt로 변환**해야 할 경우는 어떻게 하나요?

위 코드를 루프에 넣어 각 `.docx` 파일을 로드하고 동일한 `TxtSaveOptions`를 적용한 뒤 `.txt`로 저장하면 됩니다. 반복마다 `Document` 객체를 적절히 해제하여 리소스를 관리하세요.

### API가 파일 대신 스트림에 직접 저장하는 것을 지원하나요?

예, `doc.save(outputStream, saveOptions)`에 `OutputStream`을 전달하면 메모리 내 처리나 웹 서비스와의 통합에 사용할 수 있습니다.

---

**마지막 업데이트:** 2025-12-24  
**테스트 환경:** Aspose.Words for Java 24.12 (최신)  
**작성자:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}