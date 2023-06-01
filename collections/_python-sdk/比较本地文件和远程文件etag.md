---
title: '比较本地文件和远程文件etag'
sidebar:
  nav: python-sdk
---


## 使用说明

* 判断文件的完整性，用于判断文件上传、下载过程中是否发生丢失。

## 函数说明

`compare_file_etag`(*bucket*, *remotekey*, *localfile*)

​				比较本地文件和远程文件etag

### Parameters

- **bucket** – string类型, 空间名称
- **remotekey** – string类型, 文件在空间中的名称
- **localfile** – string类型，本地文件的路径

### Returns

* True为比对一致，False为不一致

## 代码示例

<div class="copyable" markdown="1">

{% highlight python linenos %}
from ufile import filemanager

public_key = ''                 #账户公钥
private_key = ''                #账户私钥

bucket = ''                     #添加空间名称
put_key = ''                    #添加远程文件key
local_file=''                   #添加本地文件路径

# 设置上传host后缀,外网可用后缀形如 .cn-bj.ufileos.com（cn-bj为北京地区，其他地区具体后缀可见控制台：对象存储-单地域空间管理-存储空间域名）
# 默认值为'.cn-bj.ufileos.com'，如果上传文件的bucket所在地域不在北京，请务必设置此项
upload_suffix = 'YOUR_UPLOAD_SUFFIX'
# 设置下载host后缀，普通下载后缀即上传后缀，CDN下载后缀为 .ufile.ucloud.com.cn
download_suffix = 'YOUR_DOWNLOAD_SUFFIX'

compare_handler = filemanager.FileManager(public_key, private_key, upload_suffix, download_suffix)
result=compare_handler.compare_file_etag(bucket,put_key,local_file)
if result==True:
    print('etag are the same!')
else:
    print('etag are different!')
{% endhighlight %}
</div>
