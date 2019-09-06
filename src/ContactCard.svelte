<script>
  import FaDribbble from "svelte-icons/fa/FaDribbble.svelte";
  import FaBehance from "svelte-icons/fa/FaBehance.svelte";
  import FaLinkedinIn from "svelte-icons/fa/FaLinkedinIn.svelte";

  export let userName;
  export let imageUrl;
  export let jobPosition;
  export let userDescription;
</script>

<style>
  .main-card {
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    background: #ffffff;
    width: 80%;
    max-width: 600px;
    display: flex;
    flex-direction: column;
    text-align: center;
    padding: 2em;
    margin-bottom: 30px;
  }
  .ul-profile {
    display: flex;
    justify-content: space-around;
    list-style: none;
    margin: 0;
    padding: 0;
    width: 110px;
    margin: 0 auto;
    padding: 5px;
  }
  .thumb{
      border-radius: 50%;
      
  }

  .thumb-placeholder{
      border-radius: 50%;
      border: 3px solid #c50756;
      width: 125px;
      height: 125px;
  }
  .profile-image {
    border-radius: 50%;
    border: 3px solid #c50756;
  }

  .icon-card {
    color: #c50756;
    height: 20px;
    opacity: 0.8;
  }

  .icon-card:hover {
    opacity: 1;
  }

  .profile-name {
    font-size: 1.5rem;
    line-height: 1;
  }

  .profile-name::after {
    content: "";
    display: block;
    height: 1px;
    width: 2em;
    background: #c50756;
    margin: 0 auto;
    margin-top: 1rem;
  }

  .profile-position {
    opacity: 0.6;
    font-weight: 500;
    text-transform: uppercase;
    font-size: 0.8rem;
    margin-bottom: 2em;
  }
  .profile-body {
    font-weight: 100;
  }

  @media (min-width: 600px) {
    .main-card {
      flex-direction: row;
    }

    .profile-main {
      text-align: left;
      margin-left: 2em;
    }

    .profile-name::after {
      margin-left: 0;
    }
  }
</style>

<div class="main-card">
  <div class="profile-sidebar">
  <!-- Dinamyc svelte css classes con operador ternario -->
    <!-- <div class="{imageUrl ? 'thumb' : 'thumb-placeholder'}"> -->
    <!-- o con el shorthand -->
    <div class="thumb" class:thumb-placeholder="{!imageUrl}">
      <img class="profile-image" src={imageUrl} alt={userName} />
    </div>
    <ul class="ul-profile">
      <li class="social-item">
        <a aria-label="Dribbble" href="/">
          <div class="icon-card">
            <FaDribbble />
          </div>
        </a>
      </li>
      <li class="social-item">
        <a aria-label="Behance" href="/">
          <div class="icon-card">
            <FaBehance />
          </div>
        </a>
      </li>
      <li class="social-item">
        <a aria-label="LinkedIn" href="/">
          <div class="icon-card">
            <FaLinkedinIn />
          </div>
        </a>
      </li>
    </ul>
  </div>
  <div class="profile-main">
    <h2 class="profile-name">{userName}</h2>
    <p class="profile-position">{jobPosition}</p>
    <p class="profile-body">{userDescription}</p>
  </div>
</div>
