<script>
    import { conversation_data } from "./stores";
    import { Button, Input, Label, Helper, Textarea } from "flowbite-svelte";



</script>

{#if $conversation_data}
<div class="flex">
    <div>
    <Label for="sys_message" color="green" class="block mb-2">Temperature</Label>
    <Input id="sys_message" color="green" class="w-1/2 mb-6" rows="2" />
    </div>
    <Button class="bg-green-500">Temperature</Button>
    <Button color="blue">Toggle FREE GPT</Button>

</div>
{/if}