<template>
    <li>
        <div @click='toggle'>
            <i v-if='isFolder' class="fa " :class="[open?'fa-folder-open':'fa-folder']"></i>
            <!--isFolder判断是否存在子级改变图标-->
            <i v-if='!isFolder' class="fa fa-file-text"></i> {{model.name}}
        </div>
        <ul v-show="open" v-if='isFolder'>
            <items v-for='cel in model.sub_node' :model='cel'></items>
        </ul>
    </li>
</template>
<script type="text/javascript">
    export default {
        name: 'items',
        props: ['model'],
        components: {},
        data() {
            return {
                open: false,
                isFolder: true
            }
        },
        computed: {
            isFolder: function() {
                return this.model.sub_node && this.model.sub_node.length
            }
        },
        methods: {
            toggle: function() {
                if(this.isFolder) {
                    this.open = !this.open
                }
            },
        }
    }
</script>