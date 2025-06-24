FFmpeg là một công cụ dòng lệnh mạnh mẽ dùng để xử lý video, âm thanh và các định dạng đa phương tiện khác. Dưới đây là các lệnh FFmpeg cơ bản mà bạn nên biết khi mới bắt đầu:

---

## ⚙️ Cài đặt FFmpeg

* **Trên Ubuntu/Debian**:

  ```bash
  sudo apt update
  sudo apt install ffmpeg
  ```

* **Trên macOS (Homebrew)**:

  ```bash
  brew install ffmpeg
  ```

* **Trên Windows**:
  Tải từ [https://ffmpeg.org/download.html](https://ffmpeg.org/download.html), giải nén và thêm đường dẫn vào `PATH`.

---

## 📋 Kiểm tra phiên bản và thông tin

```
ffmpeg -version        # Kiểm tra phiên bản
```
```
ffmpeg -codecs         # Liệt kê các codec hỗ trợ
```
```
ffmpeg -formats        # Liệt kê định dạng hỗ trợ
```

---

## 🎬 Các lệnh FFmpeg cơ bản

### 1. **Chuyển đổi định dạng video**

```bash
ffmpeg -i input.mp4 output.avi
```

### 2. **Trích xuất âm thanh từ video**

```bash
ffmpeg -i input.mp4 -q:a 0 -map a output.mp3
```

### 3. **Cắt video (ví dụ: từ 00:01:00 đến 00:02:00)**

```bash
ffmpeg -i input.mp4 -ss 00:01:00 -to 00:02:00 -c copy output.mp4
```

### 4. **Giảm kích thước video**

```bash
ffmpeg -i input.mp4 -vf scale=1280:720 output.mp4
```

### 5. **Nén video (giảm dung lượng)**

```bash
ffmpeg -i input.mp4 -vcodec libx265 -crf 28 output.mp4
```

> `CRF`: chất lượng – càng cao thì file càng nhỏ (giảm chất lượng).

### 6. **Ghép nhiều video lại với nhau**

Tạo file danh sách:

```
file 'video1.mp4'
file 'video2.mp4'
```

Sau đó:

```bash
ffmpeg -f concat -safe 0 -i list.txt -c copy output.mp4
```

### 7. **Thêm phụ đề vào video**

```bash
ffmpeg -i input.mp4 -vf subtitles=subs.srt output.mp4
```

### 8. **Ghi màn hình (trên Windows)**

```bash
ffmpeg -f gdigrab -framerate 30 -i desktop output.mp4
```

---

## 🧠 Một số tùy chọn hữu ích

| Tùy chọn           | Mô tả                              |
| ------------------ | ---------------------------------- |
| `-i`               | Chỉ định file đầu vào              |
| `-ss`              | Thời gian bắt đầu                  |
| `-t` hoặc `-to`    | Thời lượng / thời gian kết thúc    |
| `-vf`              | Filter video (như scale, crop,...) |
| `-af`              | Filter audio                       |
| `-c` hoặc `-codec` | Chỉ định codec dùng cho encode     |
| `-crf`             | Điều chỉnh chất lượng (0–51)       |

---

Nếu bạn có tác vụ cụ thể muốn làm với FFmpeg (ví dụ: làm video dọc cho TikTok, tách nhạc nền, chuyển GIF sang MP4...), mình có thể hướng dẫn chi tiết hơn. Bạn cần gì tiếp theo?
