# Boucle et condition
```python
def check_fruits(tabfruit):

    if 'poire' in tabfruit:
        print("poire est présent")
    elif tabfruit.count('cerise'):
        print("cerise est présent, poire est absent")
    else:
        print("ni poire ni cerise n'ont été trouvé")


fruits = ["pomme", "banane", "cerise"]

for f in fruits:
    print(f.upper())

check_fruits(fruits)

print(fruits)
fruits.reverse()
print(fruits)

print(len(fruits))

fruits.append("poire")
print(fruits)

check_fruits(fruits)
```

# Scripter l'analyse de traffic Réseau et Web

```python
import requests, socket, dns.resolver

domain = "taisen.fr"
show_all_dns = True
dns_servers = dns.resolver.Resolver().nameservers

# Liste des en-têtes de sécurité à vérifier
security_headers = [
    'Strict-Transport-Security',
    'Content-Security-Policy',
    'Content-Security-Policy-Report-Only',
    'X-Content-Type-Options',
    'X-Frame-Options',
    'X-XSS-Protection',
    'Referrer-Policy',
    'Permissions-Policy',
    'Feature-Policy',
    'Cache-Control',
    'Cross-Origin-Embedder-Policy',
    'Cross-Origin-Opener-Policy',
    'Cross-Origin-Resource-Policy',
    'Expect-CT',
    'NEL',
    'Report-To',
    'Clear-Site-Data',
    'Access-Control-Allow-Origin',
    'X-Permitted-Cross-Domain-Policies',
    'Public-Key-Pins'
]

# Effectue la requête et récupère les en-têtes
response = requests.get(f"https://{domain}")
dest_ip = socket.gethostbyname(domain)
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((dest_ip, 443))
src_ip, src_port = s.getsockname()
s.close()

print(f"Domaine {domain} → {dest_ip}")
print(f"Connexion: {src_ip}:{src_port} → {dest_ip}:443")

if show_all_dns:
    for i, dns_ip in enumerate(dns_servers):
        try:
            dns_name = socket.gethostbyaddr(dns_ip)[0]
        except:
            dns_name = "Non résolu"
        print(f"DNS {i+1}: {dns_name} ({dns_ip})")
else:
    dns_ip = dns_servers[0]
    try:
        dns_name = socket.gethostbyaddr(dns_ip)[0]
    except:
        dns_name = "Non résolu"
    print(f"DNS: {dns_name} ({dns_ip}){' +'+str(len(dns_servers)-1) if len(dns_servers)>1 else ''}")

# Affichage des en-têtes de sécurité
print("\nEn-têtes de sécurité:")
for header in security_headers:
    value = response.headers.get(header)
    if value:
        print(f"{header}: {value}")
    else:
        print(f"{header}: ❌ Non défini")
```
