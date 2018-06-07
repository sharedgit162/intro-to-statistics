---
  title: "Работа с датасетом"
  description: "В данной главе Вы сможете отработать все полученные знания на практике, проанализировав реальный датасет Candy, в котором собраны характеристики различных конфет для Хэллоуина."
  v2: true


---
## Начало работы

```yaml
type: VideoExercise
key: da7a060dd1
lang: r
xp: 50
skills: 1
video_link: https://dl.dropboxusercontent.com/s/338ibvuf7unej0a/3%20%D0%B3%D0%BB%D0%B0%D0%B2%D0%B0.mp4?dl=0
```

---
## Знакомство с датасетом

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 1
key: 02f6b64164



```

Перед работой с любым датасетом его необходимо обработать и ознакомиться с ним. Датасет `candy` уже загружен в Ваше рабочее пространство.

Данный датасет относительно небольшой, но в будущем Вы можете столкнуться с датасетами, в которых будет более тысячи наблюдений и десятки переменных, поэтому для примерного знакомства Вам будет достаточно первых несколько наблюдений. Встроенная функция `head()` выводит в консоль первые 6 наблюдений, что позволяет ознакомиться со всеми переменными и сложить представление о датасете, однако количество выводимых наблюдений можно уточнить внутри самой функции. 

Иногда взгляда на первые наблюдения может быть недостаточно, тогда для анализа датасета можно использовать функцию `describe()` из библиотеки psych, которая формирует краткий отчёт по каждой переменной. Вы можете подробнее ознакомиться с её выводом, выполнив задание.

`@instructions`
- Загрузите библиотеку psych с помощью функции `library()`
- Проанализируйте данный датасет.
- Выгрузите первые 10 наблюдений.

`@hint`
- Используйте функции `describe()` и `head()`.

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
test_student_typed("library(psych)", not_typed_msg = "Возникла проблема с подключением библиотеки `psych`.")

#second instruction
test_student_typed("describe(candy)", not_typed_msg = "Возникла проблема с функцией `describe()`.")

#third instruction
test_student_typed("head(candy, 10)", not_typed_msg = "Возникла проблема с выгрузкой первых 10 наблюдений.")

#General
test_error()
success_msg("Отлично! Пришло время проверить, как хорошо Вы познакомились с датасетом.")
```




---
## Анализ датасета

```yaml
type: MultipleChoiceExercise
lang: r
xp: 50
skills: 1
key: 23da8e3911



```

Какое из этих утверждений верное?

`@instructions`
- В этом датасете 79 наблюдений
- Самая высокая оценка шоколадки - 91%
- В среднем в этих шоколадках 48% сахара
- В этом датасете 12 переменных

`@hint`
- Используйте упомянутую ранее функцию `describe()`.

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
library(psych)
```


`@sct`
```{r}
msg1 <- "Попробуйте ещё раз. Посмотрите на значение переменной `n`."
msg2 <- "Не совсем. Посмотрите на максимальное значение переменной `winpercent`."
msg4 <- "Попробуйте ещё раз. Посмотрите на значения переменной `vars`."
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
lang: r
xp: 100
skills: 1
key: 90c2b0ba64



