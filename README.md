# shopify-infinite-scroll
Infinite scrolling of products listing on any page i shopify using AJAX



Follow the Steps below!
1. Open your Shopify admin, to to Online Store > Theme.
2. Go the theme you want to edit and then click Action > Edit code.
3. In the Layout section, click theme.liquid to open the file in the online code editor. Find </head> and paste the below code just above it and Save.
   ```html
   {{ 'https://raw.githubusercontent.com/3iwebexperts/shopify-infinite-scroll/master/infinite-scroll.js' | script_tag }}
   ```

3. In the online code editor of collection page find to the loop {% for product in collection.products %} and add more a DIV tag to wrapper and add more a DIV tag just below it.    For example:

   ```html
   <pre>
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
   </pre>
   ```

4. Add the javascript code to the end of the file.
   ```html
   <pre>
    <script>
      document.addEventListener("DOMContentLoaded", function() {
        var endlessScroll = new Ajaxinate({
          container: '#Huratips-Loop',
          pagination: '#Huratips-Pagination'
        });
      });
    </script>
   </pre>
   ```

5. Save
