---
category: general
date: 2026-07-16
description: บทแนะนำการสร้าง cmake x64 แสดงวิธีใช้ CMake เพื่อสร้างโซลูชัน Visual
  Studio 2022 และสร้างโครงการ VS บนโฮสต์ 64‑บิต รวมขั้นตอนการตั้งค่าไดเรกทอรีซอร์สด้วย
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: th
lastmod: 2026-07-16
og_description: 'อธิบายการสร้าง cmake x64: เรียนรู้วิธีตั้งค่าไดเรกทอรีซอร์ส, สร้างโซลูชัน
  Visual Studio 2022, และคอมไพล์โปรเจกต์ VS บนโฮสต์ 64‑บิต'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake build x64 – คู่มือแบบขั้นตอนต่อขั้นตอนในการสร้างและคอมไพล์โซลูชัน
  VS 2022
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
title: cmake build x64 – คู่มือครบวงจรสำหรับการสร้างและคอมไพล์โปรเจกต์ VS 2022
url: /th/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – คู่มือฉบับสมบูรณ์สำหรับการสร้างและสร้างโครงการ VS 2022

เคยสงสัย **how to use CMake** ว่าจะผลิตโซลูชัน Visual Studio 64‑bit ได้อย่างไรโดยไม่ต้องบีบหัวของคุณไหม? คุณไม่ได้เป็นคนเดียว ในบทแนะนำนี้เราจะพาคุณผ่านขั้นตอน **cmake build x64** ที่ตั้งค่าไดเรกทอรีซอร์ส, รันเจนเนอเรเตอร์สำหรับ Visual Studio 2022, และสุดท้ายสร้างโครงการ VS — ทั้งหมดด้วยคำสั่ง Bash ที่เรียบง่ายไม่กี่บรรทัด

เมื่อจบคู่มือนี้คุณจะมีสคริปต์ที่ทำซ้ำได้ซึ่งคุณสามารถใส่ลงในรีโพซิทอรีใดก็ได้ พร้อมกับความเข้าใจที่มั่นคงในแนวคิดพื้นฐานเพื่อให้คุณปรับแต่งตามความต้องการของคุณเอง

---

## สิ่งที่คุณจะได้เรียนรู้

- **Set source directory** อย่างถูกต้องเพื่อให้ CMake รู้ว่าไฟล์ `CMakeLists.txt` ของคุณอยู่ที่ไหน.  
- **cmake generate visual studio** – เรียกใช้เจนเนอเรเตอร์ Visual Studio 2022 ด้วยแฟล็ก host และ architecture ที่ถูกต้อง.  
- ทำการ **cmake build x64** ของโซลูชันที่สร้างขึ้น, โดยสามารถเลือกคอนฟิกูเรชัน Release ได้ตามต้องการ.  
- ทำความเข้าใจข้อผิดพลาดทั่วไปเมื่อคุณพยายาม **build vs project** บนเครื่อง 64‑bit.  

ไม่จำเป็นต้องมีความเชี่ยวชาญ CMake มาก่อน; เพียงเทอร์มินัลและการติดตั้ง Visual Studio เวอร์ชันล่าสุด

---

## ข้อกำหนดเบื้องต้น

| Requirement | Why it matters |
|-------------|----------------|
| CMake ≥ 3.20 | รองรับแฟล็ก `-Thost=` และ `-Ax64` ที่ใช้สำหรับการสร้างแบบ 64‑bit. |
| Visual Studio 2022 (Community, Professional, or Enterprise) | เจนเนอเรเตอร์ `Visual Studio 17 2022` ชี้ไปยังเวอร์ชันนี้. |
| A Bash‑compatible shell (Git Bash, WSL, PowerShell with `bash` alias) | สคริปต์ด้านล่างใช้ไวยากรณ์ Bash เพื่อความชัดเจน. |
| Source tree containing a valid `CMakeLists.txt` | CMake ไม่สามารถสร้างโซลูชันได้หากไม่มีไฟล์นี้. |

หากมีข้อใดขาดหายไป ให้ติดตั้งก่อน—CMake จาก <https://cmake.org/download/> และ VS 2022 จากตัวติดตั้งของ Microsoft

---

## ขั้นตอน 1 – ตั้งค่าไดเรกทอรีซอร์สและบิลด์ (`set source directory`)

