---
layout: article
title: "Tinh beta bằng Excel"
date: 2016-04-28 12:00:00
categories: Misc
featured: true
featured_image: "/images/Excel/excel1p.png"
tag: Amibroker
author: Thanh Nguyen M
---


Cách tiếp cận truyền thống để tính toán hệ số Beta là dựa vào phương trình hồi quy cho lợi nhuận của chỉ số thị trường và lợi nhuận của cổ phiếu. Thông thường tỉ suất lợi nhuận được tính toán dựa trên số liệu về giá đã được điều chỉnh cho các khoản như chia tách hoặc chia cổ tức bằng cổ phiếu.

Tỉ suất lợi nhuận nên được tính toán theo tháng hoặc theo tuần (theo Investment Valuation - Damodaran). Hệ số Beta về mặt lý thuyết được tính như sau:

$$ \frac{covariance(r_s, r_m)}{variance(r_m)} $$

Covariance là hiệp phương sai giữa tỉ suất lợi nhuận của cổ phiếu và tỉ suất lợi nhuận của thị trường cần tính toán.
Variance trong công thức là phương sai của tỉ suất lợi nhuận của chỉ số thị trường.
Hệ số beta được giải thích như sau:

- Giả sử Beta của 1 cổ phiếu đo được là 1.3, theo lý thuyết, khi thị trường đạt tỉ suất lợi nhuận là 1% thì tỉ suất lợi nhuận của cổ phiếu có thể đạt được là 1.3 * 1% = 1.3%. Kết quả trên chỉ đúng khi lãi suất phi rủi ro gần hoặc tương đương 0%.

- Nếu chúng ta ước lượng thị trường có tỉ lệ lãi suất phi rủi ro là 7%, tỉ suất lợi nhuận kì vọng của thị trường chung là 10%. Vậy 1 cổ phiếu có beta bằng 1.3 sẽ có tỉ suất lợi nhuận kì vọng tương đương:

$$ E(r_s) = r_f + \beta \times (E(r_m) - r_f) = 7\% + 1.3\% \times (10\% - 7\%) = 10.9 \% $$

Lúc này tỉ suất lợi nhuận kì vọng của cổ phiếu được tính toán dựa trên hệ số beta là 10.9%, cao hơn 0.9% so với tỉ suất lợi nhuận kì vọng của thị trường chung.

- Beta cũng có thể âm hoặc dương. Beta dương tức là khi thị trường có tỉ suất lợi nhuận dương, cổ phiếu cho tỉ suất lợi nhuận dương, tức là vận động cùng với thị trường. Khi Beta âm, thị trường có thể có tỉ suất loại nhuận dương, nhưng lúc này tỉ suất lợi nhuận ở cổ phiếu có thể âm, vận động ngược chiều với thị trường.

- Khi chỉ số Beta bằng 0, tức là cổ phiếu không có mối tương quan với thị trường.

Đa số các trang web tài chính ở Việt Nam như CafeF hay Vietstock đều cung cấp hệ số Beta. Tuy nhiên với những ai muốn tính toán trực tiếp hệ số Beta, điều chỉnh các thông số có thể tính toán rất nhanh qua Excel bằng hàm Slope.
Đầu tiên bạn truy cập vào [cophieu68](http://cophieu68.com), download dữ liệu excel về giá đã được điều chỉnh hằng ngày.


![c1](/images/Excel/excel1.png)

Sau đó lấy dữ liệu từ 2 cột <DTYYYMMDD> và <Close> để tính toán Beta.

![c2](/images/Excel/excel2.png)

Vấn đề ở đây là dữ liệu của cophieu68 được input cho Amibroker và Metastock Format nên ngày tháng sẽ viết liền như hình ở trên. Vì thế chúng ta chuyển đổi dữ liệu sang dạng chuẩn qua excel thông qua hàm Date như sau:

![c3](/images/Excel/excel3.png)

Dữ liệu trong Cophieu68 được sắp xếp theo thứ tự dữ liệu mới nhất được cập nhật ở trên, vì thế khi lọc xong data, chúng ta dùng bộ lọc Filter chỉnh từ oldest to newest để thuận tiện cho việc tính toán tỉ suất lợi nhuận. Sau đó copy Date, Close của VNindex và mã cổ phiếu cần tính toán ra 1 sheet riêng như hình bên dưới:

![c4](/images/Excel/excel4.png)

Tỉ suất lợi nhuận theo tháng sẽ được tính theo số liệu Close và ngày cuối cùng của tháng như công thức bên dưới:

![c5](/images/Excel/excel5.png)

Thông thường, chúng ta nên tính toán tỉ suất lợi nhuận tối thiểu trong 2 năm (24) tháng do yêu cầu của hồi quy thường phải có tối thiểu 25 quan sát. Sau khi đã có đủ số lượng quan sát của tí suất lợi nhuận, chúng ta dùng hàm Slope để tính toán ra Beta như hình dưới:

![c6](/images/Excel/excel6.png)

Do mã CAV chỉ có số liệu từ năm 2015 nên ở bài viết tôi chỉ tính toán trên 12 quan sát, số liệu sẽ không thật sự chính xác. Theo Damodaran, việc dùng tỉ suất lợi nhuận theo tuần hay theo tháng ảnh hưởng tương đối lớn đến việc tính toán beta. Ngoài ra có thể chọn chuỗi thời gian trong 2 năm tới 3 năm hoặc hơn. Tuy nhiên, chuỗi thời gian càng dài, bản chất rủi ro và hoạt động của doanh nghiệp thay đổi nên hệ số beta có khả năng không phản ánh đúng bản chất của cổ phiếu ở thời điểm tính toán.

Hàm Slope trong Beta cũng không cho xem xét hệ số R-squared (coefficient of determination) nên chúng ta khó có thể biết độ chính xác của hệ số Beta trong thực tế. Bài viết sau về OLS sẽ có cái nhìn chi tiết hơn về phương trình hồi quy dạng cơ bản trong excel.

Ngoài ra việc chọn chỉ số thị trường để tính toán beta cũng quan trọng. Giả sử cổ phiếu giao dịch trên sàn Upcom, bạn nên sử dụng chỉ số Upcom để tính toán thay vì VN-index hay HNX-index.
