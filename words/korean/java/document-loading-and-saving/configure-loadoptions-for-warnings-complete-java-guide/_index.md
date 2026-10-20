---
category: general
date: 2026-06-30
description: Aspose.Words Java에서 경고에 대한 LoadOptions를 구성합니다. 글꼴 대체 및 기타 로드 옵션 경고에 대한
  경고 콜백을 설정하는 방법을 배웁니다.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: ko
og_description: Aspose.Words Java에서 경고를 위한 LoadOptions를 구성합니다. 이 가이드는 경고 콜백을 사용하여
  글꼴 대체 알림을 캡처하는 방법을 보여줍니다.
og_title: 경고를 위한 LoadOptions 구성 – Java 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: 경고를 위한 LoadOptions 구성 – 완전한 Java 가이드
url: /ko/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 경고에 대한 LoadOptions 구성 – 완전한 Java 가이드

Aspose.Words for Java로 Word 문서를 열 때 **경고에 대한 LoadOptions 구성**이 필요했던 적이 있나요? 혼자가 아닙니다. 많은 개발자들이 누락된 폰트가 조용히 대체되어 최종 PDF가 브랜드와 맞지 않게 되는 문제에 부딪힙니다. 좋은 소식은? `LoadOptions`에 **Java 경고 콜백**을 연결하면 발생하는 즉시 모든 폰트 대체 알림을 잡을 수 있습니다.

이 튜토리얼에서는 콜백을 설정하는 방법을 보여줄 뿐만 아니라 *왜* 각 요소가 중요한지도 설명하는 실습 예제를 단계별로 진행합니다. 마지막까지 하면 **폰트 경고를 처리**하고, 로그를 남기거나, 실시간으로 폰트를 교체하는 방법을 알게 됩니다—추측이 필요 없습니다.

## 얻을 수 있는 내용

- 모든 폰트 대체 경고를 출력하는 완전 실행 가능한 Java 프로그램.
- **Aspose.Words 폰트 대체** 메커니즘에 대한 이해.
- 대규모 프로젝트를 위한 경고 처리 맞춤 팁.
- **문서 로딩 옵션**에 대한 통찰과 언제 조정해야 하는지에 대한 정보.

> **전제 조건:** Java 8+ 및 Aspose.Words for Java 라이브러리(버전 23.9 이상). 다른 외부 종속성은 필요하지 않습니다.

---

## 단계 1: 경고에 대한 LoadOptions 구성

먼저 경고를 보고하도록 설정된 `LoadOptions` 인스턴스가 필요합니다. `LoadOptions`를 Aspose.Words에 파일을 열기 전에 전달하는 도구 상자라고 생각하면 됩니다.

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**왜 중요한가:**  
`LoadOptions`는 라이브러리가 문서를 읽는 방식을 제어합니다. `IWarningCallback`을 할당하면 누락된 폰트와 같이 주목할 만한 상황이 발생할 때마다 Aspose.Words가 여러분의 코드를 호출하도록 지정합니다. 이 설정이 없으면 라이브러리는 폰트를 조용히 대체하고 여러분은 이를 전혀 알 수 없습니다.

> **프로 팁:** *모든* 경고를 캡처하고 싶다면 `if` 검사를 제거하세요. 여기서는 가장 흔한 레이아웃 문제인 폰트 이슈에 집중합니다.

---

## 단계 2: 구성된 옵션으로 문서 로드

콜백이 준비되었으니 동일한 `LoadOptions`를 사용해 `.docx`(또는 지원되는 다른 형식)를 로드합니다. 여기서 **문서 로딩 옵션**이 실제로 적용됩니다.

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**내부 동작:**  
Aspose.Words가 `input.docx`를 파싱할 때 폰트 테이블을 스캔합니다. 문서에 참조된 폰트가 호스트 머신에 설치되어 있지 않으면 엔진은 `FONT_SUBSTITUTION` 경고를 발생시키고, 앞서 정의한 콜백을 즉시 호출합니다.

---

## 단계 3: 문서 저장 – 경고는 이미 출력됨

문서 저장은 간단하지만 콜백이 올바르게 작동했는지 확인할 수 있는 순간이기도 합니다. 모든 경고는 로드 단계에서 이미 출력되었으므로 저장 작업은 정리 역할만 합니다.

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**예상 콘솔 출력:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

아무 것도 보이지 않는다면, 문서에 설치된 폰트만 사용했거나 콜백이 제대로 연결되지 않은 것입니다—단계 1을 다시 확인하세요.

---

## 단계 4: 콜백을 **폰트 경고를 우아하게 처리**하도록 확장

