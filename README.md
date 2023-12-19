# springdoc-openapi-v2.3.0
- <Mục tiêu chính của Springdoc là tạo và xuất bản tài liệu OpenAPI cho các ứng dụng Spring Boot>
- springdoc-openapi v2.3.0 dùng để tạo tài liệu API tự động dựa trên mã nguồn của application và giữ nó đồng bộ với mã nguồn.
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


# 1. @Schema Properties:

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


  dependencies đang dùng: 
"springdoc-openapi-starter-webmvc-ui" ===> nó giúp có thêm quyền truy cập vào swagger-ui
"spring-boot-starter-web" ===> thêm nó vào để nó tự config một số thứ cho mình
"org.springdoc.core.models.GroupedOpenApi" ===> gom nhóm các API có cùng chung /path/ để dễ control ==> dùng GroupedOpenApi.builder().group()
"org.springframework.boot:spring-boot-starter-data-jpa" ===> cung cấp mọi thứ cần thiết để làm việc với cơ sở dữ liệu thông qua JPA (Java Persistence API).
"org.springframework.boot:spring-boot-starter-validation" ===> thêm nó vào để dùng được @Email, @Size, @NotNull ===> kiểm tra và xác thực dữ liệu dễ dàng hơn, giảm thiểu việc viết mã kiểm tra dữ liệu thủ công



Các Modules đang được sử dụng:
@RepositoryRestResource:  nó sẽ tự động tạo ra các RESTful API dựa trên các phương thức trong các interface repository.
exported = false // dùng để ẩn hoặc hiển thị một repository trong RESTful API

@OpenAPIDefinition: define các tiêu đề (title), phiên bản (version), mô tả (description), địa chỉ trang web (termsOfService), thông tin liên hệ (contact), và thông tin giấy phép (license).
@Hidden: Khi đánh dấu một phương thức hoặc một controller với @Hidden, nó sẽ không xuất hiện trong tài liệu OpenAPI được tạo ra.

@Configuration + @Bean: 


## Thực nghiệm
- Nếu không có @Configuration, thì Info serviceInfo = new Info().title(title).version("1.0").description("Documentation API SUCCESS v1.0"); sẽ không hoạt động

# Solution for fix Configuration:
- in @SpringBootApplication(exclude = DataSourceAutoConfiguration.class), DELETE (exclude = DataSourceAutoConfiguration.class)
- addon 'com.h2database:h2' to build.gradle
## Nguyên nhân lỗi:
- Khi sử dụng @SpringBootApplication, nếu không có cấu hình cụ thể, Spring Boot tự động cấu hình nhiều thứ, bao gồm DataSource để kết nối cơ sở dữ liệu.
- Nếu muốn tùy chỉnh hoặc không sử dụng DataSource, bạn có thể thêm exclude = DataSourceAutoConfiguration.class.
- Ngược lại, nếu muốn sử dụng cấu hình mặc định, bạn có thể xóa exclude = DataSourceAutoConfiguration.class.

