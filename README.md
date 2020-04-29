# WoocommerceDescr
Adding field for category description.

<ol>
  <li>Dowload plugin <a href="https://ru.wordpress.org/plugins/wp-custom-taxonomy-meta/#installation">Category and Taxonomy Meta Fields</a></li>
  <li>Activate plugin and go to admin panel Settings > Texonomy Meta.</li>
  <li>Call your field how you want, choose Meta Type and select at Meta Taxonomy field product_cat.</li>
  <li>Now go to the admin panel in any category of goods and there appeared an additional field. Fill it out.</li>
  <li>And Now you should add at function.php next code:
    function my_woocommerce_after_shop_loop() {
    if (function_exists('wp_get_terms_meta') && is_product_category())    {
        $cate = get_queried_object();
        $category_id = $cate->term_id;
        $MetaValue = wp_get_terms_meta($category_id, 'name_of_your_field' ,true);
        echo $MetaValue;
    }
    return;
}
    add_action('woocommerce_after_shop_loop', 'my_woocommerce_after_shop_loop',5);</li>
</ol>
