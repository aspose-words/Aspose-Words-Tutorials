---
category: general
date: 2026-09-30
description: Bật chế độ khôi phục để mở tài liệu Word bị hỏng bằng Aspose.Words. Tìm
  hiểu cách khôi phục các tệp docx bị hỏng một cách an toàn và đáng tin cậy.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- open corrupted word document
- recover corrupted docx
- how to open corrupted docx
- load document with recovery
language: vi
lastmod: 2026-09-30
og_description: Kích hoạt chế độ khôi phục để mở tài liệu Word bị hỏng bằng Aspose.Words.
  Hướng dẫn này trình bày từng bước cách khôi phục các tệp docx bị hỏng và giữ cho
  quy trình làm việc của bạn ổn định.
og_image_alt: Code snippet showing Aspose.Words recovery mode enabled for a corrupted
  DOCX
og_title: Bật chế độ khôi phục để mở tài liệu Word bị hỏng
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Enable recovery mode to open a corrupted Word document using Aspose.Words.
    Learn how to recover corrupted docx files safely and reliably.
  headline: Enable recovery mode to open a corrupted Word document
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document recovery
title: Bật chế độ khôi phục để mở tài liệu Word bị hỏng
url: /vi/python/document-options-and-settings/enable-recovery-mode-to-open-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bật chế độ khôi phục để mở tài liệu Word bị hỏng

Nếu bạn cần **bật chế độ khôi phục** khi mở một tài liệu Word bị hỏng, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác bằng Aspose.Words cho Python. Dù tệp bị hỏng trong quá trình truyền tải hay được chỉnh sửa bằng chương trình không tương thích, việc bật chế độ khôi phục cho phép thư viện cố gắng sửa chữa tài liệu thay vì ném ra ngoại lệ.

Trong hướng dẫn này bạn sẽ học cách **mở tệp word bị hỏng**, **khôi phục nội dung docx bị hỏng**, và hiểu các tùy chọn kiểm soát quá trình **load document with recovery**. Các bước này hoạt động với Aspose.Words 23.10 (phiên bản mới nhất tại thời điểm viết) và chỉ yêu cầu môi trường Python tiêu chuẩn.

## Các điều kiện tiên quyết

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* Python 3.9 hoặc mới hơn đã được cài đặt.
* Aspose.Words for Python via .NET (`aspose-words`) đã được cài (`pip install aspose-words`).
* Một tệp DOCX đã biết là bị hỏng (để thử nghiệm, bạn có thể đổi tên một tệp `.docx` hợp lệ thành `.zip` và phá vỡ XML một cách thủ công).

> **Mẹo chuyên nghiệp:** Giữ một bản sao lưu của tệp gốc. Chế độ khôi phục sẽ thay đổi tài liệu trong bộ nhớ nhưng không ghi lại lại nguồn trừ khi bạn lưu nó một cách rõ ràng.

## Bước 1: Nhập thư viện và tạo LoadOptions

Điều đầu tiên bạn phải làm là nhập `aspose.words` và khởi tạo một đối tượng `LoadOptions`. Đối tượng này chứa tất cả các cài đặt ảnh hưởng đến cách tệp được đọc.

```python
import aspose.words as aw

# Create load options – this is where we will enable recovery mode
load_options = aw.loading.LoadOptions()
```

*Lý do quan trọng:* `LoadOptions` là cổng vào để tinh chỉnh bộ phân tích. Nếu không có nó, Aspose.Words sẽ sử dụng chế độ nghiêm ngặt mặc định, dừng lại khi gặp bất kỳ lỗi cấu trúc nào.

## Bước 2: Bật chế độ khôi phục

Đặt thuộc tính `recovery_mode` thành `RecoveryMode.RECOVER`. Điều này yêu cầu bộ tải cố gắng tự động sửa các phần bị hỏng như nút XML thiếu, quan hệ bị phá vỡ, hoặc luồng bị cắt ngắn.

```python
# Enable recovery mode – the core of “enable recovery mode” for this tutorial
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
```

Bật chế độ khôi phục **không** đảm bảo tài liệu sẽ hoàn hảo, nhưng nó làm tăng đáng kể khả năng bạn vẫn có thể trích xuất văn bản, hình ảnh hoặc bảng.

## Bước 3: Tải DOCX có khả năng bị hỏng với các tùy chọn đã cấu hình

Bây giờ sử dụng hàm khởi tạo `Document` chấp nhận cả đường dẫn tệp và thể hiện `LoadOptions`.

```python
# Path to the corrupted file – replace with your actual location
corrupted_path = "YOUR_DIRECTORY/corrupted.docx"

try:
    # Load the document using the recovery‑enabled options
    document = aw.Document(corrupted_path, load_options)
    print("Document loaded successfully with recovery mode.")
except aw.core.exceptions.InvalidOperationException as ex:
    # If recovery fails, the library throws an exception
    print(f"Failed to load document even with recovery mode: {ex}")
```

*Lý do quan trọng:* Khối `try/except` minh họa **cách mở docx bị hỏng** một cách an toàn. Nếu không bật chế độ khôi phục, cùng một lời gọi sẽ ngay lập tức ném ngoại lệ, làm dừng chương trình của bạn.

