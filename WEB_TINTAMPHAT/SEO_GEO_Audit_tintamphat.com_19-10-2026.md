# SEO & GEO Audit — tintamphat.com

- **Ngày kiểm tra:** 19/10/2026. Một số dữ liệu được kiểm từ 18/10/2026.
- **Phương pháp:** kiểm chứng trực tiếp trên site live: trang chủ, `/in-ly-nhua-ly-giay-tai-da-nang/`, `/in-logo-ly-giay-da-nang/`, `/in-an-ly-giay-ly-nhua-so-1-da-nang/`, `/lien-he/`, `robots.txt`, `sitemap_index.xml`, hồ sơ Google Maps. Không suy đoán.
- **Giới hạn:** chưa có dữ liệu Google Search Console, nên cột "Thứ hạng hiện tại" bỏ trống. Độ khó từ khóa ước lượng bằng khảo sát trang kết quả tìm kiếm thực tế tại thị trường Đà Nẵng, không dùng công cụ đo lượng tìm kiếm.

---

## Tóm tắt điều hành

**Đánh giá chung: nền tảng tốt, cần dọn dẹp, không cần đập đi xây lại.**

- **Nền kỹ thuật ổn:** WordPress 7.0.7 (bản mới), plugin SEO Rank Math, sitemap hoạt động, robots.txt chuẩn, có HTTPS, có Cloudflare.
- **Vấn đề chính:** site đang tự làm hại mình bằng lỗi dữ liệu và lỗi cấu trúc nội dung.
- **Điểm mạnh nhất:**
  - Thương hiệu có tài sản thật: xưởng sản xuất, khách hàng lớn, hồ sơ Maps 5 sao.
  - Có sẵn nội dung hỏi–đáp (FAQ) dạng chữ, rất hợp để AI trích dẫn.
- **Ba việc tác động lớn nhất:**
  1. Sửa mã số thuế sai và số điện thoại không thống nhất. Hai lỗi này làm Google và AI mất tin vào thông tin doanh nghiệp.
  2. Chuyển bảng giá từ ảnh PNG sang bảng HTML, để Google và AI đọc được giá.
  3. Sửa loạt tiêu đề (heading) đặt sai cấp.

---

## 1. Bảng cơ hội từ khóa

| Từ khóa | Độ khó | Cơ hội | Thứ hạng hiện tại | Ý định tìm kiếm | Loại nội dung đề xuất |
|---|---|---|---|---|---|
| in ly nhựa đà nẵng | Khó | Cao | ? | Thương mại | Trang trụ cột |
| in ly giấy đà nẵng | Khó | Cao | ? | Thương mại | Trang trụ cột |
| in logo ly giấy đà nẵng | Trung bình | Cao | ? | Thương mại | Trang dịch vụ |
| bảng giá in ly nhựa | Trung bình | Cao | ? | Thương mại | Trang bảng giá (HTML) |
| in ly nhựa số lượng ít đà nẵng | Dễ | Cao | ? | Thương mại | Nhóm bài về số lượng đặt tối thiểu thấp |
| ly nhựa pp 500ml giá sỉ | Dễ | Cao | ? | Giao dịch | Trang thông số sản phẩm |
| ly giấy 16oz đựng trà sữa | Dễ | Cao | ? | Giao dịch | Trang thông số sản phẩm |
| đường kính miệng ly nhựa pp | Dễ | Cao | ? | Thông tin | Trang kỹ thuật |
| ly giấy 1 lớp pe 2 lớp pe khác nhau | Dễ | Trung bình | ? | Thông tin | Bài cẩm nang |
| ly giấy sinh học pla là gì | Dễ | Trung bình | ? | Thông tin | Bài cẩm nang |
| hộp giấy kraft đựng thực phẩm đà nẵng | Trung bình | Cao | ? | Thương mại | Trang danh mục |
| tô giấy đựng phở bún đà nẵng | Dễ | Trung bình | ? | Thương mại | Trang sản phẩm |
| in ly nhựa quảng nam / hội an | Dễ | Cao | ? | Thương mại | Trang khu vực |
| in ly giấy huế | Dễ | Cao | ? | Thương mại | Trang khu vực |
| in ly nhựa quảng ngãi | Dễ | Trung bình | ? | Thương mại | Trang khu vực |
| vật tư mở quán cà phê cần gì | Trung bình | Trung bình | ? | Thông tin | Bài cẩm nang cho người mới tìm hiểu |
| ly nhựa pet nắp cầu đà nẵng | Dễ | Trung bình | ? | Giao dịch | Trang sản phẩm |
| in offset trên ly là gì | Dễ | Thấp | ? | Thông tin | Bài kỹ thuật |
| nắp ly phi 90 95 98 | Dễ | Trung bình | ? | Thông tin | Trang kỹ thuật |
| ống hút giấy đà nẵng | Dễ | Thấp | ? | Thương mại | Trang sản phẩm |

