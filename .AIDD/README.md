# AIDD - AI-Driven Development Docs

> Lightweight framework for organizing project documentation.
> Designed for multi-audience readability and scalability.

---

## Structure

```
.AIDD/
├── README.md                      # This file - framework overview
├── 1-research-plan.md             # Phase 1 workflow
├── 2-implement.md                 # Phase 2 workflow
├── docs/                          # Source of truth (group by module)
├── changes/                       # Proposals & drafts
└── archived/                      # Implemented history
```

## Directory Roles

| Folder | Role | Lifecycle |
|--------|------|-----------|
| `docs/` | Source of truth. Current state of the system. | Living, always up-to-date |
| `changes/` | Proposals, drafts, research. Work-in-progress. Naming: `NNN-feature-name/` (auto-increment, AI generates or user suggests). | Temporary, until approved & implemented |
| `archived/` | Implemented proposals. Historical reference. | Permanent, read-only |

---

## `docs/` Organization

Group by **module** (mirrors system architecture). Each module is a folder.

```
docs/
├── backend/
│   ├── README.md              # Business overview (non-technical)
│   ├── architecture.md        # Technical: stack, file tree, config
│   ├── api-endpoints.md       # Technical: API contracts
│   └── data-schema.md         # Technical: data models
├── frontend/
│   ├── README.md              # Business overview
│   ├── architecture.md        # Technical: stack, structure, routing
│   └── components.md          # Technical: component catalog
└── agent/
    ├── README.md              # Business overview
    ├── gemini-acp/            # Sub-feature (complex → subfolder)
    │   ├── README.md
    │   └── acp-protocol.md
    └── cache-layer.md         # Sub-feature (simple → file)
```

### Scaling Rule

Khi thêm feature/integration vào module:
- **Đơn giản** → thêm 1 file `.md` vào module folder
- **Phức tạp** → thêm 1 subfolder với `README.md` + files phụ
- `README.md` của module cập nhật link → xong

Subfolder cũng theo cùng format 2 tầng: `README.md` = business overview, detail files = technical. Nếu subfolder đủ nhỏ, có thể dùng 1 README.md chứa cả hai — agent nên hỏi user trước khi quyết định.

Không giới hạn file name, file type, hay số lượng. Chỉ cần link từ `README.md`.

### Doc Format by Audience

#### Module docs (`docs/`) — chia 2 tầng

**`README.md` = Business overview** — dành cho PM, PO, Stakeholder. Không có code, file tree, hay config.

| Section | Nội dung |
|---------|----------|
| Summary | 1-2 câu: module này làm gì |
| Capabilities | Liệt kê chức năng chính (bullet points, non-technical) |
| Key Flows | Luồng chính mô tả bằng ngôn ngữ business (user làm gì → hệ thống trả gì) |
| Detail Files | Links tới các file technical bên dưới |

**Detail files = Technical** — dành cho Dev, Tech Lead. Tên file tự do, nội dung technical.

| File ví dụ | Nội dung |
|------------|----------|
| `architecture.md` | Stack, file tree, config, how to run |
| `api-endpoints.md` | API contracts, request/response schemas |
| `components.md` | Component catalog, wireframes, state management |
| `data-schema.md` | Data models, relationships, lifecycle |

Business user đọc `README.md` → đủ hiểu module làm gì. Dev đọc detail files → đủ implement.

#### Change docs (`changes/`, `archived/`) — technical-first, business-anchored

Audience chính là Dev, nhưng phải có Goals ở đầu để anchor vào business value.

| Section | Audience | Nội dung |
|---------|----------|----------|
| Summary | Everyone | 1-2 câu mô tả change |
| Goals | Business + Dev | Mục tiêu business — tại sao làm, đo lường bằng gì |
| Acceptance Criteria | Dev, QA | Checklist verify — technical language OK |
| Decisions | Dev | Trade-offs đã quyết định (bảng Q&A) |
| Technical Approach | Dev | Architecture, code snippets, file changes |
| Edge Cases | Dev | Xử lý ngoại lệ |

PM đọc Summary + Goals → biết đang làm đúng hướng. Dev đọc 100% → đủ implement.

---

## Workflow: 2 Phases

```
Phase 1                    Gate              Phase 2
Research & Plan ──→ [changes/] ──→ Approve ──→ Implement
                                                  │
                              Update docs/ ←──────┘
                              Move to archived/
```

| Phase | Input | Output | Detail |
|-------|-------|--------|--------|
| 1. Research & Plan | Idea / requirement | Docs in `changes/` | See [1-research-plan.md](./1-research-plan.md) |
| 2. Implement | Approved docs | Code + updated `docs/` | See [2-implement.md](./2-implement.md) |

