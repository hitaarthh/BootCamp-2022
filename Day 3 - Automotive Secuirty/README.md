<div>
<img src="https://img.shields.io/badge/Domain:-Automotive Security%20-black">
<img src="https://img.shields.io/badge/Date-5%20August%202022-green[700]" align="right">

<div align="center"><h1>Automotive Security</h1></div>
</div>

- As the name suggest this field deals in securing the Automotive vehicles as in the coming future Automotive cars are more about Mircocontrollers and electronics rather than mechanical engineering, hence this field entirely focuses on capturing the vulnerabilities in the modern electronic cars and making them more secure and less vulnerable.
- One of the key tool is can-utilis which is based on <a href="https://www.embitel.com/blog/embedded-blog/what-is-can-protocol-stack-why-its-critical-software-solution-for-ecu-communication">CAN BUS</a> protocol.


### What exactly is can-utilis ?

- CAN-utils is a Linux specific set of utilities that enables Linux to communicate with the CAN network on the vehicle. In this way, we can sniff, spoof and create our own CAN packets to pwn the vehicle!

- CAN is a message-based network protocol designed for vehicles.

Here are some <a href="https://www.hackers-arise.com/post/2017/08/08/automobile-hacking-part-2-the-can-utils-or-socketcan#:~:text=can%2Dutils%20is%20a%20Linux,network%20protocol%20designed%20for%20vehicles.">basics</a>, from installation to command line, one can go through to get through with CAN-utilis.

### Tasks assigned: 

- Challenge 1. Get familiar with the CAN-Utils.
- Challenge 2. Sniff out the CAN packets and analyse the changing bits.
- Challenge 3. Dump all CAN packets and save it to file.
- Challenge 4. Replay attack- Play the previously captured packet.
- Challenge 5. The speedometer is limited to 100 Mph. Send a can packet such that the needle goes beyond 100 Mph.

### Solution: 

- Challenge 3:
   - To dump all the can packets into a file we can use ```candump -l vcan0``` command.

- Challenge 4:
   -  For replay attack we can use ```canplayer -I candump-2022-08-05_212858.log``` command.

- Challenge 5: 
  - The  given challenge we need to observe how can packets are changing and with respect to that we need to analyse the change.
  -  After a bit of analysis and research the device acceleration turned out to be 244. So, now the task is to find the can frame which takes the acceleration above 100mph. After some search I got the can frame for acceleration greater than 100mph.
  
  <div align="center"><img width="400" alt="Simulation" src="https://user-images.githubusercontent.com/91147942/186499627-276bfd55-f908-484f-a57d-cc661e21ce2c.png">   </div>
  