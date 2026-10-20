---
category: general
date: 2026-07-06
description: Xây dựng dự án CMake từng bước. Tìm hiểu cách cấu hình CMake, cách biên
  dịch CMake và cách chạy CTest để kiểm thử đáng tin cậy.
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: vi
og_description: Xây dựng dự án CMake nhanh chóng với các bước rõ ràng. Hướng dẫn này
  chỉ cách cấu hình CMake, cách biên dịch CMake và cách chạy CTest.
og_title: 'Xây dựng dự án CMake: Hướng dẫn cấu hình, xây dựng và kiểm thử'
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
title: 'Xây dựng dự án CMake: Cấu hình, Xây dựng & Kiểm thử'
url: /vi/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Xây dựng dự án CMake: Cấu hình, Xây dựng & Kiểm thử

Bạn đã bao giờ tự hỏi làm thế nào để **build CMake project** mà không phải mất hàng giờ tìm kiếm trên StackOverflow? Bạn không phải là người duy nhất. Hầu hết các nhà phát triển đều gặp khó khăn tương tự khi họ cố chuyển từ một `CMakeLists.txt` đơn giản sang một pipeline xây dựng có thể tái tạo.

Trong tutorial này chúng ta sẽ đi qua toàn bộ quy trình—*cách cấu hình CMake*, *cách xây dựng CMake*, và *cách chạy CTest*—để bạn có được một bản build sạch, có thể lặp lại và chạy trên bất kỳ máy nào. Khi kết thúc, bạn sẽ có một ví dụ hoạt động mà bạn có thể sao chép‑dán vào repository của mình, không cần script bổ sung.

## Yêu cầu trước — Những gì bạn cần trước khi bắt đầu

Trước khi chúng ta bắt đầu, hãy chắc chắn bạn có:

- Phiên bản CMake mới (3.20 trở lên) – các phiên bản cũ thiếu một số flag chúng ta sẽ dùng.
- Trình biên dịch C++ được hỗ trợ trên nền tảng của bạn (gcc, clang, MSVC, v.v.).
- Một terminal hoặc command‑prompt có quyền truy cập tới `cmake` và `ctest`.
- (Tùy chọn) Git để clone repository mẫu nếu bạn muốn theo dõi cùng nguồn chính xác.

Nếu bất kỳ mục nào còn thiếu, hãy cài đặt ngay; nếu không bạn sẽ gặp lỗi “command not found” sau này, và điều đó không bao giờ vui.

## Bước 1: Cấu hình dự án CMake (cấu hình Release)

Điều đầu tiên bạn làm khi *cách cấu hình CMake* là cho CMake biết nguồn code nằm ở đâu và bạn muốn các artefact build được đặt ở đâu. Flag `-S` chỉ tới thư mục nguồn, `-B` tạo một thư mục build riêng, và `-D CMAKE_BUILD_TYPE=Release` buộc build tối ưu.

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**Tại sao điều này quan trọng:** Giữ source và build tách biệt (`out‑of‑source` builds) ngăn việc sửa đổi nguồn nhầm và giúp việc dọn dẹp thư mục build trở nên đơn giản. Flag `Release` cũng báo cho compiler bật tối ưu hoá, điều thường bạn muốn cho binary cuối cùng.

> **Mẹo chuyên nghiệp:** Nếu bạn cần một bản build Debug để gỡ lỗi, chỉ cần đổi `Release` thành `Debug`. Cùng một lệnh vẫn hoạt động—CMake sẽ xử lý phần còn lại.

## Bước 2: Xây dựng dự án đã cấu hình

Bây giờ bước cấu hình đã tạo ra tất cả các makefile hoặc file dự án Visual Studio cần thiết, bạn có thể thực sự biên dịch mã. Tùy chọn `--build` trừu tượng hoá công cụ build nền tảng (`make`, `ninja`, `MSBuild`, v.v.), vì vậy cùng một lệnh hoạt động trên Linux, macOS và Windows.

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**Điều gì đang diễn ra phía sau?** CMake đọc file `CMakeCache.txt` được tạo ở bước trước, xác định công cụ build phù hợp, và gọi nó với các flag đúng. Đây là cốt lõi của *cách xây dựng CMake*—bạn không cần nhớ đang dùng `make` hay `ninja`; CMake sẽ lo cho bạn.

Nếu bạn muốn tăng tốc trên máy đa nhân, thêm `-- -j$(nproc)` (Linux/macOS) hoặc `-- /m` (Windows) sau lệnh:

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## Bước 3: Chạy các bài kiểm thử mẫu với đầu ra chi tiết

