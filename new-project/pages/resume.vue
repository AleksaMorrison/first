<template lang="pug">
.space.resume
  h1.resume__heading {{ name }}
  h2.resume__role {{ role }}
  .resume-block
    span.resume-block__location {{ address }}
    ul.resume-block__social
      li.resume-block__linkedin
        span.contact-me {{ contactMe }}
        a.linked-in(href="https://www.linkedin.com/in/morrison-aleksa/" target="_blank") {{ linkedIn }}

  .resume-block.skills
    h3.resume-block__heading {{ skillsHeading }}
    ul.resume-block__list
      li.resume-block__item(v-for="skill in skills")
        p {{ skill.name }}
  .resume-block.companies
    h3.resume-block__heading {{ expHeading }}
    ul.resume-block__list
      li.resume-block__item(v-for="company in companies")
        span.resume-block__date {{ company.date }}
          .resume-block__place
            span.resume-block__place-name {{ company.name }}
            span.resume-block__role {{ company.role }}
        ul.resume-block__sublist
          li.resume-block__item-sublist(v-for="exp in company.exps")
            p {{ exp.name }}
        img.git(alt="git lab overview" src="../assets/images/git.png")

  .resume-block.education
    h3.resume-block__heading {{ educationHeading }}
    ul.resume-block__list
      li.resume-block__item(v-for="education in educations")
        span.resume-block__date {{ education.date }}
        .resume-block__place
          span.resume-block__place-name {{ education.name }}
          span.resume-block__role(v-if="role") {{ education.role }}
        ul.resume-block__sublist
          li.resume-block__list-item(v-for="exp in education.exps")
            p {{ exp.name }}
</template>

<script>
  definePageMeta({
    layout: 'default',
  });

  export default {
    components: {},
    data() {
      return {
        name: 'Aleksandra Morrison',
        role: 'Front-end Developer',
        address: 'Mountain View, California, United States',
        linkedIn: 'LinkedIn',
        skillsHeading: 'Skills:',
        contactMe: 'Contact me at',
        educationHeading: 'Education',
        expHeading: 'Experience',
        companies: [
          {
            date: 'September 2021 - Present',
            name: 'Voximplant -',
            role: 'Front-end Developer',
            exps: [
              {
                name: 'Creating responsive web and landing pages for the company website using VueJS, HTML, CSS, and TypeScript;',
              },
              { name: 'Creating reusable and modular Vue.js components;' },
              { name: 'Ensure cross-browser compatibility and responsive design across devices;' },
              { name: 'Performing debugging using Chrome Dev Tools to identify and scope bugs;' },
              { name: 'Merging pull requests and deploying web pages using GitLab;' },
              {
                name: 'Collaborate across the teams, including design and product teams, throughout the development cycle;',
              },
              {
                name: 'When on-call duty, responding to incidents, troubleshooting, and debugging issues, coordinating incident response, and implementing hotfixes.',
              },
            ],
          },
        ],
        educations: [
          {
            date: 'September  2019 - March 2021',
            name: 'HTML Academy',
            role: 'Front-end Developer',
            exps: [
              {
                name: 'Successfully completed and defended graduation project',
              },
            ],
          },
          {
            date: 'September  2009 - March 2013',
            name: 'Moscow University of Industry and Finance (MUIF)',
            exps: [
              {
                name: 'Business Administration and Management, General.',
              },
            ],
          },
        ],
        skills: [
          { name: 'Vuejs' },
          { name: 'CSS' },
          { name: 'LESS' },
          { name: 'SASS' },
          { name: 'HTML5' },
          { name: 'Git' },
          { name: 'GitLab' },
          { name: 'Jira' },
          { name: 'Slack' },
          { name: 'Figma' },
        ],
      };
    },
  };
</script>
<style scoped lang="scss">
  .resume {
    &__role {
      color: #2b8add;
      margin-bottom: 15px;
    }
    & .resume-block {
      display: flex;
      flex-direction: column;

      &:not(:last-child) {
        margin-bottom: 25px;
      }

      &__heading {
        position: relative;
        padding-left: 15px;
        margin-bottom: 10px;

        &::before {
          content: '';
          position: absolute;
          width: 8px;
          height: 2px;
          background-color: #2b8add;
          top: 50%;
          left: 0;
        }
      }

      &__linkedin {
        display: flex;
        gap: 10px;

        & .linked-in {
          color: #808080;
          transition: color 0.3s ease-in-out;

          &:hover {
            color: #ffd166;
          }
        }
      }

      &__list {
        display: flex;
        flex-direction: column;
        padding-left: 15px;
      }

      &__item {
        display: flex;
        flex-direction: column;

        & img {
          max-width: 700px;
        }
      }

      &__place {
        display: flex;
        flex-direction: row;
        gap: 10px;
      }

      &__place-name,
      &__role {
        font-weight: 600;
        color: black;
        font-style: italic;
      }

      &__date {
        color: #808080;
      }

      &.skills {
        flex-direction: row;
        align-items: baseline;
        gap: 15px;
        & .resume-block__list {
          display: flex;
          gap: 10px;
          flex-direction: row;
        }

        & .resume-block__item {
          padding: 0 5px;
          background-color: #ffd166;
        }
      }

      &.companies {
        & .resume-block__sublist {
          gap: 5px;
          display: flex;
          flex-direction: column;
        }

        & img {
          margin-top: 15px;
        }

        & .resume-block__item-sublist {
          position: relative;
          padding-left: 15px;

          &::before {
            content: '';
            position: absolute;
            width: 5px;
            height: 5px;
            background-color: #2b8add;
            top: 50%;
            left: 0;
            border-radius: 50%;
          }
        }
      }

      &.education {
        & .resume-block__list {
          gap: 15px;
        }
      }
    }
  }
</style>
