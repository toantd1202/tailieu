# Virtualenv
Virtualenv tạo ra một môi trường có các thư mục cài đặt riêng, không chia sẻ thư viện với các môi trường virtualenv khác. Nó thiết lập một môi trường ảo, cho phép sử dụng với các packages của Python mà không làm ảnh hưởng đến những packages đã được cài đặt sẵn trên Python.
Công cụ tạo ra Virtual Environment trên Python là virtualenv. virtualenv tạo ra một thư mục chứa tất cả những thứ cần thiết (executables, libraries).
	Sử dụng Virtual Environment
- cài virtualenv:
```sh
$ pip install virtualenv
```
![alt](https://raw.githubusercontent.com/toantd1202/photo/master/Screenshot%20from%202020-03-12%2008-55-15.png)
Tạo virtualenv :
```sh
$ virtualenv [project_name]
```
![alt](https://raw.githubusercontent.com/toantd1202/photo/master/Screenshot%20from%202020-03-12%2008-55-35.png)
virtualenv sẽ tạo ra một thư mục có tên là [project_name] chứa tất cả những gì cần thiết.
Nếu trên server có nhiều phiên bản Python (2.x, 3.x) ta có thể khởi tạo Virtual Environment với một phiên bản chỉ định:
```sh 
$ virtualenv -p /usr/bin/python2.7 [project_name]
```
Sử dụng Virtual Environment
Khởi động Virtual Environment bằng câu lệnh:
```sh
$ source [project_name]/bin/activate
```
![alt](https://raw.githubusercontent.com/toantd1202/photo/master/Screenshot%20from%202020-03-12%2008-55-53.png)
Tên của Virtual Environment sẽ xuất hiện ở phía trước command prompt, cho ta thấy Python đang sử dụng Virtual Environment. Từ đây tất cả những packages được cài đặt mới sẽ nằm trong thư mục project_name
Thoát khỏi Virtual Environment
Sử dụng câu lệnh
```sh
$ deactivate
```
![alt](https://raw.githubusercontent.com/toantd1202/photo/master/Screenshot%20from%202020-03-12%2008-56-12.png)

# PEP 8
PEP là viết tắt của Python Enhancement Proposal. Một PEP là 1 tài liệu được thiết kế để cung cấp thông tin đến cộng đồng python, hoặc miêu tả một feature mới của python, hoặc các tiến trình hay môi trường của nó. Nó quy định một về một số hình thức để trình bày code trong Python.
##### 1. thụt đầu dòng
- sử dụng 4 khoảng trắng cho mỗi cấp đầu dòng:
![alt](https://raw.githubusercontent.com/toantd1202/photo/master/Screenshot%20from%202020-03-12%2009-24-08.png)
##### 2. chiều dài tối đa của 1 dòng code
- chiều dài tối đa của 1 dòng code là 79 ký tự
- đối với 1 khối văn bản dài(ghi chú- commen): mỗi dòng trong khối nên được giới hạn 72 ký tự.
-đối với dòng code dài thì nên ngắt ra thành nhiều dòng ngắn bằng cách đưa ra các biểu thức vào các cặp ngoặc đơn, cắt dòng khi hoàn thành biểu thức và thêm dấu “\” rồi xuống dòng tiếp theo.
![alt](https://raw.githubusercontent.com/toantd1202/photo/master/Screenshot%20from%202020-03-12%2009-24-23.png)
##### 3. dòng trống
- giữa các phương thức cách nhau bởi 1 dòng trống
- giữa các lớp và phương thức cách nhau bởi 2 dòng trống
- các khối code riêng biệt cách nhau bằng 1 dòng trống.
![alt](https://raw.githubusercontent.com/toantd1202/photo/master/Screenshot%20from%202020-03-12%2009-25-12.png)
##### 4. import
- mỗi thư viện/module import được đặt trên một dòng riêng biệt
ví dụ: 
```sh 
import os
import sys
```
hooặc:
```sh
from subprocess import Popen, PIPE
```
- import thường đặt ở đầu file, sau phần comment/ ghi chú giới thiệu về module và phần khai báo các hằng số và biến toàn cục
- thứ tự các nhóm import:
	-import các thư viện chuẩn
	-import các thư viện của nhà cung cấp thứ ba
	-import các thư viện và ứng dụng cục bộ
##### 5. tên bắt đầu với hai dấu __ liên tục trong module
- với tên biến bắt đầu bằng 2 dấu _ liên tục trong module (còn gọi là “dunders”), ví dụ như __all__,  __author__, tên sẽ được đặt sau phần comment/ ghi chú giới thiệu về module nhưng đặt trước các import.
![alt](https://raw.githubusercontent.com/toantd1202/photo/master/Screenshot%20from%202020-03-12%2009-26-24.png)
##### 6. Sử dụng dáu nháy đơn/đôi cho chuỗi
- trong python, việc để nội dung chuỗi trong dấu nháy đơn ‘’ và nháy dôi “” là như nhau
```sh
print(‘hello’)
# hoặc
print(“hello”)
```
- Tuy nhiên, khi thực hiện việc ghi chú (comment) thì ta nên sử dụng nháy đôi ””” nội dung ghi chú”””
```sh
””” 
this is the example module.
”””
```
##### 7. Sử dụng khoảng trắng trong biểu thức và câu lệnh
- khoảng trắng được đặt ngay sau dấu , dấu ; dấu : (phía trước các dấu này không có khoảng trắng)
```sh
spam(ham[1], {egg: 2})
if x == 4: print x, y; x, y = y, x
```
- không sử dụng khoảng trắng giữa tên hàm và cặp ngoặc ()
```sh
spam(1)
```
- không dùng khoảng trắng trước cặp ngoặc []
```sh
dct[‘key’] = lst[index]
```
- chỉ dùng một khoảng trắng phía trước và sau toán tử để phân cách toán hạng và toán tử
```sh
x = 1
y = 2
long_variable = 3
```
##### 8. Ghi chú
- nội dung nên ghi chú:
* thông tin: tác giả, version, ngày viết
```sh
””” 
@author: toantd
@version: 1.1
@since: Mar 11, 2020
”””
```
- ghi chú ngắn:
cú pháp: #nội dung ghi chú
có một khoảng trắng giữa # và nội dung ghi chú
ví dụ:
```sh 
# First comment
print “hello, Python!” # second comment
x = x + 1                     # increment x
```
với cú pháp dài :
```sh
”””nội dung cú pháp
”””
```
##### 9. Quy tắc đặt tên
- Tên có phân biệt chữ hoa chữ thường
- Sử dụng phong cách under_score
- Tên biến chữ thường, tên hằng chữ hoa
```sh
# tên biến
lower_case_with_underscores
# tên hằng
UPPER_CASE_WITH_UNDERSCORES
MAX_OVERFLOW
```
- Tên biến chỉ gồm một ký tự nên tránh đặt I (dễ nhầm với l), O (dễ nhầm với 0 – zero)
- Tên package: viết thường, ngắn gọn, không khuyến khích sử dụng dấu _
```sh
media
```
- Tên module: viết thường, ngắn gọn, súc tích, dễ hiểu, các từ có thể cách nhau bằng dấu _  trong trường hợp muốn tên module dễ hiểu hơn
ví dụ:
```sh
support.py
```
- Tên class sử dụng nguyên tắc CapWords/ Camelcase
ví dụ:
```sh
class Employee:
```
-Tên function (hàm): viết thường, ngắn gọn, các từ có thể cách nhau bằng dấu _ trong trường hợp muốn đặt tên function dễ hiểu hơn
ví dụ:
```sh
def printme(str):
      print(str)
      return;
printme(‘hello python’)
```



