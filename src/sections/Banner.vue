<template>
    <header>

      <div class="title">
        <span class="text-bubble">Hello, I am</span>
        <h1>Ben Lawrence</h1>
        <h2>Software Engineer</h2>
      </div>

      <ul class="details">
        <span class="text-bubble">Contact me!</span>
        <li>
          <img src="@/assets/Email.svg"/>
          12blawrence4@gmail.com
        </li>
        <li>
          <img src="@/assets/Phone.svg"/>
          +64 23802487
        </li>
        <li>
          <img src="@/assets/Location.svg"/>
          Hamilton, New Zealand
        </li>
      </ul>

      <picture>
        <img src="@/assets/pfp.jpg" alt="Picture of Ben Lawrence"/>
      </picture>

    </header>
</template>

<script>
export default {
  name: "Banner",
}
</script>

<style lang="scss" scoped>

@import '@/GlobalVariables.scss';

header {
  display: grid;
  grid-template-areas: 
    "title picture"
    "details picture";

  min-height: 400px;
  gap: 40px;

  letter-spacing: .07em;

  margin-block: 16vh;

  ul {
    list-style-type: none;
    padding: 0;
    margin-top: 40px;

    li {
      margin-block: 10px;
    }
  }
}

.title {
  grid-area: title;

  h1 {
    display: flex;
    flex-direction: column;

    font-size: 4rem;

    margin-block: 10px;
  }
  
  h2 {
    font-weight: 500;
    margin: 0;
    opacity: .8;
  }
}


.details {
  grid-area: details;
  display: flex;
  flex-direction: column;

  li {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 10px;
    
    letter-spacing: .08em;
    padding-block: 5px;
  }

  img {
    width: 30px;
  }
}

picture {
  grid-area: picture;
  margin: 0;

  width: 20vmax;
  height: 20vmax;

  max-width: 300px;
  max-height: 300px;

  margin-block: auto;

  overflow: hidden;
  
  box-shadow: 0 0 5px 2px $primary;
  border: 5px solid rgb(22, 19, 28);
  
  border-radius: 100%;
  transition: border-radius 300ms ease-in-out;

  img {
    aspect-ratio: 1 / 1;
    width: 100%;
    height: 100%;
    
    object-fit: cover;
    object-position: center;
  }
}

@media (max-width: 1000px) {
  header {
    grid-template-areas: "picture title" "picture details"
  }

  picture {
    margin: auto 0 auto auto;
  }
}

@media (max-width: 640px) {
  header {
    grid-template-areas: "picture" "title" "details";
    margin-top: 20px;
    gap: 40px;
  }

  picture {
    margin: auto auto auto 0;
  }
}

</style>