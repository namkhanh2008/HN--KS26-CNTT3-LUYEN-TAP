## 4.1. Bảo vệ dữ liệu và chống ảo giác

### a) Ghi chú đã ẩn danh hoá

**GHI CHU DA AN DANH**

```text
Khán giả [TEN_KHACH_HANG], số điện thoại [SO_DIEN_THOAI], số CCCD [CCCD_KHACH_HANG], emaiL [EMAIL_KHACH_HANG], đặt 3 vé gói SVT trận bán kết Cúp Sao Vàng ngày 18/12/2026 cho 2 người lớn và 1 trẻ em 9 tuổi. Khán giả đã chuyển khoản đặt cọc 1.500.000 đồng. Khán giả yêu cầu 3 ghế ngồi cạnh nhau gần lối đi.

```

### b) Hai câu lệnh chống ảo giác

**CAU LENH**

```text
CÂU 1:
DỰA TRÊN FILE CHÍNH SÁCH HOÀN/HỦY VÉ MÀ TÔI GỬI HÃY TRẢ KỜI CÂU HỎI TRÊN CỦA TÔI. NẾU CÁC THÔNG TIN KHÔNG CÓ TRONG CHÍNH SÁCH THÌ KHÔNG TỰ BỊA CHUYỆN CHÍNH SÁCH MÀ HÃY TRẢ LỜI TRỰC TIẾP LÀ"CHÍNH SÁCH VÀ ĐIỀU KHOẢN NÀY KHÔNG TỒN TẠI"
CÂU 2:
KHI BẠN TRẢ LỜI CHO TÔI THÌ HÃY AI ghi rõ câu trả lời lấy từ mục hoặc điều khoản nào trong file. 

```

## 4.2. Trích xuất tin nhắn đặt vé ra JSON

**PROMPT**

```text
[Context]: BẠN LÀ MỘT CHUYÊN GIA PHÂN TÍCH TIN NHẮN KHÁCH HÀNG BẠN CÓ NHIỆM VỤ CHUYỂN CÁC TIN NHẮN THÀNH DẠNG file JSON

[Request]: BẠN HÃY AI chuyển dữ liệu TN1, TN2, TN3 trong thẻ <tin_nhan> thành một mảng JSON 3 đối tượng, đúng thứ tự, đúng 6 trường như tin nhắn mẫu NHƯ SAU:{"ma_goi", "ngay_su_kien", "nguoi_lon", "tre_em", "loai_ve", "ghi_chu"}NHƯ TIN NHẮN MẪU bạn có thể xem 2 ví dụ mẫu ở bảng <vi_du>

[Explanation]: KHI CHUYỂN THÀNH file JSON HÃY BÁM THEO QUY TẮC CHUẨN HOÁ (5 quy tắc) SAU:
<quy_chuan>
BẢNG MÃ GÓI
SVT – Sân Vận Động: vé trận đấu
FZ – Fan Zone: khu cổ vũ
VIP – Khán đài VIP

QUY TẮC CHUẨN HOÁ (5 quy tắc)

1. ma_goi lấy theo bảng mã gói.
2. ngay_su_kien dạng YYYY-MM-DD; tin nhắn không ghi năm thì lấy năm 2026; không có ngày cụ thể thì null.
3. Khách không nhắc trẻ em thì tre_em là 0 và mọi khách là người lớn.
4. loai_ve chỉ nhận "thuong", "vip" hoặc null.
5. ghi_chu chỉ ghi yêu cầu đặc biệt về chỗ ngồi, hỗ trợ di chuyển hoặc ăn uống; không có thì null.
CÂU TRẢ LỜI không chào hỏi, không giải thích và chỉ trả về dạng JSON
</quy_chuan>

<vi_du>
Tin nhắn mẫu 1:
Đặt giúp mình 2 vé VIP trận chung kết ngày 15/11/2026, 2 người lớn và 1 bé. Cần chỗ ngồi cạnh lối đi.
Kết quả đúng:
{"ma_goi": "VIP", "ngay_su_kien": "2026-11-15", "nguoi_lon": 2, "tre_em": 1, "loai_ve": "vip", "ghi_chu": "chỗ ngồi cạnh lối đi"}
Tin nhắn mẫu 2:
Cho mình một vé Fan Zone, ngày nào cũng được, mình đi một mình.
Kết quả đúng:
{"ma_goi": "FZ", "ngay_su_kien": null, "nguoi_lon": 1, "tre_em": 0, "loai_ve": "thuong", "ghi_chu": null}
</vi_du>
[Action]:1- đọc dữ liệu tin nhắn khách hàng mà tôi đã gửi
         2- chuẩn hóa về đúng các trường dữ liệu
         3- trả đúng định dạng JSON
[Tone]: NGẮN GỌN CHUYÊN NGHIỆP CỔ ĐIỂN TÔN TRỌNG
[Extras]: ĐỊNH DẠNG ĐẦU RA CHỈ LÀ DỮ LIỆU JSON. KHI CHUYỂN THÀNH file JSON BẠN CẦN BÁM THEO QUY TẮC TRONG THẺ <quy_chuan>

<tin_nhan>
TN1: Mình muốn đặt gói Sân Vận Động trận tứ kết ngày 20/12 nha, 2 người lớn với 1 bé 8 tuổi, vé thường.

TN2: Cho 3 người đi Fan Zone trận ngày 05/01/2027 ạ. Một người cần hỗ trợ xe lăn.

TN3: Trận chung kết Cúp Sao Vàng tháng 12 còn vé không ạ? Nhà em 4 người lớn, có một người khiếm thị cần hỗ trợ tìm chỗ, lấy vé VIP.

</tin_nhan>
```

