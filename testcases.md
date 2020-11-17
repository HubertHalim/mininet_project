### Task 1 MininetTopo

```shell
sudo python mininetTopo.py # expect to see exact number of devices are launched.
```

### Task 2 PingAll

```shell
pingall # expect to see all hosts ping each other successfully
```

### Task 3 Fault Tolerance

```shell 
pingall # same
h1 ping h4 # connected
link s1 s2 down # make the link down
h1 ping h4 # timeout, but it will be reconnected after a while
```

### Task 4 Firewall

h5 to h2 on port 80

```shell
h2 iperf -s -p 80 & # start a iperf server on port 80
h5 iperf -c h2 -p 80 # no response
h1 iperf -c h2 -p 80 # local 10.0.0.1 port XXX connected with 10.0.0.2 port 80
h7 iperf -c h2 -p 80 # local 10.0.0.7 port XXX connected with 10.0.0.2 port 80
```

```shell
h2 iperf -s -p 8080 & # start a iperf server on port 8080
h5 iperf -c h2 -p 8080 # local 10.0.0.5 port XXX connected with 10.0.0.2 port 8080
```

h7 on port 4001

```shell
h7 iperf -s -p 4001 &
h5 iperf -c h7 -p 4001 # no response
h1 iperf -c h7 -p 4001 # no response
```

```shell
h7 iperf -s -p 8080 & # start a iperf server on port 8080
h5 iperf -c h2 -p 8080 # local 10.0.0.5 port XXX connected with 10.0.0.7 port 8080
```

### Task 5 Premium Traffic

premium to premium

```shell
iperf h7 h8 # ~ 10mb/s
```

normal to premium

```shell
iperf h1 h2 # ~ 5mb/s or ~10mb/s
iperf h2 h1 # ~ 5mb/s or ~10mb/s
```

normal to normal

```shell
iperf h2 h5 # ~ 5mb/s
```

