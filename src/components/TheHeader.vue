<template>
  <div class="header">
    <div class="header-left">
      <div class="navs">
        <div class="act-btn">
          <button class="material-icons">home</button>
        </div>
        <div class="act-btn">
          <button class="material-icons">view_compact</button>
        </div>
      </div>
      <div class="search">
        <input type="text" class="search-bar" />
      </div>
    </div>
    <div class="logo">
      <img src="logo.png" />
    </div>
    <div class="header-right">
      <div class="act-btn add-task">
        <button class="material-icons">add</button>
      </div>
      <div class="functions">
        <div class="act-btn">
          <button class="material-icons">notifications</button>
        </div>
        <div class="act-btn">
          <button class="material-icons">help_outline</button>
        </div>
        <div class="act-btn">
          <button class="material-icons">settings</button>
        </div>
      </div>
      <div class="avatar">
        <img
          src="https://png.clipart.me/istock/previews/7063/70633839-person-avatar.jpg"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TheHeader',
}
</script>

<style scoped>
.header {
  background-color: var(--darkest);
  height: 10vh;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.header-left {
  padding: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 1rem;
}

.header-right {
  padding: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 2rem;
}

.navs {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
}

.search {
  opacity: 1;
}

.search-bar {
  width: 220px;
  height: 40px;
  background-color: var(--light);
  border-radius: 1rem;
  color: var(--white);
}

.logo {
  width: 120px;
  height: 20px;
}

.act-btn {
  border-radius: 1rem;
  background-color: var(--light);
  width: 50px;
  height: 50px;
  margin-right: 2rem;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.add-task {
  margin-right: 3rem;
  background-color: var(--blue-btn);
}

.functions {
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 1;
}

.avatar {
  width: 50px;
  height: 50px;
}

.avatar img {
  border-radius: 100%;
}

@media only screen and (max-width: 1200px) {
  .search {
    display: none;
  }
  .functions {
    display: none;
  }
}
</style>
