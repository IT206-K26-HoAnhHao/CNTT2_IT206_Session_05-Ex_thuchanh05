# [Bài thực hành 5] Xây dựng chiến dịch truyền thông tuyển sinh khóa học

## 1. Tổng quan chiến dịch & Bối cảnh
* **Sản phẩm:** Khóa học Python cơ bản dành cho người mới bắt đầu (Thời lượng: 8 tuần).
* **Khách hàng mục tiêu:** Sinh viên năm nhất (Độ tuổi: 18–20).
* **Mục tiêu chiến dịch:** Thu hút 100 lượt đăng ký tư vấn.
* **Kênh truyền thông:** Facebook và TikTok.
* **Phương pháp kỹ thuật:** Áp dụng kỹ thuật **Prompt Chaining** (chuỗi 5 prompt liên tiếp, đầu ra của bước trước là đầu vào của bước sau) để đảm bảo tính liên kết chặt chẽ và không sai lệch thông tin khóa học.



## 2. Sơ đồ mô tả chuỗi Prompt (Prompt Chaining)

```text
[Thông tin khóa học gốc] 
       │
       ▼
┌────────────────────────────────────────────────────────┐
│ PROMPT 1: Phân tích chân dung khách hàng mục tiêu      │
└──────┬─────────────────────────────────────────────────┘
       │ (Output 1: Nỗi đau, nhu cầu, hành vi của SV năm 1)
       ▼
┌────────────────────────────────────────────────────────┐
│ PROMPT 2: Xác định thông điệp truyền thông chủ đạo     │
└──────┬─────────────────────────────────────────────────┘
       │ (Output 2: 1 Thông điệp chính & 3 luận điểm phụ)
       ▼
┌────────────────────────────────────────────────────────┐
│ PROMPT 3: Lập kế hoạch nội dung (Content Plan) 7 ngày  │
└──────┬─────────────────────────────────────────────────┘
       │ (Output 3: Lịch đăng bài chi tiết trên FB & TikTok)
       ▼
┌────────────────────────────────────────────────────────┐
│ PROMPT 4: Sản xuất nội dung (2 bài FB & 2 kịch bản TT) │
└──────┬─────────────────────────────────────────────────┘
       │ (Output 4: Nội dung chi tiết bám sát lịch & thông điệp)
       ▼
┌────────────────────────────────────────────────────────┐
│ PROMPT 5: Kiểm tra & Đánh giá tính nhất quán           │
└────────────────────────────────────────────────────────┘
```

### Chi tiết các câu lệnh (Prompts) đã sử dụng:
* **Prompt 1:** *"Đóng vai chuyên gia Marketing giáo dục. Dựa trên dữ liệu khóa học Python cơ bản (8 tuần, dành cho người mới bắt đầu, đối tượng sinh viên năm nhất 18-20 tuổi, mục tiêu 100 lượt đăng ký tư vấn trên Facebook và TikTok), hãy phân tích chi tiết chân dung khách hàng mục tiêu gồm: nhân khẩu học, tâm lý, nỗi đau (pain points), động lực học tập và hành vi sử dụng mạng xã hội."*
* **Prompt 2:** *"Dựa trên chân dung khách hàng ở [Output 1], hãy đề xuất DUY NHẤT 1 thông điệp truyền thông chính (Key Message) ngắn gọn, đánh trúng tâm lý sinh viên năm nhất chưa biết gì về lập trình, kèm theo 3 thông điệp hỗ trợ (Supporting Messages) làm nổi bật ưu thế khóa học 8 tuần."*
* **Prompt 3:** *"Sử dụng chân dung khách hàng từ [Output 1] và thông điệp truyền thông từ [Output 2], hãy lập kế hoạch nội dung (Content Plan) trong 7 ngày cho kênh Facebook và TikTok để đạt mục tiêu 100 lượt đăng ký tư vấn. Trình bày dạng bảng gồm: Ngày, Kênh, Chủ đề, Định dạng, Mục tiêu."*
* **Prompt 4:** *"Bám sát thông điệp ở [Output 2] và kế hoạch ở [Output 3], hãy viết chi tiết: (1) Hai bài đăng quảng cáo Facebook (có CTA kêu gọi đăng ký tư vấn); (2) Hai kịch bản video TikTok (thời lượng 30–45 giây, chia rõ phân cảnh, lời thoại, âm thanh/text trên màn hình). Tuyệt đối giữ nguyên thông tin khóa học 8 tuần."*
* **Prompt 5:** *"Đóng vai Quản lý chất lượng nội dung. Hãy rà soát toàn bộ [Output 1], [Output 2], [Output 3] và [Output 4] đối chiếu với đề bài gốc (Python cơ bản, 8 tuần, SV năm nhất 18-20 tuổi, mục tiêu 100 đăng ký tư vấn, kênh FB & TikTok). Lập báo cáo kiểm tra tính nhất quán về thông tin, đối tượng, thông điệp và đề xuất chỉnh sửa nếu có."*

