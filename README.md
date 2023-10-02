# Отчет по практиечской работе номер-2 "Идентификация и аутентификация"

## Задача

В данном задании выполнены следующие шаги:

1. Создана виртуальная машина на базе ОС Debian 12.
2. Создан пользователь `super-{Kuzina.A.S}` и наделен привилегиями суперпользователя.
3. Создана группа `group-{Miread}`.
4. Добавен пользователь `super-{Kuzina.A.S}` в группу `group-{Miread}`.
5. Проверено наличие пользователя в группе.
6. Создан пользователь `user-{Kuzina.A.S}` и добавен в группу `group-{Miread}`.
7. Наделен полномочиями пользователь `user-{Kuzina.A.S}` по созданию и удалению файлов в домашнем каталоге пользователя `super-{Kuzina.A.S}` с использованием механизма разграничения доступа `chmod`.
8. Продемонстрирована работа механизмов разграничения доступа.

## Шаги выполнения

```bash
# Шаг 2
root@Debian:~# sudo useradd super-{Kuzina.A.S}
root@Debian:~# passwd super-{Kuzina.A.S}
root@Debian:~# usermod -aG sudo super-{Kuzina.A.S}

# Шаг 3
root@Debian:~# groupadd group-{Miread}

# Шаг 4
root@Debian:~# usermod -aG group-{Miread} super-{Kuzina.A.S}

# Шаг 5
root@Debian:~# groups super-{Kuzina.A.S}

# Шаг 6
root@Debian:~# useradd user-{Kuzina.A.S}
root@Debian:~# usermod -aG group-{Miread} user-{Kuzina.A.S}

# Шаг 7
root@Debian:~# chmod 770 /home/super-{Kuzina.A.S}
root@Debian:~# chown super-{Kuzina.A.S}:group-{Miread} /home/super-{Kuzina.A.S}

# Шаг 8
$ su user-{Kuzina.A.S}
$ touch /home/super-{Kuzina.A.S}/test_file.txt
$ rm /home/super-{Kuzina.A.S}/test_file.txt

```


[Скриншот 1 - Команды в терминале для представленных выше шагов ]

![Скриншот 1 - Команды в терминале ](https://i.imgur.com/rjZxR1q.png)
