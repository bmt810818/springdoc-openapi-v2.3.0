# springdoc-openapi-v2.3.0
Learnning

  # enabled: false 
  openapi:
  
  title: Auth API
  gateway-url: ${PUBLIC_GATEWAY_URL:http://localhost:8762}

  Schema: 
  - Nơi hiển thị các cấu trúc Model mà Controller sử dụng
  - Nơi để những người (không phải API Developer) có thể đọc hiểu được cấu trúc dữ liệu.

  - Trong trường hơp API có request body, Schema trở nên thừa thãi không?
  => Không, vì không phải tất cả API đều sẽ có mô tả DSA rõ ràng trong request body, và nếu không có schema thì những người không phải API DEV có thể gặp khó khăn khi đọc hiểu.
