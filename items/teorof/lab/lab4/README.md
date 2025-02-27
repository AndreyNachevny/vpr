# Детерминизация

Нужно написать(выполнить) на бумаге некоторые действия с графом.
Для каждого будет свой вариант.

## Материалы

<details>
  <summary>Задания</summary>
  
  ###### В лаб работе #4 Вам стоит выполнить только задание 1 (на бумаге). Задание 2 (программно) предназначено для лаб #5
  
  ![image](https://user-images.githubusercontent.com/76239707/227046824-d190b997-55c0-43a7-ae68-5b358a300f7e.png)
  ![image](https://user-images.githubusercontent.com/76239707/227046845-ad9d0dcd-91da-4a22-bca4-02e86eb45ced.png)
  ![image](https://user-images.githubusercontent.com/76239707/227046866-741a1e2f-ed4c-4f49-8f90-33184bbc1425.png)
  ![image](https://user-images.githubusercontent.com/76239707/227046884-d55924c1-e805-445c-90a0-1e3daf6c053f.png)
  ![image](https://user-images.githubusercontent.com/76239707/227046902-574be413-b8cb-47cb-86c5-af600feab273.png)

</details>

<details>
  <summary>Разбор одного из вариантов</summary>
  
  ###### Авторство: Лера Радаева
  
  ![image](https://user-images.githubusercontent.com/76239707/227047193-c2a1b6de-49f6-4ffc-969a-49570a89b60f.png)
  ![image](https://user-images.githubusercontent.com/76239707/227047226-d7ea18d0-b2e5-485e-a664-8e8b4282e06a.png)
  ![image](https://user-images.githubusercontent.com/76239707/227047241-bcc0ae85-914b-4b57-98a9-b34aca67770b.png)
  ![image](https://user-images.githubusercontent.com/76239707/227047309-0c756ffd-848f-4e0b-a37b-850233c6dcf8.png)

</details>


## Алгоритм (ручная запись)
1. Построить ε-замыкания
2. Отобразить таблицу переходов автомата
3. По таблице строим граф
4. Строим детерминированный автомат
6. Строим его граф

## Реализация варианта #2

![image](https://user-images.githubusercontent.com/76239707/227050901-3a1e5a51-dc70-4668-9403-4f9109a50802.png)

##### 1. ε-замыкания

Проходимся по каждым вершинам и ищем для них все пути, в которых в весах присутствует ε.

- **S0** = **Ξ(q0)** = {q0, q1}
- **S1** = **Ξ(q1)** = {q1}
- **S2** = **Ξ(q2)** = {q2}
- **S3** = **Ξ(q3)** = {q3, q2}

PS: так как из любой вершины можно попасть в саму себя преодалев пусть ε, то всегда мн-во Ξ(вершина) будет содержать саму вершину.

##### 2. Строим таблицу переходов автомата

|      | `a`    | `b`    |
|------|--------|--------|
| `S0` | `S2 S3`| ` S2  `|
| `S1` | `S2 S3`| ` S2  `|
| `S2` | ` S2 ` | ` ∅ ` |
| `S3` | ` S2  `| `S2 S3`|

- Из состояния S0 можно попасть в S2, S3 через a, и в S2 через b.
- Из S1 можно попасть в S2 S3 через a, в S2 через b.
- Из S2 можно попасть только в S2 через a.
- Из S3 можно попасть в S2 и S3 через b, в S2 через a.

##### 3. Cтроим граф

<details>
  <summary>Фото</summary>
  
  

</details>

##### 4. Строим детерминированный автомат

- P0 = {S0, S1}
  - (P0; a) -> {(S0; a) -> {S2, S3}, (S1; a) -> {S2, S3}} -> {S2, S3} = P1
  - (P0; b) -> {(S0; b) -> {S2}, (S1; b) -> {S2}} -> {S2} = P2

- P1 = {S2, S3}
  - (P1; a) -> {(S2; a) -> {S2}, (S3; a) -> {S2}} -> {S2} = P2
  - (P1; b) -> {(S2; b) -> {∅}, (S3; b) -> {S2, S3}} -> {∅} ∪ {S2, S3} = {S2, S3} = P1

- P2 = {S2}
  - (P2; a) -> {S2} = P2
  - (P2; b) -> ∅


###### Таблица

|      | `a`    | `b`    |
|------|--------|--------|
| `P0` | ` P1 ` | ` P2  `|
| `P1` | ` P2 ` | ` P1  `|
| `P2` | ` P2 ` | ` ∅ ` |

##### 5. Граф

<details>
  <summary>Фото</summary>
  
  


</details>

*Авторство: **Бояршинов Н.О***
