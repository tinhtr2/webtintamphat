# HANDOVER — Dự án nâng cấp SEO/GEO tintamphat.com

> Cập nhật: 31/10/2026. Người viết: phiên Claude trước.
> **Đọc kỹ trước:** đây **không phải dự án code**. Không có repo git, chưa có dòng code website nào. Thư mục gốc `/home/claude` không chứa gì ngoài file này. Mọi "trạng thái" bên dưới là trạng thái tư vấn và thu thập dữ liệu.

---

## 1. Tổng quan dự án

### Mục tiêu
- Nâng cấp hoặc dựng lại **tintamphat.com** để dẫn đầu SEO (Google) và GEO (được ChatGPT, Gemini, Perplexity, AI Overviews trích dẫn) trong ngành ly giấy, ly nhựa in logo tại **Đà Nẵng**.
- Chủ dự án là người **không biết code**. Mọi hướng dẫn phải cầm tay chỉ việc: bấm vào đâu, copy gì, dán vào đâu.

### Vai trò và quy tắc làm việc đã thống nhất với user
- **Claude** là tổng chỉ huy: kiến trúc, đặt tiêu chuẩn, viết prompt giao việc, viết schema, nghiệm thu. Claude có thể thao tác WordPress qua Claude in Chrome khi user đã tự đăng nhập.
- **Tiết kiệm token (bắt buộc):** Claude không tự xử lý khối dữ liệu thô lớn và không viết bài hàng loạt. Thay vào đó, Claude viết prompt để user copy sang:
  - **Gemini Pro, bản "4 Argon"**: xử lý dữ liệu lớn, kiểm tra chéo. Dự phòng: 3.1 Pro. Việc vặt: 3.8 Flash. Không dùng 3.5 Flash-Lite.
  - **ChatGPT Plus**: viết nháp nội dung hàng loạt.
- **Mỗi lần giao việc gồm đúng 3 khung:** `📤 GỬI CHO [GEMINI/CHATGPT]` / `📋 KẾT QUẢ PHẢI CÓ DẠNG` / `📥 MANG VỀ CHO CLAUDE`. Phần mang về chỉ gồm các bảng được yêu cầu, không gửi cả cuộc chat.
- **Mỗi phản hồi kết thúc bằng đúng 1 hành động** cho user.
- Trả lời bằng tiếng Việt.
- **Không bao giờ để user dán mật khẩu vào bất kỳ AI nào.**

### Doanh nghiệp và tài sản
- **Tín Tâm Phát**: Công ty TNHH Gene Tín Tâm Phát.
  - MST đúng: `0401871646`. Footer website đang ghi sai thành `040 871 646` (CẦN XÁC NHẬN lại với giấy đăng ký kinh doanh).
  - Văn phòng: 03 Nguyễn Như Đỗ, phường Cẩm Lệ, Đà Nẵng.
  - Xưởng: Lô 8, Cụm CN Chợ Lò, Tam Thái, Phú Ninh, Quảng Nam.
  - Hotline: 0783.366.622. Zalo: 0935888239.
  - Hồ sơ Google Maps "Tín Tâm Phát - Ly giấy Ly nhựa in logo Đà Nẵng": 5.0★, 18 đánh giá (số liệu ngày 18/10).
- **Thương hiệu thứ 2 (cùng chủ)**: lynhuadanang.vn là bản chính. lygiaydanang.vn có cùng nội dung và đặt canonical về lynhuadanang.vn.
  - Văn phòng: 106 Ỷ Lan Nguyên Phi, Hải Châu.
  - Hotline: 0933.420.456.
  - Hồ sơ Maps "Ly Nhựa Nắp Cầu Đà Nẵng - LyGiaydanang" chưa xác minh.
- **Đối thủ (KHÔNG phải của user):** lygiaydanang.**com**, lynhuadanang.**com**, decaldanang.com, baobixanh.com.vn (TP.HCM), lynhuabinhminh.com (TP.HCM).

### Nền tảng hiện tại của tintamphat.com (đã quan sát từ bên ngoài)
- WordPress 7.0.7 (theo thẻ meta generator).
- Plugin SEO Rank Math (sitemap `sitemap_index.xml`).
- WooCommerce đang chạy dù không bán online.
- Có Cloudflare (thấy `cdn-cgi/l/email-protection`).
- Có plugin logo-carousel-free và google_map_easy (shortcode của plugin này đang hỏng).
- Theme: có thể là Flatsome (suy ra từ text mẫu "Image Box text"). CẦN XÁC NHẬN.
- Nhà cung cấp hosting và nơi đăng ký tên miền: CẦN XÁC NHẬN.

