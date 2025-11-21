# My-Python-Project
This is a python project for my class.


Overview — What this program does
This Python program is a Shop Management System.
It allows you to:
Add products to inventory
Update or delete products
Sell items (generate bills)
Track sales
Create revenue & profit reports
See low-stock items
Save all data in a JSON file (shop_data.json)
Everything is stored permanently so data is not lost when the program closes.
File Structure
The program stores data in:
shop_data.json
It contains two things:
{
  "products": {},
  "sales": []
}
Function-by-function Explanation
1. now_iso()
Returns current date & time in ISO format.
Example: "2025-11-21T12:30:45"
2. load_data()
If the file shop_data.json exists → load it
If not → create empty data structure
3. save_data(data)
Writes updated data into the JSON file with proper formatting.
4. generate_product_id(data)
Automatically generates product IDs like:
P0001  
P0002  
P0003  
...
It checks existing IDs and picks the next available.
5. input_nonempty(), input_float(), input_int()
These are helper functions that:
Force non-empty input
Force number input (float/int)
Validate input values (no empty/invalid numbers)
6. add_product(data)
Adds a new product to inventory.
Asks user for:
Name
Selling price
Purchase cost
Quantity
Then saves product like:
{
  "id": "P0001",
  "name": "Pen",
  "price": 10,
  "cost": 4,
  "qty": 200,
  "created_at": "2025-11-21T12:00:00"
}
7. update_product(data)
Allows user to edit an existing product.
You can update:
Name
Price
Cost
Quantity
Only values you type get updated; empty input keeps old value.
8. delete_product(data)
Deletes a product using its ID.
Asks for confirmation before deleting.
9. list_products(data, low_stock_only=False)
Displays all products in a table.
If low_stock_only=True → shows only items with quantity ≤ 5.
10. create_bill(data)
This is the billing & sales system.
Steps:
User enters product ID
Enters quantity
Item gets added to cart
Calculates:
Subtotal
12% tax
5% discount if subtotal > 1000
Final total
Shows bill preview
If confirmed:
Reduces stock
Saves sale details into sales list
Each sale saved like:
{
  "id": "S00001",
  "datetime": "2025-11-21T12:45:00",
  "items": [...],
  "subtotal": 500,
  "tax": 60,
  "discount": 0,
  "total": 560
}
11. view_sales(data)
Shows last 20 sales with:
Sale ID
Date
Total amount
Total items
12. report(data)
Generates summary:
✔ Total revenue
✔ Total profit
✔ Best selling product
✔ Low-stock products
Profit = selling_price − cost_price for each unit sold.
13. seed_demo_data(data)
This adds sample products only if inventory is empty, like:
Notebook
Pen
Bottle
Useful for first-time testing.
14. main_menu()
Runs the entire menu:
1. Add product
2. Update product
3. Delete product
4. List products
5. List low stock products
6. Create bill / Sell items
7. View sales history
8. Report
9. Save & Exit
Keeps running until you choose 9.
