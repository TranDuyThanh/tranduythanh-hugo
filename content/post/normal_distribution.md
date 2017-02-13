+++
date = "2017-02-12T13:53:07+07:00"
title = "Normal Distribution - Phân phối chuẩn"

+++

### Từ đâu người ta nhận ra sự hiện diện của phân phối chuẩn?

Làm việc với thống kê, tôi nghe nhiều về phân phối chuẩn. Cơ mà tôi cứ thắc mắc mãi:

1. Từ đâu mà người ta `nhận ra sự có mặt` của phân phối chuẩn?
2. Hàm phân phối xác suất của phân phối chuẩn được `tìm ra như thế nào`?

Từ các [câu trả lời](https://www.quora.com/How-did-humans-derive-the-normal-distribution), tôi lần theo các tham khảo và cuối cùng cũng tổng hợp cho mình một câu trả lời hài lòng. Nay tôi xin tóm tắt lại cùng với một vài kiến giải dựa trên hiểu biết khiêm tốn của mình:

Từ lâu, trong quá trình thống kê các thông số như:

1. Đặc tính sinh trắc học của những người khỏe mạnh, cùng giới tính, độ tuổi: cân nặng, chiều cao, trị số mạch, huyết áp, đường máu, số lượng hồng cầu
2. Các chỉ số sinh học của loài vật, loài cây cùng độ tuổi
3. Khối lượng, kích thước của các sản phẩm do cùng một máy (hoặc hệ thống máy) sản xuất ra
4. Độ lệch của phi tiêu (trong trò chơi phóng phi tiêu vào bia điểm gồm các vòng tròn đen trắng)
...

> Người ta đã nhận thấy biểu đồ phân phối xác suất (cũng như biểu đồ phần phối tần số) của các thông số trên đều có dạng na ná nhau, nhìn giống như cái chuông (bell curve).

![](normal_distribution.diastolic_blood_pressure.png)

Nhìn vào những biểu đồ phân phối kiểu như thế này, chắc bạn cũng bắt đầu đoán nhận rằng phải có một quy luật chung nào đó. Và nếu quy luật đó tồn tại thì nó có thể được biểu diễn được bởi một hàm số toán học (chính là hàm phân phối xác suất)

### Ta đi tìm hàm phân phối xác suất đó thế nào đây?

Ý tưởng: thử áp dụng toán học để phân tích 1 vị dụ cụ thể (đã đưa ra ở trên)

Ở đây tôi sẽ phân tích ví dụ về trò chơi ném phi tiêu. Để bắt đầu, cần lưu ý 3 giả định sau:

1. Độ lệch của phi tiêu không phụ thuộc vào `hướng của hệ trục tọa độ` (Ở đây ta lấy tâm của bia làm gốc tọa độ decarte)
2. Độ lệch theo hướng `trực giao` là `độc lập`. Tức là nếu chúng ta đi chệch nhiều theo một hướng thì xác suất của các hướng khác không bị ảnh hưởng. (Ở đây ta chỉ có 2 hướng: ngang-dọc)
3. `Sai lệch nhỏ` dễ xay ra hơn `sai lệch lớn`

Giờ vầy: giả sử giờ bạn *ngứa tay* phóng phi tiêu lên bảng. Xác suất nó bay trúng vùng tô đậm nhỏ nhỏ (gọi là A) trong hình dưới đây là bao nhiêu?

![](normal_distribution.cartesian_plane.png)

Với $\Delta x$, $\Delta y$ vô cùng nhỏ, dễ thấy:

- theo phương ngang (x), xác suất phi tiêu bay vào khoảng $[x, x+\Delta x]$ là $p(x)\Delta x$
- theo phương dọc (y), xác suất phi tiêu bay vào khoảng $[y, y+\Delta y]$ là $p(y)\Delta y$

Với giả định độc lập (2) ở trên, ta suy ra xác suất phi tiêu bay vào trong A (vùng tô đậm) là $P_A = p(x)\Delta x.p(y)\Delta y$

Với giả định (1) ở trên, ta suy ra rằng: bất kỳ vùng mặt bảng tương tự A nằm cách tâm O (cũng là tâm bảng) có diện tích bằng $\Delta x\Delta y$ đều có cùng xác suất phi tiêu bay vào. Vậy nên, ta có:
$$P_A = p(x)\Delta x.p(y)\Delta y = g( r)\Delta x\Delta y$$
Dễ thấy rằng: 
$$g( r) = p(x)p(y)$$
Đạo hàm 2 vế theo biến $\theta$. Vì hàm `g` chỉ phụ thuộc vào khoảng cách từ A đến tâm O (tức là r) chứ không phụ thuộc vào hướng của A so với O (tức là $\theta$) nên ta có:
$$0=p(x)\frac{dp(y)}{d\theta}+\frac{dp(x)}{d\theta}$$

Với $x=r.cos(\theta)$ và $y=r.sin(\theta)$, áp dụng vào phương trình trên và tính đạo hàm, ta có:
$$0=p(x)p'(y)(r.cos(\theta))+p(y)p'(x)(-r.sin(\theta))$$
tương đương với:
$$0=p(x)p'(y)x-p(y)p'(x)y$$
hay:
$$\frac{p'(x)}{x.p(x)}=\frac{p'(y)}{y.p(y)}$$
Phương trình vi phân này phải đúng với bất kỳ giá trị nào của $x$, $y$ (cần nhắc lại rằng $x$ và $y$ là 2 biến độc lập). Điều đó chỉ xảy ra khi và chỉ khi mỗi tỉ lệ ở mỗi vế của phương trình vi phân trên là một hằng số. Tức là:
$$\frac{p'(x)}{x.p(x)}=\frac{p'(y)}{y.p(y)}=C$$
Bài toán của chúng ta bây giờ quy về việc giải phương trình vi phân sau:
$$\frac{p'(x)}{x.p(x)}=C$$
$$\iff \frac{p'(x)}{p(x)}=Cx$$
$$\iff ln(p(x))=\frac{1}{2}Cx^2+c$$
$$\iff p(x)=Ae^{\textstyle\cfrac{1}{2}Cx^2}$$

Với giả định số 3  (`Sai lệch nhỏ` dễ xảy ra hơn `sai lệch lớn`), ta suy ra C phải là `số âm`. Và ta viết lại phương trình trên như sau:
$$p(x)=Ae^{\textstyle-\cfrac{1}{2}kx^2} ~~~~~ (k > 0)$$

Nhiệm vụ tiếp theo là tìm `A` và `k`

#### Xác định A

Bất kỳ một hàm phân phối xác suất nào cũng đều phải thỏa mãn: tổng diện tích ***dưới đường cong*** (phần xanh dương trong các ví dụ ở dưới) phải bằng 1.

![](normal_distribution.total.png)

Và tất nhiên hàm `p` cũng không ngoại lệ. Ta có:

$$\int\limits_{-\infty}^{\infty}\textstyle Ae^{-\cfrac{1}{2}kx^2}~dx = 1$$

$$\iff \int\limits_{-\infty}^{\infty}\textstyle e^{-\cfrac{1}{2}kx^2}~dx = \frac{1}{A}$$

Vì hàm số $~~~~~\textstyle e^{\textstyle-\cfrac{1}{2}kx^2}$ có tính đối xứng, nên ta suy ra:

$$\int\limits_{0}^{\infty}\textstyle e^{-\cfrac{1}{2}kx^2}~dx = \frac{1}{2A}$$

Tương tự, ta cũng có biểu thức với `y` như sau:

$$\int\limits_{0}^{\infty}\textstyle e^{-\cfrac{1}{2}ky^2}~dy = \frac{1}{2A}$$

Nhân vế theo vế, ta có:

<!--- 
$$\left( \int\limits_{0}^{\infty}\textstyle e^{-\cfrac{1}{2}kx^2}~dx\right).\left( \int\limits_{0}^{\infty}\textstyle e^{-\cfrac{1}{2}ky^2}~dy\right) = \frac{1}{{4A}^2}$$
-->

![](normal_distribution.equation_01.png)

Vì `x`, `y` là 2 biến độc lập, ta có thể viết lại tích 2 tích phân trên như một tích phân 2 lớp:

<!---
$$\int\limits_{0}^{\infty}\int\limits_{0}^{\infty}\textstyle e^{-\cfrac{1}{2}k(x^2+y^2)}~dydx = \frac{1}{{4A}^2}$$
-->
![](normal_distribution.equation_02.png)

Chuyển về hệ tọa độ cực (với biến $r$ và $\theta$), ta có:

<!---
$$\int\limits_{0}^{\pi/2}\int\limits_{0}^{\infty}\textstyle e^{-\cfrac{1}{2}k(r^2)}~r~dr~d\theta = \frac{1}{{4A}^2}$$
-->
![](normal_distribution.equation_03.png)

Với  $ u=-\frac{k}{2}r^2 $ , ta có:

<!---
$$\int\limits_{0}^{\pi/2} {-\frac{1}{k}} \left[ \int\limits_{0}^{-\infty}\textstyle e^u~du~d\theta \right] = \frac{1}{{4A}^2}$$
-->
![](normal_distribution.equation_04.png)

$$\iff \int\limits_{0}^{\pi/2} {-\frac{d\theta}{dk}} = \frac{1}{{4A}^2}$$

$$\iff -\frac{\pi}{2k} = \frac{1}{{4A}^2}$$

$$\iff A = \sqrt{\frac{k}{2\pi}}~~e^\left(-\cfrac{1}{2}{kx}^2\right)$$

#### Xác định k

Ta biết rằng: trung bình (mean) và phương sai (variance) được xác định như sau:

$$(1)~~~~~\mu=\int\limits_{-\infty}^{\infty}x~p(x)~dx$$

$$(2)~~~~~\sigma^2=\int\limits_{-\infty}^{\infty}(x-\mu)^2~p(x)~dx$$

Vì $x~p(x)$ là hàm lẻ nên ta có ngay $\mu=0$. Thế vào (2), ta có:

$$\sigma^2=\int\limits_{-\infty}^{\infty}x^2~p(x)~dx$$

$$\iff \sigma^2=2\int\limits_{0}^{\infty}x^2~p(x)~dx$$

$$\iff \sigma^2=2\sqrt{\frac{k}{2\pi}}\int\limits_{0}^{\infty}x^2~e^{-\cfrac{1}{2}{kx}^2}~dx$$

Quay lại với biểu thức tính tích phân quen thuộc $\int~u~dv=uv-\int~v~du$
Trong trường hợp này, với $u=x$ và $dv={xe}^{-\cfrac{1}{2}kx^2}$, ta có:

<!---
$$ \sigma^2=2\sqrt{\frac{k}{2\pi}} \left[ \left.\lim_{M \to \infty} \frac{-x}{k}e^{-\cfrac{1}{2}{kx}^2} \right|_0^M + \frac{1}{k}\int\limits_{0}^{\infty}e^{-\cfrac{1}{2}{kx}^2}~dx\right] $$
-->
![](normal_distribution.equation_05.png)

Vì 

$$\left.\lim_{M \to \infty} \frac{-x}{k}e^{-\cfrac{1}{2}{kx}^2} \right|_0^M = 0$$

và

$$\frac{1}{k}\int\limits_{0}^{\infty}e^{-\cfrac{1}{2}{kx}^2}~dx=\frac{1}{k}\frac{\sqrt{2\pi}}{2\sqrt{k}}$$

nên

$$\sigma^2=2\sqrt{\frac{k}{2\pi}}\int\limits_{0}^{\infty}x^2~e^{-\cfrac{1}{2}{kx}^2}~dx = 2\frac{\sqrt{k}}{\sqrt{2\pi}} \frac{1}{k}\frac{\sqrt{2\pi}}{2\sqrt{k}} = \frac{1}{k}$$

$$\iff k=\frac{1}{\sigma^2}$$

#### Hàm phân phối chuẩn:

Với `A` và `k` xác định như trên, ta có ngay:

$$p(x)=\frac{1}{\sigma\sqrt{2\pi}}e^{-\cfrac{1}{2}\left(\cfrac{x}{\sigma}\right)^2}$$

Và đây là hàm phân phối xác suất được suy ra cho bài toán này. Từ đây, ta có thể suy ra hàm phân phối chuẩn tổng quát với trị trung bình $\mu$ và độ lệch chuẩn $\sigma$ cho trước bằng cách `dịch` hàm phân phối trên theo phương x với giá trị $\mu$. Kết quả:

$$p(x)=\frac{1}{\sigma\sqrt{2\pi}}e^{-\cfrac{1}{2}\left(\cfrac{x-\mu}{\sigma}\right)^2}$$

### Tham khảo:
- [http://courses.ncssm.edu/math/Talks/PDFS/normal.pdf](http://courses.ncssm.edu/math/Talks/PDFS/normal.pdf)
- [https://www.quora.com/How-did-humans-derive-the-normal-distribution](https://www.quora.com/How-did-humans-derive-the-normal-distribution)
- [https://en.wikipedia.org/wiki/Normal_distribution](https://en.wikipedia.org/wiki/Normal_distribution)