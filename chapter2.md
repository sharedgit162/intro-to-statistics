---
title: Выборочные характеристики
description: This is a template chapter.
---

## Задание 2.1

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 1
key: dbe164cc29
```

В этой главе мы научимся вычислять основные выборочные характеристики при помощи *R*. Будем работать с датасетом faithful, который содержит данные о продолжительности `eruptions`  и времени ожидания `waiting` между извержениями гейзера Старый Служака. Давайте посмотрим на распределение времени ожидания извержения гейзера. Для этого построим эмпирическую функция распределения.


`@instructions`
- Для визуализации данных загрузите пакет `ggplot2`.
- Instruction 2
- Instruction 3
- Instruction 4

`@hint`
- Here is the hint for this setup problem. It should get students 50% of the way to the correct answer.

`@pre_exercise_code`

```{r}
# Load datasets and packages here.
# install.packages(MASS)
# library('faithful')
head(faithful)
```

`@sample_code`

```{r}
# Your
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
# Answer goes here
# Make sure to match the comments with your sample code
# to help students see the differences from solution
# to given.
```

`@sct`

```{r}
# Update this to something more informative.
success_msg("Some praise! Then reinforce a learning objective from the exercise.")
```
