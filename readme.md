Question and Answers - 

Q1 . Why do you see a difference in webpage fetch times with short and large router 
buffers? 

Ans - > When the queue size is substantial, TCP will consistently double its congestion 
window and continue sending an increasing number of packets. However, due to a 4ms delay
for each packet, the retrieval time becomes extended in situations with a large queue size.
Conversely, in cases of a small queue size, TCP is compelled to reduce its congestion window
by half whenever the threshold is reached. This results in a quicker transmission of webpage 
fetch requests.

Q2 . Bufferbloat can occur in other places such as your network interface card (NIC). 
Check the output of ifconfig eth0 on your VirtualBox VM. What is the 
(maximum) transmit queue length on the network interface reported by ifconfig? For 
this queue size, if you assume the queue drains at 100Mb/s, what is the maximum 
time a packet might wait in the queue before it leaves the NIC?

Ans - > With a transmit queue length setting of 1000 in Mininet, which permits a buffer
for 1000 packets, assuming each packet size is 1500 bytes, the total buffered data amounts
to 1.5 * 10^6 bytes. Considering a network speed of 100 Mbps (1.25 * 10^7 bytes/s), the time
required to transmit this buffered data is approximately 0.12 seconds.

Q3 . How does the RTT reported by ping vary with the queue size? Describe the relation 
between the two. 

ANS - > As the queue size increases, the round-trip time (RTT) also expands. This relationship 
is governed by the formula RTT = queue_size * propagation_delay. Since the propagation delay
remains constant, it's evident that as the queue size grows, the RTT lengthens accordingly.

Q4 . Identify and describe two ways to mitigate the bufferbloat problem

ANS - > There are two approaches to address this situation. The first involves adjusting the 
maximum queue size, effectively constraining the buffer size within the context of a network
with limited bandwidth. This can lead to a reduction in round-trip time (RTT). The second approach
entails implementing active queue management mechanisms like Random Early Detection (RED), where 
packets are dropped at an early stage based on a configurable probability parameter.

Q5 . Describe how and why your results change when you re-run the emulation. 

Ans - > When you re-run the emulation with these strategies implemented, your results are likely
to show reduced latency and improved network responsiveness. By controlling the queue size and using
active queue management techniques, you create an environment where congestion is better managed, 
leading to a more efficient and responsive network.