```

Из предыдущих глав Вы можете помнить, что такое выборочные характеристики, пришло время отработать эти знания на датасете. 

Следует помнить, что некоторые выборочные характеристики (например, среднее) можно считать только по числовым переменным. Если же в Вашем датасете `df` переменная `gender` принимает значения "М" и "Ж", то Вы не сможете посчитать долю женщин, но если эта переменная будет принимать значения "0" и "1", то Вы сможете воспользоваться функцией  `mean(df$gender)`.

`@instructions`
- Посчитайте среднюю долю карамели в конфетах.
- Посчитайте стандартное отклонение доли шоколада в конфетах.
- Посчитайте медиану процента стоимости конфет.

`@hint`
- Если Вы забыли названия переменных, загрузите в консоли библиотеку `psych` и воспользуйтесь функцией `describe()`.

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
```
`@sample_code`
```{r}
# Средняя оценка карамельности
mean_caramel <- ___(___)
mean_caramel

# Стандартное отклонение оценки шоколадности
sd_chocolate <- ___(___)
sd_chocolate

# Медиана стоимости конфет
median_price <- ___(___)
median_price
```
`@solution`
```{r}
# Средняя оценка карамельности
mean_caramel <- mean(candy$caramel)
mean_caramel

# Дисперсия оценки шоколадности
sd_chocolate <- sd(candy$chocolate)
sd_chocolate

# Медиана стоимости конфет
median_price <- median(candy$pricepercent)
median_price
```
`@sct`
```{r}
test_object("mean_caramel") %>% check_equal(incorrect_msg = "Проверьте правильность вычисления `mean_caramel`.")
test_object("sd_chocolate") %>% check_equal(incorrect_msg = "Проверьте правильность вычисления `sd_chocolate`.")
test_object("median_price") %>% check_equal(incorrect_msg = "Проверьте правильность вычисления `median_price`.")

#General
test_error()
success_msg("Великолепно! Однако подобное преставление не очень наглядно, в следующих упражнениях у Вас будет возможность визуализировать некоторые показатели.")
```





---
## Визуализация данных

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 1
key: 9b02ed8ddb



```

При работе с реальными данными практически никогда нельзя сделать вывод, глядя на сухие числа. У Вас должна сформироваться привычка всегда визуализировать данные, потому что тогда Вы сможете обнаружить зависимости, которые не видно при анализе таблицы или потока чисел. В данном курсе Вы будете использовать самые простые методы визуализации, но их вполне бывает достаточно для первичного анализа.

`@instructions`
- Загрузите библиотеку `ggplot2`.
- Постройте гистограмму пользовательских оценок (winpercent), установив `binwidth`, равным 7.

`@hint`
Для построения гистограммы после + вызовите функцию `geom_histogram()`.

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
# Загрузите библиотеку
library(ggplot2)

# Постройте гистограмму
ggplot(data = candy, aes(x = winpercent)) +
  geom_histogram(binwidth = 7)
```
`@sct`
```{r}
test_student_typed("library(ggplot2)", not_typed_msg = "Возникла проблема с загрузкой библиотеки. Проверьте функцию `library()`?")

check_ggplot(state, index = 1, all_fail_msg = NULL, check_data = TRUE,
  data_fail_msg = NULL, check_aes = TRUE, aes_fail_msg = NULL,
  exact_aes = TRUE, check_geom = TRUE, geom_fail_msg = NULL,
  exact_geom = TRUE, check_geom_params = NULL, check_facet = TRUE,
  facet_fail_msg = NULL, check_scale = TRUE, scale_fail_msg = NULL,
  exact_scale = FALSE, check_coord = TRUE, coord_fail_msg = NULL,
  exact_coord = FALSE, check_stat = TRUE, stat_fail_msg = NULL,
  exact_stat = FALSE, check_extra = NULL, extra_fail_msg = NULL,
  exact_extra = NULL, check = NULL)

#General
test_error()
success_msg("Превосходно! Вы можете попрактиковаться в выборе ширины bin и посмотреть, как от этого меняется результат.")
```





---
## Вид распределения

```yaml
type: MultipleChoiceExercise
lang: r
xp: 50
skills: 1
key: a6eaf579fe



```

На какое из известных распределений приблизительно похожа гистограмма пользовательских оценок?

`@instructions`
- Хи-квадрат
- Нормальное
- Биномиальное с вероятностью 0.8

`@hint`
Если Вы забыли вид распределений, обратитесь ещё раз к материалам первой главы.

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
library(ggplot2)
ggplot(data = candy, aes(x = winpercent)) +
  geom_histogram(binwidth = 7)
```


`@sct`
```{r}
msg1 <- "Попробуйте ещё раз. Максимум у хи-квадрат распределения ближе к 0, а затем оно убывает."
msg2 <- "Отлично!"
msg3 <- "Неправильно. Обратите внимание на то, где примерно находится 'горб' этого распределения."

test_mc(2, feedback_msgs = c(msg1, msg2, msg3))

#General
test_error()
success_msg("Отлично!")
```





---
## Разница между медианой и средним

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 1
key: 3c69ba8592



```

