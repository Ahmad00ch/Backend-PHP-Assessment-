# OpenCart Backend PHP Assessment



## Environment

- XAMPP 1.8.1
- PHP 5.4.x
- OpenCart 1.5.6.4



### Task 1 – Product Page Modifications

  **Added Cost column**
   - Modified the `product` table in the database to include `cost`.
   - Updated `admin/view/template/catalog/product_list.tpl` to show the `Cost`    column.
  - Updated `admin/controller/catalog/product.php` to load and pass the `cost` value, persist `filter_cost`, and wire `sort_cost`.
  - Updated `admin/model/catalog/product.php` to handle `filter_cost` (inequalities/ranges) and support sorting by `p.cost`.


  **Added Profit column**
   - Updated `admin/view/template/catalog/product_list.tpl` to show the `Profit` column.
   - Updated `admin/controller/catalog/product.php` to compute and format Profit, expose `filter_profit`, and wire `sort_profit` links.
   - Updated `admin/model/catalog/product.php` to support `filter_profit` (inequalities/ranges) and sorting via `ORDER BY (p.price - p.cost)`.




