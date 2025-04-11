# Analyse vulnérabilités

## Eternal Blue 
CVE-2017-0144 <br>
Permet d'executer du code à distance en exploitant une faille sur le protocole smb version 1. <br>
Serveurs et endpoint concerné. <br>
Score CVSS : 8.8<br>

## KRACK CVE-2017-13077 
Permet à un attaquant de compromettre le protocole de sécurité WPA2 en forçant la réutilisation des clés de chiffrement lors de la troisième étape du handshake, ce qui peut conduire au déchiffrement du trafic Wi-Fi et potentiellement à l'injection de données. <br>
Routeurs, bornes, ordinateurs, smartphones, tablettes, IoT usant du WPA2, contrôleur de réseau, OS supportant le Wi-Fi et autres micrologiciels embarqué dans les puces Wi-FI. <br>
Score CVSS : 6<br>

## log4shell
CVE-2021-44228 
Vulnérabilité de type injection JNDI dans Log4j qui permet l'exécution de code à distance lorsqu'une chaîne spécialement conçue est analysée par le composant de journalisation. <br>
Éléments d'infrastructure concernés: Serveurs d'applications Java, Applications web utilisant Log4j, Services cloud, APIs, Outils d'entreprise (comme Elasticsearch, VMware, CloudFlare), Systèmes de gestion de contenu, dispositifs IoT exécutant du code Java <br>
Score CVSS : 10.0 (Critique)<br>

## Looney Tunables 
CVE-2023-4911 <br>
Vulnérabilité d'élévation de privilèges dans la bibliothèque GNU C (glibc) permettant à un attaquant d'obtenir des privilèges root via un dépassement de tampon dans la fonction getenv() lors du traitement de variables d'environnement dynamiques. <br>
Systèmes Linux utilisant glibc, principalement: Serveurs Ubuntu, Debian et autres distributions, Conteneurs et environnements de virtualisation, systèmes embarqués, appareils IoT, infrastructure cloud <br>
Score CVSS: 7.8<br>
