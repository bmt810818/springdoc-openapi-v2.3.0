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


#1. @Schema Properties:
  @Schema annotation trong Swagger/OpenAPI chứa nhiều thuộc tính để bạn có thể tùy chỉnh mô tả của các trường dữ liệu. Dưới đây là một số thuộc tính phổ biến:
  
  description: Mô tả ngắn về trường hoặc đối tượng.
  
  name: Tên trường dữ liệu.
  
  required: Xác định xem trường có bắt buộc hay không (boolean).
  
  example: Một giá trị ví dụ để hiển thị trong tài liệu.
  
  format: Định dạng của trường dữ liệu (ví dụ: "date-time" cho ngày giờ).
  
  pattern: Một biểu thức chính quy để kiểm tra giá trị của trường.
  
  minimum và maximum: Giá trị tối thiểu và tối đa cho trường số.
  
  maxLength và minLength: Số ký tự tối đa và tối thiểu cho trường chuỗi.
  
  maximum và minimum: Giá trị tối đa và tối thiểu cho trường số.
  
  allowableValues: Một danh sách giá trị được phép cho trường.
  
  deprecated: Xác định xem trường có bị lạc hậu không (boolean).
  
  hidden: Ẩn trường trong tài liệu (boolean).
  
  type: Kiểu dữ liệu của trường (ví dụ: "string", "integer", "object",...).
  
  implementation: Chỉ định một class cụ thể mà trường sẽ được triển khai.
