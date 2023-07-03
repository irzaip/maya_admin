<script>
    import { conversation_data } from "./stores";
    import { Button, Dropdown, DropdownItem, Chevron } from "flowbite-svelte";

    const ConvType_enum = {
        1: "DEMO",
        2: "FRIEND",
        3: "GOLD",
        4: "PLATINUM",
        5: "ADMIN",
    };

    // @ts-ignore
    function cariKunci(bernilai) {
        var objek = ConvType_enum;

        var [kunci, nilai] =
            Object.entries(objek).find(([key, value]) => value === bernilai) ||
            [];

        return kunci;
    }

    const handleClick = (e) => {
        e.preventDefault();
        console.log(e);
        alert("Clicked on: " + cariKunci(e.target.innerHTML));
    };
</script>

<div class="grid grid-cols-4 gap-4">
    <div class="text-xl font-bold">Conv Type</div>
    <div color="blue">
        <Button color="blue"
            ><Chevron>{ConvType_enum[$conversation_data.convtype]}</Chevron
            ></Button
        >
        <Dropdown color="blue">
            {#each Object.values(ConvType_enum) as convtype}
                <DropdownItem color="blue" on:click={handleClick}
                    >{convtype}</DropdownItem
                >
            {/each}
        </Dropdown>
    </div>
</div>
