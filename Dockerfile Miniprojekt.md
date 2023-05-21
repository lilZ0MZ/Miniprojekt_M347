1. Verzeichnis erstellen:
```shell
mkdir myWebserver

cd myWebserver
```

2. Dockerfile erstellen und Inhalt einfügen:

```shell
touch Dockerfile

nano Dockerfile
```

```shell
# Basisimage aus dem Docker Hub verwenden
FROM nginx

# Arbeitsverzeichnis im Container erstellen
WORKDIR /usr/share/nginx/html

# Webseite in das Arbeitsverzeichnis kopieren
COPY . .

# Port 8080 im Container freigeben
EXPOSE 8080
```

3. Statische Webseite hinzufügen
```shell
touch index.html

nano index.html
```

```html
<!DOCTYPE html>
<html>
<head>
    <title>Meine statische Webseite</title>
</head>
<body>
    <h1>Willkommen auf meiner Webseite!</h1>
    <p>Dies ist eine einfache statische Webseite.</p>
</body>
</html>
```

4. Docker-Image erstellen:
```shell
docker build -t mein-webserver .
```

5. Container starten:
```shell
docker run -d -p 8080:8080 -v /lokaler/pfad/zur/webseite:/usr/share/nginx/html mein-webserver
```
Dieser Befehl startet einen Container aus dem erstellten Image und bindet den Port 8080 des Containers an den Port 8080 des Hosts. Dadurch wird die Webseite im Browser unter [http://localhost:8080](http://localhost:8080/) erreichbar.
