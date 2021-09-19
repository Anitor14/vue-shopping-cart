<template>
  <footer class="main-footer">
    <div class="container main-footer-container">
      <h3 class="team-name">Blue Cooperation</h3>
      <ul class="nav footer-nav">
        <li>
          <a href="https://www.youtube.com" target="#">
            <img src="../assets/images/YoutubeLogo.png" />
          </a>
        </li>
        <li>
          <a href="https://www.facebook.com" target="#">
            <img alt="Facebook logo" src="../assets/images/FacebookLogo.png" />
          </a>
        </li>
      </ul>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style scoped>
.main-footer {
  background-color: #56ccf2;
  color: white;
  padding: 0.25em 0;
}
.main-footer-container {
  display: flex;
  align-items: center;
  justify-content: space-around;
}
.main-footer-container ul {
  text-align: end;
}
.footer-nav li {
  padding: 0 0.5em;
}
.footer-nav img {
  width: 30px;
  height: 30px;
}
</style>
