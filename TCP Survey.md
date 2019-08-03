---


---

<h1 id="tcp-overview">1 TCP Overview</h1>
<p>TCP protocal has the following features:</p>
<ol>
<li><strong>point to point</strong>: one sender servers one receiver</li>
<li><strong>Connection-oriented</strong>: The sender&amp;receiver pair exchange control messages first to configure the initial states of the connection.</li>
<li><strong>Full duplex data delivery</strong>: One same connection delivers bi-directional data flow.</li>
<li><strong>Reliable, in-order byte stream delivery</strong>:
<ul>
<li>No message boundaries</li>
<li>Both sender and receiver must buffer data</li>
</ul>
</li>
<li><strong>Flow controlled</strong>: TCP protocol is capable of preventing senders from flood the receivers.</li>
<li><strong>Congestion control</strong>: Reduce potential jam in the network.</li>
</ol>
<h1 id="define-one-tcp-connection">2 Define one TCP connection</h1>
<p>TCP utilizes one 4-tuples to define one connection, which contains:</p>
<ol>
<li>Local host address</li>
<li>Local port</li>
<li>Remote host address</li>
<li>Remote port</li>
</ol>
<p>The two endpoints of one connection keep the states of the ongoing communication. Here are some kind of states:</p>
<ul>
<li><em>Sequence</em>: for data sent, received and acknowledged.</li>
<li><em>Retransmission</em> timer</li>
<li><em>Send window</em>: the amount of data unacknowledged.</li>
<li><em>Congestion window</em></li>
<li>…</li>
</ul>
<h1 id="exceptions">3 Exceptions</h1>
<ol>
<li><strong>Packet loss</strong></li>
<li><strong>Packet duplicated</strong></li>
<li><strong>Packet re-ordered</strong></li>
<li><strong>Packet delayed arbitrarily long</strong></li>
<li><strong>Port reused</strong> &gt; A later connection must not mistake packets from an earlier connection as its own.</li>
</ol>
<h1 id="tcp-segment-format">4 TCP segment format</h1>
<p><img src="https://github.com/Guoao-Sun/Network-Stack/blob/master/TCP/TCP_Segment_Format.svg" alt="TCP Segment Format"></p>
<h1 id="tcp-connection-establishment--close">5 TCP connection establishment &amp; close</h1>
<ol>
<li><strong>TCP connection establishment</strong>: Three way handshake.</li>
<li><strong>TCP connection close</strong>: Four way handshake.</li>
</ol>
<h2 id="three-way-handshake">5.1 Three-way Handshake</h2>
<p>In this phase, the two ends initializes tcp control variables which consist of initial sequence number and buffer size (aka. Receive Window).<br>
<img src="https://github.com/Guoao-Sun/Network-Stack/blob/master/TCP/TCP-Three-way%20Handshake.svg" alt="Three-way handshake"><br>
<strong>Pipeline</strong>:</p>
<ol>
<li>Client sends TCP “SYN” segment to server.
<ul>
<li>Initialize sequence number.</li>
<li>Carry no data.</li>
</ul>
</li>
<li>Server receivers SYN and replies with SYN-ACK and SYN segment.</li>
<li>Client receive SYN-ACK and SYN segment and sends SYN-ACK segment back to server.
<ul>
<li>This segment may carries data.</li>
</ul>
</li>
</ol>
<h2 id="four-way-handshake-connection-close">5.2 Four-way Handshake (Connection Close)</h2>
<p><img src="https://github.com/Guoao-Sun/Network-Stack/blob/master/TCP/TCP-Four-way%20Handshake.svg" alt="TCP-Four-way Handshake"><br>
<strong>Pipeline</strong>:</p>
<ol>
<li>One endpoint A sends “FIN” segment to the other end (B) of the same connection.</li>
<li>B receives “FIN” and acknowledges A back with “FIN-ACK”.</li>
<li>When it is ready, B generates one “FIN” packet and sends to A.</li>
<li>A receives “FIN” and ACKs it back.</li>
</ol>

