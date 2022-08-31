# Socket Programming For Video Streaming

## Abstract:

Upon client request, the server directs a video file to the client by sending the file into a socket. TCP socket connections are used in our project. Before sending the video file into the network, the file is segmented, and the segments are typically encapsulated with special headers appropriate for video traffic.

## Flowchart for the Server and Client Process:

![Account ownership flow](https://user-images.githubusercontent.com/76071184/187624753-e5006865-3973-4d1f-b371-8c96dfdae687.png)

## Advantages of Using Socket Programming:

1) Using socket programming in TCP guarantees the delivery of data to the destination router, thus making it reliable.

2) The speed of transmission is due to reordering and retransmission.

3) If there's a missing packet which causes a glitch in the video, TCP will let the packet to be retransmitted. YouTube/Netflix/Hulu etc, adjusts video quality based on network congestion, and this can be detected by TCP.

4) It also performs error checking and error recovery. It offers extensive error checking mechanisms using flow control and acknowledgment of data.

## Limitations:

1) If the client demands a bandwidth more than the sender could provide and there is a data loss, then latency is unavoidable. Now if we think of a live video streaming, when packet loss occurs, the performance of the live streaming will be heavily deteriorated because the protocol will be busy retransmitting the lost packets. This will result in the viewer lagging behind than what is actually being streamed on the video live.

2) TCP buffers the unacknowledged segments for every client. In some cases this is undesirable, such as TCP streaming for very popular live events because the list of simultaneous clients (and buffering requirements) are large in this case. Pre-recorded video-casts typically don't have as much of a problem with this because viewers tend to stagger their replay activity.

3) IP multicast significantly reduces video bandwidth requirements for large audiences; multicast requires UDP (and is incompatible with TCP). 

4) For real time videos, using UDP has the merit that it's faster and has lower overhead, a few packets dropped in between doesn’t matter.
