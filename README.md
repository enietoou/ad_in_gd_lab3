# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнил:
- Бобоев Азизджон Рахматович
- РИ220935
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

## Цель работы
Ознакомиться с основными операторами языка Python на примере реализации линейной регрессии.

## Задание 1
Предложите вариант изменения найденных переменных для 10 уровней в игре. Визуализируйте изменение уровня сложности в таблице.
Ход работы:
- Поиск переменных для балансировки сложности.
Переменные:
- скорость движение дракона - speed.
- расстояние, проходимое драконом - leftRightDistance.
- время между сбрасыванием яиц - timeBetweenEggDrops.
- шанс изменения направления дракона - chanceDirection.
Таблица с данными - https://docs.google.com/spreadsheets/d/14OHtd97VnuIKNgTDK0dj5kJ0LzoIqVgzUnz4avqF5z0/edit?usp=sharing
![image](https://github.com/enietoou/ad_in_gd_lab3/assets/74960429/a8fb885c-02d5-431a-97ee-ebe2ff519d08)

## Задание 2

Создайте 10 сцен на Unity с изменяющимся уровнем сложности.
Ход работы:
- Создать 9 сцен с изменёнными переменными.




## Задание 3

- Оформляем отчет в виде документации на github (markdown-разметка).
Решение в 80+ баллов должно заполнять google-таблицу данными из Python. В Python данные также должны быть визуализированы.
Ход работы:
- Заполняю таблицу и визуализурую данные с помощью matplotlib.
```py
import gspread
import numpy as np
import matplotlib.pyplot as plt
gc = gspread.service_account(filename='eng-node-405014-6823cc5359d6.json')
sh = gc.open("Workshop3")
sh.sheet1.update('A1', 'Уровень')
sh.sheet1.update('B1', 'speed')
sh.sheet1.update('C1', 'leftRightDistance')
sh.sheet1.update('D1', 'timeBetweenEggDrops')
sh.sheet1.update('E1', 'chanceDirection')
levels = [i for i in range(1,11)]
speed = [4]
leftRightDistance = [10]
timeBetweenEggDrops = [2]
chanceDirection = [0.01]
for i in range(1,10):
    speed.append(speed[i-1]+speed[i-1]/10)
    leftRightDistance.append(leftRightDistance[i-1]+leftRightDistance[i-1]/10)
    timeBetweenEggDrops.append(timeBetweenEggDrops[i-1]-0.1)
    chanceDirection.append(chanceDirection[i-1]+chanceDirection[i-1]/2.5)
for i in range(10):
    sh.sheet1.update('A'+str(i+2), str(levels[i]))
    sh.sheet1.update('B'+str(i+2), str(speed[i]))
    sh.sheet1.update('C'+str(i+2), str(leftRightDistance[i]))
    sh.sheet1.update('D'+str(i+2), str(timeBetweenEggDrops[i]))
    sh.sheet1.update('E'+str(i+2), str(chanceDirection[i]))
print("Update successful!")

levels = np.array(levels)
values1 = np.array(speed)
values2 = np.array(leftRightDistance)
values3 = np.array(timeBetweenEggDrops)
values4 = np.array(chanceDirection)

plt.figure(figsize=(10, 6))

plt.plot(levels, values1, label='speed', marker='o')
plt.plot(levels, values2, label='leftRightDistance', marker='o')
plt.plot(levels, values3, label='timeBetweenEggDrops', marker='o')
plt.plot(levels, values4, label='chanceDirection', marker='o')

plt.xlabel('Уровень')
plt.ylabel('Значение')
plt.title('Multiple Line Plots')
plt.legend()
plt.show()
```
![image](https://github.com/enietoou/ad_in_gd_lab3/assets/74960429/8e4ce122-955c-4241-8864-ee90d0f54ba0)
![image](https://github.com/enietoou/ad_in_gd_lab3/assets/74960429/a59758dd-705c-4144-a624-9394ef9af4c4)


## Выводы

В результате работы я установил программное обеспечение для работы с Python и Unity. Также мной сделан первый шаг в работе с новыми средами разработки - вывод "Hello world!".


**BigDigital Team: Denisov | Fadeev | Panov**
