# oci-a1-grabber

Auto-retry tạo Oracle Cloud **ARM A1.Flex (Always Free)** instance tới khi có capacity.

Repo này **public** để dùng GitHub Actions miễn phí không giới hạn (private chỉ 2000 phút/tháng).
Chỉ chứa 1 workflow — KHÔNG có source code hay secret nào trong repo.

## Cách hoạt động
- Workflow loop thử `oci compute instance launch` mỗi 60s, mỗi job ~50 phút.
- Hết giờ job tự re-dispatch job kế tiếp → chạy 24/7 gần như không gap.
- Chiếm được chỗ → ping Slack kèm Public IP → chuỗi dừng (instance đã tồn tại).

## Setup
Thêm 8 secret ở **Settings → Secrets and variables → Actions** (xem comment đầu file workflow),
rồi **Actions → Run workflow**. Khi có VM xong → **Disable workflow**.
