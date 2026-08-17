# Russian Certificate Rules

Автоматически обновляемый список доменов, использующих сертификаты Национального удостоверяющего центра Минцифры России.


## 📋 Описание

Этот репозиторий содержит актуальный список российских доменов, которые используют сертификаты безопасности, выданные Минцифры России (НУЦ). Такие домены требуют специального браузера с поддержкой российских сертификатов (например, Яндекс Браузер).

## 🎯 Политика проверки сайтов

**Действующая политика: лучше больше, чем меньше.**

При проверке, если сайт не ответил (таймаут, ошибка соединения), он всё равно добавляется в список как "подозрительный". 

**Почему так:**
- Некоторые сайты блокируют автоматические запросы
- Временные сетевые проблемы не должны приводить к потере доменов
- Лучше открыть через Яндекс Браузер "лишний" сайт, чем пропустить нужный

**Исключение:** домены с DNS-ошибками (несуществующие) не добавляются.

## 📁 Файлы

| Файл | Описание | Скачать |
|------|----------|---------|
| `ru-cert-rules.txt` | Список доменов | [📥 Download](https://github.com/PunDeveloper/ru-certs-sites/releases/latest/download/ru-cert-rules.txt) |
| `ru-cert-rules.txt.minisig` | Цифровая подпись | [📥 Download](https://github.com/PunDeveloper/ru-certs-sites/releases/latest/download/ru-cert-rules.txt.minisig) |
| `metadata.json` | Метаданные версии | [📥 Download](https://github.com/PunDeveloper/ru-certs-sites/releases/latest/download/metadata.json) |
| `checksum.sha256` | SHA-256 хэш | [📥 Download](https://github.com/PunDeveloper/ru-certs-sites/releases/latest/download/checksum.sha256) |
| `public.key` | Публичный ключ | [📥 Download](https://github.com/PunDeveloper/ru-certs-sites/releases/latest/download/public.key) |

## 📥 Скачивание

### Последняя версия (всегда актуальная):

```bash
# Правила
curl -L -o ru-cert-rules.txt https://github.com/PunDeveloper/ru-certs-sites/releases/latest/download/ru-cert-rules.txt

# Подпись
curl -L -o ru-cert-rules.txt.minisig https://github.com/PunDeveloper/ru-certs-sites/releases/latest/download/ru-cert-rules.txt.minisig

# Публичный ключ
curl -L -o public.key https://github.com/PunDeveloper/ru-certs-sites/releases/latest/download/public.key
```

## 🔐 Проверка подлинности
```bash
# Установите minisign
# Ubuntu/Debian:
sudo apt install minisign

# macOS:
brew install minisign

# Проверка подписи
minisign -V -p public.key -m ru-cert-rules.txt -x ru-cert-rules.txt.minisig
```
Если всё хорошо, вы увидите:
```
Signature and comment signature verified
Trusted comment: timestamp:1234567890 file:ru-cert-rules.txt
```
## 📊 Статистика

- **Обновлено:** Автоматически каждые 24 часа
- **Источники:** v2fly/domain-list-community (category-ru и другие российские категории)
- **Формат:** domain-suffix (применяется к домену и всем поддоменам)

## 💻 Использование

Android (Kotlin):
```kotlin
val rules = download("https://github.com/PunDeveloper/ru-certs-sites/releases/latest/download/ru-cert-rules.txt")
val signature = download("https://github.com/PunDeveloper/ru-certs-sites/releases/latest/download/ru-cert-rules.txt.minisig")

if (verifySignature(rules, signature, publicKey)) {
    loadRules(rules)
}
```

## 🔒 Безопасность

✅ Все файлы подписываются криптографически (Ed25519)  
✅ Проверка целостности через SHA-256  
✅ Автоматическое обновление

**Что это даёт:**
- Защита от MITM-атак при скачивании
- Гарантия, что файлы не были изменены
- Доверие к источнику данных


### Источники данных

Список формируется автоматически на основе:
v2fly/domain-list-community (категории: category-ru, category-gov-ru, category-bank-ru, и др.) <br>
Российские бренды: yandex, vk, mailru-group, sberbank, wildberries и др.

## ⚠️ Отказ от ответственности
Проект предоставляется "как есть" (as is). Авторы не несут ответственности за возможные ошибки или неточности в списке.  <br>
Рекомендуется всегда проверять цифровую подпись перед использованием.

## 📄 Лицензия

MIT License - см. файл LICENSE

## 🔗 Ссылки

- [GitHub Releases](https://github.com/PunDeveloper/ru-certs-sites/releases)
- [Minisign](https://jedisct1.github.io/minisign/)
- [v2fly/domain-list-community](https://github.com/v2fly/domain-list-community)
