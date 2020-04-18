<template>
  <footer
    class="footer"
    :class="{ [`footer-${type}`]: type }"
    :data-background-color="backgroundColor"
  >
    <div class="container">
      <nav>
        <ul>
          <li>
            <a href="https://beta.companieshouse.gov.uk/company/12552450">
              About
            </a>
          </li>
          <li>
            <a href="https://habr.com/ru/users/alexeysushkov/posts/">
              Blog
            </a>
          </li>
        </ul>
      </nav>
      <div class="copyright">
        &copy; {{ year }},
        <a href="https://beta.companieshouse.gov.uk/company/12552450" target="_blank" rel="noopener"
          >Global ID LTD</a
        >
      </div>
    </div>
  </footer>
</template>
<script>
export default {
  props: {
    backgroundColor: String,
    type: String
  },
  data() {
    return {
      year: new Date().getFullYear()
    };
  }
};
</script>
<style></style>
