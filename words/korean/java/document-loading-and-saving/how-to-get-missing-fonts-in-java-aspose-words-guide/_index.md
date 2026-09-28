---
category: general
date: 2026-02-15
description: Aspose.Words를 사용하여 Java에서 Word 문서를 로드할 때 누락된 글꼴을 가져오는 방법을 배웁니다. 경고 콜백
  및 글꼴 대체 처리도 포함됩니다.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: ko
og_description: Aspose.Words를 사용한 Java에서 누락된 글꼴을 가져오는 방법. 경고 콜백, 글꼴 대체 처리 및 문서 처리
  모범 사례를 알아보세요.
og_title: Java에서 누락된 글꼴을 가져오는 방법 – Aspose.Words 가이드
tags:
- Aspose.Words
- Java
- Font Management
title: Java에서 누락된 글꼴을 가져오는 방법 – Aspose.Words 가이드
url: /ko/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 누락된 폰트 가져오기 – Aspose.Words 가이드

Java에서 Word 문서를 열었을 때 이상한 폰트 대체가 표시되고 **누락된 폰트를 어떻게 가져올까** 하는 생각을 해본 적이 있나요? 여러분만 그런 상황을 겪는 것이 아닙니다. 많은 기업 애플리케이션에서 누락된 폰트 경고는 보고서, 계약서, 마케팅 자료 등의 시각적 완성도를 깨뜨릴 수 있습니다.

좋은 소식은? Aspose.Words는 콜백을 통해 이러한 경고를 캡처할 수 있는 깔끔한 방법을 제공하므로, 문서가 렌더링되기 전에 로그를 남기거나, 대체 폰트를 적용하거나, 사용자에게 알릴 수 있습니다. 이 튜토리얼에서는 **누락된 폰트를 어떻게 가져오는지**를 보여주는 완전한 실행 가능한 예제를 단계별로 살펴보고, 콜백이 왜 중요한지 설명하며, 실제 프로젝트에서 필요할 수 있는 몇 가지 엣지 케이스 트릭도 다룹니다.

> **프로 팁:** 이미 Aspose.Words 22.12 이상을 사용 중이라면, 아래에 표시된 API는 별도의 설정 없이 바로 사용할 수 있습니다.

---

![Aspose.Words 경고 콜백을 사용하여 누락된 폰트를 가져오는 방법을 보여주는 다이어그램](how-to-get-missing-fonts-diagram.png "누락된 폰트 가져오기 다이어그램")

## 이 튜토리얼에서 다루는 내용

- **Java LoadOptions warning callback**를 설정하여 폰트 대체 경고를 캡처하기.  
- 경고를 필터링하여 누락된 폰트와 관련된 것만 표시하기.  
- 대체된 폰트와 교체된 폰트를 명확하고 사람이 읽기 쉬운 보고서 형태로 출력하기.  
- 대용량 문서 처리, 경고 수준 맞춤 설정, 그리고 솔루션을 더 큰 처리 파이프라인에 통합하는 팁.

이 가이드를 끝까지 따라오면, **누락된 폰트를 어떻게 가져오는지**라는 질문에 바로 실행 가능한 코드 스니펫과 기본 메커니즘에 대한 확실한 이해를 가지고 답변할 수 있게 됩니다.

### 사전 요구 사항

- Java 8 이상이 설치되어 있어야 합니다.  
- Aspose.Words for Java 라이브러리(공식 사이트에서 다운로드하거나 Maven/Gradle을 통해 추가).  
- 머신에 설치되지 않은 폰트를 참조하는 Word 문서(예: `MissingFont.docx`).  

위 항목 중 하나라도 없으면, 지금 라이브러리를 받아보세요—Maven에 추가하는 것은 다음과 같이 간단합니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## 단계 1: 폰트 대체 경고를 저장할 컬렉션 준비하기

문서를 로드하기 전에 Aspose.Words가 발생시키는 모든 경고를 저장할 장소가 필요합니다. `ArrayList<WarningInfo>`는 순서를 유지하고 나중에 반복할 수 있기 때문에 적합합니다.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*왜 중요한가:* 경고 콜백은 하나의 파일에 대해 수십 번 호출될 수 있습니다—각 누락된 글리프, 각 임베드된 이미지 문제 등을 생각해 보세요. 먼저 수집함으로써 로딩 단계는 빠르게 유지하고, 처리는 제어된 루프로 연기할 수 있습니다.

---

## 단계 2: 경고 콜백과 함께 LoadOptions 구성하기

Aspose.Words는 `IWarningCallback`을 연결할 수 있게 해줍니다. 콜백 내부에서 Step 1에서 만든 리스트에 모든 `WarningInfo`를 추가합니다.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*설명:* `warning` 메서드는 문서 로딩 중 **동기적으로** 호출됩니다. `WarningInfo`를 `fontWarnings`에 단순히 추가함으로써 로드를 늦출 수 있는 파일 로그와 같은 무거운 I/O를 피할 수 있습니다. 이 패턴—수집 후 처리—은 대량 경고를 다룰 때 권장되는 방법입니다.

