## Preparations
* Interpreter version 
> - Python 3.6

* Link Library 
> - wxpy 
> - baidu_aip
> - RPI.GPIO
<br>
 
 
## Tutorials
### wxpy and tuling API 
* First, a small demo is used to introduce the simple use of ***wxpy*** and ***Tuling API***. <br>
* A few short lines of code are used to realize the automatic reply of Wechat. <br>
* [More about tuling API](https://www.kancloud.cn/turing/www-tuling123-com/718227)
```
#!coding:=utf-8
from wxpy import*

bot = Bot(None,1)
my_friend = ensure_one(bot.search(u'myCar巨无霸'))
tuling = Tuling(api_key = 'your api_key xxxxxxxxxxxxx')
@bot.register()
def auto_reply(msg):
    tuling.do_reply(msg)
embed()
```
### baidu_aip
* Then introduce Baidu Speech Recognition SDK ,its official examples are as follows.<br>
* [Relevant documents](http://ai.baidu.com/docs#/ASR-Online-Python-SDK/top)
```
#encoding:utf-8
from aip import  AipSpeech
 
# 定义常量，此处替换为你自己的应用信息
APP_ID = 'your_app_id'
API_KEY = 'your_api_key'
SECRET_KEY = 'your_secret_key'
 
# 初始化AipSpeech对象
aipSpeech = AipSpeech(APP_ID, API_KEY, SECRET_KEY)
 
# 读取文件
def get_file_content(filePath):
    with open(filePath, 'rb') as fp:
        return fp.read()
 
# 识别本地文件
#目前支持的格式较少，原始 PCM 的录音参数必须符合 8k/16k 采样率、16bit 位深、单声道，
#支持的格式有：pcm（不压缩）、wav（不压缩，pcm编码）、amr（压缩格式）。
result = aipSpeech.asr(get_file_content('C:\Users\shitianxing\Desktop\8k.amr'), 'amr', 8000, {
    'lan': 'zh',
})
print result['result'][0]
```