### File liên quan
Tất cả nằm trong container tạm và **có thể đã mất**. Nếu mất, xin user gửi lại.
- `/mnt/user-data/uploads/tintamphat_com_Kiểm_Toán_SEO_Và_GEO.md`: báo cáo audit do bên ngoài viết (~500KB). Đã bị phản biện, xem mục 5.
- `/mnt/user-data/uploads/1792752285689_VIỆC_SỐ_1__LẬP_BẢN_ĐỒ_DỮ_LIỆU_NGÀNH_…md`: kết quả Gemini Việc số 1, **bản đầy đủ** gộp 2 đối thủ (baobixanh + Bình Minh), gồm Bảng A→F.
- `/mnt/user-data/uploads/1792748654448_…md`, `1792749584930_…md`, `1792752300986_…md`: **3 file giống hệt nhau** (cùng md5), là bản cũ chỉ có đối thủ Bình Minh. Bỏ qua.
- Output đã giao cho user: **`TTP_So_Su_That_Phieu_Do_Xuong.xlsx`** (gửi ngày 23/10, file_uuid `5c912211-1deb-49be-9cf0-0525dabc7ec1`).
- Script tạo file xlsx: `/tmp/claude-0/-home-claude/29d06af2-f1f8-5dae-8b37-18ee90f6c610/scratchpad/build/make_phieu.py`.

---

## 2. Trạng thái các hạng mục

### ĐÃ XONG
- Phản biện báo cáo audit bên ngoài, kết luận **không rebuild sang Astro** (lý do ở mục 4).
- Kiểm chứng trực tiếp các lỗi trên site live (danh sách ở mục 3).
- Chạy `/seo-audit` đầy đủ ngày 19/10, có bảng từ khóa, lỗi on-page, checklist kỹ thuật và so sánh đối thủ. Báo cáo chỉ nằm trong hội thoại, không lưu thành file.
- **GĐ 0 – Thu hồi tài sản:** ngày 23/10 user báo đã có quyền tên miền, hosting/WP admin, Owner hồ sơ Maps, GSC/GA.
  - CẦN XÁC NHẬN: tên miền đã đứng tên công ty chưa; đã đổi mật khẩu và bật xác minh 2 bước chưa; email nào đang làm Owner.
- **Chốt chiến lược đa thương hiệu:** hai thương hiệu định vị như nhau, cạnh tranh trực tiếp nhau và với đối thủ. Đây là quyết định của user. Claude đã đặt "luật chơi" để không bị phạt (xem mục 4).
- Viết Luật nền cho Gem Gemini `TTP - Phân tích dữ liệu`. User đã tạo Gem, suy ra từ việc đã chạy Việc 1.
- **Gemini Việc số 1** (lập bản đồ dữ liệu ngành từ dữ liệu cào): chạy xong với 2 đối thủ và đã nghiệm thu.
- **Sổ Sự Thật v1** (file xlsx 5 tab): đã tạo, kiểm tra và gửi cho user.

### ĐANG DỞ
- **GĐ 1 – Dữ liệu:** chờ user và xưởng điền file xlsx. Đến 31/10 chưa nhận phản hồi.
- **Vá thương hiệu 2:** đã khuyến nghị, CẦN XÁC NHẬN user đã làm gì chưa (chi tiết ở mục 3).

### CHƯA BẮT ĐẦU
- Quick wins trên website live (danh sách ở mục 8).
- Sửa hồ sơ Maps Tín Tâm Phát: tên đang nhồi từ khóa; mô tả ghi "giao 2–4 ngày" và "200–500ml", mâu thuẫn với website.
- **GĐ 2 – Bản vẽ:** lấy dữ liệu Search Console, lập bản đồ từ khóa, cây URL, bảng chuyển hướng 301.
- **GĐ 3:** dựng WordPress sạch trên site thử nghiệm (staging).
- **GĐ 4:** sản xuất nội dung. Chưa viết Luật nền cho ChatGPT Project.
- **GĐ 5:** ra mắt và đo GEO hằng tháng.
- Triển khai schema JSON-LD, llms.txt.

---

## 3. Chi tiết phần ĐANG DỞ

**Chưa có file code nào bị sửa. Chưa có thay đổi nào trên website live.** Claude mới chỉ đọc site, chưa ghi gì.

### Sổ Sự Thật — `TTP_So_Su_That_Phieu_Do_Xuong.xlsx`

