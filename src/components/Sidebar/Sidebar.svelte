<script>
  import Profile from "../Profile";
  import Stories from "../Stories";
  import Footer from "../Footer";
</script>

<div class="Sidebar">
  <div class="Sidebar-container">
    <Profile />
    <Stories />
    <Footer />
  </div>
</div>

<style>
  .Sidebar {
    position: relative;
    padding: 4.5em 0 0 0;
  }
  .Sidebar-container {
    position: fixed;
  }
</style>
