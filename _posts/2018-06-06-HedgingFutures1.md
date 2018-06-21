---
layout: article
title: "Hedging bằng hợp đồng tương lai VN30 (phần 1)"
date: 2018-06-06 18:08:08
categories: MF
featured: true
featured_image: "/images/MF/safe.jpeg"
tag: MF
author: thanh Nguyen
---
Mục đích ban đầu của công cụ phái sinh là giúp nhà đầu tư giảm thiểu được rủi ro khi thị trường vận động không đúng theo kì vọng. Năm 2017, thị trường Việt Nam chứng kiến sự ra đời của công cụ phái sinh đầu tiên - hợp đồng tương lai. Series bài viết này phân tích ngắn gọn đặc điểm chung của hợp đồng tương lai, cũng như cách để hedge 1 danh mục bao gồm 1 cổ phiếu hoặc 1 danh mục đầu tư cổ phiếu, sử dụng hợp đồng tương lai với tài sản cơ sở là chỉ số VN30.

# 1. Khái niệm Hedging.
- Đầu tiên chúng ta đề cập tới khái niệm hedging (tiếng việt dịch ra là nghiệp vụ đảm bảo). Lấy ví dụ đơn giản thế này, tôi là chủ quán phở bò, **hôm qua tôi nghe phóng viên Sỹ Khỏe trên VTV1 chuyên mục "bạn nhà nông" nói, số lượng bò tiêu thụ tăng lên đột biến trong khi nguồn cung đang bị thiếu hụt ở nửa cuối năm 2018. Vậy chắc chắn giá thịt bò sẽ tăng lên tương ứng (giả sử có duy nhất 1 loại thịt bò trên thị trường và có hạn mức nhập khẩu bò từ nước ngoài).**


![Beef](/images/MF/pic1.jpg){: .center-image}

- Chiến lược kinh doanh của cửa hàng phở của tôi tập trung vào giá, đó là đưa ra 1 mức giá hợp lý, phù hợp với đa số người dân lao động trong khu vực. **Cấu trúc chi phí có đến 50% tới từ thịt bò. Vậy giả sử 1 bát phở có giá 30,000 VND, vậy cứ mỗi kg thịt bò tăng lên từ 200,000 VND lên 280,000 VND tức là 40%, tôi phải tăng chi phí của 1 bát phở lên 1 lượng tương đương 6,000 VND. Giả sử tôi muốn giữ nguyên biên lợi nhuận của mình, vậy 6,000 VND tăng lên kia sẽ được cộng toàn bộ vào giá mà khách hàng phải trả cho 1 bát phở. Lúc này giá sẽ tương đương 36,000 VND.** Thêm nữa, vì thịt bò phải nhập tươi 8 tiếng trước khi chế biến và sẵn sàng cho giờ mở cửa vào lúc 6h sáng, tức là tôi không thể mua trước thịt bò vào ngăn đá như 1 dạng hàng tồn kho. 1 điều quan trọng hơn nữa là tôi sẽ không biết giá thịt bò liệu sẽ tăng tới mức bao nhiêu, tốc độ tăng sẽ nhanh hay chậm, **liệu 1 tháng nữa thịt bò có tăng lên mức 350,000 VND hay chỉ tăng lên 240,000 VND 1 kg?**

![Beef](/images/MF/pic2.png){: .center-image}

- Điều quan trọng nhất ở đây là tôi không hề biết giá mà mình sẽ phải trả cho người buôn thịt bò vào mỗi ngày trước khi mở cửa hàng. Hơn nữa, viêc điều chỉnh giá bán phở cho khách hàng rất cứng nhắc, **việc tăng giá hay giảm giá không hợp lý sẽ khiến khách hàng bỏ đi ngay lập tức** bởi chiến lược kinh doanh của cửa hàng là tập trung vào phân khúc khách hàng bình dân.

- Vậy làm thế nào để hạn chế việc biến động của giá đầu vào? Đầu tiên tôi gọi cho nhà phân phối thịt bò, thỏa thuận với họ, tôi vẫn sẽ tiếp tục mua thịt bò, nhưng lúc này giá thịt bò sẽ không được thương lượng vào mỗi buổi sáng nữa mà sẽ được thỏa thuận trong chu kì 1 tháng. Vào mỗi ngày đầu tiên của tháng, người bán thịt bò sẽ đưa ra mức giá mà tôi phải trả trong toàn bộ tháng tiếp theo. **Giả sử lúc này là đầu tháng 10, tôi sẽ thỏa thuận giá cho toàn bộ tháng 11, bắt đầu từ ngày mùng 1/11 tới ngày 30/11. Vậy điều gì tạo nên sự khác biệt? Lúc này, tôi biết chắc chắn mức giá mình phải trả mỗi buổi sáng là bao nhiêu, và có 1 kế hoạch cụ thể cho tháng đó.**

