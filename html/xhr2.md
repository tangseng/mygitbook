# XHR2

**新增功能**
* 可以设置HTTP请求的时限
* 可以使用FormData对象管理表单数据
* 可以上传文件
* 可以请求不同域名下的数据（跨域请求）
* 可以获取服务器端的二进制数据
* 可以获得数据传输的进度信息

**HTTP请求的时限**

        xhr.timeout = 10000
        xhr.ontimeout = function(event){
            console.log(event)
        }

**FormData对象**

        let formData = new FormData()
        formData.append('name', '唐僧')
        formData.append('money', 100000000)
        xhr.send(formData)

**上传文件**

        //file为input[type="file"]
        formData.append('files[]', file) 

**CORS**

        跨域与不跨域的请求代码一致，浏览器自己做了处理

**接收二进制数据**

        //请求的时候将xhr对象的responseType设置为'blob'
        xhr.responseType = 'blob'
        //读取的时候，用浏览器的Blob对象封装
        let blob = new Blob(xhr.response, {type: 'image/png'})

**进度信息**

        传送数据的时候，有一个progress事件，用来返回进度信息。分上传和下载两种。
        xhr.onprogress = function(event){
            if (event.lengthComputable) {
                let percentComplete = event.loaded / event.total
            }
        }
        xhr.upload.onprogress = function(){}

        //其他相关事件
        * load事件： 传输成功完成。
        * abort事件：传输被用户取消。
        * error事件：传输中出现错误。
        * loadstart事件：传输开始。
        * loadend事件：传输结束，但是不知道成功还是失败。
        


**相关文章**
* [XMLHttpRequest Level 2 使用指南](http://www.ruanyifeng.com/blog/2012/09/xmlhttprequest_level_2.html)