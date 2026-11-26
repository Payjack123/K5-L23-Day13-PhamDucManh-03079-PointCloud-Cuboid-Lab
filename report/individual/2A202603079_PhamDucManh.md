# Báo cáo Day 13 — Phạm Đức Mạnh, 2A202603079

Đã gán nhãn 10 frame, xuất Bảng A và phiếu tự kiểm, chụp đủ 11 ảnh minh chứng. Số liệu trong báo cáo lấy từ hai CSV hiện tại; các việc còn cần hoàn thiện được liệt kê ở mục 6.

Ảnh minh chứng được nộp riêng trong `K5-L23-DAY13-2A202603079-images.zip`. Báo cáo ghi tên file ảnh để đối chiếu với ZIP.

## 1. Kết luận trước
MSSV: **2A202603079 — Phạm Đức Mạnh**. Task cá nhân: **D13-2A202603079**, job 20. Môi trường: Windows, Chrome, CVAT 2.81.0, cvat-sdk 2.83.0.

| Hạng mục | Kết quả đã thực hiện |
|---|---|
| Frame đã gán nhãn | 10/10 |
| Cuboid | 61 Shape; không còn Track |
| Phạm vi | Không có hộp có tâm xa hơn 50 m |
| Tự kiểm | Đã xuất phiếu; 5/61 hộp có cảnh báo |
| Ảnh minh chứng | 11/11 ảnh, đã đóng gói ZIP |
| Tệp số liệu | Bảng A và phiếu tự kiểm đã được xuất bằng `sync` |

Các frame và số hộp: s01f12: 7; s01f30: 5; s02f27: 5; s02f53: 5; s03f31: 3; s03f48: 6; s04f19: 14; s04f52: 5; s05f14: 6; s05f39: 5. Tổng cộng **61 cuboid Shape**; 5/61 hộp có cảnh báo tự kiểm. Frame ít nhất: s03f31 (3 hộp). Theo ghi nhận của người học, vùng hiển thị tối làm các cụm điểm và ranh giới vật khó phân biệt. Vì vậy, ở s01f12 chỉ gán 7 cuboid cho các vật xác định được; ở s03f31 chỉ xác định rõ 3 xe để gán nhãn, không suy đoán thêm vật cho đủ số lượng.

Các số đo mô tả nhãn đang lưu, không phải kết quả chấm với nhãn chuẩn. Những frame chưa đạt mốc số lượng và phần tự kiểm còn lại được ghi rõ ở cuối báo cáo.

Thao tác: kéo chuột trái xoay cảnh, chuột phải dời, con lăn phóng; xoay khung lớn để nhìn từ trên xuống. Vẽ bằng Shape, đặt bằng nháy đúp, chỉnh ở Top/Side/Front và bật Cuboid orientation. Muốn đối chiếu hộp trên camera thì dùng preview; Save rồi sync sau mỗi lần sửa.

## 2. Đọc frame
Hai frame đọc kỹ: s01f12, s01f30. Ảnh: t1-s01f12-3d.png, t1-s01f12-top.png, t1-s01f30-3d.png, t1-s01f30-top.png. Hai ảnh Top đã căn trước lên trên và có chú thích trục.

| Frame | Hướng trong ảnh Top | Độ cao đường ước lượng ở vùng gần | Vật đã gán xa nhất | Loại vật theo nhãn đã lưu | Phía sau / hai bên theo tâm hộp |
|---|---|---|---|---|---|
| s01f12 | Trước ↑ (−y), +x ←, +y ↓ | z ≈ −1,67 m, thấp hơn LiDAR khoảng 1,67 m | 32,93 m | Bus, Car, Pedestrian | 3 hộp có y > 0; 5 hộp có abs(x) > 3 m |
| s01f30 | Trước ↑ (−y), +x ←, +y ↓ | z ≈ −1,61 m, thấp hơn LiDAR khoảng 1,61 m | 30,13 m | Car, Truck | 4 hộp có y > 0; 4 hộp có abs(x) > 3 m |

