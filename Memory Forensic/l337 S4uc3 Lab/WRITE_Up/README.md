Q1: PCAP: Development.wse.local is a critical asset for the Wayne and Stark Enterprises, where the company stores new top-secret designs on weapons. Jon Smith has access to the website and we believe it may have been compromised, according to the IDS alert we received earlier today. First, determine the Public IP Address of the webserver?
![image 1](image/1.png)
- Dia chi 172.16.0.1 gui 14311 goi tin den 176.16.0.108
- ip.src == 172.16.0.1 && http
![image 2](image/2.png)
=> 74.204.41.73
------------------------------------------------------------------------

Q2: PCAP: Alright, now we need you to determine a starting point for the timeline that will be useful in mapping out the incident. Please determine the arrival time of frame 1 in the "GrrCON.pcapng" evidence file.

- ip.src == 172.16.0.1
![image 3](image/3.png)
=> 22;51;07 UTC
---------------------------------------------------------------------------

Q3: PCAP: What version number of PHP is the development.wse.local server running?
- ip.src == 172.16.0.108 && http
![image 4](image/4.png)
=> 5.3.2
------------------------------------------------------------------------------
Q4: PCAP: What version number of Apache is the development.wse.local web server using?
=> Apache/2.2.14 (Ubuntu)

-------------------------------------------------------------------------------

Q5: IR: What is the common name of the malware reported by the IDS alert provided?

![image 5](image/5.png)
=> zeus

--------------------------------------------------------------------------------

Q7: PCAP: Please identify the Gateway IP address of the LAN because the infrastructure team reported a potential problem with the IDS server that could have corrupted the PCAP

=> 172.16.0.1

------------------------------------------------------------------------------

Q8: IR: According to the IDS alert, the Zeus bot attempted to ping an external website to verify connectivity. What was the IP address of the website pinged?

ip.src == 172.16.0.109

![image 6](image/6.png)

=> 88.198.6.20 

-------------------------------------------------------------------------------
Q9: PCAP: The infrastructure team also requests that you identify the filename of the “.bin” configuration file that the Zeus bot downloaded right after the infection. Please provide the file name?
![image 7](image/7.png)
=> cf.bin

--------------------------------------------------------------------------------

Q10: PCAP: No other users accessed the development.wse.local WordPress site during the timeline of the incident and the reports indicate that an account successfully logged in from the external interface. Please provide the password they used to log in to the WordPress page around 6:59 PM EST?

- Phân tích frame trên trong ngữ cảnh giao thức HTTP cho thấy đây là một yêu cầu POST được gửi tới một trang đăng nhập WordPress (wp-login.php) từ máy nguồn (172.16.0.109) đến máy đích (172.16.0.108), qua cổng 80 (HTTP). 
![image 8](image/8.png)
=> wM812ugu
Time: 22.59.58 UTC

--------------------------------------------------------------------------------

Q11: PCAP: After reporting that the WordPress page was indeed accessed from an external connection, your boss comes to you in a rage over the potential loss of confidential top-secret documents. He calms down enough to admit that the design's page has a separate access code outside to ensure the security of their information. Before storming off he provided the password to the designs page “1qBeJ2Az” and told you to find a timestamp of the access time or you will be fired. Please provide the time of the accessed Designs page?

![image 9](image/9.png)

- 172.16.0.109 connect 172.16.0.108 22:59:58 UTC sau do du lieu bi mat

=> 23:04:04 UTC 

--------------------------------------------------------------------------------

PCAP: What is the source port number in the shellcode exploit? Dest Port was 31708 IDS Signature GPL SHELLCODE x86 inc ebx NOOP