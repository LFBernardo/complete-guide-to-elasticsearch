# Adding documents

## Adding departments

```
PUT /department/_doc/1
{
  "name": "Development",
  "join_field": "department"
}
```

```
PUT /department/_doc/2
{
  "name": "Marketing",
  "join_field": "department"
}
```

## How to add index based on the video as it differs from what was in the repository
```
PUT /department
{
  "mappings": {
    "_doc": {
      "properties": {
        "name": {
          "type": "text"
        },
        "employees": {
          "type": "nested"
        }
        }
      }
    }
  }
```
## Adding employees for departments

```
PUT /department/_doc/3?routing=1
{
  "name": "Bo Andersen",
  "age": 28,
  "gender": "M",
  "join_field": {
    "name": "employee",
    "parent": 1
  }
}
```

```
PUT /department/_doc/4?routing=2
{
  "name": "John Doe",
  "age": 44,
  "gender": "M",
  "join_field": {
    "name": "employee",
    "parent": 2
  }
}
```

```
PUT /department/_doc/5?routing=1
{
  "name": "James Evans",
  "age": 32,
  "gender": "M",
  "join_field": {
    "name": "employee",
    "parent": 1
  }
}
```

```
PUT /department/_doc/6?routing=1
{
  "name": "Daniel Harris",
  "age": 52,
  "gender": "M",
  "join_field": {
    "name": "employee",
    "parent": 1
  }
}
```

```
PUT /department/_doc/7?routing=2
{
  "name": "Jane Park",
  "age": 23,
  "gender": "F",
  "join_field": {
    "name": "employee",
    "parent": 2
  }
}
```

```
PUT /department/_doc/8?routing=1
{
  "name": "Christina Parker",
  "age": 29,
  "gender": "F",
  "join_field": {
    "name": "employee",
    "parent": 1
  }
}
```
## How to add users based on the video as it differs from what was in the repository
```
POST /department/_doc/1
{
  "name": "Development",
  "employees": [
    {
      "name": "Eric Green",
      "age": 39,
      "gender": "M",
      "Position": "Big Data Analys"
    },
    {
      "name": "James Taylor",
      "age": 27,
      "gender": "M",
      "Position": "Software Devleoper"
    },
    {
      "name": "Gary Jenkins",
      "age": 21,
      "gender": "M",
      "Position": "Intern"
    },
    {
      "name": "Julie Powell",
      "age": 26,
      "gender": "F",
      "Position": "Intern"
    },
    {
      "name": "Benjamin Smith",
      "age": 46,
      "gender": "M",
      "Position": "Senior Software Engineer"
    }
    ]
}
```