**Tab 1. Hướng dẫn**
- Dụng cụ cần dùng: thước kẹp điện tử, panme, cân 0,01g, ống đong 1.000ml, thước dây.
- 6 quy tắc đo: đo 3 cái lấy trung bình; chỉ ghi số; không biết thì để trống; không chép số từ nơi khác; ghi ngày và người đo; chụp ảnh khi đo.
- Chú thích màu ô và một dòng ví dụ. Dòng ví dụ có ghi rõ "số minh họa, không phải số thật".

**Tab 2. Phiếu đo**
- 63 dòng: 55 sản phẩm + 8 dòng `KHAC-*`.
- Cột E "Xưởng có bán?" (Có/Không) cần điền trước.
- Cột L tự tính `=IF(K="","",K*100)`, đổi mm sang zem, chỉ có ở dòng ly nhựa và dòng KHÁC.
- Dòng 1 có ô đếm: đang bán / đã đo xong / chưa trả lời cột E.
- Ô xám là ô không áp dụng cho sản phẩm đó.

**Tab 3. Giấy tờ NCC:** gsm, lớp PE, loại nhựa, nhiệt độ chịu đựng, hồ sơ tự công bố an toàn thực phẩm, mực in. Lấy từ giấy tờ, không đo.

**Tab 4. Chính sách chung**
- 17 chính sách. Đã điền sẵn tintamphat.com, Google Maps, lynhuadanang.vn và baobixanh đang ghi gì cho từng chính sách.
- Cột G "CON SỐ CHỐT" để trống cho user điền.

**Tab 5. Thử nghiệm:** 8 bài thử độc quyền (T1–T8) như ly giấy đựng đá, tô đựng nước nóng, nắp nghiêng, ép màng, mực in ngâm đá, túi treo xe, ly nhựa với nước nóng, so độ cứng theo độ dày.

**Kiểm tra kỹ thuật:** `recalc.py` báo 0 lỗi, 28 công thức.

**Việc user được giao (23/10):**
- Xưởng điền cột E của Tab 2.
- User tự điền Tab 4.
- Gửi lại file.
- Việc đo và thử nghiệm làm dần sau.

**Blocker:** chờ dữ liệu thật. Không có log lỗi.

**Còn thiếu:**
- Danh mục sản phẩm thật (chỉ biết sau khi có cột E).
- Kích thước hộp pizza và hộp kraft.
- Loại ống hút giấy.

**Phát hiện then chốt từ Việc số 1** (đã báo user):
- baobixanh công bố rất chi tiết cho từng sản phẩm: gsm ±5%, PE 18 g/m, nhiệt độ chịu 90–100°C, trọng lượng ±0,5g, quy cách và kích thước thùng, chứng chỉ. **Trang sản phẩm của TTP phải đạt ít nhất mức này.**
- Cả hai đối thủ không ghi zem, đều ở TP.HCM, không có thông tin giao hàng Đà Nẵng.
- baobixanh là nhà phân phối, bán hàng mang thương hiệu khác (UKP, Bình Minh).
- Thời gian sản xuất baobixanh công bố nhanh hơn TTP: in lụa khoảng 3 ngày (TTP ghi 5–7 ngày), offset 7–10 ngày (TTP ghi 12–15 ngày).
- Dữ liệu đối thủ tự mâu thuẫn, ví dụ dung tích 590/600ml, 700/710ml, phi 93/98.
- Ý tưởng đáng làm: bảng tra ly nào đi với nắp, ống hút, túi nào; chính sách giữ hàng hộ ở xưởng, giao nhiều đợt.

### Thương hiệu 2 — 3 điểm cần vá (CẦN XÁC NHẬN đã làm chưa)
- Chuyển hướng 301 lygiaydanang.vn về lynhuadanang.vn. Canonical hiện tại chưa đủ.
- Đổi tên hồ sơ Maps về tên thương hiệu thật (hiện đang nhồi từ khóa, dễ trùng với đối thủ lygiaydanang.com).
- Xác minh con số "500+ quán" và 3 lời chứng thực (anh Hoàng, chị Trang, anh Lâm) là thật và có sự đồng ý của khách; nếu không thì gỡ.
- Câu hỏi "thương hiệu 2 có pháp nhân/MST riêng không?" **chưa được trả lời**.

