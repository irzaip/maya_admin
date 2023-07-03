<script>
    import { conversation_data } from "./stores";
    import { Button, Input, Label, Helper, Textarea } from "flowbite-svelte";



</script>

{#if $conversation_data.intro_msg}
<div>
    <Label for="intro" color="green" class="block mb-2">Intro message</Label>
    <Textarea id="intro" color="green" class="mb-6" rows="2" placeholder={$conversation_data.intro_msg} />

    <Label for="outro" color="green" class="block mb-2">Outro message</Label>
    <Textarea id="outro" class="mb-6" rows="6" placeholder={$conversation_data.outro_msg} />
</div>
{/if}