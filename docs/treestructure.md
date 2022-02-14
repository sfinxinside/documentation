# How to represent the organization tree structure in the API and Data

```json
{
  "name": "John", 
  "children": [ 
    {
      "name": "Lee", 
      "children": [
         {
           "name": "Nash", 
           "children": [{ "name":"Tim"}]
         },
         {
           "name": "Nicole"
         },
         {
           "name": "Kelly"
         }
      ]
    },
    {
      "name": "Alice"
    },
    {
      "name": "Stanley" 
    } 
  ] 
}
```json