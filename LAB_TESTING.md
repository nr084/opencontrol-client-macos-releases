# Experimental VPN test / Экспериментальный тест VPN

0.2.0-lab.1 · Universal 2 · macOS 13+. Ad-hoc signed, not notarized.
**Активация расширения и реальный VPN пока не проверены.**
**Extension activation and live VPN traffic have not yet been verified.**

## Русский

1. Выключите Mac. На Apple Silicon удерживайте кнопку питания до параметров
   загрузки и выберите «Параметры». На Intel загрузитесь с Command-R.
2. В Recovery откройте «Утилиты → Терминал», выполните `csrutil disable`,
   следуйте запросам системы и перезагрузитесь. Это снижает защиту всей macOS.
   FileVault, Gatekeeper и AMFI отключать не нужно.
3. Проверьте `csrutil status`: ожидается `disabled`. Для разработки можно
   включить `sudo systemextensionsctl developer on`; сама эта команда не
   снимает проверки подписи.
4. Установите лабораторный PKG в /Applications. Если macOS блокирует
   незаверенный установщик, используйте системное «Открыть всё равно»
   в настройках конфиденциальности и безопасности.
5. Запустите приложение, создайте профиль своего сервера, проверьте отпечаток
   сертификата по доверенному каналу и подключитесь. Подтвердите системные
   запросы на расширение и VPN, перезагрузитесь, если macOS потребует.
6. Проверьте `systemextensionsctl list`: для
   `org.opencontrol.macos.PacketTunnel` ожидается `activated enabled`.
   Затем отдельно проверьте корпоративный ресурс, DNS, маршруты,
   отключение и восстановление сети. Активация ещё не доказывает работу VPN.
7. При ошибке сохраните её точный текст без паролей. Дальнейшие ослабления
   защиты автоматически не применяются: сначала разбирается причина.

После теста отключите VPN, выполните «Настройки → Подготовить удаление»
и запустите `Uninstall OpenControl Client.command`. Перезагрузитесь, если
потребуется. Выполните `sudo systemextensionsctl developer off`, затем
в Recovery — `csrutil enable`. После перезагрузки проверьте `csrutil status`.

## English

Boot into Recovery (hold power on Apple Silicon; Command-R on Intel), open
Terminal, run `csrutil disable` and reboot. This reduces system-wide protection.
Verify `csrutil status`. Optionally run `sudo systemextensionsctl developer on`;
this alone does not bypass signature checks. Do not disable FileVault, Gatekeeper
or AMFI. Install the lab PKG into /Applications, launch the app, configure your
authorized server, verify its certificate fingerprint and approve extension/VPN
prompts. Reboot if requested. Check `systemextensionsctl list`, then test actual
traffic, DNS, routes and network recovery. Report exact errors without credentials.

After testing, disconnect, prepare removal in Settings and run the uninstaller.
Reboot if requested, disable developer mode, run `csrutil enable` in Recovery,
reboot and verify SIP status. This is an experimental prerelease, not a production
release. Build/signature checks do not establish live VPN acceptance.

[Apple: testing system extensions](https://developer.apple.com/documentation/driverkit/debugging-and-testing-system-extensions)
· [Apple: SIP](https://developer.apple.com/documentation/security/disabling-and-enabling-system-integrity-protection)