В предыдущих главах Вы уже изучили разницу между медианой и средним. При наличии какого-то сильного выброса значение среднего может сильно сдвинуться и уже не будет подходить для анализа. Увидеть это, не визуализируя данные, практически невозможно, поэтому мы ещё раз обращаем внимание на необходимость отображения данных на графике.

`@instructions`
- Выведите значение среднего и медианы пользовательских оценок 
- Постройте график гистограммы пользовательских оценок, установив количество `bins`, равных 10 (библиотека `ggplot2` уже загружена)
- Отобразите на ней среднее красным цветом ("_red_") с прозрачностью 0.4, а медиану – зелёным ("_green_") цветом с прозрачностью 0.2

`@hint`
Вам необходимо построить гистограмму, на которой изображены две линии со значениями среднего и медианы.

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
#General
test_object("mean_win", incorrect_msg = "Проверьте правильность вычисления `mean_win`.")
test_object("median_win", incorrect_msg = "Проверьте правильность вычисления `median_win`.")

check_ggplot(state, index = 1, all_fail_msg = NULL, check_data = TRUE,
  data_fail_msg = NULL, check_aes = TRUE, aes_fail_msg = NULL,
  exact_aes = TRUE, check_geom = TRUE, geom_fail_msg = NULL,
  exact_geom = TRUE, check_geom_params = NULL, check_facet = TRUE,
  facet_fail_msg = NULL, check_scale = TRUE, scale_fail_msg = NULL,
  exact_scale = FALSE, check_coord = TRUE, coord_fail_msg = NULL,
  exact_coord = FALSE, check_stat = TRUE, stat_fail_msg = NULL,
  exact_stat = FALSE, check_extra = NULL, extra_fail_msg = NULL,
  exact_extra = NULL, check = NULL)


test_error()
success_msg("Бесподобно! В данном датасете медиана и среднее не сильно друг от друга отличаются, но это необходимо проверять, чтобы не допускать ошибок при анализе.")
```





---
## Построение графика плотности

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 1
key: df6dc53485



```

Как Вы могли заметить при выполнении предыдущих заданий, вид гистограммы может кардинально меняться при выборе разного количество `bins`, особенно если количество наблюдений не велико. В таких случаях Вам может понадобиться построение графика плотности, который представляет из себя сглаженный график гистограммы.

`@instructions`
- Наложите график плотности на гистограмму, чтобы посмотреть, как они друг с другом соотносятся. Установите количество `bins` равным 10, а график плотности закрасьте синим цветом и с прозрачностью равной 0.2

`@hint`
- При наложении графика плотности сначала постройте гистограмму, установив количество `bins` равным 10, а потом постройте график плотности синим цветом, используя функцию `density`.

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
library(ggplot2)
```
`@sample_code`
```{r}
# Наложение графика плотности на гистограмму
ggplot(___, ___) +
  ___(aes(y=..density..), bins = ___) +
  ___(fill = '___', alpha = ___)
```
`@solution`
```{r}
# Наложение графика плотности на гистограмму
ggplot(data = candy, aes(x = winpercent)) +
  geom_histogram(aes(y=..density..), bins = 10) +
  geom_density(fill = 'blue', alpha = 0.2)
```
`@sct`
```{r}

check_ggplot(state, index = 1, all_fail_msg = NULL, check_data = TRUE,
  data_fail_msg = NULL, check_aes = TRUE, aes_fail_msg = NULL,
  exact_aes = TRUE, check_geom = TRUE, geom_fail_msg = NULL,
  exact_geom = TRUE, check_geom_params = NULL, check_facet = TRUE,
  facet_fail_msg = NULL, check_scale = TRUE, scale_fail_msg = NULL,
  exact_scale = FALSE, check_coord = TRUE, coord_fail_msg = NULL,
  exact_coord = FALSE, check_stat = TRUE, stat_fail_msg = NULL,
  exact_stat = FALSE, check_extra = NULL, extra_fail_msg = NULL,
  exact_extra = NULL, check = NULL)

#General
test_error()
success_msg("Невероятно! Вы можете заметить, что график плотности как будто обрывается, не доходя до границ гистограммы, это вызвано выбранным количеством `bins`.")
```





---
## Построение квантилей

```yaml
type: NormalExercise

