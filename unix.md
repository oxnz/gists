UNIX
----

### Get Lines in Middle of a File

    sed -n '8000000,8001000p' /tmp/uid1.txt


### Find processes hold tcp/10000

    lsof -i:10000
    COMMAND  PID   USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
    ssh     7570 ahorne    6u  IPv6 0xffffff8014a33800      0t0  TCP localhost:ndmp (LISTEN)
    ssh     7570 ahorne    7u  IPv4 0xffffff8015f03c20      0t0  TCP localhost:ndmp (LISTEN)


### Tunnel to a server

#### Simple Tunnel

The '-Nf' is not essential but states no command being executed and to run in background. Example shows a MySql tunnel:

    ssh ahorne@mysql.arunhorne.co.uk -L63306:localhost:3306 -Nf

#### Remote Forwarding

This will forward traffic from foo.arunhorne.co.uk:9000 to localhost:9111

    ssh ahorne@foo.arunhorne.co.uk -R9000:localhost:9111 -Nf


### Login via MySQL:

It seems necessary to use 127.0.0.1 rather than localhost for this to work correctly.

    mysql -u root -p -h 127.0.0.1 -P 63306

### Allow routing from wlan0 to eth0

    echo 1 > /proc/sys/net/ipv4/ip_forward
    /sbin/iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
    /sbin/iptables -A FORWARD -i wlan0 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
    /sbin/iptables -A FORWARD -i eth0 -o wlan0 -j ACCEPT

### Execute remote command and return immediately

    ssh foo@bar.com "sleep 10 > /dev/null 2>&1 &"

### Public IP address of cloud machine

    curl http://169.254.169.254/latest/meta-data/public-ipv4

### Localhost aliases

    sudo ifconfig lo0 alias 127.0.0.2 netmask 255.0.0.0