# backend_for_sane_people

C++ Moscow №0: «‎бэкенд на плюсах для нормальных людей»‎

В рамках доклада был совершен обзор трех самых популярных и функциональных плюсовых веб-фреймворков: [drogon](https://github.com/cppmoscow/drogon_sample), [oat++](https://github.com/cppmoscow/oat_sample) и [userver](https://github.com/cppmoscow/userver_sample).

Кроме того, на всех из них был реализован крошечный pastebin сервис с минимальной функциональностью: добавление, обновление, удаление и получение паст. Репозитории: [drogon_sample](https://github.com/cppmoscow/drogon_sample), [oat_sample](https://github.com/cppmoscow/oat_sample), [userver_sample](https://github.com/cppmoscow/userver_sample).

## LOC metrics

| Место | Фреймворк | Lines of code | % |
| ----- | --------- | ------------- | - |
| 1     | userver   | 162 LOC       | 100 |
| 2     | Drogon    | 165 LOC       | 101 |
| 3     | Oat++     | 310 LOC       | 191% |

![image](https://github.com/cppmoscow/backend_for_sane_people/assets/47888628/e82ba3fd-53e0-40a1-879b-995749011c80)

## Performance metrics

Для простоты сравнение производилось следующим образом:

1. В базу данных помещалось содержание заголовочного файла [array](https://github.com/llvm/llvm-project/blob/main/libcxx/include/array)
2. Производилось стрессовое тестирование с помощью инструмента `drogon_ctl` с следующими параметрами: количество запросов — 10 тысяч, количество одновременных соединений — 100, количество потоков — 4. Сначала сервера разогревались тестовым прогоном, дальше делалось еще пять прогонов, и за результат бралось их среднее.

| Место | Фреймворк | Requests per second | % |
| ----- | --------- | ------------------- | - |
| 1     | userver   | 39547 RPS           | 100% |
| 2     | Drogon    | 35890 RPS           | 90%  |
| 3     | Oat++     | 31512 RPS           | 79%  |

![image](https://github.com/cppmoscow/backend_for_sane_people/assets/47888628/574bc817-2160-485b-a089-ddfdedaf8587)
