TCP
===

| source port     | Destination Port |   |   |   |
|-----------------|------------------|---|---|---|
|           sequence Number          |   |   |   |
|               Ack Number           |   |   |   |
|    misc flags   |       Window     |   |   |   |
| checksum        | Urgent Pointer   |   |   |   |
|             Options                |   |   |   |

* No Ip address, only source and dest port.
* sequence number for re-ordering
* ack for packget loss
* advertised windows for flow ctontrol
* TCP for TCP_FSM

Socket Programming with TCP
=====================
client                								server
SYN_SENT connect()  ---(SYN seq = x)--->    		LISTEN listen()
       ESTABLISED   <---(SYN seq = y, ACK = x + 1) ---| SYN_RCVD
a               |------(ACK= y+1)--------------->   ESTABLISED

          write() ---------seq=x+1 ack = y+1----->  read()
                  <---------ACK = x+2 ----------------|

 FIN_WAIT closed() ---------FIN seq =x+2 ACK=y+1---> CLOSE_WAIT
                   <-------ACK x + 3 ------          LAST_ACK
                   <-------FIN seq = y +1---
                   --------ACK = y + 2 ---------->

3 hand shake for initial: for initial SYN's value
4 for closing: 2* (Fin + ACK)

SYN flood:
happen at step a.
tcp_syncookies, when sync quene is full, resend sequence number AKA cookie.

TIME_WAIT to much? try keepAlive
don't do tcp_tw_resue, or tcp_tw_recycle


Retransmit
=====
calibration timeout
RTT


slide windows
========
Advertised-Window: how much buffer I got to receive data.

receiver
LastByteRead NextByteExpected null LastByteRcvd

sender
LastByteAcked LastByteSend LastByteWritten

Congestion handling
============
don't just resend.

slow start.
congestion avoidance
fast recovery


