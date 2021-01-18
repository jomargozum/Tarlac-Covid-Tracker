<template>
  <nav id="navbar-id" class="navbar is-clearfix is-transparent">
    <div class="navbar-brand">
      <nuxt-link to="/" class="navbar-item ">
        <span style="font: bold 20px sans-serif;">Tarlac Covid Tracker</span>
      </nuxt-link>
      <div class="navbar-burger burger" data-target="navbarExampleTransparentExample">
        <span />
        <span />
        <span />
      </div>
    </div>

    <div id="navbarExampleTransparentExample" class="navbar-menu">
      <div class="navbar-end has-text-weight-medium">
        <nuxt-link class="navbar-item" to="/">
          HOME
        </nuxt-link>
        <nuxt-link class="navbar-item" to="/404">
          CASES
        </nuxt-link>
        <nuxt-link class="navbar-item" to="/404">
          LATEST NEWS
        </nuxt-link>
      </div>
    </div>
  </nav>
</template>
<script>
import $ from 'jquery'
export default {
  mounted () {
    $(document).ready(function () {
      // Check for click events on the navbar burger icon
      $('.navbar-burger').click(function () {
      // Toggle the "is-active" class on both the "navbar-burger" and the "navbar-menu"
        $('.navbar-burger').toggleClass('is-active')
        $('.navbar-menu').toggleClass('is-active')
      })
    })
    $(window).scroll(function () {
      const nav = $('#navbar-id')
      const img = $('#img-logo')
      const top = 200
      if ($(window).scrollTop() >= top) {
        nav.removeClass('is-transparent')
        nav.addClass('is-fixed-top')
        img.removeClass('yb-logo')
        img.addClass('yb-logo-dark')
      } else {
        nav.removeClass('is-fixed-top')
        nav.addClass('is-transparent')
        img.removeClass('yb-logo-dark')
        img.addClass('yb-logo')
      }
    })
  }
}
</script>
<style lang="scss">
.navbar {
&.is-transparent {
     background-color: transparent
}
}
  .navbar {
        color: #fff;
        border: none;
        padding: 10px 20px;
        text-decoration: none;
        -webkit-transition: background 1s; /* For Safari 3.0 to 6.0 */
        transition: background 1s; /* For modern browsers */
    }
</style>
