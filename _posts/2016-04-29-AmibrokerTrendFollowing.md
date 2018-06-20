---
layout: article
title: "Amibroker: Trend Following System trong Amibroker (1)"
date: 2016-04-29 12:00:00
categories: Misc
featured: true
featured_image: "/images/Amibroker/amp1.jpg"
tag: Amibroker
author: Thanh Nguyen M
---

*HỆ THỐNG GIAO DỊCH DỰA THEO XU HƯỚNG (TREND FOLLOWING SYSTEM) ĐƯỢC DỰA TRÊN GIẢ THIẾT RẰNG GIÁ THƯỜNG VẬN ĐỘNG THEO 1 XU HƯỚNG NHẤT ĐỊNH ĐỦ LÂU ĐỂ TRADER CÓ THỂ NHẬN RA KHI NÀO XU HƯỚNG BẮT ĐẦU, ĐẶT LỆNH VÀ KIẾM LỢI NHUẬN TỪ VIỆC ĐI THEO XU HƯỚNG. 2 CHIẾN LƯỢC CỔ ĐIỂN NỔI BẬT NHẤT TRONG HỆ THỐNG GIAO DỊCH THEO XU HƯỚNG LÀ MOVING AVERAGE CROSSOVER VÀ BREAKOUT.*

# 1. MOVING AVERAGE CROSSOVER SYSTEMS (MACS).
Hệ thống MACS đặt lệnh mua khi đường MA nhanh cắt đường MA chậm từ dưới lên trên. Giả sử khi đường MA(15) cắt lên trên đường MA(30), chúng ta có tín hiệu mua.

Dưới đây là ví dụ cổ điển được trình bày trong cuốn “Quantitative Trading Systems” của tác giả Howard B.Bandy. Đoạn code được viết bằng ngôn ngữ AFL của Amibroker và được backtest, optimize bằng bộ công cụ automatic analysis.

Tôi sẽ không đề cập cụ thể chức năng và cách sử dụng của các hàm (function) trong thư viện AFL vì lý do bản quyền từ Amibroker.

Bước đầu tiên, bạn vào Analysis -> Formula Editor rồi gõ đoạn code sau:

{% highlight C %}
Length1 = Param("Length1", 6, 1, 81, 2);
Length2 = Param("Length2", 35, 2, 200, 2);
MA1 = MA(C, Length1);
MA2 = MA(C, Length2);
Buy = Cross(MA1, MA2);
Sell = Cross(MA2, MA1);

e = Equity();
Maxe = LastValue(Highest(e));
Plot(Close, "Price", colorBlack, styleCandle);

Plot(MA1, "MA1", colorGreen, styleLine);
Plot(MA2, "MA2", colorBlue, styleLine);

shape = Buy*shapeUpArrow + Sell*shapeDownArrow;
PlotShapes(shape(IIf(Buy, colorGreen, colorRed), 0 , Iff(Buy, Low, High)));

{% endhighlight %}


Save đoạn code phía trên lại thành file MACrossSystem.afl vào trong 1 folder nào để sau đó có thể mở lại trong phần Automatic Analysis.

Ở 2 dòng đầu tiên, tác giả dùng hàm Param để tạo ra tham số cho 2 đường MA, cụ thể là độ nhanh hay chậm. Length1 dùng làm tham số cho đường MA nhanh, với minimum =6, maximum = 81 với bước nhảy (step) = 1 và Length2 dùng làm tham số cho đường MA chậm với minimum = 35, bước nhảy (step) = 2 và maxium =200.
2 dòng tiếp theo tạo ra 2 đường MA1 (Nhanh) và MA2 (chậm) dựa trên tham số của 2 dòng trước đó.
Ở dòng 5 và 6, tác giả tạo ra tín hiệu mua hay bán bằng hàm cross.
Các đoạn code tiếp theo dùng để hiển thị tín hiệu mua bán trên đồ thị giá khi thực hiện backtest.

Sau khi thực hiện xong đoạn code, tác giả tạo ra một indicator trong menu chart ở bên tay trái. Cụ thể trong hình bên dưới, tôi đặt tên chỉ báo là MACrossSystem.

![folder](/images/Amibroker/ami1.png){: .center-image}


Sau đó tôi load dữ liệu 1 mã cổ phiếu bất kì trong hệ thống để Backtest P&L. Mã ở đây tôi chọn là VIC (Vingroup). Tôi có đồ thị như phía dưới:

![chart1](/images/Amibroker/ami2.png){: .center-image}

Mũi tên xanh lá cây thể hiện tín hiệu mua và mũi tên đỏ thể hiện tín hiệu bán. bằng trực quan, có thể thấy nếu xu hướng giá rõ ràng, tín hiệu mua cho ra kết quả tốt, tuy nhiên tín hiệu bán với đường MA(35)  không hề tốt, luôn cho ra tín hiệu bán khi giá đã điều chỉnh tương đối sâu. Khi viết đoạn code trên, tác giả đã sử dụng hàm Param để điều chỉnh độ nhanh chậm của đường MA trực tiếp trên chart. Vì vậy, bạn chỉ cần right-click vào chart, chọn parameters, rồi điều chỉnh lại đường MA theo ý muốn. Giả sử tôi chọn MA nhanh là 6 và MA chậm là 12, tôi có kết quả như sau:

