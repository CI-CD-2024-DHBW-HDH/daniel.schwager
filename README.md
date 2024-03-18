# Klausur 2023 DHBW HDH

## Setup

### Klone dieses Repository

1. Klone das Repository
    ```bash
    git clone <TODO repo url>
    cd klausur
    git remote remove origin
    ```
2. Erstelle in der GitHub Organisation ein Repository mit dem Namen **\<vorname>.\<nachname>**
3. Lade den Stand in das Repository hoch
   ```bash
   git remote add origin <url deines Repositories>
   git push -u origin master
   ```
4. Erstelle einen Branch für die Bearbeitung
   > Vergesse am Ende nicht deine Bearbeitung hochzuladen

### Sicherstellen, dass alles geht

Führe folgende Befehle in deinem Repository aus, um sicherzustellen, dass alles geht:

```bash
npm install

npm run dev
```

## Aufgaben (20 Punkte)

1. Installiere: **(3 Punkte)**
   * ESLint
   * Jest
   * Prettier
   > Die Config Dateien brauchen nicht angepasst werden
   
   > Denke auch an die nötigen Typescript dependencies
2. Schreibe ein `Dockerfile`, dass dazu benutzt werden kann, die Seite zur Verfügung zu stellen **(2 Punkte)**
3. Schreibe GitHub Actions für: **(3 Punkte)**
   * Continuous Integration
   * Continuous Delivery (GitHub Packages)
   * Continuous Deployment (GitHub Pages)
4. Definiere alle nötigen Manifeste um das erstellte Image auf einem Kubernetes Cluster zu deployen **(5 Punkte)**
5. Erkläre in eigenen Worten:
   * Welche Vorteile ein Kubernetes Deployment gegenüber einem Kubernetes Pod hat **(2 Punkte)**
      * Ein Kubernetes Deployment bietet gegenüber einem einzelnen Pod folgende Vorteile:
         * Automatisches Management: Deployments automatisieren das Erstellen, Löschen und Aktualisieren von Pods, sodass diese Prozesse  nicht manuell verwaltet werden müssen.
         * Skalierung: Ermöglicht die einfache Skalierung der Anzahl der Pods hoch oder runter, je nach Bedarf, ohne manuellen Eingriff.
         * Rollouts und Rollbacks: Ermöglicht das schrittweise Ausrollen von Änderungen (Updates) an der Anwendung oder das Zurücksetzen auf eine vorherige Version, falls etwas schief geht.
         * Selbstheilung: Automatisches Ersetzen von Pods, die ausfallen, gelöscht werden oder nicht reagieren, um den gewünschten Zustand der Anwendung zu erhalten.  
   * Wofür ein Kubernetes Service gut ist **(2 Punkte)**
      * Ein Kubernetes Service erleichtert die Verbindung zwischen den verschiedenen Pods - den kleinsten Einheiten der Arbeit in Kubernetes - durch die Bereitstellung einer konstanten IP-Adresse und eines Namens. Diese stabilen Identifikatoren ermöglichen es, dass Pods, unabhängig davon, wo oder in welchem Umfang sie im Cluster verteilt sind, zuverlässig miteinander und mit Anwendungen kommunizieren können. So wird sichergestellt, dass Anwendungen, die in diesen Pods ausgeführt werden, stets zugänglich sind, selbst wenn sich ihre Position oder Größe im Netzwerk ändert.
   * Mehrere Wege wie man eine Kubernetes Anwendung von außen erreichen kann **(3 Punkte)**
      * NodePort: Diese Methode eröffnet die Möglichkeit, einen spezifischen Port auf jedem Arbeitsknoten Ihres Clusters freizugeben. Jeglicher Datenverkehr, der diesen Port erreicht, wird nahtlos zu der zugehörigen Applikation innerhalb eines Pods umgeleitet. Diese Methode zeichnet sich durch ihre Einfachheit in der Einrichtung aus, allerdings ist sie für den Einsatz in Produktionsumgebungen oft weniger geeignet, da sie eine direkte Freilegung von Ports auf den Knoten voraussetzt.

      * LoadBalancer: Diese Methode ist besonders vorteilhaft, wenn Sie Kubernetes in einer Cloud-Umgebung betreiben, die externe Load Balancer unterstützt, wie es bei den meisten Cloud-Diensten der Fall ist. Durch die Erstellung eines LoadBalancer-Services wird ein externer Lastverteiler bereitgestellt, der eingehenden Datenverkehr auf die Pods Ihrer Anwendung verteilt. Dies erleichtert die Konfiguration und Verwaltung erheblich, da der Lastverteiler in der Regel automatisch eingerichtet wird.

      * Ingress: Ingress-Controller stellen eine ausgeklügelte und anpassbare Lösung dar, um den externen Zugriff auf Ihre Kubernetes-Services zu steuern. Mithilfe eines Ingress können Sie den Zugang basierend auf der angefragten URL oder dem Hostnamen regeln und profitieren dabei von fortgeschrittenen Funktionen wie SSL/TLS-Terminierung, Routing basierend auf dem Pfad und vieles mehr. Um diese Methode nutzen zu können, ist die Installation eines Ingress-Controllers in Ihrem Cluster erforderlich, beispielsweise nginx, traefik oder andere.

      * ExternalName: Diese Option ermöglicht die Erstellung eines Services, der auf externe Services außerhalb Ihres Clusters verweist. Praktisch handelt es sich dabei um einen CNAME-DNS-Eintrag, der besonders nützlich ist, wenn Sie Services sowohl innerhalb als auch außerhalb von Kubernetes im Rahmen einer serviceorientierten Architektur verwalten möchten.

      * Port-Forwarding: Diese Methode ist besonders für Entwicklungs- und Testzwecke geeignet. Durch den Einsatz von kubectl port-forward lässt sich ein lokaler Port zu einem Port eines Pods im Kubernetes-Cluster weiterleiten. Dies ermöglicht einen direkten Zugriff auf den Pod von Ihrem lokalen System aus. Allerdings sollte diese Methode aufgrund potenzieller Sicherheitsrisiken nicht in Produktionsumgebungen verwendet werden.


## Zusatzaufgabe:

Definiere einen Kubernetes Job **(2 Punkte)**