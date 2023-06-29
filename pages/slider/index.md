<script>
    import Slider from '../../../../../src/lib/ui/Slider.svelte';
    let score = 8;

</script>

## Slider Component
**Contributed by: [@kuatroka](https://github.com/kuatroka)**

- It's a slider component that lives in `./components`  
- We import it here and bind its only attribute `value` to a variable `score` declared in `script` section
- Then we add some text that dynamically changes when we move the slider
- `value` comes from the imported `Slider.svelte`
- `score` is bound to this `value` variable

<Slider 
    min=0
    max=20
    step=1
    bind:value={score}
/>

The score is: **{score}**