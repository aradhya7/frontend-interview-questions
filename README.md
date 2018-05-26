# frontend-interview-questions
HTML, CSS, JS, ReactJS, Redux, Bootstrap interview questions

1.Difference between debounce and throttle

Debounce is called only once after a specific delay normally used for input kepress


function debounce(fn, delay) {
  var timer = null;
  return function () {
    var context = this, args = arguments;
    clearTimeout(timer);
    timer = setTimeout(function () {
      fn.apply(context, args);
    }, delay);
  };
}

$('input.username').keypress(debounce(function (event) {
  // do the Ajax request
}, 250));


throttle fires every time with some intervals - used for mouse moves

function throttle(fn, threshhold, scope) {
  threshhold || (threshhold = 250);
  var last,
      deferTimer;
  return function () {
    var context = scope || this;

    var now = +new Date,
        args = arguments;
    if (last && now < last + threshhold) {
      // hold on to it
      clearTimeout(deferTimer);
      deferTimer = setTimeout(function () {
        last = now;
        fn.apply(context, args);
      }, threshhold);
    } else {
      last = now;
      fn.apply(context, args);
    }
  };
}

$('body').on('mousemove', throttle(function (event) {
  console.log('tick');
}, 1000));


=========================================================================================

2.How to compare dates