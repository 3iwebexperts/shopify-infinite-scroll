# shopify-infinite-scroll
Infinite scrolling of products listing on any page i shopify using AJAX



Follow the Steps below!
1. Open your Shopify admin, to to Online Store > Theme.
2. Go the theme you want to edit and then click Action > Edit code.
3. Copy the <a href="https://github.com/3iwebexperts/shopify-infinite-scroll/blob/master/infinite-scroll.js">infinite-scroll.js</a> from this repository and add it to assets
4. Copy the below code and add it before </head>
   ```html
   {{ 'infinite-scroll.js' | asset_url | script_tag }}
   ```

5. In the online code editor of collection page find to the loop {% for product in collection.products %} and add more a DIV tag to wrapper and add more a DIV tag just below it.    For example:

   ```html
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
   ```

6. Add the javascript code to the end of the file. ( upload the loading.gif image to assets folder )
   ```html
   <script type="text/javascript">
     function callbackInfiniteScroll(){}
     document.addEventListener("DOMContentLoaded", function() {
       var endlessScroll = new Ajaxinate({
          container: '#infinite-loop',
          pagination: '#infinite-pagination',
         loadingText: '<center><img src="{{ 'loading.gif' | asset_url }}" al="loading"></center>',
         callback: callbackInfiniteScroll
       });
     });
   </script>
   ```

7. Save
Note : you can copy assets from this repository.
