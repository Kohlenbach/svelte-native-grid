<script>
  export let areas
  export let columns
  export let rows
  export let alignContent
  export let justifyContent
  export let alignItems
  export let justifyItems
  export let minmax
  
  function normalizedStyle() {
    let res = ''

    if (minmax) res += `grid-template-columns: repeat(auto-fit, minmax(${minmax.split(' ')[0]},${minmax.split(' ')[1]}));`
    else if (columns) res += `grid-template-columns: ${columns};`
    if (areas) res += `grid-template-areas: ${areas};`
    if (rows) res += `grid-template-rows: ${rows};`
    if (justifyContent) res += `justify-content: ${justifyContent};`
    if (justifyItems) res += `justify-items: ${justifyItems};`
    if (alignContent) res += `align-content: ${alignContent};`
    if (alignItems) res += `align-items: ${alignItems};`

    return res
  }
</script>

<div  
  class="container"
  style="{normalizedStyle()}"
>
  <slot/>
</div>

<style>
.container {
  display: grid;
}
</style>