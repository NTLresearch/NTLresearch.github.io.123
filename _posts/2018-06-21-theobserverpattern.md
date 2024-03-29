---
layout: article
title: "Design Pattern 1: The observer pattern (phần 1)"
date: 2018-06-21 12:00:00
categories: DesignPatterns
featured: true
featured_image: "/images/Prgm/prg1.jpg"
tags: Programming DesignPatterns
author: Nathan Nguyen
---

Ở series bài viết này, tôi sẽ code và phân tích các design pattern (hay còn gọi là mẫu thiết kế lập trình) được thiết kế và tối ưu hóa trong quá trình lập trình OOP (hướng đối tượng). Ngôn ngữ được sử dụng sẽ là Java và Python. Trong một số trường hợp tôi sẽ dùng C++. Thêm vào đó, tôi sẽ phân tích các design pattern được sử dụng trong các framework ứng dụng vào ngành tài chính.

Bài viết này sẽ nghiên cứu ứng dụng của 1 design pattern rất phổ biến, đó là observer pattern.


### 1. Observer Pattern là gì
Về mặt trừu tượng, observer pattern khá giống với việc subscription. Đơn giản thế này, tôi có thông tin liên lạc của 1 analyst, bản tin của anh này rất hữu ích cho tôi. Để nhận bản tin hằng ngày, anh ta cần đưa tôi vào danh sách gửi email 3 tiếng trước mỗi phiên giao dịch. Báo cáo của anh ta bao gồm 1 số thông tin như sau:

- giá trị kì vọng trong phiên

- khối lượng kì vọng trong phiên

- khuyến nghị: mua hoặc bán

Ở khía cạnh lập trình, có thể hiểu ở danh sách khách hàng của analyst  là 1 subject object (đối tượng chủ thể) và địa chỉ của khách hàng là 1 observer object (đối tượng quan sát). Analyst sẽ update bản tin hằng ngày, và thông tin được update sẽ chuyển tới danh sách khách hàng. Sau khi cập nhật, các khách hàng đã đăng kí sẽ nhận được bản tin.

Giả sử có 3 trader đồng ý nhận bản tin và cung cấp . Cấu trúc của hệ thống tương tự như sơ đồ bên dưới:

![c1](/images/Prgm/dp1.png)


### 2. Observer Pattern trong Java

Trong java, Observer Pattern sẽ được thực hiện bằng cách viết class sử dụng 2 interface Subject và Observers như đoạn code bên dưới:

{% highlight java %}
// Interface cho Subject
public interface Subject{
    public void registerObserver(Observer o);
    public void removeObserver(Observer o);
    public void notifyObservers();
}

// Interface cho Observer, tham so co the thay doi
public interface Observer {
    public void update(float index, int volume, int recommend);
}

public interface DisplayElement {
    public void display();
}
{% endhighlight %}

Tôi viết interface DisplayElement nhằm mục đích print ngoài màn hình. Mỗi 1 class implements DisplayElement phải override phương thức display.

### a. Observer Pattern cho analyst và trader:

Ở phần này tôi sẽ viết 2 class Info (sử dụng Subject interface) và class receiveInfo (sử dụng Observer interface). 3 thông tin quan trọng mà analyst cần cập nhật cho trader lần lượt là:

- Giá trị kì vọng trong phiên: thuộc tính index dạng float (ví dụ 1250)

- Khối lượng kì vọng trong phiên: thuộc tính volume dạng int (ví dụ 1200)

- Khuyến nghị: thuộc tính recommend dạng int (1 là mua 0 là bán)

Class Info sẽ được viết như sau:

{% highlight java %}
// class Info (Subject)
import java.util.ArrayList;

public class Info implements Subject {
    // arrayList de giu cac observer object
    private ArrayList<Observer> observers;
    private float index;
    private int volume;
    private int recommend;

    public Info(){
        observers = new ArrayList<Observer>();
    }

    // dang ky observer object vao arrayList
    public void registerObserver(Observer o) {
        observers.add(o);
    }

    // huy dang ky observer object trong arrayList theo index
    public void removeObserver(Observer o){
        int i = observers.indexOf(o);
        if (i >= 0){
            observers.remove(i);
        }
    }

