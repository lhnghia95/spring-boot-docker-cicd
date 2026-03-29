# Sử dụng Nginx bản nhẹ nhất để chạy web tĩnh
FROM nginx:alpine

# Xóa các file mặc định của Nginx
RUN rm -rf /usr/share/nginx/html/*

# Copy toàn bộ file code (HTML, CSS...) vào thư mục web của Nginx
COPY . /usr/share/nginx/html/

# Mở port 80 (bắt buộc theo yêu cầu của hệ thống server)
EXPOSE 80

# Chạy Nginx
CMD ["nginx", "-g", "daemon off;"]