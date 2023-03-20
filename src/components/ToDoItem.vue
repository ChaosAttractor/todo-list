<template>
    <div class="task">
        <div class="task_content">
            <div class="task_check">
                <input type="checkbox" name="done" id="done" class="check">
            </div>
            <div class="task_text">
                <h2 class="title">{{ task.title }}</h2>
                <h2 class="date">{{ task.date }}</h2>
            </div>
        </div>
        <div class="todo_btns">
            <svg-icon type="mdi" :path="pathPencil" class="icon green"></svg-icon>
            <svg-icon type="mdi" :path="pathDelete" class="icon" @click="$emit('removeTask', task)"></svg-icon>
        </div>
    </div>
</template>

<script>
import SvgIcon from '@jamescoyle/vue-icon';
import { mdiDelete, mdiPencil } from '@mdi/js';

    export default {
        props: {
            task: {
                id: Number,
                title: String,
            }
        },
        components: {
            SvgIcon
        },
        data() {
            return {
                pathDelete: mdiDelete,
                pathPencil: mdiPencil,
            }
        },
    }
</script>

<style scoped>
.task {
    user-select: none;
    background: var(--main-todo-color);
    min-height: 50px;
    width: 580px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 10px;
    box-shadow: 12px 9px 20px #b9b9b9;
}
.task:hover {
    box-shadow: 12px 9px 20px 10px #b9b9b9;
    transition: all .3s;
}
.task_text {
    width: 400px;
    word-wrap: break-word;
}
.date {
    opacity: 60%;
}
.icon:hover {
    cursor: pointer;
    color: var(--red-icon-color);
    transition: all .3s;
}
.green:hover {
    color: var(--green-icon-color);
}
.check {
    height: 20px;
    width: 20px;
}
.task_content {
    display: flex;
    align-items: center;
    gap: 10px;
}
</style>