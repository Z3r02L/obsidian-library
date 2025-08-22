
| Категория             | Ubuntu                                    | Fedora                           | Arch                            | NixOS                                                          |
| :-------------------- | :---------------------------------------- | :------------------------------- | :------------------------------ | :------------------------------------------------------------- |
| Менеджер пакетов      | `apt`                                     | `dnf`                            | `pacman`                        | `nix`                                                          |
| Установка пакета      | `sudo apt install <пакет>`                | `sudo dnf install <пакет>`       | `sudo pacman -S <пакет>`        | `nix-env -i <пакет>`                                           |
| Обновление системы    | `sudo apt update && sudo apt upgrade`     | `sudo dnf upgrade`               | `sudo pacman -Syu`              | `sudo nixos-rebuild switch --upgrade`                          |
| Поиск пакета          | `apt search <пакет>`                      | `dnf search <пакет>`             | `pacman -Ss <пакет>`            | `nix-env -qaP <пакет>`                                         |
| Удаление пакета       | `sudo apt remove <пакет>`                 | `sudo dnf remove <пакет>`        | `sudo pacman -R <пакет>`        | `nix-env -e <пакет>`                                           |
| Система инициализации | systemd                                   | systemd                          | systemd                         | systemd                                                        |
| Конфигурация системы  | Файлы в `/etc/` и `/usr/share/`           | Файлы в `/etc/` и `/usr/share/`  | Файлы в `/etc/` и `/usr/share/` | Конфигурация через `/etc/nixos/configuration.nix`              |
| Файловая система      | ext4, btrfs, xfs                          | ext4, btrfs, xfs                 | ext4, btrfs, xfs                | ext4, btrfs, xfs                                               |
| Обновления ядра       | Через apt-репозитории                     | Через dnf-репозитории            | Через pacman или AUR            | Ядро управляется через nixpkgs и конфигурацию                  |
| Особенности           | Широкое сообщество, удобство для новичков | Частые обновления, современность | Роллинг-релиз, полный контроль  | Управление через декларативную конфигурацию, воспроизводимость |

