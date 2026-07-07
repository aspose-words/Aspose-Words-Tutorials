---
category: general
date: 2026-07-06
description: สร้างโครงการ CMake ทีละขั้นตอน เรียนรู้วิธีกำหนดค่า CMake วิธีการสร้าง
  CMake และวิธีการรัน CTest เพื่อการทดสอบที่น่าเชื่อถือ
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: th
og_description: สร้างโครงการ CMake อย่างรวดเร็วด้วยขั้นตอนที่ชัดเจน คู่มือนี้แสดงวิธีการกำหนดค่า
  CMake, วิธีการสร้าง CMake, และวิธีการเรียกใช้ CTest.
og_title: 'สร้างโครงการ CMake: คู่มือการกำหนดค่า, สร้างและทดสอบ'
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
title: 'สร้างโครงการ CMake: กำหนดค่า, สร้างและทดสอบ'
url: /th/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างโครงการ CMake: กำหนดค่า, สร้าง & ทดสอบ

เคยสงสัยไหมว่า **build CMake project** อย่างไรโดยไม่ต้องเสียเวลาหลายชั่วโมงค้นหาใน StackOverflow? คุณไม่ได้เป็นคนเดียวที่เจอเรื่องนี้ นักพัฒนาส่วนใหญ่ก็เจออุปสรรคเดียวกันเมื่อพยายามย้ายจาก `CMakeLists.txt` แบบง่ายไปสู่ pipeline การสร้างที่ทำซ้ำได้  

ในบทแนะนำนี้เราจะเดินผ่านกระบวนการทั้งหมด—*how to configure CMake*, *how to build CMake*, และ *how to run CTest*—เพื่อให้คุณได้ผลลัพธ์เป็นการสร้างที่สะอาดและทำซ้ำได้บนเครื่องใดก็ได้ เมื่อจบคุณจะมีตัวอย่างที่ทำงานได้ซึ่งสามารถคัดลอก‑วางไปยัง repository ของคุณเองได้โดยไม่ต้องใช้สคริปต์เพิ่มเติม

## ข้อกำหนดเบื้องต้น — สิ่งที่คุณต้องมีก่อนเริ่ม

ก่อนที่เราจะดำเนินการต่อ ให้ตรวจสอบว่าคุณมี:

- เวอร์ชัน CMake ล่าสุด (3.20 หรือใหม่กว่า) – รุ่นเก่าอาจขาดบาง flag ที่เราจะใช้
- คอมไพเลอร์ C++ ที่รองรับโดยแพลตฟอร์มของคุณ (gcc, clang, MSVC ฯลฯ)
- เทอร์มินัลหรือ command‑prompt ที่เข้าถึง `cmake` และ `ctest`
- (ไม่บังคับ) Git เพื่อโคลน repository ตัวอย่างหากต้องการทำตามขั้นตอนพร้อมซอร์สโค้ดที่ตรงกัน

หากขาดสิ่งใดสิ่งหนึ่ง ให้ติดตั้งทันที; มิฉะนั้นคุณจะเจอข้อผิดพลาด “command not found” ในภายหลัง ซึ่งไม่สนุกเลย

## ขั้นตอนที่ 1: กำหนดค่าโครงการ CMake (การกำหนดค่า Release)

สิ่งแรกที่คุณทำเมื่อ *how to configure CMake* คือบอก CMake ว่าแหล่งที่มาของโค้ดอยู่ที่ไหนและต้องการให้ไฟล์ผลลัพธ์ของการสร้างไปอยู่ที่ไหน flag `-S` ชี้ไปที่ไดเรกทอรีซอร์ส, `-B` สร้างโฟลเดอร์ build แยกออก, และ `-D CMAKE_BUILD_TYPE=Release` บังคับให้สร้างแบบปรับประสิทธิภาพ

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**ทำไมสิ่งนี้ถึงสำคัญ:** การแยกไฟล์ซอร์สและไฟล์ build (`out‑of‑source` builds) ป้องกันการแก้ไขซอร์สโดยบังเอิญและทำให้การทำความสะอาดไดเรกทอรี build ง่ายขึ้น `Release` ยังบอกคอมไพเลอร์ให้เปิดการเพิ่มประสิทธิภาพ ซึ่งเป็นสิ่งที่คุณมักต้องการสำหรับไบนารีขั้นสุดท้าย

