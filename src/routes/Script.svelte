<script>
    import { conversation_data } from "./stores";
    import { Button, Dropdown, DropdownItem, Chevron } from "flowbite-svelte";

    const Script_enum = {
        1: "BRAIN",
        2: "DEPARSE",
        3: "JS_OBJECTS",
        4: "JSON_SERVER",
        5: "PARSER",
        6: "SESSIONS",
        7: "NEWCOMER",
        8: "INTERVIEW",
    };

    // @ts-ignore
    function cariKunci(bernilai) {
        var objek = Script_enum;

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
    <div class="text-xl font-bold">Script</div>
    <div color="blue">
        <Button color="blue"
            ><Chevron>{Script_enum[$conversation_data.script]}</Chevron></Button
        >
        <Dropdown color="blue">
            {#each Object.values(Script_enum) as script}
                <DropdownItem color="blue" on:click={handleClick}
                    >{script}</DropdownItem
                >
            {/each}
        </Dropdown>
    </div>
</div>
