<script>
    import { conversation_data } from "./stores";
    import { Button, Dropdown, DropdownItem, Chevron } from "flowbite-svelte";

    const ConvMode_enum = {
        1: "CHITCHAT",
        2: "ASK",
        3: "THINK",
        4: "QUIZ",
        5: "TIMED",
        6: "INTERVIEW",
        7: "YESNO",
        8: "CHAIN",
    };

    // @ts-ignore
    function cariKunci(bernilai) {
        var objek = ConvMode_enum;

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
    <div class="text-xl font-bold">Conv Mode</div>
    <div color="blue">
        <Button color="blue"
            ><Chevron>{ConvMode_enum[$conversation_data.convmode]}</Chevron
            ></Button
        >
        <Dropdown color="blue">
            {#each Object.values(ConvMode_enum) as convmode}
                <DropdownItem color="blue" on:click={handleClick}
                    >{convmode}</DropdownItem
                >
            {/each}
        </Dropdown>
    </div>
</div>
