# Laboratorium 14 — Docker Compose LEMP Stack

## Użyte polecenia

### Uruchomienie stosu
```bash
docker compose up -d
```

### Sprawdzenie statusu kontenerów
```bash
docker compose ps
```

### Sprawdzenie sieci backend
```bash
docker network inspect lab14-lemp_backend
```

### Sprawdzenie sieci frontend
```bash
docker network inspect lab14-lemp_frontend
```

### Zatrzymanie i usunięcie kontenerów
```bash
docker compose down
```
