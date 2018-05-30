---
title       : Работа с датасетом
description : Insert the chapter description here


---
## Знакомство с датасетом

```yaml
type: NormalExercise
key: 02f6b64164
lang: r
xp: 100
skills: 1
```

Перед работой с любым датасетом его необходимо обработать и ознакомиться с ним. Датасет `candy` уже загружен в Ваше рабочее пространство.

Данный датасет относительно небольшой, но в будущем Вы можете столкнуться с датасетами, в которых будет более тысячи наблюдений и десятки переменных, поэтому для примерного знакомства Вам будет достаточно первых несколько наблюдений. Встроенная функция 'head()' выводит в консоль первые 6 наблюдений, что позволяет ознакомиться со всеми переменными и сложить представление о датасете, однако количество выводимых наблюдений можно уточнить внутри самой функции. 

Иногда взгляда на первые наблюдения может быть недостаточно, тогда для анализа датасета можно использовать функцию 'describe()' из библиотеки psych, которая формирует краткий отчёт по каждой переменной. Вы можете подробнее ознакомиться с её выводом, выполнив задание.

`@instructions`

- Загрузите библиотеку psych с помощью функции library()
- Проанализируйте данный датасет.
- Выгрузите первые 10 наблюдений.

`@hint`
- Используйте функции describe() и head()

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
```

`@sample_code`
```{r}
# подключите библиотеку psych
___(psych)

# проанализируйте данный датасет
___(___)

# выгрузите первые 10 наблюдений
___(___, 10)
```

`@solution`
```{r}
# подключите библиотеку psych
library(psych)

# проанализируйте данный датасет
describe(candy) 

# выгрузите первые 10 наблюдений
head(candy, 10)
```

`@sct`
```{r}
#first instruction
test_student_typed("library(psych)", not_typed_msg = "Вы не подгрузили библиотеку psych. Внимательно прочтите инструкцию")

#second instruction
test_student_typed("describe(candy)", not_typed_msg = "Возникла проблема с анализом датасета. Внимательно прочтите инструкцию.")

#third instruction
test_student_typed("head(candy, 10)", not_typed_msg = "Возникла проблема с выгрузкой первых 10 наблюдений. Внимательно прочтите инструкцию.")

#General
test_error()
success_msg("Отлично! Пришло время проверить, как хорошо Вы познакомились с датасетом.")
```


---
## Анализ датасета

```yaml
type: MultipleChoiceExercise
key: 23da8e3911
lang: r
xp: 50
skills: 1
```
Какое из этих утверждений верное?

`@instructions`

- В этом датасете 79 наблюдений
- Самая высокая оценка шоколадки - 91%
- В среднем в этих шоколадках 47% сахара
- В этом датасете 12 переменных

`@hint`

- Используйте упомянутую ранее функцию describe()

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
library(psych)

```

`@sct`
```{r}
msg1 <- "Неверно. Посмотрите на значение n."
msg2 <- "Не совсем. Посмотрите на максимальное значение переменной winpercent."
msg4 <- "Неправильно. Посмотрите, сколько названий переменных Вы видите при анализе датасета."
msg3 <- "Замечательно! Теперь Вы познакомились с датасетом и готовы начать более подробный анализ."

test_mc(3, feedback_msgs = c(msg1, msg2, msg3, msg4))

#General
test_error()
success_msg("Замечательно! Теперь Вы познакомились с датасетом и готовы начать более подробный анализ.")
```



---

## Работа с выборочными характеристиками

```yaml
type: NormalExercise
key: 32455795f4
lang: r
xp: 100
skills: 1
```

Из предыдущих глав Вы можете помнить, что такое выборочные характеристики, пришло время отработать эти знания на датасете. 

Следует помнить, что некоторые выборочные характеристики (например, среднее) можно считать только по числовым переменным. Если же в Вашем датасете _df_ переменная _gender_ принимает значения "М" и "Ж", то Вы не сможете посчитать долю женщин, но если эта переменная будет принимать значения "0" и "1", то Вы сможете воспользоваться функцией  `mean(df$gender)`.

`@instructions`
- Посчитайте среднюю долю карамели в конфетах.
- Посчитайте дисперсию доли шоколада в конфетах.
- Посчитайте медиану процента стоимости конфет.

`@hint`
- Если Вы забыли названия переменных, загрузите библиотеку psych и воспользуйтесь функцией describe().

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
```

`@sample_code`
```{r}
# Средняя оценка карамельности
___(___)

# Дисперсия оценки шоколадности
___(___)

# Медиана стоимости конфет
___(___)
```

`@solution`
```{r}
# Средняя оценка карамельности
mean(candy$caramel)

