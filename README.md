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
<img width="1051" alt="image" src="https://github.com/SlaneDRV/DockerZad2/assets/125742851/283454ef-2209-4026-ac07-f3598d11bcd2">
<img width="597" alt="image" src="https://github.com/SlaneDRV/DockerZad2/assets/125742851/5f35f0ea-7f6d-4589-b7f7-2849395c37c7">
<img width="684" alt="image" src="https://github.com/SlaneDRV/DockerZad2/assets/125742851/05ef8cc4-9134-4041-ad4a-b753910b814d">
<img width="957" alt="image" src="https://github.com/SlaneDRV/DockerZad2/assets/125742851/7b3d8580-b45b-4811-8f42-efbd564e051f">
<img width="950" alt="image" src="https://github.com/SlaneDRV/DockerZad2/assets/125742851/c5dd2922-1e6d-4838-b1f7-3514828a93f5">
<img width="960" alt="image" src="https://github.com/SlaneDRV/DockerZad2/assets/125742851/2c057296-b31d-4695-b43d-ae1026816a30">
<img width="851" alt="image" src="https://github.com/SlaneDRV/DockerZad2/assets/125742851/639b7977-59ae-4e0a-9e3c-831204d8fc78">
