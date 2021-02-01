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