## 4.3. Báo giá vé bằng Chain-of-Thought

### a) Prompt

**PROMPT**

```text
[CONTEXT]: bạn là chuyên viên tổng thu chi bạn có nhiệm vụ tính tổng tiền 
[Request]:  bạn hãy tính tổng tiềnDỰA VÀO BẢNG <phan_tach> hãy suy luận từng bước theo thứ tự tiền người lớn → tiền trẻ em → tiền vé → giảm giá nhóm → phụ thu → tổng tiền
, mỗi bước ghi phép tính dòng cuối có dạng [RESULT: <tổng tiền> đồng]
<phan_tach>
BẢNG GIÁ VÉ (đồng/người lớn)
SVT – Sân Vận Động: 1.200.000
FZ – Fan Zone: 800.000
VIP – Khán đài VIP: 2.500.000

QUY TẮC TÍNH GIÁ
1. Trẻ em từ 5 đến 11 tuổi tính 70% giá người lớn. Trẻ dưới 5 tuổi miễn phí.
2. Nhóm từ 5 người lớn trở lên được giảm 5% trên tiền vé (tiền người lớn + tiền trẻ em).
3. Phụ thu khu ghế ưu tiên: 300.000 đồng/người. Phụ thu không được giảm giá.
4. Tổng tiền = tiền vé sau giảm + phụ thu.

YÊU CẦU BÁO GIÁ
Nhóm cổ động viên đi xem trận bán kết, mua gói SVT, gồm 5 người lớn, 2 trẻ em (8 tuổi và 10 tuổi) và 1 bé 3 tuổi. Có 1 người lớn chọn khu ghế ưu tiên.
</phan_tach>
[Explanation]: khi tính tổng tiền hãy dựa vào QUY TẮC TÍNH GIÁ ở bảng <phan_tach>
[ACTION]: ĐỌC DỮ LIỆU MÀ TÔI GỬI->TÍNH THỨ TỰ TIỀN TỪNG BƯỚC->TÍNH TỔNG TIỀN->ĐƯA RA DẠNG [RESULT: <tổng tiền> đồng]
[TONE]: CHUYÊN NGHIỆP, NGẮN GỌN, KHÔNG LỜI CHÀO
```

