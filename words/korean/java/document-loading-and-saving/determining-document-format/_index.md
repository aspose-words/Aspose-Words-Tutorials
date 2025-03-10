---
title: Java용 Aspose.Words에서 문서 형식 결정
linktitle: 문서 형식 결정
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words를 사용하여 Java에서 문서 형식을 감지하는 방법을 알아보세요. DOC, DOCX 등을 식별하세요. 파일을 효율적으로 정리하세요.
weight: 25
url: /ko/java/document-loading-and-saving/determining-document-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 문서 형식 결정


## Aspose.Words for Java에서 문서 형식 결정 소개

Java에서 문서 처리를 할 때는 다루는 파일의 형식을 결정하는 것이 중요합니다. Aspose.Words for Java는 문서 형식을 식별하는 강력한 기능을 제공하며, 이 과정을 안내해 드리겠습니다.

## 필수 조건

시작하기에 앞서 다음과 같은 전제 조건이 충족되었는지 확인하세요.

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- 시스템에 Java Development Kit(JDK) 설치
- Java 프로그래밍에 대한 기본 지식

## 1단계: 디렉토리 설정

먼저, 우리는 파일을 효과적으로 정리하기 위해 필요한 디렉토리를 설정해야 합니다. 우리는 다양한 문서 유형에 대한 디렉토리를 만들 것입니다.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// 아직 존재하지 않으면 디렉토리를 만듭니다.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

지원되는 문서 유형, 알려지지 않은 문서 유형, 암호화된 문서 유형, 97년 이전 문서 유형에 대한 디렉토리를 만들었습니다.

## 2단계: 문서 형식 감지

이제 디렉토리에 있는 문서의 형식을 감지해 보겠습니다. 이를 위해 Aspose.Words for Java를 사용하겠습니다.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // 문서 유형 표시
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // 필요에 따라 다른 문서 형식에 대한 사례를 추가합니다.
    }

    // 암호화된 문서 처리
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // 다른 문서 유형 처리
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

이 코드 조각에서는 파일을 반복하고, 형식을 감지하고, 이를 해당 디렉터리로 구성합니다.

## Aspose.Words for Java에서 문서 형식을 결정하기 위한 완전한 소스 코드

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // 아직 존재하지 않으면 디렉토리를 만듭니다.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // 문서 유형 표시
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## 결론

Aspose.Words for Java에서 문서 형식을 결정하는 것은 효율적인 문서 처리에 필수적입니다. 이 가이드에 설명된 단계를 통해 문서 유형을 식별하고 Java 애플리케이션에서 적절히 처리할 수 있습니다.

## 자주 묻는 질문

### Java용 Aspose.Words를 어떻게 설치하나요?

 Aspose.Words for Java는 다음에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/java/)제공된 설치 지침을 따르세요.

### 지원되는 문서 형식은 무엇입니까?

Aspose.Words for Java는 DOC, DOCX, RTF, HTML 등 다양한 문서 형식을 지원합니다. 전체 목록은 설명서를 참조하세요.

### Aspose.Words for Java를 사용하여 암호화된 문서를 어떻게 감지할 수 있나요?

 당신은 사용할 수 있습니다`FileFormatUtil.detectFileFormat()` 이 가이드에서 설명하는 대로 암호화된 문서를 감지하는 방법입니다.

### 이전 문서 형식을 사용할 때 제한이 있나요?

MS Word 6 또는 Word 95와 같은 이전 문서 형식은 기능 및 최신 애플리케이션과의 호환성 측면에서 제한이 있을 수 있습니다. 필요한 경우 이러한 문서를 업그레이드하거나 변환하는 것을 고려하세요.

### Java 애플리케이션에서 문서 형식 감지를 자동화할 수 있습니까?

네, 제공된 코드를 Java 애플리케이션에 통합하여 문서 형식 감지를 자동화할 수 있습니다. 이를 통해 감지된 형식에 따라 문서를 처리할 수 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
