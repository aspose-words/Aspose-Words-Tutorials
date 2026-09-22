---
category: general
date: 2026-02-18
description: Java에서 누락된 폰트를 감지하기 위한 로드 옵션을 만들고, 경고 콜백을 사용하여 DOCX 파일을 로드하는 방법을 배워보세요.
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: ko
og_description: Java에서 로드 옵션을 생성하여 누락된 폰트를 감지하고, 경고 콜백을 사용해 DOCX 파일을 로드하는 방법을 배우세요.
og_title: Java에서 로드 옵션 만들기 – 누락된 폰트 감지 및 DOCX 로드 방법
tags:
- java
- aspose-words
- document-processing
title: Java에서 로드 옵션 만들기 – 누락된 폰트 감지 및 DOCX 로드 방법
url: /ko/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

Proceed to translate.

Let's produce final Korean markdown.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 Load Options 만들기 – 누락된 폰트 감지 및 DOCX 로드 방법

DOCX를 읽을 뿐만 아니라 폰트가 누락되었을 때 알려주는 **로드 옵션**을 만든 적이 있나요? 당신만 그런 것이 아닙니다. 누락된 폰트는 완벽하게 스타일링된 문서를 엉망으로 만들 수 있으며, 이를 조기에 발견하면 디버깅에 들어가는 시간을 크게 절약할 수 있습니다. 이번 튜토리얼에서는 **누락된 폰트를 감지**하는 정확한 단계와 **DOCX 파일을 로드**하는 방법을 맞춤형 경고 콜백과 함께 살펴보겠습니다.

## 배울 내용

- `LoadOptions`를 인스턴스화하고 경고 핸들러를 구성하는 방법  
- 폰트 대체 문제를 잡아내기 위해 경고 콜백이 왜 필수적인지  
- **DOCX** 파일을 안전하게 **로드**하는 데 필요한 정확한 코드와 실제 프로젝트에 적용할 수 있는 몇 가지 팁  
- 다른 경고 유형을 처리하거나 동일한 접근 방식으로 PDF를 로드하는 등 엣지 케이스 처리 방법  

외부 문서는 필요 없습니다—여기서 바로 모든 것을 확인할 수 있습니다.

## 사전 요구 사항

- Java 17 이상 (API는 이전 버전에서도 동작하지만 17이 가장 적합합니다)  
- 프로젝트에 추가된 Aspose.Words for Java 라이브러리 (`aspose-words-x.x.jar`)  
- Java 예외 처리에 대한 기본 이해  

위 조건을 갖췄다면, 바로 시작해봅시다.

![Diagram showing the flow of creating load options, setting a warning callback, and loading a DOCX file](/images/create-load-options-diagram.png){: .center-image alt="로드 옵션 생성 흐름도"}

## 1단계: Load Options 만들기 (DOCX 로드 방법)

먼저 **로드 옵션**을 **생성**해야 합니다. 이 객체는 Aspose.Words가 파일을 열 때 어떻게 동작할지를 알려줍니다. 마치 DOCX를 보기 전에 라이브러리에 전달하는 일련의 지시문과 같습니다.

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

그냥 `new Document("file.docx")`만 호출하면 안 될까요? `LoadOptions` 없이 하면 누락된 폰트와 같은 경고에 대응할 수 없으며, 문서가 이미 로드된 뒤에야 문제를 알게 되어 특정 워크플로에서는 너무 늦을 수 있습니다.

## 2단계: 누락된 폰트를 감지하기 위한 Warning Callback 설정

이제 Aspose.Words가 경고를 발생시킬 때마다 호출되는 콜백을 연결합니다. 여기서는 `WarningType.FONT_SUBSTITUTION`에 관심이 있습니다.

```java
// Step 2: Register a warning callback
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // React only to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Missing font detected: " + info.getDescription());
        }
    }
});
```

주의할 점 몇 가지:

- **왜 콜백인가?** 로드 과정 중에 실행되므로 문서가 완전히 메모리에 올라오기 전에 로그를 남기거나 작업을 중단할 수 있습니다.  
- **왜 `WarningType.FONT_SUBSTITUTION`을 확인하나요?** 누락된 폰트 상황에 Aspose.Words가 사용하는 정확한 enum 값입니다. 필요에 따라 `TABLE_STRUCTURE` 등 다른 경고 유형도 동일하게 필터링할 수 있습니다.  
- **성능 팁:** 콜백은 가볍게 유지하세요. 무거운 I/O 작업은 피하고, 파일에 기록해야 한다면 메시지를 큐에 넣어 로드가 끝난 뒤 플러시하는 것이 좋습니다.

