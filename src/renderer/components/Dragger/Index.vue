<template>
    <div v-if="false"></div>
</template>

<script>
    export default {
        name: "buter-dragger",
        mounted () {
            this.disableDragEvent()
        },
        methods: {
            disableDragEvent () {
                window.addEventListener('dragenter', this.disableDrag, false);
                window.addEventListener('dragover', this.disableDrag);
                window.addEventListener('drop', this.disableDrag)
            },
            disableDrag (e) {
                const dropzone = document.getElementById('gallery'); // 这个是可拖拽的上传区
                if (dropzone === null || !dropzone.contains(e.target)) {
                    e.preventDefault();
                    e.dataTransfer.effectAllowed = 'none';
                    e.dataTransfer.dropEffect = 'none'
                }
            }
        },
        beforeDestroy () {
            window.removeEventListener('dragenter', this.disableDrag, false);
            window.removeEventListener('dragover', this.disableDrag);
            window.removeEventListener('drop', this.disableDrag)
        }
    }
</script>

<style scoped>

</style>