# pro-launch

[English](README.md) | [简体中文](README.zh-CN.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | Tiếng Việt | [हिन्दी](README.hi.md)

<p align="center"><img src="docs/share.png" alt="pro-launch: from an idea to style frames" width="100%"></p>

Một skill cho Claude Code giúp đưa sản phẩm từ 0 lên 1 theo hướng **gu thẩm mỹ đặt lên hàng đầu**: định vị → đặt tên, tên miền & nhãn hiệu → tìm tham chiếu (ưu tiên GitHub/mã nguồn mở, sau đó đến App Store và các app đạt giải) → style bible → bản đồ tính năng → vòng lặp xây dựng UI/UX → tạo asset → QA trên thiết bị thật → video ra mắt → GTM → tăng trưởng → phát hành mã nguồn mở / lên App Store.

Vì sao có skill này: phần lớn sản phẩm do AI làm thất bại không phải vì code, mà vì (1) chưa từng nghiên cứu tham chiếu thật, (2) mô hình tự chấm điểm bài của chính mình, (3) những lần người dùng sửa đi sửa lại không bao giờ được ghi lại. Mỗi giai đoạn ở đây đều buộc phải tạo ra **sản phẩm thật** và vượt qua một **cổng kiểm tra** (`scripts/phase_gate.py`) trước khi sang giai đoạn tiếp theo.

## Cài đặt

Trong Claude Code:

```
/plugin marketplace add jack-reson8/pro-launch
/plugin install pro-launch@pro-launch
```

Hoặc cài như một thư mục skill thông thường:

```bash
git clone https://github.com/jack-reson8/pro-launch /tmp/pro-launch && cp -R /tmp/pro-launch/plugins/pro-launch/skills/pro-launch ~/.claude/skills/
```
Sau đó hãy nói với Claude Code những câu như "làm cho tôi một app", "UI này trông quá đại trà", "tìm tham chiếu", "đặt tên cho sản phẩm này", "lên kế hoạch ra mắt".

**Codex** (CLI hoặc app ChatGPT trên máy tính):

```bash
codex plugin marketplace add jack-reson8/pro-launch
codex plugin add pro-launch@pro-launch
```

Hoặc sao chép `plugins/pro-launch/skills/pro-launch` vào `~/.codex/skills/`. Skill tuân theo chuẩn mở [Agent Skills](https://agentskills.io), nên chạy được trong Claude Code, Codex và mọi agent đọc được SKILL.md.

**Các agent khác** (Cursor, Gemini CLI, GitHub Copilot và các agent khác được skills CLI hỗ trợ):

```bash
npx skills add jack-reson8/pro-launch
```

## Bên trong có gì

Skill nằm ở `plugins/pro-launch/skills/pro-launch`; mọi đường dẫn bên dưới đều tính từ thư mục này.

- `SKILL.md` – các giai đoạn, cổng kiểm tra, nguyên tắc sắt đá
- `references/01-13` – mỗi giai đoạn một trang (gồm nhãn hiệu & sở hữu trí tuệ cho việc ra mắt nhiều quốc gia)
- `references/mistakes.md`, `user-repeated-demands.md` – sổ ghi lại các sai lầm thực tế và những yêu cầu người dùng hay lặp lại
- `scripts/` – cổng giai đoạn, công cụ tải poster App Store, công cụ lưu trữ tham chiếu, kiểm tra trùng tên miền / tên trên App Store, quy trình tách nền→vector (Vision + vtracer + svgo)
- `examples/`, `assets/` – ví dụ thực tế và mẫu

Giấy phép MIT. Hoạt động như skill của Claude Code; phương pháp này có thể áp dụng cho các agent khác.
