<script>

</script>

<template>
  <div class="filter">
    <div class="filter__wrapper">
      <div class="filter__items">

        <div class="filter__item">
          <div class="filter__item-name">
            <div class="filter__item--text">Frontend</div>
            <div class="filter__item--btn-close">&times;</div>
          </div>
        </div>
        
      </div>
      <div class="filter-btn--clear">Clear</div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.filter {
  &__wrapper {
    background-color: #fff;
    border-radius: 4px;
    display: flex;
    flex-wrap: nowrap;
    align-items: center;
    justify-content: space-between;
    gap: 8px;
    padding: 20px;
    max-width: 327px;
    margin: 0 auto;
  }
  
  &__items {
    display: flex;
    flex-wrap: wrap;
    gap: 16px;
  }

  &__item{
    font-size: 13px;
    font-weight: 700;
    color: var(--desaturated-dark-cyan);
    border-radius: 4px;
    background-color: var(--light-grayish-cyan);
    display: flex;
    
    &--text {
      padding: 6px 8px 4px;
    }

    &--btn-close {
      background-color: var(--desaturated-dark-cyan);
      color: #fff;
      border-radius: 4px;
      height: 100%;
      display: flex;
      align-items: center;
      align-self: stretch;
      padding: 0 8px;
      font-size: 24px;
      line-height: 1;

      &:hover {
        cursor: pointer;  
        background-color: var(--very-dark-grayish-cyan);
      }
    }
  }
  .filter-btn--clear {
    color: var(--dark-grayish-cyan);
    font-weight: 700;

    &:hover {
      cursor: pointer;
      text-decoration: underline;
      color: var(--desaturated-dark-cyan);
    }
  }
  
  &__item-name {
    display: flex;
    justify-content: space-between;
    gap: 8px;
    align-items: center;
  }

  @media(min-width: 768px) {
    &__wrapper {
      max-width: 1110px;
      padding: 20px 36px;
    }
  }
}
</style>
