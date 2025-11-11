# Web Bruteforce

A minimal Python script that attempts HTTP Basic Auth by trying passwords from a wordlist. Designed for lab/educational use only — **do not** run against systems you don’t own or have explicit permission to test.

## Features

* Tries passwords from a newline-separated wordlist against a target URL using HTTP Basic Auth.
* Prints progress for each attempted password and reports the first password that appears to succeed.
* Simple, single-file script with only the `requests` dependency.
* Basic network error handling and timeouts to survive flaky connections.

## How to Run

1. Clone or download the repo.
2. Install dependency:

```bash
pip install requests
```

3. Run the script:

```bash
python3 web-bruteforce.py <URL> <username> <passwords-file>
# Example:
python3 web-bruteforce.py http://example.com/protected administrator ./passwords.txt
```

The script reads the password file (one password per line), tries each password for HTTP Basic Auth, and prints the server response status. It stops on the first password that returns a success-like response (HTTP 200 or common redirects).

## Notes

* This tool targets **HTTP Basic Auth** only. Many web logins use form-based auth (HTML forms, CSRF tokens) — those require a different approach.
* The script treats HTTP 200 and 3xx redirects as likely success indicators; you may want to adapt the success criteria for your target.
* Use reasonable timeouts and delays when testing large wordlists to avoid overwhelming the target.
* **Legal & ethical:** Only use this on targets you own or have explicit authorization to test. Unauthorized brute-forcing is illegal and unethical. For legitimate remote access, prefer secure methods like SSH with proper authentication.
