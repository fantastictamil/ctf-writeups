# nmap 

- network mapper 

## ports 

- direct trafic 
- 65535
- well-known ports `1023`

### version check

```bash
$ nmap -v 
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-02 12:13 IST
Read data files from: /usr/bin/../share/nmap
WARNING: No targets were specified, so 0 hosts scanned.
Nmap done: 0 IP addresses (0 hosts up) scanned in 0.05 seconds
```

### syn scan 

```bash
$ sudo nmap 10.10.132.98 -sS
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-02 12:12 IST
Nmap scan report for 10.10.132.98
Host is up (0.31s latency).
Not shown: 995 filtered ports
PORT     STATE SERVICE
21/tcp   open  ftp
53/tcp   open  domain
80/tcp   open  http
135/tcp  open  msrpc
3389/tcp open  ms-wbt-server

Nmap done: 1 IP address (1 host up) scanned in 19.41 seconds
```

### UDB scan 

```bash
$ sudo nmap 10.10.132.98 -sU
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Nmap scan report for 10.10.132.98
Host is up (0.36s latency).
Not shown: 999 open|filtered ports
PORT   STATE SERVICE
53/udp open  domain

Nmap done: 1 IP address (1 host up) scanned in 559.81 seconds
```

### os scan

```bash
$ sudo nmap 10.10.132.98 -O
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-02 12:26 IST
Nmap scan report for 10.10.132.98
Host is up (0.24s latency).
Not shown: 995 filtered ports
PORT     STATE SERVICE
21/tcp   open  ftp
53/tcp   open  domain
80/tcp   open  http
135/tcp  open  msrpc
3389/tcp open  ms-wbt-server
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: specialized|general purpose
Running (JUST GUESSING): AVtech embedded (87%), Microsoft Windows XP (85%)
OS CPE: cpe:/o:microsoft:windows_xp::sp3
Aggressive OS guesses: AVtech Room Alert 26W environmental monitor (87%), Microsoft Windows XP SP3 (85%)
No exact OS matches for host (test conditions non-ideal).

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 22.50 seconds
```

### detect version 

```bash
$ sudo nmap 10.10.132.98 -sV 
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-02 12:25 IST
Nmap scan report for 10.10.132.98
Host is up (0.30s latency).
Not shown: 995 filtered ports
PORT     STATE SERVICE       VERSION
21/tcp   open  ftp           FileZilla ftpd
53/tcp   open  domain?
80/tcp   open  http          Microsoft IIS httpd 10.0
135/tcp  open  msrpc         Microsoft Windows RPC
3389/tcp open  ms-wbt-server Microsoft Terminal Services
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 180.03 seconds
```

### verbosity

**level -1**

```bash
$ sudo nmap 10.10.132.98 -v
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-02 12:24 IST
Initiating Parallel DNS resolution of 1 host. at 12:24
Completed Parallel DNS resolution of 1 host. at 12:24, 0.01s elapsed
Initiating SYN Stealth Scan at 12:24
Scanning 10.10.132.98 [1000 ports]
Discovered open port 53/tcp on 10.10.132.98
Discovered open port 3389/tcp on 10.10.132.98
Discovered open port 135/tcp on 10.10.132.98
Discovered open port 80/tcp on 10.10.132.98
Discovered open port 21/tcp on 10.10.132.98
Completed SYN Stealth Scan at 12:25, 21.48s elapsed (1000 total ports)
Nmap scan report for 10.10.132.98
Host is up (0.30s latency).
Not shown: 995 filtered ports
PORT     STATE SERVICE
21/tcp   open  ftp
53/tcp   open  domain
80/tcp   open  http
135/tcp  open  msrpc
3389/tcp open  ms-wbt-server

Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 21.60 seconds
           Raw packets sent: 2006 (88.264KB) | Rcvd: 16 (704B)
```

**level -2**

