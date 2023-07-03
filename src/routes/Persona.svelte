<script>
    import { Button, Dropdown, DropdownItem, Chevron } from "flowbite-svelte";
    import { conversation_data } from "./stores";

    const Persona_enum = {
        1: "ASSISTANT",
        2: "USTAD",
        3: "HRD",
        4: "CONTENT_MANAGER",
        5: "CONTENT_CREATOR",
        6: "PSYCHOLOG",
        7: "ROLEPLAY",
        8: "VOLD",
        9: "INDOSOAI",
        10: "KOBOLD",
        11: "SALES_CS",
    };

    // @ts-ignore
    function cariKunci(bernilai) {
        var objek = Persona_enum;

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

<div class="grid grid-cols-4">
    <div class="text-xl font-bold">Persona</div>
    <div color="blue">
        <Button color="blue"
            ><Chevron>{Persona_enum[$conversation_data.persona]}</Chevron
            ></Button
        >
        <Dropdown color="blue">
            {#each Object.values(Persona_enum) as persona}
                <DropdownItem color="blue" on:click={handleClick}
                    >{persona}</DropdownItem
                >
            {/each}
        </Dropdown>
    </div>
</div>