# Дисперсия оценки шоколадности
sd(candy$chocolate)

# Медиана стоимости конфет
median(candy$pricepercent)
```

`@sct`
```{r}

```


---
## Визуализация данных

```yaml
type: NormalExercise
key: 9b02ed8ddb
lang: r
xp: 100
skills: 1
```
При работе с реальными данными практически никогда нельзя сделать вывод, глядя на сухие числа. У Вас должна сформироваться привычка всегда визуализировать данные, потому что тогда Вы сможете обнаружить зависимости, которые не видно при анализе таблицы или потока чисел. В данном курсе Вы будете использовать самые простые методы визуализации, но их вполне бывает достаточно для первичного анализа.

`@instructions`
- Загрузите библиотеку ggplot2.
- Постройте гистограмму пользовательских оценок (winpercent), установив binwidth, равным 7.

`@hint`
Для построения гистограммы после + вызовите функцию 'geom_histogram()'.

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
```
`@sample_code`
```{r}
#загрузка библиотеки
___(___)

#построение гистограммы
ggplot(data = ___, aes(x = ___)) +
___(binwidth = ___)
```
`@solution`
```{r}
#загрузка библиотеки
library(ggplot2)

#построение гистограммы
ggplot(data = candy, aes(x = winpercent)) +
  geom_histogram(binwidth = 7)
```
`@sct`
```{r}
#first instruction
test_student_typed("library(ggplot2)", not_typed_msg = "Возникла проблема с загрузкой библиотеки. Вы воспользовались функцией 'library()'?")

#second instruction
test_student_typed("ggplot(data = candy, aes(x = winpercent)) + geom_histogram(binwidth = 7)", not_typed_msg = "Возникла проблема с построением гистограммы. Проверьте, установлена ли правильная ширина bins и правильность анализируемой переменной.")

#General
test_error()
success_msg("Превосходно! Вы можете попрактиковаться в выборе ширины bin и посмотреть, как от этого меняется результат.")
```



---
## Вид распределения

```yaml
type: MultipleChoiceExercise
key: a6eaf579fe
lang: r
xp: 50
skills: 1
```
На какое из известных распределений приблизительно похоже распределений пользовательских оценок?

`@instructions`
- Хи-квадрат
- Нормальное
- Биномиальное с вероятностью 0.8


`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
library(ggplot2)
ggplot(data = candy, aes(x = winpercent)) +
  geom_histogram(binwidth = 7)
```


`@sct`
```{r}
msg1 <- "Неверно."
msg2 <- "Отлично!"
msg3 <- "Неправильно."

test_mc(c(2, 3), feedback_msgs = c(msg1, msg2, msg3))

#General
test_error()
success_msg("Отлично!")
```


---
## Разница между медианой и средним

```yaml
type: NormalExercise
key: 3c69ba8592
lang: r
xp: 100
skills: 1
```
В предыдущих главах Вы уже изучили разницу между медианой и средним. При наличии какого-то сильного выброса значение среднего может сильно сдвинуться и уже не будет подходить для анализа. Увидеть это, не визуализируя данные, практически невозможно, поэтому мы ещё раз обращаем внимание на необходимость отображения данных на графике.

`@instructions`
- Выведите значение среднего и медианы пользовательских оценок 
- Постройте график гистограммы пользовательских оценок, установив количество bins, равных 10 (библиотека ggplot2 уже загружена)
- Отобразите на ней среднее красным цветом (“red”) с прозрачностью 0.4, а медиану – зелёным (“green”) цветом с прозрачностью 0.2


`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
library(ggplot2)
```
`@sample_code`
```{r}
# Среднее значение пользовательских оценок
mean_win <- ___(___)
mean_win

# Медиана пользовательских оценок
median_win <- ___(___)
median_win

# Гистограмма с отображёнными значениями среднего и медианы
ggplot(___, aes(___)) +
   ___(bins = 10) +
  geom_vline(xintercept = ___, col = "___", alpha = ___) +
  geom_vline(xintercept = ___, col = "___", alpha = ___)
```
`@solution`
```{r}
# Среднее значение пользовательских оценок
mean_win <- mean(candy$winpercent)
mean_win

# Медиана пользовательских оценок
median_win <- median(candy$winpercent)
median_win

# Гистограмма с отображёнными значениями среднего и медианы
ggplot(data = candy, aes(x = winpercent)) +
  geom_histogram(bins = 10) +
  geom_vline(xintercept = mean_win, col = "red", alpha = 0.4) +
  geom_vline(xintercept = median_win, col = "green", alpha = 0.2)
```
`@sct`
```{r}

```


