---
category: general
date: 2026-07-06
description: بناء مشروع CMake خطوة بخطوة. تعلّم كيفية تكوين CMake، وكيفية بناء CMake،
  وكيفية تشغيل CTest للاختبار الموثوق.
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: ar
og_description: بناء مشروع CMake بسرعة مع خطوات واضحة. يوضح هذا الدليل كيفية تكوين
  CMake، وكيفية بناء CMake، وكيفية تشغيل CTest.
og_title: 'بناء مشروع CMake: دليل التكوين والبناء والاختبار'
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Build CMake project step‑by‑step. Learn how to configure CMake, how
    to build CMake, and how to run CTest for reliable testing.
  headline: 'Build CMake Project: Configure, Build & Test'
  type: TechArticle
tags:
- cmake
- ctest
- build-system
title: 'بناء مشروع CMake: التكوين، البناء والاختبار'
url: /ar/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# بناء مشروع CMake: التكوين، البناء والاختبار

هل تساءلت يومًا كيف **build CMake project** دون قضاء ساعات في البحث على StackOverflow؟ لست وحدك. يواجه معظم المطورين نفس المشكلة عندما يحاولون الانتقال من `CMakeLists.txt` بسيط إلى خط أنابيب بناء قابل لإعادة الإنتاج. 

في هذا الدرس سنستعرض العملية بالكامل—*how to configure CMake*، *how to build CMake*، و*how to run CTest*—حتى تحصل على بناء نظيف وقابل للتكرار يمكنك تشغيله على أي جهاز. في النهاية ستحصل على مثال عملي يمكنك نسخه ولصقه في مستودعك الخاص، دون الحاجة إلى أي سكريبتات إضافية.

## المتطلبات المسبقة — ما تحتاجه قبل البدء

- إصدار حديث من CMake (3.20 أو أحدث) – الإصدارات القديمة تفتقد بعض العلامات التي سنستخدمها.
- مترجم C++ مدعوم من نظامك (gcc، clang، MSVC، إلخ).
- طرفية أو موجه أوامر يمكنه الوصول إلى `cmake` و `ctest`.
- (اختياري) Git لاستنساخ المستودع المثال إذا رغبت في المتابعة مع المصدر الدقيق.

إذا كان أي منها مفقودًا، احصل عليه الآن؛ وإلا ستواجه أخطاء “command not found” لاحقًا، وهذا ليس ممتعًا أبداً.

## الخطوة 1: تكوين مشروع CMake (إعداد Release)

أول شيء تقوم به عندما *how to configure CMake* هو إخبار CMake بمكان وجود المصدر وأين تريد وضع مخرجات البناء. العلامة `-S` تشير إلى دليل المصدر، `-B` تنشئ مجلد بناء منفصل، و`-D CMAKE_BUILD_TYPE=Release` تفرض بناءً مُحسّنًا.

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**لماذا هذا مهم:** الحفاظ على فصل ملفات المصدر والبناء (`out‑of‑source` builds) يمنع التعديلات غير المقصودة على المصدر ويسهل تنظيف دليل البناء لاحقًا. علامة `Release` أيضًا تخبر المترجم بتمكين التحسينات، وهو ما تريده عادةً للملف التنفيذي النهائي.

> **نصيحة احترافية:** إذا كنت بحاجة إلى بناء Debug للتصحيح، فقط استبدل `Release` بـ `Debug`. الأمر نفسه يعمل—CMake يتولى البقية.

## الخطوة 2: بناء المشروع المُكوَّن

الآن بعد أن خطوة التكوين أنشأت جميع ملفات makefile أو ملفات مشروع Visual Studio اللازمة، يمكنك فعليًا تجميع الشيفرة. خيار `--build` يُجرد أداة البناء الأساسية (`make`، `ninja`، `MSBuild`، إلخ)، لذا يعمل الأمر نفسه على Linux و macOS و Windows.

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**ما الذي يحدث في الخلفية؟** يقرأ CMake ملف `CMakeCache.txt` الذي تم إنشاؤه في الخطوة السابقة، يحدد أداة البناء المناسبة، ويستدعيها بالعلامات الصحيحة. هذا هو جوهر *how to build CMake*—لا تحتاج إلى تذكر ما إذا كنت تستخدم `make` أو `ninja`؛ CMake يقوم بذلك نيابةً عنك.

إذا أردت تسريع العملية على الأجهزة متعددة النوى، أضف `-- -j$(nproc)` (Linux/macOS) أو `-- /m` (Windows) بعد الأمر:

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## الخطوة 3: تشغيل اختبارات المثال مع مخرجات مفصلة

الاختبار هو المكان الذي يُظهر فيه الأداء الفعلي. يأتي CMake مع `ctest`، أداة اختبار يمكنها اكتشاف وتشغيل أي اختبار مضاف عبر `add_test()` في ملف `CMakeLists.txt`. لتنفيذ الاختبارات ورؤية مخرجات مفصلة، استخدم المساعد `-E chdir` لتغيير الدليل إلى دليل البناء أولاً:

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**لماذا تستخدم `--verbose`؟** يطبع سطر أوامر كل اختبار، رمز الخروج، وأي مخرجات يكتبها الاختبار نفسه. هذا أساسي عندما تتعلم *how to run CTest* لأنه يُظهر بالضبط ما يحدث في الخلفية.

