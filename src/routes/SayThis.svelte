<script>
    import { conversation_data } from "./stores";
    import { Button, Input, Label, Helper, Textarea } from "flowbite-svelte";



</script>

{#if $conversation_data}
<div class="flex">
    <div>
    <Label for="say_this" color="green" class="mb-2">Say This</Label>
    <Input id="say_this" color="green" class="w-1/2" rows="2" />
    </div>
    <Button class="bg-blue-700 w-20">SEND</Button>

</div>
{/if}