## 3. Chân dung khách hàng mục tiêu (Output 1)

* **Nhân khẩu học:** Sinh viên năm nhất tại các trường Đại học/Cao đẳng, độ tuổi 18–20. Sống xa nhà, phụ thuộc tài chính phần lớn vào gia đình, nhạy cảm về học phí.
* **Nỗi đau (Pain Points):**
  * Bỡ ngỡ với môi trường đại học, sợ bị "ngợp" hoặc rớt môn các học phần Đại cương/Tin học cơ sở.
  * Chưa có nền tảng tư duy lập trình, lo sợ mình "không có năng khiếu IT" hoặc học không theo kịp bạn bè.
  * Mông lung về định hướng nghề nghiệp tương lai, lo lắng ra trường thất nghiệp nếu không có kỹ năng thực tế.
* **Động lực & Mong muốn:**
  * Muốn tìm một ngôn ngữ lập trình dễ tiếp cận nhất để làm bàn đạp (Python).
  * Muốn đạt điểm cao trên trường và sớm có kỹ năng để tự tin tham gia các CLB học thuật, cuộc thi sinh viên.
  * Cần một lộ trình ngắn gọn (8 tuần), cầm tay chỉ việc, không lan man lý thuyết hàn lâm.
* **Hành vi truyền thông:**
  * Sử dụng TikTok hàng ngày để giải trí nhanh, thích các video ngắn (30–45s), hài hước, bắt trend, phản ánh đúng đời sống sinh viên.
  * Sử dụng Facebook để cập nhật tin tức trường lớp, tham gia các hội nhóm sinh viên/tân sinh viên và nhắn tin trao đổi trực tiếp khi cần tư vấn.



## 4. Thông điệp truyền thông chính (Output 2)

* **Thông điệp chính (Key Message):** 
  > **"8 tuần làm chủ Python từ con số 0 – Tân sinh viên tự tin bứt phá điểm số và đón đầu cơ hội nghề nghiệp!"**
* **3 Thông điệp hỗ trợ (Supporting Messages):**
  1. **Dễ tiếp cận:** Lộ trình thiết kế riêng cho người mới bắt đầu, không yêu cầu kiến thức nền tảng.
  2. **Nhanh chóng & Thực tế:** Chỉ gói gọn trong 8 tuần, thực hành trực tiếp giúp giải quyết gọn gàng các bài tập trên giảng đường.
  3. **Đồng hành tận tâm:** Hỗ trợ giải đáp 1-1 và định hướng lộ trình công nghệ dài hạn cho sinh viên năm nhất.



## 5. Lịch đăng nội dung trong 7 ngày (Output 3)

| Ngày | Kênh | Chủ đề nội dung | Định dạng | Mục tiêu |
| :--- | :--- | :--- | :--- | :--- |
| **Ngày 1** | TikTok | Nỗi sợ mang tên "Code đại cương" của tân sinh viên và giải pháp | Video ngắn (35s) | Thu hút sự chú ý, tạo sự đồng cảm (Awareness) |
| **Ngày 2** | Facebook | Khai giảng khóa Python cơ bản 8 tuần dành riêng cho 2k7/2k8 (SV năm 1) | Bài viết + Ảnh Infographic | Giới thiệu tổng quan khóa học & Thông điệp chính |
| **Ngày 3** | TikTok | 1 ngày học Python thực chiến của sinh viên năm nhất có gì? | Video Vlog (40s) | Tạo niềm tin, cho thấy môi trường học gần gũi |
| **Ngày 4** | Facebook | Lộ trình 8 tuần từ "mù công nghệ" đến tự viết ứng dụng đầu tay | Bài viết Carousel (4 ảnh) | Thuyết phục bằng lộ trình rõ ràng, kích thích đăng ký tư vấn |
| **Ngày 5** | TikTok | 3 lý do tân sinh viên nên học Python càng sớm càng tốt | Video Talking-head (30s) | Khẳng định giá trị khóa học, điều hướng về Link Bio |
| **Ngày 6** | Facebook | Chia sẻ góc nhìn: Học sớm 8 tuần, nhàn tênh suốt 4 năm đại học | Bài viết Storytelling | Đánh vào tâm lý muốn bứt phá, tăng lượt inbox tư vấn |
| **Ngày 7** | FB & TikTok | Tổng kết tuần: Ưu đãi học phí đặc biệt cho 20 suất đăng ký tư vấn cuối cùng | Bài viết FB & Video nhắc nhở | Thúc đẩy hành động (Conversion) đạt mốc 100 đăng ký |

---

## 6. Sản phẩm nội dung chi tiết (Output 4)

### A. Hai bài đăng Facebook

