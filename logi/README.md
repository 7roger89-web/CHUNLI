# LOGI — bản vá chờ tích hợp (kênh phân phối dự phòng)

Repo đích: **`7roger89-web/logistics-work-desk-arena`**, nhánh
`arena/85dbc833-logistics-work-desk-arena` (PR **#232**, base staging
`arena/ae5f9f47-logistics-work-desk-arena`).

## Vì sao bản vá nằm ở đây

Môi trường thực thi (Arena sandbox) **không có quyền ghi** lên repo đích:
`git push` bị từ chối (`403 Permission to 7roger89-web/… denied`), và các API
ghi (`git/blobs`, issue comment, `gh pr merge`) đều trả
`Resource not accessible by integration`. Vì vậy commit được tạo cục bộ, xuất
thành `git format-patch` và đưa lên nhánh session này để Owner/agent có quyền
áp dụng. Repo đích chỉ có thể nhận qua `git am`/`git apply` từ một máy có quyền.

## Hai commit chờ áp dụng (theo thứ tự)

| # | SHA (cục bộ trên repo đích) | Commit | Patch |
| --- | --- | --- | --- |
| 1 | `119689d` | `test(g15): independent acceptance challenge for approved-content integrity` | `g15-review/0001-….patch` |
| 2 | `7989e68` | `feat(journey): stage discussion and attachments shared by staff and the portal` | `journey-notes/0001-….patch` |

Parent chung: `968e7cfb945a2e2b269a2829576d86df021f27b5` (HEAD PR #232).

## Cách áp dụng

```bash
git clone https://github.com/7roger89-web/logistics-work-desk-arena.git
cd logistics-work-desk-arena
git checkout arena/85dbc833-logistics-work-desk-arena
git am /path/to/logi/g15-review/0001-*.patch
git am /path/to/logi/journey-notes/0001-*.patch
python -m pytest tests/test_customer_portal_g15_independent_challenge.py \
                 tests/test_journey_notes.py -q
```

## Nội dung tóm tắt

1. **G1.5 (PR #232) — kiểm chứng độc lập PASS.** 29 test challenge mới do actor
   khác tác giả bản sửa; sửa 1 test hồi quy thật ở HEAD PR; đột biến tắt kiểm
   tra hash nội dung làm 25 test FAIL. Full suite 38F/2115P → 35F/2148P.
   Đủ điều kiện tích hợp **staging** theo đánh giá của người kiểm chứng này.
2. **Trao đổi + chứng từ theo công đoạn** (lát phát triển tiếp theo):
   `core/journey_notes.py`, `views/journey_discussion.py`,
   `tests/test_journey_notes.py` (31 PASS, 3 đột biến FAIL), bằng chứng
   `evidence/journey-notes/README.md`. Full suite 34F/2178P.

Chi tiết đầy đủ nằm trong nội dung patch (docs/NEXT.md và evidence/).

## Trạng thái

- Staging: **CHƯA MERGE** — sandbox không có quyền merge; cần Owner hoặc agent
  có quyền ghi thực hiện `gh pr merge 232 --merge` sau khi áp dụng commit 1.
- `main`/production: không đụng vào. `CLOUD_QA=BLOCKED` (deployed SHA và DB
  identity của Cloud chưa được xác minh).
