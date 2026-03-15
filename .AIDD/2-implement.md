# 2 - Implement

> **Prerequisite:** Read [README.md](./README.md) for framework structure and rules.
> All paths are relative to `.AIDD/`.

---

## Flow

### Implement

1. Read approved docs in `changes/NNN-feature-name/`.
2. **Clarify & Confirm:** Ask any technical questions. ⛔ **STOP — Get approval before coding.**
3. Implement according to the docs.
4. Test per Acceptance Criteria and stated edge cases.
5. ⛔ **STOP — Wait for user to verify implementation works correctly.**

### Archive & Update

1. Identify which module in `docs/` this feature belongs to.
2. Choose how to merge into `docs/`:
   - **New module**: create `docs/[module-name]/` with README.md + files
   - **Extend existing module**: add file or subfolder to `docs/[module-name]/`, update README.md links. Subfolder mới cũng theo format 2 tầng (xem Scaling Rule trong [README.md](./README.md)).
3. **When updating `docs/`** (xem format trong [README.md](./README.md)):
   - **README.md = business overview** — chỉ sửa khi module thêm/bỏ capability lớn. Không thêm code, file paths, hay implementation detail vào đây.
   - **Technical content → detail files** — merge vào file phù hợp (`architecture.md`, `api-endpoints.md`, ...). Nếu chưa có file phù hợp → tạo mới và link từ README.
   - **Merge into correct section** — tìm section đúng trong detail file, không append cuối file.
   - **Detail file quá dài (~80+ dòng)** → tách thêm file hoặc subfolder.
4. Update related modules in `docs/` if cross-module impact.
5. Move `changes/NNN-feature-name/` → `archived/NNN-feature-name/`.

---

## Rules

1. **Implement only.** Do not move or archive files during implementation step.
2. **Update cross-module docs** before archiving.
3. **Do not delete, only move** to `archived/`.
4. **Update docs/ README links** when adding new files or subfolders.

---

## Agent Operational Rules

1. **First Principles + 80/20** — solve from fundamentals; focus on the 20% that delivers 80% of value. Keep code simple, avoid over-engineering. Keep docs concise — only essential decisions, no verbose explanations.
2. **Clarify until clear** — ask questions until requirements are fully understood; summarize and get approval before drafting or making changes
3. **Context Mastery** — understand the repo structure, existing patterns, relevant docs before writing. Never assume.
4. **Never self-answer** — present questions and **WAIT** for user response. Do not assume answers or proceed without confirmation.