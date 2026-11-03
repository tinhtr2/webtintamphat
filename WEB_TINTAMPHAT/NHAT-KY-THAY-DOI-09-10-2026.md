# Nhật ký thay đổi trên site thật — 09/10/2026

## lynhuadanang.vn/blog
| Việc | Cách hoàn tác |
|---|---|
| 49 chuyển hướng Rank Math (48×301 về tintamphat.com, 1×410 /blog/wishlist/) | Rank Math › Chuyển hướng › chọn rule › Thùng rác |
| 28 + 11 bài sao chép, 4 sản phẩm sao chép, trang wishlist → Thùng rác | Bài viết / Sản phẩm / Trang › Thùng rác › Khôi phục (WordPress tự xoá vĩnh viễn sau 30 ngày) |
| Gỡ khối JSON lộ ở cuối 4 bài riêng (1350, 1340, 1332, 1320) | Sửa bài › Bản sửa đổi |
| Tắt plugin kk Star Ratings | Plugin › kk Star Ratings › Kích hoạt |
| Theme Nhà Máy kích hoạt (Flatsome vẫn còn) | Giao diện › Flatsome › Kích hoạt |
| Tuỳ chọn Nhà Máy: tên "Ly Giấy – Ly Nhựa Đà Nẵng", hotline 0933.420.456, VP 106 Ỷ Lan Nguyên Phi, xưởng Cụm CN Chợ Lò; ô "Thuộc công ty" để trống | Nhà Máy (menu trái) |
| Cài đặt › Đọc: trang chủ /blog/ = bài viết mới (trước là trang id 8) | Cài đặt › Đọc › Trang tĩnh = id 8 |
| Trang id 8 (trang chủ cũ) và id 48 (san-pham cũ) → Bản nháp | Trang › sửa › Đăng |
| 6 trang Sản phẩm mới (id 1404–1409) | Sản phẩm › Thùng rác |
| Viết lại trang Giới thiệu (154), Liên hệ (360); bật index | Trang › sửa › Bản sửa đổi |
| 2 menu: "Menu chính Nhà Máy", "Menu chân trang Nhà Máy" | Giao diện › Menu |
| Rank Math: tên tổ chức/website "Ly Giấy – Ly Nhựa Đà Nẵng", logo lynhuadanang.vn/img/logo.jpg, tiêu đề/mô tả trang /blog/ | Rank Math › Tiêu đề & Meta › Toàn cục / Trang chủ |
| Tên hiển thị tài khoản đăng bài (id 2) → "Ban biên tập Ly Nhựa Đà Nẵng" | Thành viên › sửa › Tên hiển thị |

## tintamphat.com
| Việc | Cách hoàn tác |
|---|---|
| Rank Math: LocalBusiness "Tín Tâm Phát", địa chỉ 03 Nguyễn Như Đỗ, phường Cẩm Lệ; SĐT +84783366622; xoá giờ mẫu 9–17h; tắt schema Article cho Trang | Rank Math › Tiêu đề & Meta › SEO cục bộ / Trang |
| Tắt plugin kk Star Ratings | Plugin › kích hoạt lại |
| Cài + bật plugin "NM sửa lỗi tintamphat" (viewport + /llms.txt) | Plugin › Huỷ kích hoạt |
| Header: topbar + nút gọi = 0783.366.622; nút 2 = "Liên hệ" | Giao diện › Tuỳ biến › Header |
| Chân trang (UX block 451, 567): 1 hotline, địa chỉ phường mới, gỡ link Bao bì | Flatsome › UX Blocks › sửa (bản cũ lưu trong localStorage trình duyệt: nm_backup_ux_451/567) |
| Gỡ mục menu "Bao bì giấy – Túi giấy thực phẩm" (id 462) | Giao diện › Menu › thêm lại link /bao-bi-giay-tui-giay-thuc-pham |
| Tiêu đề + meta Rank Math: trang chủ, 4 sản phẩm, bài 925, giới thiệu, liên hệ, 3 danh mục; wishlist noindex | Sửa từng trang › Rank Math |
| 28 chuyển hướng gộp bài về 7 trang trụ cột + 28 bài vào Thùng rác | Rank Math › Chuyển hướng; Bài viết › Thùng rác |
| Đổi số 0795…/0789…/0702… thành 0783.366.622 trong 8 bài + 3 sản phẩm | Sửa bài › Bản sửa đổi |
| Thêm "Câu hỏi thường gặp" + thông số vào 3 sản phẩm trụ cột (121, 560, 1061) và bài 925; đổi tên sản phẩm 121 và 1061 (bỏ "#1") | Bản sửa đổi / sửa tên sản phẩm |

## Chủ site cần làm (ngoài quyền WordPress)
1. Công cụ đăng bài định kỳ: bỏ phần chèn JSON-LD vào nội dung (cả 2 site); trên tintamphat.com bỏ số 0795.790.444 khỏi mẫu bài.
2. Cloudflare: kiểm tra không chặn bot AI.
3. Hosting lynhuadanang.vn (thư mục gốc): robots.txt, sitemap.xml, llms.txt, schema landing (file trong fixes/lynhuadanang.vn/).
4. Google Business Profile + danh bạ Trang Vàng cho từng thương hiệu (NAP khớp website).
5. Gửi ảnh thật cho 6 trang sản phẩm lynhuadanang.vn; giờ làm việc; giá "từ…" cho 4 sản phẩm tintamphat.com (đang thiếu giá → schema Product thiếu offers).
