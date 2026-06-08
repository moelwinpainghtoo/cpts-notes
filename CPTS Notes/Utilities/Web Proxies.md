

# Proxychains

```bash
/etc/proxychains.conf
# add this and comment out the last line
http 127.0.0.1 8080

# Usage
proxychains -q curl http://SERVER_IP:PORT
```

# Metasploit

```bash
use auxiliary/scanner/http/robots_txt
set PROXIES HTTP:127.0.0.1:8080
set RHOST SERVER_IP
set RPORT PORT
run
```