```bash
$ sudo nmap 10.10.132.98 -vv
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-02 12:24 IST
Initiating Parallel DNS resolution of 1 host. at 12:24
Completed Parallel DNS resolution of 1 host. at 12:24, 0.01s elapsed
Initiating SYN Stealth Scan at 12:24
Scanning 10.10.132.98 [1000 ports]
Discovered open port 3389/tcp on 10.10.132.98
Discovered open port 21/tcp on 10.10.132.98
Discovered open port 53/tcp on 10.10.132.98
Discovered open port 135/tcp on 10.10.132.98
Discovered open port 80/tcp on 10.10.132.98
Completed SYN Stealth Scan at 12:24, 19.80s elapsed (1000 total ports)
Nmap scan report for 10.10.132.98
Host is up, received user-set (0.29s latency).
Scanned at 2021-08-02 12:24:07 IST for 19s
Not shown: 995 filtered ports
Reason: 995 no-responses
PORT     STATE SERVICE       REASON
21/tcp   open  ftp           syn-ack ttl 127
53/tcp   open  domain        syn-ack ttl 127
80/tcp   open  http          syn-ack ttl 127
135/tcp  open  msrpc         syn-ack ttl 127
3389/tcp open  ms-wbt-server syn-ack ttl 127

Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 19.92 seconds
           Raw packets sent: 2006 (88.264KB) | Rcvd: 17 (744B)
```

### output formats

**normal**

```bash
$ nmap 10.10.132.98 -oN output.txt
# Nmap 7.91 scan initiated Mon Aug  2 12:31:16 2021 as: nmap -oN output 10.10.132.98
Nmap scan report for 10.10.132.98
Host is up (0.29s latency).
Not shown: 995 filtered ports
PORT     STATE SERVICE
21/tcp   open  ftp
53/tcp   open  domain
80/tcp   open  http
135/tcp  open  msrpc
3389/tcp open  ms-wbt-server

# Nmap done at Mon Aug  2 12:31:40 2021 -- 1 IP address (1 host up) scanned in 23.50 seconds
```

**grepable**

```bash
$ nmap 10.10.132.98 -oG output.gnmap
# Nmap 7.91 scan initiated Mon Aug  2 12:36:00 2021 as: nmap -oA output 10.10.132.98
Host: 10.10.132.98 ()	Status: Up
Host: 10.10.132.98 ()	Ports: 21/open/tcp//ftp///, 53/open/tcp//domain///, 80/open/tcp//http///, 135/open/tcp//msrpc///, 3389/open/tcp//ms-wbt-server///	Ignored State: filtered (995)
# Nmap done at Mon Aug  2 12:36:19 2021 -- 1 IP address (1 host up) scanned in 19.00 seconds
```

### xml 

