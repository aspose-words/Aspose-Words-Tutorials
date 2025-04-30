---
"date": "2025-03-29"
"description": "Tìm hiểu cách tối ưu hóa việc lưu tài liệu với Aspose.Words cho Python bằng định dạng luồng XAML và lệnh gọi lại tiến trình. Nâng cao hiệu quả trong việc quản lý tài liệu."
"title": "Tối ưu hóa việc lưu tài liệu trong Python&#58; Aspose.Words XAML Flow và Progress Callbacks"
"url": "/vi/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---

# Cách tối ưu hóa việc lưu tài liệu trong Python bằng Aspose.Words: XAML Flow và Progress Callbacks

## Giới thiệu

Bạn đang muốn quản lý hiệu quả việc chuyển đổi tài liệu bằng Python? Bạn đang gặp khó khăn trong việc xử lý hình ảnh và theo dõi tiến trình trong quá trình lưu tài liệu? Hướng dẫn này sẽ hướng dẫn bạn cách tối ưu hóa việc lưu tài liệu bằng Aspose.Words for Python, tập trung vào hai tính năng mạnh mẽ: `XamlFlowSaveOptions` với chức năng Gọi lại tiến trình lưu thư mục hình ảnh và tài liệu.

Hướng dẫn toàn diện này hoàn hảo cho các nhà phát triển muốn cải thiện quy trình xử lý tài liệu của mình bằng thư viện Aspose.Words.

**Những gì bạn sẽ học được:**
- Cách lưu tài liệu theo định dạng luồng XAML trong khi quản lý tài nguyên hình ảnh.
- Triển khai lệnh gọi lại tiến trình trong quá trình lưu tài liệu để tránh các thao tác kéo dài.
- Thiết lập và cấu hình Aspose.Words cho Python trong môi trường phát triển của bạn.
- Ứng dụng thực tế của các tính năng này trong hệ thống quản lý tài liệu.

Hãy cùng tìm hiểu các điều kiện tiên quyết trước khi bắt đầu viết mã!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

### Thư viện và phiên bản bắt buộc
- **Aspose.Words cho Python**: Đảm bảo bạn có phiên bản 23.3 trở lên.
- **Trăn**: Khuyến nghị sử dụng phiên bản 3.6 trở lên.

### Yêu cầu thiết lập môi trường
- Trình soạn thảo mã như VSCode hoặc PyCharm.
- Kiến thức cơ bản về lập trình Python.

### Điều kiện tiên quyết về kiến thức
- Làm quen với các khái niệm xử lý tài liệu.
- Hiểu biết về xử lý tệp và quản lý thư mục trong Python.

## Thiết lập Aspose.Words cho Python

Để bắt đầu sử dụng Aspose.Words, bạn cần cài đặt qua pip. Mở terminal hoặc dấu nhắc lệnh và chạy:

```bash
pip install aspose-words
```