> **เคล็ดลับ:** หากต้องการ build แบบ Debug เพื่อแก้ปัญหา เพียงเปลี่ยน `Release` เป็น `Debug` คำสั่งเดียวกันทำงานได้ – CMake จะจัดการส่วนที่เหลือให้เอง

## ขั้นตอนที่ 2: สร้างโครงการที่กำหนดค่าแล้ว

เมื่อขั้นตอนการกำหนดค่าได้สร้างไฟล์ makefile หรือไฟล์โครงการ Visual Studio ที่จำเป็นแล้ว คุณสามารถคอมไพล์โค้ดได้จริง ตัวเลือก `--build` จะทำหน้าที่เป็นชั้นนามธรรมของเครื่องมือ build พื้นฐาน (`make`, `ninja`, `MSBuild` ฯลฯ) ทำให้คำสั่งเดียวกันทำงานได้บน Linux, macOS, และ Windows

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**อะไรกำลังเกิดขึ้นเบื้องหลัง?** CMake อ่าน `CMakeCache.txt` ที่สร้างในขั้นตอนก่อนหน้า, ตัดสินใจเลือกเครื่องมือ build ที่เหมาะสม, แล้วเรียกใช้มันพร้อม flag ที่ถูกต้อง นี่คือแก่นของ *how to build CMake* – คุณไม่ต้องจำว่าใช้ `make` หรือ `ninja`; CMake ทำให้คุณเอง

หากต้องการเร่งความเร็วบนเครื่องหลายคอร์ ให้เพิ่ม `-- -j$(nproc)` (Linux/macOS) หรือ `-- /m` (Windows) หลังคำสั่ง:

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## ขั้นตอนที่ 3: รันการทดสอบตัวอย่างพร้อมรายละเอียดผลลัพธ์

การทดสอบคือจุดที่ความสำเร็จถูกพิสูจน์ CMake มาพร้อมกับ `ctest` ซึ่งเป็น driver ที่สามารถค้นหาและรันการทดสอบใด ๆ ที่เพิ่มผ่าน `add_test()` ใน `CMakeLists.txt` ของคุณ เพื่อรันการทดสอบและดูผลลัพธ์แบบละเอียด ให้ใช้ตัวช่วย `-E chdir` เพื่อเปลี่ยนไปยังไดเรกทอรี build ก่อน:

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**ทำไมต้องใช้ `--verbose`?** มันจะแสดงบรรทัดคำสั่งของแต่ละการทดสอบ, รหัสออก, และเอาต์พุตใด ๆ ที่การทดสอบเขียนออกมา สิ่งนี้สำคัญเมื่อคุณกำลังเรียนรู้ *how to run CTest* เพราะจะแสดงให้เห็นว่ากำลังเกิดอะไรขึ้นเบื้องหลังอย่างชัดเจน

ผลลัพธ์ทั่วไปจะมีลักษณะดังนี้:

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

หากการทดสอบล้มเหลว, log แบบละเอียดจะรวมคำสั่งที่ล้มเหลวและข้อความข้อผิดพลาด ทำให้การดีบักเร็วขึ้นมาก

## ขั้นตอนที่ 4: ทำอัตโนมัติทั้ง workflow (ไม่บังคับ)

สำหรับหลายโครงการคุณอาจต้องการคำสั่งหนึ่งบรรทัดที่ทำการกำหนดค่า, สร้าง, และทดสอบในคราวเดียว คุณทำได้ด้วยสคริปต์ Bash (หรือ PowerShell) ง่าย ๆ:

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

บันทึกเป็น `run_all.sh`, ทำให้เป็นไฟล์ที่เรียกใช้ได้ (`chmod +x run_all.sh`), แล้วคุณจะได้ pipeline **cmake build and test** ที่ทำซ้ำได้ซึ่งสามารถใส่ลงในระบบ CI ใดก็ได้ (GitHub Actions, GitLab CI, Azure Pipelines, ตามที่คุณต้องการ)

## Edge Cases & Common Pitfalls