```bash
$ nmap 10.10.132.98 -oX output.xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE nmaprun>
<?xml-stylesheet href="file:///usr/bin/../share/nmap/nmap.xsl" type="text/xsl"?>
<!-- Nmap 7.91 scan initiated Mon Aug  2 12:36:00 2021 as: nmap -oA output 10.10.132.98 -->
<nmaprun scanner="nmap" args="nmap -oA output 10.10.132.98" start="1627887960" startstr="Mon Aug  2 12:36:00 2021" version="7.91" xmloutputversion="1.05">
<scaninfo type="connect" protocol="tcp" numservices="1000" services="1,3-4,6-7,9,13,17,19-26,30,32-33,37,42-43,49,53,70,79-85,88-90,99-100,106,109-111,113,119,125,135,139,143-144,146,161,163,179,199,211-212,222,254-256,259,264,280,301,306,311,340,366,389,406-407,416-417,425,427,443-445,458,464-465,481,497,500,512-515,524,541,543-545,548,554-555,563,587,593,616-617,625,631,636,646,648,666-668,683,687,691,700,705,711,714,720,722,726,749,765,777,783,787,800-801,808,843,873,880,888,898,900-903,911-912,981,987,990,992-993,995,999-1002,1007,1009-1011,1021-1100,1102,1104-1108,1110-1114,1117,1119,1121-1124,1126,1130-1132,1137-1138,1141,1145,1147-1149,1151-1152,1154,1163-1166,1169,1174-1175,1183,1185-1187,1192,1198-1199,1201,1213,1216-1218,1233-1234,1236,1244,1247-1248,1259,1271-1272,1277,1287,1296,1300-1301,1309-1311,1322,1328,1334,1352,1417,1433-1434,1443,1455,1461,1494,1500-1501,1503,1521,1524,1533,1556,1580,1583,1594,1600,1641,1658,1666,1687-1688,1700,1717-1721,1723,1755,1761,1782-1783,1801,1805,1812,1839-1840,1862-1864,1875,1900,1914,1935,1947,1971-1972,1974,1984,1998-2010,2013,2020-2022,2030,2033-2035,2038,2040-2043,2045-2049,2065,2068,2099-2100,2103,2105-2107,2111,2119,2121,2126,2135,2144,2160-2161,2170,2179,2190-2191,2196,2200,2222,2251,2260,2288,2301,2323,2366,2381-2383,2393-2394,2399,2401,2492,2500,2522,2525,2557,2601-2602,2604-2605,2607-2608,2638,2701-2702,2710,2717-2718,2725,2800,2809,2811,2869,2875,2909-2910,2920,2967-2968,2998,3000-3001,3003,3005-3007,3011,3013,3017,3030-3031,3052,3071,3077,3128,3168,3211,3221,3260-3261,3268-3269,3283,3300-3301,3306,3322-3325,3333,3351,3367,3369-3372,3389-3390,3404,3476,3493,3517,3527,3546,3551,3580,3659,3689-3690,3703,3737,3766,3784,3800-3801,3809,3814,3826-3828,3851,3869,3871,3878,3880,3889,3905,3914,3918,3920,3945,3971,3986,3995,3998,4000-4006,4045,4111,4125-4126,4129,4224,4242,4279,4321,4343,4443-4446,4449,4550,4567,4662,4848,4899-4900,4998,5000-5004,5009,5030,5033,5050-5051,5054,5060-5061,5080,5087,5100-5102,5120,5190,5200,5214,5221-5222,5225-5226,5269,5280,5298,5357,5405,5414,5431-5432,5440,5500,5510,5544,5550,5555,5560,5566,5631,5633,5666,5678-5679,5718,5730,5800-5802,5810-5811,5815,5822,5825,5850,5859,5862,5877,5900-5904,5906-5907,5910-5911,5915,5922,5925,5950,5952,5959-5963,5987-5989,5998-6007,6009,6025,6059,6100-6101,6106,6112,6123,6129,6156,6346,6389,6502,6510,6543,6547,6565-6567,6580,6646,6666-6669,6689,6692,6699,6779,6788-6789,6792,6839,6881,6901,6969,7000-7002,7004,7007,7019,7025,7070,7100,7103,7106,7200-7201,7402,7435,7443,7496,7512,7625,7627,7676,7741,7777-7778,7800,7911,7920-7921,7937-7938,7999-8002,8007-8011,8021-8022,8031,8042,8045,8080-8090,8093,8099-8100,8180-8181,8192-8194,8200,8222,8254,8290-8292,8300,8333,8383,8400,8402,8443,8500,8600,8649,8651-8652,8654,8701,8800,8873,8888,8899,8994,9000-9003,9009-9011,9040,9050,9071,9080-9081,9090-9091,9099-9103,9110-9111,9200,9207,9220,9290,9415,9418,9485,9500,9502-9503,9535,9575,9593-9595,9618,9666,9876-9878,9898,9900,9917,9929,9943-9944,9968,9998-10004,10009-10010,10012,10024-10025,10082,10180,10215,10243,10566,10616-10617,10621,10626,10628-10629,10778,11110-11111,11967,12000,12174,12265,12345,13456,13722,13782-13783,14000,14238,14441-14442,15000,15002-15004,15660,15742,16000-16001,16012,16016,16018,16080,16113,16992-16993,17877,17988,18040,18101,18988,19101,19283,19315,19350,19780,19801,19842,20000,20005,20031,20221-20222,20828,21571,22939,23502,24444,24800,25734-25735,26214,27000,27352-27353,27355-27356,27715,28201,30000,30718,30951,31038,31337,32768-32785,33354,33899,34571-34573,35500,38292,40193,40911,41511,42510,44176,44442-44443,44501,45100,48080,49152-49161,49163,49165,49167,49175-49176,49400,49999-50003,50006,50300,50389,50500,50636,50800,51103,51493,52673,52822,52848,52869,54045,54328,55055-55056,55555,55600,56737-56738,57294,57797,58080,60020,60443,61532,61900,62078,63331,64623,64680,65000,65129,65389"/>
<verbose level="0"/>
<debugging level="0"/>
<hosthint><status state="up" reason="unknown-response" reason_ttl="0"/>
<address addr="10.10.132.98" addrtype="ipv4"/>
<hostnames>
</hostnames>
</hosthint>
<host starttime="1627887960" endtime="1627887979"><status state="up" reason="syn-ack" reason_ttl="0"/>
<address addr="10.10.132.98" addrtype="ipv4"/>
<hostnames>
</hostnames>
<ports><extraports state="filtered" count="995">
<extrareasons reason="no-responses" count="995"/>
</extraports>
<port protocol="tcp" portid="21"><state state="open" reason="syn-ack" reason_ttl="0"/><service name="ftp" method="table" conf="3"/></port>
<port protocol="tcp" portid="53"><state state="open" reason="syn-ack" reason_ttl="0"/><service name="domain" method="table" conf="3"/></port>
<port protocol="tcp" portid="80"><state state="open" reason="syn-ack" reason_ttl="0"/><service name="http" method="table" conf="3"/></port>
<port protocol="tcp" portid="135"><state state="open" reason="syn-ack" reason_ttl="0"/><service name="msrpc" method="table" conf="3"/></port>
<port protocol="tcp" portid="3389"><state state="open" reason="syn-ack" reason_ttl="0"/><service name="ms-wbt-server" method="table" conf="3"/></port>
</ports>
<times srtt="309540" rttvar="57765" to="540600"/>
</host>
<runstats><finished time="1627887979" timestr="Mon Aug  2 12:36:19 2021" summary="Nmap done at Mon Aug  2 12:36:19 2021; 1 IP address (1 host up) scanned in 19.00 seconds" elapsed="19.00" exit="success"/><hosts up="1" down="0" total="1"/>
</runstats>
</nmaprun>
```

