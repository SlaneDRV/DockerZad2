# Docker Zadanie 2

## Opis

Repozytorium zawiera łańcuch CI (Continuous Integration), który został skonfigurowany do budowania obrazu Docker, skanowania pod kątem podatności oraz wdrażania do publicznego repozytorium obrazów na GitHub (GHCR), tylko jeżeli nie zostaną wykryte zagrożenia klasyfikowane jako krytyczne lub wysokie.

## Konfiguracja Testu CVE

Test podatności (CVE) został zintegrowany z wykorzystaniem akcji GitHub Actions - Docker Scout, która analizuje obraz Docker pod kątem znanych podatności. Konfiguracja została przeprowadzona zgodnie z następującymi krokami:

1. **Budowanie Obrazu Docker**:
   - Obraz jest budowany z wykorzystaniem pliku `Dockerfile` znajdującego się w repozytorium.
   - Obraz jest budowany dla architektur `linux/amd64` i `linux/arm64`.

2. **Skanowanie Obrazu**:
   - Po zbudowaniu, obraz jest skanowany przy użyciu akcji Docker Scout.
   - Wyniki skanowania są zapisywane do pliku `sarif.output.json`.

3. **Analiza Wyników Skanowania**:
   - Wyniki z pliku SARIF są analizowane, aby sprawdzić, czy znajdują się tam podatności klasyfikowane jako krytyczne lub wysokie.
   - Jeżeli takie podatności zostaną znalezione, łańcuch CI kończy się niepowodzeniem, co zapobiega wypchnięciu obrazu do GHCR.

4. **Wdrażanie Obrazu**:
   - Jeśli w raporcie SARIF nie zostaną wykryte krytyczne lub wysokie podatności, obraz jest wypychany do GHCR.

## Uruchomienie Łańcucha CI
![image](https://github.com/SlaneDRV/DockerZad2/assets/125742851/b35d75e6-98a7-4adb-8760-eba1b731b28c)
![image](https://github.com/SlaneDRV/DockerZad2/assets/125742851/9c82fdf5-6776-4018-b281-50b58f5a6923)
![image](https://github.com/SlaneDRV/DockerZad2/assets/125742851/86d946f1-4cb7-4594-8814-ecdff683b020)

