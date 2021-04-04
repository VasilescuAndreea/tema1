# Soluție

## 1. DNS over HTTPS
Am implementat funcția aici:
```
import requests

#IP de tip V4
def getIP(name):

    headers = {
        "Accept": "application/dns-json",
    }

    #https://cloudflare-dns.com/dns-query?name=' + name => IP(sub forma de string)
    response = requests.get('https://cloudflare-dns.com/dns-query?name=' + name, headers = headers)

    #vreau ca IP-ul meu sa fie de tip Json ca sa il pot folosi
    responseJson = response.json()

    #verific ca in Answer se vor afla IP-urile
    #in caz contrar afisez un mesaj corespunzator
    if "Answer" in responseJson:
        answer = ""
        for ip in responseJson["Answer"]:
            answer += ip["data"] + "\n"
        return answer
    else:
        return "Nu a fost primit niciun raspuns."

print (getIP("netflix.com"))
```
iar aici e un exemplu de execuție
```
print (getIP("netflix.com"))

54.155.178.5
54.74.73.31
3.251.50.149
```

## 2. Traceroute

Am implementat soluția iar aici este output-ul:

### Ruta către IP1
```
IP11 - Oraș, Regiune, Țară
IP12 - Oraș, Regiune, Țară
IP13 - Oraș, Regiune, Țară
...
IP1N - Oraș, Regiune, Țară
```

### Ruta către IP2
```
IP21 - Oraș, Regiune, Țară
IP22 - Oraș, Regiune, Țară
IP23 - Oraș, Regiune, Țară
...
IP2N - Oraș, Regiune, Țară
```

### Ruta către IP3
```
IP31 - Oraș, Regiune, Țară
IP32 - Oraș, Regiune, Țară
IP33 - Oraș, Regiune, Țară
...
IP3N - Oraș, Regiune, Țară
```


## 3. Reliable UDP

### Emițător - mesaje de logging
Rulăm `docker-compose logs emitator` și punem rezultatul aici:
```
....
....
....
....
....
```


### Receptor - mesaje de logging
Rulăm `docker-compose logs receptor` și punem rezultatul aici:
```
....
....
....
....
....
```
