---
category: general
date: 2026-10-04
description: Kích hoạt chế độ khôi phục trong Aspose.Words để phục hồi an toàn tài
  liệu Word bị hỏng. Thực hiện theo hướng dẫn từng bước với mã Python đầy đủ và giải
  thích.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: vi
lastmod: 2026-10-04
og_description: Bật chế độ khôi phục để phục hồi tài liệu Word bị hỏng bằng Aspose.Words.
  Hướng dẫn này trình bày mã Python chính xác, lý do nó hoạt động và cách xử lý các
  trường hợp đặc biệt.
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: Kích hoạt chế độ khôi phục để phục hồi tài liệu Word bị hỏng – hướng dẫn
  đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: Bật chế độ khôi phục để phục hồi tài liệu Word bị hỏng
url: /vi/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bật chế độ khôi phục để phục hồi tài liệu Word bị hỏng

Nếu bạn cần **bật chế độ khôi phục** khi tải một tệp Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác với Aspose.Words for Python. Bằng cách bật chế độ khôi phục, bạn có thể **phục hồi tài liệu Word bị hỏng** mà nếu không sẽ gây ra ngoại lệ.

Trong các phần sau, bạn sẽ học:

* Các lớp và thuộc tính kiểm soát hành vi khôi phục.  
* Cách tải một tệp `.docx` có khả năng bị hỏng mà không làm ứng dụng của bạn sập.  
* Mẹo khắc phục các vấn đề tải thường gặp và tùy chỉnh chiến lược khôi phục.

> **Prerequisite** – Bạn đã cài đặt Aspose.Words for Python (`pip install aspose-words`) và có hiểu biết cơ bản về I/O tệp trong Python.

## Chế độ khôi phục làm gì và tại sao bạn nên bật nó

Aspose.Words phân tích cấu trúc nội bộ của tệp Word trước khi đưa ra đối tượng `Document`. Khi tệp bị hỏng—thiếu phần, XML bị phá vỡ, hoặc quan hệ không hợp lệ—bộ phân tích có thể:

| Chế độ | Hành vi |
|------|------------|
| `STRICT` | Ném ngoại lệ ngay khi phát hiện dấu hiệu hỏng. |
| `IGNORE_ERRORS` | Bỏ qua các phần không đọc được nhưng có thể mất nội dung một cách im lặng. |
| `RECOVER` (tùy chọn **bật chế độ khôi phục**) | Cố gắng xây dựng lại tài liệu, giữ lại càng nhiều nội dung càng tốt và hiển thị chế độ đã chọn qua `load_options.recovery_mode`. |

`RECOVER` là lựa chọn được khuyến nghị khi bạn phải **phục hồi các tệp tài liệu Word bị hỏng** để xử lý tiếp theo, chẳng hạn như trích xuất văn bản hoặc chuyển đổi sang PDF.

## Bước 1: Tạo LoadOptions và bật chế độ khôi phục

Bước đầu tiên là khởi tạo `LoadOptions` và đặt thuộc tính `recovery_mode` thành `RecoveryMode.RECOVER`. Điều này báo cho thư viện vào đường dẫn khôi phục trong quá trình phân tích.

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**Tại sao điều này quan trọng:**  
Nếu bạn bỏ qua bước này và tài liệu bị hỏng, hàm khởi tạo `aw.Document(...)` sẽ ném `InvalidOperationException`. Bật chế độ khôi phục ngăn ngừa sự cố và cung cấp cho bạn một đối tượng `Document` đã được sửa chữa một phần mà bạn vẫn có thể làm việc.

## Bước 2: Tải tài liệu có khả năng bị hỏng bằng các tùy chọn đã chỉ định

Truyền thể hiện `load_options` vào hàm khởi tạo `Document`. Trình tải bây giờ sẽ tự động áp dụng thuật toán khôi phục.

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**Mẹo:** Thay thế `YOUR_DIRECTORY` bằng đường dẫn tuyệt đối hoặc tương đối mà runtime của bạn có thể truy cập. Nếu tệp không tồn tại, Aspose.Words sẽ ném `FileNotFoundError` trước khi tới logic khôi phục.

## Bước 3: Xác minh rằng chế độ khôi phục đã được áp dụng

