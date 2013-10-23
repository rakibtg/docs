---
layout: api-command 
language: Python
permalink: api/python/row/
command: row
rb: false
github_doc: https://github.com/rethinkdb/docs/edit/master/2-query-language/api/python/document-manipulation/row.md
---

{% apibody %}
r.row → value
{% endapibody %}

Returns the currently visited document.

__Example:__ Get all users whose age is greater than 5.

```py
r.table('users').filter(r.row['age'] > 5).run(conn)
```


__Example:__ Accessing the attribute 'child' of an embedded document.

```py
r.table('users').filter(r.row['embedded_doc']['child'] > 5).run(conn)
```


__Example:__ Add 1 to every element of an array.

```py
r.expr([1, 2, 3]).map(r.row + 1).run(conn)
```


__Example:__ For nested queries functions should be used instead of r.row.

```py
r.table('users').filter(
    lambda doc: doc['name'] == r.table('prizes').get('winner')
).run(conn)
```
