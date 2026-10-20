---
category: general
date: 2026-07-16
description: Учебник «cmake build x64» показывает, как использовать CMake для генерации
  решения Visual Studio 2022 и сборки проекта VS на 64‑разрядном хосте. Включает шаги
  по установке каталога исходных файлов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: ru
lastmod: 2026-07-16
og_description: 'cmake build x64 объяснено: узнайте, как задать каталог исходного
  кода, сгенерировать решение Visual Studio 2022 и собрать проект VS на 64‑разрядном
  хосте.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: Сборка cmake x64 – Пошаговое руководство по генерации и сборке решений VS 2022
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: cmake build x64 tutorial shows how to use CMake to generate a Visual
    Studio 2022 solution and build a VS project on a 64‑bit host. Includes set source
    directory steps.
  headline: cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects
  type: TechArticle
tags:
- cmake
- visual-studio
- x64
- build-automation
title: Сборка cmake x64 – Полное руководство по генерации и сборке проектов VS 2022
url: /ru/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Полное руководство по генерации и сборке проектов VS 2022

Вы когда‑нибудь задавались вопросом, **как использовать CMake**, чтобы создать 64‑разрядное решение Visual Studio, не теряя волосы? Вы не одиноки. В этом руководстве мы пройдем через рабочий процесс **cmake build x64**, который задаёт каталог исходников, запускает генератор для Visual Studio 2022 и, наконец, собирает проект VS — всё с помощью нескольких чистых команд Bash.

К концу руководства у вас будет воспроизводимый скрипт, который можно добавить в любой репозиторий, а также твёрдое понимание базовых концепций, позволяющее адаптировать его под свои нужды.

---

## Что вы узнаете

- **Set source directory** правильно, чтобы CMake знал, где находится ваш `CMakeLists.txt`.  
- **cmake generate visual studio** – вызвать генератор Visual Studio 2022 с правильными флагами хоста и архитектуры.  
- Выполнить **cmake build x64** сгенерированного решения, при желании выбрав конфигурацию Release.  
- Понять распространённые подводные камни при попытке **build vs project** на 64‑разрядной машине.  

Не требуется предварительное волшебство CMake; достаточно терминала и свежей установки Visual Studio.

---

## Требования

| Требование | Почему это важно |
|-------------|----------------|
| CMake ≥ 3.20 | Поддерживает флаги `-Thost=` и `-Ax64`, используемые для 64‑разрядных сборок. |
| Visual Studio 2022 (Community, Professional, or Enterprise) | Генератор `Visual Studio 17 2022` указывает на эту версию. |
| Bash‑совместимая оболочка (Git Bash, WSL, PowerShell с алиасом `bash`) | Скрипт ниже использует синтаксис Bash для наглядности. |
| Дерево исходников, содержащее корректный `CMakeLists.txt` | CMake не может сгенерировать решение без него. |

Если что‑то из этого отсутствует, установите сначала — CMake с <https://cmake.org/download/> и VS 2022 через установщик Microsoft.

---

## Шаг 1 – Установка каталогов исходников и сборки (`set source directory`)

Прежде чем вызвать CMake, нужно указать ему **где** искать файлы проекта. Жёстко прописанные пути делают скрипт хрупким, поэтому мы будем использовать переменные окружения, которые можно менять для каждого проекта.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Почему это важно:**  
> CMake рассматривает *каталог исходников* (`SRC_DIR`) как корень проекта. *Каталог сборки* (`BUILD_DIR`) — это место, где находятся все промежуточные файлы, кэши и финальный `.sln`. Разделение их помогает избежать загрязнения дерева исходников и делает очистку тривиальной (`rm -rf "$BUILD_DIR"`).

Вы можете заменить `YOUR_DIRECTORY` на любой абсолютный или относительный путь; просто убедитесь, что в папке есть `CMakeLists.txt`.

---

## Шаг 2 – Генерация решения Visual Studio 2022 (`cmake generate visual studio`)

Теперь мы просим CMake вывести решение VS 2022, нацеленное на **x64**. Ключевые флаги:

- `-G "Visual Studio 17 2022"` – выбирает генератор VS 2022.  
- `-Thost=x64` – сообщает CMake, что *хост* (IDE) работает как 64‑разрядный процесс.  
- `-Ax64` – заставляет сгенерированный проект собираться для архитектуры x64.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **Что происходит под капотом?**  
> CMake читает `CMakeLists.txt` из `$SRC_DIR`, разрешает все вызовы `add_executable()` и `add_library()`, затем создаёт файл `.sln` и набор файлов `.vcxproj` внутри `$BUILD_DIR`. Эти файлы проекта теперь готовы к открытию в Visual Studio или к сборке из командной строки.