## Bước 4: Xác minh nội dung đã khôi phục (tùy chọn nhưng nên làm)

Sau khi tải, bạn nên kiểm tra xem tài liệu có chứa nội dung có ý nghĩa hay không. Cách nhanh là trích xuất văn bản thuần và in ra một vài ký tự đầu tiên.

```python
# Extract plain text to verify recovery
text = document.get_text()
if text.strip():
    print("Recovered text preview (first 200 chars):")
    print(text[:200])
else:
    print("Document appears empty after recovery – further inspection may be needed.")
```

Nếu đầu ra hiển thị một đoạn xem trước hợp lý, bạn có thể tiếp tục xử lý tài liệu (ví dụ: chuyển sang PDF, trích xuất bảng, v.v.). Nếu văn bản rỗng, tệp có thể đã vượt quá mức có thể sửa và bạn có thể cần yêu cầu một bản sao mới.

## Bước 5: Lưu tài liệu đã sửa (nếu bạn muốn một bản sạch)

Khi bạn hài lòng với nội dung đã khôi phục, có thể lưu một DOCX mới, sạch sẽ. Bước này là tùy chọn nhưng thường hữu ích cho các quy trình downstream.

```python
repaired_path = "YOUR_DIRECTORY/repaired.docx"
document.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Việc lưu tạo ra một tệp mới không còn chứa lỗi gây ra chế độ khôi phục.

## Các trường hợp đặc biệt và mẹo bổ sung

| Tình huống                               | Cách tiếp cận đề xuất |
|----------------------------------------|----------------------|
| **Tệp không phải là DOCX** (ví dụ, `.doc`) | Sử dụng `aw.loading.LoadOptions.file_format = aw.LoadFormat.DOC` trước khi tải. |
| **Chỉ khôi phục một phần**              | Sau khi tải, kiểm tra `document.get_text()` và `document.get_page_count()`. Nếu số trang là 0, tài liệu có thể không thể khôi phục. |
| **Tài liệu lớn**                    | Bật `load_options.memory_optimization = aw.loading.MemoryOptimizationMode.OPTIMIZE` để giảm sử dụng RAM trong quá trình khôi phục. |
| **Cần ghi lại những gì đã được sửa**      | Đặt `load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER` và sau đó đọc `document.get_last_save_options().recovery_log` (nếu có) để biết chi tiết. |

> **Cảnh báo:** Chế độ khôi phục có thể lặng lẽ loại bỏ các yếu tố không hỗ trợ (ví dụ, phông chữ thiếu). Nếu độ chính xác hình ảnh là quan trọng, hãy so sánh tệp đã sửa với phiên bản đã biết tốt.

## Ví dụ hoàn chỉnh hoạt động

Kết hợp mọi thứ lại, đây là một script tự chứa mà bạn có thể chạy ngay:

```python
import aspose.words as aw

def open_corrupted_docx(path: str, output_path: str = None):
    """Load a corrupted DOCX with recovery mode and optionally save a repaired copy."""
    # 1. Configure load options
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # 2. Attempt to load the document
    try:
        doc = aw.Document(path, load_options)
        print("✅ Document loaded with recovery mode.")
    except aw.core.exceptions.InvalidOperationException as err:
        print(f"❌ Unable to recover document: {err}")
        return None

    # 3. Verify recovered content
    txt = doc.get_text()
    if txt.strip():
        print("📄 Text preview (first 200 chars):")
        print(txt[:200])
    else:
        print("⚠️ Document appears empty after recovery.")

    # 4. Save a clean copy if requested
    if output_path:
        doc.save(output_path)
        print(f"💾 Repaired file saved to {output_path}")

    return doc

if __name__ == "__main__":
    corrupted_file = "YOUR_DIRECTORY/corrupted.docx"
    repaired_file = "YOUR_DIRECTORY/repaired.docx"
    open_corrupted_docx(corrupted_file, repaired_file)
```

Chạy script sẽ in ra thông báo thành công, một đoạn trích ngắn, và tạo `repaired.docx` trong cùng thư mục.

## Kết luận

Bây giờ bạn đã biết cách **bật chế độ khôi phục** để **mở tài liệu word bị hỏng**, **khôi phục nội dung docx bị hỏng**, và an toàn **load document with recovery** bằng Aspose.Words cho Python. Các bước chính—tạo `LoadOptions`, bật `RecoveryMode.RECOVER`, và xử lý ngoại lệ—tạo thành một mẫu đáng tin cậy mà bạn có thể tái sử dụng trong bất kỳ quy trình tự động nào.

Tiếp theo, hãy khám phá các chủ đề liên quan như **chuyển đổi tài liệu đã khôi phục sang PDF**, **trích xuất bảng bằng `DocumentVisitor`**, hoặc **xử lý hàng loạt thư mục chứa các tệp bị hỏng**. Tất cả đều dựa trên nền tảng chế độ khôi phục đã được trình bày ở đây.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn khỏe mạnh!


## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, dựa trên các kỹ thuật đã được minh họa trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [how to recover docx – set recovery mode & open corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [recover damaged docx with Aspose.Words – set recovery mode and load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [Recover corrupted DOCX with Aspose.Words LoadOptions – Complete C# Guide](/words/english/net/programming-with-loadoptions/recover-corrupted-docx-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}