ก่อนที่คุณจะเรียก CMake คุณต้องบอกให้มันรู้ **ที่ไหน** ที่จะค้นหาไฟล์โครงการ การกำหนดค่าพาธแบบคงที่ทำให้สคริปต์เปราะบาง ดังนั้นเราจะใช้ตัวแปรสภาพแวดล้อมที่คุณสามารถปรับตามโครงการได้

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **ทำไมสิ่งนี้ถึงสำคัญ:**  
> CMake ถือว่า *source directory* (`SRC_DIR`) เป็นรากของโครงการ. *build directory* (`BUILD_DIR`) คือที่ที่ไฟล์กลาง, แคช, และไฟล์ `.sln` สุดท้ายอยู่ การแยกแยะพวกมันออกจากกันช่วยป้องกันไม่ให้ต้นไม้ซอร์สของคุณถูกสกปรกและทำให้การทำความสะอาดง่ายดาย (`rm -rf "$BUILD_DIR"`).

คุณสามารถแทนที่ `YOUR_DIRECTORY` ด้วยพาธใดก็ได้ ไม่ว่าจะเป็นพาธเต็มหรือพาธสัมพันธ์; เพียงตรวจสอบให้แน่ใจว่าโฟลเดอร์นั้นมีไฟล์ `CMakeLists.txt`

---

## ขั้นตอน 2 – สร้างโซลูชัน Visual Studio 2022 (`cmake generate visual studio`)

ตอนนี้เราขอให้ CMake สร้างโซลูชัน VS 2022 ที่มุ่งเป้าไปที่ **x64**. แฟล็กสำคัญมีดังนี้:

- `-G "Visual Studio 17 2022"` – เลือกเจนเนอเรเตอร์ VS 2022.  
- `-Thost=x64` – บอก CMake ว่า *host* (IDE) ทำงานเป็นกระบวนการ 64‑bit.  
- `-Ax64` – บังคับให้โปรเจกต์ที่สร้างขึ้นคอมไพล์สำหรับสถาปัตยกรรม x64.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **อะไรเกิดขึ้นภายใน?**  
> CMake อ่านไฟล์ `CMakeLists.txt` จาก `$SRC_DIR`, แก้ไขการเรียก `add_executable()` และ `add_library()` ทั้งหมด, จากนั้นสร้างไฟล์ `.sln` และชุดไฟล์ `.vcxproj` ภายใน `$BUILD_DIR`. ไฟล์โปรเจกต์เหล่านี้พร้อมที่จะเปิดใน Visual Studio หรือคอมไพล์จากบรรทัดคำสั่งแล้ว.

หากคุณรันคำสั่งและเห็นรายการข้อความการกำหนดค่ายาวจนจบด้วย `-- Configuring done` และ `-- Generating done` คุณได้ทำขั้นตอน **cmake generate visual studio** สำเร็จแล้ว

---

## ขั้นตอน 3 – สร้างโซลูชันที่สร้างขึ้น (`cmake build x64`)

เมื่อมีโซลูชันแล้ว ขั้นตอนต่อไปที่สมเหตุสมผลคือการคอมไพล์ CMake สามารถควบคุมการสร้างให้คุณได้ โดยมอบหมายให้ MSBuild ทำงานเบื้องหลัง

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **ทำไมต้องใช้ `--config Release`?**  
> โปรเจกต์ Visual Studio รองรับหลายคอนฟิกูเรชัน (Debug, Release, RelWithDebInfo, ฯลฯ). การระบุ `Release` ทำให้ไบนารีถูกปรับให้เหมาะกับการผลิตและไฟล์ `.exe` หรือ `.dll` ที่ได้จะอยู่ภายใต้โฟลเดอร์ `Release/` ในโครงสร้างบิลด์.

หากคุณต้องการบิลด์แบบ Debug ให้แทนที่ `Release` ด้วย `Debug`. คำสั่งทำงานเช่นเดียวกัน, แสดงให้เห็นว่า **how to use CMake** สำหรับคอนฟิกูเรชันต่าง ๆ เพียงแค่สลับแฟล็กนี้

---

## ขั้นตอน 4 – ตรวจสอบการบิลด์ (`build vs project` sanity check)

