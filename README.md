# Upsell-Items
#### Add upsell items to the slide cart section of the Shopify Dawn theme. Create custom Javascript code to remove upsell items if there's no base product in the cart without page refresh using Shopify Cart API and Section Rendering API.

1. Go to `cart-drawer.liquid` file in the snippets directory and find(Ctrl + F) `</cart-drawer-items>`.

2. Paste the code from the `cart-drawer.liquid` file before the closing of `</cart-drawer-items>` or after the closing of `</form>` tag.

3. Create a new liquid snippet file `upsell-js.liquid` in the snippets directory.

4. Paste the code from the `upsell-js.liquid` file.

5. Include the `upsell-js.liquid` file in the `<body>` section of your `theme.liquid` file.

    ```
    {% if settings.upsell_collection != blank %}
    {% render 'upsell-js' %}
    {% endif %}
    ```
6. Create a new asset file `upsell-items.css` in the assets directory.

7. Include the `upsell-items.css` file in the `cart-drawer.liquid` file at the top of the file.

    `{{ 'upsell-items.css' | asset_url | stylesheet_tag }}`
    
8. Paste the code from the `upsell-items.css` file.

9. Go to `base.css` file in the assets directory and paste the code from `base.css` file at the bottom of the file and save.

10. Go to `component-cart-drawer.css` file in the assets directory and paste the code from `component-cart-drawer.css` file at the bottom of the file and save.

11. Go to `settings_schema.json` file in the config directory and find(Ctrl + F) `"cart_drawer_collection"`.

12. Paste the following schema code after the closing of `"cart_drawer_collection"` json and save.

    ```
    {
      "type": "header",
      "content": "Upsell items"
    },
    {
      "type": "text",
      "id": "upsell_heading",
      "label": "Upsell heading"
    },
    {
      "type": "collection",
      "id": "upsell_collection",
      "label": "Upsell collection",
      "info": "Visible when cart drawer is not empty."
    }
    ```
13. Go to Online Store > Themes > Customize
 
14. Go to Theme Settings > Cart > Select the Upsell Collection

15. If you have to hide the quantity selector for the Upsell items then add product tag to the Upsell items ex. `Upsell Mixed`.

16. Go to `cart-drawer.liquid` and `main-cart-items.liquid` files and find(Ctrl + F) `<quantity-input`.

17. Replace the class attribute of the `<quantity-input>` element with the following code in both the files and save.

    `class="quantity{% if item.product.tags contains 'Upsell Mixed' %} visibility-hidden{% endif %}"`
    
18. Go to `main-cart-footer.liquid` and `main-cart-items.liquid` files and then go to section schema code.

19. Add the `class` attribute after the `name` attribute.

    ```
    "class": "cart__footer-wrapper"
    "class": "cart__items-wrapper"
    ```
