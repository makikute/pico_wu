# Write up PicoCTF 2023

## General
1.   Chrono
     - Description: How to automate tasks to run at intervals on linux servers? Additional details will be available after launching your challenge instance.
     - Cách làm:
       - Vào trong thư mục etc sau đó cat crontab để hiện ra flag.
2.   Money-ware
     - Description: Flag format picoCTF{Malwarename}. The first letter of the malware name should be capitalized and the rest lowercase. Your friend just got hacked and has been asked to pay some bitcoins to 1Mz7153HMuxXTuR2R1t78mGSdzaAtNbBWX. He doesn’t seem to understand what is going on and asks you for advice. Can you identify what malware he’s being a victim of?
     - Cách làm:
       - Lên google tra "crypto-currencies abuse databases", vào trang https://www.bitcoinabuse.com/ và search 1Mz7153HMuxXTuR2R1t78mGSdzaAtNbBWX.
       - Sau đó sẽ hiện ra ảnh như sau 
       ![image](https://user-images.githubusercontent.com/129378740/229077513-553206d5-2b27-48ae-908e-eebf59fba8c5.png)
       - Có thể thấy tên của ransomware ở cuối là có flag là picoCTF{Petya}
3.   Permissions
     - Description: Can you read files in the root file? Additional details will be available after launching your challenge instance.
     - Cách làm:
       - Vào thư mục challenge, sau đó ls thì hiện ra file metadata.json
       - cat metadata.json và ra được flag.
4.   repetitions
     - Description: Can you make sense of this file? Download the file [here](https://artifacts.picoctf.net/c/476/enc_flag).
     - Cách làm:
       - Vào trang web https://www.base64decode.org/ và decode đoạn mã tải trong file và ra được flag
5.   useless
     - Description: There's an interesting script in the user's home directory. Additional details will be available after launching your challenge instance.
     - Cách làm:
       - man useless và ra được flag
## Web Exploitation
