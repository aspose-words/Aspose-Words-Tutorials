---
category: general
date: 2026-10-26
description: Utwórz wykres pierścieniowy i wstaw wykres kołowy w Javie, korzystając
  z kodu krok po kroku. Poznaj pełny przepływ pracy dla elastycznych wizualizacji
  wykresów.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: pl
lastmod: 2026-10-26
og_description: Utwórz wykres pierścieniowy w Javie za pomocą tego przewodnika, który
  także pokazuje, jak wstawić wykres kołowy dla elastycznych wizualizacji.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Utwórz wykres pierścieniowy i wstaw wykres kołowy – przewodnik Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Jak stworzyć wykres pierścieniowy i wstawić wykres kołowy
url: /pl/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć wykres pierścieniowy i wstawić wykres kołowy

Jeśli potrzebujesz **utworzyć wykres pierścieniowy** w Javie, ten samouczek przeprowadzi Cię krok po kroku. Pokażemy także, jak **wstawić wykres kołowy** przy użyciu tego samego API buildera, abyś mógł łatwo przełączać się między stylami wizualnymi. Po zakończeniu przewodnika będziesz mieć kompletny, działający program, który generuje oba typy wykresów i demonstruje typowe dostosowania.

Tutorial obejmuje:

* Inicjalizację buildera wykresów dostarczonego przez wybraną bibliotekę.  
* Tworzenie wykresu pierścieniowego i konfigurowanie rozmiaru otworu.  
* Wstawianie wykresu kołowego i „eksplodowanie” kawałka w celu podkreślenia.  
* Wskazówki dotyczące obsługi przypadków brzegowych, takich jak brak serii lub nieobsługiwane typy wykresów.

Wystarczy, że masz aktualny JDK (8 lub nowszy) oraz plik JAR biblioteki wykresów w classpath. Żadne zewnętrzne usługi nie są wymagane.

---

## Wymagania wstępne

| Element | Powód |
|------|--------|
| Java Development Kit (JDK) 8+ | Wymagany do kompilacji i uruchomienia przykładu. |
| Biblioteka wykresów (np. **Aspose.Cells for Java** lub **JFreeChart**) | Udostępnia `ChartBuilder`, `ChartType` oraz metody manipulacji seriami używane w kodzie. |
| IDE lub edytor tekstu | Do napisania i uruchomienia pliku źródłowego Java. |

Upewnij się, że plik JAR biblioteki został dodany do ścieżki budowania projektu. Jeśli używasz Maven, dodaj odpowiednią zależność; w przeciwnym razie umieść JAR w folderze `libs` i odwołuj się do niego podczas kompilacji.

---

## Krok 1: Skonfiguruj builder wykresu

Pierwszy krok to utworzenie instancji `ChartBuilder` (lub równoważnej), która będzie generować obiekty wykresów. Obiekt ten działa jako fabryka i przechowuje arkusz lub płótno, na którym wykres zostanie umieszczony.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Dlaczego to jest ważne:**  
Builder łączy wykres z konkretnym arkuszem, zapewniając, że wszystkie kolejne obiekty wykresów korzystają z tej samej powierzchni rysunkowej. Pominięcie tego kroku spowodowałoby brak docelowego miejsca dla elementów wizualnych.

---

## Krok 2: **Utwórz wykres pierścieniowy**