콘솔에 출력하는 것은 데모에는 충분하지만, 실제 코드에서는 파일에 로그를 남기거나 알림을 보내거나 프로그래밍 방식으로 폰트를 교체하는 등 더 풍부한 처리가 필요합니다.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**왜 이렇게 하는가:**  
로그 파일은 특히 문서 배치를 처리할 때 사후 분석에 유용합니다. 선택적인 대체 블록은 **경고에 대한 LoadOptions 구성**과 동시에 기업 폰트 정책을 적용하는 방법을 보여줍니다.

---

## 고급: 다른 **Aspose.Words 폰트 대체** 시나리오 제어

경고 콜백은 누락된 폰트에만 국한되지 않습니다. 다음과 같은 경우도 잡을 수 있습니다:

- **지원되지 않는 유니코드 문자** (`WarningType.UNSUPPORTED_CHAR`).
- **복합 스크립트 문제** (`WarningType.COMPLEX_SCRIPT`).

`if` 문을 다음과 같이 확장하면 됩니다:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

이렇게 하면 다국어 문서에 대한 견고한 솔루션이 됩니다—글로벌 애플리케이션에서 흔히 마주치는 엣지 케이스이기 때문입니다.

---

## 전체 작동 예제

아래는 완전한 실행 가능한 프로그램입니다. Java IDE에 붙여넣고 `YOUR_DIRECTORY` 자리표시자를 실제 경로로 교체한 뒤 *Run*을 누르세요.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### 예상 결과

- 콘솔에 폰트 대체 경고가 출력됩니다.
- `font-warnings.log`에 타임스탬프가 포함된 목록이 저장됩니다(옵션 로그를 사용한 경우).
- `output.docx`가 대체된 폰트와 함께 저장되어, 정의한 폰트 폴백과 일치합니다.

---

## 흔히 발생하는 함정 & 해결 방법

| 함정 | 발생 원인 | 해결 방법 |
|------|----------|----------|
| **경고가 전혀 나타나지 않음** | 콜백이 연결되지 않았거나 문서에 설치된 폰트만 사용됨. | `loadOptions.setWarningCallback(...)`가 **문서를 로드하기 전에** 호출됐는지 확인하세요. |
| `input.docx`에 대한 **FileNotFoundException** | 경로가 잘못됐거나 파일이 프로젝트에 포함되지 않음. | 절대 경로를 사용하거나 파일을 프로젝트의 `resources` 폴더에 배치하세요. |
| **수천 개 문서 처리 시 성능 저하** | 각 경고마다 디스크에 과도하게 로그를 남김. | 로그를 버퍼링해 배치로 기록하거나, 중요한 경고만 로그하도록 제한하세요. |
| **폴백을 지정했음에도 예상치 못한 폰트 대체** | 대체 설정이 충분히 일찍 적용되지 않음. | 문서를 로드하기 **전에** 대체 설정을 적용하거나, 전역적으로 `FontSettings.setSubstitutionSettings`를 사용하세요. |

---

## 다음 단계

이제 **경고에 대한 LoadOptions 구성**을 마스터했으니, 다음 주제들을 살펴보세요:

- **배치 처리**: 디렉터리의 문서를 순회하면서 모든 폰트 경고를 하나의 보고서로 집계.
- **맞춤 폰트 제공자**: 로컬 OS 대신 네트워크 공유나 임베디드 리소스에서 폰트를 로드.
- **Log4j**와 같은 로깅 프레임워크와 통합해 엔터프라이즈 수준 추적성 확보.
- `LoadFormat` 자동 감지나 보호된 파일에 대한 `Password` 처리 등 다른 **문서 로딩 옵션** 탐색.

이 모든 내용은 동일한 패턴—`LoadOptions` 객체를 생성하고, 적절한 콜백을 연결하고, Aspose.Words가 무거운 작업을 수행하도록—에 기반합니다.

---

## 결론

우리는 Aspose.Words for Java에서 **경고에 대한 LoadOptions 구성**, **Java 경고 콜백 설정**, 그리고 해당 정보를 활용해 **폰트 경고를 지능적으로 처리**하는 방법을 깊이 있게 살펴보았습니다. 코드는 간결하고 개념은 명확하며, 이제 지원되지 않는 문자나 복합 스크립트와 같은 다른 시나리오에도 경고 처리를 확장할 탄탄한 기반을 갖추었습니다.

코드를 실행해 보고, 기업 폰트에 맞게 대체 테이블을 조정해 보세요. 조용히 일어나던 폰트 교체가 사라지는 것을 확인할 수 있을 겁니다. 즐거운 코딩 되세요!

--- 

![Diagram showing the flow of configuring LoadOptions for warnings, loading a document, capturing font substitution events, and saving the output](configure-loadoptions-for-warnings-diagram.png "Configure LoadOptions for warnings flow")


## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 다양한 구현 방식을 탐색할 수 있습니다.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Load RTF Documents with Configuring RTF Load Options in Aspose.Words for Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}