### Lỗi đã xác minh trên site live (chưa sửa)
- Footer toàn site ghi MST sai `040 871 646`.
- Nút gọi góc phải ở `/in-an-ly-giay-ly-nhua-so-1-da-nang/` và `/lien-he/` dùng số **0795.790.444**, khác hotline 0783.366.622.
- Bảng giá ở `/in-ly-nhua-ly-giay-tai-da-nang/` nằm trong ảnh `wp-content/uploads/2020/05/bang-gia-in-ly-nhua-da-nang-2.png`, Google và AI không đọc được.
- Thừa H1:
  - `/in-an-ly-giay-ly-nhua-so-1-da-nang/` có 6 H1.
  - `/in-logo-ly-giay-da-nang/` có 8 H1, không có H2, nhãn "Tin Tức" là H6, và có một H1 bọc link ra provietnam.com.vn.
- Trang chủ có chuỗi "A title / Image Box text" lặp 3 lần.
- `/lien-he/` có shortcode hỏng hiển thị dạng chữ `[google_map_easy id="1"]` và không có bản đồ.
- Thẻ meta keywords nhồi khoảng 40 từ khóa trên mọi trang.
- Alt ảnh vô nghĩa: "Trang Chủ 36", "1", "2"…
- Chưa có JSON-LD Organization, LocalBusiness, Product hay FAQPage. Trang bảng giá và trang dịch vụ đã có sẵn khối FAQ bằng chữ.
- WooCommerce còn sinh `product-sitemap`, form đăng nhập, `₫0.00`.
- Cùng một nội dung tồn tại ở hai URL: `/hop-giay-thuc-pham-cao-cap-da-nang/` và `/san-pham/hop-giay-thuc-pham-cao-cap-da-nang/`. Tương tự với `in-ly-nhua-tai-da-nang`.
- Trang chủ vẫn ghim bài "mẫu đẹp nhất 2020". Bài "2025" chưa cập nhật kể từ 22/4/2025.
- Video .mp4 tự host trong thư mục uploads.

---

## 4. Quyết định đã chốt và lý do

- **Giữ WordPress, dựng lại sạch; KHÔNG chuyển sang Astro hay headless.**
  - Chủ không biết code, cần tự sửa giá và tự đăng bài.
  - 8/9 lỗi là lỗi biên tập, không phải lỗi nền tảng.
  - WordPress core đang là bản mới; site đã có Cloudflare.
  - "Xây lại" nghĩa là làm lại cấu trúc và nội dung, không phải đổi công nghệ.
- **Dữ liệu cào của đối thủ chỉ dùng làm "bản đồ"**: lấy danh sách thuộc tính, câu hỏi khách hay hỏi, khung danh mục. **Không chép câu chữ, không chép số liệu.**
  - Google xếp nội dung cào hoặc viết lại hàng loạt vào spam.
  - Sản phẩm của đối thủ khác sản phẩm của TTP, chép số là ghi sai.
  - AI luôn trích dẫn nguồn gốc của thông tin.
  - Bản thân dữ liệu đối thủ còn tự mâu thuẫn.
- **Sổ Sự Thật là nguồn số liệu duy nhất** cho website, Maps và mọi LLM.
  - Thiếu số thì ghi `[CẦN ĐO]` hoặc `[KHÔNG CÓ DỮ LIỆU]`, tuyệt đối không đoán.
- **Số liệu chia 3 nhóm theo nguồn:**
  - A: xưởng đo trực tiếp, 3 mẫu lấy trung bình.
  - B: giấy tờ nhà cung cấp.
  - C: chính sách chung (MOQ, thời gian, giá, giao hàng). Không đo theo từng sản phẩm.
- **Bảng trên website dùng `<table>` HTML.** Markdown chỉ là định dạng LLM trả kết quả.
- **URL:** giữ ngắn gọn; trang đang có thứ hạng thì giữ URL hoặc chuyển 301; Silo tạo bằng liên kết nội bộ và breadcrumb.
- **robots.txt hiện tại đúng, KHÔNG sửa.**
- **llms.txt:** làm vì gần như không tốn gì, nhưng không phải trụ cột. Google đã tuyên bố không dùng file này.
- **Chiến lược đa thương hiệu:**
  - Tuân thủ chính sách "doorway abuse" của Google và quy định "mỗi doanh nghiệp một hồ sơ Maps".
  - Hai thương hiệu phải vận hành tách biệt thật: pháp nhân/MST, số điện thoại, Zalo, biển hiệu, người trực.
  - Nội dung riêng 100%, không liên kết qua lại giữa hai site.
  - Năng lực xưởng (thời gian sản xuất, MOQ kỹ thuật) phải nhất quán giữa hai thương hiệu.
  - Đánh giá và chứng thực phải là thật.
  - Từ khóa chính: hai bên cạnh tranh trực tiếp. Nội dung chuyên sâu chia vùng:
    - TTP: kỹ thuật, hộp/tô giấy, sỉ số lượng lớn, khu vực Huế/Quảng Nam/Quảng Ngãi.
    - Thương hiệu 2: mở quán, đồng phục, combo; khu vực từng quận Đà Nẵng.
  - **Làm TTP trước.**