**major 3 formats** 

```bash
$ nmap 10.10.132.98 -oA output
```

### accressive scan 

```bash 
$ nmap 10.10.132.98 -A 
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-02 12:41 IST
Nmap scan report for 10.10.132.98
Host is up (0.29s latency).
Not shown: 995 filtered ports
PORT     STATE SERVICE       VERSION
21/tcp   open  ftp           FileZilla ftpd
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
| ftp-syst:
|_  SYST: UNIX emulated by FileZilla
53/tcp   open  domain        Simple DNS Plus
80/tcp   open  http          Microsoft IIS httpd 10.0
| http-methods:
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: IIS Windows Server
135/tcp  open  msrpc         Microsoft Windows RPC
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info:
|   Target_Name: WIN-SCAN
|   NetBIOS_Domain_Name: WIN-SCAN
|   NetBIOS_Computer_Name: WIN-SCAN
|   DNS_Domain_Name: win-scan
|   DNS_Computer_Name: win-scan
|   Product_Version: 10.0.17763
|_  System_Time: 2021-08-02T07:11:49+00:00
| ssl-cert: Subject: commonName=win-scan
| Not valid before: 2021-08-01T06:23:58
|_Not valid after:  2022-01-31T06:23:58
|_ssl-date: 2021-08-02T07:12:19+00:00; 0s from scanner time.
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 76.22 seconds
```

## Timming

**time 1**

```bash
$ nmap 10.10.132.98 -T1
```

**time 2**

```bash
$ nmap 10.10.132.98 -T2
```

**time 3**

```bash
$ nmap 10.10.132.98 -T3
```

**time 4**

```bash
$ nmap 10.10.132.98 -T4 
```

**time 5**

```bash
$ nmap 10.10.132.98 -T5
```

## specify ports

**one port**

```bash
$ nmap 10.10.132.98 -p 80
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-02 12:47 IST
Nmap scan report for 10.10.132.98
Host is up (0.40s latency).

PORT   STATE SERVICE
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 1.06 seconds
```

**port range**

```bash
$ nmap 10.10.132.98 -p 1-100
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-02 12:49 IST
Nmap scan report for 10.10.132.98
Host is up (0.42s latency).
Not shown: 97 filtered ports
PORT   STATE SERVICE
21/tcp open  ftp
53/tcp open  domain
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 20.54 seconds
```

**full port **

```bash
$ nmap 10.10.132.98 -p-

Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-02 12:12 IST
Nmap scan report for 10.10.132.98
Host is up (0.31s latency).
Not shown: 995 filtered ports
PORT     STATE SERVICE
21/tcp   open  ftp
53/tcp   open  domain
80/tcp   open  http
135/tcp  open  msrpc
3389/tcp open  ms-wbt-server

Nmap done: 1 IP address (1 host up) scanned in 19.41 seconds
```

