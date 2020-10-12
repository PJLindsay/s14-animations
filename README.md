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