# Hướng Dẫn Sử Dụng — KnowledgeBase Skill

Hướng dẫn chi tiết cách sử dụng skill KnowledgeBase để quản lý ghi chú trong Obsidian vault.

---

## Mục Lục

1. [Cài Đặt](#1-cài-đặt)
2. [Workflow: Save — Lưu Ghi Chú](#2-workflow-save--lưu-ghi-chú)
3. [Workflow: Search — Tìm Kiếm](#3-workflow-search--tìm-kiếm)
4. [Workflow: Daily Journal — Nhật Ký](#4-workflow-daily-journal--nhật-ký)
5. [Workflow: Daily Note — Ghi Chú Hàng Ngày](#5-workflow-daily-note--ghi-chú-hàng-ngày)
6. [Workflow: Watch Later — Xem Sau](#6-workflow-watch-later--xem-sau)
7. [Cấu Trúc Thư Mục](#7-cấu-trúc-thư-mục)
8. [Mẹo Sử Dụng](#8-mẹo-sử-dụng)

---

## 1. Cài Đặt

### Bước 1: Cấu hình vault path

Mở file `CONFIG.example.md` và thay thế `{{YOUR_VAULT_PATH}}` bằng đường dẫn thực tế đến Obsidian vault của bạn:

```yaml
VAULT_PATH: "/duong/dan/den/vault/cua/ban"
```

### Bước 2: Tạo cấu trúc thư mục

Tạo các thư mục sau trong vault (nếu chưa có):

```
Vault/
├── 1. Inbox/
├── 2. Notes/
│   ├── Reference/
│   ├── Learning/
│   ├── Ideas/
│   └── Conversations/
├── 3. Projects/
├── 4. Journal/
├── 5. Resources/
│   ├── Clippings/
│   └── Templates/
└── 7. Daily Notes/
```

### Bước 3: Đặt skill files

Copy thư mục `KnowledgeBase/` vào thư mục skills của Claude Code.

### Bước 4: Kiểm tra

Nói với Claude: **"save a test note about setup complete"** — nếu file được tạo trong vault, bạn đã cài đặt thành công.

---

## 2. Workflow: Save — Lưu Ghi Chú

### Cách dùng

Nói bất kỳ câu nào có ý "lưu" hoặc "ghi chú":

| Câu lệnh | Loại ghi chú | Thư mục |
|-----------|-------------|---------|
| "Save this note about..." | Reference | `2. Notes/Reference/` |
| "Save this learning..." | Learning | `2. Notes/Learning/` |
| "Save this idea..." | Idea | `2. Notes/Ideas/` |
| "Clip this article..." | Resource | `5. Resources/Clippings/` |
| "Save this..." (không rõ loại) | Inbox | `1. Inbox/` |

### Ví dụ

```
"Save this learning — Khi dùng Docker multi-stage build,
luôn copy package.json trước rồi mới run npm install
để tận dụng cache layer."
```

**Kết quả:**
- File: `{{VAULT_PATH}}/2. Notes/Learning/2026-03-12-docker-multi-stage-build-cache.md`
- Tags: `docker`, `devops`, `optimization`
- Tự động tìm ghi chú liên quan trong vault và tạo wikilinks

### Định dạng file

Mỗi ghi chú được lưu với YAML frontmatter:

```markdown
---
title: "Docker Multi-stage Build Cache"
date: 2026-03-12
type: learning
tags:
  - docker
  - devops
  - optimization
source: "conversation"
connections:
  related: ["[[2026-03-01-docker-best-practices]]"]
  status: connected
---

# Docker Multi-stage Build Cache

Khi dùng Docker multi-stage build, luôn copy package.json
trước rồi mới run npm install để tận dụng cache layer.

## Connections

**Related:** [[2026-03-01-docker-best-practices]]
```

---

## 3. Workflow: Search — Tìm Kiếm

### Các chế độ tìm kiếm

| Chế độ | Câu lệnh | Ví dụ |
|--------|----------|-------|
| **Từ khóa** | "search vault for..." | "search vault for docker" |
| **Tag** | "find notes tagged..." | "find notes tagged with devops" |
| **Tên file** | "find note named..." | "find note named docker" |
| **Ngày** | "find notes from..." | "find notes from 2026-03-10" |
| **Loại** | "find all learnings" | "find all learning notes" |

### Ví dụ

```
"Tìm trong vault về rate limiting"
```

**Kết quả:**

```
### Search Results for "rate limiting"

3 notes found:

1. **API Rate Limiting Best Practices** (2026-03-05)
   Type: reference | Tags: api, security, performance
   > When implementing rate limiting, use a sliding window...
   Path: {{VAULT_PATH}}/2. Notes/Reference/2026-03-05-api-rate-limiting.md

2. ...
```

---

## 4. Workflow: Daily Journal — Nhật Ký

### Cách dùng

Nói **"journal entry"** theo sau bởi nội dung:

```
"Journal entry — Hôm nay deploy xong feature authentication mới.
Team feedback tích cực. Cần follow up vấn đề performance
ở dashboard page."
```

### Đặc điểm

- **Một file mỗi ngày:** `{{VAULT_PATH}}/4. Journal/2026-03-12.md`
- **Nhiều entry trong ngày:** Mỗi entry có timestamp riêng
- **Giữ nguyên giọng viết:** AI không chỉnh sửa nội dung của bạn

### Định dạng

```markdown
---
title: "Journal — March 12, 2026"
date: 2026-03-12
type: journal
tags:
  - journal
  - daily
---

# Journal — March 12, 2026

## 14:30

Hôm nay deploy xong feature authentication mới...

## 17:45

Follow up meeting với team về performance...
```

### Weekly Review — Đánh giá tuần

Nói **"weekly review"** để tạo file đánh giá tuần từ template.

---

## 5. Workflow: Daily Note — Ghi Chú Hàng Ngày

### Cách dùng

Daily Note được **tự động cập nhật** mỗi khi bạn lưu bất kỳ ghi chú nào. Bạn cũng có thể xem trực tiếp:

```
"What did I save today?"
"Show today's daily note"
```

### Đặc điểm

- **Tự động:** Mỗi lần Save hoặc Journal, daily note được cập nhật
- **Tổng hợp:** Hiển thị tất cả ghi chú, journal, resources trong ngày
- **Backfill:** Nói "backfill daily notes" để tạo daily notes cho ghi chú cũ

### Định dạng

```markdown
# March 12, 2026

## Journal

- [[2026-03-12]] — Journal entry

## Notes

- [[2026-03-12-docker-multi-stage-build-cache]] — Docker Multi-stage Build Cache
- [[2026-03-12-api-design-patterns]] — API Design Patterns

## Resources

- [[2026-03-12-scaling-postgres-tips]] — Scaling Postgres Tips
```

---

## 6. Workflow: Watch Later — Xem Sau

### Thêm vào hàng đợi

```
"Watch later: https://example.com/video-about-ai"
"Read later: https://example.com/article-about-rust"
```

### Xem hàng đợi

```
"Show my queue"
"What's in my queue?"
```

### Xử lý item trong hàng đợi

```
"Process the first article from my queue"
```

→ Tự động fetch nội dung, lưu vào vault, và chuyển từ Queue sang Processed.

### Các loại content

| Loại | Ví dụ |
|------|-------|
| `article` | Blog post, tin tức, essay |
| `video` | YouTube, Vimeo |
| `podcast` | Audio content |
| `thread` | Twitter/X thread, Reddit |
| `paper` | Academic paper, PDF |
| `tool` | GitHub repo, app, product |

---

## 7. Cấu Trúc Thư Mục

```
{{VAULT_PATH}}/
├── 1. Inbox/              ← Quick captures, watch-later queue
│   └── watch-later.md     ← File quản lý hàng đợi
├── 2. Notes/
│   ├── Reference/         ← Ghi chú tham khảo
│   ├── Learning/          ← Bài học, TIL
│   ├── Ideas/             ← Ý tưởng, brainstorm
│   └── Conversations/     ← Tóm tắt cuộc họp
├── 3. Projects/           ← Ghi chú theo dự án
├── 4. Journal/            ← Nhật ký hàng ngày
├── 5. Resources/
│   ├── Clippings/         ← Bài viết đã clip
│   └── Templates/         ← Templates (weekly review, etc.)
└── 7. Daily Notes/        ← Tổng hợp hàng ngày (tự động)
```

---

## 8. Mẹo Sử Dụng

### Ghi chú nhanh
Nếu không chắc loại ghi chú, cứ nói **"save this"** — nó sẽ được lưu vào Inbox. Bạn có thể sắp xếp lại sau trong Obsidian.

### Tận dụng tags
Skill tự động tạo 2-5 tags cho mỗi ghi chú. Dùng Search workflow để tìm theo tag khi cần.

### Vault connections
Mỗi ghi chú mới sẽ tự động tìm và link đến ghi chú liên quan đã có trong vault bằng `[[wikilinks]]`. Điều này giúp xây dựng knowledge graph tự nhiên.

### Kết hợp với Obsidian Graph View
Sau khi tích lũy đủ ghi chú, mở Graph View trong Obsidian để thấy mối liên hệ giữa các ghi chú — rất hữu ích cho việc khám phá ý tưởng mới.

### URL luôn được lưu
Nếu trong cuộc hội thoại có đề cập URL nào, skill sẽ tự động lưu vào phần References của ghi chú. Không bao giờ mất link.

### Watch Later workflow
Đừng đọc tất cả ngay — queue lại và xử lý vào cuối tuần. Skill sẽ tự động link bài đã xử lý với ghi chú đã lưu.