- **Vậy Hedging ở đây được hiểu là gì? Chúng ta có thể hiểu đó là thỏa thuận 1 mức giá cố định cho 1 loại hàng hóa nào đó, được giao dịch trong tương lai, ở thời điểm hiện tại.** Dù mức giá ngoài thị trường có biến động như thế nào thì tôi vẫn có thể mua 1 mặt hàng với giá được xác định trước. Vậy câu hỏi đặt lúc này là việc thỏa thuận với nhà phân phối thịt bò kia sẽ đem đến lợi ích và những bất lợi cụ thể gì?

# 2. Hedging, lợi ích và bất lợi
- **Kịch bản thứ 1, trong suốt tháng 11, giá thịt bò trong tháng tăng lên rất nhanh, dao động quanh ngưỡng 400,000 VND 1 kg. Giá mà tôi thỏa thuận với nhà buôn thịt bò chỉ là 280,000 VND 1kg. Vậy đương nhiên chỉ phí đầu vào của 1 bát phở của tôi đương nhiên sẽ thấp hơn đối thủ cạnh tranh.** Nếu điều chỉnh giá bán hợp lý thì biên lợi nhuận vẫn có thể được duy trì, khách hàng sẽ vẫn trung thành với cửa hàng. Vậy việc hedging lúc này đương nhiên đem lại lợi ích.

- **Kịch bản thứ 2, trong suốt tháng 11, giá thịt bò bỗng nhiên suy giảm mạnh mẽ, chỉ ở mức 150,000 VND 1 kg. Lúc này, thay vì mua của nhà buôn thịt bò kia, giá tôi có thể mua ngoài thị trường thấp hơn nhiều. Lúc này chi phí đầu vào cao hơn hẳn thị trường, tuy nhiên giá bán cho khách hàng không thể tăng tương ứng**. Kết quả là việc hedging làm cho biên lợi nhuận suy giảm rõ rệt và ảnh hưởng đến hoạt động kinh doanh.

# 3. Khi nào thì sử dụng hedging bằng hợp đồng tương lai
- Vậy lúc nào thì nên thực hiện hedging? Tôi chỉ nên thực hiện hedging khi tôi chắc chắn biết rằng giá thịt bò sẽ tăng mạnh trong thời gian tới.

- Thứ nhất, khi giá thịt bò tăng, mọi cửa hàng phở đều có chi phí đầu vào tăng, vậy giá bán cho người tiêu dùng chắc chắn tăng lên tương ứng. Tuy nhiên mức giá mà cửa hàng đưa ra sẽ khác nhau do cơ cấu chi phí khác nhau và chiến lược kinh doanh khác nhau. Vậy có thực sự cần thiết thực hiện hedging nếu ảnh hưởng của việc tăng giá thịt bò đến cấu trúc chi phí và giá bán là không đáng kể?

- Thứ hai, hedging không đồng nghĩ với việc chắc chắn có lợi nhuận. Hedging nên được hiểu như việc cố định giá để mua 1 mặt hàng trong tương lai. Nếu giá tăng nhiều hơn mức giá thỏa thuận trước, người bán thịt bò hưởng lợi. Nếu giá giảm nhiều hơn mức giá thỏa thuận trước, người bán thịt bò thua thiệt.

![Beef](/images/MF/pic3.jpg){: .center-image}

# 4. Long hedge và Short hedge với hợp đồng tương lai

## Long hedge

- Ví dụ đề cập ở trên được phân loại là long hedge. Long hedge được sử dụng khi chủ thể cần phải mua phải mua một loại tài sản hay hàng hóa trong tương lai. Ở đây là chủ cửa hàng phở muốn mua thịt bò trong tương lai. Tương tự, 1 công ty sản xuất ô tô sẽ cần mua sắt thép, da, bông, cao su ... làm nguyên liệu, họ sẽ cần long hedge cho các nguyên liệu cơ bản đầu vào. Hoặc các chuỗi bán lẻ cafe như Starbucks sẽ cần mua cafe, đường, các nguyên liệu và hương liệu phục vụ cho sản xuất đồ uống. Tương tự họ cũng cần biết chính xác giá mà họ sẽ phải trả cho các chi phí đầu vào khi lên kế hoạch kinh doanh và thiết lập hệ thống quản lý rủi ro khi cần thiết.

## Short hedge
- Short hedge được sử dụng khi chủ thể đã sở hữu một tài sản và muốn bán nó trong tương lai. Chúng ta thường thấy người nông dân khai thác nông sản như vải, dưa hấu, nhãn ... sau khi thu hoạch sẽ muốn biết rõ mức giá mà họ có thể bán ra thị trường. Việc biết trước được mức giá họ có thể bán sẽ giúp họ tính toán được mức lợi nhuận và kế hoạch cho mùa tiếp theo. Ngay cả trong trường hợp thị trường dư thừa nguồn cung, họ cũng cần xác định mức giá họ có thể bán để bù đắp cho chi phí lỗ họ phải hứng chịu.
