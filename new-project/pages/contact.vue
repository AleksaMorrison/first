<template lang="pug">
.space.contact
  p.text I am currently based in Mountain View, California.
  .contact-info
    a.tel(href="tel:+1 510 2298019") +1 510 2298019
    a.email(href="mailto:aleksa.morrison@gmail.com") aleksa.morrison@gmail.com
    a.github(href="https://github.com/AleksaMorrison") Github
    a.fb(href="https://www.facebook.com/AleksaMorrison") Facebook
</template>

<script>
  definePageMeta({
    layout: 'default',
  });

  export default {
    components: {},
    setup() {},
  };
</script>
<style scoped lang="scss">
  .contact {
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    gap: 16px;

    & .contact-info {
      display: flex;
      justify-content: center;
      gap: 16px;
      & a {
        color: #979797;
        transition: color 0.3s ease;
        text-decoration: none;

        &:hover,
        &:active,
        &:focus {
          color: black;
        }
      }

      & .tel {
        position: relative;
        padding-left: 30px;

        &::before {
          position: absolute;
          content: '';
          width: 20px;
          height: 20px;
          left: 0;
          top: 2px;
          background-image: url(../assets/icons/phone.svg);
          background-repeat: no-repeat;
          background-position: center;
          background-size: contain;
        }
      }

      & .email {
        position: relative;
        padding-left: 30px;

        &::before {
          position: absolute;
          content: '';
          width: 20px;
          height: 20px;
          left: 0;
          top: 3px;
          background-size: contain;
          background-repeat: no-repeat;
          background-position: center;
          background-image: url(../assets/icons/email.svg);
        }
      }
      & .github {
        position: relative;
        padding-left: 30px;

        &::before {
          position: absolute;
          content: '';
          width: 20px;
          height: 20px;
          left: 0;
          top: 2px;
          background-size: contain;
          background-repeat: no-repeat;
          background-position: center;
          background-image: url(../assets/icons/github.svg);
        }
      }
      & .fb {
        position: relative;
        padding-left: 30px;

        &::before {
          position: absolute;
          content: '';
          width: 20px;
          height: 20px;
          left: 0;
          top: 2px;
          background-size: contain;
          background-repeat: no-repeat;
          background-position: center;
          background-image: url(../assets/icons/facebook.svg);
        }
      }
    }
  }
</style>
