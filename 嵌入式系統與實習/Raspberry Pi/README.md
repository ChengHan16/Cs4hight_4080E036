### - Google - drive
https://drive.google.com/drive/u/1/folders/1Jk-4lyOcSUsEbsoeJve9QuG1U4UxBnCg
### - 參考資料
https://hackmd.io/@ShenTengTu/r1baxV4pQ

### Raspberry Pi Address ：192.168.2.183

### - ASUS AP Password
> ssid = " ASUSLAB "; <br><br>
> password = " ASUSASUS ";
------------------------
### - 操作問題
可以輸入Python的關鍵字，例如print來獲得其相關的幫助。<br> 也可以輸入模組名或主題來獲取幫助資訊。如果要退出幫助資訊，可以按Q鍵。<br> 如果要退出互動式shell的幫助，可以按住Ctrl鍵，然後按一下D鍵，這個組合鍵寫作Ctrl+D。<br> 或者，也可以輸入quit並按下回車鍵來退出。 當用完了Python互動式shell後，只需輸入exit()然後按回車鍵，Python就會退出互動式shell，並回到命令列。 
 - Url： https://itw01.com/FQ76E54.html
------------------------
### - Note
```
useradd --help
useradd -m
sudo adduser -m 4080E036
useradd -m 4080E036
```
------------------------
### - 設定使用者
```
sudo useradd -m 4080E036
ls /home/ -la
groups 4080E036
```
------------------------
###  - 預設帳密
```
pi
raspberry
```
------------------------
###  - 更新時間設定
```
timedatectl
sudo timedatectl set-timezone Asia/Taipei
sudo timedatectl set-ntp 0
sudo timedatectl set-time "2021-11-23 11:17"
sudo timedatectl set-ntp 1
```
------------------------
###  - 更新套件庫"名稱"
```
sudo apt update -y
```
###  - python 權限問題設定
```
錯誤訊息
Traceback (most recent call last):
  File "/home/4080E036/Program_ch3/RGBLED/test.py", line 10, in <module>
    led = RGBLED(11,13,15,mode=0)
  File "/home/4080E036/Program_ch3/RGBLED/RGBLED.py", line 21, in __init__
    GPIO.setup(self.__redpin, GPIO.OUT)
RuntimeError: No access to /dev/mem.  Try running as root!

需再自己使用者設定
sudo usermod -a -G gpio 使用者帳號
sudo chown root.gpio /dev/gpiomem
sudo chmod g+rw /dev/gpiomem
```
### - su: 驗證失敗
```
sudo passwd root
新 密碼: 0000
------------------
連接不到樹莓派？
先檢查一下主機地址和樹莓派用戶名及密碼是否填寫正確
+ 一般樹莓派買了默認用戶名是pi，密碼是raspberry
+ 主機那裏加上協議如：sftp://192.xxx.xxx.xxx
也是最重要的一個點，上傳文件給樹莓派時，樹莓派切換至root下
+ 一般樹莓派買來如果沒有開啓過root的話，先設置一下root密碼
> sudo passwd root
(一般讓你輸兩次密碼)
再切入root下，su root 並輸入剛設定的密碼即可
至此，再次使用filezilla就能上傳樹莓派了~
```
----
> https://www.twblogs.net/a/5ca887b3bd9eee5b1a077c5d
## Error
### - 找不到 Adafruit_Sensor.h
```
將 https://raw.githubusercontent.com/adafruit/Adafruit_Sensor/master/Adafruit_Sensor.h 檔案放置下位置
C:\Users\User\Documents\Arduino\libraries\DHT_sensor_library
```
### - winSCP：無權訪問。 錯誤碼：3 伺服器傳回的錯誤訊息：Permission denied（真正解決方案）
> https://blog.csdn.net/qq_31201781/article/details/78919914
