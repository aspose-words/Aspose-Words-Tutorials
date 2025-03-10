---
title: Zmniejsz rozmiar pliku PDF za pomocą funkcji Skaluj czcionki WMF do rozmiaru metapliku
linktitle: Zmniejsz rozmiar pliku PDF za pomocą funkcji Skaluj czcionki WMF do rozmiaru metapliku
second_title: Aspose.Words API przetwarzania dokumentów
description: Przewodnik krok po kroku pokazujący, jak zmniejszyć rozmiar pliku PDF, skalując czcionki WMF do rozmiaru metapliku podczas konwersji do pliku PDF za pomocą Aspose.Words dla platformy .NET.
weight: 10
url: /pl/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zmniejsz rozmiar pliku PDF za pomocą funkcji Skaluj czcionki WMF do rozmiaru metapliku

## Wstęp

Podczas pracy z plikami PDF, zwłaszcza tymi generowanymi z dokumentów Word zawierających grafikę WMF (Windows Metafile), zarządzanie rozmiarem może stać się kluczowym aspektem obsługi dokumentów. Jednym ze sposobów kontrolowania rozmiaru pliku PDF jest dostosowanie sposobu renderowania czcionek WMF w dokumencie. W tym samouczku zbadamy, jak zmniejszyć rozmiar pliku PDF, skalując czcionki WMF do rozmiaru metapliku za pomocą Aspose.Words dla .NET.

## Wymagania wstępne

Zanim przejdziesz do dalszych kroków, upewnij się, że masz następujące rzeczy:

1. Aspose.Words dla .NET: Upewnij się, że masz zainstalowaną bibliotekę Aspose.Words. Jeśli nie, możesz[pobierz tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: W tym samouczku przyjęto założenie, że masz skonfigurowane środowisko programistyczne .NET (np. Visual Studio), w którym możesz pisać i wykonywać kod C#.
3. Podstawowa znajomość programowania .NET: Znajomość podstawowych koncepcji programowania .NET i składni języka C# będzie pomocna.
4. Dokument Word z grafiką WMF: Będziesz potrzebować dokumentu Word zawierającego grafikę WMF. Możesz użyć własnego dokumentu lub utworzyć go do testów.

## Importuj przestrzenie nazw

Najpierw musisz zaimportować niezbędne przestrzenie nazw do swojego projektu C#. To da ci dostęp do klas i metod wymaganych do pracy z Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Załaduj dokument Word

 Aby rozpocząć, załaduj dokument Word zawierający grafikę WMF. Można to zrobić za pomocą`Document` klasa z Aspose.Words.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Załaduj dokument
Document doc = new Document(dataDir + "WMF with text.docx");
```

 Tutaj,`dataDir` jest symbolem zastępczym dla ścieżki katalogu dokumentów. Tworzymy wystąpienie`Document` klasa poprzez przekazanie ścieżki do pliku Word. To ładuje dokument do pamięci, gotowy do dalszego przetwarzania.

## Krok 2: Skonfiguruj opcje renderowania metaplików

 Następnie musisz skonfigurować opcje renderowania metapliku. Dokładniej, ustaw`ScaleWmfFontsToMetafileSize`nieruchomość do`false`. Kontroluje, czy czcionki WMF są skalowane w celu dopasowania do rozmiaru metapliku.

```csharp
// Utwórz nową instancję MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

 Ten`MetafileRenderingOptions` Klasa udostępnia opcje dotyczące sposobu renderowania metaplików (takich jak WMF). Poprzez ustawienie`ScaleWmfFontsToMetafileSize` Do`false`, wydajesz Aspose.Words polecenie, aby nie skalował czcionek zgodnie z rozmiarem metapliku, co może pomóc w zmniejszeniu całkowitego rozmiaru pliku PDF.

## Krok 3: Ustaw opcje zapisywania pliku PDF

Teraz skonfiguruj opcje zapisywania PDF, aby użyć opcji renderowania metapliku, które właśnie ustawiłeś. To mówi Aspose.Words, jak obsługiwać metapliki podczas zapisywania dokumentu jako PDF.

```csharp
// Utwórz nową instancję PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

 Ten`PdfSaveOptions` Klasa pozwala określić różne ustawienia zapisywania dokumentu jako PDF. Przypisując wcześniej skonfigurowane`MetafileRenderingOptions` do`MetafileRenderingOptions` własność`PdfSaveOptions`, upewniasz się, że dokument jest zapisywany zgodnie z wybranymi przez Ciebie ustawieniami renderowania metapliku.

## Krok 4: Zapisz dokument jako PDF

Na koniec zapisz dokument Word jako PDF, używając skonfigurowanych opcji zapisu. Spowoduje to zastosowanie wszystkich ustawień, w tym opcji renderowania metapliku, do wyjściowego pliku PDF.


```csharp
// Zapisz dokument jako PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

 Na tym etapie`Save` metoda`Document` Klasa służy do eksportowania dokumentu do pliku PDF. Ścieżka, w której zostanie zapisany plik PDF, jest określona wraz z`PdfSaveOptions` które zawierają ustawienia renderowania metapliku.

## Wniosek

Skalując czcionki WMF do rozmiaru metapliku, możesz znacznie zmniejszyć rozmiar plików PDF generowanych z dokumentów Word. Ta technika pomaga w optymalizacji przechowywania i dystrybucji dokumentów bez uszczerbku dla jakości treści wizualnej. Postępowanie zgodnie z powyższymi krokami zapewnia, że pliki PDF są bardziej łatwe w zarządzaniu i wydajne pod względem rozmiaru.

## Najczęściej zadawane pytania

### Czym jest WMF i dlaczego ma znaczenie dla rozmiaru pliku PDF?

WMF (Windows Metafile) to format graficzny używany w systemie Microsoft Windows. Może zawierać zarówno dane wektorowe, jak i bitmapowe. Ponieważ dane wektorowe można skalować i manipulować nimi, ważne jest, aby obsługiwać je prawidłowo, aby uniknąć niepotrzebnie dużych plików PDF.

### Jak skalowanie czcionek WMF do rozmiaru metapliku wpływa na plik PDF?

Skalowanie czcionek WMF do rozmiaru metapliku może pomóc w zmniejszeniu całkowitego rozmiaru pliku PDF poprzez uniknięcie renderowania czcionek w wysokiej rozdzielczości, co mogłoby zwiększyć rozmiar pliku.

### Czy mogę używać innych formatów metaplików z Aspose.Words?

Tak, Aspose.Words obsługuje różne formaty metaplików, w tym EMF (Enhanced Metafile) i WMF.

### Czy tę technikę można stosować do wszystkich typów dokumentów Word?

Tak, tę technikę można zastosować w przypadku dowolnego dokumentu Word zawierającego grafikę WMF, co pomaga zoptymalizować rozmiar generowanego pliku PDF.

### Gdzie mogę znaleźć więcej informacji na temat Aspose.Words?

 Możesz dowiedzieć się więcej o Aspose.Words w[Dokumentacja Aspose.Words](https://reference.aspose.com/words/net/) Aby pobrać pliki, uzyskać wersje próbne i uzyskać pomoc, odwiedź stronę[Strona do pobrania Aspose.Words](https://releases.aspose.com/words/net/), [Kup Aspose.Words](https://purchase.aspose.com/buy), [Bezpłatna wersja próbna](https://releases.aspose.com/), [Licencja tymczasowa](https://purchase.aspose.com/temporary-license/) , I[Wsparcie](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
