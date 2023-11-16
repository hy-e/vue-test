<template>
<div @mousedown="$emit('modalClose')" class="black-bg" v-if="isOpen">
  <div class="white-bg">
    <img :src="contents.image" class="modal-image">
    <h4>{{contents.title}}</h4>
    <p>{{contents.content}}</p>
    <p>가격 : {{contents.price}}원</p>
    <discount-banner/>
  </div>
</div>
</template>

<script>
export default {
    name: "ModalComponent",
    props: {
        isOpen : Boolean,
        contents : Object,
    }
}
</script>

<style>

</style>