#### Bài đăng 1: Giới thiệu khóa học & Đánh trúng tâm lý tân sinh viên (Ngày 2)
* **Tiêu đề:**  TÂN SINH VIÊN ƠI, ĐỪNG ĐỂ MÔN LẬP TRÌNH LÀM "RƠI" GPA NGAY TỪ NĂM NHẤT!
* **Nội dung:**
  Mới bước chân vào giảng đường đại học, hẳn nhiều bạn 18–20 tuổi vẫn đang "choáng ngợp" trước hàng tá kiến thức mới, đặc biệt là nỗi lo mang tên **Lập trình**. Chưa từng viết một dòng code nào, không biết bắt đầu từ đâu, sợ học không theo kịp bạn bè?
  
  Đừng lo lắng! Khóa học **Python Cơ Bản Dành Cho Người Mới Bắt Đầu** sẽ giúp bạn xóa tan nỗi sợ đó:
  ✅ **8 tuần làm chủ Python từ con số 0:** Lộ trình tinh gọn, đi từ tư duy cốt lõi đến thực hành dự án thực tế.
  ✅ **Thiết kế chuẩn cho người mới:** Giảng dạy dễ hiểu, cầm tay chỉ việc, không cần kiến thức nền tảng trước đó.
  ✅ **Bứt phá điểm số & Kỹ năng:** Tự tin chinh phục các môn đại cương trên trường và tạo nền tảng vững chắc cho các kỳ thực tập tương lai.

   Chỉ còn **30 suất ưu đãi học phí** dành riêng cho sinh viên năm nhất đăng ký trong tuần này!
  👉 **Comment "TƯ VẤN"** hoặc **Inbox trực tiếp cho Fanpage** ngay hôm nay để nhận lộ trình học chi tiết 8 tuần miễn phí nhé!
  `#PythonCoBan #TanSinhVien #LapTrinhChoNguoiMoi #HocPython8Tuan`

---

#### Bài đăng 2: Bài viết phân tích lộ trình & Thúc đẩy chuyển đổi (Ngày 4)
* **Tiêu đề:**  TỪ "MÙ CÔNG NGHỆ" ĐẾN TỰ TAY VIẾT ỨNG DỤNG CHỈ SAU 8 TUẦN – BẠN CÓ TIN KHÔNG?
* **Nội dung:**
  Nhiều bạn sinh viên năm nhất thường nghĩ: *"Chờ lên năm 2, năm 3 rồi học lập trình cũng chưa muộn"*. Nhưng thực tế, những người bắt đầu sớm từ năm nhất luôn là những người nắm giữ cơ hội học bổng và thực tập tốt nhất!

  Cùng khám phá hành trình **8 tuần lột xác** cùng khóa học **Python Cơ Bản** tại trung tâm:
  🔹 **Tuần 1 – 2:** Làm quen tư duy lập trình, cài đặt môi trường và nắm vững cú pháp Python cơ bản.
  🔹 **Tuần 3 – 4:** Thành thạo cấu trúc dữ liệu, vòng lặp và cách giải quyết bài toán logic.
  🔹 **Tuần 5 – 6:** Làm việc với thư viện phổ biến và xử lý dữ liệu thực tế.
  🔹 **Tuần 7 – 8:** Hoàn thiện đồ án mini cá nhân và nhận chứng nhận hoàn thành khóa học.

  Không lý thuyết suông, không nhồi nhét! Đội ngũ giảng viên luôn theo sát và giải đáp thắc mắc 1-1 cho từng học viên.
   **Để lại thông tin tại Form đăng ký hoặc nhắn tin cho Page** để được đội ngũ tư vấn viên hỗ trợ xếp lớp phù hợp nhất với lịch học trên trường của bạn!
  `#KhoaHocPython #SinhVienNamNhat #CodeTuConSo0 #TuVanKhoaHoc`

---

### B. Hai kịch bản video TikTok (30–45 giây)

#### Kịch bản 1: Nỗi sợ "Code đại cương" của tân sinh viên (Thời lượng: 35 giây)
* **Mục tiêu:** Thu hút sự chú ý (Hook), tạo sự đồng cảm và giới thiệu giải pháp.

| Thời gian | Hình ảnh / Cảnh quay | Lời thoại (Voice-over / Nhân vật) | Text trên màn hình & Âm thanh |
| :--- | :--- | :--- | :--- |
| **00:00 - 00:05** | Sinh viên năm 1 ôm đầu gục xuống bàn trước màn hình laptop toàn chữ đỏ báo lỗi. | "Cứu tôi với! Mới năm nhất đại học mà nhìn màn hình code như nhìn bức vách thế này thì qua môn kiểu gì?" | **Text:** Khi tân sinh viên lần đầu học lập trình 😭<br>**Âm thanh:** Nhạc nền kịch tính, tiếng báo lỗi *Bíp!* |
