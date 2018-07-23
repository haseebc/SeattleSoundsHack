# Recon

## Getting started
Download the vulnerable VM from https://www.vulnhub.com/entry/seattle-v03,145/
Simply start up the virtual machine using Virtual Box! The root user account has a password of PASSWORD

## Check the network
Main points:
- looking mostly for common-ish vulns
- not competing with others
- racing vs. time

Try `netdiscover 192.168.0.0/24`

## See what ports are open

`nmap -p 80 192.168.0.168`

```
root@kali:~# nmap 192.168.0.168

Starting Nmap 7.01 ( https://nmap.org ) at 2018-07-23 06:39 EDT
Nmap scan report for 192.168.0.168
Host is up (0.0016s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE
80/tcp open  http
```
Okay seems only port 80 is open.

## Check for vulnerabilities
Use nikto
```
root@kali:~# nikto -h 192.168.0.168
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          192.168.0.168
+ Target Hostname:    192.168.0.168
+ Target Port:        80
+ Start Time:         2018-07-23 06:30:36 (GMT-4)
---------------------------------------------------------------------------
+ Server: Apache/2.4.16 (Fedora) OpenSSL/1.0.2d-fips PHP/5.6.14
+ Retrieved x-powered-by header: PHP/5.6.14
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type
+ Cookie level created without the httponly flag
+ Web Server returns a valid response with junk HTTP methods, this may cause false positives.
+ OSVDB-877: HTTP TRACE method is active, suggesting the host is vulnerable to XST
+ Uncommon header 'content-disposition' found, with contents: filename="downloads"
+ /config.php: PHP Config file may contain database IDs and passwords.
+ OSVDB-3268: /admin/: Directory indexing found.
+ OSVDB-3092: /admin/: This might be interesting...
+ OSVDB-3268: /downloads/: Directory indexing found.
+ OSVDB-3092: /downloads/: This might be interesting...
+ Server leaks inodes via ETags, header found with file /manual/, fields: 0x2304 0x51b0c59e09040 
+ OSVDB-3092: /manual/: Web server manual found.
+ /info.php: Output from the phpinfo() function was found.
+ OSVDB-3233: /info.php: PHP is installed, and a test script which runs phpinfo() was found. This gives a lot of system information.
+ OSVDB-3268: /icons/: Directory indexing found.
+ OSVDB-3268: /manual/images/: Directory indexing found.
+ OSVDB-3268: /images/: Directory indexing found.
+ OSVDB-3268: /images/?pattern=/etc/*&sort=name: Directory indexing found.
+ OSVDB-3233: /icons/README: Apache default file found.
+ Cookie lang created without the httponly flag
+ /info.php?file=http://cirt.net/rfiinc.txt?: Output from the phpinfo() function was found.
+ OSVDB-5292: /info.php?file=http://cirt.net/rfiinc.txt?: RFI from RSnake's list (http://ha.ckers.org/weird/rfi-locations.dat) or from http://osvdb.org/
+ 8327 requests: 0 error(s) and 25 item(s) reported on remote host
+ End Time:           2018-07-23 06:30:59 (GMT-4) (23 seconds)
---------------------------------------------------------------------------
```

It's worth making a note of `/images` and `/admin` directories can be traversed

## Browse the site manually

When browsing the Blog section it's noticeable the username of Admin is defined. interesting, make a note of this!
