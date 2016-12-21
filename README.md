# Auto0px.js
A library for transition between automatic CSS values and absolute ones               
## Problem:
  While CSS transitions work well with JavaScript, there is one exception; when
  you change 'height: auto' to 'height: 0px'. This immediately jumps to the
  ending position. To fix this you have to change the element's height to it's
  calculated one and then set it to 0px. However this problem gets even more
  complicated because some browsers (Firefox 50 and IE 11 in my experience)
  don't let you change a CSS property to an absolute property right after
  changing it from auto to another absolute value. Furthermore a transition from
  0px to auto involves longer timeouts which has to be cancellable otherwise the
  main feature of transitions would be lost.

  In conclusion you have to run a function first, wait a few milliseconds,
  change some CSS properties and after the transition finishes run another
  function. And both timeouts should handle changing the animation.

Example of a modal fade out animation:

  *  Set opacity to 1 and height to calculated value
  *  Wait for browser processing the request
  *  Set opacity to 0 and height to 0px
  *  Wait for transition
  *  Set display to none

Reverse of this animation:

  *  Set opacity to 0, height to 0px and display to block
  *  Wait for browser
  *  Set opacity to 1 and height to calculated value
