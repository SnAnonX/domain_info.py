import socket
import whois
import requests

def get_ip(domain):
    try:
        ip = socket.gethostbyname(domain)
        return ip
    except Exception as e:
        return f"Error: {e}"

def get_whois(domain):
    try:
        info = whois.whois(domain)
        return info
    except Exception as e:
        return f"Error: {e}"

def get_headers(domain):
    try:
        response = requests.get(f"http://{domain}")
        return response.headers
    except Exception as e:
        return f"Error: {e}"

if __name__ == "__main__":
    domain = input("Enter domain name (example.com): ").strip()

    print(f"\n[+] IP Address of {domain}:")
    print(get_ip(domain))

    print(f"\n[+] WHOIS Information:")
    print(get_whois(domain))

    print(f"\n[+] HTTP Headers:")
    print(get_headers(domain))
