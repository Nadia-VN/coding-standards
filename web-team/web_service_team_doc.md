# Web Service Team's Documentation
***

### Table of content
***
1. ##### [Lời nói đầu](#anchor1)
2. ##### [Recomendation before starting](#anchor2)
3. ##### [Front-end Development practice](#anchor3)
4. ##### [General Coding Standard](#anchor4)
5. ##### [Laravel's PHP coding standard](#anchor5)
6. ##### [1 số lưu ý khi sử dụng Laravel](#anchor6)
7. ##### [API Programming Guide](#anchor7)


### [Lời nói đầu](id:anchor1)
***
***Để nâng cao chất lượng code, đồng thời đảm bảo tính thống nhất, khả năng chia sẻ, hỗ trợ trong các project và giữa cáp lập trình viên của team, từ bây giờ các developer trong web service team cần tham khảo trước tài liệu này và áp dụng các qui chuẩn trong đó cho các project mà mình phụ trách***

Có gì cần thắc mắc thì liên lạc <linhtm@nadia.bz> hoặc skype: linhmtran168  

### [Recommendation before starting](id:anchor2)
***
1. Sử dụng 1 hệ điều hành Unix-based (recommend Ubuntu) hoặc ai có điều kiện thì Mac
	* Cài đặt Ubuntu:
		* Nếu ai dùng laptop đời mới có logo windows 8 thì phải dùng Ubuntu 64 bit và làm theo hướng dẫn ở đây <https://help.ubuntu.com/community/UEFI>
		* Cách tạo usb chứa bộ cài ubuntu <http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows>
		* Tham khảo cài đặt
			* [Cài đặt bình thường và phân ổ](http://www.linuxbsdos.com/2012/11/03/ubuntu-12-10-installation-and-disk-partitioning-guide/)
			* [Dual boot với windows 8](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)
	* Tham khảo tutorial để sử dụng Ubuntu 
		* (English) Command line <http://www.faculty.ucr.edu/~tgirke/Documents/UNIX/linux_manual.html> 
		* (Tiếng Việt) <http://wiki.ubuntu-vn.org/index.php/T%C3%A0i_li%E1%BB%87u_Ubuntu-VN>
	* Some commands for server-side programming <http://rubytune.com/cheat>
	* Biết cách cài đặt LAMP (Linux, Apache, MySQL, PHP) stack 
		* PHP, MySQL, Apache <http://www.liberiangeek.net/2012/10/install-lamp-linux-apache-mysql-php-in-ubuntu-12-10-quantal-quetzal/>
		* phpMyAdmin <http://howtofindsolution.blogspot.com/2012/11/how-to-install-and-configure-phpmyadmin_8675.html>
2. Sử dụng text editor "for programmer"
 	* Sublimetext (recommended)
 	* Vim (ai pro thì dùng)
 	* Netbeans
 	* Eclipse
3. Cần học cách sử dụng GIT. Tham khảo
   * <http://git-scm.com/book>
   * <http://gitref.org/basic/>
4. ***Cần khả năng đọc hiểu tiếng Anh tốt***
 	
### [Front-end Deveplopment practice](id:anchor3)
***
1. **Không bao giờ để lẫn CSS, HTML, Javascript. CSS file riêng, Javascript file riêng tách biệt với HTML code**
2. CSS
	+ Nên đặt tên **id**, **class** dưới dạng giống như Bootstrap (có dấu - giữa các từ). Ví dụ: 
				
			<div class=""col-lg-offset-1" id="user-login-div"></div>
			
	+ Còn **name** của các element thì nên theo naming của framework serverside đang sử dụng (với Laravel 4 thì là camel case). Ví dụ với Laravel 4: 
	
			<input name="userLanguage" class="input-long"></input>
			
3. Nên sử dụng 1 front-end framework (Bootstrap,…)
4. Optimize các ảnh trước khi sử dụng cho web (png hoặc gif)
5. Code HTML cần rõ cấu trúc, phần nào ra phần đấy, không lẫn lỗn các thẻ
6. Khi đóng 1 thẻ div cần comment đã đóng thẻ nào

		<div id="header">
  			<div id="sub" class="first left">
    			...
  			</div><!-- #sub.first.left -->
		</div><!-- #header -->
		
7. Import file javascript ở cuối file html

		 		...
    			<script type='text/javascript' src='jquery.js?ver=1.8.1'></script>
  			</body>
		</html>
		
8. Import file css trong thẻ head ở đầu file

			<head>
				...
				<link rel='stylesheet' type='text/css' href='a.css'>
			</head>
		
9. To be continued…  
  

### [General Coding Standards](id:anchor4)
***
1. **Đối với PHP, CSS, HTML, Javascript, cài đặt "tab space"(tabstop) cho editor là 2**
2. To be continued..



### [Laravel 4's PHP coding standards (đồng thời cũng áp dụng cho code PHP thường)](id:anchor5)
***
##### Naming convention

- Sử dụng [Camel Case](http://en.wikipedia.org/wiki/CamelCase)
- Đặt tên file phải theo camelCase như trên
	* Nếu file đấy chứa 1 class hoặc interface thì viết hoa ký tự đầu. ví dụ: UserValidator.php
	* Còn lại các trường hợp khác thì không viết hoa ký tự đầu. ví dụ: userProfile.blade.php, configDatabase.php
	
	 
##### File Format 
Luôn save file với encoding utf-8
##### PHP open closing tag
Với bất kì một file php nào mà chỉ chứa code php, thì ko cần close the php tag '?>' và không được có space trước open tag

			// INCORRECT
			// test.php
			<?php
				php_info();
			?>
			
			// INCORRECT
			// test.php
			
			   <?php
			  php_info();
			 ?>
			 
			//CORRECT
			// test.php
			<?php
				php_info();
				// End of file, don't close the php tag
				
##### Class, Method, Function, Variable
**Class, Interface**

* Chỉ một class cho 1 file php
* Sử dụng Camel Case, các từ viết liền, viết hoa kí tự đầu của các từ trong tên của class ví dụ:  **AdminController**
* Tên phải ngắn gọn dễ hiểu, nêu rõ mục đích của class
* Dấu { ở cùng dòng với khai báo class

			// CORRECT
			class AdminHomeController extends BaseController {

    			…….

			}
			
			// INCORRECT
			class Admin_homeController 
			{
			…
			}
			
			class Adminhomecontroller 
			s{
			..
			}
			
**Method, function**

* Camel Case, viết liền, ko viết hoa kí tự đầu của từ đầu tiền, các từ sau thì kí tự đầu viết hoa ví dụ: **getUserProfile**
* Tên ngắn gọn dễ hiểu, nói rõ mục đích của method
* Dấu { không cùng dòng với khai báo class

			// CORRECT
			function getAdminUsers($number = NULL) 
			{
			   …
			}
			
			// INCORRECT
			function get_Amin_users() {
			}

**Variables, property**

* Tương tự như đặt tên method và function
* Các tên biến gồm 1 kí tự như $i, $j chỉ dùng trong vòng lặp for. Còn lại tên biến cần rõ ràng, thể hiện rõ chức năng

			// CORRECT
			$password
			$accessTtoken
				
			// INCORRECT
			$Password
			$access_Token
			$access_token
				
**Constant**

Viết hoa tất cả các ký tự, nếu gồm nhiều từ thì cách các từ bằng kí tự "_"

		// CORRECT
		define('MY_CONSTANT', 'MY_CONSTANT');
		echo MY_CONSTANT;

##### Vòng lặp và điều kiện
Với tất cả các vòng lặp và điều kiện thì dấu { phải ở 1 dòng riêng

			// CORRECT
			if ($test > 0)
			{
			  ...
			}
			else 
			{
			  ...
			}
			
			// CORRECT
			for ($i = 0; $i < rows.length; i++)
			{
			 …
			}
			
			// CORRECT
			foreach ($arr as $key => $val)
			{
			…
			}			

		
##### Các giá trị boolean and NULL
Luôn viết ở dạng thường các kí tự này:

		true
		false
		null
		
##### Dấu cách trong các dấu (), []
Không có dấu cách giữa nội dung bên trong của dấu và các dấu này

		// CORRECT
		$arr['abc']
		if ($isValid)
		
		// INCORRECT
		$arr[ 'abc' ]
		if ( $isValid )
		
##### Comment
* Comment theo [DocBlock](http://phpdoc.org/docs/latest/index.html) style. 1 số ví dụ:

		/**
 		* UserController Class
 		* 
 		* @package	Package Name
 		* @subpackage	Subpackage
 		* @category	Category
 		* @author	Linh Tran
 		* @link	
 		*/
		class User_Controller extends Base_Controller 
		{
		...
		}

			
		/**
 		* Decode json string to array
 		*
 		* @access	public
 		* @param	string
 		* @return	Array
 		*/
		function jsonDecode($str)
		{
		…
		}
		
		/**
		* @var property to define user data
		*/
		protected $userData;
		
		/**
		* Constant to define timezone
		*/
		define('DEFAULT_TIMEZONE', 'Asia/Bangkok')
				
* Với các trường hợp khác thì sử dụng inline comment. **Trước 1 block of code để thực hiện 1 chức năng nào đấy, cần phải sử dụng comment**.

		// Create the hashed string for user password
		$password = Input::get('password')
		$hash = Hash::make($password)
		
##### Khai báo function, điều kiện, vòng lặp, biến thành nhiều dòng (do quá dài)
**Class**

	class SampleClass
    	extends FooAbstract
    	implements BarInterface {
	}

**Function**

	public function bar($arg1, $arg2, $arg3,
        $arg4, $arg5, $arg6)
    {
        // all contents of function
        // must be indented four spaces
    }
    
**String**
	
	$sql = "SELECT `id`, `name` FROM `people` "
     	. "WHERE `name` = 'Susan' "
     	. "ORDER BY `name` ASC ";
     
**Array**

	// Normal Array
	$sampleArray = array(1, 2, 3, 'Zend', 'Studio',
                     	$a, $b, $c,
                     	56.44, $d, 500);
    // Associative array                 
    $sampleArray = array(
    	'first_key'  => 'firstValue',
    	'second_key' => 'secondValue',
	);

	
### [1 số lưu ý khi sử dụng Laravel](id:anchor6)
***
##### MVC Architecture
Trong 1 application cần phân biệt rõ giữa Model, View, Controller

* Model: Bao gồm các business logic ví dụ như:

  * Database Interactions
  * File I/O
  * Interactions with Web Services
  
* Controller: Chức năng kết nối giữa Model và View, xử lý Input, lấy dữ liệu từ Model cho View
* View: **View ko được chứa code logic**. View chỉ dùng đễ thể hiện các dữ liệu mà controller đã trả về cho View. 
  * Nên sử dụng Blade template của Laravel để có thể có được sự phân tách rõ ràng hơn giữa View và Controller <http://laravel.com/docs/views/templating> 
  
##### Security
* Luôn lấy input thông qua hàm của Laravel: Input::get('…') tránh lấy trực tiếp từ $_GET, $_POST vì Laravel sẽ xử lý input tránh XSS, SQL injection
* Trừ những trường hợp mã hoá không quan trọng, thì nên sử dụng các hàm mã hoá của Laravel
  * Ví dụ như lấy hash password (không cần giải mã)thì dùng Hash::make('…')
  * Các trường hợp cần giải mã thì dùng Crypter::encrypt('..')
  * Tránh dùng md5 vì nó không bảo mật, dễ bị phá
  
##### Sử dụng [Composer](http://getcomposer.org/)
* Laravel 4 sử dụng [Composer](http://getcomposer.org/) để quản lý các 3rd packages sử dụng cho application của mình. Có thể tìm các packages này ở trang [https://packagist.org/](https://packagist.org/)
* Có thể chỉnh sửa các thiết lập composer cũng như add thêm các thư mục để application autoload ở trong file ```composer.json``` trong thư mục gốc 



### [API Programming Guide](id:anchor7)
***
##### RESTful API
Hầu hết các API hiện tại đều là RESTful API. Các API (web service) mà chúng ta lập trình trong tương lai cũng đều sẽ là RESTful API. Vậy RESTful API là gì?

RESTful API (hay RESTful web service) là 1 api được thiết kế dựa trên giao thức HTTP và các nguyên tắc của kiến trúc [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) (Có thể đọc kĩ thêm để hiểu về REST, mặc dù ko cần thiết lắm, chỉ cần hiểu rõ RESTful API hoạt động thế nào, và implement thế nào). RESTful API là 1 tập hợp của các tài nguyên với 4 đặc điểm sau

* Base URI của web API ví dụ *http://icts.vn/api/users*
* Internet mediatype của dữ liệu trả về được hỗ trợ bởi API (thường là JSON, đây cũng là format dữ liệu mà ta sẽ sử dụng chính yếu)
* Tập hợp các thao tác được hỗ trỡ bởi API sử dụng các HTTP methods (ta sẽ thưởng chỉ sử dụng GET, PUT, POST, DELETE)
* Hypertext driven, đại ý là các clients của API chỉ biết được access path (URI) của 1 resource và từ đó có thể lấy được URI (access path) của các thành phần của resource đó. Ví dụ: ta có resource User với URI là *http://icts.vn/api/users*. Thì dữ liệu trả về từ URI này sẽ cho phép ta biết được URI để lấy dữ liệu cho User 100 là *http://icts.vn/api/users/100*

Tham khảo thêm

* <http://rest.elkstein.org/2008/02/what-is-rest.html>
* <https://blog.apigee.com/detail/does_your_api_need_to_be_truly_restful/>


##### RESTful API HTTP methods
Các HTTP methods thông thường được sử dụng trong API bao gồm GET, PUT, POST, DELETE.

* **GET** Lấy thông tin của 1 resource từ API
* **POST** Tạo resource mới
* **PUT** Update thông tin của 1 resource đã có
* **DELETE** Xoá 1 resouce

Ví dụ: Nếu ta có 1 resouces là user thì ta có thể có 1 RESTful API cho User như sau

Base URI: *http://sample.icts.vn/api/users*

HTTP methods | URI | Ý nghĩa | Thông tin trả về 
-------------|-----|---------|--------
POST | http://sample.icts.vn/api/users | Tạo 1 user mới | Trả về id của user mới này
GET | http://sample.icts.vn/api/users | Lấy tất cả các user | Trả về thông tin của users (quan trọng là id)
GET | http://sample.icts.vn/api/users/:id | Lấy thông tin của 1 user | Trả về thông tin của 1 user
PUT | http://sample.icts.vn/api/users/:id | Update thông tin của 1 user | Trả về thông báo thành công cùng thông tin mới
DELETE | http://sample.icts.vn/api/users/:id | Xoá bỏ user này | Trả về thông báo thành công

Tham khảo thêm: <http://www.restapitutorial.com/lessons/httpmethods.html>

##### Dữ liệu trả về từ API
Thông thường tuỳ theo trạng thái xử lý request từ client mà API sẽ trả về các HTTP status code khác nhau (tham khảo: <http://www.restapitutorial.com/httpstatuscodes.html>). Tuy nhiên do chúng ta chủ yếu tạo API cho các mobile app, để cho người lập trình client dễ dàng xử lý dữ liệu trả về, sẽ chỉ có status code 200 được sử dụng (HTTP status code mặc định khi trả dữ liệu về, ko cần thêm thắt gì vào code).

JSON là định dịnh dữ liệu trả về chủ yếu mà chúng ta sẽ sử dụng. Các response json trả về cần ít nhất các trường như sau:

* **statusCode**: Khác với HTTP status code, đây là status code do chúng ta tự định tuỳ theo app mà để phù hợp. Ví dụ 0 là thất bại, 1 là thành công
* **message**: Thông báo kèm theo với dữ liệu trả về (cần rõ ràng, ngắn gọn)
* **data**: Dữ liệu trả về

##### Basic security for API

* Nếu API không có hệ thống login/logout chỉ đơn giản là access API thì mỗi request chỉ cần gửi kèm 1 ***apiKey*** (apiKey này chỉ có server và client biết)
* Nếu API có hệ thống login/logout
	* Vẫn cần có 1 ***apiKey*** cho những API mà không cần user phải login
	* Sau khi user đã login thì server cần phải tạo ra 1 unique ***authToken*** riêng cho user đó và trả về cho client. Tất cả các request sau khi user đã login cần phải gửi kèm ***authToken*** này
* Không phương pháp nào là bảo mật hoàn toàn nếu giao tiếp với API vẫn chỉ qua HTTP. Trong các trường hợp cần bảo mật cảo thì nên giao tiếp qua HTTPS (thường bên mình sẽ không tự quyết định được vì cái này cần phải mua certification cho domain và cài đặt lên server) 



 


 	
 	


