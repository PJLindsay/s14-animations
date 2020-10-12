# s14-animations

Udemy Vue3 course - Section 14 [Animation and CSS Transitions]

## Concepts

- transition wrapper:
  - adds css utility classes:
    - enter-from (first)
    - enter-to (added when animation finishes)
    - enter-active
    - leave-from
    - leave-active
    - leave-to
  - analyses CSS code for CSS class names, find duration and add css classes over duration
  - ** removes element from DOM ** when duration is over
  - helpful for v-if and v-show
  - can also be used to apply an animation

- using custom CSS class names
  - put prefix in 'name' attribute of the transition to differentiate animation styles (e.g. para)
    - this gives you para-enter-to instead of default v-enter-to
    - allows multiple different transitions/component usage in same component
  - for completely custom class names (e.g. using 3rd party animation library):
    - use enter-to-class="" attributes on transition

- GOTCHA: because in Vue 3 we can have more than one root element:
    - fall through will cause animation to not work (transition wants just one child element)
    - backdrop and dialog in BaseModal.vue (comment out backdrop to see)
    - SOLUTION: move transition wrapper from App.vue to BaseModal.vue

- GOTCHA: transition is not part of template so v-if won't get animation/transition
  - SOLUTION: use :open property (instead of v-if) to control open/close

- transition typically needs only 1 child element, exception:
  - swapping in/out components (transition) - e.g. v-if with v-else
  - use transition 'mode' to control which button can be animated first (don't see 2 buttons at same time)

### Using Transition Events

-  @before-enter | @enter | @after-enter | @before-leave | @leave | @after-leave
- c/w parameter for element
- allows use of JS in various phases of animation
- can control entire animation w/ JS using Transition events (e.g. 3rd party JS animation libraries: GreenSock)

  must use done() to notify Vue explicitly when finished

  GOTCHA: animations can run at same time (e.g. opacity in and opacity out - you will get flickering)
  SOLUTION: @enter-cancelled | @leave-cancelled

### Disable CSS Transitions

- :css="false"
- tells Vue not to search for css classes and don't attempt to read durations
- skips CSS analysis (seeking classes, etc.)
- improves performance (if you're not using CSS code for transition)

### Animated Lists

transition-group used to work with multiple elements (lists)
can animate single elements or multiple elements at same time

transition renders no element to DOM
transition-group does render element to DOM

can use any HTML element as tag (tag="ul)
use name as prefix for events styling class names

GOTCHA: list jumps when items added
FIX: use x-move class to animated elements not being removed

move: (e.g. user-list-move) Vue will use transform under hood for moving elements which are not added or removed

GOTCHA: snapping animation on remove (e.g. remove item from middle of list)
FIX: on 'leave-active' class, use 'position: absolute'

### Animating Route Changes

GOTCHA: Older versions of Vue: router-view can no longer be used directly inside transition (use slot props instead)
FIX: use transition element inside router-view and :is="slotProps.Component"

GOTCHA: when you first load - first route is empty route so you get 'unwanted' animation on first load
FIX: call router.isReady() in main.js with then block and mount app only when router is fully setup and aware of page to be loaded

when animating route changes you must not have multiple root elements!