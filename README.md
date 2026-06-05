# Laboratorium 14 — Filip Kwietniak

### Uruchomienie stosu
docker compose up -d

Wynik:
[+] up 67/67
 ✔ Image php:8.2-fpm            Pulled                                     60.9s
 ✔ Image phpmyadmin:5.2         Pulled                                     66.2s
 ✔ Image mysql:8.0              Pulled                                     63.2s
 ✔ Image nginx:1.25             Pulled                                     59.3s
 ✔ Network lab14-lemp_frontend  Created                                    0.0s
 ✔ Network lab14-lemp_backend   Created                                    0.0s
 ✔ Volume lab14-lemp_mysql_data Created                                    0.0s
 ✔ Container mysql              Started                                    1.0s
 ✔ Container php                Started                                    1.0s
 ✔ Container phpmyadmin         Started                                    0.8s
 ✔ Container nginx              Started                                    0.9s


### Sprawdzenie statusu kontenerów
docker compose ps

Wynik:
NAME         IMAGE            COMMAND                  SERVICE      CREATED              STATUS              PORTS
mysql        mysql:8.0        "docker-entrypoint.s…"   mysql        About a minute ago   Up About a minute   3306/tcp, 33060/tcp
nginx        nginx:1.25       "/docker-entrypoint.…"   nginx        About a minute ago   Up About a minute   0.0.0.0:4001->80/tcp, [::]:4001->80/tcp
php          php:8.2-fpm      "docker-php-entrypoi…"   php          About a minute ago   Up About a minute   9000/tcp
phpmyadmin   phpmyadmin:5.2   "/docker-entrypoint.…"   phpmyadmin   About a minute ago   Up About a minute   0.0.0.0:6001->80/tcp, [::]:6001->80/tcp


### Sprawdzenie sieci backend
docker network inspect lab14-lemp_backend

Wynik:
        "Name": "lab14-lemp_backend",
        "Id": "7c53328806a41fa16371c7a174f09176476c5a54eabe2896adddea399792ec7f",
        "Created": "2026-06-05T16:46:31.864047247+02:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv4": true,
                "Name": "phpmyadmin",
                "EndpointID": "74eda703ae9a574af8429a241e3ffa37592c8c52694de9d6da4bccc66a120343",
                "MacAddress": "1e:4f:e2:48:8e:a3",
                "IPv4Address": "172.20.0.4/16",
                "IPv6Address": ""
            },
                "Name": "nginx",
                "EndpointID": "864420b1acb40fb40d05f6d64c2bebc98e7266971e5fc942d20688e797584aa1",
                "MacAddress": "da:9c:da:30:0c:fd",
                "IPv4Address": "172.20.0.5/16",
                "IPv6Address": ""
            },
                "Name": "php",
                "EndpointID": "cb316bb296693fc66e4fbf6231f410c75aebf4aa70a0a38813987a39ce229d63",
                "MacAddress": "06:8e:6f:5f:36:72",
                "IPv4Address": "172.20.0.3/16",
                "IPv6Address": ""
            },
                "Name": "mysql",
                "EndpointID": "7e7a1159c344e67ffb1a3803e4c1a07dad7e3001702791a7514f461693cc6efe",
                "MacAddress": "3a:e0:09:c4:e2:10",
                "IPv4Address": "172.20.0.2/16",
                "IPv6Address": ""
            }


### Sprawdzenie sieci frontend
docker network inspect lab14-lemp_frontend

Wynik:
        "Name": "lab14-lemp_frontend",
        "Id": "669ae914762b9b69dc6e2ef96a1ad85fdf04a7f1cc70ed867abfb9872e3bfd94",
        "Created": "2026-06-05T16:46:31.831743023+02:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv4": true,
                "Name": "phpmyadmin",
                "EndpointID": "6c8e90e10ce2cc3a76ebb4c28a5a2270315b6039c86f73bc4effdd64e5cf407e",
                "MacAddress": "d6:4f:b2:27:b2:40",
                "IPv4Address": "172.19.0.2/16",
                "IPv6Address": ""
            },
                "Name": "nginx",
                "EndpointID": "4f57a6697073244f12c72e4583c57672d0123bb7f35f45dcef3df6cc040fa437",
                "MacAddress": "16:31:6c:3d:d8:0b",
                "IPv4Address": "172.19.0.3/16",
                "IPv6Address": ""
            }

### Zatrzymanie i usunięcie kontenerów
docker compose down

Wynik:
[+] down 6/6
 ✔ Container nginx             Removed                                                                                                                           0.4s
 ✔ Container phpmyadmin        Removed                                                                                                                           1.3s
 ✔ Container php               Removed                                                                                                                           0.2s
 ✔ Container mysql             Removed                                                                                                                           1.0s
 ✔ Network lab14-lemp_backend  Removed                                                                                                                           0.3s
 ✔ Network lab14-lemp_frontend Removed                                                                                                                           0.1s
