<script lang="ts">
  export let size: 'small' | 'medium' | 'large'
  export let fill: string = 'currentColor'
</script>

<svg class="svg-{size}" {fill} viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
  <path
    d="M8.3,12.8H5.8C4.3,12.8,3,11.6,3,10s1.3-2.8,2.8-2.8h2.5c0.3,0,0.5-0.2,0.5-0.5S8.6,6.2,8.3,6.2H5.8C3.7,6.2,2,7.9,2,10s1.7,3.8,3.8,3.8h2.5c0.3,0,0.5-0.2,0.5-0.5S8.6,12.8,8.3,12.8z"
  />
  <path d="M6.2,10c0,0.3,0.2,0.5,0.5,0.5h6.7c0.3,0,0.5-0.2,0.5-0.5s-0.2-0.5-0.5-0.5H6.7C6.4,9.5,6.2,9.7,6.2,10z" />
  <path
    d="M14.2,6.2h-2.5c-0.3,0-0.5,0.2-0.5,0.5s0.2,0.5,0.5,0.5h2.5c1.6,0,2.8,1.3,2.8,2.8s-1.3,2.8-2.8,2.8h-2.5c-0.3,0-0.5,0.2-0.5,0.5s0.2,0.5,0.5,0.5h2.5c2.1,0,3.8-1.7,3.8-3.8S16.3,6.2,14.2,6.2z"
  />
</svg>
