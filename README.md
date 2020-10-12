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