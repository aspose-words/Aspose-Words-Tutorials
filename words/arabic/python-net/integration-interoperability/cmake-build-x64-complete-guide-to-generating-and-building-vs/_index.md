---
category: general
date: 2026-07-16
description: دليل بناء cmake x64 يوضح كيفية استخدام CMake لإنشاء حل Visual Studio 2022
  وبناء مشروع VS على مضيف 64‑بت. يتضمن خطوات تعيين دليل المصدر.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: ar
lastmod: 2026-07-16
og_description: 'شرح بناء cmake x64: تعلّم كيفية تعيين دليل المصدر، إنشاء حل Visual Studio 2022،
  وتجميع مشروع VS على مضيف 64‑بت.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: بناء cmake x64 – دليل خطوة بخطوة لتوليد وبناء حلول VS 2022
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
title: بناء cmake x64 – دليل كامل لإنشاء وبناء مشاريع VS 2022
url: /ar/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – دليل شامل لتوليد وبناء مشاريع VS 2022

هل تساءلت يومًا **how to use CMake** لإنتاج حل Visual Studio 64‑بت دون أن تشد شعرك؟ لست وحدك. في هذا الدرس سنستعرض سير عمل **cmake build x64** يحدد دليل المصدر، يشغّل المولد لـ Visual Studio 2022، وأخيرًا يبني مشروع VS — كل ذلك باستخدام بضع أوامر Bash نظيفة.

بنهاية الدليل ستحصل على سكريبت قابل لإعادة الاستخدام يمكنك وضعه في أي مستودع، بالإضافة إلى فهم قوي للمفاهيم الأساسية لتتمكن من تعديلها وفق احتياجاتك.

---

## ما ستتعلمه

- **Set source directory** بشكل صحيح حتى يعرف CMake مكان وجود ملف `CMakeLists.txt` الخاص بك.  
- **cmake generate visual studio** – استدعاء مولد Visual Studio 2022 مع العلامات المناسبة للمضيف والمعمارية.  
- تنفيذ **cmake build x64** للحل المُولد، مع إمكانية اختيار تكوين Release.  
- فهم المشكلات الشائعة عند محاولة **build vs project** على جهاز 64‑بت.  

لا تحتاج إلى خبرة سابقة في CMake؛ مجرد طرفية وتثبيت حديث لـ Visual Studio يكفي.

## المتطلبات المسبقة

| المتطلب | لماذا يهم |
|-------------|----------------|
| CMake ≥ 3.20 | يدعم العلامات `-Thost=` و `-Ax64` المستخدمة في عمليات البناء 64‑بت. |
| Visual Studio 2022 (Community, Professional, or Enterprise) | المولد `Visual Studio 17 2022` يشير إلى هذا الإصدار. |
| صدفة متوافقة مع Bash (Git Bash, WSL, PowerShell مع alias `bash`) | السكريبت أدناه يستخدم ص syntax Bash للوضوح. |
| شجرة مصدر تحتوي على ملف `CMakeLists.txt` صالح | لا يمكن لـ CMake توليد حل بدون هذا الملف. |

إذا كان أي من هذه غير موجود، قم بتثبيته أولاً — CMake من <https://cmake.org/download/> و VS 2022 من مُثبت Microsoft.

## الخطوة 1 – تعيين دليل المصدر والبناء (`set source directory`)

قبل استدعاء CMake تحتاج إلى إخبارها **أين** تبحث عن ملفات المشروع. كتابة المسارات صراحة تجعل السكريبت هشًا، لذا سنستخدم متغيرات بيئية يمكنك تعديلها لكل مشروع.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Why this matters:**  
> CMake treats the *source directory* (`SRC_DIR`) as the root of the project. The *build directory* (`BUILD_DIR`) is where all intermediate files, caches, and the final `.sln` live. Keeping them separate avoids polluting your source tree and makes clean‑up trivial (`rm -rf "$BUILD_DIR"`).

يمكنك استبدال `YOUR_DIRECTORY` بأي مسار مطلق أو نسبي؛ فقط تأكد أن المجلد يحتوي على ملف `CMakeLists.txt`.

---

## الخطوة 2 – توليد حل Visual Studio 2022 (`cmake generate visual studio`)

الآن نطلب من CMake أن ينتج حل VS 2022 يستهدف **x64**. العلامات الرئيسية هي:

- `-G "Visual Studio 17 2022"` – يحدد مولد VS 2022.  
- `-Thost=x64` – يخبر CMake أن *المضيف* (IDE) يعمل كعملية 64‑بت.  
- `-Ax64` – يجبر المشروع المُولد على البناء للمعمارية x64.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **What happens under the hood?**  
> CMake reads `CMakeLists.txt` from `$SRC_DIR`, resolves all `add_executable()` and `add_library()` calls, then creates a `.sln` file and a set of `.vcxproj` files inside `$BUILD_DIR`. Those project files are now ready to be opened in Visual Studio or built from the command line.

إذا نفذت الأمر ورأيت قائمة طويلة من رسائل التكوين تنتهي بـ `-- Configuring done` و `-- Generating done`، فقد أتممت خطوة **cmake generate visual studio** بنجاح.

---

## الخطوة 3 – بناء الحل المُولد (`cmake build x64`)

مع وجود الحل، الخطوة المنطقية التالية هي تجميعه. يمكن لـ CMake قيادة عملية البناء لك، مع تفويض MSBuild في الخلفية.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Why use `--config Release`?**  
> Visual Studio projects support multiple configurations (Debug, Release, RelWithDebInfo, etc.). Specifying `Release` ensures the binaries are optimized for production and that the resulting `.exe` or `.dll` lives under `Release/` inside the build tree.

إذا كنت تفضّل بناء Debug، استبدل `Release` بـ `Debug`. يعمل الأمر بنفس الطريقة، مما يثبت أن **how to use CMake** لتكوينات مختلفة هو مجرد تبديل لهذه العلامة.

---

## الخطوة 4 – التحقق من البناء (`build vs project` sanity check)

يجب أن يترك لك تجميع ناجح ملفًا تنفيذيًا أو مكتبة. دعنا نتأكد من وجوده:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Common pitfalls:**  
> - Forgetting to run the generator step after changing `CMakeLists.txt` will cause this check to fail.  
> - Mixing 32‑bit and 64‑bit toolchains can lead to linker errors; always keep `-Ax64` consistent.  
> - If you see “MSB3073” errors, it usually means a post‑build step (like copying resources) failed—inspect the output for clues.

---

## الخطوة 5 – التنظيف وإعادة التشغيل (تكرار **cmake build x64**)

أثناء التطوير قد تحتاج غالبًا إلى إعادة بناء من الصفر. أنظف الطريقة هي حذف مجلد البناء والبدء من جديد:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Tip:**  
> Adding `-DCMAKE_BUILD_TYPE=Release` to the generator command is optional for multi‑config generators like Visual Studio, but it can be handy when you switch to a single‑config generator such as Ninja.

---

## الخطوة 6 – توسيع السكريبت (سيناريوهات متقدمة لـ `cmake generate visual studio`)

ماذا لو كان مشروعك في مجلد فرعي، أو تحتاج إلى تمرير تعريفات مخصصة؟ يسمح لك CMake بذلك باستخدام معاملات `-D`:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

الآن سيحتوي الحل المُولد على الماكرو `MyFeature_ENABLED`، وستضع هدف التثبيت الملفات تحت `/opt/myapp`. هذا يوضح مرونة **how to use CMake** بعيدًا عن التدفق الأساسي المكوّن من ثلاث خطوات.

---

## النتيجة المتوقعة

عند تشغيل السكريبت بالكامل من البداية إلى النهاية، يجب أن يعرض الطرفية شيئًا مشابهًا لـ:

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

إذا حدث أي خطأ، سيصدر CMake رسائل خطأ تشير إلى السطر المخطئ في `CMakeLists.txt` أو إلى مكونات SDK مفقودة — مثالي لتصحيح سريع.

---

## الخلاصة

غطينا كل ما تحتاجه لتنفيذ **cmake build x64**: تعيين دليل المصدر، استدعاء خطوة **cmake generate visual studio**، تجميع **build vs project** الناتج، والتحقق من النتيجة. السكريبت صغير، محمول، وجاهز للتكامل في خطوط CI أو سير عمل التطوير المحلي.

بعد ذلك قد ترغب في استكشاف:

- إضافة تنفيذ اختبارات الوحدة باستخدام `ctest`.  
- التحويل إلى مولد Ninja لبناءات متزايدة السرعة (`-G Ninja`).  
- استخدام إعدادات CMake مسبقة (`CMakePresets.json`) لتخزين العلامات التي كتبناها للتو.

لا تتردد في التجربة، كسر الأشياء، ثم إعادة البناء — فهذه أسرع طريقة لتعلم **how to use CMake** بفعالية. بناء موفق!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك الخاصة.

- [إنشاء جدول](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [إنشاء جدول مع نمط](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [إنشاء جدول مع حدود](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}