Camera cung cấp màu bề mặt, chi tiết/ký hiệu và dấu hiệu nhận biết đầu–đuôi của vật. LiDAR cung cấp vị trí/khoảng cách theo mét, hình học/kích thước 3D và độ cao/phân bố điểm so với mặt đường. Vì vậy ảnh camera dùng để đối chiếu nhận dạng và hướng; Top/Side/Front dùng để kiểm hình học hộp. Phần mô tả các ví dụ quan sát cụ thể và độ dốc của hai frame được ghi trong danh sách cần hoàn thiện ở mục 6.

Tám frame lướt, dùng cùng quy ước BEV trước ở trên của báo cáo; hướng trên màn hình CVAT có thể đổi khi xoay cảnh:

| Frame | Phía trước theo quy ước của báo cáo | Tóm tắt nhãn đã lưu |
|---|---|---|
| s02f27 | −y, phía trên ảnh BEV đã căn | 5 hộp đã lưu |
| s02f53 | −y, phía trên ảnh BEV đã căn | 5 hộp đã lưu |
| s03f31 | Trước là −y; khi căn BEV như hai ảnh mẫu thì ở trên | Chỉ xác định rõ 3 xe; phần hiển thị còn lại tối, khó phân biệt điểm và vật để gán nhãn thêm |
| s03f48 | −y, phía trên ảnh BEV đã căn | 6 hộp đã lưu |
| s04f19 | −y, phía trên ảnh BEV đã căn | 14 hộp đã lưu |
| s04f52 | −y, phía trên ảnh BEV đã căn | 5 hộp đã lưu |
| s05f14 | −y, phía trên ảnh BEV đã căn | 6 hộp đã lưu |
| s05f39 | −y, phía trên ảnh BEV đã căn | 5 hộp đã lưu |

## 3. Ba cuboid mẫu
Ảnh: t2-a-car.png, t2-b-bus-truck.png, t2-c-ped-cyclist.png. Ảnh chụp từ giao diện CVAT, có khung 3D và các view Top/Side/Front.

| Vật | Frame, idx | Class đang lưu | Yaw của hộp | z đáy | Ảnh minh chứng | Dài × rộng × cao |
|---|---|---|---|---|---|---|
| (a) Xe con | s01f12, 1 | Car | 268,00° | −1,768 m | t2-a-car.png | 4,37 × 1,70 × 1,52 m |
| (b) Xe buýt/tải | s01f12, 3 | Bus | 283,70° | −1,903 m | t2-b-bus-truck.png | 12,65 × 2,75 × 3,44 m |
| (c) Người/xe hai bánh | s01f12, 6 | Pedestrian | 0,00° | −1,474 m | t2-c-ped-cyclist.png | 0,58 × 0,66 × 1,76 m |

Hộp Car mẫu có yaw gần 270°, tương ứng hướng −y của hệ VF. Ba z đáy lệch mốc đường −1,7 m lần lượt −0,068 m, −0,203 m và +0,226 m. Đây là đối chiếu số học; kết luận đầu–đuôi và độ khớp thực tế thuộc bước rà soát cuối.

Hiệu chuẩn: chưa tham gia nên không có kết quả so lệch để báo cáo. Khó khăn quan sát được ghi nhận ở s01f12 và s03f31: vùng hiển thị tối khiến người học khó xác định cụm điểm, ranh giới vật và vị trí đặt hộp. Chỉ gán nhãn các vật nhận ra đủ rõ; các vùng chưa đủ cơ sở được ghi nhận là LOW_VISIBILITY, không suy đoán thêm vật.

## 4. Bốn hiện tượng chất lượng
Hai ảnh dùng task chung là s02f00 và s02f35; các ảnh còn lại dùng nhãn cá nhân. Nguyên nhân đều là giả thuyết, không phải kết luận chắc chắn.