xp: 100

key: ca569da340



```

Ещё одним полезным навыком для анализирования датасета является построение квантилей для числовых переменных. Вы можете воспользоваться функцией quantile(), которая выведет список из значений всех квантилей. Достать квантиль 50% можно двумя способами:
- `quantile(df$col)[3]`
- `quantile(df$col, p = 0.5)`

`@instructions`
- Найдите 25% и 75% квантили для доли сахара.
- Постройте гистограмму для доли сахара с количеством `bins`, равному 10.
- Изобразите интервал значений, лежащих между квантилями 25% и 75%, с помощью двух вертикальных линий красного цвета, установив толщину, равной 3.

`@hint`
Квантили 25% и 75% находятся под вторым и четвёртым индексом соответственно.

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
library(ggplot2)
```
`@sample_code`
```{r}
# Квантиль 25% для доли сахара
xmin <- quantile(___)

# Квантиль 75% для доли сахара
xmax <- ___

# Постройте гистограмму для доли сахара
ggplot(___, ___)+
  ___(___) +
  ___(xintercept = ___, col = ___, size = ___) +
  ___(___)

```
`@solution`
```{r}
# Квантиль 25% для доли сахара
xmin <- quantile(candy$sugarpercent)[2]

# Квантиль 75% для доли сахара
xmax <- quantile(candy$sugarpercent)[4]

# Постройте гистограмму для доли сахара
ggplot(candy, aes(x = sugarpercent)) +
  geom_histogram(bins = 10) +
  geom_vline(xintercept = xmin, col = "red", size = 3) +
  geom_vline(xintercept = xmax, col = "red", size = 3)

```
`@sct`
```{r}
#General
test_object("xmin", incorrect_msg = "Проверьте правильность вычисления `xmin`.")
test_object("xmax", incorrect_msg = "Проверьте правильность вычисления `xmax`.")
check_ggplot(state, index = 1, all_fail_msg = NULL, check_data = TRUE,
  data_fail_msg = NULL, check_aes = TRUE, aes_fail_msg = NULL,
  exact_aes = TRUE, check_geom = TRUE, geom_fail_msg = NULL,
  exact_geom = TRUE, check_geom_params = NULL, check_facet = TRUE,
  facet_fail_msg = NULL, check_scale = TRUE, scale_fail_msg = NULL,
  exact_scale = FALSE, check_coord = TRUE, coord_fail_msg = NULL,
  exact_coord = FALSE, check_stat = TRUE, stat_fail_msg = NULL,
  exact_stat = FALSE, check_extra = NULL, extra_fail_msg = NULL,
  exact_extra = NULL, check = NULL)
test_error()
success_msg("Невероятно! Теперь Вы сможете сформировать представление о любом датасете!")
```





---
## Подсчёт корреляции

```yaml
type: NormalExercise

xp: 100

key: 8096133bee



```

При анализе датасета бывает полезно посмотреть, какие переменные зависят друг от друга, потому что это может объяснить некоторые не очевидные следствия. Для этого Вам может понадобиться библиотека corrplot для удобной и наглядной работы с корреляционными матрицами. 
Так как корреляция может существовать только для числовых значений, то перед работой с датасетом из него необходимо убрать все нечисловые и, возможно, категориальные переменные. Чтобы убрать из датасета `df` столбец под названием `col` можно подключить библиотеку `dplyr` и написать `df <- select(df, -col)`. К полученному датасету можно применять функцию `cor`, которая построит корреляционную матрицу.

`@instructions`
- Загрузите библиотеку `corrplot` и `dplyr`.
- Уберите из датасета нечисельные переменные.
- Постройте корреляционную матрицу.

`@hint`
Для построения корреляционной матрицы Вам необходимо удалить столбец с названием `competitorname`.

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
```
`@sample_code`
```{r}
# Подключите библиотеку
library(___)
library(___)

# Приведите датасет к необходимому виду
candy_cut <- select(___)

# Постройте корреляционную матрицу
candy_cor <- ___
candy_cor
```
`@solution`
```{r}
# Подключите нужные библиотеки
library(corrplot)
library(dplyr)

