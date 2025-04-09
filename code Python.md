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
import requests
import socket
import dns.resolver

domain = "drive.google.com"

# Liste des en-têtes de sécurité à vérifier
security_headers = [
    'Strict-Transport-Security', 'Content-Security-Policy', 'X-Content-Type-Options',
    'X-Frame-Options', 'X-XSS-Protection', 'Referrer-Policy', 'Permissions-Policy',
    'Feature-Policy', 'Cache-Control', 'Cross-Origin-Embedder-Policy',
    'Cross-Origin-Opener-Policy', 'Cross-Origin-Resource-Policy', 'Expect-CT',
    'NEL', 'Report-To', 'Clear-Site-Data', 'Access-Control-Allow-Origin',
    'X-Permitted-Cross-Domain-Policies', 'Public-Key-Pins'
]

my_resolver = dns.resolver.Resolver()
dns_servers = my_resolver.nameservers

# Effectue la requête DNS et HTTP
answers = my_resolver.resolve(domain, 'A')
for rdata in answers:
    dest_ip = rdata.to_text()
    print(f"Domaine {domain} → {dest_ip}")
    response = requests.get(f"https://{domain}")
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        s.connect((dest_ip, 443))
        src_ip, src_port = s.getsockname()
    print(f"Connexion: {src_ip}:{src_port} → {dest_ip}:443")

# Affiche les informations sur le serveur DNS configuré
print(dns_servers)

# Affichage des en-têtes de sécurité
print("\nEn-têtes de sécurité:")
for header in security_headers:
    print(f"{header}: {response.headers.get(header) or '❌ Non défini'}")
```
