<script>
    import { conversation_data } from "./stores";
    import { Button, Input, Label, Helper, Textarea } from "flowbite-svelte";



</script>

{#if $conversation_data.free_tries > 0}
<div class="flex">
    <div>
    <Label for="sys_message" color="green" class="block mb-2">Unit</Label>
    <Input id="sys_message" color="green" class="w-1/2 mb-6" rows="2" />
    </div>
    <Button class="bg-green-500">Free Tries</Button>
    <Button color="blue">Paid Messages</Button>

</div>
{/if}