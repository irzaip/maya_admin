<script>
    import { conversation_data } from "./stores";
    import { Button, Input, Label, Helper, Textarea } from "flowbite-svelte";



</script>

{#if $conversation_data.messages}
<div>
    <Label for="sys_message" color="green" class="block mb-2">System Message</Label>
    <Textarea id="sys_message" color="green" class="mb-6" rows="2" placeholder={$conversation_data.messages[0].content} />

    <Label for="user_message" color="green" class="block mb-2">User Message</Label>
    <Textarea id="user_message" class="mb-6" rows="6" placeholder={$conversation_data.messages[1].content} />

    <Label for="assistant_message" color="green" class="block mb-2">Assistant Message</Label>
    <Textarea id="assistant_message" class="mb-6" rows="4" placeholder={$conversation_data.messages[2].content} />

</div>
{/if}