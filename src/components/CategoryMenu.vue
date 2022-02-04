<template>
  <div class="category-menu">
      <ul>
          <li v-for="category in categoriesList" :key="category.id" @click="onCategoryClick(category.id)" :class="{ 'active' : isActive(category.id)}">
              <Component :is="category.icon" />
              <p>{{category.label}}</p>
          </li>
      </ul>
  </div>
</template>

<script>
import Pizza from '../assets/img/icons/pizza.svg'
import Combo from '../assets/img/icons/french-fries.svg'
import Deserts from '../assets/img/icons/ice-cream.svg'
import Drinks from '../assets/img/icons/smothie.svg'
import Burguer from '../assets/img/icons/food.svg'

export default {
    name: 'CategoryMenu',
    components: {
        Pizza,
        Combo,
        Deserts,
        Drinks,
        Burguer,
    },
    data() {
        return {
            categoriesList: [
                {label: 'Pizza', icon: 'Pizza', id: 'pizza'},
                {label: 'Bebidas', icon: 'Drinks', id: 'drinks'},
                {label: 'Doces', icon: 'Deserts', id: 'deserts'},
                {label: 'Combos', icon: 'Combo', id: 'combo'},
                {label: 'Burguers', icon: 'Burguer', id: 'burguer'},
            ],
            selectedCategory: 'pizza'
        }
    },
    methods: {
        onCategoryClick(id){
            this.selectedCategory = id;
        },
        isActive(id) {
            return this.selectedCategory === id
        }
    }
}
</script>

<style lang="less" scoped>

.category-menu {
    width: 130px;
    height: 100vh;
    background: #fff;
    display: flex;
    align-items: center;

    ul {
        list-style: none;
        padding: 0;
        width: 100%;

        li {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100px;

            p {
                margin-bottom: 0px;
                font-size: 14px;
                color: @dark-grey;
            }

            svg {
                path{
                    fill: @dark-grey;
                }
            }

            &.active {
                background: @yellow;
                border-radius: 8px;

                p {
                    color: #000
                }

                svg {
                    path{
                        fill: #000;
                    }
                }
            }
        }
    }

    @media @tablets {
        width: 100%;
        height: fit-content;
        

        ul {
            display: flex;
            margin: 20px;
            overflow: scroll;
            justify-content: center;

            li {
                min-width: 78px;
            }
        }
    }
}

</style>