# Приведите датасет к необходимому виду
candy_cut <- select(candy, -competitorname)

#Постройте корреляционную матрицу
candy_cor <- cor(candy_cut)
candy_cor
```
`@sct`
```{r}
test_student_typed("library(corrplot)", not_typed_msg = "Вы не подгрузили библиотеку `corrplot`.")
test_student_typed("library(dplyr)", not_typed_msg = "Вы не подгрузили библиотеку `dplyr`.")
test_object("candy_cut", incorrect_msg = "Проверьте правильность вычисления `candy_cut`.")
test_object("candy_cor", incorrect_msg = "Проверьте правильность вычисления `candy_cor`.")

#General
test_error()
success_msg("Безупречно! В следующем упражнении Вы научитесь извлекать из этой таблицы информацию о датасете и обнаруженных в нём зависимостях.")
```





---
## Анализ зависимостей

```yaml
type: MultipleChoiceExercise

xp: 50

key: d6c1759f04



```

С какой переменной у `pluribus` самая сильная корреляция? (матрица `candy_cor` уже загружена для работы с ней)

`@instructions`
- chocolate
- bar
- nougat
- fruity

`@hint`
Выведите в консоль `candy_cor[, "pluribus"]` и посмотрите на соответствующие показатели.

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
library(dplyr)
library(corrplot)
candy_cut <- select(candy, -competitorname)
candy_cor <- cor(candy_cut)
```


`@sct`
```{r}
msg1 <- "Попробуйте ещё раз. Существует переменная, у которой уровень корреляции с переменной `pluribus` по модулю выше."
msg2 <- "Правильно!"
msg4 <- "Попробуйте ещё раз. Существует переменная, у которой уровень корреляции с переменной `pluribus` по модулю выше."
msg3 <- "Попробуйте ещё раз. Существует переменная, у которой уровень корреляции с переменной `pluribus` по модулю выше."

test_mc(2, feedback_msgs = c(msg1, msg2, msg3, msg4))

#General
test_error()
success_msg("Прекрасно! Однако анализировать корреляционную матрицу, чтобы проследить зависимости переменных одной от другой, довольно неудобно…")
```





---
## Визуализация корреляции

```yaml
type: NormalExercise

xp: 100

key: 263d269a1d



```

Как Вы могли заметить, работа с численным выражением корреляции не удобна, поэтому Вы, как опытный исследователь, должны уметь визуализировать данную информацию с помощью корреляционной таблицы, используя функцию `corrplot()`. Помните, что эта функция может принимать только тот датасет, который был приведён к нужному типу с помощью функции `cor()`. Построенная Вами в предыдущих упражнениях матрица `candy_cor` уже загружена.

`@instructions`
- Постройте корреляционную матрицу.

`@hint`
Передайте функции `corrplot()` в качестве аргумента корреляционную  матрицу.

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
library(dplyr)
library(corrplot)
candy_cut <- select(candy, -competitorname)
candy_cor <- cor(candy_cut)
```
`@sample_code`
```{r}
# Корреляционная матрица показателей конфет
corrplot(___, method = 'circle')

```
`@solution`
```{r}
# Корреляционная матрица показателей конфет
corrplot(candy_cor, method = 'circle')

```
`@sct`
```{r}
test_student_typed("corrplot(candy_cor, method = 'circle')", not_typed_msg = "Возникла ошибка при построении матрицы.")

#General
test_error()
success_msg("Чудесно! Сила корреляции на графике изображена насыщенностью оттенка, а её направленность – цветом. По диагонали можно заметить ряд из синих кругов, так как корреляция переменной самой от себя всегда равна 1.")
```





---
## Анализ корреляционной матрицы

```yaml
type: MultipleChoiceExercise

xp: 50

key: 34e621648c



