CC
Week 1:

1). Types of simulators?

Live: Simulation involving real people operating real systems 
Virtual: Simulation involving real people operating simulated systems
Constructive: Simulation involving simulated people operating simulated systems. 


tcpdump is a common packet analyzer that runs under the command line. It allows the user to display TCP/IP and other packets being transmitted or received over a network to which the computer is attached. 

2). Helper classes vs container:





3). Different types of topoligies?
1). CSMA
2). P2p
3). Wireless

4). Different ms3odules of n?

a). Udp client, server
b). Ip4,6
c). Bulk send


5).How to install specific modules of ns-3?
Move to utils and open  .ns3rc in any editor (use terminal only)

6). Test cases and test suites
Write a file inheriting Testcases class. Test.py --suit =”test suit name”


























…………………………………………………………………………………………………………….Enable support of ASCII traces in first.cc and collect the statistics



Add some code on scratch/first.cc and open it with traceMatrix.jar, ask why removing destroy doesn’t work.
It gives details like Total received packets: 	0
Total dropped packets: 	0
Total simulation time: 	0.0 seconds




Use Valgrind to understand memory leaks using first.cc

`./waf --command-template="valgrind --leak-check=full --show-reachable=yes %s" --run scratch/first.cc`



Set breakpoints at three places in star.cc and list all of them using gdb (GNU Debugger)



For going to gdb terminal
`./waf --command-template="gdb %s" --run scratch/first`


After you come to gdb terminal, 
To set:
`b 3`(number of line)

To run the program:
`r`

To get the info of the program:
`info b`


Print the data type of the variables in star.cc using gdb (GNU Debugger):

`whatis i` i is the variable name



Modify first.cc to support IPv6 addressing

>  ipv6.SetBase (Ipv6Address (":db8:2001:"), Ipv6Prefix (64));
>  UdpEchoClientHelper echoClient (ic.GetAddress (1,1), 9);

//already edited on the scratch/first


Enable support of flow monitor in tcp-bulk-send.cc
he Flow Monitor module goal is to provide a flexible system to measure the performance of network protocols. The module uses probes, installed in network nodes, to track the packets exchanged by the nodes, and it will measure a number of parameters. Packets are divided according to the flow they belong to, where each flow is defined according to the probe’s characteristics (e.g., for IP, a flow is defined as the packets with the same {protocol, source (IP, port), destination (IP, port)} tuple.


Ptr<FlowMonitor> flowMonitor;
  FlowMonitorHelper flowHelper;
  flowMonitor = flowHelper.InstallAll();
 flowMonitor->SerializeToXmlFile("File.xml", true, true);


Ptr<PacketSink> sink1 = DynamicCast<PacketSink> (sinkApps.Get (0));

Compare the congestion window plots for TCP Newreno and TCP Highspeed
Cp examples/tutorial/fifth.cc scratch/fifth.cc and then go to below link
https://www.nsnam.org/docs/release/3.29/tutorial/singlehtml/index.html#running-fifth-cc

Above link tells you how to plot networking using gnuplot

1). So firstly it will plot using newrreno(default).
2).std::string transport_prot = "ns3::TcpHighSpeed";
  TypeId tcpTid;
  NS_ABORT_MSG_UNLESS (TypeId::LookupByNameFailSafe (transport_prot, &tcpTid), "TypeId " << transport_prot << " not found");
  Config::SetDefault ("ns3::TcpL4Protocol::SocketType", TypeIdValue (TypeId::LookupByName (transport_prot)));
//add above lines for changing default to highspeed.


WEEK 4

Write a single flow ns-3 example program with different- ○ TCP Extensions
https://github.com/nsnam/ns-3-dev-git/blob/master/examples/tcp/tcp-variants-comparison.cc
$ ./waf --run="command-line-example --intArg=2 --boolArg --strArg=Hello --cbArg=World"

Queue limits on bottleneck links:
Search for: queueDiscSize
Then change the variables there.

TCP Segment sizes = line 393 tcp variant

GNUPLOT :


> set terminal png size 640,480
> set output "cwnd-tcp-variants-westwood.png"
> plot "TcpWestwood-cwnd.data" using 1:2 title 'Congestion Window' with    linespoints
Plots number of packets vs time


Q3. Window Scale add line before installing internet stack.

Config::SetDefault ("ns3::TcpSocketBase::WindowScaling", BooleanValue (false));




File Location

/example/tcp/bulk send .cc  → bulkSend, ascii tracing, sink

/src/fd-net-device/examples/fd-emu-onoff.cc and star.cc for onoff

/src/netanim/examples/dumbbell-animation.cc
and
/src/point-to-point-layout/model/point-to-point-dumbbell.cc for dumbbell