## 3단계: 구성된 옵션으로 DOCX 파일 로드

옵션과 콜백이 준비되었으면 이제 DOCX를 로드합니다. 이것이 **DOCX를 로드하는 방법**이며, 앞서 설정한 경고를 반영합니다.

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**내부에서 무슨 일이 일어나나요?** 파일이 스트리밍되는 동안 Aspose.Words는 각 폰트 참조를 검사합니다. 설치되지 않은 폰트를 발견하면 앞서 정의한 경고 콜백이 트리거됩니다. 콘솔에는 다음과 같은 출력이 나타납니다:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

배치 처리 중 서버에서 파일을 여러 개 다룰 때 이 즉각적인 피드백은 매우 유용합니다.

## 전체 작동 예제

모든 내용을 하나로 합친, IDE에 복사·붙여넣기 할 수 있는 독립 실행형 프로그램입니다.

```java
import com.aspose.words.*;

public class DetectMissingFonts {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register warning callback to detect missing fonts
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Missing font: " + info.getDescription());
                }
            }
        });

        // 3️⃣ Load the DOCX using the configured options
        try {
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            System.out.println("DOCX loaded – you can now work with it.");
        } catch (Exception ex) {
            System.err.println("Error loading DOCX: " + ex.getMessage());
        }
    }
}
```

**예상 출력**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

파일에 누락된 폰트가 없으면 콜백은 조용히 동작하고 “DOCX loaded” 라인만 표시됩니다.

## 전문가 팁 & 엣지 케이스

| 상황 | 해결 방법 |
|-----------|------------|
| **여러 개의 누락된 폰트** | 콜백이 각각 호출되므로 폰트당 한 줄씩 출력됩니다. 나중에 요약이 필요하면 `List<String>`에 모아두세요. |
| **다른 경고도 잡고 싶을 때** | `else if` 구문을 추가해 `WarningType.TABLE_STRUCTURE`, `WarningType.UNKNOWN_FILE_FORMAT` 등을 처리합니다. |
| **대용량 DOCX 파일 로드** | `LoadOptions.setLoadFormat(LoadFormat.DOCX)`를 사용해 형식을 명시하고 탐지 속도를 높이세요. |
| **웹 서비스에서 실행** | `System.out.println` 대신 콜백 내부에 로거(`SLF4J`, `Log4j`)를 주입하세요. |
| **런타임에 폰트 설치** | 누락된 폰트를 감지한 뒤 `GraphicsEnvironment.registerFont(...)`로 프로그램matically 로드하고 문서를 다시 로드할 수 있습니다. |

## “Try‑Catch만” 방법보다 이 접근법이 뛰어난 이유

많은 개발자가 `new Document(...)`를 `try‑catch`로 감싸서 예외가 발생하면 폰트가 누락됐다고 판단합니다. 그러나 Aspose.Words는 폰트 대체를 *경고*로 처리하므로 예외가 발생하지 않습니다. **로드 옵션**을 만들고 경고 콜백을 연결하면 성능을 희생하지 않으면서도 폰트 문제에 대한 확정적인 정보를 얻을 수 있습니다.

## 다음 단계

- **PDF에서 누락된 폰트 감지** – 동일한 `LoadOptions` 패턴을 사용하고 파일 경로와 로드 형식만 바꾸면 됩니다.  
- **폰트 자동 설치** – 콜백과 연동해 공유 저장소에서 누락된 폰트를 가져오는 스크립트를 작성하세요.  
- **다른 경고 유형 탐색** – Aspose.Words는 사용되지 않는 태그, 복잡한 테이블 등 다양한 경고를 제공하므로 활용해 보세요.  

실험해 보세요: 메모리 내 데이터를 다룰 때는 `Document` 생성자를 스트림(`new Document(InputStream, loadOptions)`)으로 교체하거나, 대규모 파이프라인을 위해 복합 패턴으로 여러 콜백을 체인할 수 있습니다.

---

### TL;DR

Java에서 **로드 옵션을 만들고**, 누락된 폰트를 **감지하는 콜백**을 설정한 뒤, **DOCX 파일을 안전하게 로드**하는 방법을 보여드렸습니다. 세 단계만 따라 하면 어떤 Aspose.Words 프로젝트에도 바로 적용할 수 있는 재사용 가능한 패턴을 얻게 됩니다.

다른 파일 형식에 대한 질문이 있거나 콜백을 특정 환경에 맞게 조정하고 싶다면 아래에 댓글을 남겨 주세요. 즐거운 코딩 되세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}