Если вы выполните команду и увидите длинный список сообщений конфигурации, заканчивающийся `-- Configuring done` и `-- Generating done`, вы успешно выполнили шаг **cmake generate visual studio**.

---

## Шаг 3 – Сборка сгенерированного решения (`cmake build x64`)

С готовым решением следующий логичный шаг — его компиляция. CMake может управлять сборкой за вас, делегируя работу MSBuild.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Зачем использовать `--config Release`?**  
> Проекты Visual Studio поддерживают несколько конфигураций (Debug, Release, RelWithDebInfo и т.д.). Указание `Release` гарантирует, что бинарники оптимизированы для продакшна и что полученный `.exe` или `.dll` окажется в каталоге `Release/` внутри дерева сборки.

Если вам нужен Debug, замените `Release` на `Debug`. Команда работает так же, доказывая, что **how to use CMake** для разных конфигураций — это лишь замена флага.

---

## Шаг 4 – Проверка сборки (`build vs project` sanity check)

Успешная компиляция должна оставить исполняемый файл или библиотеку. Давайте убедимся, что они существуют:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Распространённые подводные камни:**  
> - Забвение выполнить шаг генерации после изменения `CMakeLists.txt` приведёт к провалу этой проверки.  
> - Смешивание 32‑ и 64‑разрядных тулчейнов может вызвать ошибки линковки; всегда сохраняйте согласованность `-Ax64`.  
> - Если вы видите ошибки “MSB3073”, обычно это означает, что пост‑сборочный шаг (например, копирование ресурсов) завершился неудачей — проверьте вывод для получения подсказок.

---

## Шаг 5 – Очистка и повторный запуск (итерации `cmake build x64`)

Во время разработки часто требуется полностью пересобрать проект. Самый чистый способ — удалить папку сборки и начать заново:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Подсказка:**  
> Добавление `-DCMAKE_BUILD_TYPE=Release` к команде генератора опционально для мульти‑конфигурных генераторов, таких как Visual Studio, но может быть полезным, когда вы переключаетесь на одно‑конфигурный генератор, например Ninja.

---

## Шаг 6 – Расширение скрипта (расширенные сценарии `cmake generate visual studio`)

Что если ваш проект находится в подкаталоге или требуется передать пользовательские определения? CMake позволяет делать это с помощью аргументов `-D`:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Теперь сгенерированное решение VS будет иметь определённый макрос `MyFeature_ENABLED`, а цель установки разместит файлы в `/opt/myapp`. Это демонстрирует гибкость **how to use CMake** за пределами базового трёхшагового процесса.

---

## Ожидаемый вывод

При запуске полного скрипта от начала до конца терминал должен отобразить что‑то вроде:

```
-- The C compiler identification is MSVC 19.35.31107.0
-- The CXX compiler identification is MSVC 19.35.31107.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
...
-- Configuring done
-- Generating done
-- Build files have been written to: /path/to/Examples/DocsExamples/build
...
[ 50%] Building CXX object CMakeFiles/MyApp.dir/main.cpp.obj
[100%] Linking CXX executable Release/MyApp.exe
✅ Build succeeded! Executable ready at /path/to/Examples/DocsExamples/build/Release/MyApp.exe
```

Если что‑то пойдёт не так, CMake выведет сообщения об ошибках, указывающие на проблемную строку в `CMakeLists.txt` или на недостающие компоненты SDK — идеально для быстрой отладки.

---

## Заключение

Мы рассмотрели всё, что нужно для выполнения **cmake build x64**: установка каталога исходников, вызов шага **cmake generate visual studio**, компиляция полученного **build vs project** и проверка результата. Скрипт компактен, переносим и готов к интеграции в CI‑конвейеры или локальные рабочие процессы.

Дальше вы можете изучить:

- Добавление выполнения модульных тестов с помощью `ctest`.  
- Переход на генератор Ninja для более быстрых инкрементных сборок (`-G Ninja`).  
- Использование пресетов CMake (`CMakePresets.json`) для хранения только что введённых флагов.

Не бойтесь экспериментировать, ломать вещи и затем пересобирать — так вы быстрее научитесь эффективно использовать CMake. Удачной сборки!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы реализации в ваших проектах.

- [Создать таблицу](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Создать таблицу со стилем](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Создать таблицу с границами](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}