---

## 2. Lỗi trên từng trang (On-Page)

| Trang | Lỗi | Mức độ | Cách sửa |
|---|---|---|---|
| Toàn site (chân trang) | Mã số thuế ghi `040 871 646`: sai, thiếu 1 chữ số. Số đúng là `0401871646` | **Nghiêm trọng nhất** | Sửa chân trang thành `0401871646` |
| /in-an-ly-giay-ly-nhua-so-1-da-nang/ | Nút gọi ở góc phải dùng số **0795.790.444**, khác hotline 0783.366.622 ở đầu trang | **Nghiêm trọng nhất** | Dùng một số duy nhất trên toàn site |
| /in-ly-nhua-ly-giay-tai-da-nang/ | Bảng giá nằm trong ảnh PNG (`bang-gia-in-ly-nhua-da-nang-2.png`), Google và AI không đọc được | **Nghiêm trọng nhất** | Chuyển thành bảng HTML (`<table>`) |
| /in-an-ly-giay-ly-nhua-so-1-da-nang/ | Có 6 thẻ H1 trên một trang, nhảy thẳng từ H1 xuống H3 | Cao | Giữ 1 H1, các tiêu đề còn lại chuyển thành H2/H3 |
| /in-logo-ly-giay-da-nang/ | Có 8 thẻ H1, không có H2 nào; nhãn "Tin Tức" đặt là H6; một H1 bọc link dẫn sang website khác (provietnam.com.vn) | Cao | Giữ 1 H1, sắp xếp lại H2/H3, bỏ link trong tiêu đề |
| /lien-he/ | Mã nhúng bản đồ hỏng: dòng chữ `[google_map_easy id="1"]` hiện ra trang, **không có bản đồ** | Cao | Sửa hoặc thay plugin, nhúng Google Maps |
| /lien-he/ | Nút gọi góc phải cũng dùng số 0795.790.444 | Cao | Dùng một số duy nhất |
| Trang chủ | Chữ mẫu "A title. Image Box text." của theme còn sót, lặp 3 lần ở phần đánh giá khách hàng | Cao | Xóa chữ mẫu |
| /in-an-ly-giay-ly-nhua-so-1-da-nang/, /in-logo-ly-giay-da-nang/ | Đã có khối hỏi–đáp bằng chữ nhưng chưa có mã đánh dấu FAQPage (JSON-LD) | Cao | Thêm schema FAQPage |
| Toàn site | Thẻ meta keywords nhồi khoảng 40 từ khóa | Trung bình | Gỡ bỏ. Thẻ này không còn tác dụng và là tín hiệu xấu |
| Toàn site | Chữ mô tả ảnh (alt) vô nghĩa: "Trang Chủ 36", "1", "2"; logo khách hàng chỉ ghi số | Trung bình | Viết mô tả thật cho từng ảnh |
| Trang chủ | Vẫn ghim bài "In ly nhựa trà sữa mẫu đẹp nhất 2020" | Trung bình | Bỏ ghim, thay bằng bài mới |
| /in-logo-ly-giay-da-nang/ | Tiêu đề ghi "2025", nội dung chưa cập nhật từ 22/4/2025 | Trung bình | Cập nhật nội dung và ngày |
| /in-an-ly-giay-ly-nhua-so-1-da-nang/ | H1 ("In ly giấy, ly nhựa theo logo tại Đà Nẵng") trùng với nhiều trang khác | Trung bình | Viết H1 khác nhau theo đúng mục đích từng trang |

**Điểm tốt cần giữ:**
- Thẻ tiêu đề (title) và mô tả (meta description) của các trang chính đều đúng độ dài, có từ khóa và số điện thoại.
- Khối hỏi–đáp bằng chữ chính xác và đúng kiểu "trả lời trước". Ví dụ: *"In lụa phù hợp in 1 màu, nhận từ 1.000 ly mỗi size, giao 5–7 ngày. In offset in được tối đa 6 màu, nhận từ 10.000 ly mỗi size, giao 12–15 ngày kể từ khi duyệt mẫu."*

---

## 3. Nội dung còn thiếu cần bổ sung