## 4.4. Dây chuyền xử lý khiếu nại (Prompt Chaining)

### a) Prompt Trạm 1

**PROMPT**

```text
[Context]:BẠN LÀ CHUYÊN VIÊN QUẢN LÝ KHIẾU NẠI CỦA TRẠM NHIỆM VỤ HÃY ĐỌC EMAIL VÀ CHI TRẢ KHIẾU NẠI ĐÚNG CÁCH
[Request]:Trạm 1 – BẠN HÃY đọc email Ở BẢNG <email>, trả về chỉ một đối tượng JSON gồm đúng 4 trường:
{"loai_su_co": một trong "tran_gio" | "sai_khu_vuc" | "nhan_vien" | "khac", "so_khach": số nguyên, "so_hiep_bi_anh_huong": số nguyên hoặc null, "tom_tat": "không quá 20 từ"}

 
[Explanation]:khi chuyển sang dạng JSON HÃY BÁM THEO NHỮNG chính sách SAU Ở BẢNG <chinh_sach>

<chinh_sach>
======================================================
CHÍNH SÁCH ĐỀN BÙ CỦA BAN TỔ CHỨC CÚP SAO VÀNG
======================================================

- tran_gio: trận đấu bắt đầu trễ trên 2 giờ do ban tổ chức: tặng voucher 200.000 đồng/khách.
- sai_khu_vuc: khán giả bị xếp sang khu vực thấp hơn quyền lợi đã cam kết: hoàn 500.000 đồng/khách cho mỗi hiệp bị ảnh hưởng.
- nhan_vien: khiếu nại về thái độ nhân viên: tặng voucher 300.000 đồng/khách.
- khac: chuyển bộ phận Chăm sóc khán giả xem xét, chưa đề xuất mức đền bù.
- Tổng mức đền bù trên 1.500.000 đồng phải được Trưởng ban Chăm sóc khán giả duyệt trước khi gửi khách.

</chính_sach>
[Action]:1- đọc dữ liệu tin nhắn khách hàng mà tôi đã gửi
         2- chuẩn hóa về đúng các trường dữ liệu
         3- trả đúng định dạng JSON
[Tone]: NGẮN GỌN CHUYÊN NGHIỆP CỔ ĐIỂN TÔN TRỌNG
[Extras]: ĐỊNH DẠNG ĐẦU RA CHỈ LÀ DỮ LIỆU JSON
<email>
EMAIL KHIẾU NẠI CỦA KHÁN GIẢ

Tôi là khán giả mua vé gói SVT trận Cúp Sao Vàng ngày 02/11/2026, đi 2 người lớn. Ban tổ chức cam kết khu khán đài có mái che nhưng trong 2 hiệp đầu chúng tôi bị xếp sang khu không mái, trời mưa và ghế ướt. Nhân viên soát vé rất nhiệt tình, tôi không có gì phàn nàn về nhân viên. Tôi đề nghị ban tổ chức giải quyết thỏa đáng.

</email>
```

### b) Hai điều cần kiểm tra ở JSON đầu ra của Trạm 1

1. JSON hợp lệ, có đúng 4 trường theo yêu cầu, đúng kiểu dữ liệu.

2. Loại sự cố, số khách, số hiệp bị ảnh hưởng và nội dung tóm tắt phải chính xác, khớp với email gốc.

### c) Câu lệnh viết tiếp

**CAU LENH**

```text
Bạn là nhân viên chăm sóc khán giả của Ban tổ chức Cúp Sao Vàng. Dựa trên JSON trong thẻ <ket_qua_tram_2>, viết email phản hồi khán giả: xin lỗi, nêu đúng mức đền bù trong JSON, không tự đặt mức khác, giọng điệu chân thành, chuyên nghiệp, dưới 150 từ.
<ket_qua_tram_2>(JSON của Trạm 2)</ket_qua_tram_2>

```