---

## 단계 3: 구성된 옵션으로 문서 로드하기

이제 실제로 Word 파일을 읽습니다. 문서에 설치되지 않은 폰트가 포함되어 있으면, Aspose.Words가 자동으로 대체하고 방금 연결한 경고 콜백을 호출합니다.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*내부 동작:* Aspose.Words는 파일의 폰트 테이블을 파싱하고 호스트 OS에 설치된 폰트와 비교합니다. 누락된 항목마다 `WarningSource.FontSubstitution`을 가진 `WarningInfo`를 생성합니다. 이 소스가 누락된 폰트 경고를 구분하는 키가 됩니다.

---

## 단계 4: 폰트 대체 경고만 필터링하고 표시하기

로드 후 `fontWarnings`에는 다양한 메시지(예: 사용 중단된 기능, 이미지 문제)가 섞여 있을 수 있습니다. 우리는 누락된 폰트에만 관심이 있으므로 리스트를 순회하며 간결한 보고서를 출력합니다.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**샘플 출력**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*왜 유용한가:* `description` 필드는 문서가 요청한 폰트를 알려주고, `additionalInfo`는 Aspose.Words가 실제로 사용한 폰트를 알려줍니다. 이 데이터를 바탕으로 다음을 할 수 있습니다:

- 사용자에게 누락된 폰트를 설치하도록 안내하기.  
- 프로그램matically 대체 폰트를 문서에 임베드하기 (`doc.getFontInfos().add(...)`).  
- 컴플라이언스 감사를 위해 이벤트를 로그에 남기기.

---

## 엣지 케이스 및 일반적인 변형 처리

### 1. 폰트와 무관한 경고 억제

폰트와 관련된 메시지만 원한다면, 콜백을 더 엄격하게 설정할 수 있습니다:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

대용량 배치를 처리할 때 메모리 사용량을 줄여줍니다.

### 2. 경고 심각도 조정

Aspose.Words는 `WarningType`으로 경고를 분류합니다. 누락된 폰트의 경우 보통 `WarningType.FontSubstitution`이 표시됩니다. 이를 오류로 처리해야 한다면(예: 로드 중단) 콜백 내부에서 예외를 발생시킬 수 있습니다:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. 파일 대신 스트림 사용하기

때때로 문서는 데이터베이스나 HTTP 요청을 통해 들어옵니다. 동일한 방법을 `InputStream`과 함께 사용할 수 있습니다:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

로드 후 스트림을 반드시 닫아야 합니다.

### 4. 사용자 정의 폰트 폴더 사용하기

공유 드라이브에 기업 폰트 컬렉션이 있다면, Aspose.Words가 해당 폴더를 참조하도록 지정하세요:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

이제 라이브러리는 시스템 폰트로 대체하기 *전에* 해당 폴더를 먼저 확인하므로, 누락된 폰트 경고 수가 크게 감소합니다.

---

## 전체 작업 예제

모든 내용을 종합하면, 다음은 어떤 Java 프로젝트에도 바로 넣어 사용할 수 있는 독립형 클래스입니다:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

이 프로그램을 실행하면 Aspose.Words가 교체한 모든 폰트의 정리된 목록을 확인할 수 있습니다. 추가 라이브러리도, 숨겨진 마법도 없습니다—순수 Java와 **Aspose.Words 누락 폰트** API만으로 가능합니다.

---

## 결론

우리는 Java 환경에서 Aspose.Words를 사용해 **누락된 폰트를 어떻게 가져오는지**라는 핵심 질문에 답했습니다. `LoadOptions` 경고 콜백을 연결하고, `WarningInfo` 객체를 수집하며, `FontSubstitution` 소스를 필터링함으로써 렌더링이 시작되기 전에 폰트 관련 문제를 완전히 파악할 수 있습니다. 이 접근 방식은 단일 파일 유틸리티부터 대규모 배치 프로세서까지 확장 가능하며, 사용자 정의 폰트 폴더, 심각도 처리, 스트림 기반 입력 등을 유연하게 지원합니다.

다음 단계는? 대체 폰트를 문서에 직접 임베드(`doc.getFontInfos().add(...)`)하여 최종 파일을 완전히 자체 포함하도록 하거나, 경고 보고서를 모니터링 대시보드에 통합해 보세요. 또한 **document processing Java**, **Aspose.Words font substitution warning**, **Java LoadOptions warning callback**과 같은 관련 주제를 탐색하면 전문성을 더욱 높일 수 있습니다.

코딩 즐겁게 하시고, 문서가 언제나 기대한 폰트로 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}