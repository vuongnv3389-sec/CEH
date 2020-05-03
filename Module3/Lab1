##Hping3
#Description:
UDP and TCP packet crafting techniques using Hping3
Practicing Scanning network Procedure by Hping3 to determine all possible open ports, live hosts and services running

#Task1: Lanch Hping3
root@kali:~# hping3 10.239.184.1 -c 3
HPING 10.239.184.1 (eth0 10.239.184.1): NO FLAGS are set, 40 headers + 0 data bytes
len=46 ip=10.239.184.1 ttl=64 DF id=47219 sport=0 flags=RA seq=0 win=0 rtt=3.7 ms
len=46 ip=10.239.184.1 ttl=64 DF id=47318 sport=0 flags=RA seq=1 win=0 rtt=11.2 ms
len=46 ip=10.239.184.1 ttl=64 DF id=47365 sport=0 flags=RA seq=2 win=0 rtt=10.0 ms
--- 10.239.184.1 hping statistic ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 3.7/8.3/11.2 ms
root@kali:~# 

 =>Explain: hping3 <IP adress of the target machine> -c <Numbers of packet is going to be send to the target machine>
 =>Explain: Send 3 (-c 3) packets to the target machine (10.239.184.1)

root@kali:~# hping3 --scan 1-6000 -S 10.239.184.1
Scanning 10.239.184.1 (10.239.184.1), port 1-6000
6000 ports to scan, use -V to see all the replies
+----+-----------+---------+---+-----+-----+-----+
|port| serv name |  flags  |ttl| id  | win | len |
+----+-----------+---------+---+-----+-----+-----+
   22 ssh        : .S..A...  64     0 29200    46
   53 domain     : .S..A...  64     0 29200    46
   80 http       : .S..A...  64     0 29200    46
All replies received. Done.
Not responding ports: 
root@kali:~#

 =>Explain: "--scan" parameter defines the port range to scan and "-S" paramater represents SYN flag
 =>Explain: determine open ports from  1 to 6000 port (--scan 1-6000) by sending SYN Packet (-S) to the target machine (10.239.184.1)
  
root@kali:~# hping3 --udp --rand-source 10.239.184.1 --data 500 
HPING 10.239.184.1 (eth0 10.239.184.1): udp mode set, 28 headers + 500 data bytes
=>Explain: Performing UDP parket (--udp) crafting

#Task 2: Send TCP SYN Request
root@kali:~# hping3 -S -p 80 -c 5 10.239.184.1
HPING 10.239.184.1 (eth0 10.239.184.1): S set, 40 headers + 0 data bytes
len=46 ip=10.239.184.1 ttl=64 DF id=0 sport=80 flags=SA seq=0 win=29200 rtt=7.9 ms
len=46 ip=10.239.184.1 ttl=64 DF id=0 sport=80 flags=SA seq=1 win=29200 rtt=11.4 ms
len=46 ip=10.239.184.1 ttl=64 DF id=0 sport=80 flags=SA seq=2 win=29200 rtt=15.0 ms
len=46 ip=10.239.184.1 ttl=64 DF id=0 sport=80 flags=SA seq=3 win=29200 rtt=9.8 ms
len=46 ip=10.239.184.1 ttl=64 DF id=0 sport=80 flags=SA seq=4 win=29200 rtt=3.9 ms

--- 10.239.184.1 hping statistic ---
5 packets transmitted, 5 packets received, 0% packet loss
round-trip min/avg/max = 3.9/9.6/15.0 ms
root@kali:~#
=>Explain: Send 5 (-c 5) SYS-TCP (-S) requests through port 80 (-p 80) to the target machine (10.239.184.1)

#Task3: perform TCP flooding
root@kali:~# hping3 --flood 10.239.184.1
HPING 10.239.184.1 (eth0 10.239.184.1): NO FLAGS are set, 40 headers + 0 data bytes
hping in flood mode, no replies will be shown
^C
--- 10.239.184.1 hping statistic ---
1052409 packets transmitted, 0 packets received, 100% packet loss
round-trip min/avg/max = 0.0/0.0/0.0 ms

==> On the same network, another machine cannot go outside the internet (from 6 request) while attack machine is performing TCP flooding
C:\>ping 8.8.8.8 -t

Pinging 8.8.8.8 with 32 bytes of data:
Reply from 8.8.8.8: bytes=32 time=716ms TTL=53
Reply from 8.8.8.8: bytes=32 time=41ms TTL=53
Reply from 8.8.8.8: bytes=32 time=105ms TTL=53
Reply from 8.8.8.8: bytes=32 time=48ms TTL=53
Reply from 8.8.8.8: bytes=32 time=1555ms TTL=53
Request timed out.
No resources.
No resources.

Ping statistics for 8.8.8.8:
    Packets: Sent = 8, Received = 5, Lost = 3 (37% loss),
Approximate round trip times in milli-seconds:
    Minimum = 41ms, Maximum = 1555ms, Average = 493ms
Control-C
^C
C:\>






  