## firewall evasion

**pn**

```bash
$ nmap 10.10.10.10 -Pn 
```

**fragment**

- `-f`split small pieces packet and send
- `--mtu` maximum transmission size 

```bash
$ nmap 10.10.10.10 -f --mtu 10
```

**delay**

- delay between packet send 

```bash
$ nmap 10.10.10.10 --scan-delay 5
```

**checksum**

- generate checksum packets

```bash
$ nmap 10.10.10.10 --badsum
```

**random**

- send random packets on server

```bash
$ nmap 10.10.10.10 --data-length
```

**tcp null scan**

`note : windows response reset for all scans xmas, null, fin` 

- send `no flag` set at all 
- `response` port is open
-  `RST` ( reset ) port is close

![](/home/craft/ctf/tryhackme/nmap/null-scan.png)

```bash
$ nmap 10.10.132.98 -sN
```

**tcp fin scan**

- sending empty packet
- last set fin flag `1` true
- `no responce` port is open
- `RST` port close 

![](/home/craft/ctf/tryhackme/nmap/fin-scan.png)

```bash
$ nmap 10.10.132.98 -sF 
```

**xmas scan**

- `URG`, `FIN`, `PSH` send
- `no response` port open
- `RST ` port close

![](/home/craft/ctf/tryhackme/nmap/xmas-scan.png)

```bash
$ nmap 10.10.132.98 -sX
```

**ping scan**

```bash
$ nmap 10.10.95.52 -sP
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-05 06:40 IST
Nmap scan report for 10.10.95.52
Host is up (0.25s latency).
Nmap done: 1 IP address (1 host up) scanned in 0.29 seconds
```

## other methods

**TCP scan**

```bash
$ nmap 10.10.132.98 -sT
```

**UDP scan**

```bash
$ nmap 10.10.132.98 -sU
```

**syn scan**

```bash 
$ nmap 10.10.132.98 -sS
```

## syn scan

- names : `half-open`, `stealth` scan
- syn scan `sudo` permission is importent 

```bash
$ nmap 10.10.132.98 -sS
```

## UDP scan

- no response `open|filtered`

```bash
$ nmap 10.10.132.98 -sU 
```

## top ports 

- scan top `100` ports

```bash
$ nmap 10.10.132.98 -sU --top-ports 100
```

## ICMP scan `ping sweep`

- ip address contain active host

```bash
$ nmap 192.168.1.0/24 -sn 
```



```bash
$ nmap 10.10.10.1-254 -sn
```

## NSE script scan

- `nse` nmap script engine
- **nse categories**
  - `safe` - don't affect target
  - `intrusive` - affect target ( bad practice )
  - `vuln` - find vulnerability scan
  - `exploit` - exploit a vulnerability
  - `auth`  -  bypass authentication 
  - `brute`  - brute fource credentials 
  - `discovery`  - information about the network

### update nse script

- nse script writen in `lua`

```bash
$ sudo nmap --script-update
[sudo] password for craft:
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-04 13:43 IST
NSE: Updating rule database.
NSE: Script Database updated successfully.
Nmap done: 0 IP addresses (0 hosts up) scanned in 0.93 seconds
```

**install new script**

```bash
$ sudo wget -O /usr/share/nmap/new.nse https://svn.nmap.org/nmap/scripts/new.nse
$ sudo nmap --script-updatedb 
```

### nse script help 

