---
title: Выборочные характеристики
description: This is a template chapter.
---

## Задание 2.1

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 2
key: dbe164cc29
```

В этой главе мы научимся вычислять основные выборочные характеристики при помощи *R*. Будем работать с датасетом faithful, который содержит данные о продолжительности `eruptions`  и времени ожидания `waiting` между извержениями гейзера Старый Служака. Давайте посмотрим на распределение времени ожидания извержения гейзера. Для этого построим эмпирическую функцию распределения.
Для построения Вам необходимо вспомнить, что такое вариационный ряд
$$ X_(n-1) \le X_(n-1) $$ ##дописать

`@instructions`
- Для визуализации данных загрузите пакет `ggplot2`.
- Посчитатйте число наблюдений (количество строк в матрице `nrow()`).
- Постройте вариационный ряд значений времени ожидания.  Полученные значения сохраните в переменную `x_ecdf`.
- Сгенерируйте значения функции распределения и сохраните их в переменную `y_cdf`.
- С помощью функции `ggplot2()` постройте эмпирическую функцию распределения. Вам нужно указать оси `mapping = aes(x=  , y=   )`. Тип графика  - `geom_line()`.


`@hint`
- Here is the hint for this setup problem. It should get students 50% of the way to the correct answer.

`@pre_exercise_code`

```{r}
# Load datasets and packages here.
#library(datasets)
#datasets('faithful')
#data <- faithful


```

`@sample_code`

```{r}
# Загрузите пакет для визуализации 
# sample
# code
# should
# be
# ideally
# 10 lines or less,
# with a max
# of 16 lines.
```

`@solution`

```{r}
#Загрузите пакет для визуализации данных
library(ggplot2)
#Найдите число наблюдений
n <- nrow(faithful)
#Постройте вариационный ряд значений времени ожидания
x_ecdf <- sort(faithful$waiting, decreasing = FALSE)
#Сгенерируйте значения выборочной функции распределения
y_ecdf <- seq(from = 1, to = n, by=1)/n
#Постройте выборочную функцию распределения
ggplot(mapping = aes(x_ecdf, y_ecdf)) + geom_line() + labs(title = 'Эмпирическая функция распределения', x = 'Время ожидания', y = 'F(x)')+theme(plot.title = element_text(hjust = 0.5))

```

`@sct`

```{r}
# Update this to something more informative.
success_msg("Some praise! Then reinforce a learning objective from the exercise.")
```
