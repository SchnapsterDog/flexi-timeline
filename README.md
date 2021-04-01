[[Flexi Timeline ]](https://akrinum.com)

[![prs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](https://github.com/SchnapsterDog/flexi-timeline/pulls)
[![npm version](https://img.shields.io/bundlephobia/min/flexi-timeline?style=flat-square)](https://www.npmjs.com/package/flexi-timeline)

Welcome to [version 0.0.2]() of **Flexi Timeline**, an easy to implement, and well maintained **Vue.js** component.

You can support this project by giving it a star, or following the author. :heart:.

## :exclamation::exclamation::exclamation: This is README for FlexiTimeline component :exclamation::exclamation::exclamation:

Flexi Timeline vue component made by [Oliver](https://akrinum.com)

## ⚙ Installation

- npm install flexi-timeline --save

## 🤔 How to use it? 

### Module usage 

```js
import FlexiTimeline from 'flexi-timeline';

export default {
  name: 'yourComponent',
  components: { FlexiTimeline },
  widgets: [
    {
      title: 'some Title 1',
      subTitle: 'Some SubTitle',
      description: 'Some Description',
      buttonText: 'Some ButtonText'
    },
    {
      title: 'some Title 2',
      subTitle: 'Some SubTitle',
      description: 'Some Description',
      buttonText: 'Some ButtonText'
    },
    {
      title: 'some Title 3',
      subTitle: 'Some SubTitle',
      description: 'Some Description',
      buttonText: 'Some ButtonText'
    },
    {
      title: 'some Title 4',
      subTitle: 'Some SubTitle',
      description: 'Some Description',
      buttonText: 'Some ButtonText'
    }
  ]
}
```

```html
<flexi-timeline
  :widgets="widgets"
  :widgetsAos="true"
  :widgetsAosType="'fade-up'"
  :widgetsAosDuration="'1500'"
  @button-clicked="openModal"
/>
```

### Browser usage

Include the script file, then install the component with `Vue.use(FlexiTimeline);` e.g.:

```html
<script type="text/javascript" src="node_modules/vuejs/dist/vue.min.js"></script>
<script type="text/javascript" src="node_modules/flexi-timeline/dist/flexi-timeline.min.js"></script>
<script type="text/javascript">
  Vue.use(FlexiTimeline);
</script>
```

### ❔ Props & event

```

| Name                    | Type        | Mandatory     | Description 

| :-----                  | :-------    | :--------     |------------------------------- 
| widgets                 | Array       | Yes           | List of items as given the sample above
| widgetsAos              | Boolean     | No            | By default this functionality is turned off / true for turning on Animate on Scroll Animation
| widgetsAosType          | String      | No            | Type of the AOS. By default is fade-up animation
| widgetsAosDuration      | String      | No            | Duration of the AOS. By default is 1500 (miliseconds)
| button-clicked          | Event       | No            | Fired an event when the button is clicked
```

## License

[MIT](http://opensource.org/licenses/MIT)