# Конфиденциальность / Privacy

Дата / Date: 2026-10-15. Применяется к разрабатываемой версии 0.1.0.

## Русский

OpenControl Client подключает Mac к частному серверу, указанному пользователем.
Проект не предоставляет аккаунты или открытые VPN-серверы. При подключении сервер
получает логин, пароль внутри защищённого TLS-канала, метаданные соединения и
трафик, направленный через VPN. Администратор сервера определяет его обработку.

Профили и настройки сохраняются локально. Пароль сохраняется в macOS Keychain
только при выбранной опции. Для активной сессии пароль передаётся расширению через
временные параметры запуска, а не сохраняется в VPN-конфигурации. Данные профилей
не синхронизируются приложением через облако. В приложении нет рекламы, аналитики
и телеметрии. События соединения хранятся в ограниченном списке в памяти без паролей
и содержимого трафика.

Проверка сертификата связывается только с указанным сервером и не отправляет
учётные данные. QR-код профиля содержит пароль: экспорт выполняется по запросу
пользователя с предупреждением. Импорт изображения выполняется локально.

Профили и пароли можно удалить в настройках. Обычное удаление приложения сохраняет
их, если отдельная очистка не выбрана. Публичные issues GitHub открыты всем;
не публикуйте в них конфиденциальные данные. Ссылки на GitHub обслуживаются GitHub
по его собственной политике.

## English

OpenControl Client connects your Mac to a private server you specify. The project
provides no accounts or public VPN service. During connection, your server receives
credentials through TLS, connection metadata and traffic routed through the VPN.
The server administrator controls its processing.

Profiles/settings stay local. Passwords are saved in macOS Keychain only when you
choose to remember them. The active session receives the password through transient
start options, never persisted VPN configuration. The app does not sync profiles
through cloud services and contains no advertising, analytics or telemetry.
Connection events are held in a bounded in-memory list without credentials or payloads.

Certificate inspection contacts the specified server without sending credentials.
Profile QR codes include passwords and are shown only on request with a warning;
image import is local. Settings can erase profiles and Keychain entries. Ordinary
app removal retains them unless explicit cleanup is selected. GitHub issues are
public: never post sensitive information. GitHub links are subject to GitHub's own policy.