المخرجات النموذجية تبدو هكذا:

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

إذا فشل اختبار، سيتضمن السجل المفصل الأمر الفاشل وأي رسائل خطأ، مما يجعل عملية التصحيح أسرع بكثير.

## الخطوة 4: أتمتة سير العمل بالكامل (اختياري)

في العديد من المشاريع قد ترغب في سطر واحد يقوم بالتكوين، البناء، والاختبار دفعة واحدة. يمكنك تحقيق ذلك باستخدام سكريبت Bash (أو PowerShell) بسيط:

```bash
#!/usr/bin/env bash
SRC=YOUR_DIRECTORY/Examples/DocsExamples
BUILD=$SRC/build

# 1️⃣ Configure
cmake -S "$SRC" -B "$BUILD" -D CMAKE_BUILD_TYPE=Release

# 2️⃣ Build
cmake --build "$BUILD" -- -j$(nproc)

# 3️⃣ Test
cmake -E chdir "$BUILD" ctest --verbose
```

احفظه باسم `run_all.sh`، اجعله قابلًا للتنفيذ (`chmod +x run_all.sh`)، وستحصل على خط أنابيب **cmake build and test** قابل لإعادة الإنتاج يمكنك إدراجه في أي نظام CI (GitHub Actions، GitLab CI، Azure Pipelines، إلخ).

## الحالات الخاصة والمشكلات الشائعة

| الحالة | ما يجب مراقبته | الحل |
|-----------|-------------------|-----|
| **المترجم مفقود** | يتوقف CMake مع الرسالة “No CMAKE_CXX_COMPILER could be found.” | ثبّت مترجمًا (`sudo apt install build-essential` على أوبونتو، `xcode-select --install` على macOS). |
| **مجلد out‑of‑source موجود مسبقًا** | قد يرفض CMake إعادة التكوين إذا كان المجلد يحتوي على ملفات قديمة. | احذف دليل `build` (`rm -rf build`) أو شغّل `cmake --fresh` (CMake 3.24+). |
| **CTest لا يستطيع العثور على الاختبارات** | لم يتم استدعاء `add_test()` أبداً أو فشل تجميع ملف تنفيذ الاختبار. | تأكد من وجود `add_test(NAME MyTest COMMAND MyTestExe)` في `CMakeLists.txt` وأن الهدف يُبنى. |
| **بناء متوازي يتسبب في تعارض الأوامر المخصصة** | بعض الأوامر المخصصة غير مُعلمة بـ `DEPENDS`، مما يؤدي إلى فشل غير حتمي. | أضف إدخالات `add_custom_command(... DEPENDS ...)` المناسبة. |

فهم هذه الفروق يحدث الفارق بين بناء غير مستقر وخط أنابيب CI صلب كالصخر.

## نظرة بصرية (النص البديل يتضمن الكلمة الرئيسية)

![Diagram showing the flow of configuring, building, and testing a CMake project](/images/cmake-workflow.png "Build CMake Project workflow diagram")

## ملخص – ما تعلمته

بدأنا بالسؤال الأساسي: *how to build CMake project* من الصفر. في النهاية الآن تعرف كيف **configure CMake** باستخدام بناء out‑of‑source نظيف، **build CMake** باستخدام العلامة العامة `--build`، و**run CTest** مع مخرجات مفصلة للتحقق من أن كل شيء يعمل. لديك أيضًا سكريبت جاهز للاستخدام يربط الخطوات الثلاث معًا، مما يمنحك سير عمل كامل **cmake build and test**.

## ما التالي؟

- **إضافة تقارير التغطية** – دمج `gcov` أو `llvm-cov` ودع CTest ينشر النتائج.
- **الترجمة عبر الأنظمة** – استكشف `-DCMAKE_TOOLCHAIN_FILE` للبناء على الأجهزة المدمجة.
- **إنشاء حزم** – استخدم `cpack` لتجميع ملفاتك التنفيذية للتوزيع.
- **دمج CI** – انسخ السكريبت إلى سير عمل GitHub Actions وشاهد الأتمتة تعمل على كل طلب سحب.

لا تتردد في تجربة أنواع بناء مختلفة، إضافة المزيد من الاختبارات، أو استبدال مصدر المثال بمشروعك الخاص. الأنماط التي غطيناها اليوم تنطبق على أي قاعدة شفرة مبنية على CMake، سواء كانت أداة صغيرة أو نظام متعدد الوحدات ضخم.

بناء موفق، ولتكن عمليات بناء CMake دائمًا قابلة لإعادة الإنتاج!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية تصدير LaTeX من Word – دليل خطوة بخطوة](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [كيفية حفظ Markdown من DOCX – دليل خطوة بخطوة](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [كيفية عرض إصدار Aspose.Words في Python و .NET&#58; دليل خطوة بخطوة](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}