- **Phân công LLM:**
  - Gemini 4 Argon cho dữ liệu và kiểm tra chéo; ChatGPT viết nháp.
  - Gợi ý cho user: mỗi thương hiệu giao cho một LLM viết để giọng văn khác nhau.
  - Claude duyệt 100% trang bán hàng, chỉ lấy mẫu để duyệt bài cẩm nang.
- **Không có artifact type "Sheets"** trong tài khoản này, nên bảng để điền được giao dưới dạng file `.xlsx`.
- **Mẫu JSON-LD trong báo cáo audit bên ngoài KHÔNG được dùng:**
  - Email `info@tintamphat.com` không tồn tại.
  - Số 0795.790.444 đã cũ.
  - Mã `areaServed` không còn đúng sau khi sắp xếp lại đơn vị hành chính.

---

## 5. Cách tiếp cận đã thử và thất bại

- **Báo cáo audit bên ngoài sai ở 2 điểm cốt lõi:**
  - Nói robots.txt không truy cập được. Thực tế file trả về 200 và cấu hình đúng.
  - Nói site "không có giá". Thực tế giá nằm trong ảnh PNG.
  - Báo cáo đề xuất rebuild sang Astro + Sanity + Cloudflare Worker. Đã bác bỏ (lý do ở mục 4).
- **WebFetch `lygiadanang.vn`** (user gõ thiếu chữ "y") trả về `ROBOTS_DISALLOWED`. Tên miền đúng là `lygiaydanang.vn`.
- **Tra MST qua WebSearch** không ra kết quả liên quan.
- **Bấm "Manage profile" trong Business Profile Manager** mở ra trang Google Search "my business" chứ không vào hồ sơ. Cách đọc được hồ sơ: tìm thẳng trên Google Maps rồi dùng `get_page_text`.
  - Lưu ý: lúc đó (18/10) tài khoản Google đang đăng nhập trên Chrome chỉ quản lý hồ sơ của thương hiệu 2. Sau ngày 23/10: CẦN XÁC NHẬN.
- **Gemini Việc số 1, lần chạy đầu:**
  - Chỉ có 1 đối thủ.
  - Bảng E liệt kê sản phẩm của đối thủ thay vì của TTP.
  - Trộn thuộc tính đo được với thuộc tính không đo được.
  - Đánh dấu "có công bố" quá rộng tay.
  - Cách sửa: chuẩn hóa thành 3 nhóm A/B/C, chạy lại với 2 đối thủ, và dồn việc chốt danh mục vào cột E của file xlsx.
- **User gửi toàn bộ output Gemini, gửi trùng file 2–3 lần, kèm cả code Python** nên tốn token. Đã nhắc user chỉ gửi đúng các bảng được yêu cầu.

---

## 6. Quy ước đang dùng

- **Code / DB:** không có. Chưa có repo, chưa có database.
- **Mã sản phẩm trong phiếu đo:**

| Tiền tố | Ý nghĩa |
|---|---|
| `LG-<oz>` | Ly giấy |
| `LK-` | Ly giấy kraft |
| `LS-` | Ly giấy gợn sóng |
| `PP-<ml>` | Ly PP đáy bằng |
| `PB-` | Ly PP đáy bầu |
| `PT-` | Ly PP nắp tim |
| `PET-<ml>` | Ly PET |
| `NC/NB/NN/NT-<phi>` | Nắp cầu / bằng / nóng / tim |
| `OH-` | Ống hút |
| `TG-` | Tô giấy |
| `HG-` | Hộp kraft |
| `HP-` | Hộp pizza |
| `TUI-` | Túi |
| `MANG-` | Màng ép |
| `KHAC-` | Sản phẩm khác |