```bash
$ nmap 10.10.10.1 --script-help ftp*
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-04 13:47 IST

ftp-anon
Categories: default auth safe
https://nmap.org/nsedoc/scripts/ftp-anon.html
  Checks if an FTP server allows anonymous logins.

  If anonymous is allowed, gets a directory listing of the root directory
  and highlights writeable files.

ftp-bounce
Categories: default safe
https://nmap.org/nsedoc/scripts/ftp-bounce.html
  Checks to see if an FTP server allows port scanning using the FTP bounce method.

ftp-brute
Categories: intrusive brute
https://nmap.org/nsedoc/scripts/ftp-brute.html
  Performs brute force password auditing against FTP servers.

  Based on old ftp-brute.nse script by Diman Todorov, Vlatko Kosturjak and Ron Bowes.

ftp-libopie
Categories: vuln intrusive
https://nmap.org/nsedoc/scripts/ftp-libopie.html
  Checks if an FTPd is prone to CVE-2010-1938 (OPIE off-by-one stack overflow),
  a vulnerability discovered by Maksymilian Arciemowicz and Adam "pi3" Zabrocki.
  See the advisory at https://nmap.org/r/fbsd-sa-opie.
  Be advised that, if launched against a vulnerable host, this script will crash the FTPd.

ftp-proftpd-backdoor
Categories: exploit intrusive malware vuln
https://nmap.org/nsedoc/scripts/ftp-proftpd-backdoor.html
  Tests for the presence of the ProFTPD 1.3.3c backdoor reported as BID
  45150. This script attempts to exploit the backdoor using the innocuous
  <code>id</code> command by default, but that can be changed with the
  <code>ftp-proftpd-backdoor.cmd</code> script argument.

ftp-syst
Categories: default discovery safe
https://nmap.org/nsedoc/scripts/ftp-syst.html
  Sends FTP SYST and STAT commands and returns the result.

  The canonical SYST response of "UNIX Type: L8" is stripped or ignored, since it
  is meaningless. Typical FTP response codes (215 for SYST and 211 for STAT) are
  also hidden.

  References:
  * https://cr.yp.to/ftp/syst.html

ftp-vsftpd-backdoor
Categories: exploit intrusive malware vuln
https://nmap.org/nsedoc/scripts/ftp-vsftpd-backdoor.html
  Tests for the presence of the vsFTPd 2.3.4 backdoor reported on 2011-07-04
  (CVE-2011-2523). This script attempts to exploit the backdoor using the
  innocuous <code>id</code> command by default, but that can be changed with
  the <code>exploit.cmd</code> or <code>ftp-vsftpd-backdoor.cmd</code> script
  arguments.

  References:

  * http://scarybeastsecurity.blogspot.com/2011/07/alert-vsftpd-download-backdoored.html
  * https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/unix/ftp/vsftpd_234_backdoor.rb
  * http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=CVE-2011-2523

ftp-vuln-cve2010-4221
Categories: intrusive vuln
https://nmap.org/nsedoc/scripts/ftp-vuln-cve2010-4221.html
  Checks for a stack-based buffer overflow in the ProFTPD server, version
  between 1.3.2rc3 and 1.3.3b. By sending a large number of TELNET_IAC escape
  sequence, the proftpd process miscalculates the buffer length, and a remote
  attacker will be able to corrupt the stack and execute arbitrary code within
  the context of the proftpd process (CVE-2010-4221). Authentication is not
  required to exploit this vulnerability.

  Reference:
  * https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2010-4221
  * http://www.exploit-db.com/exploits/15449/
  * http://www.metasploit.com/modules/exploit/freebsd/ftp/proftp_telnet_iac
```

### specify nse script

```bash
$ nmap 10.10.10.1 --scripts=vuln*
```

### searching scripts 

```bash
$ cat /usr/share/nmap/scripts/script.db | grep -i "ftp"
Entry { filename = "ftp-anon.nse", categories = { "auth", "default", "safe", } }
Entry { filename = "ftp-bounce.nse", categories = { "default", "safe", } }
Entry { filename = "ftp-brute.nse", categories = { "brute", "intrusive", } }
Entry { filename = "ftp-libopie.nse", categories = { "intrusive", "vuln", } }
Entry { filename = "ftp-proftpd-backdoor.nse", categories = { "exploit", "intrusive", "malware", "vuln", } }
Entry { filename = "ftp-syst.nse", categories = { "default", "discovery", "safe", } }
Entry { filename = "ftp-vsftpd-backdoor.nse", categories = { "exploit", "intrusive", "malware", "vuln", } }
Entry { filename = "ftp-vuln-cve2010-4221.nse", categories = { "intrusive", "vuln", } }
Entry { filename = "tftp-enum.nse", categories = { "discovery", "intrusive", } }
```

## iptable ( net filter fireware table )

```bash 
$ iptables -L -n -v 
```

* `-L` list chaines 
* `-n` numeric 
* `-v` verbosity
