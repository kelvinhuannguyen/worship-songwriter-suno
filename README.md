# Worship Songwriter cho Suno

Skill viết mới hoặc đánh bóng lời nhạc worship / thờ phượng Cơ Đốc cho **Suno**. Dùng được trong Claude (claude.ai, app desktop, Cowork) và Claude Code.

- Lời tiếng Anh mộc mạc, đời thường nhưng sâu, chạm cảm xúc, theo khẩu quyết *"Sự thật lớn, chữ nhỏ"*
- Hook và cấu trúc giữ chân người nghe: giọng vào trong 10 giây đầu, chorus trước 1:05, có đoạn hạ xuống gần im rồi dâng lên, kết lặp lại câu mở đầu
- Song ngữ Hebrew cho kênh Messianic: 23 cụm đã kiểm tra, có ghi chú dạng nam/nữ theo người hát
- Bàn giao gồm: Style of Music, Exclude Styles, cài đặt Suno v6, lyrics có metatag, điểm WORSHIP-8, gói YouTube
- **v1.1:** học kỹ thuật từ các thánh ca và bài worship đỉnh cao (không chép lời), danh mục 29 thánh ca public domain kèm năm và giai điệu, quy trình "thánh ca + chorus mới", 19 preset phong cách (gospel, Celtic, Messianic, Afro, Latin…), lịch lễ Cơ Đốc và lễ Do Thái, kế hoạch series/album

*English: A Claude skill for writing new, or polishing existing, Christian worship lyrics for Suno. Lyrics are plain-spoken and emotional, built around a strong hook and a structure that keeps listeners. The skill supports optional Hebrew phrases (all verified) and outputs a Suno-ready package plus YouTube copy.*

---

## Cài đặt

### 1. Claude (claude.ai, app desktop, Cowork)

1. Tải file [`dist/worship-songwriter-suno.zip`](dist/worship-songwriter-suno.zip).
2. Mở **Customize → Skills** ([claude.ai/customize/skills](https://claude.ai/customize/skills)), chọn tải skill lên và chọn file `.zip` vừa tải.
3. Bật skill. Cần bật code execution trong cài đặt.

Skill nằm trong tài khoản nên dùng được ở mọi nơi bạn đăng nhập Claude.

### 2. Claude Code: cài như plugin (khuyên dùng, cập nhật dễ)

Chạy trong terminal:

```bash
claude plugin marketplace add kelvinhuannguyen/worship-songwriter-suno
claude plugin install worship-songwriter-suno@worship-skills
```

Hoặc gõ trong một phiên Claude Code:

```
/plugin marketplace add kelvinhuannguyen/worship-songwriter-suno
/plugin install worship-songwriter-suno@worship-skills
```

Lệnh gọi skill: `/worship-songwriter-suno:worship-songwriter-suno`. Claude cũng tự dùng skill khi bạn nhờ viết hoặc đánh bóng nhạc worship.

Cập nhật bản mới: `claude plugin marketplace update worship-skills`.

### 3. Claude Code: chép tay vào thư mục skill cá nhân

Chọn cách này **hoặc** cách 2, đừng cài cả hai (skill sẽ bị trùng).

**Windows (PowerShell):**
```powershell
git clone https://github.com/kelvinhuannguyen/worship-songwriter-suno "$env:TEMP\wss"
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null
Copy-Item -Recurse -Force "$env:TEMP\wss\plugins\worship-songwriter-suno\skills\worship-songwriter-suno" "$HOME\.claude\skills\"
```

**macOS / Linux:**
```bash
git clone https://github.com/kelvinhuannguyen/worship-songwriter-suno /tmp/wss
mkdir -p ~/.claude/skills
cp -r /tmp/wss/plugins/worship-songwriter-suno/skills/worship-songwriter-suno ~/.claude/skills/
```

Lệnh gọi skill: `/worship-songwriter-suno`.

---

## Cách dùng

Ví dụ câu lệnh:

- *"Đánh bóng bài này theo chuẩn Suno"* rồi dán lời và tag style
- *"Viết bài worship mới về chờ đợi lời cầu nguyện chưa được đáp, giọng nữ, có 2–3 câu Hebrew"*
- *"Làm bản Shorts 2:30 và bản soaking 30 phút từ bài HN59"*
- *"Làm gói YouTube: 3 tiêu đề, mô tả, chữ thumbnail, đoạn cắt Shorts"*

Skill có 4 chế độ: **Viết mới**, **Đánh bóng**, **Biến thể** (Shorts, soaking, acoustic, đổi giọng, thêm song ngữ) và **Gói phát hành** (YouTube).

## Cấu trúc repo

```
.claude-plugin/marketplace.json                      # marketplace "worship-skills"
plugins/worship-songwriter-suno/
  .claude-plugin/plugin.json                         # manifest plugin
  skills/worship-songwriter-suno/SKILL.md            # nội dung skill (bản gốc duy nhất)
dist/worship-songwriter-suno.zip                     # gói tải lên claude.ai
```

Sau khi sửa `SKILL.md`, tạo lại file zip:

```bash
cd plugins/worship-songwriter-suno/skills && rm -f ../../../dist/worship-songwriter-suno.zip && zip -r -X ../../../dist/worship-songwriter-suno.zip worship-songwriter-suno
```

Rồi tăng `version` trong `plugin.json` để Claude Code nhận bản mới.

## Lưu ý

- Thông số Suno trong skill theo Suno v6 (tháng 10/2026). Suno thay đổi nhanh, nên nếu giao diện khác thì giữ nguyên tắc.
- Muốn kiếm tiền từ bài hát thì phải tạo bài khi đang có gói Suno trả phí. Hãy kiểm tra điều khoản hiện hành của Suno và chính sách YouTube trước khi đăng.