Teraz generujemy wykres pierścieniowy o określonym rozmiarze. Rozmiar otworu określa, jak duża część środka wykresu jest pusta, zamieniając zwykły wykres kołowy w pierścieniowy.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Wyjaśnienie:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` tworzy obiekt wykresu i rezerwuje miejsce w arkuszu.  
* `setHoleSize(30)` przekształca koło w pierścień z 30 % pustym środkiem.  
* `add("{10, 20, 30, 40}", true)` dostarcza cztery punkty danych; flaga `true` mówi bibliotece, aby traktowała wartości jako jedną serię.

**Przypadek brzegowy:** Jeśli wybrany typ wykresu nie obsługuje otworu (np. wykres słupkowy), wywołanie `getDoughnutChart()` zgłasza wyjątek. Zawsze weryfikuj typ wykresu przed zmianą rozmiaru otworu.

---

## Krok 3: **Wstaw wykres kołowy**

Po przygotowaniu pierścienia pokazujemy, jak **wstawić wykres kołowy** przy użyciu tego samego buildera. Ten krok podkreśla podobieństwo obu typów wykresów i pokazuje, jak wyróżnić kawałek.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Wyjaśnienie:**  

* `ChartType.PIE` instruuje builder, aby stworzył klasyczny wykres kołowy.  
* `setExplode(10)` odsuwa pierwszy kawałek o 10 % promienia, co jest powszechną techniką podkreślania kluczowego punktu danych.  

**Wskazówka:** Metoda `setExplode` działa tylko na pierwszej serii wykresu kołowego. Jeśli masz wiele serii, musisz skierować się do właściwego indeksu.

---

## Krok 4: Zapisz skoroszyt

Na koniec zapisujemy skoroszyt do pliku, aby móc wyświetlić wykresy w Excelu lub innym kompatybilnym podglądzie.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Dlaczego zapisać teraz:** Zapisanie skoroszytu finalizuje wszystkie operacje rysunkowe. Próba otwarcia pliku przed zapisem skutkuje pustym lub niekompletnym dokumentem.

**Wynik:** Otwierając *DoughnutAndPieChart.xlsx* zobaczysz wykres pierścieniowy z 30 % otworem po lewej oraz wykres kołowy z „eksplodowanym” pierwszym kawałkiem po prawej.

---

## Krok 5: Typowe warianty i rozwiązywanie problemów

| Sytuacja | Dostosowanie |
|-----------|------------|
| **Różne wymiary wykresu** | Zmień argumenty szerokości i wysokości w `insertChart`. |
| **Wiele serii danych** | Wywołaj `add` wielokrotnie lub przekaż łańcuch 2‑wymiarowej tablicy. |
| **Dynamiczny rozmiar otworu** | Oblicz rozmiar otworu na podstawie zakresu danych, a następnie wywołaj `setHoleSize`. |
| **Wybuch wielu kawałków** | Iteruj przez `chart.getSeries().get(i).setExplode(percent)` dla każdego kawałka, który chcesz odsunąć. |
| **Biblioteka nie obsługuje wykresu pierścieniowego** | Użyj wykresu kołowego i ręcznie narysuj białe koło jako nakładkę, choć jest to mniej precyzyjne. |

**Porada:** Zawsze wywołuj `builder.flush()` (jeśli jest dostępne) po wstawianiu wykresów przy pracy z dużymi skoroszytami. To zwalnia wewnętrzne bufory i zapobiega wyciekom pamięci.

![Kod Java tworzący wykres pierścieniowy i wstawiający wykres kołowy](https://example.com/images/doughnut-pie-java.png "przykład tworzenia wykresu pierścieniowego w Javie")

*Obraz ilustruje ostateczny układ skoroszytu z oboma wykresami obok siebie.*

---

## Zakończenie

Teraz wiesz, jak **utworzyć wykres pierścieniowy** i **wstawić wykres kołowy** w Javie przy użyciu płynnego API buildera. Pełny przykład obejmuje inicjalizację, konfigurację rozmiaru, ustawianie otworu, „eksplodowanie” kawałka oraz zapis do pliku. Od tego momentu możesz eksplorować dodatkowe dostosowania, takie jak kolory, legendy i etykiety danych, aby dopasować wykresy do wymagań raportowania.

**Kolejne kroki**

* Eksperymentuj z funkcjami **chart customization Java**, takimi jak gradientowe wypełnienia i etykiety danych.  
* Zintegruj generowanie wykresów z usługą webową, która zwraca skoroszyt na żądanie.  
* Porównaj podejście buildera z innymi bibliotekami (np. JFreeChart), aby wybrać najlepsze rozwiązanie dla swojego projektu.

Miłego wykreślania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu wraz z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak utworzyć wykres pierścieniowy w dokumencie Word przy użyciu Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Zapisz dokument Word po edycji wykresu pierścieniowego w Javie](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Wstaw wykres kołowy w Javie – Wybuch, Obrót i podświetlenie kawałków](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}