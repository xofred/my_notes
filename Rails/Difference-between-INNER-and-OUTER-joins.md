Examples

Suppose you have two tables, with a single column each, and data as follows:

```
A    B
-    -
1    3
2    4
3    5
4    6
```
Note that (1,2) are unique to A, (3,4) are common, and (5,6) are unique to B.

**Inner join**

An inner join using either of the equivalent queries gives the intersection of the two tables, i.e. the two rows they have in common.

select * from a INNER JOIN b on a.a = b.b;
select a.*,b.*  from a,b where a.a = b.b;
```
a | b
--+--
3 | 3
4 | 4
```
**Left outer join**

A left outer join will give all rows in A, plus any common rows in B.

select * from a LEFT OUTER JOIN b on a.a = b.b;
select a.*,b.*  from a,b where a.a = b.b(+);
```
a |  b
--+-----
1 | null
2 | null
3 |    3
4 |    4
```

**In Rails**
```ruby
Client.joins('LEFT OUTER JOIN addresses ON addresses.client_id = clients.id')
# SELECT clients.* FROM clients LEFT OUTER JOIN addresses ON addresses.client_id = clients.id
```