การคอมไพล์ที่สำเร็จควรทำให้คุณได้ไฟล์ executable หรือ library. มาตรวจสอบว่ามีอยู่จริงหรือไม่:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **ข้อผิดพลาดทั่วไป:**  
> - ลืมรันขั้นตอนเจนเนอเรเตอร์หลังจากแก้ไข `CMakeLists.txt` จะทำให้การตรวจสอบนี้ล้มเหลว.  
> - การผสมผสาน toolchain 32‑bit และ 64‑bit อาจทำให้เกิดข้อผิดพลาดของลิงเกอร์; ควรทำให้ `-Ax64` สอดคล้องกันเสมอ.  
> - หากคุณเห็นข้อผิดพลาด “MSB3073” มักหมายถึงขั้นตอนหลังการบิลด์ (เช่นการคัดลอกทรัพยากร) ล้มเหลว — ตรวจสอบผลลัพธ์เพื่อหาสาเหตุ.

---

## ขั้นตอน 5 – ทำความสะอาดและรันใหม่ (ทำซ้ำบน `cmake build x64`)

ระหว่างการพัฒนา คุณมักต้องการสร้างใหม่จากศูนย์ วิธีที่สะอาดที่สุดคือการลบโฟลเดอร์บิลด์และเริ่มใหม่:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **เคล็ดลับ:**  
> การเพิ่ม `-DCMAKE_BUILD_TYPE=Release` ไปยังคำสั่งเจนเนอเรเตอร์เป็นทางเลือกสำหรับเจนเนอเรเตอร์หลายคอนฟิกเช่น Visual Studio, แต่ก็อาจเป็นประโยชน์เมื่อคุณสลับไปใช้เจนเนอเรเตอร์แบบคอนฟิกเดียวเช่น Ninja.

---

## ขั้นตอน 6 – ขยายสคริปต์ (สถานการณ์ `cmake generate visual studio` ขั้นสูง)

ถ้าโครงการของคุณอยู่ในซับ‑ไดเรกทอรี, หรือคุณต้องการส่งค่าสนิทกำหนดเอง? CMake ให้คุณทำเช่นนั้นด้วยอาร์กิวเมนต์ `-D`:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

ตอนนี้โซลูชัน VS ที่สร้างขึ้นจะมีแมโคร `MyFeature_ENABLED` ถูกกำหนด, และเป้าหมายการติดตั้งจะวางไฟล์ไว้ที่ `/opt/myapp`. สิ่งนี้แสดงให้เห็นถึงความยืดหยุ่นของ **how to use CMake** นอกเหนือจากขั้นตอนพื้นฐานสามขั้นตอน

---

## ผลลัพธ์ที่คาดหวัง

เมื่อคุณรันสคริปต์เต็มจากต้นจนจบ, เทอร์มินัลควรแสดงบางอย่างคล้ายกับ:

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

หากมีอะไรผิดพลาด, CMake จะส่งข้อความข้อผิดพลาดที่ชี้ไปยังบรรทัดที่ทำให้เกิดปัญหาใน `CMakeLists.txt` หรือส่วนประกอบ SDK ที่หายไป—เหมาะสำหรับการดีบักอย่างรวดเร็ว

---

## สรุป

เราได้ครอบคลุมทุกอย่างที่คุณต้องการทำ **cmake build x64**: ตั้งค่าไดเรกทอรีซอร์ส, เรียกขั้นตอน **cmake generate visual studio**, คอมไพล์ **build vs project** ที่ได้, และตรวจสอบผลลัพธ์ สคริปต์นี้กระชับ, พกพาได้, และพร้อมสำหรับการรวมเข้ากับ CI pipelines หรือเวิร์กโฟลว์การพัฒนาท้องถิ่น

ต่อไป, คุณอาจสำรวจ:

- เพิ่มการรัน unit‑test ด้วย `ctest`.  
- สลับไปใช้เจนเนอเรเตอร์ Ninja เพื่อการบิลด์เพิ่มทีเร็ว (`-G Ninja`).  
- ใช้ CMake presets (`CMakePresets.json`) เพื่อเก็บแฟล็กที่เราเพิ่งพิมพ์

อย่ากลัวที่จะทดลอง, ทำให้พัง, แล้วค่อยบิลด์ใหม่—เพราะนั่นคือวิธีที่เร็วที่สุดในการเรียนรู้ **how to use CMake** อย่างมีประสิทธิภาพ. สร้างสนุก!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้. แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโครงการของคุณเอง

- [สร้างตาราง](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [สร้างตารางพร้อมสไตล์](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [สร้างตารางพร้อมขอบ](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}