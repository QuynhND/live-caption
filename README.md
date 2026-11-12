# Live Captions

Phụ đề trực tiếp và dịch realtime cho Windows. Ứng dụng nghe âm thanh từ **loa** (cuộc họp, video, người khác nói) và **micro** (giọng của bạn), hiện phụ đề ở một cửa sổ nổi, bản dịch ở cửa sổ bên cạnh, và lưu toàn bộ nội dung thành file song ngữ.

Việc nhận dạng giọng nói chạy ngay trên máy bạn — âm thanh không được gửi đi đâu. Chỉ phần chữ cần dịch hoặc tóm tắt mới được gửi tới dịch vụ bạn chọn.

## Cài đặt

1. Tải file `LiveCaptions-…-win64.zip` mới nhất tại trang [Releases](https://github.com/QuynhND/live-caption/releases/latest).
2. Giải nén vào một thư mục bất kỳ (ví dụ `D:\LiveCaptions`; đừng đặt trong `Program Files`).
3. Chạy `LiveCaptions.exe`. Nếu Windows hiện cảnh báo *Windows protected your PC*, bấm **More info → Run anyway** (ứng dụng chưa được ký số).

Lần chạy đầu tiên ứng dụng tự tải mô hình nhận dạng giọng nói (0,6–1,6 GB), chờ tới khi dòng trạng thái báo **Sẵn sàng**.

**Máy có card NVIDIA:** cửa sổ chính sẽ hiện nút **Tải gói GPU** (1,3 GB, chỉ tải một lần). Nên tải: phụ đề nhanh và chính xác hơn rõ rệt. Máy không có card NVIDIA vẫn chạy được bằng CPU.

Yêu cầu: Windows 10 hoặc 11 (64-bit), có Internet cho lần đầu và khi dịch.

## Sử dụng

1. Bấm **● Bắt đầu**. Phụ đề hiện ngay khi có người nói: chữ nhạt là phần đang nghe, khi hết câu sẽ được thay bằng bản chính xác.
2. Bấm **■ Dừng** khi xong. Nội dung được lưu thành file; bấm **Mở file** để xem, **Thư mục** để mở nơi lưu.

Trên cửa sổ điều khiển:

| | |
|---|---|
| **Loa / Micro** | Chọn nguồn âm thanh cần ghi. Câu từ micro được đánh dấu `Tôi`. |
| **Ngôn ngữ** | Ngôn ngữ đang nói (mặc định English UK) → ngôn ngữ dịch (mặc định tiếng Việt). |
| **Dịch bằng** | Nguồn dịch, xem [bên dưới](#nguồn-dịch). |
| **Phụ đề gốc / Bản dịch** | Bật, tắt từng cửa sổ phụ đề. |
| **Tóm tắt** | Tóm tắt cuộc họp, xem [bên dưới](#tóm-tắt-cuộc-họp). |

Hai cửa sổ phụ đề: kéo để di chuyển, kéo mép để đổi cỡ, `A−` `A+` đổi cỡ chữ, 📌 giữ cửa sổ luôn nổi trên cùng. Phông chữ, màu chữ, màu nền, độ trong suốt: **Cài đặt → Giao diện** hoặc bấm chuột phải vào cửa sổ.

Mở ứng dụng lần thứ hai chỉ đưa cửa sổ đang chạy lên trước. Đóng cửa sổ điều khiển để thoát; nếu đang ghi, ứng dụng lưu xong rồi mới thoát.

## File lưu

Mỗi phiên tạo hai file, tự lưu vài giây một lần trong lúc ghi:

- **`.txt`** — bản gốc theo mốc thời gian, bên dưới là bản dịch, cuối cùng là tóm tắt (nếu có).
- **`.html`** — bản gốc và bản dịch đặt cạnh nhau theo từng dòng, có ô tìm kiếm và nút sao chép.

Trong **Cài đặt → Lưu trữ & Tóm tắt** bạn đổi được:

- **Thư mục lưu** — mặc định `Documents\Live Captions`.
- **Tên file** — mặc định `Live_captions_{ddmmyyyy}_{hhmmss}`. Gõ chữ bất kỳ kèm mã ngày giờ: `{ddmmyyyy}` `{yyyymmdd}` `{hhmmss}` `{hhmm}` hoặc từng phần `{dd}` `{mm}` `{yyyy}` `{hh}` `{mi}` `{ss}`. Ví dụ `Họp {yyyy}-{mm}-{dd} {hh}h{mi}` → `Họp 2026-11-12 09h30`. Tên trùng thì tự thêm `(2)`, `(3)`… chứ không ghi đè.

## Nguồn dịch

| Nguồn | Tốc độ | Cần gì |
|---|---|---|
| **Google Translate** (mặc định) | dưới 1 giây mỗi câu | Không cần gì |
| **Claude – gói subscription** | khoảng 5 giây mỗi câu | Máy đã cài và đăng nhập Claude Code |
| **Claude API** / **OpenAI** | tùy model | API key, nhập trong **Cài đặt → Dịch** |
| **Ollama** | tùy máy | Miễn phí; cài [Ollama](https://ollama.com) và tải một mô hình |

Google phù hợp cho họp thông thường. Các nguồn AI dịch theo ngữ cảnh, tự sửa từ nghe nhầm, hợp với nội dung chuyên ngành; khi dùng chúng, bản Google vẫn hiện trước rồi được thay bằng bản tinh chỉnh. API key được lưu trong Windows Credential Manager.

## Tóm tắt cuộc họp

Tóm tắt cần một nguồn AI. **Nếu máy chưa có nguồn nào, nút Tóm tắt bị tắt** — rê chuột lên nút để xem còn thiếu gì. Có ba cách bật:

- **Miễn phí:** cài [Ollama](https://ollama.com), mở Command Prompt và chạy `ollama pull qwen3:14b` (khoảng 9 GB, hợp với card 16 GB; card nhỏ hơn hãy chọn mô hình nhỏ hơn). Nội dung không rời máy.
- **Gói Claude đang có:** cài Claude Code và đăng nhập.
- **API key** của Claude hoặc OpenAI: nhập trong **Cài đặt → Dịch**.

Sau khi cài, vào **Cài đặt → Lưu trữ & Tóm tắt** bấm **Kiểm tra lại**. Ở đó cũng chọn được nguồn tóm tắt, ngôn ngữ tóm tắt và bật *Tự tóm tắt khi bấm Dừng*.

## Cập nhật

Khi có phiên bản mới, cửa sổ chính hiện nút **Cập nhật**: ứng dụng tự tải, thay file rồi mở lại. Cài đặt, API key, mô hình, gói GPU và các phiên đã lưu được giữ nguyên. Kiểm tra thủ công hoặc tắt việc tự kiểm tra trong **Cài đặt → Cập nhật**.

## Mẹo để phụ đề chính xác

- Điền tên riêng, tên sản phẩm, thuật ngữ vào **Cài đặt → Phụ đề → Từ điển thuật ngữ**. Đây là cách hiệu quả nhất.
- Dùng tai nghe khi họp, để micro không thu lại tiếng loa.
- Cần chính xác tối đa: chọn `large-v3` cho *Mô hình lượt chính xác* (tải thêm khoảng 3 GB, cần card NVIDIA).

## Lưu ý

- Đổi loa hoặc micro mặc định của Windows giữa chừng (ví dụ cắm tai nghe): bấm Dừng rồi Bắt đầu lại.
- Ứng dụng tách được *loa* và *micro*, chưa phân biệt từng người nói trong âm thanh loa.
- Google Translate là dịch vụ miễn phí không có cam kết; dùng dày đặc trong thời gian dài có thể bị giới hạn tạm thời.
