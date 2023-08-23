# Paste this at line number 42

```cmd
explore: +order_items {
  
    query:start_from_here{
      dimensions: [products.department, users.state]
      measures: [order_count, users.count]
      filters: [users.country: "USA"]
    }
    
    
  
}
```
