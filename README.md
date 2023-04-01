# Write up PicoCTF 2023

## General
1.   ***Chrono***
     - Description: How to automate tasks to run at intervals on linux servers?
     - Cách làm:
       - Vào trong thư mục etc sau đó cat crontab để hiện ra flag.
2.   ***Money-ware***
     - Description: Flag format picoCTF{Malwarename}. The first letter of the malware name should be capitalized and the rest lowercase. Your friend just got hacked and has been asked to pay some bitcoins to 1Mz7153HMuxXTuR2R1t78mGSdzaAtNbBWX. He doesn’t seem to understand what is going on and asks you for advice. Can you identify what malware he’s being a victim of?
     - Cách làm:
       - Lên google tra "crypto-currencies abuse databases", vào trang https://www.bitcoinabuse.com/ và search 1Mz7153HMuxXTuR2R1t78mGSdzaAtNbBWX.
       - Sau đó sẽ hiện ra ảnh như sau 
       ![image](https://user-images.githubusercontent.com/129378740/229077513-553206d5-2b27-48ae-908e-eebf59fba8c5.png)
       - Có thể thấy tên của ransomware ở cuối là có flag là picoCTF{Petya}
3.   ***Permissions***
     - Description: Can you read files in the root file? 
     - Cách làm:
       - Vào thư mục challenge, sau đó ls thì hiện ra file metadata.json
       - cat metadata.json và ra được flag.
4.   ***repetitions***
     - Description: Can you make sense of this file? Download the file [here](https://artifacts.picoctf.net/c/476/enc_flag).
     - Cách làm:
       - Vào trang web https://www.base64decode.org/ và decode đoạn mã tải trong file và ra được flag
5.   ***useless***
     - Description: There's an interesting script in the user's home directory. 
     - Cách làm:
       - man useless và ra được flag
## Web Exploitation
1.   ***findme***
     - Description: Help us test the form by submiting the username as test and password as test! 
     - Cách làm:
       - Log in vào bằng tk mk là test và test!
       - Sau đó trên burp hiện ra 2 đường link, decode 2 đường link đấy ra và ra được flag.
       ![image](https://user-images.githubusercontent.com/129378740/229084103-995501f9-75be-43c3-b6ba-0c1bf5b46b8b.png)
       ![image](https://user-images.githubusercontent.com/129378740/229084201-057d8983-8e04-4a52-81f8-d34631341bf6.png)
2.   ***MatchTheRegex***
     - Description: How about trying to match a regular expression.
     - Cách làm:
       - Đọc source code mình thấy 1 dòng comment 7 ký tự bắt đầu bằng p kết bằng f khá là sú nên mình nhập ngay picoctf
       ![image](https://user-images.githubusercontent.com/129378740/229085188-13508fee-739d-43f1-909a-171bbd64972f.png)
       - Nhập xong và hiện ra flag.   
3.   ***SOAP***
     - Description: The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?
     - Cách làm:
       - Có thể thấy được là khi chọn 1 chỗ trên web thì trên burp sẽ trả về 1 script xml.
       ![image](https://user-images.githubusercontent.com/129378740/229086307-48b1d956-04ad-402c-94d8-d72df1626fa1.png)
       - Vì hint có nói đến XXE nên mình đã thử nhập payload theo web https://portswigger.net/web-security/xxe.  
       ![image](https://user-images.githubusercontent.com/129378740/229089150-c60d53b8-fd0f-439c-a027-b8e0a3b1278a.png)
       - Send và ra flag.
4.   ***More SQLi***
     - Description: Can you find the flag on this website.
     - Cách làm:
       - Sử dụng payload ' OR TRUE -- 
       ![image](https://user-images.githubusercontent.com/129378740/229091765-bf37755f-860e-412a-a21a-c2dedcad2c23.png)
       - Flag đã hiện ra.
## Cryptography
1. ***HidetoSee***
     - Description: How about some hide and seek heh? Look at this image [here](https://artifacts.picoctf.net/c/239/atbash.jpg).
     ![atbash](https://user-images.githubusercontent.com/129378740/229092762-9d8f4c76-d665-4aa2-8fc3-ba6804e122f5.jpg)
     - Cách làm:
       - Sử dụng tool steghide bằng câu lệnh steghide extract -sf Desktop/atbash.jpg  
       - Sau đó tool sẽ extract ra 1 file txt mới có chưa thông tin bị ẩn đi
       - Lên [atbash cipher](https://www.dcode.fr/atbash-cipher) decode và ra được flag.
2. ***ReadMyCert***
     - Description: How about we take you on an adventure on exploring certificate signing requests. Take a look at this CSR file [here](https://artifacts.picoctf.net/c/420/readmycert.csr).
     - Cách làm:
       - Lên trang web [csr decode](https://www.sslshopper.com/csr-decoder.html) để đọc file tải về và ra được flag
       ![image](https://user-images.githubusercontent.com/129378740/229095858-0f090867-211d-47ad-9d47-a457fc332a23.png)
3. ***Rotation***
     - Description: You will find the flag after decrypting this file. Download the encrypted flag [here](https://artifacts.picoctf.net/c/388/encrypted.txt).
     - Cách làm:
       - Lên trang web [ceasar cipher decode](https://www.dcode.fr/caesar-cipher) copy đoạn text được mã hoá và ra flag.   
## Reverse Engineering
1. ***Ready Gladiator 0***
     - Description: Can you make a CoreWars warrior that always loses, no ties? Your opponent is the Imp. The source is available [here](https://artifacts.picoctf.net/c/310/imp.red). If you wanted to pit the Imp against himself, you could download the Imp and connect to the CoreWars server like this: nc saturn.picoctf.net 63422 < imp.red
     - Cách làm:
       - Mình gõ bừa như hình thì bỗng dưng ra flag=)
       ![image](https://user-images.githubusercontent.com/129378740/229255994-1ed946b1-c371-4f7f-970b-c7b9d525aa04.png)
2. ***Reverse***
     - Description: Try reversing this file? Can ya? I forgot the password to this [file](https://artifacts.picoctf.net/c/275/ret). Please find it for me?
     - Cách làm:
       - Mình mở file trên ida, sau đó ấn vào main, ấn f5 để compile file và ra flag.  
3. ***Safe Opener 2***
     - Description: What can you do with this file? I forgot the key to my safe but this [file](https://artifacts.picoctf.net/c/287/SafeOpener.class) is supposed to help me with retrieving the lost key. Can you help me unlock my safe?
     - Cách làm:
       - Mở file trên notepad và ra flag.
4. ***Timer***
     - Description: You will find the flag after analysing this apk. Download [here](https://artifacts.picoctf.net/c/449/timer.apk).
     - Cách làm:
       - Mở file trên tool jadx và search từ khoá picoctf để ra flag.
       ![image](https://user-images.githubusercontent.com/129378740/229256341-b0a534cc-a359-49e6-a7d6-8f6053ef0f89.png)
## Forensics
1. ***hideme***
     - Description: Every file gets a flag. The SOC analyst saw one image been sent back and forth between two people. They decided to investigate and found out that there was more than what meets the eye [here](https://artifacts.picoctf.net/c/256/flag.png).
     - Cách làm:
       - Sử dụng binwalk để extract các file ẩn thì được 1  file secret.
       - Mở file và ra được flag.
       ![image](https://user-images.githubusercontent.com/129378740/229256792-c79b1766-8b8c-4ee8-920c-a82dd66c337f.png)
2. ***PcapPoisoning***
     - Description: How about some hide and seek heh? Download this [file](https://artifacts.picoctf.net/c/373/trace.pcap) and find the flag.
     - Cách làm:
       - Mở file trên wireshark, sort theo length và ra được flag
       ![image](https://user-images.githubusercontent.com/129378740/229256981-3d038ae3-4e64-4e96-a9f4-46275d8a5adf.png)
3. ***who is it***
     - Description: Someone just sent you an email claiming to be Google's co-founder Larry Page but you suspect a scam. Can you help us identify whose mail server the email actually originated from? Download the email file [here](https://artifacts.picoctf.net/c/499/email-export.eml). Flag: picoCTF{FirstnameLastname}
     - Cách làm:
       - Mở file trên outlook, sau đó chọn property thì mình tìm được địa chỉ ip của người gửi
       ![image](https://user-images.githubusercontent.com/129378740/229257161-52fda7bb-dd3d-4ed2-84ff-f626d474ab28.png)
       - Sau đó mình lên tran web https://www.whatismyip.com/ip-whois-lookup/ để search địa chỉ ip đấy và có được tên của người gửi.
       ![image](https://user-images.githubusercontent.com/129378740/229257250-368749b3-6f69-4d51-b6e8-f749c885b665.png)
       - Copy tên gười gửi là có flag là picoCTF{WilhelmZwalina}.
4. ***FindAndOpen***
     - Description: Someone might have hidden the password in the trace file. Find the key to unlock this [file](https://artifacts.picoctf.net/c/492/flag.zip). [This tracefile](https://artifacts.picoctf.net/c/492/dump.pcap) might be good to analyze.
     - Cách làm:
       - Đầu tiên mở file pcap trên wiresahrk.
       - Sau khi xem qua các packet thì em phát hiện 1 đoạn dã được mã hoá khá là sú. 
       ![image](https://user-images.githubusercontent.com/129378740/229257481-fcc7593d-aedc-4f58-9bc7-fb1160d358ad.png)
       - Copy đoạn đấy lại và xoá đi header ở đầu rồi đưa lên [base64 decode](https://www.base64decode.org/) để giải mã đoạn đó và mình có passwork của file zip.
       ![image](https://user-images.githubusercontent.com/129378740/229257541-3b7138a0-5c79-4b28-82ca-15707ae4b267.png)
       - Điền password vào file zip và có đuọc flag.
       ![image](https://user-images.githubusercontent.com/129378740/229257596-68b3dc83-7c69-418e-831a-db1d6656334f.png)
5. ***MSB***
     - Description: This image passes LSB statistical analysis, but we can't help but think there must be something to the visual artifacts present in this image... Download the image [here](https://artifacts.picoctf.net/c/306/Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png)
     - Cách làm:
       - Sử dụng tool stegsolve sau đó chọn extract data rồi set RGB thành 777 thì dược 1 đoạn text như sau.
       ![image](https://user-images.githubusercontent.com/129378740/229257991-889cbc7d-2f26-4168-8e03-e71f067d3b25.png)
       - Lưu file text lại và search picoctf và ra được flag.
       ![image](https://user-images.githubusercontent.com/129378740/229258021-a4a3a655-e60a-432a-9158-333b860a21f5.png)
