<template>
  <div class="footer-section">
    <div class="left-wrapper">
      <h4 class="logo-style"><span>cloud</span>9 Movies</h4>
      <p class="movies-content">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus assumenda asperiores eveniet
        perspiciatis iusto iure.
      </p>
      <div class="social-icons">
        <i class="fa-brands fa-facebook-f"></i>
        <i class="fa-brands fa-x-twitter"></i>
        <i class="fa-brands fa-whatsapp"></i>
        <i class="fa-brands fa-instagram"></i>
      </div>
    </div>
    <div class="right-wrapper">
      <div class="users">
        <p class="follower"><i class="fa-solid fa-hashtag"></i> followers</p>
        <div class="user-image">
          <div class="profile-image">
            <img src="/public/images/Ellipse 5.png" alt="user profiles" />
            <img src="/public/images/Ellipse 5-1.png" alt="user profiles" />
            <img src="/public/images/Ellipse 5-2.png" alt="user profiles" />
          </div>
          <div class="user-name">
            <p>Kate, Saviour, and 17 other</p>
          </div>
        </div>
      </div>
      <div class="subscription">
        <input type="text" placeholder="subscribe with email" /><button>Submit Email</button>
      </div>
    </div>
  </div>
</template>

<script setup></script>

<style>
.footer-section {
  width: 100%;
  padding: 1rem 2.5rem;
  background: var(--secondary-color);
  display: flex;
  gap: 30px;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
}

.social-icons {
  display: flex;
  gap: 10px;
}

.social-icons .fa-brands:hover {
  background: red;
  transition: background-color 0.3s ease-in;
  color: #fff;
  transition: ease-out 0.5s;
  transform: translateY(-8px);
}

.left-wrapper {
  flex-direction: column;
  display: flex;
  gap: 32px;
}
.left-wrapper .movies-content {
  color: #fff;
  max-width: 230px;
  font-size: calc(9px + 0.5vw);
}

.subscription {
  height: 35px;
  display: flex;
  justify-content: space-between;
  border: none;
  outline: none;
  min-width: 320px;
  gap: 13px;
  background: #fff;
  border-radius: 14px;
}

.right-wrapper {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  align-items: space-between;
}

.subscription input {
  padding: 5px 10px;
  border-radius: 14px;
  outline: none;
  border: none;
}
.users .profile-image img {
  width: 35px;
  border: 1.5px solid #fff;
  margin-left: -9px;
  border-radius: 50px;
}
.users .user-name {
  margin-left: 9px;
  color: gray;
  font-size: calc(12px + 0.5vw);
}
.users {
  background: #fff;
  min-width: 320px;
  padding: 2rem;
  border-radius: 19px;
}

.users .follower {
  font-weight: 800;
  font-size: 3rem;
  font-size: var(--style-font);
  color: var(--primary-color);
}
.user-image {
  display: flex;
  align-items: center;
  margin-top: 13px;
}
.subscription button {
  background: red;
  color: #fff;
  padding: 3px 7px;
  border-radius: 14px;
  border: none;
  cursor: pointer;
}

.social-icons .fa-brands {
  display: flex;
  justify-content: center;
  font-size: 16px;
  width: 35px;
  border-radius: 50px;
  background: #fff;
  color: var(--primary-color);
  padding: 10px;
}
</style>
