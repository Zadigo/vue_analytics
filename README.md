# Vue Analytics

Implements analytics functions for a Vue application.

## Getting started

Create a file and add the following:

```javascript
import { createGoogleAnalytics } from "./vue-analytics";

var analytics = createGoogleAnalytics('google_tag', {
    brand: 'My Brand',
    currency: 'EUR'
})

export default analytics
```

And then in main:

```javascript
import analytics from './plugins/analytics

var app = Vue.mount()
            app.use(analytics)
```

## Google Analytics

### Login

```html
<script>
export default {
    methods: {
        login () {
            this.$analytics.login('method')
        }
    }
}
</script>
```

### Signup

```html
<script>
export default {
    methods: {
        signup () {
            this.$analytics.signup('method')
        }
    }
}
</script>
```

### Share

```html
<script>
export default {
    methods: {
        share () {
            this.$analytics.share('', 'image', 'id_1234')
        }
    }
}
</script>
```

### Page View

* `path`: current page of the page
* `titlee`: current page title

```html
<script>
export default {
    mounted () {
        this.$analytics.pageView('/', 'Home')
    }
}
</script>
```

### Search

* `searchTerm`: current page of the page

```html
<script>
export default {
    methods: {
        search (searchValue) {
            this.$analytics.search(searchValue)
        }
    }
}
</script>
```

### Create Event

```html
<script>
export default {
    beforeMount() {
        this.$analytics.createEvent('event_name', 'custom_category', { ... })
    }
}
</script>
```

### Select item

```html
<script>
export default {
    methods: {
        gotToItem (index, item) {
            this.$analytics.selectItem({
                item_id: item.id,
                item_name: item.name,
                price: item.price,
                // item_brand: '',
                item_category: item.category,
                // index: index,
                // discount: discount,
                // coupon: coupon
            }, 'list_name', 'list_id')
            this.$router.push({ ... })
        }
    }
}
</script>
```

### View item

```html
<script>
export default {
    mounted () {
        var item = this.$store.getters['getItem'](this.$route.params.id)

        this.$analytics.viewItem({
            item_id: item.id,
            item_name: item.name,
            price: item.price,
            // item_brand: '',
            item_category: item.category,
            // index: index,
            // discount: discount,
            // coupon: coupon
        }, 'list_name', 'list_id')
    }
}
</script>
```

### View items

```html
<script>
export default {
    beforeMount () {
        var items = _.map(this.$store.state.items , (item) => {
            return {
                item_id: item.id,
                item_name: item.name,
                price: item.price,
                // item_brand: '',
                item_category: item.category,
                // index: index,
                // discount: discount,
                // coupon: coupon
            }
        })
        this.$analytics.viewItems(items)

        // If the items being seen are on a single item
        // page, you can also pass in the current item
        // var currentItem = this.$store.getters['getItem'](this.$route.params.id)
        // this.$analytics.viewItems(items, currentItem)

    }
}
</script>
```

### View cart

```html
<script>
export default {
    beforeMount () {
        var items = _.map(this.$store.state.items , (item) => {
            return {
                item_id: item.id,
                item_name: item.name,
                price: item.price,
                // item_brand: '',
                item_category: item.category,
                // index: index,
                // discount: discount,
                // coupon: coupon
            }
        })
        this.$analytics.viewCart(items)
    }
}
</script>
```

### Seleect promotion

```html
<script>
export default {
    methods: {
        goToPromotion () {
            this.$analytics.selectPromotion ('promotion_id', 'promotion_name', 'creative_slot', 'location_id')
            this.$router.push({ ... })
        }
    }
}
</script>
```

### View promotion

```html
<script>
export default {
    mounted () {
        this.$analytics.viewPromotion ('promotion_id', 'promotion_name', 'creative_slot', 'location_id')
        this.$router.push({ ... })
    }
}
</script>
```

### Select content

```html
<script>
export default {
    methods: {
        goToPage () {
            this.$analytics.selectContent ('product', 'item_id')
            this.$router.push({ ... })
        }
    }
}
</script>
```

### Add to cart

```html
<script>
export default {
    methods: {
        addToCart (item) {
            this.$analytics.addToCart({
                item_id: item.id,
                item_name: item.name,
                price: item.price,
                // item_brand: '',
                item_category: item.category,
                // index: index,
                // discount: discount,
                // coupon: coupon
            }, 123.44)
        }
    }
}
</script>
```

### Add to wishlist

```html
<script>
export default {
    methods: {
        addToCart (item) {
            this.$analytics.addToWishlist({
                item_id: item.id,
                item_name: item.name,
                price: item.price,
                // item_brand: '',
                item_category: item.category,
                // index: index,
                // discount: discount,
                // coupon: coupon
            }, 123.44)
        }
    }
}
</script>
```

### Remove from cart

```html
<script>
export default {
    methods: {
        addToCart (item) {
            this.$analytics.removeFromCart({
                item_id: item.id,
                item_name: item.name,
                price: item.price,
                // item_brand: '',
                item_category: item.category,
                // index: index,
                // discount: discount,
                // coupon: coupon
            }, 123.44)
        }
    }
}
</script>
```