| Hiện tượng | Frame / ảnh / nguồn | Nguyên nhân (giả thuyết) | Bằng chứng / số đo | Hệ quả gán nhãn |
|---|---|---|---|---|
| Bóng che | s02f00; t4-1-bong-che.png; task chung D13-HC485087 | Giả thuyết: vật cản gần che tia LiDAR tới vùng phía sau | Vùng trống điểm sau vật cản, theo frame gợi ý của đề | Vùng chưa quan sát được không đồng nghĩa không có vật; chỉ suy luận khi đủ cơ sở, bật occluded cho vật bị che |
| Thưa ở xa | s03f31, #3; t4-2-thua-o-xa.png; task cá nhân | Giả thuyết: độ phân giải góc làm mật độ điểm giảm theo khoảng cách | Hộp Car ở 34.12 m có 95 điểm trong hộp | Áp dụng quy tắc 15–20% hoặc có bằng chứng camera đủ rõ; thiếu cơ sở thì ghi LOW_VISIBILITY |
| Ít điểm bất thường / phản xạ thấp (giả thuyết) | s05f14, #3; t4-3-phan-xa-thap.png; task cá nhân | Phản xạ thấp là một khả năng; che khuất, góc tới hoặc hộp chưa khớp cũng có thể gây ít điểm | Hộp ở 10.08 m có 867 điểm; hộp Car đối chiếu s05f14 #5 ở 6.14 m có 4111 điểm | Chỉ ghi là giả thuyết, cần đối chiếu camera và độ khớp hộp trước khi kết luận nguyên nhân |
| Điểm lạ | s02f35; t4-4-diem-la.png; task chung D13-HC485087 | Giả thuyết: phép đo/phản xạ bất thường; chưa xác định nguyên nhân | Cụm điểm thấp dưới mặt đường; trung vị z trong vùng chọn khoảng -13.27 m | Không gán cụm bất thường thành một vật thật |

## 5. Số từ cuboid của tôi
Nguồn: submission/D13-2A202603079-bangA.csv và submission/D13-2A202603079-tukiem.csv. Đơn vị chiều dài là m, yaw là °. z đáy = z − h/2; dist_m = √(x²+y²); r = √(x²+y²+z²). Mốc z đường −1,7 m chỉ là tham khảo; quyết định sửa cần nhìn mặt đường tại vật.

| Cuboid | z | h | z đáy | dist_m | r | yaw_deg | Đối chiếu đáy |
|---|---|---|---|---|---|---|---|
| s01f12 / #1 / Car | -1.008 | 1.520 | -1.768 | 6.15 | 6.23 | 268.00 | Thấp hơn mốc −1,7 m: 0,068 m |
| s01f12 / #3 / Bus | -0.182 | 3.441 | -1.903 | 32.93 | 32.93 | 283.70 | Thấp hơn mốc −1,7 m: 0,203 m |
| s01f12 / #6 / Pedestrian | -0.595 | 1.758 | -1.474 | 7.53 | 7.55 | 0.00 | Cao hơn mốc −1,7 m: 0,226 m |

Gần nhất trong Bảng A: s05f14 / #2 / Car, dist_m=6.05 m, r=6.15 m. Xa nhất: s03f31 / #3 / Car, dist_m=34.12 m, r=34.13 m.

So kích thước với bảng 4.3: Car mẫu 4,37 × 1,70 × 1,52 m nằm trong khoảng sedan tham chiếu 3,8–5,0 / 1,70–1,90 / 1,40–1,60 m theo số hiển thị. Pedestrian mẫu 0,58 × 0,66 × 1,76 m nằm trong khoảng người lớn 0,4–0,9 / 0,5–0,9 / 1,50–1,95 m. Bus mẫu dài 12,65 m và rộng 2,75 m, mỗi chiều vượt trần xe buýt thường tương ứng 0,15 m; chiều cao 3,44 m nằm trong khoảng 3,00–3,50 m. Khoảng tham chiếu hỗ trợ phát hiện điểm cần xem lại, không thay thế bằng chứng từ vật và point cloud.

Mẫu yaw cùng hướng −y: s04f19 / #1 / Car có yaw 270,10°, lệch mốc 270° khoảng 0,10°. Mẫu yaw hướng +y: s02f53 / #5 / Car có yaw 89,90°, lệch mốc 90° khoảng 0,10°. Các số này mô tả hướng hộp đã lưu; bước đối chiếu đầu–đuôi thật được liệt kê ở mục 6.

| Cuboid | dist_m (m) | points_in |
|---|---|---|
| s05f14 / #2 / Car | 6.05 | 1608 |
| s04f19 / #1 / Car | 12.95 | 1062 |
| s04f19 / #12 / Car | 19.27 | 793 |
| s03f31 / #3 / Car | 34.12 | 95 |

