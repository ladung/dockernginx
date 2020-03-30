# Bài viết này chia sẻ cài đặt nginx (tùy chọn phiên bản) bằng dockerfile tất cả từ local.

Cài đặt ELK trên Docker localhost sử dụng dockerfile.
Dowload soucre nginx (tùy chọn phien bản) tại http://nginx.org/download/ và 1 file images nền tảng từ internet. File images có thể pull về từ https://hub.docker.com/_/centos. Sau đó import images vào server local.

**Copy các file vào thư mục như sau:
[root@ladung nginx]# ls
config  Dockerfile  html  mnt  nginx.tar.gz  repo
**Trong đó:
  - config: chứa file config chính của nginx
  - Dockerfile: chứa dockerfile
  - html: chứa source của web
  - mnt: chứ kho repo local mà ta sử dụng để cài các gói phụ thuộc
  - repo: chứa file .repo
  =========================================================================================
  
  Bước 1: Tạo kho repo local để cài các gói phụ thuộc. ( các bạn tìm hiểu tạo repo local trên linux).
  
  Bước 2: Xây dựng nginx từ dockerfile
  
  [root@ladung nginx]: docker build -t nginx:[version] -t Dockerfile/nginx .
  
  Bước 3: Sau khi xây dựng xong images ở trên, các bạn run images đã buil thành container
  
  [root@ladung nginx]: docker run -d -p 8080:80 nginx:[version]
  
  Bước 4: Truy cập http://[ip]:8080 để kiểm tra kết quả
