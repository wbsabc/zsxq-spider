# zsxq-spider

爬取知识星球，并制作 PDF 电子书。[https://www.zsxq.com/](https://www.zsxq.com/)

## 简介

本代码参考了网上的其他开源代码和一些文章。  
我需要生成一个可以真正方便我浏览知识星球中历史内容的 PDF，但是感觉大家只偏重于技术实现，不太满足我的需求，所以就自己再加工了一版。  
目前生成的 PDF 至少能够让自己满意了。

## 功能

* 支持下载图片并写入 PDF。
* 支持 PDF 中显示链接。
* 支持下载评论。
* 可控制只下载精华内容或下载全部内容。
* 支持按时间区间下载。

## 环境

* Python 3.7 测试通过。
* 安装 wkhtmltox，[https://wkhtmltopdf.org/downloads.html](https://wkhtmltopdf.org/downloads.html)。安装后将 bin 目录加入到环境变量。
* 安装相应依赖：pip install pdfkit
* 安装 BeautifulSoup：pip install BeautifulSoup4
* 安装 Requests：pip install requests

## 用法

参考以下配置内容
```python
ZSXQ_ACCESS_TOKEN = '86D82CA0-301A-3797-8528-D09322903A59_6DF24A4ED3558CD4'    # 登录后Cookie中的Token（必须修改）
USER_AGENT = 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:79.0) Gecko/20100101 Firefox/79.0'    # 登录时使用的User-Agent（必须修改）
GROUP_ID = '452445212848'                         # 知识星球中的小组ID
PDF_FILE_NAME = '电子书.pdf'                       # 生成PDF文件的名字
DOWLOAD_PICS = True                               # 是否下载图片 True | False 下载会导致程序变慢
DOWLOAD_COMMENTS = True                           # 是否下载评论
ONLY_DIGESTS = False                              # True-只精华 | False-全部
FROM_DATE_TO_DATE = False                         # 按时间区间下载
EARLY_DATE = '2017-05-25T00:00:00.000+0800'       # 最早时间 当FROM_DATE_TO_DATE=True时生效 为空表示不限制 形如'2017-05-25T00:00:00.000+0800'
LATE_DATE = '2018-05-25T00:00:00.000+0800'        # 最晚时间 当FROM_DATE_TO_DATE=True时生效 为空表示不限制 形如'2017-05-25T00:00:00.000+0800'
DELETE_PICS_WHEN_DONE = True                      # 运行完毕后是否删除下载的图片
DELETE_HTML_WHEN_DONE = True                      # 运行完毕后是否删除生成的HTML
COUNTS_PER_TIME = 30                              # 每次请求加载几个主题 最大可设置为30
DEBUG = False                                     # DEBUG开关
DEBUG_NUM = 120                                   # DEBUG时 跑多少条数据后停止 需与COUNTS_PER_TIME结合考虑
SLEEP_FLAG = True                                 # 请求之间是否SLEEP避免请求过于频繁
SLEEP_SEC = 2                                     # SLEEP秒数 SLEEP_FLAG=True时生效
```
ZSXQ_ACCESS_TOKEN 需要自己在浏览器里登录一次，然后查看Cookie中的值。  
USER_AGENT 需要保证和登录时的一致。  
GROUP_ID 可以从浏览器地址栏中看到，或者截取网络请求。  
修改完以上参数后，cd到文件夹所在路径，运行crawl.py。  

## 说明

1. 请大家合理使用本代码，不要随意传播生成的PDF，保护网站及作者的合法权益。
2. 爬虫会对网站性能造成一定影响，请勿频繁使用，在必要时合理使用，大家都是去学习知识的，体谅一下吴老板。