Hai mẫu đầu/cuối xa nhau theo khoảng cách khoảng 5.64 lần; số điểm lần lượt là 1608 và 95. Mật độ còn phụ thuộc loại/kích thước vật, góc quan sát, che khuất và độ khớp cuboid; bốn hộp riêng lẻ không chứng minh một quy luật suy giảm duy nhất. Slide cho trung vị Car khoảng 1968 điểm ở 0–10 m, 718 ở 10–20 m, 214 ở 20–30 m, 72 ở 30–40 m và 19 ở 60–80 m; các giá trị này dùng tham khảo, không phải ngưỡng ép từng hộp phải đạt.

Đã sửa kiểu đối tượng: chuyển 4 Track thành 6 Shape tại các keyframe đã vẽ, giữ nguyên vị trí, kích thước và hướng. Bảng A và preview đã được xuất lại sau chuyển đổi. Phiếu tự kiểm hiện còn năm cảnh báo để rà soát:

- s01f12 / #6 / Pedestrian: 600 điểm sát ngay ngoài mép (quá chật, hay vật bên cạnh?)
- s01f12 / #7 / Car: đáy thấp hơn mặt đường 0.68 m (chìm?)
- s01f30 / #5 / Truck: height=1.40 ngoài khoảng 1.7–4.5 của Truck
- s05f39 / #2 / Car: đáy cao hơn mặt đường 0.47 m (lơ lửng?)
- s05f39 / #3 / Car: width=1.30 ngoài khoảng 1.4–2.3 của Car

Giải trình phần tự sửa hình học: người học cho biết vùng hiển thị tối, khó xác định các điểm thuộc vật và ranh giới hộp nên chưa đủ chắc chắn để điều chỉnh thêm. Hiện chưa thực hiện hai chỉnh sửa hình học sau tự kiểm; phần đã hoàn thành là chuyển kiểu Track sang Shape như mô tả trên.

## 6. Ý nghĩa của nhãn, cách dùng AI và điều còn chưa chắc
Model học nhãn 3D cần vị trí/kích thước trong hệ tọa độ vật lý theo mét; pixel thay đổi theo camera và khoảng cách nên không thay thế được kích thước thật. Vật thưa điểm cần quy tắc riêng để tránh tạo nhãn thiếu cơ sở, đồng thời giữ cách suy luận nhất quán cho các vật bị che hoặc ở xa.

- **Công cụ AI:** Codex/ChatGPT.
- **Câu hỏi chính:** cài Docker/CVAT/Python, đếm Shape/Track, cách chụp 3D/Top và chuẩn bị các tệp nộp.
- **Cách dùng kết quả:** hỗ trợ thao tác kỹ thuật, chuyển kiểu hộp giữ nguyên hình học, chụp ảnh CVAT và tổng hợp báo cáo từ CSV. Phần đánh giá cuối về độ khớp nhãn thuộc người học.

**Giới hạn quan sát và phần tự kiểm còn lại:**

- Tự sửa hình học: chưa thực hiện hai chỉnh sửa sau tự kiểm. Lý do người học ghi nhận là vùng hiển thị tối, khó phân biệt điểm thuộc vật và vị trí cần chỉnh. Năm cảnh báo ở mục 5 vẫn được giữ để tiếp tục đối chiếu khi có đủ cơ sở quan sát.
- Số lượng: s01f12 có 7/8 hộp và s03f31 có 3/5 hộp theo mốc yêu cầu. Người học chỉ xác định chắc chắn được các vật đã gán nhãn; những vùng hiển thị tối còn lại không đủ cơ sở để nhận ra thêm vật. Đây là lý do thiếu số lượng, chưa phải xác nhận hai frame đã đạt mốc.
- Đối chiếu class, đầu–đuôi và độ khớp sáu mặt của ba hộp mẫu bằng camera và Top/Side/Front.
- Bổ sung nhận xét về độ dốc, cụm chưa đọc được và ví dụ camera cụ thể ở hai frame đầu; đây là phần quan sát thực tế chưa có ghi chép từ người học.

Nguyên nhân của hiện tượng ít điểm vẫn được ghi là giả thuyết. Chưa ghi nhận lỗi phát hiện sau hạn.
