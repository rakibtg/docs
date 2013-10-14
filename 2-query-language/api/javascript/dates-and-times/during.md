---
layout: api-command 
permalink: api/javascript/during/
command: during
---

{% apibody %}
time.during(startTime, endTime[, options]) → bool
{% endapibody %}

Return if a time is between two other times (by default, inclusive for the start,
exclusive for the end).

__Example:__ Retrieve all the posts that were posted between December 1st, 2013
(inclusive) and December 10th, 2013 (exclusive).

```js
r.table("posts").filter(
    r.row('date').during(r.time(2013, 12, 1), r.time(2013, 12, 10))
).run(conn, callback)
```


__Example:__ Retrieve all the posts that were posted between December 1st, 2013
(exclusive) and December 10th, 2013 (inclusive).

```js
r.table("posts").filter(
  r.row('date').during(r.time(2013, 12, 1), r.time(2013, 12, 10), {leftBound: "open", rightBound: "closed"})
).run(conn, callback)
```
