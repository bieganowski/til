## Expand in postgres console 

`\x` - enables/disables expanded display for tables; convenient for tables containing huge amount of columns or very long content

e.g. changes from:
```
 id |      app      |                   name                   |            applied            
----+---------------+------------------------------------------+-------------------------------
  1 | contenttypes  | 0001_initial                             | 2021-03-24 11:13:58.548554+01
  2 | taggit        | 0001_initial                             | 2021-03-24 11:13:58.583759+01

```
to:
```
-[ RECORD 1 ]-------------------------------------
id      | 1
app     | contenttypes
name    | 0001_initial
applied | 2021-03-24 11:13:58.548554+01
-[ RECORD 2 ]-------------------------------------
id      | 2
app     | taggit
name    | 0001_initial
applied | 2021-03-24 11:13:58.583759+01
```