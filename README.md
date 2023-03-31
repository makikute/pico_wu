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
