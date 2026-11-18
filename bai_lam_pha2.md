## 4.2. Trích xuất tin nhắn đặt vé ra JSON

**KET QUA AI**

```text
[
  {
    "ma_goi": "SVT",
    "ngay_su_kien": "2026-12-20",
    "nguoi_lon": 2,
    "tre_em": 1,
    "loai_ve": "thuong",
    "ghi_chu": null
  },
  {
    "ma_goi": "FZ",
    "ngay_su_kien": "2027-01-05",
    "nguoi_lon": 3,
    "tre_em": 0,
    "loai_ve": "thuong",
    "ghi_chu": "hỗ trợ xe lăn"
  },
  {
    "ma_goi": "VIP",
    "ngay_su_kien": null,
    "nguoi_lon": 4,
    "tre_em": 0,
    "loai_ve": "vip",
    "ghi_chu": "hỗ trợ người khiếm thị tìm chỗ"
  }
]
```

**Link trò chuyện:** https://chatgpt.com/share/6afd2778-0f88-83ec-ab86-01a4de943124

## 4.3. Báo giá vé bằng Chain-of-Thought

**KET QUA AI**

```text
1. Tiền người lớn
5 × 1.200.000 = 6.000.000 đồng.
2. Tiền trẻ em
- Trẻ 8 tuổi: 1.200.000 × 70% = 840.000 đồng.
- Trẻ 10 tuổi: 1.200.000 × 70% = 840.000 đồng.
- Trẻ 3 tuổi: Miễn phí.
Tổng: 840.000 + 840.000 = 1.680.000 đồng.
3. Tiền vé
6.000.000 + 1.680.000 = 7.680.000 đồng.
4. Giảm giá nhóm
Nhóm có 5 người lớn nên được giảm 5%.

7.680.000 × 5% = 384.000 đồng.
5. Phụ thu
1 × 300.000 = 300.000 đồng.
6. Tổng tiền
7.680.000 - 384.000 + 300.000 = 7.596.000 đồng.
KẾT QUẢ
[RESULT: 7.596.000 đồng]
```

**Link trò chuyện:**https://chatgpt.com/share/6afd2cc0-8bf8-83ec-ad6e-f4925a615bd5

### b) Kiểm tra kết quả AI

```
AI TÍNH ĐÚNG TỪNG BƯỚC 
```

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
{
  "loai_su_co": "sai_khu_vuc",
  "so_khach": 2,
  "so_hiep_bi_anh_huong": 2,
  "tom_tat": "2 khán giả bị xếp vào khu không mái che trong 2 hiệp đầu, không đúng quyền lợi vé đã cam kết."
}
```

**Link trò chuyện:**https://chatgpt.com/share/6afd30e4-5aac-83ec-bd79-26c1dc09525f