### Các bước xin cấp giấy phép
1. **Dùng thử miễn phí**: Truy cập giấy phép tạm thời [đây](https://purchase.aspose.com/temporary-license/) với mục đích thử nghiệm.
2. **Mua**: Để sử dụng lâu dài, hãy mua giấy phép [đây](https://purchase.aspose.com/buy).
3. **Khởi tạo và thiết lập cơ bản**:
   - Tải tài liệu của bạn bằng cách sử dụng `aw.Document()`.
   - Cấu hình tùy chọn lưu khi cần thiết.

## Hướng dẫn thực hiện

Phần này sẽ hướng dẫn bạn cách triển khai hai tính năng chính của hướng dẫn này: XamlFlowSaveOptions với Thư mục hình ảnh và Gọi lại tiến trình lưu tài liệu.

### Tính năng 1: XamlFlowSaveOptions với Thư mục hình ảnh

#### Tổng quan
Tính năng này cho phép bạn lưu tài liệu theo định dạng luồng XAML trong khi chỉ định thư mục hình ảnh và bí danh. Tính năng này lý tưởng để quản lý hiệu quả các tài liệu lớn có hình ảnh nhúng.

#### Các bước thực hiện

##### Bước 1: Nhập các thư viện cần thiết
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### Bước 2: Xác định lớp gọi lại ImageUriPrinter
Lớp này đếm và chuyển hướng luồng hình ảnh đến thư mục bí danh được chỉ định trong quá trình chuyển đổi.

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # loại: List[str]

        def image_saving(self, args: aw.saving.ImageSavingArgs):
            self.resources.append(args.image_file_name)
            with open(f"{self.images_folder_alias}/{args.image_file_name}", "wb") as image_stream:
                args.image_stream = image_stream
            args.keep_image_stream_open = False

    def test_image_folder(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Rendering.docx")
        callback = self.ImageUriPrinter(YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias")

        options = aw.saving.XamlFlowSaveOptions()
        options.images_folder = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolder"
        options.images_folder_alias = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias"
        options.image_saving_callback = callback

        os.makedirs(options.images_folder_alias, exist_ok=True)
        
        doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.image_folder.xaml", options)

        for resource in callback.resources:
            print(f"{callback.images_folder_alias}/{resource}")
```
**Tùy chọn cấu hình chính:**
- `images_folder`: Chỉ định thư mục lưu hình ảnh.
- `images_folder_alias`: Đặt đường dẫn bí danh được sử dụng trong quá trình chuyển đổi tài liệu.

##### Mẹo khắc phục sự cố
- Đảm bảo tất cả các thư mục đều tồn tại trước khi chạy mã để tránh lỗi không tìm thấy tệp.
- Kiểm tra quyền ghi trong thư mục đầu ra của bạn.

### Tính năng 2: Gọi lại tiến trình lưu tài liệu

#### Tổng quan
Tính năng này quản lý quá trình lưu bằng cách sử dụng lệnh gọi lại tiến trình, cho phép bạn hủy các hoạt động lưu kéo dài.

#### Các bước thực hiện

##### Bước 1: Xác định lớp SavingProgressCallback
Lớp học sẽ theo dõi thời lượng lưu tài liệu và hủy nếu vượt quá thời gian quy định.

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # Thời gian tối đa cho phép tính bằng giây

        def notify(self, args: aw.saving.DocumentSavingArgs):
            canceled_at = datetime.now()
            elapsed_seconds = (canceled_at - self.saving_started_at).total_seconds()
            if elapsed_seconds > self.max_duration:
                raise OperationCanceledException(f"estimated_progress = {args.estimated_progress}; canceled_at = {canceled_at}")

    def test_progress_callback(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        parameters = [
            (aw.SaveFormat.XAML_FLOW, "xamlflow"),
            (aw.SaveFormat.XAML_FLOW_PACK, "xamlflowpack"),
        ]

        for save_format, ext in parameters:
            doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Big document.docx")
            save_options = aw.saving.XamlFlowSaveOptions(save_format)
            save_options.progress_callback = self.SavingProgressCallback()

            try:
                doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.progress_callback.{ext}", save_options)
            except OperationCanceledException as e:
                print(e)
```
**Tùy chọn cấu hình chính:**
- `save_format`: Chọn giữa XAML_FLOW và XAML_FLOW_PACK.
- `progress_callback`: Theo dõi tiến trình lưu để xử lý các hoạt động dài.

##### Mẹo khắc phục sự cố
- Điều chỉnh `max_duration` dựa trên kích thước và độ phức tạp của tài liệu.
- Xử lý các trường hợp ngoại lệ một cách khéo léo để cung cấp thông báo lỗi có thông tin hữu ích.

## Ứng dụng thực tế

Sau đây là một số trường hợp sử dụng thực tế của các tính năng này:
1. **Hệ thống quản lý tài liệu**: Quản lý hiệu quả các tài liệu lớn có nhúng hình ảnh bằng cách chỉ định thư mục hình ảnh, nâng cao hiệu suất và khả năng tổ chức.
2. **Công cụ báo cáo tự động**:Sử dụng lệnh gọi lại tiến trình để đảm bảo báo cáo được tạo trong khung thời gian chấp nhận được, cải thiện trải nghiệm của người dùng.
3. **Mạng lưới phân phối nội dung**: Tối ưu hóa việc chuyển đổi tài liệu để phân phối trên web đồng thời quản lý tài nguyên hiệu quả.

## Cân nhắc về hiệu suất

Để tối ưu hóa hiệu suất khi sử dụng Aspose.Words với Python:
- **Quản lý bộ nhớ**: Theo dõi việc sử dụng tài nguyên và quản lý bộ nhớ hiệu quả bằng cách loại bỏ các đối tượng sau khi sử dụng.
- **Hoạt động I/O tập tin**: Giảm thiểu các thao tác đọc/ghi tệp để cải thiện tốc độ.
- **Xử lý hàng loạt**: Xử lý tài liệu theo từng đợt khi có thể để giảm chi phí chung.

## Phần kết luận

Trong hướng dẫn này, chúng tôi đã khám phá cách tối ưu hóa việc lưu tài liệu với Aspose.Words for Python bằng XAML Flow và các lệnh gọi lại tiến trình. Bằng cách triển khai các tính năng này, bạn có thể nâng cao hiệu quả của quy trình xử lý tài liệu, quản lý tài nguyên hiệu quả và đảm bảo các hoạt động kịp thời.