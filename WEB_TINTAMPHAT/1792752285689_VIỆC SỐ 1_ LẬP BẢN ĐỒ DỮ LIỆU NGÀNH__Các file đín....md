

Python  
import os  
import pandas as pd  
import json

files \= sorted(os.listdir('.'))  
print("All files in directory:", files)

\# Let's check tat-ca-url.csv  
if 'tat-ca-url.csv' in files:  
    df\_urls \= pd.read\_csv('tat-ca-url.csv')  
    print("\\n--- tat-ca-url.csv (rows: {}) \---".format(len(df\_urls)))  
    print(df\_urls.columns.tolist())  
    print(df\_urls\['group'\].value\_counts() if 'group' in df\_urls.columns else df\_urls.head(5))

\# Check pages in du-lieu-tham-khao.json where group \== 'pages' or 'collections'  
with open('du-lieu-tham-khao.json', 'r', encoding='utf-8') as f:  
    data\_json \= json.load(f)

pages\_grp \= \[p for p in data\_json\['pages'\] if p.get('group') \== 'pages'\]  
print("\\n--- Pages group in JSON ({}) \---".format(len(pages\_grp)))  
for p in pages\_grp:  
    print(p\['url'\], "\|", p\['title'\], "\| headings:", p.get('headings') or p.get('article\_headings'))  
    if 'faq' in p\['url'\] or 'thoi-gian' in p\['url'\] or 'chinh-sach' in p\['url'\]:  
        txt \= p.get('article\_text') or "\\n".join(p.get('description\_lines', \[\]))  
        print("  Text:", txt\[:500\])

Kết quả chạy mã

All files in directory: \['bai-viet-seo-tham-khao.csv', 'bao-cao-danh-gia.md', 'chu-de-bai-viet-phu-hop.csv', 'danh-muc-chuan-hoa-so-bo.csv', 'danh-muc-tham-khao.csv', 'doi-chieu-hai-nguon-tham-khao.csv', 'doi-chieu-ngay-bai-viet.csv', 'du-lieu-tham-khao.json', 'phieu-xac-minh-22-san-pham.csv', 'sitemap\_collections\_1.xml', 'sitemap\_pages\_1.xml', 'sitemap\_products\_1.xml', 'snapshot-progress.json', 'tat-ca-url.csv', 'thong-ke-ngay-bai-viet.json', 'thong-ke.json'\]

\--- tat-ca-url.csv (rows: 1118\) \---  
\['group', 'url', 'status', 'final\_url', 'sitemap\_lastmod', 'title', 'h1', 'meta\_description', 'canonical', 'og\_type', 'parse\_error'\]  
group  
products       952  
blogs          115  
collections     36  
pages           15  
Name: count, dtype: int64

\--- Pages group in JSON (15) \---  
https\://baobixanh.com.vn/cac-cau-hoi-thuong-gap-faqs \| Các câu hỏi thường gặp \- FAQS tại Bao bì XANH \| headings: \['1. Bao Bì Xanh cung cấp những loại bao bì nào?', '2. Bao Bì Xanh có bán sỉ không?', '3. Có bán số lượng ít không?', '4. Bao Bì Xanh có giao hàng không?', '5. Tôi không biết nên chọn loại bao bì nào, Bao Bì Xanh có tư vấn không?', '6. Bao Bì Xanh có bán nhiều loại bao bì trong cùng một đơn hàng không?', '7. Bao Bì Xanh có nhận in logo lên bao bì không?', '8. Bao bì có sẵn và bao bì in logo khác nhau như thế nào?', '9. Thời gian giao hàng bao lâu?', '10. Bao bì dùng cho thực phẩm có cần kiểm tra thông tin gì?', '11. Làm sao để nhận báo giá?', '12. Có thể đặt nhiều loại bao bì cùng một đơn không?'\]  
  Text:   
https\://baobixanh.com.vn/chi-nh-sa-ch-thanh-toa-n \| Chính sách vận chuyển và thanh toán của Bao bì XANH \| headings: None  
https\://baobixanh.com.vn/chinh-sach \| Chính sách cụ thể cho khách hàng tại Bao Bì Xanh \| headings: None  
  Text:   
https\://baobixanh.com.vn/chinh-sach-bao-hanh \| Chính sách bảo hành của Bao bì Xanh \| headings: None  
  Text:   
https\://baobixanh.com.vn/chinh-sach-doi-tra \| Chính sách bảo hành của Bao bì Xanh \| headings: None  
  Text:   
https\://baobixanh.com.vn/chinh-sach-van-chuyen-thanh-toan \| Chính sách vận chuyển và thanh toán của Bao bì XANH \| headings: None  
  Text:   
https\://baobixanh.com.vn/dang-ky-tha-nh-vien \| Đăng ký thành viên \| headings: None  
https\://baobixanh.com.vn/dieu-khoan \| Điều khoản sử dụng và mua hàng tại Bao Bì Xanh \| headings: None  
https\://baobixanh.com.vn/doi-tra-va-ba-o-ha-nh \| Đổi trả và bảo hành \| headings: None  
https\://baobixanh.com.vn/giao-nha-n-va-thanh-toa-n \| Chính sách vận chuyển và thanh toán của Bao bì XANH \| headings: None  
https\://baobixanh.com.vn/gioi-thieu \| Giới thiệu Thương hiệu Bao bì Xanh Uy Tín Tại TPHCM \| headings: \['Câu chuyện về thương hiệu Bao bì Xanh', 'Tại sao Bao bì Xanh được ra đời?', 'Cam kết tại Bao bì Xanh', 'Những con số biết nói về Bao bì Xanh', 'Giá trị cốt lõi của Bao bì Xanh'\]  
https\://baobixanh.com.vn/huong-dan-mua-hang \| Hướng dẫn mua hàng và thanh toán trên Bao Bì Xanh \| headings: \['Cách 1: Đặt hàng tại website', 'Cách 2: Đặt hàng tại Zalo', 'Cách 3: Đặt hàng qua Facebook Fanpage'\]  
https\://baobixanh.com.vn/huong-dan-mua-hang-thanh-toan \| Hướng dẫn mua hàng và thanh toán trên Bao Bì Xanh \| headings: \['Cách 1: Đặt hàng tại website', 'Cách 2: Đặt hàng tại Zalo', 'Cách 3: Đặt hàng qua Facebook Fanpage'\]  
https\://baobixanh.com.vn/lien-he \| Liên Hệ Đặt Hàng & Tư Vấn \- Bao bì Xanh \| headings: None  
https\://baobixanh.com.vn/thoi-gian-san-xuat-ly-nhua-ly-giay \| Thời gian sản xuất ly nhựa \- ly giấy Bao Bì Xanh \| headings: \['Thời gian sản xuất', 'Thời gian nên đặt hàng trước', 'Lưu ý về tiến độ sản xuất'\]  
  Text: 

Python  
for p in pages\_grp:  
    if p\['url'\] in \[  
        'https\://baobixanh.com.vn/cac-cau-hoi-thuong-gap-faqs',  
        'https\://baobixanh.com.vn/thoi-gian-san-xuat-ly-nhua-ly-giay',  
        'https\://baobixanh.com.vn/chinh-sach-van-chuyen-thanh-toan',  
        'https\://baobixanh.com.vn/chinh-sach-doi-tra'  
    \]:  
        print("===", p\['url'\], "===")  
        for k, v in p.items():  
            if v:  
                print(f"  {k}: {str(v)\[:600\]}")

Kết quả chạy mã

