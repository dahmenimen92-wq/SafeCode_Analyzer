# SafeCode Analyzer

> **Audit de Sécurité Distribué par IA**  
> *Réalisé par : Imen Dahmen & Yessmine Ellouze*

**SafeCode Analyzer** est une application distribuée qui détecte les failles de sécurité (SQLi, XSS...) dans le code source en utilisant l'IA Google Gemini 2.0

## Architecture Hybride

Le projet repose sur une architecture 3-Tiers combinant Web, REST et RMI :

1.  **Client Web** (JS/HTML) : Interface utilisateur qui communique en JSON
2.  **RestServer** (Gateway) : Agit comme un Pont. Il traduit les requêtes HTTP/JSON du web en appels RMI Java
3.  **ServerRMI** (Backend) : Héberge la logique métier et interroge l'API Google AI

## Pourquoi cette architecture ?

*   RMI vs CORBA : Nous avons choisi RMI car notre environnement est 100% Java (plus performant que CORBA ici). L'interopérabilité avec le Web est assurée par REST/JSON, le standard moderne, plutôt que par CORBA
*   Rôle du RestServer :Il est indispensable pour combler l'incompatibilité entre le navigateur (qui parle HTTP) et le backend (qui parle RMI)

## Démarrage Rapide
**Prérequis :Java 17, Maven, Clé API Google.
1.  Config : Ajoutez votre clé dans Server/src/main/resources/config.properties
2.  Build : `mvn clean install`
3.  Lancer Backend : Exécutez server.ServerRMI (Port 1099)
4.  Lancer Gateway : Exécutez rest.RestServer (Port 8081)
5.  Accès : Ouvrez http://localhost:8081


