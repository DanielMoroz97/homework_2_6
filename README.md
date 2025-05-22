# homework_2_6
`\timing`

`SELECT payment_type, round(sum(tips)/sum(tips+fare)*100) AS tips_percent, count(*)`
`FROM taxi_trips`
`GROUP BY payment_type`
`ORDER BY tips_percent DESC;`

Результат выполнения:

| payment_type | tips_percent | count |
| -------------- | -------------- | ------- |
| Cash | 0 | 17,231,871 |
| Credit Card | 18 | 9,224,956 |
| Unknown | 0 | 103,869 |
| Prcard | 1 | 86,053 |
| Mobile | 17 | 61,256 |
| No Charge | 0 | 26,294 |
| Pcard | 2 | 13,575 |
| Dispute | 0 | 5,596 |
| Split | 19 | 180 |
| Way2ride | 14 | 27 |
| Prepaid | 0 | 6 |

Время выполнения:  
26.507 секунд (примерно 26506.593 мс)


![image](https://github.com/user-attachments/assets/42100fb9-53d3-483e-85ac-544224bc5012)
Видим что запрос  выполняеется  26.507 секунды !!!
Решение:Cоздания индекса по колонке payment_type
`taxi2_db=# CREATE INDEX idx_payment_type ON taxi_trips(payment_type);`


![image](https://github.com/user-attachments/assets/d1e6da7e-59d6-48c9-b0d6-795ba8c87dc1)


`taxi2_db=# SELECT payment_type,`
`    rountaxi2_db-#        round(sum(tips)/sum(tips+fare)*100) AS tips_percent,`
`    countaxi2_db-#        count(*)`
`FROMtaxi2_db-# FROM taxi_trips`
`taxi2_db-# GROUP BY payment_type`
`taxi2_db-# ORDER BY tips_percent DESC;`

Результат выполнения:

 payment_type | tips_percent |  count
--------------+--------------+----------
 Split        |           19 |      180
 Credit Card  |           18 |  9224956
 Mobile       |           17 |    61256
 Way2ride     |           14 |       27
 Pcard        |            2 |    13575
 Prcard       |            1 |    86053
 Cash         |            0 | 17231871
 Prepaid      |            0 |        6
 No Charge    |            0 |    26294
 Unknown      |            0 |   103869
 Dispute      |            0 |     5596
 (11 rows)

Время выполнения: 
Time: 3718.340 ms (00:03.718)


Вывод:Время выполнения запроса уменьшилось примерно в 7 раз.Создание индекса по колонке payment_type значительно повысило производительность запроса. Это классический пример того, как индекс помогает ускорить операции группировки и сортировки на больших объемах данных



