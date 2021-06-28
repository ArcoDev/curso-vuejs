<template>
  <section>
    <h3><span>Mis paneles</span> ► {{ name }}</h3>
    <input 
        type="text"
        placeholder="Agregar una lista"
        v-model="listName"
        @keyup.enter="add()"
    >
    <div class="contaier">
        <column v-for="(list, index) in boardList"
                :key="index"
                :listId="list.id"
                :name="list.name"
        >
        </column>
    </div>
  </section>
</template>

<script>
import Column from '@/components/Column'
export default {
    name: 'board-view',
    components: { Column },
    props: {
        name: String,
        id: String,
    },
    data () {
        return {
            listName: '',
            boardList: [
                {id: '1', name: 'Todo'},
                {id: '2', name: 'Doing'},

            ]
        }
    }, 
    methods: {
        add() {
            this.boardList.push({ name: this.listName })
        }
    }
}
</script>

<style lang="scss" scoped>
    section {
        text-align: left;
        h3 {
            color: #37474f;
            text-align: left;
            margin: 1.5rem;
            span {
                color: #546e7a;
            }
        }
        input {
            box-sizing: border-box;
            background-color: #546e7a;
            border:  2px solid #546e7a;
            border-radius: 3px;
            font-size: 1.1rem;
            outline: 0;
            padding: 0.5rem;
            margin-left: 1rem;
            transition: all 600ms ease;
            &:focus,
            &:active {
                background-color: #ffffff;
                color: #546e7a;
            }
            &::placeholder {
                color: #ffffff;
            }
        }
    }
</style>