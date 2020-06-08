[![Build Status](https://travis-ci.com/STaRiCHDED/Lab04.svg?branch=master)](https://travis-ci.com/STaRiCHDED/Lab04)
## Laboratory work IV

<a href="https://yandex.ru/efir/?stream_id=vCgeA9EiySzw"><img src="https://raw.githubusercontent.com/tp-labs/lab04/master/preview.png" width="640"/></a>

Данная лабораторная работа посвещена изучению систем непрерывной интеграции на примере сервиса **Travis CI**

```sh
$ open https://travis-ci.org
```

## Tasks

- [x] 1. Авторизоваться на сервисе **Travis CI** с использованием **GitHub** аккаунта
- [x] 2. Создать публичный репозиторий с названием **lab04** на сервисе **GitHub**
- [x] 3. Ознакомиться со ссылками учебного материала
- [x] 4. Включить интеграцию сервиса **Travis CI** с созданным репозиторием
- [x] 5. Получить токен для **Travis CLI** с правами **repo** и **user**
- [x] 6. Получить фрагмент вставки значка сервиса **Travis CI** в формате **Markdown**
- [x] 7. Выполнить инструкцию учебного материала
- [x] 8. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial
```sh
$ export GITHUB_USERNAME=STaRiCHDED
$ export GITHUB_TOKEN=*************************************
$ cd ${GITHUB_USERNAME}/workspace
$  pushd .
~/STaRiCHDED/workspace ~/STaRiCHDED/workspace
$ source scripts/activate
$ git clone https://github.com/${GITHUB_USERNAME}/Lab03 projects/Lab04
Клонирование в «projects/Lab04»…
$ cd projects/Lab04
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/Lab04
$ cat > .travis.yml <<EOF
> language: cpp
> EOF
$ cat >> .travis.yml <<EOF
> 
> script:
> - cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
> - cmake --build _build
> - cmake --build _build --target install
> EOF
$ cat >> .travis.yml <<EOF
> 
> addons:
>   apt:
>     sources:
>       - george-edison55-precise-backports
>     packages:
>       - cmake
>       - cmake-data
> EOF
$ travis login --github-token ${GITHUB_TOKEN}
Successfully logged in as STaRiCHDED!
$ travis lint
Hooray, .travis.yml looks valid :)
$ ex -sc '1i|[![Build Status](https://travis-ci.com/STaRiCHDED/Lab04.svg?branch=master)](https://travis-ci.com/STaRiCHDED/Lab04)' -cx README.md
$ cat README.md
$ git add .travis.yml
$ git add README.md
$ git commit -m"added CI"
$ git push origin master


$ travis lint # Проверяет.travis.yml на ошибки, предупреждения
$ travis accounts # Отображает всех учетных записей, для которых можно настроить репозиторий
$ travis sync # Запускает новую синхронизацию с GitHub
$ travis repos # Перечисляет репозитории, на которые пользователь имеет определенные разрешения.
$ travis enable # Активирует проект на TravisCI
$ travis whatsup # Перечисляет самые последние изменения
$ travis branches # Показывает последнюю информацию для каждой ветки
$ travis history # Выводит историю сборки проектов
$ travis show # Отображает общую информацию о последней сборке
```

## Links

- [Travis Client](https://github.com/travis-ci/travis.rb)
- [AppVeyour](https://www.appveyor.com/)
- [GitLab CI](https://about.gitlab.com/gitlab-ci/)

```
Copyright (c) 2015-2020 The ISC Authors
```