    // update thong tin vao cac observer chua trong arrayList
    public void notifyObservers() {
        for (Observer observer: observers){
            // method update duoc overide o class observer
            observer.update(index, volume, recommend);
        }
    }

    //wrappers cho notifyObservers()
    public void InfoChanged(){
        notifyObservers();
    }

    // thay doi thong tin va cap nhat voi object
    public void setInfo(float index, int volume, int recommend){
        this.index = index;
        this.volume = volume;
        this.recommend = recommend;
        InfoChanged();
    }

    public float getIndex(){
        return index;
    }

    public int getVolume(){
        return volume;
    }

    public int getRecommend(){
        return recommend;
    }

}

{% endhighlight %}

Phân tích đoạn code trên, có thể thấy mỗi khi khởi tạo 1 object Info, constructor của class sẽ khởi tạo 1 ArrayList (cấu trúc dữ liệu trong java) để lưu lại các observer. Sau đó mỗi lần cần update các thuộc tính (thông tin về index, volume và recommend) thông qua phương thức setInfo, các observer trong ArrayList sẽ được update thông tin tương ứng.

Class ReceiveInfo được viết như sau:

{% highlight Java %}
public class ReceiveInfo implements DisplayElement, Observer {
    private float index;
    private int volume;
    private int recommend;
    private Subject Info;

    public ReceiveInfo(Subject Info){
        this.Info = Info;
        Info.registerObserver(this);
    }

    public void update(float index, int volume, int recommend){
        this.index = index;
        this.volume = volume;
        this.recommend = recommend;
        display();
    }

    public void display(){
        System.out.println("Expeted Index: " + index + " and Expected Volume: " + volume);
        if (recommend==1){
            System.out.println("Expected BUY");
        } else {
            System.out.println("Expected SELL");
        }
    }

}
{% endhighlight %}

Ở đoạn code trên, có thể thấy khi khởi tạo 1 object thuộc class ReceiveInfo, cần phải truyền vào 1 tham số là 1 object thuộc class Subject. Mỗi khi khởi tạo, object thuộc class ReceiveInfo sẽ tự động được lưu vào arrayList của object class Subject. Tôi cung cấp thêm phương thức display để in ra màn hình thông tin cập nhật .


Chương trình Main của Java sẽ được viết như sau:

{% highlight java %}
public class TradingDesk {
    public static void main(String[] args) {
        Info Info = new Info();
        ReceiveInfo ReceiveInfo = new ReceiveInfo(Info);

        Info.setInfo(1000, 1200, 1);
        Info.setInfo(1100, 2000, 0);
        Info.setInfo(1200, 20000, 1);


    }
}
{% endhighlight %}

Sau khi chạy chương trình tôi được output như sau

{% highlight Java %}
run:
Expeted Index: 1000.0 and Expected Volume: 1200
Expected BUY
Expeted Index: 1100.0 and Expected Volume: 2000
Expected SELL
Expeted Index: 1200.0 and Expected Volume: 20000
Expected BUY
BUILD SUCCESSFUL (total time: 0 seconds)

{% endhighlight %}


### **3. Những điều cần lưu ý về Observer pattern**

* Đầu tiền là sử dụng interface cho Subject và Observer với các phương thức cần được override
* Thứ 2, nếu để ý kỹ, khi khởi tạo object của class ReceiveInfo, cần truyền vào 1 tham số là object của class Subject. Tức là mỗi khi 1 class implement interface Subject sẽ luôn có thể truyền vào hàm constructor (Đây là đặc tính rõ nhất về tính đa hình - polymorphism trong java). Trong chương trình main, tôi truyền vào object của class Info (class implement interface Subject)
* Thứ 3, arrayList sử dụng reference, tức là các object Observer sẽ update ở môi trường global environment hơn là local (check pass by reference và pass by copy of value trong java).

### **4. Ứng dụng của Observer pattern**

Có lẽ Observer pattern là một trong những Design pattern phổ biến nhất trong giới lập trình. Ví dụ điển hình nhất notification của post trên Facebook. Mỗi khi người dùng comment vào 1 post, người dùng mặc định đăng kí nhận thông báo mỗi khi có ai phản hồi hoặc comment trong post đó. Ở đây post là subject, hộp notification của người dùng là observer.
