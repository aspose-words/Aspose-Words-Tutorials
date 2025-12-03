{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
---
"date": "2025-03-29"
"description": "Dowiedz się, jak zoptymalizować zapisywanie dokumentów za pomocą Aspose.Words dla Pythona przy użyciu formatu przepływu XAML i wywołań zwrotnych postępu. Zwiększ wydajność zarządzania dokumentami."
"title": "Optymalizacja zapisywania dokumentów w Pythonie&#58; przepływ i wywołania zwrotne postępu w Aspose.Words XAML"
"url": "/pl/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---

# Jak zoptymalizować zapisywanie dokumentów w Pythonie przy użyciu Aspose.Words: XAML Flow i wywołania zwrotne postępu

## Wstęp

Czy chcesz efektywnie zarządzać konwersjami dokumentów za pomocą Pythona? Masz problemy z obsługą obrazów i śledzeniem postępów podczas zapisywania dokumentów? Ten samouczek przeprowadzi Cię przez optymalizację zapisywania dokumentów za pomocą Aspose.Words dla Pythona, skupiając się na dwóch potężnych funkcjach: `XamlFlowSaveOptions` z folderem obrazów i funkcją wywołania zwrotnego postępu zapisywania dokumentu.

Ten kompleksowy przewodnik doskonale sprawdzi się dla programistów pragnących usprawnić procesy przetwarzania dokumentów za pomocą biblioteki Aspose.Words.

**Czego się nauczysz:**
- Jak zapisać dokument w formacie przepływu XAML, zarządzając jednocześnie zasobami obrazów.
- Wprowadzanie wywołań zwrotnych postępu podczas zapisywania dokumentu w celu zapobiegania długim operacjom.
- Konfigurowanie i instalowanie Aspose.Words dla języka Python w środowisku programistycznym.
- Praktyczne zastosowania tych funkcji w systemach zarządzania dokumentacją.

Zanim zaczniemy kodować, zapoznajmy się z wymaganiami wstępnymi!

## Wymagania wstępne

Zanim zaczniesz, upewnij się, że masz następujące rzeczy:

### Wymagane biblioteki i wersje
- **Aspose.Words dla Pythona**: Upewnij się, że masz wersję 23.3 lub nowszą.
- **Pyton**:Zalecana jest wersja 3.6 lub nowsza.

### Wymagania dotyczące konfiguracji środowiska
- Edytor kodu, taki jak VSCode lub PyCharm.
- Podstawowa znajomość programowania w języku Python.

### Wymagania wstępne dotyczące wiedzy
- Znajomość zagadnień związanych z przetwarzaniem dokumentów.
- Zrozumienie obsługi plików i zarządzania katalogami w Pythonie.

## Konfigurowanie Aspose.Words dla Pythona

Aby zacząć używać Aspose.Words, musisz zainstalować go za pomocą pip. Otwórz terminal lub wiersz poleceń i uruchom:

```bash
pip install aspose-words
```

### Etapy uzyskania licencji
1. **Bezpłatna wersja próbna**:Uzyskaj dostęp do tymczasowej licencji [Tutaj](https://purchase.aspose.com/temporary-license/) w celach testowych.
2. **Zakup**:Do długotrwałego użytkowania należy zakupić licencję [Tutaj](https://purchase.aspose.com/buy).
3. **Podstawowa inicjalizacja i konfiguracja**:
   - Załaduj swój dokument za pomocą `aw.Document()`.
   - Skonfiguruj opcje zapisu według potrzeb.

## Przewodnik wdrażania

W tej sekcji zostanie przeprowadzony proces implementacji dwóch głównych funkcji tego samouczka: opcji XamlFlowSaveOptions z folderem obrazów i wywołania zwrotnego postępu zapisywania dokumentu.

### Funkcja 1: XamlFlowSaveOptions z folderem obrazów

#### Przegląd
Ta funkcja umożliwia zapisanie dokumentu w formacie przepływu XAML, określając jednocześnie folder obrazów i alias. Jest idealna do wydajnego zarządzania dużymi dokumentami z osadzonymi obrazami.

#### Etapy wdrażania

##### Krok 1: Importuj niezbędne biblioteki
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### Krok 2: Zdefiniuj klasę wywołania zwrotnego ImageUriPrinter
Ta klasa zlicza i przekierowuje strumienie obrazów do określonego folderu aliasu podczas konwersji.

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # typ: Lista[str]

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
**Kluczowe opcje konfiguracji:**
- `images_folder`: Określa katalog, w którym zapisywane są obrazy.
- `images_folder_alias`: Ustawia ścieżkę aliasu używaną podczas konwersji dokumentu.

##### Porady dotyczące rozwiązywania problemów
- Przed uruchomieniem kodu upewnij się, że wszystkie katalogi istnieją, aby uniknąć błędów informujących o tym, że plik nie został znaleziony.
- Sprawdź uprawnienia zapisu w katalogu wyjściowym.

### Funkcja 2: Wywołanie zwrotne postępu zapisywania dokumentu

#### Przegląd
Ta funkcja zarządza procesem zapisywania za pomocą wywołania zwrotnego postępu, umożliwiając anulowanie długotrwałych operacji zapisywania.

#### Etapy wdrażania

##### Krok 1: Zdefiniuj klasę SavingProgressCallback
Klasa monitoruje czas zapisywania dokumentu i anuluje zapis, jeśli przekroczy on określony limit czasowy.

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # Maksymalny dozwolony czas trwania w sekundach.

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
**Kluczowe opcje konfiguracji:**
- `save_format`: Wybierz pomiędzy XAML_FLOW i XAML_FLOW_PACK.
- `progress_callback`:Monitoruje postęp zapisywania w celu obsługi długotrwałych operacji.

##### Porady dotyczące rozwiązywania problemów
- Regulować `max_duration` na podstawie rozmiaru i złożoności dokumentu.
- Obsługuj wyjątki w sposób elegancki, aby dostarczać informacyjne komunikaty o błędach.

## Zastosowania praktyczne

Oto kilka przykładów rzeczywistego wykorzystania tych funkcji:
1. **Systemy zarządzania dokumentacją**:Skuteczne zarządzanie dużymi dokumentami z osadzonymi obrazami poprzez określenie folderów obrazów, co zwiększa wydajność i organizację.
2. **Zautomatyzowane narzędzia do raportowania**:Używaj wywołań zwrotnych postępu, aby mieć pewność, że raporty będą generowane w akceptowalnych ramach czasowych, co poprawi komfort użytkowania.
3. **Sieci dystrybucji treści**:Usprawnij konwersję dokumentów do dystrybucji internetowej, jednocześnie efektywnie zarządzając zasobami.

## Rozważania dotyczące wydajności

Aby zoptymalizować wydajność podczas używania Aspose.Words z Pythonem:
- **Zarządzanie pamięcią**:Monitoruj wykorzystanie zasobów i efektywnie zarządzaj pamięcią, usuwając obiekty po użyciu.
- **Operacje wejścia/wyjścia plików**:Zminimalizuj operacje odczytu/zapisu plików, aby zwiększyć szybkość.
- **Przetwarzanie wsadowe**:W miarę możliwości przetwarzaj dokumenty w partiach, aby ograniczyć koszty ogólne.

## Wniosek

W tym samouczku przyjrzeliśmy się sposobowi optymalizacji zapisywania dokumentów za pomocą Aspose.Words dla Pythona przy użyciu XAML Flow i wywołań zwrotnych postępu. Dzięki wdrożeniu tych funkcji możesz zwiększyć wydajność przepływów pracy przetwarzania dokumentów, skutecznie zarządzać zasobami i zapewnić terminowe operacje.
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}