| Chủ đề | Vì sao cần | Dạng nội dung | Ưu tiên | Công sức |
|---|---|---|---|---|
| Trang thông số từng sản phẩm (ly PP/PET/giấy, đủ các size, độ dày zem, đường kính miệng, định lượng giấy gsm, nhiệt độ chịu được) | Đối thủ decaldanang thắng nhờ ghi rõ kiểu "5 zem, cao 11cm, miệng 7cm". Tín Tâm Phát chưa có | Trang sản phẩm có bảng `<table>` | Cao | Nhiều ngày, phải **đo tại xưởng** |
| Bảng giá HTML theo mốc 1.000 / 5.000 / 10.000 ly | Giá hiện đang nằm trong ảnh | Bảng HTML | Cao | Nửa ngày |
| Nhóm trang khu vực: Quảng Nam, Huế, Quảng Ngãi | Tận dụng lợi thế xưởng ở Phú Ninh; đối thủ chưa làm | Trang địa phương | Cao | Nửa ngày mỗi trang |
| Bài cẩm nang: "1 lớp PE và 2 lớp PE", "PLA là gì", "chọn size ly" | Trả lời câu hỏi của người mới mở quán, kéo khách mới | Bài cẩm nang | Trung bình | Nửa ngày mỗi bài |
| Trang hộp giấy / tô giấy kraft chuyên sâu | Mảng ít đối thủ, lợi nhuận tốt | Trang danh mục | Trung bình | Nửa ngày |
| Khung thông tin tác giả và trang năng lực xưởng (ảnh thật tại Phú Ninh) | Tăng độ tin cậy E-E-A-T (kinh nghiệm, chuyên môn, uy tín, đáng tin), hiện hoàn toàn chưa có | Trang riêng + khung tác giả | Cao | Nửa ngày |

---

## 4. Danh sách kiểm tra kỹ thuật

| Hạng mục | Kết quả | Chi tiết |
|---|---|---|
| robots.txt | ✅ Đạt | Hoạt động, chặn đúng các phần cần chặn, có khai báo sitemap |
| Sitemap XML | ✅ Đạt | 5 sitemap con do Rank Math tạo, hoạt động |
| HTTPS | ✅ Đạt | Có, qua Cloudflare |
| Canonical | ✅ Đạt | Các trang có thẻ canonical đúng |
| WordPress core | ✅ Đạt | Bản 7.0.7, mới |
| Hiển thị trên điện thoại | ✅ Đạt | Có khai báo viewport |
| Schema JSON-LD | ❌ Không đạt | Thiếu Organization, LocalBusiness, Product, FAQPage |
| Cấu trúc tiêu đề | ❌ Không đạt | Các trang chính có 6–8 H1 mỗi trang |
| Tốc độ (Core Web Vitals) | ⚠️ Cảnh báo | Video .mp4 tự lưu trên host; ảnh tải chậm dùng khung SVG trống, dễ gây xô lệch bố cục (CLS) và tải chậm phần chính (LCP) |
| WooCommerce | ⚠️ Cảnh báo | Plugin bán hàng vẫn chạy dù site không bán online: thừa mã JavaScript, có form đăng nhập lạc chỗ, hiện giá `₫0.00` |
| Trùng URL | ⚠️ Cảnh báo | `/hop-giay-thuc-pham-cao-cap-da-nang/` và `/san-pham/hop-giay-thuc-pham-cao-cap-da-nang/` cùng tồn tại, cùng được link từ trang chủ |
| Các trang tự tranh từ khóa với nhau | ⚠️ Cảnh báo | Khoảng 13 URL cùng nhắm "in ly nhựa Đà Nẵng" |
| Thống nhất tên – địa chỉ – số điện thoại (NAP) | ❌ Không đạt | Mã số thuế sai; một trang có 2 số điện thoại khác nhau |
| Sitemap sản phẩm | ⚠️ Cảnh báo | Còn `product-sitemap` và `product_cat-sitemap` của WooCommerce, không cần thiết |

---

## 5. So sánh với đối thủ

| Tiêu chí | tintamphat.com | decaldanang.com | lygiaydanang.com |
|---|---|---|---|
| Công khai giá bằng chữ số | ❌ (giá nằm trong ảnh) | ✅ Niêm yết theo gói | ✅ Giá từng sản phẩm |
| Thông số vật lý (zem, đường kính, chiều cao) | ❌ | ✅ Rất chi tiết | ⚠️ Có cỡ nắp (phi) |
| Dùng bảng HTML | ❌ | ⚠️ | ⚠️ |
| Mã số thuế hiển thị đúng | ❌ Sai | ✅ 0402052015 | ✅ |
| Thống nhất tên – địa chỉ – số điện thoại | ❌ | ✅ | ✅ |
| Tín hiệu uy tín (tên nhân viên, địa chỉ) | ⚠️ Thiếu thông tin tác giả | ✅ | ✅ 4 nhân viên + Zalo |
| Hỏi–đáp viết sẵn cho AI trích dẫn | ✅ (điểm mạnh riêng) | ⚠️ | ⚠️ |
| Hồ sơ Google Maps | ✅ 5.0★ / 18 đánh giá | Chưa kiểm tra | Chưa kiểm tra |
| **Bên dẫn đầu** | — | **decaldanang** (dữ liệu số liệu cụ thể) | lygiaydanang (giá + nhân sự) |