```

Какие выводы можно сделать, глядя на эту матрицу?

`@instructions`
- Пользовательская оценка шоколада больше всего зависит от его карамельности.
- Между наличием шоколада и фруктов существует достаточно сильная отрицательная зависимость.
- Чем больше твёрдость шоколадки, тем больше её цена.
- Количество сахара больше всего зависит от количества нуги.

`@hint`
Посмотрите на цвет и интенсивность соответствующих показателей.

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
library(dplyr)
library(corrplot)
candy_cut <- select(candy, -competitorname)
candy_cor <- cor(candy_cut)
corrplot(candy_cor, method = "circle")
```


`@sct`
```{r}
msg1 <- "Попробуйте ещё раз. Внимательно смотрите на насыщенность остальных кругов у переменной `winpercent`."
msg2 <- "Правильно!"
msg4 <- "Попробуйте ещё раз. Внимательно смотрите на насыщенность остальных кругов у переменной `nougat`."
msg3 <- "Попробуйте ещё раз. Внимательно смотрите на цвет круга на пересечении переменных `pricepercent` и  `hard`."

test_mc(2, feedback_msgs = c(msg1, msg2, msg3, msg4))

#General
test_error()
success_msg("Отлично! В следующем упражнении у Вас будет возможность поработать с интервалами.")
```





---
## Вычисление доверительного интервала для среднего

```yaml
type: NormalExercise

xp: 100

key: 427cb183aa



```

Умение строить доверительные интвервалы и отображать их на графиках $-$ это ещё одно важное умение для исследователя датасетов. Сейчас Вам будет представлена возможность рассчитать интервалы для значения среднего пользовательских оценок. 


`@instructions`
- Высчитайте среднее пользовательских оценок.
- Высчитайте стандартное отклонение пользовательских оценок.
- Высчитайте критическое значение для 95% доверительного интервала.

`@hint`

Для 95% доверительного интервала значение, передаваемое в функцию `qnorm()` не равно 0.95.

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
```
`@sample_code`
```{r}
# Вычислите среднее пользовательских оценок
mean_win <- ___

# Вычислите стандартное отклонение пользовательских оценок
sd_win <- ___

# Вычислите статистику для 95% доверительного интервала
z <- qnorm(___)

```
`@solution`
```{r}
# Вычислите среднее пользовательских оценок
mean_win <- mean(candy$winpercent)

# Вычислите стандартное отклонение пользовательских оценок
sd_win <- sd(candy$winpercent)

# Вычислите статистику для 95% доверительного интервала
z <- qnorm(p = 0.975)

```
`@sct`
```{r}
test_object("mean_win", incorrect_msg = "Проверьте правильность вычисления `mean_win`.")
test_object("sd_win", incorrect_msg = "Проверьте правильность вычисления `sd_win`.")
test_object("z", incorrect_msg = "Проверьте правильность вычисления `z`.")


#General
test_error()
success_msg("Прекрасно! В следующем упражнении Вы сможете вычислить и отобразить построенный Вами интервал на графике.")
```





---
## Изображение доверительного интервала для среднего

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 1
key: 106eb1bdad


```
Теперь пришло время изобразить этот интервал на гистограмме! Созданные ранее переменные `mean_win`, `sd_win`и `z` уже загружены в рабочее пространство.

Формула для расчёта: $CI \in [\mu - \frac{z * sd}{\sqrt{n}}; \mu + \frac{z*sd}{\sqrt{n}}]$

`@instructions`
- Вычислите значения верхней и нижней границы интервала.
- На гистограмме с `bins` равным 10 изобразите двумя красными линиями интервал пользовательских оценок.

`@hint`
Для вычисления количества пользовательских оценок воспользуйтесь функцией `nrow()`.

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
library(ggplot2)
mean_win <- mean(candy$winpercent)
sd_win <- sd(candy$winpercent)
z <- qnorm(p = 0.975)
```
`@sample_code`
```{r}
# Вычислите нижнее и верхнее значение доверительного интервала 
lower <- ___ - ___*___/sqrt(___)
upper <- ___

# Изобразите доверительный интервал
ggplot(___) +
  geom_histogram(bins = ___) +
  geom_vline(xintercept = ___, col = ___) +
  geom_vline(___)

```
`@solution`
```{r}
# Вычислите нижнее и верхнее значение доверительного интервала 
lower <- mean_win - z*sd_win/sqrt(nrow(candy))
upper <- mean_win + z*sd_win/sqrt(nrow(candy))