![chart2](/images/Amibroker/ami3.png){: .center-image}

Rõ ràng khi điều chỉnh độ lớn của MA chậm bằng 12, tín hiệu bán trở nên rõ nét hơn, bắt kịp với xu hướng điều chỉnh của đường cong giá. Tuy nhiên khi để MA12, tín hiệu nhiễu trở nên nhiều hơn, đặc biệt khi giá giao động trong biên độ nhỏ, xu hướng không rõ ràng, tín hiệu mua bán cho ra liên tục tăng phí giao dịch và turnover của tài khoản. Hơn thế nữa, lệnh mua và bán thường rơi vào cùng 1 vùng giá, không hề tạo ra lợi nhuận, đặc biệt là các tín hiệu mua bán đưa ra với chu kì nắm giữ ngắn hạn, thường khoảng 5-7 ngày

Để máy tính tự tối ưu hóa độ nhanh chậm của đường MA, ta có thể thay hàm Param thành hàm Optimize trong đoạn code viết ở trên.


{% highlight C %}
Length1 = Optimize("Length1", 6, 1, 81, 2);
Length2 = Optimize("Length2", 35, 2, 200, 2);
{% endhighlight %}

Save vào 1 file riêng trong folder, đặt tên là MACrossSystem2.afl. Sau đó mở Analysis trên Menu, chọn Automatic Analysis, bấm pick rồi chọn file MACrossSystem2.afl đã save trước đó trong mục code editor.

![chart3](/images/Amibroker/ami4.png){: .center-image}

Trong menu Automatic Analysis, trong mục Settings chọn Report rồi chọn summary để kết quả sau khi tối ưu hóa hoặc backtest cho ra 1 report tổng hợp

Sau đó ở menu automatic analysis, chọn current symbol (tức là VIC) đã chọn ở phần trên, chọn from 2014 tới ngày hiện tại, sau đó bấm Optimize để tối ưu hóa lựa chọn về độ nhanh chậm của đường MA. Amibroker sẽ mô phỏng từ 4100 mẫu test để cho ra kết quả với lợi nhuận cao nhất được test với tín hiệu Cross MA.

![chart3](/images/Amibroker/ami5.png){: .center-image}

Kết quả được thể hiện như hình bên dưới, lợi nhuận cao nhất là 70% khi kết hợp 2 đường MA nhanh là 65 và chậm là 24. Kì cục ở chỗ là tín hiệu cho ra khi thực hiện optimize lại cho thấy rằng đường MA chậm cắt lên trên đường MA nhanh thì tín hiệu mua cho ra lợi nhuận cao nhất. Cụ thể ở đây Length1 có giá trị 65 và Length2 có giá trị 24. Tôi tạo 1 đoạn code khác và apply vào chart VIC như sau:

{% highlight C %}
Length1 = 65;
Length2 = 24;
MA1 = MA(C, Length1);
MA2 = MA(C, Length2);
Buy = Cross(MA1, MA2);
Sell = Cross(MA2, MA1);

e = Equity();
Maxe = LastValue(Highest(e));
Plot(Close, "Price", colorBlack, styleCandle);

Plot(MA1, "MA1", colorGreen, styleLine);
Plot(MA2, "MA2", colorBlue, styleLine);

shape = Buy*shapeUpArrow + Sell*shapeDownArrow;
PlotShapes(shape(IIf(Buy, colorGreen, colorRed), 0 , Iff(Buy, Low, High)));

{% endhighlight %}

Hệ thống cho ra tín hiệu như sau:

![chart4](/images/Amibroker/ami6.png){: .center-image}

Cụ thể hơn, khi đường MA(65) cắt lên trên đường MA(24) tín hiệu cho lợi nhuận cao hơn nhiều, đối nghịch hoàn toàn với lý thuyết thường thấy. Khi áp dụng kết quả của quá trình tối ưu hóa, cổ phiếu cho ra lợi nhuận 77%. Giả sử tôi có 100 triệu vào ngày 1/1/2014, nếu theo hệ thống giao dịch này, tới 29/4/2016, tôi đã có 177 triệu VND trong tài khoản theo như kết quả backtest, đánh bại hoàn toàn hệ thống giao dịch sử dụng tín hiệu MA nhanh cắt lên trên MA chậm cổ điển. Tuy nhiên tối ưu hóa hệ thống giao dịch không đảm bảo trong tương lai bạn sẽ có lợi nhuận y hệt.

1 Điều cần lưu ý là nếu áp dụng MACS thì chu kì nắm giữ sẽ dài hơn, theo kết quả backtest, chu kì nắm giữ trung bình vào khoảng 44 ngày giao dịch, tức khoảng hơn 2 tháng. Các tay trader ngắn hạn theo xu hướng vài tuần tới 1 tháng hay những tay giao dịch T+3 sẽ không thích hệ thống này.

![chart5](/images/Amibroker/ami7.png){: .center-image}

Bạn có thể backtest và optimize nhiều mã dựa vào chiến lược giao dịch như trên. Có thể thấy từ ví dụ này, các chỉ báo phân tích kĩ thuật cần được điều chỉnh và tối ưu hóa để cho ra tín hiệu tốt nhất. Một hệ thống giao dịch chỉ đúng khi được backtest hiệu quả và cho ra kết quả Out-of-sample tích cực.