**Kết luận:** Tín Tâm Phát thua đối thủ **không phải vì công nghệ**, mà vì **thiếu dữ liệu số công khai**. Phần hỏi–đáp của bạn tốt hơn cả hai đối thủ; bạn thua vì giá nằm trong ảnh và thiếu số đo sản phẩm.

---

## 6. Kế hoạch hành động theo thứ tự ưu tiên

### Việc làm ngay trong tuần (gần như không tốn tiền)

| Việc | Tác động | Thời gian | Cần có |
|---|---|---|---|
| Sửa mã số thuế thành `0401871646` trên toàn site | Cao | 10 phút | Quyền quản trị WordPress |
| Dùng một số điện thoại duy nhất (bỏ 0795.790.444 ở nút gọi) | Cao | 15 phút | — |
| Chuyển bảng giá từ ảnh PNG sang bảng HTML | Cao | 4 giờ | Quyền quản trị WordPress |
| Thêm schema FAQPage (trang bảng giá và trang dịch vụ) | Cao | 1 giờ | — |
| Sửa 6 H1 (trang dịch vụ) và 8 H1 (bài in-logo) | Cao | 1 giờ | — |
| Xóa chữ mẫu "A title. Image Box text." (3 chỗ) | Trung bình | 15 phút | — |
| Sửa mã nhúng bản đồ hỏng ở /lien-he/ | Trung bình | 30 phút | — |
| Gỡ thẻ meta keywords | Thấp | 5 phút | Vào phần cài đặt Rank Math |

### Việc đầu tư trong quý

| Việc | Tác động | Thời gian | Cần có |
|---|---|---|---|
| **Lấy lại quyền quản lý:** tên miền, hosting, hồ sơ Maps, Search Console | Sống còn | 1–2 tuần | Làm việc với bên làm web cũ |
| Thêm bộ schema (Organization, LocalBusiness, Product, Service) | Cao | 2–3 ngày | Sổ Sự Thật |
| Viết trang thông số sản phẩm chuyên sâu (**đo tại xưởng**) | Cao | Nhiều ngày | Số đo thật |
| Gỡ WooCommerce, bật lưu đệm toàn trang trên Cloudflare | Cao (tốc độ) | 1 ngày | Quyền hosting |
| Chuyển video .mp4 lên YouTube hoặc dùng ảnh đại diện + tải chậm | Trung bình | Nửa ngày | — |
| Xây nhóm trang khu vực (Quảng Nam, Huế, Quảng Ngãi) | Cao | 1 tuần | Nội dung |
| Gộp 13 URL tự tranh từ khóa, xử lý URL trùng bằng chuyển hướng 301 | Cao | 2–3 ngày | Bản đồ URL |
| Thêm khung thông tin tác giả và trang năng lực xưởng | Trung bình | Nửa ngày | Ảnh thật |

---

## Ghi chú cập nhật sau ngày 19/10/2026

- **23/10:** user báo đã có quyền quản lý tên miền, hosting/WordPress, hồ sơ Google Maps và Search Console. Việc "lấy lại quyền quản lý" coi như xong. CẦN XÁC NHẬN tên miền đã đứng tên công ty và đã bật xác minh 2 bước.
- **23/10:** đã phân tích thêm đối thủ **baobixanh.com.vn** (TP.HCM, 952 sản phẩm):
  - Trang sản phẩm của họ ghi rất chi tiết: định lượng giấy (gsm ±5%), lớp tráng PE, nhiệt độ chịu được, trọng lượng (±0,5g), số cái mỗi thùng, kích thước thùng, chứng chỉ. Trang sản phẩm của Tín Tâm Phát phải đạt ít nhất mức này.
  - Thời gian sản xuất họ công bố: in lụa khoảng 3 ngày, in offset 7–10 ngày. Tín Tâm Phát đang ghi 5–7 ngày và 12–15 ngày.
- Mẫu mã JSON-LD trong báo cáo kiểm toán bên ngoài **không dùng được**, vì có email không tồn tại, số điện thoại cũ và mã khu vực (areaServed) đã sai.
- Đến thời điểm xuất file này, **chưa có lỗi nào ở trên được sửa trên site live.**
