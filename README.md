# shopify-infinite-scroll
Infinite scrolling of products listing on any page i shopify using AJAX



Follow the Steps below!
1. Open your Shopify admin, to to Online Store > Theme.
2. Go the theme you want to edit and then click Action > Edit code.
3. In the Layout section, click theme.liquid to open the file in the online code editor.
    Find </head> and paste the below code just above it.
    {% if template contains 'collection' %}{{ 'https://cdn.shopify.com/s/files/1/0382/4185/files/ajaxinate.js?937' | script_tag }}{% endif %}
    Save.

3. In the online code editor of collection page find to the loop {% for product in collection.products %} and add more a DIV tag to wrapper and add more a DIV tag just below it.    For example:
    <div id="infinite-loop" >
          {% for product in collection.products %}
            {% include 'product-grid-item' %}
          {% endfor %}
    </div>
    <div id="infinite-pagination">
        {% if paginate.next %}
        <a href="{{ paginate.next.url }}">Loading More</a>
        {% endif %}  
    </div>

4. Add the javascript code to the end of the file.
    <script>
      document.addEventListener("DOMContentLoaded", function() {
        var endlessScroll = new Ajaxinate({
          container: '#Huratips-Loop',
          pagination: '#Huratips-Pagination'
        });
      });
    </script>

5. Save
