## 文件预览与上传

	多文件上传，input的multiple属性
		<input type="file" multiple>  

#### 文件预览
当文件改变时，读取本地文件

	读取本地文件 FileReader API
		1. FileReader接口方法
			readAsBinaryString  将文件读取为二进制编码
			readAsText   将文件读取为文本
			readAsDataURL   将文件读取为DataURL
			abort  终端读取操作
		2. FileReader接口事件
			onabort  中断
			onerror  出错
			onloadstart  开始
			onprogress  正在读取
			onload  成功读取
			onloadend  读取完成，无论成功失败

	文件读取进度
		reader.onprogress=function(e){
			e.loaded
		}

#### 文件上传
	```
	var fd = new FormData();
    fd.append('img_form_data', file);
    fd.append('img_subfix', "png");
    ```

Demo
	```
	<script>
		var input = document.querySelector('input'),
			img = document.querySelector('img');
		input.addEventListener('change',function(){
			let file=this.files[0];
			console.log(file.size)
			var reader = new FileReader();
			reader.readAsDataURL(file);
			reader.onloadstart=function(){
				console.log('开始读取')
			}
			reader.onprogress=function(e){
				console.log('正在读取')
				console.log(e.loaded);
			}
			reader.onload=function(){
				console.log('读取成功')
				img.src=reader.result;
				console.log(reader)
			}
			reader.onloadend=function(){
				console.log('读取完成')
			}
		})
	</script>
	```