Bạn có thể xác nhận chế độ đang hoạt động bằng cách kiểm tra `load_options.recovery_mode`. Điều này hữu ích cho việc ghi log hoặc xử lý có điều kiện sau này trong pipeline.

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**Kết quả mong đợi**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

Nếu kết quả hiển thị `RECOVER`, bạn đã thành công **bật chế độ khôi phục** và tài liệu hiện đã sẵn sàng cho các xử lý tiếp theo (ví dụ: trích xuất văn bản, chuyển đổi sang PDF, hoặc lưu bản sao đã sửa).

## Bước 4 (tùy chọn): Lưu bản sao đã sửa để sử dụng sau

Sau khi tải, bạn có thể muốn lưu tài liệu đã được khôi phục để không phải lặp lại bước khôi phục.

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Việc lưu tạo ra một tệp `.docx` mới mà Aspose.Words coi là hợp lệ, có thể mở trong Microsoft Word mà không có cảnh báo.

## Các câu hỏi thường gặp và xử lý trường hợp biên

| Câu hỏi | Trả lời |
|----------|--------|
| **Nếu tài liệu hoàn toàn không đọc được thì sao?** | Ngay cả trong chế độ `RECOVER`, một số tệp không thể sửa chữa. Đối tượng `Document` sẽ được tạo nhưng có thể chỉ chứa một trang trống duy nhất. Kiểm tra `doc.get_page_count()` để xác nhận nội dung. |
| **Tôi có thể chuyển sang `IGNORE_ERRORS` sau khi đã tải không?** | Không. Chế độ khôi phục phải được đặt **trước** khi hàm khởi tạo `Document` chạy. Tạo một thể hiện `LoadOptions` mới nếu bạn cần chiến lược khác. |
| **Chế độ khôi phục có ảnh hưởng đến hiệu năng không?** | Có, nó gây thêm một chút chi phí vì thư viện cố gắng tái cấu trúc các phần bị hỏng. Ảnh hưởng này là không đáng kể đối với hầu hết các tệp (< 2 MB). |
| **Cách tiếp cận này có độc lập ngôn ngữ không?** | Khái niệm tương tự tồn tại trong các API .NET, Java và Node.js (`LoadOptions.RecoveryMode`). Cú pháp mã thay đổi, nhưng logic vẫn giống nhau. |

## Mẹo chuyên nghiệp: Ghi log thông tin khôi phục chi tiết

Aspose.Words cung cấp một `LoadOptions.recovery_callback` nhận các thông điệp chi tiết về mỗi bước khôi phục. Kết nối callback này có thể giúp bạn chẩn đoán lý do một tài liệu cụ thể thất bại.

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

Bây giờ mọi sửa chữa nội bộ (ví dụ: “Removed duplicate relationship”) sẽ được in ra console.

## Ví dụ đầy đủ, có thể chạy ngay

Kết hợp tất cả các phần lại, dưới đây là một script tự chứa mà bạn có thể sao chép‑dán và chạy ngay lập tức:

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

Chạy script sẽ in ra chế độ khôi phục, số trang và danh sách các từ được trích xuất từ tài liệu đã sửa. Nếu bạn đặt `save_repaired=True`, một tệp sạch mới sẽ xuất hiện bên cạnh tệp gốc.

## Kết luận

Bạn giờ đã biết cách **bật chế độ khôi phục** trong Aspose.Words for Python và đáng tin cậy **phục hồi các tệp tài liệu Word bị hỏng**. Các bước chính là:

1. Tạo `LoadOptions` và đặt `recovery_mode` thành `RECOVER`.  
2. Tải tệp `.docx` bằng các tùy chọn đó.  
3. Xác nhận chế độ và tùy chọn lưu bản sao đã sửa.

Từ đây, bạn có thể khám phá các chủ đề tiếp theo như **trích xuất văn bản từ tài liệu đã khôi phục**, **chuyển đổi nó sang PDF**, hoặc **tự động khôi phục hàng loạt** cho các thư viện tài liệu lớn.

---


## Bạn nên học gì tiếp theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Khôi phục DOCX bị hỏng – Hướng dẫn đầy đủ để bật chế độ khôi phục & lấy trang](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [Khôi phục DOCX bị hỏng – Mở & Tải tài liệu Word](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [khôi phục docx hỏng với Aspose.Words – đặt chế độ khôi phục và tùy chọn tải](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}