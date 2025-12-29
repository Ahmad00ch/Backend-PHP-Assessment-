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


  **Add Column: Category (Full Path)**
   - Updated `admin/view/template/catalog/product_list.tpl` to show the `Category` column and render the product’s full category path.
   - Updated `admin/controller/catalog/product.php` to load category full paths in getList() and pass 'category_path' with each product.
   - Updated `admin/model/catalog/product.php` to compute full category paths via getProductCategoryFullPaths($product_id) using product_to_category, category_path.




### TASK 2 — CATEGORY PAGE MODIFICATIONS (ADMIN)


  **Add Column: Product Count**
   - `admin/model/catalog/category.php`
     - getCategories(): COUNT(DISTINCT pc.product_id) AS product_count, typed filter parsed via HAVING, sorting by product_count.
     - getTotalCategories($data): total respects the same typed filter.
   - `admin/controller/catalog/category.php`
     - Passes raw filter_product_count to model, preserves it in URLs, wires sort link for product_count, exposes $button_filter.
   - `admin/view/template/catalog/category_list.tpl`
     - Adds Product Count column with sortable header (asc/desc class).
     - Adds typed filter input in header;n Filter button uses $button_filter.


  **Add Column: Parent Category (Full Path)**
   - `admin/model/catalog/category.php`
       - getCategories(): adds parent_path via category_path excluding the current node, ordered by level.
   - `admin/controller/catalog/category.php`
       - getList(): passes parent_path in categories array; adds column_parent_path label.
   - `admin/view/template/catalog/category_list.tpl`
       - Renders a “Parent Category” column showing parent_path.





