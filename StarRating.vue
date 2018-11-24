<template>
  <div>
    <span>{{rating}}</span>
    <div class="stars-outer">
      <div class="stars-inner" :style="{width: `${starWidthPercentage}%`}"></div>
    </div>
  </div>
</template>

<script>
  const props = {
    rating: {
      type: Number,
      default: 0
    }
  }

  const totalStars = 5;

  function starWidthPercentage() {
    return (this.rating / totalStars) * 100
  }

  const StarRating = {
    props,
    computed: {
      starWidthPercentage
    }
  }

  export default StarRating;
</script>

<style scoped lang="scss">
  @font-face {
    font-family: 'FontAwesome';
    src: url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/fonts/fontawesome-webfont.eot?v=4.7.0');
    src: url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/fonts/fontawesome-webfont.eot?#iefix&v=4.7.0') format('embedded-opentype'), 
    url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/fonts/fontawesome-webfont.woff2?v=4.7.0') format('woff2'), 
    url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/fonts/fontawesome-webfont.woff?v=4.7.0') format('woff'), 
    url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/fonts/fontawesome-webfont.ttf?v=4.7.0') format('truetype'), 
    url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/fonts/fontawesome-webfont.svg?v=4.7.0#fontawesomeregular') format('svg');
    font-weight: normal;
    font-style: normal
  }

  .stars-outer {
    margin-left: 20px;
    display: inline-block;
    position: relative;
    font-family: FontAwesome;

    &::before {
      content: "\f006 \f006 \f006 \f006 \f006";
    }
  }

  .stars-inner {
    position: absolute;
    top: 0;
    left: 0;
    white-space: nowrap;
    overflow: hidden;
    width: 0;

    &::before {
      content: "\f005 \f005 \f005 \f005 \f005";
      color: #f8ce0b;
    }
  }
</style>
