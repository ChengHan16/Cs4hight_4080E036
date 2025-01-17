Scrapy crawler ☟
=============
[虛擬環境設定](https://github.com/ChengHan16/Cs4high_4080E036/blob/master/%E5%B0%88%E9%A1%8C%E8%A3%BD%E4%BD%9C%20Thematic%20production%20%E3%80%8A109-2%E3%80%8B/%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83%E6%9E%B6%E8%A8%AD.md)
----------
>檢查目前版本 ： conda –v
>>進行更新命令： conda update conda
>>>查看目前系統已有的虛擬環境： conda env list
>>>>建立一個叫做 myenv 的虛擬環境，且安裝python 3.8的版本
  ：conda create --name myflash01 python=3.8
>>>>>啟動一個新的虛擬環境：conda activate 安裝 scrapyte myflash01
```
安裝 scrapy
  ：pip install scrapy

  ：pip install beautifulsoup4
  
  ：scrapy startproject apple
```
## ★ 爬蟲模組在 apple 資料夾下
### 【●】Items.py 定義資料該怎麼做儲存
### 【●】pipelines.py 定義資料該怎麼做處理
### 【●】settings.py 包含所有設定檔
###  ->接下來所有的爬蟲程式都寫在spidersファイル中に，在spiders下開新檔案定義爬蟲就能開始

# 【●】範例1
## 抓取蘋果即時新聞
### [crawler.py](https://github.com/ChengHan16/Cs4high_4080E036/blob/master/%E5%B0%88%E9%A1%8C%E8%A3%BD%E4%BD%9C%20Thematic%20production%20%E3%80%8A109-2%E3%80%8B/Scrapy%20Python%20Crawler%20%E3%82%B3%E3%83%BC%E3%83%89.md)
```python
import scrapy
from bs4 import BeautifulSoup

class AppleCrawler(scrapy.Spider):
    name = 'apple'
    start_urls = ['https://tw.appledaily.com/realtime/new/']
    def parse(self, response):
        res = BeautifulSoup(response.body)
            for news in res.select('.flex-feature'):
                print news.select('timestamp"')[0].text
```
>完成後 
>> ls 查看目前資料夾
>>> cd apple
>>>> dir 看目前目錄裡的檔案
>>>>> 輸入 scrapy crawl apple 執行

# 【●】範例2
## 清單連結抓取下一層的內容頁面
### crawler.py!
### 先抓取看使否能成功將連結抓取出來
```python
import scrapy
from bs4 import BeautifulSoup
class AppleCrawler(scrapy.Spider):
    name = 'apple'
    start_urls = ['https://tw.appledaily.com/home/']
    def parse(self,response):
        domain = 'https://tw.appledaily.com/'
        res = BeautifulSoup(response.body)
        for news in res.select('.flex-feature'):
            #print (news.select('headline  truncate truncate--3')[0].text)
            #print domain+(news.select('a')[0]['href'])
```
### 可成功抓取後加上 ` domain = 'https://tw.appledaily.com/‘` 讓網址完整

### `yield scrapy.Request(domain + news.select('a')[0]['href'],self.parse_detail)`
### 這段是能夠抓取頁面後抓取`標題、網址`
### yield 是個產生器，在調取後不會立即執行，只有for迴圈在執行呼叫到yield的時候才會繼續
### 透過self.parse_detail 解析內容
### [crawler.py](https://github.com/ChengHan16/Cs4high_4080E036/blob/master/%E5%B0%88%E9%A1%8C%E8%A3%BD%E4%BD%9C%20Thematic%20production%20%E3%80%8A109-2%E3%80%8B/Scrapy%20Python%20Crawler%20%E3%82%B3%E3%83%BC%E3%83%89.md)
```python
import scrapy
from bs4 import BeautifulSoup

class AppleCrawler(scrapy.Spider):
    name = 'apple'
    start_urls = ['https://tw.appledaily.com/home/']
    def parse(self,response):
        domain = 'https://tw.appledaily.com/'
        res = BeautifulSoup(response.body)
        for news in res.select('.flex-feature'):
            #print (news.select('headline  truncate truncate--3')[0].text)
            #print domain+(news.select('a')[0]['href'])
            yield scrapy.Request(domain + news.select('a')[0]['href'],self.parse_detail)
    def parse_detail(self,response):
        res = BeautifulSoup(response.body)
        res.select('#h1')[0].text
```
![結果](https://github.com/ChengHan16/Cs4high_4080E036/blob/master/image/2%E7%B5%90%E6%9E%9C1.PNG)
### Debugger訊息從清單連結下去抓取成功抓取後會有顯示(200)的code

<br>

# Website video download crawler ☟
> ## AV.py
```python
from Module import  net_fn

class AV:

    def __init__(self):
        self.Net = net_fn.Net()

    def Read_Home(self):
        url = "https://airav.cc/"
        header = header = "Host: airav.cc###Connection: keep-alive###Upgrade-Insecure-Requests: 1###User-Agent: Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/67.0.3396.99 Safari/537.36###Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8###Accept-Encoding: gzip, deflate, br###Accept-Language: zh-TW,zh;q=0.9,en-US;q=0.8,en;q=0.7"
        rs = self.Net.Get(url=url,header_string=header)
        data = rs.content.decode()
        print(data)

        if __name__ == "__main__":
            obj = AV()
            obj.Read_Home()
```
> ## net_fn.py
```python
# -*- coding: UTF-8 -*-
import requests
import re
import urllib3
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

class Net:
    def __init__(self):
        pass

    def Get(self,url,header_string="",cookie="",SSL_verify=0):

        header_dict = self.get_header_dict(header_string)


        rs = requests.get(url,headers=header_dict,verify=SSL_verify,cookies=cookie)

        return rs
    def Download(self,url,local_filename=None):
        if local_filename == None:
            local_filename = url.split('/')[-1]
        # NOTE the stream=True parameter
        r = requests.get(url, stream=True)
        with open(local_filename, 'wb') as f:
            for chunk in r.iter_content(chunk_size=1024):
                if chunk:  # filter out keep-alive new chunks
                    f.write(chunk)
                    # f.flush() commented by recommendation from J.F.Sebastian
        return local_filename

    # 將文字header變成字典
    def get_header_dict(self,string):
        string = string.replace("https://", "https#")
        string = string.replace("http://", "http#")
        arr = string.split("###")

        end = dict()
        for item in arr:
            if item != "":
                temp = item.split(":")
                temp[1] = temp[1].replace("https#", "https://")
                temp[1] = temp[1].replace("http#", "http://")
                end[temp[0].strip()] = temp[1].strip()
        return end

    # 用正則表達式取得文字
    def preg_get_word(self,preg_word, num, text, mode=0):

        try:

            patte = re.compile(preg_word)
            grk = patte.search(text)

            if num == "all":
                bb = re.findall(preg_word, text)
                rs = bb
                if len(rs) == 0:
                    rs = "empty_data"
            else:
                rs = grk.group(num)
                if mode == "test":
                    print("正則表達式:" + preg_word + "\n 結果:" + rs.encode("utf-8"))

        except:

            rs = "empty_data"

        return rs


if __name__ == "__main__":
    obj = Net()
    #模擬測試
    header_str = "Host: class.ruten.com.tw###Connection: keep-alive###Cache-Control: max-age=0###Upgrade-Insecure-Requests: 1###User-Agent: Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/67.0.3396.99 Safari/537.36###Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8###Accept-Encoding: gzip, deflate###Accept-Language: zh-TW,zh;q=0.9,en-US;q=0.8,en;q=0.7###If-Modified-Since: Mon, 30 Jul 2018 19:28:15 GMT###"
    url = "http://class.ruten.com.tw/user/index00.php?s=dodo790119&d=5216722&o=0&m=1"
    rs = obj.Get(url,header_string=header_str)
    print(rs.content.decode())
    # print(rs)
```
