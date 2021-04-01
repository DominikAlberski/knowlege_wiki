EXISTS operator is a boolean operator that tests for existence of rows in a subquery.

The following illustrates syntax of the EXISTS operator:

```SQL
EXISTS (subquery)
```

The EXISTS accepts an argument which is a subquery

If the subquery returns at least one row, the result of EXISTS is true.
In case the subquery returns no row, the result of EXISTS is false.

The NOT operator negates the result of the EXISTS operator.
The NOT EXISTS is opposite to EXISTS.
It means that if the subquery returns no row, the NOT EXISTS returns true.
If the subquery returns one or more rows, the NOT EXISTS returns false.


ARRAY_AGG()
Allows to return values in form of an array grouped by other values. For example
in join table it allows to retrun data in form of:
user_id: 1, ther_model_ids: [1, 2, 5]

```ruby
CustomQueue::Permission.select('custom_queue_id, ARRAY_AGG(user_id)').group(1)
```
You can decide on the order of the returned values in array
```SQL
title,
    ARRAY_AGG (
        first_name || ' ' || last_name
        ORDER BY
            first_name
    ) actors

```

`LIKE` "\_" - one single character
`LIKE` "%" - any character

---

(site with datasets)[kaggle.com] to have some fun with or to simply have
something to train on

\copy table_name from 'file_anme.csv' CSV dellimiter ',' NULL AS 'N/A' header;

