# drawerlayout
a vue.js drawer with more function for vue2.x
> A Vue.js project

## demo

[online-demo](https://cdn.rawgit.com/bajian/vue-drawer/master/dist/demo1.html)

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

```

```html
	<!-- drawer-->
    <drawer 
    :show="drawerShow" 
    :pos="pos" :tran="tran"
    @change-show="changeDrawerShow">
    <!-- drawerlayout with slot="drawer"-->
      <div class="layout" slot="drawer" >
        <h2><a href="#">bajian drawer</a></h2>
        <ul>
          <li v-for="item in navItems"><a href="#{{item}}">{{item}}</a></li>
        </ul>
      </div>
      <!-- page content -->
      <button v-on:click="directionFlip">directionChange</button><br><br>
      <button v-on:click="tranFlip">tranChange</button><br><br>
      <button v-on:click="drawerToggle">toggle</button>
    </drawer>


    changeDrawerShow(state) {
      this.drawerShow=state;
    }
```

## Api
### Properties
| Name                 | Type      | Default      | Description                                                        |
|----------------------|-----------|--------------|--------------------------------------------------------------------|
| pos            | `String`  | `left` | the position where the drawer is:`left`/`right` |
| tran            | `String`  | `overlay` | the transition that the drawer beharior:`overlay`/`push` |
| show.sync            | `Boolean`  | `false` | the drawer visibility，set `true` to show the drawer |
| on-hide   | `Function` | `undefined`       | the drawer hide listener  |
| on-show   | `Function` | `undefined`       | the drawer show listener  |
| change-show   | `Function` | `undefined`       | as vue2.0 deprecated the `sync`,this event must be called to change drawer state by the component itself |
| ==================== | ========= | ============ | =================== |


For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