- **Đơn vị:** ml, oz, mm, zem (1 zem = 0,01 mm), gsm, °C, VNĐ. Thùng ghi `D x R x C` theo cm.
- **Màu ô trong xlsx:** vàng = cần điền; xám = không áp dụng; trắng = có sẵn hoặc tự tính.
- **Ký hiệu thiếu dữ liệu:** `[KHÔNG CÓ DỮ LIỆU]`, `[CẦN ĐO]`.
- **Tên do user tạo:**
  - Gem `TTP - Phân tích dữ liệu`.
  - Google Doc `TTP - Dữ liệu ngành`, nơi user được dặn lưu Bảng A, C, D của Gemini (CẦN XÁC NHẬN đã lưu).
- **Luật nền Gem (tóm tắt 7 luật):**
  1. Không bịa số.
  2. Mọi số phải có nguồn.
  3. Chuẩn hóa đơn vị.
  4. Trả bảng Markdown, đúng cột được yêu cầu.
  5. Không chép câu văn của đối thủ.
  6. Viết tiếng Việt ngắn gọn.
  7. Cuối mỗi câu trả lời có mục "TỰ KIỂM TRA".
  - Nguyên văn luật nền chỉ nằm trong lịch sử hội thoại; cần thì viết lại theo 7 ý trên.

---

## 7. Cách chạy

- Không có lệnh install, chạy dev hay chạy test, vì chưa có dự án code.
- **Tạo lại file xlsx** (nếu script còn tồn tại):
  ```bash
  python3 make_phieu.py <đường_dẫn_output.xlsx>
  python3 /mnt/skills/public/xlsx/scripts/recalc.py <đường_dẫn_output.xlsx> 60
  ```
  Cần openpyxl (đã cài sẵn) và LibreOffice (dùng để recalc).
- **Biến môi trường:** không có.
- **Quyền truy cập cần dùng:** WordPress admin, Search Console, Google Business Profile, tài khoản tên miền, hosting.
  - Chỉ user giữ thông tin đăng nhập.
  - Làm việc bằng cách: user tự đăng nhập trên Chrome, Claude thao tác qua Claude in Chrome.

---

## 8. Việc tiếp theo, theo thứ tự ưu tiên

1. **Hỏi user về file xlsx:** đã điền Tab 4 và cột E Tab 2 chưa? Nếu có, nghiệm thu và chốt danh mục sản phẩm cùng bộ chính sách chuẩn.
2. **Xác nhận an toàn tài sản:** tên miền đứng tên công ty, đã bật xác minh 2 bước.
3. **Quick wins trên site live** (user đăng nhập, Claude thao tác qua Chrome). Làm được ngay:
   - Sửa MST thành `0401871646`.
   - Bỏ số 0795.790.444 khỏi nút gọi.
   - Xóa "Image Box text".
   - Sửa H1 ở 2 trang.
   - Sửa shortcode bản đồ.
   - Gỡ meta keywords.
4. **Sau khi Tab 4 được chốt:**
   - Thống nhất chính sách trên website và Maps (thời gian giao, MOQ, dung tích).
   - Chuyển bảng giá PNG sang `<table>` HTML. Cần đọc số liệu trong ảnh hoặc lấy từ user.
   - Thêm FAQPage schema.
5. **GĐ 2:**
   - Lấy dữ liệu Search Console 16 tháng: top truy vấn, top trang, truy vấn CTR thấp, báo cáo lập chỉ mục.
   - Từ đó lập: danh sách URL phải giữ nguyên, nhóm cơ hội ở vị trí 5–15, bản đồ URL mới, bảng 301.
6. **Schema:** Organization, LocalBusiness, Product, Service, lấy số liệu từ Sổ Sự Thật.
7. **Kỹ thuật:**
   - Gỡ WooCommerce, bật full page cache trên Cloudflare.
   - Chuyển .mp4 sang YouTube hoặc ảnh poster + tải chậm.
   - Xử lý URL trùng nội dung bằng canonical hoặc 301.
8. **Nội dung (GĐ 4):**
   - Viết Luật nền cho ChatGPT Project.
   - Viết content brief: trang thông số từng sản phẩm, trang khu vực Huế/Quảng Nam/Quảng Ngãi, bài cẩm nang (1PE vs 2PE, PLA, chọn size).
   - Làm bảng tra ly – nắp – ống hút – túi.
   - Làm trang năng lực xưởng và hộp tác giả, dùng ảnh thật.
9. **Thương hiệu 2:** chuyển 301, đổi tên hồ sơ Maps, xác minh chứng thực, làm rõ pháp nhân.
10. **Đo GEO hằng tháng:** hỏi cùng khoảng 20 câu trên ChatGPT, Gemini, Perplexity, Claude; ghi lại AI nào nhắc đến Tín Tâm Phát.
11. **llms.txt** (ưu tiên thấp).