Kiểm thử là nơi mà lý thuyết gặp thực tiễn. CMake đi kèm với `ctest`, một driver kiểm thử có thể phát hiện và chạy bất kỳ test nào được thêm bằng `add_test()` trong `CMakeLists.txt` của bạn. Để thực thi các test và xem đầu ra chi tiết, dùng helper `-E chdir` để chuyển vào thư mục build trước:

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**Tại sao dùng `--verbose`?** Nó in ra dòng lệnh của mỗi test, mã thoát, và bất kỳ đầu ra nào mà test tự viết. Điều này rất cần thiết khi bạn đang học *cách chạy CTest* vì nó cho thấy chính xác những gì đang diễn ra phía sau.

Đầu ra điển hình trông như sau:

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

Nếu một test thất bại, log chi tiết sẽ bao gồm lệnh gây lỗi và bất kỳ thông báo lỗi nào, giúp việc gỡ lỗi nhanh hơn rất nhiều.

## Bước 4: Tự động hoá toàn bộ quy trình (Tùy chọn)

Đối với nhiều dự án, bạn sẽ muốn một lệnh một‑dòng để cấu hình, build và test cùng lúc. Bạn có thể đạt được điều này bằng một script Bash (hoặc PowerShell) đơn giản:

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

Lưu lại dưới tên `run_all.sh`, cấp quyền thực thi (`chmod +x run_all.sh`), và bạn sẽ có một pipeline **cmake build and test** có thể tái tạo, có thể đưa vào bất kỳ hệ thống CI nào (GitHub Actions, GitLab CI, Azure Pipelines, bạn muốn).

## Các trường hợp đặc biệt & Những lỗi thường gặp

| Tình huống | Điều cần chú ý | Cách khắc phục |
|-----------|-------------------|-----|
| **Thiếu trình biên dịch** | CMake dừng lại với thông báo “No CMAKE_CXX_COMPILER could be found.” | Cài đặt một trình biên dịch (`sudo apt install build-essential` trên Ubuntu, `xcode-select --install` trên macOS). |
| **Thư mục out‑of‑source đã tồn tại** | CMake có thể từ chối cấu hình lại nếu thư mục chứa các file cũ. | Xóa thư mục `build` (`rm -rf build`) hoặc chạy `cmake --fresh` (CMake 3.24+). |
| **CTest không tìm thấy test** | `add_test()` chưa được gọi hoặc executable test không biên dịch được. | Kiểm tra rằng `add_test(NAME MyTest COMMAND MyTestExe)` xuất hiện trong `CMakeLists.txt` và target được build. |
| **Build song song gây race trên custom command** | Một số custom command không được đánh dấu `DEPENDS`, dẫn tới lỗi không xác định. | Thêm các mục `add_custom_command(... DEPENDS ...)` phù hợp. |

Hiểu được những tinh tế này tạo nên sự khác biệt giữa một build lỗi lỏng và một pipeline CI vững chắc.

## Tổng quan trực quan (Alt text bao gồm từ khóa chính)

![Sơ đồ mô tả luồng cấu hình, xây dựng và kiểm thử một dự án CMake](/images/cmake-workflow.png "Sơ đồ quy trình Build CMake Project")

## Tóm tắt – Những gì bạn đã học

Chúng ta bắt đầu với câu hỏi cốt lõi: *cách build CMake project* từ đầu. Khi kết thúc, bạn đã biết cách **cấu hình CMake** với một build out‑of‑source sạch sẽ, **xây dựng CMake** bằng flag `--build` đa nền tảng, và **chạy CTest** với đầu ra chi tiết để xác nhận mọi thứ hoạt động. Bạn cũng có một script sẵn sàng sử dụng để liên kết ba bước lại, cung cấp cho bạn một workflow **cmake build and test** hoàn chỉnh.

## Tiếp theo là gì?

- **Thêm báo cáo coverage** – tích hợp `gcov` hoặc `llvm-cov` và để CTest công bố kết quả.
- **Cross‑compilation** – khám phá `-DCMAKE_TOOLCHAIN_FILE` để build trên thiết bị nhúng.
- **Tạo package** – dùng `cpack` để đóng gói binary cho việc phân phối.
- **Tích hợp CI** – sao chép script vào workflow GitHub Actions và quan sát tự động hoá chạy trên mỗi pull request.

Hãy thoải mái thử nghiệm các loại build khác nhau, thêm nhiều test hơn, hoặc thay thế source mẫu bằng dự án của bạn. Các mẫu chúng ta đã đề cập hôm nay áp dụng cho bất kỳ codebase nào dựa trên CMake, dù là một tiện ích nhỏ hay một hệ thống đa module quy mô lớn.

Chúc bạn build vui vẻ, và mong các build CMake của bạn luôn có thể tái tạo!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây bao quát các chủ đề liên quan chặt chẽ, dựa trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã nguồn hoàn chỉnh cùng các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách xuất LaTeX từ Word – Hướng dẫn từng bước](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [Cách lưu Markdown từ DOCX – Hướng dẫn từng bước](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Cách hiển thị phiên bản Aspose.Words trong Python và .NET: Hướng dẫn từng bước](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}