# Изобразите доверительный интервал
ggplot(data = candy, aes(x = winpercent)) +
  geom_histogram(bins = 10) +
  geom_vline(xintercept = lower, col = "red") +
  geom_vline(xintercept = upper, col = "red")

```
`@sct`
```{r}
test_object("lower", incorrect_msg = "Посмотрите ещё раз на формулу в инструкции и проверьте правильность вычисления `lower`.")
test_object("upper", incorrect_msg = "Посмотрите ещё раз на формулу в инструкции и проверьте правильность вычисления `upper`.")

check_ggplot(state, index = 1, all_fail_msg = NULL, check_data = TRUE,
  data_fail_msg = NULL, check_aes = TRUE, aes_fail_msg = NULL,
  exact_aes = TRUE, check_geom = TRUE, geom_fail_msg = NULL,
  exact_geom = TRUE, check_geom_params = NULL, check_facet = TRUE,
  facet_fail_msg = NULL, check_scale = TRUE, scale_fail_msg = NULL,
  exact_scale = FALSE, check_coord = TRUE, coord_fail_msg = NULL,
  exact_coord = FALSE, check_stat = TRUE, stat_fail_msg = NULL,
  exact_stat = FALSE, check_extra = NULL, extra_fail_msg = NULL,
  exact_extra = NULL, check = NULL)

#General
test_error()
success_msg("Хорошо! В следующем упражнении Вам предстоит рассчитать интервал для дисперсии доли сахара.")
```





---
## Построение доверительных интервалов для дисперсии

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 1
key: 5eb027fa4b



```

Теперь Вы можете отработать построение доверительных интервалов для дисперсии. Для этого Вам необходимо построить хи-квадрат распределение с количеством степеней свободы, равных количеству наблюдений - 1. 

Формула для расчёта: $\sigma \in [\dfrac{(n-1)\hat{\sigma^2}}{r}; \dfrac{(n-1)\hat{\sigma^2}}{l}]$

`@instructions`
- Найдите дисперсию доли сахара.
- Найдите количество степеней свободы.
- Найдите верхнюю и нижнюю статистику для хи-квадрат распределения для 90% интервала.
- Найдите верхнюю и нижнюю границу интервала.

`@hint`
```{r}
- Для построения границ 90% интервала необходимо подставить значения вероятности, равные 0.05 и 0.95 соответственно. 
```

`@pre_exercise_code`
```{r}
candy <- read.csv(url("https://raw.githubusercontent.com/fivethirtyeight/data/master/candy-power-ranking/candy-data.csv"))
```
`@sample_code`
```{r}
# Дисперсия доли сахара в шоколадках
var_sug <- ___(___)

# Количество наблюдений
df <- ___

# Нахождение критических значений для 90% доверительного интервала
l_q <- qchisq(p = ___, df = ___)
r_q <- ___(___, ___)

lower <- ___*___/___
lower

upper <- ___
upper

```
`@solution`
```{r}
# Дисперсия доли сахара в шоколадках
var_sug <- var(candy$sugarpercent)

# Количество наблюдений
df <- nrow(candy) - 1 

# Нахождение статистик для 90% доверительного интервала
l_q <- qchisq(p = 0.05, df = df)
r_q <- qchisq(p = 0.95, df = df)

lower <- var_sug*df/r_q
lower

upper <- var_sug*df/l_q
upper

```
`@sct`
```{r}
test_object("var_sug", incorrect_msg = "Проверьте правильность вычисления `var_sug`.")
test_object("df", incorrect_msg = "Проверьте правильность вычисления `df`.")
test_object("l_q", incorrect_msg = "Проверьте правильность вычисления `l_q`.")
test_object("r_q", incorrect_msg = "Проверьте правильность вычисления `r_q`.")
test_object("lower", incorrect_msg = "Проверьте правильность вычисления `lower`.")
test_object("upper", incorrect_msg = "Проверьте правильность вычисления `upper`.")

#General
test_error()
success_msg("Безупречно!  Вы прекрасно справились со всеми заданиями и смогли проанализировать представленный Вам датасет.")
```

