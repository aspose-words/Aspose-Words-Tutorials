---
"date": "2025-03-29"
"description": "XAML 플로우 포맷과 진행률 콜백을 사용하여 Aspose.Words for Python에서 문서 저장을 최적화하는 방법을 알아보세요. 문서 관리 효율성을 높여 보세요."
"title": "Python에서 문서 저장 최적화하기&#58; Aspose.Words XAML 흐름 및 진행 콜백"
"url": "/ko/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---
{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
# Aspose.Words를 사용하여 Python에서 문서 저장을 최적화하는 방법: XAML 흐름 및 진행 콜백

## 소개

Python을 사용하여 문서 변환을 효율적으로 관리하고 싶으신가요? 문서 저장 중 이미지 처리 및 진행 상황 추적에 어려움을 겪고 계신가요? 이 튜토리얼은 Python용 Aspose.Words를 사용하여 문서 저장을 최적화하는 방법을 안내하며, 두 가지 강력한 기능에 중점을 둡니다. `XamlFlowSaveOptions` 이미지 폴더와 문서 저장 진행 콜백이 포함되어 있습니다.

이 포괄적인 가이드는 Aspose.Words 라이브러리를 사용하여 문서 처리 워크플로를 개선하고자 하는 개발자에게 적합합니다.

**배울 내용:**
- 이미지 리소스를 관리하면서 XAML 흐름 형식으로 문서를 저장하는 방법.
- 긴 작업이 소요되는 것을 방지하기 위해 문서를 저장하는 동안 진행 상황 콜백을 구현합니다.
- 개발 환경에서 Python용 Aspose.Words를 설정하고 구성합니다.
- 문서 관리 시스템에서 이러한 기능을 실제로 적용한 사례입니다.

코딩을 시작하기 전에 필수 조건을 살펴보겠습니다!

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

### 필수 라이브러리 및 버전
- **파이썬을 위한 Aspose.Words**: 버전 23.3 이상인지 확인하세요.
- **파이썬**: 버전 3.6 이상을 권장합니다.

### 환경 설정 요구 사항
- VSCode나 PyCharm과 같은 코드 편집기.
- 파이썬 프로그래밍에 대한 기본 지식.

### 지식 전제 조건
- 문서 처리 개념에 익숙함.
- Python에서의 파일 처리 및 디렉토리 관리에 대한 이해.

## Python용 Aspose.Words 설정

Aspose.Words를 사용하려면 pip를 통해 설치해야 합니다. 터미널이나 명령 프롬프트를 열고 다음을 실행하세요.

```bash
pip install aspose-words
```

### 라이센스 취득 단계
1. **무료 체험**: 임시 라이센스에 접근 [여기](https://purchase.aspose.com/temporary-license/) 테스트 목적으로.
2. **구입**: 장기 사용을 위해서는 라이센스를 구매하세요 [여기](https://purchase.aspose.com/buy).
3. **기본 초기화 및 설정**:
   - 다음을 사용하여 문서를 로드하세요. `aw.Document()`.
   - 필요에 따라 저장 옵션을 구성합니다.

## 구현 가이드

이 섹션에서는 이 튜토리얼의 두 가지 주요 기능인 이미지 폴더를 사용한 XamlFlowSaveOptions와 문서 저장 진행 콜백을 구현하는 과정을 안내합니다.

### 기능 1: 이미지 폴더가 있는 XamlFlowSaveOptions

#### 개요
이 기능을 사용하면 이미지 폴더와 별칭을 지정하여 XAML 플로우 형식으로 문서를 저장할 수 있습니다. 이미지가 포함된 대용량 문서를 효율적으로 관리하는 데 적합합니다.

#### 구현 단계

##### 1단계: 필요한 라이브러리 가져오기
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### 2단계: ImageUriPrinter 콜백 클래스 정의
이 클래스는 변환 중에 이미지 스트림을 계산하여 지정된 별칭 폴더로 리디렉션합니다.

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # 유형: List[str]

        def image_saving(self, args: aw.saving.ImageSavingArgs):
            self.resources.append(args.image_file_name)
            with open(f"{self.images_folder_alias}/{args.image_file_name}", "wb") as image_stream:
                args.image_stream = image_stream
            args.keep_image_stream_open = False

    def test_image_folder(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Rendering.docx")
        callback = self.ImageUriPrinter(YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias")

        options = aw.saving.XamlFlowSaveOptions()
        options.images_folder = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolder"
        options.images_folder_alias = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias"
        options.image_saving_callback = callback

        os.makedirs(options.images_folder_alias, exist_ok=True)
        
        doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.image_folder.xaml", options)

        for resource in callback.resources:
            print(f"{callback.images_folder_alias}/{resource}")
```
**주요 구성 옵션:**
- `images_folder`: 이미지가 저장되는 디렉토리를 지정합니다.
- `images_folder_alias`: 문서 변환 중에 사용되는 별칭 경로를 설정합니다.

##### 문제 해결 팁
- 파일을 찾을 수 없다는 오류를 방지하려면 코드를 실행하기 전에 모든 디렉토리가 있는지 확인하세요.
- 출력 디렉토리에서 쓰기 권한을 확인하세요.

### 기능 2: 문서 저장 진행 콜백

#### 개요
이 기능은 진행률 콜백을 사용하여 저장 프로세스를 관리하고, 장기 저장 작업을 취소할 수 있도록 해줍니다.

#### 구현 단계

##### 1단계: SavingProgressCallback 클래스 정의
클래스는 문서 저장 기간을 모니터링하고 지정된 시간 제한을 초과하면 취소합니다.

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # 허용되는 최대 기간(초)

        def notify(self, args: aw.saving.DocumentSavingArgs):
            canceled_at = datetime.now()
            elapsed_seconds = (canceled_at - self.saving_started_at).total_seconds()
            if elapsed_seconds > self.max_duration:
                raise OperationCanceledException(f"estimated_progress = {args.estimated_progress}; canceled_at = {canceled_at}")

    def test_progress_callback(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        parameters = [
            (aw.SaveFormat.XAML_FLOW, "xamlflow"),
            (aw.SaveFormat.XAML_FLOW_PACK, "xamlflowpack"),
        ]

        for save_format, ext in parameters:
            doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Big document.docx")
            save_options = aw.saving.XamlFlowSaveOptions(save_format)
            save_options.progress_callback = self.SavingProgressCallback()

            try:
                doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.progress_callback.{ext}", save_options)
            except OperationCanceledException as e:
                print(e)
```
**주요 구성 옵션:**
- `save_format`: XAML_FLOW와 XAML_FLOW_PACK 중에서 선택하세요.
- `progress_callback`: 장기 작업을 처리하기 위해 진행 상황을 저장하는 모니터입니다.

##### 문제 해결 팁
- 조정하다 `max_duration` 문서 크기와 복잡성에 따라 다릅니다.
- 유익한 오류 메시지를 제공하기 위해 예외를 우아하게 처리합니다.

## 실제 응용 프로그램

이러한 기능의 실제 사용 사례는 다음과 같습니다.
1. **문서 관리 시스템**: 이미지 폴더를 지정하여 내장된 이미지가 있는 대용량 문서를 효율적으로 관리하고, 성능과 구성을 향상시킵니다.
2. **자동 보고 도구**: 진행 콜백을 사용하여 허용 가능한 시간 프레임 내에서 보고서가 생성되도록 하여 사용자 경험을 개선합니다.
3. **콘텐츠 배포 네트워크**: 리소스를 효과적으로 관리하면서 웹 배포를 위한 문서 변환을 간소화합니다.

## 성능 고려 사항

Python에서 Aspose.Words를 사용할 때 성능을 최적화하려면:
- **메모리 관리**: 사용 후 객체를 삭제하여 리소스 사용량을 모니터링하고 메모리를 효율적으로 관리합니다.
- **파일 I/O 작업**: 파일 읽기/쓰기 작업을 최소화하여 속도를 향상시킵니다.
- **일괄 처리**: 가능하면 일괄적으로 문서를 처리하여 간접비를 줄입니다.

## 결론

이 튜토리얼에서는 XAML Flow와 진행률 콜백을 사용하여 Aspose.Words for Python에서 문서 저장을 최적화하는 방법을 살펴보았습니다. 이러한 기능을 구현하면 문서 처리 워크플로의 효율성을 높이고, 리소스를 효과적으로 관리하며, 적시에 작업을 수행할 수 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}