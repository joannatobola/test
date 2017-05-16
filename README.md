- [ ] ## 1. Logi z części backendowej systemu są rejestrowane w ELK (Elasticsearch / Logstash / Kibana).

- [ ]  2. System (aplikacja) używa tylko instancji RabbitMQ utrzymywanych przez Zespół Wsparcia, dedykowanych dla danego środowiska (DEV, BETA, PROD). Konsumpcja zdarzeń jest realizowana przez HAProxy, a publikowanie odbywa się albo przez lokalną instancję RabbitMQ albo przez HAProxy.

- [ ] 3. Consumery (aplikacje konsumujące zdarzenia) są hostowane w osobnych procesach niezależnie od IIS.

- [ ] 4. System używa wspólnego mechanizmu uwierzytelniania i autoryzacji – Heimdallr. Jeżeli system wymaga autoryzacji, to jest ona oparta na claim'ach. W wyjątkowych sytuacjach dopuszczalny jest brak uwierzytelniania.

- [ ] 5. Proces budowania i deploymentu jest w pełni automatyczny w oparciu o TeamCity, Octopus, Jenkins i nie wymaga ręcznych akcji ani nie wymaga dostępu (np. logowanie się poprzez RDP czy ssh) do środowiska produkcyjnego.

- [ ] 6. System jest skalowalny horyzontalnie. Działają przynajmniej 2 instancje systemu na różnych hostach, dotyczy to zarówno WebApi jak i Consumerów. Instancje WebApi są gotowe by działać za HAProxy. Wszystkie systemy WebApi są zarejestrowane w Consulu.

- [ ] 7. System zapewnia ciągłość działania usług np. poprzez redundancję komponentów hostowanych na różnych hostach w trybie active-active, brak sticky session. Ciągłość działania jest zapewniona także podczas deploymentu.

- [ ] 8. Hosty i ich zasoby typu zużycie procesora, zajętość pamięci, zajętość dysku, stan podstawowych procesów są administrowane i monitorowane przez K2.

- [ ] 9. Systemy zlokalizowane w jednym centrum danych komunikują się między sobą protokołem HTTP (nie HTTPS), a także nie komunikują się za pomocą interfejsów publicznych przez sieć Internet. Usługi udostępnione do Internetu są dostępne z zewnątrz po HTTPS.

- [ ] 10. Systemy do komunikacji po http wykorzystują adresy dostarczone przez Consula lub HaProxy. Systemy nie używają wpisów w plikach hosts do rozwiązywania adresów.

- [ ] 11. Działanie komponentów (onlineowych i batchowych) jest sprawdzane po deploymencie przy użyciu smoke testów.

- [ ] 12. Zespół jest w stanie zmienić wszystkie poświadczenia systemu (nie dotyczy poświadczeń użytkowników) w tym client secret we współpracy z Zespołem Wsparcia w przeciągu 60 minut. Żadne hasła dostępowe ani dane wrażliwe nie mogą być przechowywane w kodzie źródłowym w repozytorium (z wyjątkiem poświadczeń na środowisko DEV), w logach. Poświadczenia nie mogą być dostępne/ulokowane w aplikacjach działających na urządzeniach użytkowników. Poświadczenia powinny się znajdować w Octopus i muszą być zamaskowane. Na środowiskach DEV-owych mogą być tylko poświadczenia DEV-owe.

- [ ] 13. Działanie produkcyjnych usług systemu Windows i pul w IIS jest monitorowane w CheckMK.

- [ ] 14. Żaden z komponentów (WebApi, Consumer) nie może działać w kontekście konta użytkownika. Powinien działać w kontekście systemowego użytkownika.

- [ ] 16. Aplikacja najpóźniej przed pierwszym wdrożeniem lub w razie fundamentalnych zmian jest zweryfikowana pod kątem architektury, procesu deploymentu, bezpieczeństwa, integracji z Heimdallrem, Consulem, RabbitMQ, Prometheus-em, itp., oraz w/w wymagań przez Architektów, Zespół Wsparcia lub osoby przez nie wyznaczone.