| สถานการณ์ | สิ่งที่ควรระวัง | วิธีแก้ |
|-----------|-------------------|-----|
| **Missing compiler** | CMake ยกเลิกการทำงานด้วยข้อความ “No CMAKE_CXX_COMPILER could be found.” | ติดตั้งคอมไพเลอร์ (`sudo apt install build-essential` บน Ubuntu, `xcode-select --install` บน macOS) |
| **Out‑of‑source folder already exists** | CMake อาจปฏิเสธการกำหนดค่าใหม่หากโฟลเดอร์มีไฟล์เก่าอยู่ | ลบไดเรกทอรี `build` (`rm -rf build`) หรือใช้ `cmake --fresh` (CMake 3.24+) |
| **CTest cannot find tests** | `add_test()` ไม่ได้ถูกเรียกใช้หรือไฟล์ executable ของการทดสอบไม่คอมไพล์ | ตรวจสอบว่า `add_test(NAME MyTest COMMAND MyTestExe)` ปรากฏใน `CMakeLists.txt` และ target สร้างสำเร็จ |
| **Parallel builds race on custom commands** | คำสั่ง custom บางตัวไม่ได้ระบุ `DEPENDS` ทำให้เกิดความล้มเหลวที่ไม่แน่นอน | เพิ่ม `add_custom_command(... DEPENDS ...)` อย่างเหมาะสม |

การเข้าใจความแตกต่างเหล่านี้ทำให้คุณแยกแยะระหว่าง build ที่ไม่เสถียรและ pipeline CI ที่แข็งแรงได้อย่างชัดเจน

## Visual Overview (Alt text includes primary keyword)

![แผนภาพแสดงขั้นตอนการกำหนดค่า, สร้าง, และทดสอบโครงการ CMake](/images/cmake-workflow.png "แผนผังการทำงานของการสร้างโครงการ CMake")

## Recap – สิ่งที่คุณได้เรียนรู้

เราเริ่มจากคำถามหลัก: *how to build CMake project* ตั้งแต่ต้นจนจบ ตอนนี้คุณรู้วิธี **configure CMake** ด้วยการสร้าง out‑of‑source ที่สะอาด, **build CMake** ด้วย flag `--build` สากล, และ **run CTest** ด้วยเอาต์พุตแบบ verbose เพื่อยืนยันว่าทุกอย่างทำงานได้ คุณยังมีสคริปต์พร้อมใช้ที่เชื่อมสามขั้นตอนเข้าด้วยกัน ทำให้คุณมี workflow **cmake build and test** ที่ครบวงจร

## What’s Next?

- **เพิ่มการรายงาน coverage** – ผสาน `gcov` หรือ `llvm-cov` แล้วให้ CTest เผยผลลัพธ์
- **Cross‑compilation** – สำรวจ `-DCMAKE_TOOLCHAIN_FILE` เพื่อสร้างบนอุปกรณ์ฝังตัว
- **สร้างแพคเกจ** – ใช้ `cpack` เพื่อบรรจุไบนารีของคุณสำหรับการแจกจ่าย
- **การบูรณาการ CI** – คัดลอกสคริปต์ไปยัง workflow ของ GitHub Actions แล้วดูการทำงานอัตโนมัติในทุก Pull Request

คุณสามารถทดลองกับประเภทการสร้างต่าง ๆ, เพิ่มการทดสอบเพิ่ม, หรือเปลี่ยนซอร์สตัวอย่างเป็นโปรเจกต์ของคุณเอง รูปแบบที่เราอธิบายวันนี้ใช้ได้กับโค้ดเบสที่ใช้ CMake ใด ๆ ไม่ว่าจะเป็นยูทิลิตี้เล็ก ๆ หรือระบบหลายโมดูลขนาดใหญ่

ขอให้สนุกกับการสร้าง และขอให้การ build ด้วย CMake ของคุณทำซ้ำได้เสมอ!

## What Should You Learn Next?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดที่ทำงานได้เต็มรูปแบบพร้อมคำอธิบายขั้นตอน‑ต่อ‑ขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโปรเจกต์ของคุณเอง

- [วิธีส่งออก LaTeX จาก Word – คู่มือขั้นตอน‑ต่อ‑ขั้นตอน](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [วิธีบันทึก Markdown จาก DOCX – คู่มือขั้นตอน‑ต่อ‑ขั้นตอน](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [วิธีแสดงเวอร์ชัน Aspose.Words ใน Python และ .NET: คู่มือขั้นตอน‑ต่อ‑ขั้นตอน](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}