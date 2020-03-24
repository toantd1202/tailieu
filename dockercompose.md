# Docker-compose
Compose là một tool để xác định và chạy các ứng dụng multi-container. Với Compose, sử dụng tệp YAML để định cấu hình dịch vụ của ứng dụng. Sau đó, với một lệnh duy nhất, tạo và bắt đầu tất cả các dịch vụ từ cấu hình.
Install `docker-compose` :
```sh
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.25.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
$ docker-compose --version
docker-compose version 1.25.4, build 1110ad01
```
Tạo `docker-compose` cho `flask app`.
![alt](https://github.com/toantd1202/buoc1/blob/master/Screenshot%20from%202020-03-24%2022-33-19.png?raw=true)
clone repo chứa app trên github rồi checkout sang nhánh của em:
![alt](https://github.com/toantd1202/buoc1/blob/master/Screenshot%20from%202020-03-24%2022-21-17.png?raw=true)
Tạo các file `Dockerfile`, `docker-compose.yml` có nội dung lần lượt:
+ `Dockerfile`
```sh
FROM python:3.7-alpine
ENV FLASK_RUN_HOST 0.0.0.0
RUN apk add --no-cache gcc musl-dev linux-headers
WORKDIR /app
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
COPY . .
ENTRYPOINT ["python"]
CMD ["get_post_put_delete.py"]
```
Build image
![alt](https://github.com/toantd1202/buoc1/blob/master/Screenshot%20from%202020-03-24%2020-16-45.png?raw=true)
Run container:
![alt](https://github.com/toantd1202/buoc1/blob/master/Screenshot%20from%202020-03-24%2020-16-13.png?raw=true)

+ `docker-compose.yml`
```sh
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/code
```
![alt](https://raw.githubusercontent.com/toantd1202/buoc1/master/Screenshot%20from%202020-03-24%2022-06-37.png).
kết quả:
![alt](https://github.com/toantd1202/buoc1/blob/master/Screenshot%20from%202020-03-24%2022-06-11.png?raw=true).
Sử dụng `Compose` về cơ bản là một quá trình gồm ba bước:
    • Xác định môi trường ứng dụng với `Dockerfile` để có thể sao chép nó ở bất cứ đâu.
    • Xác định các dịch vụ tạo nên ứng dụng trong` docker-compose.yml` để chúng có thể được chạy cùng nhau trong một môi trường biệt lập.
    • Chạy `docker-compose up` và `Compose` bắt đầu và chạy toàn bộ ứng dụng.
###### Chay thử docker-compose.yml


```sh
version: '3.3'
services:
  db:  # database service
    image: mysql:5.7    #Sử dụng mysql:5.7 image được pull về từ trang chủ của docker.hub
    volumes:        #Mounts nội dung thư mục db_data ở trên máy vào thư mục /var/www/html/blog trong containers. Việc này cho phép sửa code mà không cần phải rebuilt lại image. (sửa code -> reload trình duyệt).
      - db_data:/var/lib/mysql
    restart: always     # luôn restart
    environment:    # khai báo các tham số
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress

  wordpress:    # wordpress service
    image: wordpress:latest     #Sử dụng wordpress:latest image được pull về từ docker.hub
    ports: 
      - 8000:80     # Chuyển từ cổng 80 trên container đến cổng 8000 trên máy host local
    restart: always     # luôn khởi động lại
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
    depends_on:     # muốn chạy đươch thì phụ thuộc vào các service db, pma hoàn thành 
      - db
      - pma
  
  pma:      # pma service
    image: phpmyadmin/phpmyadmin    #Sử dụng phpmyadmin/phpmyadmin image được pull về từ docker.hub
    environment:        
      PMA_HOST: db
      PMA_PORT: 3306
      MYSQL_ROOT_PASSWORD: somewordpress
    restart: always 
    ports:      
      - 8020:80     # huyển từ cổng 80 trên container đến cổng 8020 trên máy host local
    depends_on:     
      - db

volumes:
  db_data: {}
```

Sau khi chạy `docker-compose.yml`
![alt](https://raw.githubusercontent.com/toantd1202/buoc1/master/Screenshot%20from%202020-03-25%2000-21-26.png).
![alt](https://raw.githubusercontent.com/toantd1202/buoc1/master/Screenshot%20from%202020-03-25%2000-23-20.png).
![alt](https://raw.githubusercontent.com/toantd1202/buoc1/master/Screenshot%20from%202020-03-25%2000-20-43.png).


