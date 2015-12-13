chartist-vuejs
==============

Plugin [Vuejs](http://vuejs.org/) for [Chartist.js](https://gionkunz.github.io)

## Install
    npm install chartist-vuejs
## Setup
```javascript
Vue.use(require('chartist-vuejs'))
```
## Usage
In your HTML, add `<chartist>` tag. This tag take following attributes :
- **id-chart** - `String` (required)  
id attribute for the query selector of Chartist
- **ratio** - `String`  
class ratio of Chartist, see values on [Chartist web site](https://gionkunz.github.io/chartist-js/getting-started.html#as-simple-as-it-can-get)
- **type** - `String` (required)  
the chart type, possible values :
    - `Line`
    - `Bar`
    - `Pie`
- **data** - `Object`
the data object like this
```javascript
const data = {
    labels: ["A", "B", "C"],
    series:[[1, 3, 2], [4, 6, 5]]
}
```
- **options** - `Object`  
the options object, see defaultOptions on [API Documentation](https://gionkunz.github.io/chartist-js/api-documentation.html)
- **event-handlers** - `Array`  
a special array to use `chart.on(event, function)`  
```javascript
const eventHanders = [{
    event: 'draw',
    fn: function () {
        //animation
    }
}, {
    //an other event hander
}]
```
- **responsive-options** - `Object`  
the object for responsive options

Example :
```html
<chartist
    id-chart="ct-chart"
    ratio="ct-major-second"
    type="Line"
    :data="chartData"
    :options="chartOptions" >
</chartist>
```
>*Note: think about using the [dynamic props](http://vuejs.org/guide/components.html#Dynamic_Props) of Vuejs to bind easliy your data or other.*

```javascript
new Vue({
    el:'#app',
    data: {
        chartData: {
            labels: ["A", "B", "C"],
            series:[[1, 3, 2], [4, 6, 5]]
        }
    },
    chartOptions: {
        lineSmooth: false
    }
})
```

### Customize chart with no data
If chart datas are empty or not definite the plugin add `ct-nodata` class and witre a message on the element. Way, you can customize your element with CSS when you have no data to display. To choose your message use the options plugin :
```javascript
Vue.use(require('chartist-vuejs'), {
    messageNoData: "You have not enough data"
})
```

## Run an example
    git clone https://github.com/Yopadd/chartist-vuejs.git
    cd chartist-vuejs
    npm install
    npm start
Go to http://localhost:1337/
