<script>
export default {
  data () {
    return {
      data: {}
    }
  },
  created () {
    fetch('/src/assets/data.json')
      .then(response => {
        if (response.status === 200) {
          response.json().then(data => {
            this.data = data
          })
        } else {
          console.error('Error: Unable to fetch data.json')
        }
      })
    }
}
</script>

<template>
  <li class="card" v-for="item in data" :key="item.id">
    <div class="card--wrapper">
      <div class="card--content"> 
        <div class="card-top">
          <div class="company">
            <div class="company-logo">
              <img v-bind:src="item.logo" alt="Company logo">
            </div>
          </div>
          
          <div class="card-middle">
            <div class="card-middle-top">
              <span class="company-name"> {{ item.company }}</span>
              <div class="tags">
                <span v-if="item.new" class="tag tag--new">NEW!</span>
                <span v-if="item.featured" class="tag tag--feat">FEATURED</span>
              </div>
            </div>
            

            <div class="card-middle-bottom">
              <div class="job-title">{{ item.position }}</div>
              <div class="job-meta">
                <span class="job-meta--text">{{ item.postedAt }}</span>
                <span class="job-meta--middot">&middot;</span>
                <span class="job-meta--text"> {{ item.contract }}</span>
                <span class="job-meta--middot">&middot;</span>
                <span class="job-meta--text"> {{ item.location }}</span>
              </div>
            </div>
          </div>
        </div>
        <div class="job-stack">
          <ul class="job-stack--list">
            <li class="job-stack--item">Frontend</li>
            <li class="job-stack--item">Senior</li>
            <li class="job-stack--item">HTML</li>
            <li class="job-stack--languages">
              <div class="job-stack--item" v-for="language in item.languages" :key="language">
                {{ language }}
              </div>
            </li>
            <li v-if="item.tools.length > 0" class="job-stack--tools">
              <template v-if="item.tools.length > 0">
                <div class="job-stack--item" v-for="tool in item.tools" :key="tool">
                  {{ tool }}
                </div>
              </template>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </li>
</template>

<style scoped lang="scss">
$dark-grayish-cyan-shade: rgba(hsl(180, 8%, 52%), 0.25);
.card {
  padding: 25px 0 16px;
  &--wrapper{
    margin: 0 auto;
    list-style: none;
    border-left: 5px solid var(--desaturated-dark-cyan);
    border-radius: 5px;
    background-color: #fff;
    box-shadow:  0px 8px 20px $dark-grayish-cyan-shade;
    max-width: 327px;
    padding: 32px 19px 24px;
    .company-name {
      color: var(--desaturated-dark-cyan);
      font-size: 13px;
      font-weight: 700;
    }
    .tags {
      .tag {
        font-size: 12px;
        font-weight: 700;
        color: #fff;
        padding: 6px 8px 4px;
        border-radius: 16px;
        &--new {
          background-color: var(--desaturated-dark-cyan);
        }
        &--feat {
          background-color: var(--very-dark-grayish-cyan);
          border-radius: 16px;
        }
      }
    }
    .company {
      position: relative;
      display: flex;
      align-items: center;
      gap: 8px;
      .company-logo {
        img {
          width: 100%;
        }
        width: 50px;
        height: 50px;
        position: absolute;
        z-index: 1;
        top: -57px;
        svg {
          width: 50px;
          height: 50px;
        }
      }
    }
    .card-middle-top {
      display: flex;
      gap: 16px;
      flex-wrap: wrap;
      align-items: center;

      .tags {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
      }
    }
    .job-title {
      font-size: 14px;
      font-weight: 700;
      padding-top: 12px;
      
      &:hover {
        color: var(--desaturated-dark-cyan);
        cursor: pointer;
      }
    }
    .job-meta {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 8px;
      padding-block: 16px;
      border-bottom: 1px solid var(--dark-grayish-cyan);
      margin-bottom: 16px;
      &--text {
        font-weight: 500;
        color: var(--dark-grayish-cyan);
      }
      &--middot {
        font-size: 25px;
        line-height: 5px;
        color: var(--dark-grayish-cyan);
      }
    }
    .job-stack {
      &--list {
        list-style: none;
        padding: 0;
        display: flex;
        flex-wrap: wrap;
        gap: 16px;
      }

      &--item{
        font-size: 13px;
        font-weight: 700;
        color: var(--desaturated-dark-cyan);
        padding: 6px 8px 4px;
        border-radius: 4px;
        background-color: var(--light-grayish-cyan);

        &:hover {
          background-color: var(--desaturated-dark-cyan);
          color: #fff;
          cursor: pointer;
        }
      }

      &--languages,
      &--tools {
        display: flex;
        gap: 16px;
        flex-wrap: wrap;
      }
    }
  }
  @media(min-width: 768px) {
    .card{
      &--wrapper {
        max-width: 1110px;
        padding: 24px 32px;
        .company {
          .company-logo {
            position: relative;
            top: initial;
            width: 88px;
            height: 88px;
          }
        }
        .card-top {
          display: flex;
          gap: 24px
        }
      }

      &--content {
        display: flex;
        justify-content: space-between;
        gap: 24px;
        .job-meta {
          border-bottom: none;
          margin-bottom: 0;
          padding-bottom: 0;
        }
      }

      &--top {
        display: flex;
        justify-content: flex-start;
        border: 1px solid red ;
      }
    }
    .job-stack {
      display: flex;
      align-items: center;
      &--list {
        justify-content: flex-end;
      }
    }
  }
}
</style>
