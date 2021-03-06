# Task description

# Задание #2 Автоматизация этапов разработки

Особенности распределённой системы:

1. Множество независимо исполняющихся (и зачастую независимо обновляемых) компонентов.
2. Множество связей между компонентами.
3. Связям характерно наличие множества динамически меняющихся атрибутов (адреса служб, версии протоколов и пр).

## Agile, CI/CD, DevOps

Процесс промышленной разработки программного продукта вовлекает специалистов разных областей - это дизайнеры, 
разработчики, тестировщики, аналитики и пр. 

Для повышения эффективности разработки ПО выработано множество подходов, среди которых наибольшее распространение 
в последнее время получила "гибкая методология разработки" (**Agile**). *Agile* подразумевает постоянное общение вовлечённых в разработку специалистов, разработку и доставку функционала пользователям небольшими итерациями с постоянной корректировкой приоритетов задач и готовностью к изменениям.

Термин **CI/CD** означает практику непрерывной интеграции (*CI - Continious Integration*) и непрерывной доставки (*CD - Continious Delivery*) программного продукта конечным пользователям.

**DevOps** (от *Development* + *Operations*) означает, с одной стороны, культуру взаимодействия в команде разработки, с другой - набор инструментов, реализующих эту культуру взаимодействия. *DevOps* определяет соглашение пользованием системой контроля версий, системой ведения задач, инструментами сборки и доставки и т.п.


## Семантическое версионирование (Semantic Versioning)

https://semver.org/

Семантическое версионирование предписывает определённые правила назначения версии компонента или продукта.

Номер версии имеет вид *MAJOR.MINOR.PATCH*, в котором отдельные части увеличиваются:
1. MAJOR - когда присутствуют несовместимые изменния в API компонента;
2. MINOR - появился новый функционал, но сохранилась обратная совместимость в API;
3. PATCH - исправление ошибок.

В дополнение к *MAJOR.MINOR.PATCH* номер версии может содержать пререлизные, альфа, бета и другие метки.

## Задание

Требуется разработать скрипты автоматизации сборки и разворачивания вашей системы:

1. *build.cmd* – скрипт компиляции и сборки пакета для разворачивания.
Входной параметр – номер версии программного продукта в формате SemVer.
Результат работы – папка с бинарными файлами компонентов системы с именем *product-semver_version*. В корне папки лежат *start* и *stop*-скрипты, о которых ниже, 
а также должна находится папка *config*, где в последующем будут находиться конфигурационные файлы приложения;
2. *start.cmd* – запуск компонентов системы. Параметры запуска, такие как используемые порты, адреса служб, должны браться из конфигурационного файла в папке *config*;
3. *stop.cmd* – завешршение работы компонентов системы.

В качестве альтернативы *cmd* можно использовать *PowerShell*, *bash* или другой язык командной оболочки.

### Задание с повышающим коэффициентом

Сборка и разворачивание системы производится с помощью Docker-контейнеров

https://docs.microsoft.com/ru-ru/aspnet/core/host-and-deploy/docker/building-net-docker-images?view=aspnetcore-3.1

1. *build*-скрипт вместо папки с бинарными файлама собирает образ контейнера с указанной версией в качестве тега;
2. *start/stop*-скрипты запускают и останавливают соответствующие Docker-контейнеры.
