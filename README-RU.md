### Сервер с использованием реверс-прокси NGINX
Этот скрипт предназначен для быстрой настройки обратного прокси-сервера на базе NGINX в связке с Xray. В данном варианте Xray работает напрямую на порту 443, перенаправляет на сокет, а NGINX его слушает, что исключает избыточные затраты на TCP. Такой подход повышает производительность и стабильность соединения.
> [!IMPORTANT]
> Этот скрипт был протестирован в среде виртуализации KVM. Для корректной работы вам потребуется собственный домен, который необходимо привязать к Cloudflare. Скрипт рекомендуется запускать с правами root на свежеустановленной системе.
-----
### Настройка Cloudflare
1. Настройте Cloudflare:
   - Привяжите ваш домен к Cloudflare.
   - Добавьте следующие DNS записи:

| Type  | Name              | Content          | Proxy status  |
| ----- | ----------------- | ---------------- | ------------- |
| A     | example.com       | your_server_ip   | DNS only      |
| CNAME | panel.example.com | example.com      | DNS only      |
| CNAME | sub.example.com   | example.com      | DNS only      |

2. Настройки SSL/TLS в Cloudflare:
   - Перейдите в раздел SSL/TLS > Overview и выберите Full для параметра Configure.
   - Установите Minimum TLS Version на TLS 1.3.
   - Включите TLS 1.3 (true) в разделе Edge Certificates.
-----
1. Конфигурация прокси сервера:
   - Поддержка автоматического обновления конфигураций через подписку и JSON подписку с возможностью конвертации в форматы для популярных приложений.
2. Настройку обратного прокси NGINX в связке с Xray.
3. Обеспечение безопасности:
   - Автоматические обновления системы через unattended-upgrades.
   - Настройка SSL сертификатов Cloudflare с автоматическим обновлением для защиты соединений.
   - Настройка UFW (Uncomplicated Firewall) для управления доступом.
   - Отключение IPv6 для предотвращения возможных уязвимостей.
   - Шифрование DNS-запросов с использованием systemd-resolved (DoT)
   - Выбор случайного шаблона веб-сайта из массива.
4. Включение BBR — улучшение производительности TCP-соединений.
-----
### Настройка сервера:

Для настройки сервера запустите на нём эту команду:

```
bash <(curl -Ls https://raw.githubusercontent.com/eGamesAPI/remnawave-reverse-proxy/refs/heads/main/install_remnawave.sh)
```

Скрипт проведёт вас через процесс установки, предлагая ввести необходимые данные шаг за шагом. По завершении будет выведена вся необходимая информация.

<p align="center"><a href="#"><img src="./media/remnawave-reverse-proxy.png" alt="Showcase"></a></p>

### Star History

<a href="https://github.com/eGamesAPI/remnawave-reverse-proxy/stargazers">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=eGamesAPI/remnawave-reverse-proxy&type=Date&theme=dark" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=eGamesAPI/remnawave-reverse-proxy&type=Date" />
   <img alt="Stars" src="https://api.star-history.com/svg?repos=eGamesAPI/remnawave-reverse-proxy&type=Date" />
 </picture>
</a>