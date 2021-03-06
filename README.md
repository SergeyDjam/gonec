[![GitHub issues](https://img.shields.io/github/issues/covrom/gonec.svg)](https://github.com/covrom/gonec/issues) [![Travis](https://travis-ci.org/covrom/gonec.svg?branch=master)](https://github.com/covrom/gonec/releases)

# ГОНЕЦ (gonec)
## Интерпретатор и платформа создания микросервисов на 1С-подобном языке

[![Gonec Logo](/gonec.png)](https://github.com/covrom/gonec/releases)

[![Download](/button_down.png)](https://github.com/covrom/gonec/releases)
[![Docs](/button_doc.png)](https://github.com/covrom/gonec/wiki)
[![Demo](/button_play.png)](https://gonec.herokuapp.com/)

## Цели

Интерпретатор создан для решения программистами 1С множества задач, связанных с высокопроизводительными распределенными вычислениями, создания вэб-сервисов и вэб-порталов для работы сотен тысяч пользователей, работы с высокоэффективными key-value базами данных с использованием синтаксиса языка, похожего, но не ограниченного возможностями языка 1С.

Включив такой интерпретатор в свое решение, Вы можете предоставить высокий уровень сервиса для своих клиентов, который обгонит решения не только ваших конкурентов на рынке 1С, но и конкурентных платформ в enterprise (SAP Cloud) и в web (node.js).

Интерпретатор разрабатывается “от простого к сложному”. На начальных этапах будет включена базовая функциональность многопоточных вычислений и сетевых сервисов. В перспективе планируется организация работы с различными базами данных и визуализация управляемых форм, созданных в конфигураторе.

Еще никогда не были так просто доступны программистам 1С возможности:
* Создать микросервис с произвольным сетевым протоколом, развернуть его на linux, в docker контейнере или кластере kubernetes
* Выполнить сложную многопоточную вычислительную задачу для десятков тысяч подключающихся пользователей за миллисекунды
* Взаимодействовать с пользователем через web-браузер с минимальным трафиком
* Сохранять и получать данные с максимально доступной скоростью в key-value базах данных

## Описание синтаксиса языка и примеры использования интерпретатора

[Документация находится здесь](https://github.com/covrom/gonec/wiki)

## Почему синтаксис похож на 1С?

Синтаксис 1С знаком и удобен сотням тысяч программистов в России и СНГ, а в перспективе и зарубежом. Это позволяет создавать решения, которые могут поддерживаться любыми программистами 1С, и которые не будут требовать дополнительной квалификации.

Интерпретатор поддерживает синтаксис языка платформы 1С:Предприятие 8.3, за исключением объектов метаданных и глобальных объектов - в интерпретаторе, по понятным причинам, используются свои объекты.

## Какие основные отличия от языка 1С?
Язык интерпретатора поддерживает синтаксис языка 1С, но дополнительно к этому имеет возможности, унаследованные от синтаксиса языка Go (Golang), поскольку в основе интерпретатора используется парсер от этого языка:
* Впервые для 1С! Многопоточное программирование: создание и работа с параллельно выполняемыми функциями и каналами передачи информации между ними (полный аналог chan и go из языка Го)
* Поддержка срезов массивов и строк, как в языке Python (высокоскоростная реализация на слайсах Go)
* Поддержка множества возвращаемых значений из функций и множественного присваивания между переменными (а,б=б,а) как в языке Go
* Возможность указания структурных литералов и содержимого массивов прямо в исходном коде (как в Go)
* Передача функций как параметров (функциональное программирование)

## Каковы отличия в метаданных и среде исполнения?
На первом этапе разработки планируется:
* поддержка стандартной библиотеки Go в части создания вэб-сервисов с html-шаблонами
* поддержка и работа с boltdb и postgresql
* мултиплатформенность: выполнение кода на любой платформе (Windows, Linux, MacOs)
* выполнение в легковесных ОС alpinelinux
* запуск на встраиваемых устройствах с низким энергопотреблением класса "умный дом"/"интернет вещей" (например, Raspberry Pi)
* запуск в контейнерах docker

## Какова производительность интерпретатора?
Производительность ожидается сравнимой или выше, чем у интерпретатора языка Python.
Скорость интерпретации кода соответствует скорости компиляции программ на Go и скорости работы библиотек, написанных на Go.
А эта скорость, в свою очередь, сопоставима с разработкой на чистом Си.

## Какая технологическая основа используется в интерпретаторе?
Интерптетатор реализован на языке Go путем адаптации исходных кодов очень быстрого и стабильного интерпретатора языка anko (https://github.com/mattn/anko).
Таким образом, поскольку компилятор Go считается самым высокоскоростным из всех существующих на сегодняшний день, то и интерпретатор будет работать максимально эффективно.
Интерпретатор использует собственную виртуальную машину, также написанную на языке Go, а значит, имеющую производительность не ниже системы виртуализации контейнеров docker, которая так же написана на Go.

## Какой статус разработки интерпретатора?
Интерпретатор находится в стадии разработки.
Первая версия уже работает!
В ближайшее время планируется описание расширенного синтаксиса языка.
