<template>
  <footer class="footer__wrapper">
    <span class="mr-1">&copy; {{ currentYear }} |</span>
    <span class="mr-1"><i class="fas fa-code"></i></span>
    <span class="mr-1">built with</span>
    <span class="mr-1 heart__salmon"><i class="fas fa-heart "></i></span>
    <span class="mr-1">by</span>
    <span class="mr-1">
      <a
        class="footer__link"
        target="blank"
        title="Fady Soliman Website"
        href="http://fadysoliman.name"
      >
        Fady Soliman
      </a>
    </span>
  </footer>
</template>

<script>
export default {
  name: "FooterComponent",
  data() {
    return {
      currentYear: new Date().getFullYear()
    };
  }
};
</script>
<style lang="scss">
.footer__wrapper {
  font-size: 12px;
  background: #333333;
  color: #cccccc;
  display: flex;
  flex-flow: row wrap;
  justify-content: flex-end;
  padding: 2rem;

  .heart__salmon {
    color: salmon;
  }

  .footer__link {
    color: #1de9b6;
    text-decoration: none;
  }
}
</style>