\=== https\://baobixanh.com.vn/cac-cau-hoi-thuong-gap-faqs \===  
  group: pages  
  url: https\://baobixanh.com.vn/cac-cau-hoi-thuong-gap-faqs  
  final\_url: https\://baobixanh.com.vn/cac-cau-hoi-thuong-gap-faqs  
  status: 200  
  content\_type: text/html; charset=utf-8  
  sitemap\_lastmod: 2026-09-19T04:24:50Z  
  title: Các câu hỏi thường gặp \- FAQS tại Bao bì XANH  
  h1: Các câu hỏi thường gặp \- FAQS tại Bao bì XANH  
  meta\_description: Một số câu hỏi thường gặp của thương hiệu Bao bì XANH. Mọi thắc mắc sẽ được chúng tôi giải đáp một cách rõ ràng nhất.  
  og\_type: website  
  canonical: https\://baobixanh.com.vn/cac-cau-hoi-thuong-gap-faqs  
  images: \['http\://bizweb.dktcdn.net/100/339/225/themes/696668/assets/logo.png?1789799831243'\]  
  headings: \['1. Bao Bì Xanh cung cấp những loại bao bì nào?', '2. Bao Bì Xanh có bán sỉ không?', '3. Có bán số lượng ít không?', '4. Bao Bì Xanh có giao hàng không?', '5. Tôi không biết nên chọn loại bao bì nào, Bao Bì Xanh có tư vấn không?', '6. Bao Bì Xanh có bán nhiều loại bao bì trong cùng một đơn hàng không?', '7. Bao Bì Xanh có nhận in logo lên bao bì không?', '8. Bao bì có sẵn và bao bì in logo khác nhau như thế nào?', '9. Thời gian giao hàng bao lâu?', '10. Bao bì dùng cho thực phẩm có cần kiểm tra thông tin gì?', '11. Làm sao để nhận báo giá?', '12. Có thể đặt nhiều loại bao bì cùng một đơn khôn  
  content\_excerpt: 1\. Bao Bì Xanh cung cấp những loại bao bì nào? Bao Bì Xanh cung cấp nhiều nhóm bao bì dùng cho quán ăn, cà phê, trà sữa, nhà hàng và cửa hàng bán mang đi như ly nhựa PP/PET, ly giấy, chai nhựa, hộp nhựa, tô giấy, ống hút, muỗng, nắp ly, cuộn màng ép ly và các phụ kiện đóng gói. 2\. Bao Bì Xanh có bán sỉ không? Có. Bao Bì Xanh cung cấp sản phẩm cho khách mua số lượng lớn và có nhiều quy cách đóng thùng khác nhau tùy sản phẩm. Một số sản phẩm hiện áp dụng đơn sỉ từ 1.000 cái tại TP.HCM. Giá tận xưởng được sử dụng cho nhiều mô hình kinh doanh như: \- Cà phê, trà sữa, nước uống- Nhà hàng, quán ăn- Đ  
\=== https\://baobixanh.com.vn/chinh-sach-doi-tra \===  
  group: pages  
  url: https\://baobixanh.com.vn/chinh-sach-doi-tra  
  final\_url: https\://baobixanh.com.vn/chinh-sach-bao-hanh  
  status: 200  
  content\_type: text/html; charset=utf-8  
  sitemap\_lastmod: 2026-06-04T03:51:13Z  
  title: Chính sách bảo hành của Bao bì Xanh  
  h1: Chính sách bảo hành của Bao bì Xanh  
  meta\_description: Bao bì Xanh luôn nỗ lực mang đến cho quý khách những sản phẩm sắm tuyệt và những dịch vụ hậu mãi không ngừng được hoàn thiện.  
  og\_type: website  
  canonical: https\://baobixanh.com.vn/chinh-sach-bao-hanh  
  images: \['http\://bizweb.dktcdn.net/100/339/225/themes/696668/assets/logo.png?1789799831243'\]  
  content\_excerpt: Bao bì Xanh luôn nỗ lực mang đến cho quý khách những sản phẩm sắm tuyệt và những dịch vụ hậu mãi không ngừng được hoàn thiện. Theo đó, Bao bì Xanh đã cải tiến và áp dụng Chính sách bảo hành đối với sản phẩm của Bao bì Xanh. ► Điều kiện áp dụng: – Sản phẩm được bảo hành miễn phí trong thời gian sử dụng tương ứng trong các trường hợp sau: Lỗi do sản xuất, không đóng gói theo quy cách, thiếu sản phẩm hoặc chất lượng sản phẩm không như cam kết. Lỗi do quá trình vận chuyển từ phía công ty chúng tôi đến quý khách hàng. Cam kết đổi trả hoàn tiền 100% nếu khách hàng không hài lòng – Bao bì Xanh từ chố  
\=== https\://baobixanh.com.vn/chinh-sach-van-chuyen-thanh-toan \===  
  group: pages  
  url: https\://baobixanh.com.vn/chinh-sach-van-chuyen-thanh-toan  
  final\_url: https\://baobixanh.com.vn/chinh-sach-van-chuyen-thanh-toan  
  status: 200  
  content\_type: text/html; charset=utf-8  
  sitemap\_lastmod: 2026-09-16T08:32:18Z  
  title: Chính sách vận chuyển và thanh toán của Bao bì XANH  
  h1: Chính sách vận chuyển và thanh toán của Bao bì XANH  
  meta\_description: Chính sách vận chuyển cũng như thanh toán của Bao bì XANH. Các bạn có thể đọc thêm để nắm rõ thông tin khi mua hàng. Đảm bảo quyền lợi cho cả 2 bên.  
  og\_type: website  
  canonical: https\://baobixanh.com.vn/chinh-sach-van-chuyen-thanh-toan  
  images: \['http\://bizweb.dktcdn.net/100/339/225/themes/696668/assets/logo.png?1789799831243'\]  
  content\_excerpt: CHÍNH SÁCH VÀ PHÍ VẬN CHUYỂN TẠI TP HỒ CHÍ MINH & CÁC TỈNH TOÀN QUỐC CỦA “BAO BÌ XANH” Dịch vụ tương tác: Tất cả các khách hàng khi mua sỉ, lẻ tại Bao Bì Xanh có thể tương tác : website:https\://baobixanh.com.vn https\://www\.facebook.com/baobixanh.com.vn/ Email: banhang.baobixanh@gmail.com Hotline: 0934585373 Thời gian giao hàng và đặt hàng: Đặt hàng: \+ Từ 8:00 đến 20:00 hàng ngày Giao hàng: \+ Buổi sáng: Từ 8:30 đến 12:00 \+ Buổi chiều: Từ 13:30 đến 17:30 TP HCM. Từ 13:30 đến 16:00 (ngoại tỉnh) Giao hàng ngay: Đơn hàng đã thanh toán hoặc thanh toán trực tiếp (không muộn quá 24h). Đơn hàng đặt: Gi  
\=== https\://baobixanh.com.vn/thoi-gian-san-xuat-ly-nhua-ly-giay \===  
  group: pages  
  url: https\://baobixanh.com.vn/thoi-gian-san-xuat-ly-nhua-ly-giay  
  final\_url: https\://baobixanh.com.vn/thoi-gian-san-xuat-ly-nhua-ly-giay  
  status: 200  
  content\_type: text/html; charset=utf-8  
  sitemap\_lastmod: 2026-09-19T04:28:07Z  
  title: Thời gian sản xuất ly nhựa \- ly giấy Bao Bì Xanh  
  h1: Thời gian sản xuất ly nhựa \- ly giấy Bao Bì Xanh  
  meta\_description: Thời gian sản xuất Loại sản phẩm Trường hợp Thời gian dự kiến In lụa 1 màu Dưới 10.000 cái Đơn hàng mới, chưa có khung in Khoảng 3 ngày Mùa cao điểm: 5–7 ngày In lụa 1 màu Dưới 10.000 cái Đơn hàng cũ, đã có khung in, không đổi thiết kế Khoảng 1 ngày Mùa cao điểm: 3–5 ngày In lụa 1 màu Từ 10.000 cái Tùy số lượng và lịch  
  og\_type: website  
  canonical: https\://baobixanh.com.vn/thoi-gian-san-xuat-ly-nhua-ly-giay  
  images: \['http\://bizweb.dktcdn.net/100/339/225/themes/696668/assets/logo.png?1789799831243'\]  
  headings: \['Thời gian sản xuất', 'Thời gian nên đặt hàng trước', 'Lưu ý về tiến độ sản xuất'\]  
  content\_excerpt: Thời gian sản xuất Loại sản phẩm Trường hợp Thời gian dự kiến In lụa 1 màuDưới 10.000 cái Đơn hàng mới, chưa có khung in Khoảng 3 ngàyMùa cao điểm: 5–7 ngày In lụa 1 màuDưới 10.000 cái Đơn hàng cũ, đã có khung in, không đổi thiết kế Khoảng 1 ngàyMùa cao điểm: 3–5 ngày In lụa 1 màuTừ 10.000 cái Tùy số lượng và lịch sản xuất tại xưởng Cộng thêm khoảng 1–2 ngày In offset nhiều màu Đơn hàng mới, chưa có bản kẽm Khoảng 7–10 ngày In offset nhiều màu Đơn hàng cũ, đã có bản kẽm, không đổi thiết kế Khoảng 5–7 ngày Ly giấy 2 lớp Đơn hàng mới, chưa có bản kẽm Khoảng 15–20 ngày Ly giấy 2 lớp Đơn hàng cũ, 

Python  
for p in pages\_grp:  
    if p\['url'\] in \[  
        'https\://baobixanh.com.vn/cac-cau-hoi-thuong-gap-faqs',  
        'https\://baobixanh.com.vn/thoi-gian-san-xuat-ly-nhua-ly-giay',  
        'https\://baobixanh.com.vn/chinh-sach-van-chuyen-thanh-toan'  
    \]:  
        print("===", p\['url'\], "===")  
        print(p.get('content\_excerpt'))

Kết quả chạy mã

\=== https\://baobixanh.com.vn/cac-cau-hoi-thuong-gap-faqs \===  
1\. Bao Bì Xanh cung cấp những loại bao bì nào? Bao Bì Xanh cung cấp nhiều nhóm bao bì dùng cho quán ăn, cà phê, trà sữa, nhà hàng và cửa hàng bán mang đi như ly nhựa PP/PET, ly giấy, chai nhựa, hộp nhựa, tô giấy, ống hút, muỗng, nắp ly, cuộn màng ép ly và các phụ kiện đóng gói. 2\. Bao Bì Xanh có bán sỉ không? Có. Bao Bì Xanh cung cấp sản phẩm cho khách mua số lượng lớn và có nhiều quy cách đóng thùng khác nhau tùy sản phẩm. Một số sản phẩm hiện áp dụng đơn sỉ từ 1.000 cái tại TP.HCM. Giá tận xưởng được sử dụng cho nhiều mô hình kinh doanh như: \- Cà phê, trà sữa, nước uống- Nhà hàng, quán ăn- Đồ ăn mang đi- Thực phẩm đóng gói- Cửa hàng kinh doanh thực phẩm 3\. Có bán số lượng ít không? Có thể tùy sản phẩm và quy cách đóng gói. Khách nên gửi loại bao bì, kích thước và số lượng cần mua để được báo đúng sản phẩm và quy cách. 4\. Bao Bì Xanh có giao hàng không? Có. Chính sách giao hàng phụ thuộc vào sản phẩm, số lượng và khu vực nhận hàng. Với một số sản phẩm tại TP.HCM, website đang hiển thị chính sách giao nhanh và freeship theo điều kiện đơn hàng. 5\. Tôi không biết nên chọn loại bao bì nào, Bao Bì Xanh có tư vấn không? Có. Khách hàng có thể cung cấp sản phẩm cần đóng gói, kích thước/dung tích, số lượng dự kiến và cách sử dụng. Bao Bì Xanh sẽ tư vấn loại bao bì phù hợp với nhu cầu. 6\. Bao Bì Xanh có bán nhiều loại bao bì trong cùng một đơn hàng không? Có, tùy sản phẩm và quy cách đóng gói. Khách hàng có thể gửi danh sách các sản phẩm cần mua để Bao Bì Xanh kiểm tra hàng và tư vấn   
\=== https\://baobixanh.com.vn/chinh-sach-van-chuyen-thanh-toan \===  
CHÍNH SÁCH VÀ PHÍ VẬN CHUYỂN TẠI TP HỒ CHÍ MINH & CÁC TỈNH TOÀN QUỐC CỦA “BAO BÌ XANH” Dịch vụ tương tác: Tất cả các khách hàng khi mua sỉ, lẻ tại Bao Bì Xanh có thể tương tác : website:https\://baobixanh.com.vn https\://www\.facebook.com/baobixanh.com.vn/ Email: banhang.baobixanh@gmail.com Hotline: 0934585373 Thời gian giao hàng và đặt hàng: Đặt hàng: \+ Từ 8:00 đến 20:00 hàng ngày Giao hàng: \+ Buổi sáng: Từ 8:30 đến 12:00 \+ Buổi chiều: Từ 13:30 đến 17:30 TP HCM. Từ 13:30 đến 16:00 (ngoại tỉnh) Giao hàng ngay: Đơn hàng đã thanh toán hoặc thanh toán trực tiếp (không muộn quá 24h). Đơn hàng đặt: Giao trong ngày hoặc đúng theo lịch hai bên đã hẹn. Trường hợp khách quan: Giao nhanh trong ngày hoặc có thông báo trực tiếp với khách hàng. Với những khách hàng tại chung cư cao tầng, cơ quan, văn phòng, nhà hàng ở trên cao vui lòng nhận hàng tại tầng trệt hoặc nơi nhận thuận tiện nhất. Phí vận chuyển được tính như sau: Tùy thuộc vào số lượng và khối lượng đơn hàng sẽ có giá vận chuyển phù hợp. Nếu muốn biết thêm chi tiết liên hệ hotline. \+ Các điểm giao hàng khác liên hệ Hotline: 0934585373 \+ Với các khách hàng ngoại tỉnh, vui lòng thanh toán trước phí VC từ nhà xe tại TP HCM về đến nơi quý khách muốn nhận hàng. \+ Hiện đã có kho của Bao bì Xanh tại Bình Dương: Số 14 Đặng Thùy Trâm, TT. Phước Vĩnh, Phú Giáo, Bình Dương Quý khách lưu ý: Quãng đường để tính phí VC được tính theo bản đồ trực tuyến như: http\://maps.google.com Phương thức thanh toán: Thanh toán trực tiếp: Ngay sau khi giao và   
\=== https\://baobixanh.com.vn/thoi-gian-san-xuat-ly-nhua-ly-giay \===  
Thời gian sản xuất Loại sản phẩm Trường hợp Thời gian dự kiến In lụa 1 màuDưới 10.000 cái Đơn hàng mới, chưa có khung in Khoảng 3 ngàyMùa cao điểm: 5–7 ngày In lụa 1 màuDưới 10.000 cái Đơn hàng cũ, đã có khung in, không đổi thiết kế Khoảng 1 ngàyMùa cao điểm: 3–5 ngày In lụa 1 màuTừ 10.000 cái Tùy số lượng và lịch sản xuất tại xưởng Cộng thêm khoảng 1–2 ngày In offset nhiều màu Đơn hàng mới, chưa có bản kẽm Khoảng 7–10 ngày In offset nhiều màu Đơn hàng cũ, đã có bản kẽm, không đổi thiết kế Khoảng 5–7 ngày Ly giấy 2 lớp Đơn hàng mới, chưa có bản kẽm Khoảng 15–20 ngày Ly giấy 2 lớp Đơn hàng cũ, đã có bản kẽm, không đổi thiết kế Khoảng 10–15 ngày Thời gian nên đặt hàng trước Loại sản phẩm Nên đặt trước In lụa Ít nhất 5–7 ngày In offset Ít nhất 10–15 ngày Ly giấy 2 lớp Khoảng 20–25 ngày Lưu ý về tiến độ sản xuất \- Thời gian trên là thời gian dự kiến, có thể thay đổi theo số lượng và lịch sản xuất thực tế tại xưởng. \- Đơn đặt vào đầu tuần thường thuận lợi hơn về tiến độ so với cuối tuần do có thể phát sinh ngày nghỉ Chủ nhật. \- Khoảng tháng 6–9 thường là mùa thấp điểm nên tiến độ có thể nhanh hơn. Vào mùa cao điểm hoặc khi lượng đơn tại xưởng tăng, thời gian sản xuất có thể kéo dài. \- Đặc biệt với các sản phẩm in logo riêng, khách hàng nên đặt hàng sớm để tránh thiếu ly khi cần sử dụng. \- Bao Bì Xanh sẽ kiểm tra lịch sản xuất thực tế tại thời điểm đặt hàng và thông báo thời gian giao dự kiến trước khi khách xác nhận đơn.

**XÁC ĐỊNH TÊN MIỀN ĐỐI THỦ TRONG DỮ LIỆU:**

* **SITE A:** baobixanh.com.vn — có đầy đủ dữ liệu cào chi tiết (952 trang sản phẩm, 36 trang danh mục, 107 bài viết và 15 trang tĩnh trong các file du-lieu-tham-khao.json, danh-muc-chuan-hoa-so-bo.csv, bai-viet-seo-tham-khao.csv, bao-cao-danh-gia.md, tat-ca-url.csv, thong-ke.json).  
* **SITE B:** lynhuabinhminh.com — có dữ liệu đối chiếu 22 sản phẩm trọng tâm trong file doi-chieu-hai-nguon-tham-khao.csv và phieu-xac-minh-22-san-pham.csv. Các nhóm sản phẩm hoặc thuộc tính ngoài 22 dòng đối chiếu này của Site B được ghi nhận là \[KHÔNG CÓ DỮ LIỆU\].

### **━━ BẢNG A — DANH MỤC SẢN PHẨM ━━**

| Nhóm | Loại sản phẩm | Dung tích/Kích cỡ | Biến thể (loại nắp, màu…) | Site A có | Site B có |
| :---- | :---- | :---- | :---- | :---- | :---- |
| Ly giấy | Ly giấy trắng trơn / in hình sẵn | 2.5oz \- 80ml; 3oz \- 90ml; 4oz \- 120ml; 4.5oz \- 130ml; 5oz \- 150ml; 5.5oz \- 155ml; 6oz \- 180ml; 6.5oz \- 190ml; 7oz \- 210ml; 8oz \- 240ml; 9oz \- 270ml; 10oz \- 300ml; 12oz \- 360ml; 14oz \- 420ml; 16oz \- 500ml; 18oz \- 520ml; 22oz \- 680ml (Site B có bản 700ml \~680ml); 32oz \- 1000ml (1 lít) (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv; lynhuabinhminh.com trong doi-chieu-hai-nguon-tham-khao.csv) | Trắng sữa (trắng trơn), in hình sẵn; tráng 1PE (đựng nóng) hoặc 2PE (đựng nóng & lạnh); dùng nắp bằng, nắp cầu, nắp nóng có khóa | Có (baobixanh.com.vn/ly-giay) | Có (lynhuabinhminh.com \- các cỡ 4oz, 6oz, 8oz, 9oz, 12oz, 16oz, 22oz, 360ml, 500ml, 700ml trong doi-chieu-hai-nguon-tham-khao.csv) |
| Ly giấy | Ly giấy Kraft | 8oz \- 280ml; 12oz \- 400ml; 16oz \- 500ml (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, sitemap\_products\_1.xml) | Màu nâu giấy Kraft; 1PE hoặc 2PE | Có (baobixanh.com.vn/ly-giay-kraft) | \[KHÔNG CÓ DỮ LIỆU\] |
| Ly giấy | Ly giấy gợn sóng (2 lớp) | 9oz \- 270ml; 12oz \- 360ml (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, sitemap\_products\_1.xml) | Thân gợn sóng cách nhiệt nhiều màu, kèm nắp nóng | Có (baobixanh.com.vn/ly-giay-gon-song) | \[KHÔNG CÓ DỮ LIỆU\] |
| Ly giấy | Ly giấy in logo theo yêu cầu | 12oz \- 360ml; 16oz \- 500ml; 22oz \- 680ml (Nguồn: baobixanh.com.vn/ly-giay-1m55-coffee-tea-juice trong du-lieu-tham-khao.json, sitemap\_products\_1.xml) | In offset nhiều màu hoặc in lụa 1 màu theo thương hiệu quán (baobixanh.com.vn/thoi-gian-san-xuat-ly-nhua-ly-giay) | Có (baobixanh.com.vn/ly-giay-tra-sua) | \[KHÔNG CÓ DỮ LIỆU\] |
| Ly nhựa PP | Ly nhựa PP đáy bằng (dáng truyền thống / kiểu cao) | 60ml; 120ml; 140ml (phi 65mm); 160ml (phi 70mm); 180ml (phi 70mm); 200ml (phi 70mm, phi 95mm ly tàu hũ); 220ml (phi 75mm); 300ml (phi 95mm); 360ml (phi 95mm); 400ml (phi 95mm); 450ml (phi 95mm); 500ml (16oz, phi 95mm); 650ml (22oz, phi 95mm); 700ml (24oz, phi 95mm); 710ml (phi 117mm); 750ml (phi 117mm); 800ml (phi 117mm); 900ml (phi 117mm); 1000ml \- 1 lít (phi 106mm kiểu cao, phi 117mm) (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, snapshot-progress.json; lynhuabinhminh.com trong doi-chieu-hai-nguon-tham-khao.csv) | Trong đục / sáng mờ; trơn (4 phiên bản dày/mỏng) hoặc có sọc gân (loại đủ, loại thiếu); ép màng hoặc đậy nắp bằng, nắp cầu, nắp bật | Có (baobixanh.com.vn/ly-nhua-pp) | Có (lynhuabinhminh.com \- các cỡ 360ml, 500ml, 700ml trong doi-chieu-hai-nguon-tham-khao.csv) |
| Ly nhựa PP | Ly nhựa PP đáy bầu (Q-cup) | 360ml (phi 95mm); 420ml (phi 90mm); 500ml (16oz, phi 95mm); 600ml (phi 95mm); 700ml (24oz, phi 95mm) (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, snapshot-progress.json) | Đáy bo tròn chữ U, nhựa PP mềm dẻo hoặc đáy bầu cứng (trong, nhám); ép màng hoặc dùng nắp cầu, nắp bằng, nắp bật | Có (baobixanh.com.vn/ly-nhua-day-bau) | \[KHÔNG CÓ DỮ LIỆU\] |
| Ly nhựa PP | Ly nhựa PP nắp tim (cứng / mềm / nhám) | 500ml (16oz, phi 90mm); 600ml (phi 90mm); 700ml (24oz, phi 90mm) (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, snapshot-progress.json) | Ly tim mềm trong, ly tim cứng, ly tim mờ/nhám (đỏ nhám, hồng Sapphire); đi kèm nắp tim (đen, trắng sữa, trong) nút trái tim | Có (baobixanh.com.vn/ly-nap-tim) | \[KHÔNG CÓ DỮ LIỆU\] |
| Ly nhựa PET | Ly nhựa PET đáy bằng | 230ml (8oz \- phi 84mm); 270ml (9oz \- phi 93mm); 300ml (10oz \- phi 84mm); 350ml (12oz \- phi 84mm); 360ml (12oz \- phi 93mm); 420ml (14oz \- phi 98mm); 470ml (16oz \- phi 93mm); 500ml (16oz \- phi 98mm); 590ml (20oz \- phi 93mm ở Site A, phi 98mm ở Site B); 600ml (20oz \- phi 98mm ở Site A, phi 93mm ở Site B); 650ml (22oz \- phi 98mm); 700ml (24oz \- phi 98mm ở Site A); 710ml (24oz \- phi 98mm ở Site B) (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, snapshot-progress.json; lynhuabinhminh.com trong doi-chieu-hai-nguon-tham-khao.csv) | Trong suốt sáng bóng; không ép màng; kết hợp nắp cầu, nắp bằng hoặc nắp uống trực tiếp | Có (baobixanh.com.vn/ly-nhua-pet) | Có (lynhuabinhminh.com \- các cỡ 360ml, 470ml, 500ml, 590ml, 600ml, 710ml trong doi-chieu-hai-nguon-tham-khao.csv) |
| Ly nhựa PET | Ly nhựa PET đáy bầu | 360ml (12/14oz \- phi 93mm) (Nguồn: baobixanh.com.vn/ly-nhua-day-bau-360ml trong danh-muc-chuan-hoa-so-bo.csv, sitemap\_products\_1.xml) | Trong suốt, đáy bầu, dùng nắp cầu hoặc nắp bằng phi 93mm | Có (baobixanh.com.vn/ly-nhua-day-bau-360ml) | \[KHÔNG CÓ DỮ LIỆU\] |
| Nắp | Nắp cầu PET | Phi 84mm; phi 90mm; phi 93mm; phi 95mm; phi 98mm; phi 95mm (dáng cầu vuông) (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, snapshot-progress.json; lynhuabinhminh.com trong doi-chieu-hai-nguon-tham-khao.csv) | Nhựa PET trong suốt, có đục lỗ tròn hoặc cắt chữ thập cắm ống hút | Có (baobixanh.com.vn/nap-nhua) | Có (lynhuabinhminh.com \- dòng ly nắp cầu phi 93mm, phi 98mm tại doi-chieu-hai-nguon-tham-khao.csv) |
| Nắp | Nắp bằng (Nắp phẳng) PET / PP | Phi 67mm; phi 90mm; phi 93mm; phi 95mm; phi 98mm; phi 106mm (PP có lỗ / không lỗ); D98 (PP); D107 (PP); phi 117mm; D122 (PP); D138 (PP); phi 150mm (PET/PP) (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, sitemap\_products\_1.xml) | Trong suốt hoặc trong mờ; có lỗ chữ thập hoặc không lỗ (dành cho ly và tô/hộp) | Có (baobixanh.com.vn/nap-nhua) | \[KHÔNG CÓ DỮ LIỆU\] |
| Nắp | Nắp ly giấy chịu nhiệt (Nắp nóng có khóa) | Phi 75mm; phi 77mm; phi 80mm; phi 90mm (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, sitemap\_products\_1.xml) | Màu đen hoặc màu trắng, có khóa gài miệng uống chống tràn | Có (baobixanh.com.vn/nap-nong-den-co-khoa-90) | \[KHÔNG CÓ DỮ LIỆU\] |
| Nắp | Nắp uống trực tiếp (Nắp bật) & Nắp tim | Phi 90mm (nắp bật, nắp tim); phi 93mm (nắp uống trực tiếp) (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, sitemap\_products\_1.xml) | Nắp tim có màu đen, trắng, trong suốt kèm nút gài hình tim; nắp bật uống trực tiếp không cần ống hút | Có (baobixanh.com.vn/nap-tim-den, baobixanh.com.vn/nap-truc-tiep-90-nap-bat-90) | \[KHÔNG CÓ DỮ LIỆU\] |
| Ống hút | Ống hút nhựa PP | Phi 6mm x dài 210mm; phi 8mm x dài 200mm (20cm); phi 12mm (hút trân châu) (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, snapshot-progress.json) | Màu đen hoặc trắng trong suốt; có bọc màng từng cái hoặc không bọc màng; quy cách bịch 500g (200 cái) hoặc 1000g (1kg \~400 cái) | Có (baobixanh.com.vn/ong-hut) | \[KHÔNG CÓ DỮ LIỆU\] |
| Ống hút | Ống hút giấy | \[KHÔNG CÓ DỮ LIỆU\] (Nguồn chỉ ghi tên "Ống hút giấy" trong danh-muc-chuan-hoa-so-bo.csv, sitemap\_products\_1.xml) | Phân hủy sinh học | Có (baobixanh.com.vn/ong-hut-giay) | \[KHÔNG CÓ DỮ LIỆU\] |
| Tô/Hộp giấy | Tô giấy trắng / in hình | 90ml (3oz); 120ml (4oz); 150ml (5oz); 200ml (7oz); 240ml (8oz); 270ml (9oz); 300ml (10oz); 360ml (12oz); 390ml (13oz); 420ml (14oz); 450ml (15oz); 500ml (16oz); 600ml (20oz); 650ml (22oz); 750ml (25oz); 950ml (32oz); 1000ml \- 1 lít (36oz) (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, sitemap\_products\_1.xml) | Trắng trơn hoặc in hình sẵn; tráng 1PE hoặc 2PE | Có (baobixanh.com.vn/to-giay) | \[KHÔNG CÓ DỮ LIỆU\] |
| Tô/Hộp giấy | Tô giấy Kraft & Dĩa giấy | Tô Kraft: 750ml, 1000ml; Dĩa giấy: 100mm (10cm) (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, sitemap\_products\_1.xml) | Tô Kraft thường hoặc miệng rộng đựng salad; dĩa giấy hoa văn (có hoặc không kèm nĩa \+ muỗng) | Có (baobixanh.com.vn/to-giay-kraft, baobixanh.com.vn/dia-giay) | \[KHÔNG CÓ DỮ LIỆU\] |
| Túi | Túi đựng ly mang đi & Túi Zipper | Túi 1 ly; túi 2 ly; túi chữ T; túi zipper (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, snapshot-progress.json) | Túi 1 ly / 2 ly có biến thể ép hông hoặc ép đáy; túi zipper có biến thể đáy đứng mặt bạc hoặc trong suốt | Có (baobixanh.com.vn/tui-nilon, baobixanh.com.vn/tui-zipper) | \[KHÔNG CÓ DỮ LIỆU\] |
| Phụ kiện khác | Cuộn màng ép ly | Ngang 105mm (10.5cm) x Dài 19000mm (1.900cm), khoảng 1.700 nắp/cuộn (Nguồn: baobixanh.com.vn/cuon-mang-ep-ly-tron, baobixanh.com.vn/cuon-ep-ly-in-san trong snapshot-progress.json) | Màng ép trơn trong suốt, in sẵn hình, in lụa 1 màu (nền trong/nền trắng), in flexo nhiều màu, in ống đồng, cuộn ép dành cho ly giấy | Có (baobixanh.com.vn/cuon-mang-ep-ly) | \[KHÔNG CÓ DỮ LIỆU\] |
| Phụ kiện khác | Chai nhựa PET, Hộp/Khay nhựa, Thố/Hũ tương, Muỗng/Nĩa, Khăn lạnh, Ly thủy tinh | Chai nhựa: 100ml, 200ml, 250ml, 300ml, 330ml, 450ml, 500ml, 1000ml (1 lít); Hũ tương: 60ml (2oz), 120ml (4oz); Thố nhựa: 360ml, 500ml; Hộp thực phẩm PP: 500ml, 550ml, 600ml, 650ml, 700ml, 750ml, 1000ml; Hộp trái cây: 350g, 500g, 1000g (1kg); Muỗng nhựa: 150mm (15cm), 200mm (20cm); Ly thủy tinh: 100ml \- 700ml (Nguồn: baobixanh.com.vn trong danh-muc-chuan-hoa-so-bo.csv, sitemap\_products\_1.xml, snapshot-progress.json) | Chai tròn/vuông/tam giác/tròn lùn/miệng rộng (cổ 28mm, 30mm, 38mm); Khay cơm 1-5 ngăn (HT12, HT17, HT17A, HT25A, HT88, HT203, HC5); Muỗng đen/đỏ/hồng/trắng/trong/vàng/xanh (bịch 50 hoặc 100 cái); Khăn lạnh màng ngọc/vỏ kẽm | Có (baobixanh.com.vn) | \[KHÔNG CÓ DỮ LIỆU\] |

### **━━ BẢNG B — MA TRẬN THUỘC TÍNH ━━**

| Thuộc tính | Đơn vị | Áp dụng cho nhóm | Site A công bố (Có/Không) | Site B công bố (Có/Không) | Ví dụ giá trị kèm nguồn | Mức quan trọng với người mua (Cao/TB/Thấp) |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| Dung tích | ml, oz (lít) | Ly giấy, Ly nhựa PP, Ly nhựa PET, Tô/Hộp giấy, Phụ kiện khác | Có | Có | 500ml (16oz) (Nguồn: baobixanh.com.vn/ly-nhua-pet-500ml, \[lynhuabinhminh.com/san-pham/ly-nhua-pet-500ml-16oz-phi-98/\](https\://lynhuabinhminh.com/san-pham/ly-nhua-pet-500ml-16oz-phi-98/) trong doi-chieu-hai-nguon-tham-khao.csv, snapshot-progress.json) | Cao |
| Đường kính miệng / Cổ (Phi / Ø) | mm | Ly giấy, Ly nhựa PP, Ly nhựa PET, Nắp, Ống hút, Tô/Hộp giấy, Phụ kiện khác | Có | Có | 98mm / phi 98 / Ø98 cho ly PET (baobixanh.com.vn/ly-nhua-pet-500ml, \[lynhuabinhminh.com/san-pham/ly-nhua-pet-500ml-16oz-phi-98/\](https\://lynhuabinhminh.com/san-pham/ly-nhua-pet-500ml-16oz-phi-98/)); cổ chai 28mm, 30mm, 38mm (baobixanh.com.vn/chai-nhua-mieng-rong-330ml-nap-co-dai trong snapshot-progress.json) | Cao |
| Đường kính đáy | mm | Ly giấy, Ly nhựa PP, Ly nhựa PET, Tô/Hộp giấy, Phụ kiện khác | Có | Không | 59mm cho ly PET 500ml (baobixanh.com.vn/ly-nhua-pet-500ml); 47mm cho ly bầu 500ml (baobixanh.com.vn/ly-nhua-day-bau-500ml trong snapshot-progress.json) | TB |
| Chiều cao / Chiều dài | mm (cm) | Ly giấy, Ly nhựa PP, Ly nhựa PET, Nắp, Ống hút, Tô/Hộp giấy, Phụ kiện khác | Có | Không | Cao 120mm cho ly PET 500ml (baobixanh.com.vn/ly-nhua-pet-500ml); cao 70mm cho nắp cầu 93 (baobixanh.com.vn/nap-cau-93); dài 150mm (15cm) cho muỗng (baobixanh.com.vn/muong-nhua-trang trong snapshot-progress.json) | Cao |
| Trọng lượng tịnh (kèm sai số) | g (gram, kg) | Ly giấy, Ly nhựa PP, Ly nhựa PET, Tô/Hộp giấy, Phụ kiện khác | Có | Không | 11.5g (+/-0.5) cho ly PET 500ml (baobixanh.com.vn/ly-nhua-pet-500ml); 1500g (1.5kg) cho cuộn màng ép (baobixanh.com.vn/cuon-mang-ep-ly-tron trong snapshot-progress.json) | Cao |
| Chất liệu & An toàn BPA | Văn bản | Tất cả các nhóm | Có | Có | Giấy PO, Cupstock \+ 2PE, không chứa BPA (baobixanh.com.vn/ly-giay-12oz-360ml); Nhựa pet nguyên sinh (baobixanh.com.vn/ly-nhua-pet-470ml, \[lynhuabinhminh.com/san-pham/ly-nhua-pet-470ml-16oz-phi-93/\](https\://lynhuabinhminh.com/san-pham/ly-nhua-pet-470ml-16oz-phi-93/) trong doi-chieu-hai-nguon-tham-khao.csv) | Cao |
| Định lượng giấy | gsm | Ly giấy, Tô/Hộp giấy, Phụ kiện khác (Khăn lạnh) | Có | Không | 240gsm (+/- 5%) cho ly giấy 12oz/16oz (baobixanh.com.vn/ly-giay-12oz-360ml); 260gsm (+/- 5%) cho ly giấy 22oz (baobixanh.com.vn/ly-giay-22oz-680ml); 190gsm (+/- 5%) cho ly 4oz/6oz (baobixanh.com.vn/ly-giay-4oz-120ml trong snapshot-progress.json) | Cao |
| Số lớp tráng PE & Định lượng PE | lớp (PE), g/m | Ly giấy, Tô/Hộp giấy | Có | Không | 1PE hoặc 2PE, PE 18 g/m (+/- 5%) (baobixanh.com.vn/ly-giay-9oz-270ml, baobixanh.com.vn/ly-giay-12oz-360ml trong snapshot-progress.json) | Cao |
| Khả năng chịu nhiệt / Nhiệt độ sử dụng | °C (độ C) | Ly giấy, Ly nhựa PP, Ly nhựa PET, Ống hút, Tô/Hộp giấy, Phụ kiện khác | Có | Không | 100°C (100 độ C) cho ly giấy 12oz 2PE (baobixanh.com.vn/ly-giay-12oz-360ml); 90°C (90 độ C) cho ly giấy 4oz 1PE (baobixanh.com.vn/ly-giay-4oz-120ml); 15°C \- 80°C cho muỗng/ống hút (baobixanh.com.vn/muong-nhua-trang); \-20°C đến 80°C cho chai PET (baobixanh.com.vn/chai-nhua-vuong-330ml trong snapshot-progress.json) | Cao |
| Tương thích nắp & màng ép | mm (phi) / Văn bản | Ly giấy, Ly nhựa PP, Ly nhựa PET, Nắp, Tô/Hộp giấy, Phụ kiện khác | Có | Có | Ly PP 500ml miệng 95mm dùng màng ép hoặc nắp bằng, nắp cầu, nắp bật phi 95 (baobixanh.com.vn/ly-nhua-pp-500ml trong snapshot-progress.json) | Cao |
| Đường kính lỗ cắm ống hút & Kiểu lỗ trên nắp | mm / Văn bản | Nắp | Có | Không | Đường kính lỗ 20mm, khoét lỗ tròn hoặc cắt chữ thập (baobixanh.com.vn/nap-cau-93, baobixanh.com.vn/nap-bang-95 trong snapshot-progress.json, du-lieu-tham-khao.json) | TB |
| Màng bọc từng chiếc (vệ sinh cá nhân) | Văn bản (Có/Không) | Ống hút | Có | Không | Có bọc màng hoặc Không sử dụng (baobixanh.com.vn/ong-hut-phi-12-den-co-boc-mang, baobixanh.com.vn/ong-hut-phi-6-den-khong-boc-mang trong snapshot-progress.json) | TB |
| Quy cách đóng gói (cái/túi, cái/thùng) | cái/túi, cái/thùng, cái/bịch, chai/kiện, cuộn/thùng | Tất cả các nhóm | Có | Không | 1.000 cái/thùng, 50 cái/1 túi nilong (baobixanh.com.vn/ly-nhua-pet-500ml); 500 cái/thùng, 25 cái/túi (baobixanh.com.vn/ly-giay-22oz-680ml); 3.000 cái/thùng (baobixanh.com.vn/ly-giay-4oz-120ml); 12 cuộn/thùng (baobixanh.com.vn/cuon-ep-ly-in-san trong snapshot-progress.json) | Cao |
| Kích thước thùng carton | mm (cm) | Ly giấy, Ly nhựa PP, Ly nhựa PET, Tô/Hộp giấy | Có | Không | 500 x 400 x 390 mm (50 x 40 x 39 cm) (baobixanh.com.vn/ly-nhua-pet-500ml); 545 x 470 x 590 mm (54.5 x 47 x 59 cm) (baobixanh.com.vn/ly-giay-12oz-360ml trong snapshot-progress.json) | TB |
| Màu sắc & Độ trong bề mặt | Văn bản | Tất cả các nhóm | Có | Không | Trong suốt, sáng bóng (ly PET); Trong đục, sáng mờ (ly PP); Trắng sữa (Trắng trơn) (ly giấy) (baobixanh.com.vn trong snapshot-progress.json) | TB |
| Kỹ thuật in & Số màu in | màu / Văn bản | Ly giấy, Ly nhựa PP, Ly nhựa PET, Phụ kiện khác | Có | Không | In offset, Nhiều màu, chuyển màu, full chân (baobixanh.com.vn/ly-giay-1m55-coffee-tea-juice); In flexo, 2 màu (Đen, Cam) (baobixanh.com.vn/ly-nhua-4t-coffee trong du-lieu-tham-khao.json) | Cao |
| Số lượng đặt sỉ / đặt in tối thiểu (MOQ) | cái, cuộn | Ly giấy, Ly nhựa PP, Ly nhựa PET, Phụ kiện khác | Có | Không | Đơn sỉ từ 1.000 cái (baobixanh.com.vn/cac-cau-hoi-thuong-gap-faqs); in logo 5.000 cái (baobixanh.com.vn/ly-nhua-4t-coffee); in màng ép từ 3 cuộn (baobixanh.com.vn/cuon-ep-ly-in-lua-1-mau trong du-lieu-tham-khao.json) | Cao |
| Thời gian sản xuất đơn in | ngày | Ly giấy, Ly nhựa PP, Ly nhựa PET, Phụ kiện khác | Có | Không | In lụa 1 màu dưới 10.000 cái: 3 ngày (đơn mới) / 1 ngày (đơn cũ có khung); In offset nhiều màu: 7-10 ngày (đơn mới) / 5-7 ngày (đơn cũ); Ly giấy 2 lớp: 15-20 ngày (baobixanh.com.vn/thoi-gian-san-xuat-ly-nhua-ly-giay trong du-lieu-tham-khao.json) | Cao |
| Kích thước trải phẳng (Ngang x Dài) & Số nắp/cuộn | mm (cm), nắp/cuộn | Phụ kiện khác (Cuộn màng ép) | Có | Không | Ngang: 105mm (10.5cm), Dài: 19000mm (1.900cm), 1.700 nắp/cuộn (baobixanh.com.vn/cuon-mang-ep-ly-tron, baobixanh.com.vn/cuon-ep-ly-in-san trong snapshot-progress.json) | TB |
| Chứng chỉ & Tiêu chuẩn chất lượng | Văn bản | Ly giấy, Ly nhựa PP, Ly nhựa PET, Tô/Hộp giấy, Phụ kiện khác | Có | Không | HACCP, GMP, ISO 9001, FDA, RoHS, BRC, Quatest3 (baobixanh.com.vn/ly-nhua-pet-470ml); GB181006.1-2009 (baobixanh.com.vn/ly-nhua-nap-tim-500ml trong snapshot-progress.json) | TB |
| Hạn sử dụng | tháng (năm) | Ly giấy, Ly nhựa PP, Ly nhựa PET, Ống hút, Phụ kiện khác | Có | Không | 24 tháng cho ống hút và ly in (baobixanh.com.vn/ong-hut-phi-6-den-khong-boc-mang); 36 tháng (3 năm) cho ly nắp tim (baobixanh.com.vn/ly-nhua-nap-tim-500ml); 72 tháng cho muỗng nhựa (baobixanh.com.vn/muong-nhua-trang trong snapshot-progress.json) | Thấp |
| Mã sản phẩm (SKU) & Thương hiệu | Văn bản | Tất cả các nhóm | Có | Không | Mã UKP98-16OZ PET-T thương hiệu UKP (baobixanh.com.vn/ly-nhua-pet-500ml); mã MD-12OZ2PE thương hiệu Bình Minh (baobixanh.com.vn/ly-giay-12oz-360ml trong snapshot-progress.json) | Thấp |
| Độ dày nhựa | zem | Ly nhựa PP, Ly nhựa PET, Túi | Không | Không | \[KHÔNG CÓ DỮ LIỆU\] (Không xuất hiện thông số zem trong toàn bộ 952 sản phẩm của du-lieu-tham-khao.json và doi-chieu-hai-nguon-tham-khao.csv; chỉ ghi định tính "Loại dày", "Loại mỏng", "Loại đủ", "Loại thiếu") | Cao |

### **━━ BẢNG C — GIÁ THAM CHIẾU (chỉ dùng nội bộ) ━━**

| Sản phẩm | Quy cách | Đơn vị bán | Giá (VNĐ) | Nguồn | Ghi chú |
| :---- | :---- | :---- | :---- | :---- | :---- |
| Ly giấy 2.5oz \- 80ml / 3oz \- 90ml | Ly giấy sampling nhỏ | Cái (trong microdata) | 330 / 306 | baobixanh.com.vn/ly-giay-2-5oz-80ml, baobixanh.com.vn/ly-giay-3oz-90ml (danh-muc-chuan-hoa-so-bo.csv) | Giá 2.5oz: 330 VNĐ; 3oz: 306 VNĐ |
| Ly giấy 4oz \- 120ml | Giấy PO 190gsm, 1PE, miệng 65mm x đáy 47mm x cao 52mm, nặng 3g (+/-0.5), 3.000 cái/thùng | Cái (trong microdata) | 412 | baobixanh.com.vn/ly-giay-4oz-120ml (snapshot-progress.json) | Mã MD-4OZ1PE  |
| Ly giấy 6oz \- 180ml | Giấy PO 190gsm, 1PE, miệng 71mm x đáy 49mm x cao 70mm, nặng 4g (+/-0.5), 2.000 cái/thùng | Cái (trong microdata) | 471 | baobixanh.com.vn/ly-giay-6oz-180ml (snapshot-progress.json) | Mã PT-6OZ1PE; bản in hình sẵn 1PE giá 540 VNĐ (baobixanh.com.vn/ly-giay-6oz-180ml-in-hinh trong danh-muc-chuan-hoa-so-bo.csv) |
| Ly giấy 8oz \- 240ml | Giấy PO 190gsm (+/-18), 1PE, trắng trơn | Cái (trong microdata) | 520 | baobixanh.com.vn/ly-giay-8oz-240ml (doi-chieu-hai-nguon-tham-khao.csv) | Bản in hình sẵn 1PE giá 700 VNĐ (baobixanh.com.vn/ly-giay-8oz-240ml-in-hinh trong danh-muc-chuan-hoa-so-bo.csv) |
| Ly giấy 9oz \- 270ml | Giấy PO 240gsm, nặng 5.5g (+/-0.5); 1PE (1.000 cái/thùng) hoặc 2PE (2.000 cái/thùng) | Cái (trong microdata) | 624 | baobixanh.com.vn/ly-giay-9oz-270ml (snapshot-progress.json) | Mã HN-9OZ1PE / MD-9OZ2PE; bản in hình 1PE giá 800 VNĐ; bản gợn sóng 9oz giá 1.200 VNĐ (baobixanh.com.vn/ly-giay-gon-song-9oz) |
| Ly giấy 12oz \- 360ml | Giấy PO 240gsm, 2PE, miệng 88mm (90mm) x đáy 58mm x cao 99mm, nặng 7.5g (+/-0.5), 1.000 cái/thùng | Cái (trong microdata) | 753 | baobixanh.com.vn/ly-giay-12oz-360ml (snapshot-progress.json) | Mã MD-12OZ2PE; bản in hình 1PE giá 900 VNĐ; bản gợn sóng 12oz giá 1.800 VNĐ (baobixanh.com.vn/ly-giay-gon-song-12oz) |
| Ly giấy 14oz \- 420ml | Giấy PO 2PE | Cái (trong microdata) | 741 | baobixanh.com.vn/ly-giay-14oz-420ml (danh-muc-chuan-hoa-so-bo.csv) | Mã MD-14OZ2PE |
| Ly giấy 16oz \- 500ml | Giấy PO 240gsm, 2PE, miệng 89mm x đáy 63mm x cao 123mm, nặng 9.5g (+/-0.5), 1.000 cái/thùng | Cái (trong microdata) | 871 | baobixanh.com.vn/ly-giay-16oz-500ml (snapshot-progress.json) | Mã PT-16OZ2PE; bản in sẵn 2PE giá 1.050 VNĐ (baobixanh.com.vn/ly-giay-16oz-500ml-in-hinh trong danh-muc-chuan-hoa-so-bo.csv) |
| Ly giấy 22oz \- 680ml | Giấy PO 260gsm, 2PE, miệng 88mm (90mm) x đáy 62mm x cao 154mm, nặng 12g (+/-0.5), 500 cái/thùng (25 cái/túi) | Cái (trong microdata) | 1.058 | baobixanh.com.vn/ly-giay-22oz-680ml (snapshot-progress.json) | Mã PT-22OZ2PE; mẫu in offset nhiều màu theo yêu cầu (đơn 5.000 cái) giá 1.600 VNĐ (baobixanh.com.vn/ly-giay-1m55-coffee-tea-juice trong du-lieu-tham-khao.json) |
| Ly giấy 1 lít (1000ml) \- 32oz | 2 lớp PE | Cái (trong microdata) | 1.500 | baobixanh.com.vn/ly-giay-1-lit-1000ml-32oz (danh-muc-chuan-hoa-so-bo.csv) | Cỡ đại 1000ml |
| Ly giấy Kraft (8oz / 12oz / 16oz) | 8oz (280ml), 12oz (400ml), 16oz (500ml) | Cái (trong microdata) | 1.691 / 2.128 / 2.506 | baobixanh.com.vn/ly-giay-kraft-8oz-280ml, .../ly-giay-kraft-12oz-400ml, .../ly-giay-kraft-16oz-500ml (danh-muc-chuan-hoa-so-bo.csv) | Giá tương ứng cho 3 cỡ 8oz, 12oz, 16oz |
| Ly nhựa PP nhỏ (60ml \- 220ml) | 60ml, 120ml, 140ml (phi 65mm), 160ml (phi 70mm), 180ml (phi 70mm), 200ml (phi 70mm / phi 95mm), 220ml (phi 75mm) | Cái (trong microdata) | 85 \- 306 | baobixanh.com.vn/ly-nhua-65-140ml, .../ly-nhua-pp-tron-95-200ml-ly-tau-hu (danh-muc-chuan-hoa-so-bo.csv) | 140ml: 85 VNĐ; 220ml: 102 VNĐ; 60ml: 124 VNĐ; 160ml: 167 VNĐ; 180ml: 171 VNĐ; 200ml (phi 70): 194 VNĐ; 120ml: 220 VNĐ; 200ml (phi 95 tàu hũ): 306 VNĐ |
| Ly nhựa PP 300ml & 400ml | Nhựa PP nguyên sinh, miệng 95mm, nặng 6g \- 6.5g, 2.000 cái/thùng | Cái (trong microdata) | 729 / 810 | baobixanh.com.vn/ly-nhua-pp-300ml, baobixanh.com.vn/ly-nhua-pp-400ml (snapshot-progress.json) | Mã UKP95-Y300PP-C, trạng thái OutOfStock |
| Ly nhựa PP 360ml | Nhựa PP nguyên sinh, miệng 95mm x đáy 56mm x cao 102mm, nặng 6.5g (+/-0.5), 1.000 cái/thùng | Cái (trong microdata) | 376 | baobixanh.com.vn/ly-nhua-pp-360ml (snapshot-progress.json) | Mã UKP95-360PP-C-T; bản đáy bầu 360ml PP giá 377 VNĐ (baobixanh.com.vn/ly-nhua-pp-95-360ml-day-bau trong danh-muc-chuan-hoa-so-bo.csv) |
| Ly nhựa PP 500ml (16oz) | Nhựa PP nguyên sinh, miệng 95mm x đáy 55mm x cao 126mm, nặng 8g (+/-0.5), 1.000 cái/thùng | Cái (trong microdata) | 492 | baobixanh.com.vn/ly-nhua-pp-500ml (snapshot-progress.json) | Mã UKP95 \- 500PP-C-T; bản PP sọc 500ml giá 225 VNĐ (baobixanh.com.vn/ly-nhua-soc-500ml); bản đáy bầu 500ml (nặng 9g) giá 513 VNĐ (baobixanh.com.vn/ly-nhua-day-bau-500ml); bản đáy bầu cứng 500ml (trong/nhám) giá 1.106 VNĐ |
| Ly nhựa PP 650ml (22oz) | Nhựa PP nguyên sinh, miệng 95mm x đáy 58mm x cao 149mm, nặng 8.5g (+/-0.5), 1.000 cái/thùng | Cái (trong microdata) | 550 | baobixanh.com.vn/ly-nhua-pp-650ml (snapshot-progress.json) | Mã UKP95-650PP-C-T; bản đáy bầu 600ml PP giá 565 VNĐ (baobixanh.com.vn/ly-nhua-day-bau-600ml) |
| Ly nhựa PP 700ml (24oz) | Nhựa PP nguyên sinh, miệng 95mm x đáy 85mm x cao 105mm, nặng 10.5g (+/-0.5), 1.000 cái/thùng | Cái (trong microdata) | 624 | baobixanh.com.vn/ly-nhua-pp-700ml (snapshot-progress.json) | Mã UKP95 \- 700PP-C; bản sọc 700ml loại đủ giá 325 VNĐ, loại thiếu giá 316 VNĐ; bản đáy bầu 700ml PP (miệng 95mm x đáy 50mm x cao 158mm, nặng 11g) giá 635 VNĐ (baobixanh.com.vn/ly-nhua-day-bau-700ml) |
| Ly nhựa PP cỡ lớn (710ml \- 1000ml) | Phi 106mm và phi 117mm | Cái (trong microdata) | 307 \- 894 | baobixanh.com.vn/ly-nhua-pp-710ml, .../ly-nhua-pp-800ml, .../ly-nhua-1-lit (danh-muc-chuan-hoa-so-bo.csv) | 710ml: 307 VNĐ; 750ml: 322 VNĐ; 800ml: 588 VNĐ; 900ml: 741 VNĐ; 1000ml kiểu cao phi 106: 798 VNĐ; 1000ml phi 117: 894 VNĐ |
| Ly nhựa PP nắp tim (500ml / 600ml / 700ml) | Phi 90mm; tim cứng (500 cái/thùng, nặng 15g và 21.5g) hoặc tim mềm/tim mờ | Cái (trong microdata) | 748 \- 1.859 | baobixanh.com.vn/ly-nhua-nap-tim-500ml, baobixanh.com.vn/ly-nhua-nap-tim-700ml (snapshot-progress.json, danh-muc-chuan-hoa-so-bo.csv) | Tim mềm 500ml: 748 VNĐ, 600ml: 824 VNĐ, 700ml: 866 VNĐ; Tim mờ 500ml: 766 VNĐ, 700ml: 907 VNĐ; Tim đỏ nhám 700ml: 1.270 VNĐ; Hồng Sapphire: 1.320 VNĐ; Tim cứng 500ml: 1.459 VNĐ; Tim cứng 700ml: 1.859 VNĐ |
| Ly nhựa PET (230ml / 270ml / 300ml / 350ml) | Nhựa PET nguyên sinh, phi 84mm và phi 93mm | Cái (trong microdata) | 370 / 482 / 453 / 448 | baobixanh.com.vn/ly-nhua-pet-230ml-8oz-84, .../ly-nhua-pet-270ml, .../ly-nhua-pet-300ml, .../ly-nhua-pet-350ml (danh-muc-chuan-hoa-so-bo.csv) | Giá lần lượt cho 230ml (8oz-Ø84): 370 VNĐ; 270ml (9oz-Ø93): 482 VNĐ; 300ml (10oz-Ø84): 453 VNĐ; 350ml (12oz-Ø84): 448 VNĐ |
| Ly nhựa PET 360ml \- 12oz (Ø93) | Nhựa PET nguyên sinh, miệng 93mm x đáy 56mm x cao 107mm, nặng 9.5g (+/-0.5), 1.000 cái/thùng | Cái (trong microdata) | 509 | baobixanh.com.vn/ly-nhua-pet-360ml (snapshot-progress.json) | Mã UKP93-12/14 OZ PET-T; bản đáy bầu 360ml PET giá 471 VNĐ; bản in flexo 2 màu (5.000 cái) giá 813 VNĐ (baobixanh.com.vn/ly-nhua-4t-coffee trong du-lieu-tham-khao.json) |
| Ly nhựa PET 420ml (14oz \- Ø98) & 470ml (16oz \- Ø93) | Nhựa PET nguyên sinh; mẫu 470ml miệng 93mm x đáy 54.5mm x cao 133mm, nặng 10g (+/-0.5), 1.000 cái/thùng | Cái (trong microdata) | 588 / 568 | baobixanh.com.vn/ly-nhua-pet-420ml-14oz-98, baobixanh.com.vn/ly-nhua-pet-470ml (danh-muc-chuan-hoa-so-bo.csv, snapshot-progress.json) | 420ml (Ø98): 588 VNĐ; 470ml (Ø93): 568 VNĐ |
| Ly nhựa PET 500ml (16oz \- Ø98) | Nhựa PET nguyên sinh, miệng 98mm x đáy 59mm x cao 120mm, nặng 11.5g (+/-0.5), 1.000 cái/thùng | Cái (trong microdata) | 642 | baobixanh.com.vn/ly-nhua-pet-500ml (snapshot-progress.json) | Mã UKP98-16OZ PET-T-1  |
| Ly nhựa PET 590ml (20oz \- Ø93) & 600ml (20oz \- Ø98) | Nhựa PET nguyên sinh, nặng 13.5g (+/-0.5), 1.000 cái/thùng; 590ml cao 148mm, 600ml cao 130mm | Cái (trong microdata) | 809 / 792 | baobixanh.com.vn/ly-nhua-pet-590ml, baobixanh.com.vn/ly-nhua-pet-600ml (snapshot-progress.json) | 590ml (Ø93): 809 VNĐ; 600ml (Ø98): 792 VNĐ |
| Ly nhựa PET 650ml (22oz \- Ø98) & 700ml (24oz \- Ø98) | Nhựa PET nguyên sinh; mẫu 700ml miệng 98mm x đáy 59mm x cao 154mm, nặng 15.5g (+/-0.5), 1.000 cái/thùng | Cái (trong microdata) | 900 / 960 | baobixanh.com.vn/ly-nhua-pet-650ml-22oz-98, baobixanh.com.vn/ly-nhua-pet-700ml (danh-muc-chuan-hoa-so-bo.csv, snapshot-progress.json) | 650ml (Ø98): 900 VNĐ; 700ml (Ø98): 960 VNĐ |
| Nắp cầu PET (phi 84 / 90 / 93 / 95 / 98 / cầu vuông 95\) | Nhựa PET trong suốt, 2.000 cái/bao (50 cái/túi) | Cái (trong microdata) | 168 / 220 / 222 / 227 / 248 / 218 | baobixanh.com.vn/nap-cau-84, .../nap-cau-90, .../nap-cau-93, .../nap-cau-95, .../nap-cau-98, .../nap-cau-vuong-95 (danh-muc-chuan-hoa-so-bo.csv, snapshot-progress.json) | Giá tương ứng từng kích cỡ phi 84, 90, 93, 95, 98 và cầu vuông 95 |
| Nắp bằng PET / PP (phi 67 / 90 / 93 / 95 / 98 / 106 / 117 / 150\) | Nhựa PET hoặc PP, 2.000 cái/thùng | Cái (trong microdata) | 102 \- 545 | baobixanh.com.vn/nap-bang-95, .../nap-bang-150-pp (danh-muc-chuan-hoa-so-bo.csv) | PET 95: 102 VNĐ; PET 90: 122 VNĐ; PET 98: 175 VNĐ; PET 67: 176 VNĐ; PP 106 không lỗ: 195 VNĐ, có lỗ: 213 VNĐ; PET 117: 196 VNĐ; PET 93: 198 VNĐ; PP D98: 320 VNĐ; PP D122: 420 VNĐ; PP D107: 466 VNĐ; PP D138: 480 VNĐ; PET 150: 530 VNĐ; PP 150: 545 VNĐ |
| Nắp nóng có khóa, Nắp bật & Nắp tim (phi 75 / 77 / 80 / 90 / 93\) | Nhựa chịu nhiệt / nhựa cứng | Cái (trong microdata) | 207 \- 529 | baobixanh.com.vn/nap-nong-den-co-khoa-90, .../nap-tim-den (danh-muc-chuan-hoa-so-bo.csv, snapshot-progress.json) | Nóng đen 77: 207 VNĐ; Trực tiếp 93: 252 VNĐ; Nắp bật 90: 256 VNĐ; Nóng đen 80: 259 VNĐ; Tim trong: 286 VNĐ; Nóng đen 90: 289 VNĐ; Nóng trắng 90: 306 VNĐ; Tim đen/trắng: 400 VNĐ; Nóng đen 75: 412 VNĐ; Nóng trắng 80: 529 VNĐ |
| Tô giấy trắng & Kraft (90ml \- 1000ml) | 90ml (3oz) đến 1000ml (36oz), 1PE hoặc 2PE | Cái (trong microdata) | 485 \- 1.957 | baobixanh.com.vn/to-giay-90ml-3oz, .../to-giay-500ml-16oz, .../to-giay-kraft-dung-salad-1000ml (danh-muc-chuan-hoa-so-bo.csv) | Trắng 90ml: 485 VNĐ; 120ml: 730 VNĐ; 270ml: 800 VNĐ; 360ml: 1.170 VNĐ; 500ml: 1.400 VNĐ; 750ml: 1.398 VNĐ; 1000ml: 1.500 VNĐ; Kraft 750ml: 1.420 VNĐ; Kraft 1000ml: 1.600 VNĐ; Kraft salad 750ml: 1.740 VNĐ, 1000ml: 1.957 VNĐ |
| Ống hút nhựa PP (phi 6, 8, 12), Ống hút giấy, Túi, Cuộn màng ép, Chai nhựa, Muỗng | Ống hút: bịch 500g / 1000g (1kg); Túi: kg/bịch; Cuộn màng ép: cuộn 1.5kg; Muỗng: bịch 50 / 100 cái | Bịch / Kg / Cuộn / Cái | 6.000 \- 430.000 | baobixanh.com.vn (danh-muc-chuan-hoa-so-bo.csv, snapshot-progress.json) | Ống hút nhựa: 33.000 \- 65.000 VNĐ/bịch; Ống hút giấy: 1.100 VNĐ/cái; Túi 1-2 ly: 50.000 VNĐ, chữ T: 53.500 VNĐ, zipper: 85.000 \- 94.000 VNĐ; Cuộn màng ép: 110.000 VNĐ (trơn/in sẵn), 260.000 VNĐ (ly giấy), 350.000 \- 400.000 VNĐ (in lụa), 430.000 VNĐ (in flexo); Chai PET: 1.140 \- 3.340 VNĐ/chai; Muỗng: 6.000 \- 20.000 VNĐ/bịch |
| Tất cả 22 sản phẩm của Site B (lynhuabinhminh.com) | Ly giấy, ly PP, ly PET, ly nắp cầu | \[KHÔNG CÓ DỮ LIỆU\] | \[KHÔNG CÓ DỮ LIỆU\] | doi-chieu-hai-nguon-tham-khao.csv, phieu-xac-minh-22-san-pham.csv  | Dữ liệu đính kèm không chứa trường giá của lynhuabinhminh.com |

### **━━ BẢNG D — NGÂN HÀNG CÂU HỎI KHÁCH HÀNG ━━**

| Câu hỏi | Ý định (Thông tin/So sánh/Mua hàng) | Site nào trả lời | Câu trả lời có con số cụ thể không (Có/Không) |
| :---- | :---- | :---- | :---- |
| Đơn vị cung cấp những nhóm bao bì nào, có bán sỉ, bán số lượng ít và gộp nhiều loại bao bì trong cùng một đơn hàng không? | Mua hàng | Site A (baobixanh.com.vn/cac-cau-hoi-thuong-gap-faqs trong du-lieu-tham-khao.json) | Có |
| Thời gian sản xuất ly nhựa, ly giấy in lụa 1 màu, in offset nhiều màu và ly giấy 2 lớp (đơn mới chưa có khung/bản kẽm so với đơn cũ) mất bao nhiêu ngày và nên đặt trước bao lâu? | Mua hàng | Site A (baobixanh.com.vn/thoi-gian-san-xuat-ly-nhua-ly-giay trong du-lieu-tham-khao.json) | Có |
| Đơn vị Oz là gì, quy đổi các cỡ ly 4oz, 6oz, 8oz, 9oz, 12oz, 16oz, 20oz, 22oz, 24oz sang ml như thế nào? | Thông tin | Cả hai (baobixanh.com.vn/oz-la-gi trong bai-viet-seo-tham-khao.csv; tên sản phẩm của cả 2 site trong doi-chieu-hai-nguon-tham-khao.csv) | Có |
| Vì sao nhiều quán chọn ly nhựa PP thay vì ly nhựa PET (hoặc ngược lại) khi bán trà sữa, cà phê và giao qua ứng dụng? | So sánh | Site A (baobixanh.com.vn/ly-nhua-pp-700ml, baobixanh.com.vn/cac-loai-nhua-lam-bao-bi trong snapshot-progress.json, du-lieu-tham-khao.json) | Có |
| Ly giấy tráng 1 lớp PE (1PE) và 2 lớp PE (2PE) khác nhau thế nào, loại nào đựng được đá lạnh mà không bị thấm nhũn form ly? | So sánh | Site A (baobixanh.com.vn/ly-giay-6oz-180ml, baobixanh.com.vn/ly-giay-9oz-270ml, baobixanh.com.vn/ly-giay-12oz-360ml trong snapshot-progress.json) | Có |
| Ly nhựa PET và chai nhựa PET có đựng được nước sôi, cà phê nóng, cho vào lò vi sóng hay ép màng nhiệt được không? | Thông tin | Site A (baobixanh.com.vn/ly-nhua-pet-500ml, baobixanh.com.vn/chai-nhua-1-lit trong snapshot-progress.json) | Có |
| Cách chọn đường kính nắp (phi 84, 90, 93, 95, 98mm) và kiểu nắp (nắp cầu, nắp bằng, nắp bật, nắp tim, nắp nóng có khóa) khớp với từng loại ly? | Mua hàng | Cả hai (baobixanh.com.vn/nap-cau-93, baobixanh.com.vn/nap-bang-95 và tên/URL sản phẩm lynhuabinhminh.com trong snapshot-progress.json, doi-chieu-hai-nguon-tham-khao.csv) | Có |
| Một thùng ly giấy, ly nhựa, nắp hoặc cuộn màng ép đóng gói bao nhiêu cái/túi, bao nhiêu cái/thùng và kích thước thùng carton là bao nhiêu? | Mua hàng | Site A (baobixanh.com.vn/ly-nhua-pet-500ml, baobixanh.com.vn/ly-giay-22oz-680ml, baobixanh.com.vn/cuon-ep-ly-in-san trong snapshot-progress.json) | Có |
| Một cuộn màng ép ly nặng bao nhiêu kg, ép được bao nhiêu nắp và số lượng nhận in lụa 1 màu tối thiểu là mấy cuộn? | Mua hàng | Site A (baobixanh.com.vn/cuon-mang-ep-ly-tron, baobixanh.com.vn/cuon-ep-ly-in-lua-1-mau trong snapshot-progress.json, du-lieu-tham-khao.json) | Có |
| Giải mã 6 loại nhựa thông dụng (PET, HDPE, PVC, PP, PS, PC) và các ký hiệu dưới đáy bao bì: loại nào an toàn thực phẩm, không chứa BPA? | Thông tin | Site A (baobixanh.com.vn/cac-loai-nhua-lam-bao-bi, baobixanh.com.vn/ky-hieu-nhua trong du-lieu-tham-khao.json, bai-viet-seo-tham-khao.csv) | Có |
| Mở quán cafe, trà sữa nên chọn mẫu ly và dung tích nào (360ml size S, 500ml size M, 700ml size L) để tối ưu giá cost nguyên liệu? | Mua hàng | Site A (baobixanh.com.vn/ly-giay-9oz-270ml, baobixanh.com.vn/ly-nhua-pp-500ml, baobixanh.com.vn/ly-nhua-pp-700ml trong snapshot-progress.json) | Có |
| Cách bảo quản ly giấy, ly nhựa, nắp PET trong kho để tránh ẩm mốc, côn trùng và tránh biến dạng do nắng nóng? | Thông tin | Site A (baobixanh.com.vn/ly-giay-12oz-360ml, baobixanh.com.vn/nap-cau-93 trong snapshot-progress.json) | Có |
| Chính sách giao nhận nội thành, gửi nhà xe đi tỉnh, thời gian giao hàng trong ngày và điều kiện bảo hành đổi trả hoàn tiền như thế nào? | Mua hàng | Site A (baobixanh.com.vn/chinh-sach-van-chuyen-thanh-toan, baobixanh.com.vn/chinh-sach-doi-tra trong du-lieu-tham-khao.json) | Có |
| Chuẩn ATVS TP, tiêu chuẩn HACCP, ISO 9001 là gì và điều kiện để cơ sở kinh doanh thực phẩm, đồ uống được cấp phép? | Thông tin | Site A (baobixanh.com.vn/atvs-tp-la-gi, baobixanh.com.vn/tieu-chuan-iso-9001-la-gi trong du-lieu-tham-khao.json, thong-ke-ngay-bai-viet.json) | Có |
| Mở quán cà phê nhượng quyền, trang trí quán trà sữa bình dân và quản lý quán cafe cho người mới cần lưu ý những gì? | Thông tin | Site A (baobixanh.com.vn/ca-phe-nhuong-quyen, baobixanh.com.vn/cach-quan-ly-quan-cafe, baobixanh.com.vn/cach-trang-tri-tra-sua-binh-dan trong du-lieu-tham-khao.json) | Có |

### **━━ BẢNG E — PHIẾU ĐO XƯỞNG ━━**

| Mã tạm | Nhóm | Loại | Dung tích | Dung tích thực tế khi đổ đầy tới miệng / tới vạch dùng (ml) | Đường kính miệng ngoài (mm, đo mép ngoài) | Đường kính đáy ngoài (mm) | Chiều cao tổng (mm) | Trọng lượng 1 cái (g, cân điện tử) | Chất liệu & Số lớp phủ PE (1PE/2PE) | Định lượng giấy (gsm) / Độ dày nhựa (zem) | Nhiệt độ chịu nhiệt tối đa (°C) | Mã nắp đậy vừa khít & Ép được màng không (Có/Không) | Đường kính lỗ hút trên nắp (mm) & Kiểu lỗ | Có màng bọc từng chiếc không (Có/Không) | Quy cách đóng gói (số cái/túi, số cái/thùng) | Kích thước thùng carton Dài x Rộng x Cao (mm) | Màu sắc & Độ trong thực tế | Kỹ thuật in áp dụng & Số màu tối đa | Số lượng nhận in tối thiểu (cái/cuộn) | Thời gian sản xuất đơn in mới / đơn cũ (ngày) | Khổ màng Ngang x Dài (mm) & Số nắp/cuộn | Hồ sơ chứng chỉ ATTP có sẵn | Ghi chú |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| TTP-LG-01 | Ly giấy | Ly giấy trắng / in logo | 4oz \- 120ml | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo mẫu ly thử cafe nóng |
| TTP-LG-02 | Ly giấy | Ly giấy trắng / in logo | 6oz \- 180ml | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Kiểm tra 1PE hay 2PE |
| TTP-LG-03 | Ly giấy | Ly giấy trắng / in logo | 8oz \- 240ml | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Thử lắp nắp nóng khóa phi 80mm |
| TTP-LG-04 | Ly giấy | Ly giấy trắng / in logo | 9oz \- 270ml | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo tách biệt bản 1PE và 2PE |
| TTP-LG-05 | Ly giấy | Ly giấy trắng / in logo | 12oz \- 360ml | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo kỹ miệng 88mm hay 90mm |
| TTP-LG-06 | Ly giấy | Ly giấy trắng / in logo | 14oz \- 420ml | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Kiểm tra độ khít nắp phi 90mm |
| TTP-LG-07 | Ly giấy | Ly giấy trắng / in logo | 16oz \- 500ml | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Size M chủ lực quán cafe/trà sữa |
| TTP-LG-08 | Ly giấy | Ly giấy trắng / in logo | 22oz \- 680ml (700ml) | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Chốt dung tích thực là 680ml hay 700ml |
| TTP-LG-09 | Ly giấy | Ly giấy Kraft / Gợn sóng | 8oz / 9oz / 12oz / 16oz | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo từng cỡ thực bán tại xưởng |
| TTP-PP-01 | Ly nhựa PP | Ly PP đáy bằng | 360ml (12oz) | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Kiểm tra miệng phi 95mm |
| TTP-PP-02 | Ly nhựa PP | Ly PP đáy bằng | 500ml (16oz) | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo cả bản dày, mỏng và bản sọc |
| TTP-PP-03 | Ly nhựa PP | Ly PP đáy bằng | 650ml (22oz) | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đối chiếu chiều cao với bản 700ml |
| TTP-PP-04 | Ly nhựa PP | Ly PP đáy bằng | 700ml (24oz) | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo cả bản trơn và bản sọc (đủ/thiếu) |
| TTP-PP-05 | Ly nhựa PP | Ly PP cỡ đại (tắc/mía) | 800ml / 900ml / 1000ml | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo miệng phi 106mm hoặc phi 117mm |
| TTP-PP-06 | Ly nhựa PP | Ly PP đáy bầu (Q-cup) | 360ml / 500ml / 700ml | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo chiều cao và phi miệng 90mm / 95mm |
| TTP-PP-07 | Ly nhựa PP | Ly PP cứng/mềm nắp tim | 500ml / 700ml | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Kiểm tra độ khít với nắp tim phi 90mm |
| TTP-PET-01 | Ly nhựa PET | Ly PET trong suốt | 360ml (12oz \- Ø93) | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đối chiếu mẫu phieu-xac-minh-22-san-pham.csv  |
| TTP-PET-02 | Ly nhựa PET | Ly PET trong suốt | 470ml (16oz \- Ø93) | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | So sánh với mẫu 500ml phi 98mm |
| TTP-PET-03 | Ly nhựa PET | Ly PET trong suốt | 500ml (16oz \- Ø98) | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Thử độ khít nắp cầu/nắp bằng phi 98mm |
| TTP-PET-04 | Ly nhựa PET | Ly PET trong suốt | 20oz \- Ø93 (590ml/600ml) | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo thực tế để chốt nhãn 590ml hay 600ml |
| TTP-PET-05 | Ly nhựa PET | Ly PET trong suốt | 20oz \- Ø98 (590ml/600ml) | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo thực tế để chốt nhãn 590ml hay 600ml |
| TTP-PET-06 | Ly nhựa PET | Ly PET trong suốt | 24oz \- Ø98 (700ml/710ml) | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo thực tế để chốt nhãn 700ml hay 710ml |
| TTP-NAP-01 | Nắp | Nắp cầu / Nắp bằng PET | Phi 84 / 90 / 93 / 95 / 98mm | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo đường kính lọt lòng và lỗ cắm ống hút |
| TTP-NAP-02 | Nắp | Nắp nóng khóa / Nắp bật / Nắp tim | Phi 80 / 90 / 93mm | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Thử khả năng chống tràn khi nghiêng ly |
| TTP-OH-01 | Ống hút | Ống hút nhựa PP / Ống hút giấy | Phi 6 / Phi 8 / Phi 12mm | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đếm số cái thực tế trên mỗi bịch 500g / 1000g |
| TTP-TG-01 | Tô/Hộp giấy | Tô giấy trắng / Kraft | 360ml / 500ml / 750ml / 1000ml | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Kiểm tra độ khít của nắp PP đậy tô khi đựng nóng |
| TTP-TUI-01 | Túi | Túi 1 ly, 2 ly, chữ T | Đựng ly 360ml \- 700ml | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đếm số cái/kg và thử độ bền khi treo xe máy |
| TTP-PK-01 | Phụ kiện khác | Cuộn màng ép ly | Cuộn tiêu chuẩn / In logo | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | \_\_\_\_ | Đo khổ màng (mm), cân nặng (kg) và số nắp thực tế |

### **━━ BẢNG F — KHOẢNG TRỐNG CƠ HỘI ━━**

| Thuộc tính/Chủ đề | Vì sao người mua cần | Ưu tiên (Cao/TB/Thấp) |
| :---- | :---- | :---- |
| Dung tích tràn viền so với dung tích pha chế sử dụng thực tế (kèm vạch định lượng) | Hai đối thủ đang ghi lệch nhau trên cùng một cỡ ly (cùng cỡ nhưng nơi ghi dung tích lớn, nơi ghi dung tích nhỏ hơn). Chủ quán tại Đà Nẵng cần biết chính xác dung tích tới vạch pha chế để định lượng công thức cốt trà, sữa và đá không bị hụt hoặc tràn khi đóng nắp. | Cao |
| Độ dày thành nhựa thực tế đo bằng đơn vị Zem (hoặc mm) và lực bóp thân ly | Cả hai đối thủ không công bố số zem mà chỉ ghi chung chung "dày dặn", "loại đủ", "loại thiếu". Chủ quán cần thông số độ dày cụ thể để biết ly có bị ọp ẹp khi khách cầm hay bị bẹp miệng khi dập máy ép màng tự động hay không. | Cao |
| Bảng tra cứu chéo độ tương thích Ly – Nắp – Ống hút – Túi theo từng mã hàng của xưởng | Khách mua lẻ từng món rất dễ mua nhầm nắp lệch kích cỡ miệng ly hoặc nắp có lỗ nhỏ không đút vừa ống hút trân châu. Một bảng tra cứu chuẩn xác ngay trên từng trang sản phẩm giúp chủ quán chốt đơn nguyên bộ nhanh chóng. | Cao |
| Thời gian chống ngấm/mủn thực tế của ly giấy, tô giấy khi đựng đá lạnh hoặc nước lèo nóng trong điều kiện khí hậu nóng ẩm miền Trung | Các quán bán mang đi qua ứng dụng giao đồ ăn cần biết sau bao lâu kể từ lúc đóng gói thì ly giấy bắt đầu đổ mồ hôi làm mềm thân ly hoặc tô giấy đựng bún/phở bị mềm đáy. | Cao |
| Chính sách giao hàng nội thành Đà Nẵng và gửi chành xe đi miền Trung (Huế, Quảng Nam, Quảng Ngãi) | Cả hai đối thủ trong dữ liệu đều đặt trụ sở tại TP.HCM (thậm chí trang danh mục ly giấy của đối thủ còn để sót dòng nháp chưa viết chính sách giao hàng). Chủ quán ở Đà Nẵng cần biết thời gian giao khẩn cấp khi quán hết ly đột xuất vào cuối tuần và mức miễn phí vận chuyển theo quận/huyện. | Cao |
| Chính sách hỗ trợ lưu kho tại xưởng (in số lượng lớn để được giá tốt nhưng nhận hàng và thanh toán chia làm nhiều đợt) | Phần lớn quán cafe, trà sữa tại Đà Nẵng có mặt bằng nhỏ, không có kho chứa cùng lúc nhiều thùng ly cồng kềnh. Công bố rõ chính sách giữ hàng hộ tại xưởng sẽ giải quyết ngay rào cản diện tích cho khách. | Cao |
| Bảng giá bậc thang minh bạch theo số lượng thùng cho cả ly trơn và ly in logo | Đối thủ chỉ để một mức giá đơn lẻ trong dữ liệu cấu trúc (hoặc để giá bằng không ghi Liên hệ) khiến khách hàng không tính ngay được chi phí bao bì trên mỗi ly nước bán ra khi tăng sản lượng đặt mua. | Cao |
| Quy chuẩn file thiết kế in ấn, vùng an toàn in trên thân ly côn (tránh méo logo) và chính sách duyệt mẫu thực tế | Chủ quán mới mở thường không có file thiết kế chuẩn hoặc không hình dung được logo khi lên mặt cong của ly sẽ bị biến dạng thế nào. Cần hướng dẫn rõ định dạng file và cam kết gửi mẫu duyệt trước khi chạy hàng loạt. | TB |
| Độ bám mực in khi ngâm đá lạnh, đổ mồ hôi và chứng nhận mực in an toàn thực phẩm (không mùi) | Quán cafe, trà sữa và khách sạn rất sợ mực in bị bong tróc dính vào tay khách hàng hoặc có mùi hôi của mực in công nghiệp khi cầm uống. | TB |
| Khả năng xếp chồng chịu lực và chống rò rỉ khi tài xế giao hàng treo xe di chuyển đường xa | Tài xế tại Đà Nẵng thường treo nhiều túi ly trên xe hoặc xếp chồng các hộp/tô giấy trong thùng giữ nhiệt; thông tin thực nghiệm về độ kín của nắp khi nghiêng lắc sẽ tạo niềm tin lớn. | TB |
| Chính sách gửi bộ mẫu thử tận quán tại Đà Nẵng | Chủ quán muốn cầm tận tay để thử độ cứng của ly, độ trong của nhựa PET và thử đưa vào máy ép màng sẵn có tại quán trước khi đặt in hàng loạt. | TB |

### **TỰ KIỂM TRA**

* **Số dòng mỗi bảng (tính số dòng dữ liệu, không tính dòng tiêu đề bảng):**  
  * **Bảng A (Danh mục sản phẩm):** 20 dòng.  
  * **Bảng B (Ma trận thuộc tính):** 23 dòng.  
  * **Bảng C (Giá tham chiếu):** 29 dòng.  
  * **Bảng D (Ngân hàng câu hỏi khách hàng):** 15 dòng.  
  * **Bảng E (Phiếu đo xưởng):** 28 dòng.  
  * **Bảng F (Khoảng trống cơ hội):** 11 dòng.  
* **Có con số nào không có nguồn không?** Không (Mọi con số ở Bảng A, B, C, D đều được trích xuất trực tiếp và ghi kèm nguồn từ các file đính kèm du-lieu-tham-khao.json, snapshot-progress.json, danh-muc-chuan-hoa-so-bo.csv, doi-chieu-hai-nguon-tham-khao.csv, bai-viet-seo-tham-khao.csv, sitemap\_products\_1.xml; Bảng E để trống \_\_\_\_ cho xưởng đo; Bảng F là bảng đề xuất hoàn toàn không chứa con số theo đúng quy định).  
* **Có ô nào bạn suy đoán thay vì trích xuất không? (liệt kê):**  
  * Cột **"Mức quan trọng với người mua (Cao/TB/Thấp)"** ở **Bảng B** (23 ô) và cột **"Ý định (Thông tin/So sánh/Mua hàng)"** ở **Bảng D** (15 ô): Được đánh giá và phân loại theo yêu cầu cấu trúc cột của đề bài dựa trên nghiệp vụ phân tích hành vi mua hàng B2B ngành F\&B.  
  * Toàn bộ **Bảng F (Khoảng trống cơ hội)** (11 dòng): Là nội dung đề xuất chiến lược dựa trên khoảng trống dữ liệu giữa 2 đối thủ và nhu cầu thực tế của khách hàng F\&B tại Đà Nẵng theo đúng yêu cầu của đề bài.  
  * Các thông tin không có trong bộ dữ liệu đối chiếu của Site B (lynhuabinhminh.com) hoặc không được công bố trên cả 2 site (như độ dày nhựa tính bằng đơn vị zem) đều được ghi rõ là \[KHÔNG CÓ DỮ LIỆU\], tuyệt đối không tự suy đoán.