## Generic easing functions lib
Originally made for use with wanted-tuts.com.


Functions:
```
linear
easeInQuad
easeOutQuad
easeInOutQuad
easeInCubic
easeOutCubic
easeInOutCubic
easeInQuart
easeOutQuart
easeInOutQuart
easeInQuint
easeOutQuint
easeInOutQuint
```


Usage:

```js
const Tween = require('ease-lib');
const scrollTo = ({target}) => {

  var duration, doc, from, to, start, timer, delta;

  if (!target) {
    return;
  }
  duration = 256;

  doc = document.documentElement;
  from = window.scrollY || doc.scrollTop || 0;
  to = target.offsetTop - 30;
  start = new Date().getTime();
  delta = to - from;

  document.body.scrollTop = from;

  timer = setInterval(() => {

    var percent = Tween.easeInQuad(
        Math.min(1, (new Date().getTime() - start) / duration)
    );

    document.body.scrollTop = from + percent * delta;

    if (percent === 1) {
      clearInterval(timer);
    }

  }, 25);

}

export default scrollTo;

```

