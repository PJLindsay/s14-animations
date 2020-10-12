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