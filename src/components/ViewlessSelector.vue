<script>
import { ref, onMounted, onUnmounted } from 'vue'

export default {
    name: 'ViewlessSelector',
    props: {
        options: {
            required: true,
            type: Array
        },
        keyz: {
            required: true,
            type: String
        },
        value: null
    },
    setup(props, { slots }) {
        const menuRef = ref(null);
        const showDropdown = ref(false);
        const selectedOption = ref();
        const handleOptionSelection = (keyValue) => {
            selectedOption.value = props.options.find(lang => lang[props.keyz] === keyValue);
        }

        onMounted(() => {
            document.addEventListener('click', (event) => {
                if (menuRef.value == event.target || event.composedPath().includes(menuRef.value)) {
                    return;
                }

                showDropdown.value = false;
            });
        })

        onUnmounted(() => {
            document.removeEventListener('click', () => { });
        })



        return () => slots.default?.({
            value: 'Hello',
            options: props.options,
            selectedOption: selectedOption.value,
            menuRef,
            showDropdown: showDropdown.value,
            handleOptionSelection
        })
    },
}
</script>