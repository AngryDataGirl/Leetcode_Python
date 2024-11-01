
# Append List Item to Dictionary Key 
```python
            if table not in orders_dict.keys():
                print(table)
                orders_dict[table] = [food_item]
            if table in orders_dict.keys():
                orders_dict[table].append(food_item)
```
